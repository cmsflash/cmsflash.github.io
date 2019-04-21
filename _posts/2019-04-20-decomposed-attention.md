---
layout: post
title:  "Decomposed Attention: Self-Attention with Linear Complexities"
date:   2019-04-20 21:43:24 +0800
categories: AI
---

[*Decomposed Attention: Self-Attention with Linear Complexities*](https://arxiv.org/abs/1812.01243) is a work by myself and colleagues at SenseTime. We proposed a simple but effective method to decrease the computational and memory complexities of the self-attention mechanism from quadratic to linear, without loss of accuracy. This blog post will introduce the method and major results of the paper.

- [Motivation](#motivation)
  - [The Self-Attention Mechanism](#the-self-attention-mechanism)
  - [Drawback of Self-Attention](#drawback-of-self-attention)
- [Our Method](#our-method)
  - [A Closer Look at the Architecture Diagram](#a-closer-look-at-the-architecture-diagram)
  - [What about Normalization?](#what-about-normalization)
  - [Multi-Head Mechanism](#multi-head-mechanism)
- [Empirical Validation](#empirical-validation)
  - [Object Detection and Instance Segmentation](#object-detection-and-instance-segmentation)
  - [Stereo Depth Estimation and Image Classification](#stereo-depth-estimation-and-image-classification)
    - [Stereo Depth Estimation](#stereo-depth-estimation)
    - [Image Classification](#image-classification)
- [Why It Matters?](#why-it-matters)

# Motivation
## The Self-Attention Mechanism

The self-attention mechanism is a mechanism in neural networks that allows direct connection between each pair of positions in the input. Its core advantage over recurrence and convolution is its ability to modeling long-range dependency. Following is a diagram depicting a typical self-attention module.

![Illustration of the network architecture of conventional attention](/assets/2019-04-20-decomposed-attention/ca.png)

In this diagram, `n` represents the number of positions in the input, `k` and `c` represent the dimensionalities of the keys and the input, `K`, `Q`, `V`, and `M` represent the keys, the queries, the values, and the attention masks, respectively. This blog post will assume knowledge of the conventional self-attention mechanism. For more information on this topic, please refer to this [blog post](http://jalammar.github.io/illustrated-transformer/) by Jay Alammar from Udacity. 

## Drawback of Self-Attention

Despite its excellent ability for long-range dependency modeling, self-attention has a serious drawback. As you can see in the figure above, the intermediate result `M`'s shape is `n*n`. This means 1) its memory complexity is quadratic; 2) to generate the quadratically many elements, the computational complexity is also quadratic. Consequently, the memory and computational complexities of the entire self-attention module are quadratic.

This is a critical drawback. As computer scientists, we understand that a quadratical algorithm is much slower than a linear one on large inputs. And the gap grows rapidly as the input gets largers. This effectively forbids the application of self-attention on large inputs, like high-definition images, long sequences, and large videos. However, these inputs are important in various tasks, like object detection, instance segmentation, stereo vision, and video classification. Therefore, to democratize the self-attention mechanism to many more fields, it is critical to address its quadratic complexities.

# Our Method

## A Closer Look at the Architecture Diagram

To learn how to solve the issue of quadratic complexities, let's take a closer look at the architecture diagram of the self-attention module. The most resource-consuming and the only quadratically complex part of the module is the attention masks `M` of size `n*n`.

![The attention masks are the most resource-consuming part of a self-attention module](/assets/2019-04-20-decomposed-attention/ca-bottleneck.png)

However, if we more closely examine the diagram, we can see that `M` is surrounded by two consective matrix multiplications, as illustrated below. Now, recall your freshman-year linear algebra course. Matric multiplication is associative, which means if there are multiple consecutive matrix multiplications, you can choose whatever order to calculate. Therefore, what we can do is to simply swap the order of the two multiplications. Aha! This is the magic.

![Swapping the two multiplications lead to massive saving of resrouce usage](/assets/2019-04-20-decomposed-attention/association.png)

After the swapping, the size of the intermediate result changes from `n*n` to `k*c`. Since both `k` and `c` are constants under our control, the resultant memory complexity is `O(1)`. After some calculation, you can get the computational complexity, which is `O(n)`. This is the *decomposed attention* (DA) mechanism.

![Illustration of the network architecture for decomposed attention](/assets/2019-04-20-decomposed-attention/da.png)

## What about Normalization?

However, the analysis above is only for the vanilla version of self-attention. In practice, we often apply normalization to the attention masks to stablized training. Will the addition of normalization mess up the analysis? Let's look into this question with two dominant approaches for attention normalization, scaling normalization and softmax normalization.

For scaling normalization, the question is trivial. Since scaling normalization is merely dividing the attention masks `M` by a scalar that depends on `k` (`sqrt(k)`, to be precise), we can do the exact same thing on `N`, and the effect remains unchanged.

![Illustration of the network architecture for decomposed attention](/assets/2019-04-20-decomposed-attention/association-scaling.png)

The situation is slightly more complicated for softmax normalization. Since softmax is nonlinear, we cannot simply move the operation to `N` or anothre matrix. However, we can approximate its effect with two seperate softmax operations on `C` and `B`, respectively. The softmax on `C` is performed along its channel dimension, while the one on `B` is along the spatial dimension. After these operations, if we multiply `C` and `B`, their product will satisfy the same essential property as `M` that each row in it sums up to 1. Despite these operations are not exactly equivalent to the original, we have conducted empirical experiments to verify that the approximation doesn't cause any degradation in performance.

![Illustration of the network architecture for decomposed attention](/assets/2019-04-20-decomposed-attention/association-softmax.png)

## Multi-Head Mechanism

The multi-head mechanism is a method to enhance the expressive power of a self-attention module. It works by running the input through a set of slimmer (i.e. less channels) self-attention modules in parallel, concatenate their outputs, and apply a pointwise reprojection to the concatenated result. The process looks like the following diagram.

![The multi-head mechanism](/assets/2019-04-20-decomposed-attention/multihead.png)

The self-attention module used by the multi-head mechanism can be arbitary. For example, both conventional self-attention modules and DA modules are supported. However, since each conventional attention module will consume `O(n^2)` memory and computation, the total resource usage will scale linearly with the number of heads. In contrast, since the resource consumptions of a DA module is `O(cn)`, and the multi-head mechanism usually reduces the number of channels for each head by the number of heads, the total consumptions of a DA module have little changes when the number of heads increases. Somewhat surprisingly, the total consumptions decrease slightly with the increase of the number of heads. (For detailed analysis, refer to the [paper](https://arxiv.org/abs/1812.01243).)

# Empirical Validation

Okay. So now we have finished presenting the DA module itself. Let's have a look at how it performs in the real world. We picked 4 tasks to validate its performance: object detection, instance segmentation, image classification, and stereo depth estimation.

## Object Detection and Instance Segmentation

We mainly conducted comparative and ablative studies on these two tasks. For these tasks, we use the standard MS-COCO 2017 dataset.

| Method | Box AP | Mask AP |
| - | - | - |
| None | NaN | NaN |
| Scaling | **40.2** | 35.9 |
| Softmax | **40.2** | **36.0** |

We first compared the two proposed attention normalization methods. You can see that the two methods perform almost identically. This shows that the effectiveness of the DA module lies in its essential formulation, rather than any specific implementation.

| Number of heads | Box AP | Mask AP |
| - | - | - |
| 1 | 40.2 | **36.0** |
| 8 | 40.3 | **36.0** |
| 32 | **40.4** | 35.9 |

Then, we tried different numbers of heads. The results are once again close. This further confirms the effectiveness of the DA module in its essential formulation.

| Number of modules | Box AP | Mask AP |
| - | - | - |
| 1 | 40.2 | 36.0 |
| 5 | 40.6 | 36.1 |
| 7 | **41.2** | **36.7** |

After that, we experimented with adding not just one, but multiple DA modules to different parts of the network. (For details on where we inserted the modules and hyperparameter settings, refer to the [paper](https://arxiv.org/abs/1812.01243).) In this table, the trend is that the more you insert, the more (performance) you get. This results shows that the performance advantage provided by the DA module can scale with more of the module included in the network.

| Backbone | Box AP (improvement by DA) | Mask AP (improvement by DA) |
| - | - | - |
| ResNet-50 | 39.4 (+1.8) | 35.1 (+1.6) |
| ResNet-101 | 41.3 (+1.8) | 36.6 (+1.3) |
| ResNeXt-101 | 43.5 (+1.4) | 38.5 (+1.0) |

Next, we explore the effect of DA on different backbone networks. The table shows that DA is consistently effective on a diversity of backbones. It provides a considerable gain (+1.4 box AP and +1.0 mask AP) even on a highly competitive, ResNeXt-101 baseline.

| Number of modules | DA (box/mask) | conventional (box/mask) |
| - | - | - |
| 1 | 40.2/36.0 | 40.3/35.9 |
| 5 | 40.6/36.1 | OOM |
| 7 | **41.2**/**36.7** | OOM |

Then, we compared the effectiveness of DA agaisnt conventional attention. As you can see, when inserting the same number of modules, DA and conventional attention have very similar performance. When adding more modules, DA's performance increases steadily. However, the conventional modules quickly experienced out-of-memory errors and wasn't able to enjoy the benefit brought by incorporating more modules into the network.

| Method | Backbone | AP |
| - | - | - |
| TDM Faster R-CNN | Inception-ResNet-v2 | 36.8 |
| Mask R-CNN | ResNeXt-101 | 39.8 |
| Soft-NMS | Aligned-Inception-ResNet | 40.9 |
| Lighthead R-CNN | ResNet-101 | 41.5 |
| Fitness-NMS | ResNet-101 | 41.8 |
| **DA Mask R-CNN** | ResNet-101 | 43.1 |
| **DA Mask R-CNN** | ResNeXt-101 | 45.9 |

Finally, we contrasted DA-augmented detectors and instance segmenters against state-of-the-art published methods. DA Mask R-CNN has set  a new state-of-the-art on MS-COCO 2017 object detection and instance segmentation.

## Stereo Depth Estimation and Image Classification

To prove the generalizability of DA, we also tried it on two other important tasks, stereo depth estimation and image classification.

### Stereo Depth Estimation

For stereo depth estimation, we used a PSMNet with optimized hyperparameters as the baseline. The dataset used was Scene Flow. We only experimented with adding a single DA module.

| Model | EPE |
| - | - |
| iResNet-i2 | 1.40 |
| PSMNet | 1.09 |
| EdgeStereo | 1.12 |
| CSPN | 0.78 |
| DA-PSMNet | **0.48** |

As the table shows, DA PSMNet has set a record of end-point error (EPE) on the Scene Flow dataset by a large margin.

### Image Classification

For image classification, we used ResNet-50 as our baseline and tested on the ImageNet dataset.

| Number of modules | Top-1 accuracy(%) | Improvement |
| - | - | - |
| 0 | 76.052 | 0.000 |
| 1 | 76.932 | 0.880 |
| 2 | 77.312 | 1.260 |

As in the table, the incorporation of a couple of DA modules substantially improves the performance of a ResNet-50.

# Why It Matters?

Decomposed attention dramatically reduces the resource needs of the attention mechanism. It offers three advantages over conventional formulations:

1. With the same network architecture, DA saves resources.
2. Under the same resource budget, DA offers better performance.
3. In fields where the application of attention wasn't possible, DA enables the possibilities.

DA has the potential to democratize attention to many more applications and offers a huge amount of extra freedom in network architecture design.

*To learn more, refer to the paper on [arXiv](https://arxiv.org/abs/1812.01243) or [download](https://arxiv.org/pdf/1812.01243.pdf) it.*

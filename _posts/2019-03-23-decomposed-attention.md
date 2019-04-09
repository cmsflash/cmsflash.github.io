---
layout: post
title:  "Decomposed Attention: Self-Attention with Linear Complexities"
date:   2019-03-23 22:26:11 +0800
categories: AI
---

*Decomposed Attention: Self-Attention with Linear Complexities* is a work by Shen Zhuoran and colleagues at SenseTime. It proposes a simple but effective method to decrease the computational and memory complexities of the self-attention mechanism from quadratic to linear, without loss of accuracy. This blog post will introduce the method and major results of the paper.

- [Motivation](#motivation)
  - [The Self-Attention Mechanism](#the-self-attention-mechanism)
  - [Drawback of Self-Attention](#drawback-of-self-attention)
- [Our Method](#our-method)
  - [A Closer Look at the Architecture Diagram](#a-closer-look-at-the-architecture-diagram)
  - [What about Normalization?](#what-about-normalization)
  - [Multi-Head Mechanism](#multi-head-mechanism)
- [Empirical Validation](#empirical-validation)
  - [Object Detection and Instance Segmentation](#object-detection-and-instance-segmentation)
  - [Image Classification and Stereo Depth Estimation](#image-classification-and-stereo-depth-estimation)
- [Why it matters?](#why-it-matters)

# Motivation
## The Self-Attention Mechanism

The self-attention mechanism is a mechanism in neural networks that allows direct connection between each pair of positions in the input. Its core advantage over recurrence and convolution is its ability to modeling long-range dependency. Following is a diagram depicting a typical self-attention module.

![Illustration of the network architecture of conventional attention](/assets/2019-03-23-deco,posed-attention/ca.png)

In this diagram, `n` represents the number of positions in the input, `k` and `c` represent the dimensionalities of the keys and the input, `K`, `Q`, `V`, and `M` represent the keys, the queries, the values, and the attention masks, respectively. This blog post will assume knowledge of the conventional self-attention mechanism. For more information on this topic, please refer to this [blog post](http://jalammar.github.io/illustrated-transformer/) by Jay Alammar from Udacity. 

## Drawback of Self-Attention

Despite its excellent ability for long-range dependency modeling, self-attention has a serious drawback. As you can see in the figure above, the intermediate result `M`'s shape is `n*n`. This means 1) its memory complexity is quadratic; 2) to generate the quadratically many elements, the computational complexity is also quadratic. Consequently, the memory and computational complexities of the entire self-attention module are quadratic.

This is a critical drawback. As computer scientists, we understand that a quadratical algorithm is much slower than a linear one on large inputs. And the gap grows rapidly as the input gets largers. This effectively forbids the application of self-attention on large inputs, like high-definition images, long sequences, and large videos. However, these inputs are important in various tasks, like object detection, instance segmentation, stereo vision, and video classification. Therefore, to democratize the self-attention mechanism to many more fields, it is critical to address its quadratic complexities.

# Our Method

## A Closer Look at the Architecture Diagram

To learn how to solve the issue of quadratic complexities, let's take a closer look at the architecture diagram of the self-attention module. The most resource-consuming and the only quadratically complex part of the module is the attention masks `M` of size `n*n`.

![The attention masks are the most resource-consuming part of a self-attention module](/assets/2019-03-23-decomposed-attention/ca-bottleneck.png)

However, if we more closely examine the diagram, we can see that `M` is surrounded by two consective matrix multiplications, as illustrated below. Now, recall your freshman-year linear algebra course. Matric multiplication is associative, which means if there are multiple consecutive matrix multiplications, you can choose whatever order to calculate. Therefore, what we can do is to simply swap the order of the two multiplications. Aha! This is the magic.

![Swapping the two multiplications lead to massive saving of resrouce usage](/assets/2019-03-23-decomposed-attention/association.png)

After the swapping, the size of the intermediate result changes from `s*s` to `k*c`. Since both `k` and `c` are constants under our control, the resultant memory complexity is `O(1)`. After some calculation, you can get the computational complexity, which is `O(s)`. This is the *decomposed attention* (DA) mechanism.

![Illustration of the network architecture for decomposed attention](/assets/2019-03-23-decomposed-attention/da.png)

## What about Normalization?

However, the analysis above is only for the vanilla version of self-attention. In practice, we often apply normalization to the attention masks to stablized training. Will the addition of normalization mess up the analysis? Let's look into this question with two dominant approaches for attention normalization, scaling normalization and softmax normalization.

For scaling normalization, the question is trivial. Since scaling normalization is merely dividing the attention masks `M` by a scalar that depends on `k` (`sqrt(k)`, to be precise), we can do the exact same thing on `N`, and the effect remains unchanged.

![Illustration of the network architecture for decomposed attention](/assets/2019-03-23-decomposed-attention/association-scaling.png)

The situation is slightly more complicated for softmax normalization. Since softmax is nonlinear, we cannot simply move the operation to `N` or anothre matrix. However, we can approximate its effect with two seperate softmax operations on `C` and `B`, respectively. The softmax on `C` is performed along its channel dimension, while the one on `B` is along the spatial dimension. After these operations, if we multiply `C` and `B`, their product will satisfy the same essential property as `M` that each row in it sums up to 1. Despite these operations are not exactly equivalent to the original, we have conducted empirical experiments to verify that the approximation doesn't cause any degradation in performance.

![Illustration of the network architecture for decomposed attention](/assets/2019-03-23-decomposed-attention/association-softmax.png)

## Multi-Head Mechanism

The multi-head mechanism is a method to enhance the expressive power of a self-attention module. It works by running the input through a set of slimmer (i.e. less channels) self-attention modules in parallel, concatenate their outputs, and apply a pointwise reprojection to the concatenated result. The process looks like the following diagram.

![The multi-head mechanism](/assets/2019-03-23-decomposed-attention/multihead.png)

The self-attention module used by the multi-head mechanism can be arbitary. For example, both conventional self-attention modules and DA modules are supported.

# Empirical Validation

Okay. So now we have finished presenting the DA module itself. Let's have a look at how it performs in the real world. We picked 4 tasks
## Object Detection and Instance Segmentation

## Image Classification and Stereo Depth Estimation

# Why it matters?







To learn more, refer to the paper on [arXiv](https://arxiv.org/abs/1812.01243) or [download](https://arxiv.org/pdf/1812.01243.pdf) it.

---
layout: page
---

Shen Zhuoran (Zhuoran is the first name) is an AI Resident at [Google AI](https://ai.google/). Formerly, he was Research Interns at [Tencent](https://www.tencent.com/en-us/) and [SenseTime](https://www.sensetime.com/en/). He graduated with a BEng in Compute Science from [The University of Hong Kong](https://www.hku.hk/). His research interests include computer vision, natural language processing (NLP), and speech analysis with deep learning. Currently, he focuses on the the attention mechanism, especially the application of [efficient attention](ai/2019/03/23/decomposed-attention.html) in various domains. He also has interests in stereo vision, object recognition, and visual relationship detection.

# Education

**The University of Hong Kong**, Hong Kong

- Sep. 2015 - Jun. 2019.
- *Bachelor of Engineering* in *Computer Science*.
- GPA: 3.85/4.30. Standing: 1/111. Major GPA: 3.96/4.30.

**University of California, Davis**, Davis, CA, Unites States

- Sep. 2017 - Dec. 2017.
- *Bachelor's Reciprocity Student* in *Computer Science*.
- GPA: 4.00/4.00.

# Work Experience

**Google**, Seattle, WA, United States

- Oct. 2019 - Present.
- *AI Resident, Cerebra Team, Google AI*
- Working on foundations of fully-attentional visual modeling.

**Tencent**, Shenzhen, Guangdong, China

- Jul. 2019 - Sep. 2019.
- *Research Intern, Applied Research Center, Platform and Content Group*
- Designed and validated the *global context* module, which uses *efficient attention* to achieve linear complexities in spatial size and constant complexities in temporal span for deep video memories. Details in [Research Experience](#research-experience)
- Designed a natural scribble synthesis algorithm using skeletonization and random walks to improve data synthesis for interactive object segmentation.

**SenseTime**, Hong Kong

- Jun. 2017 - Jun. 2019.
- *Research Intern, Intelligent Perception and Services Team, Smart City Group*
- Conducted academic research projects listed in [Research Experience](#research-experience).

# Awards

- **Dean’s Honours List 2017-2018**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours List 2016-2017**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours List 2015-2016**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honor List, Fall Quarter 2017**, *College of Letters and Science, University of California, Davis*
- **YC Cheng Engineering Scholarship, 2017**, *Faculty of Engineering, The University of Hong Kong*

# Programming Contests

- **First Runner-up**, *ACM-HK Programming Contest 2017*
- **Second Runner-up**, *ACM-ICPC Hong Kong PolyU International Invitational 2017*
- **Second Runner-up**, *hackUST 2017 Radica Challenge*
- **Invited to A Day with Google**, *Google Code Jam 2017 Asia-Pacific University Test*
- **First Prize**, *China’s National Olympiad of Informatics in Provinces 2014*

# Research Experience

**Global Context Module**, Tencent
- Jul. 2019 - Sep. 2019.
- *Supervised by [Dr. Li Yu](https://yu-li.github.io/), Senior Research Scientist, Tencent.*
- Proposed the *global context* module, which uses *efficient attention* to achieve linear complexities in spatial size and constant complexities in temporal duration for deep video memory.
- Built the first real-time video object segmenter that has state-of-the-art accuracy (86.6, J&F @ 25 FPS, [DAVIS 2016](https://davischallenge.org/)).
- Submitted a first-author [paper](#preprints) to CVPR 2020.

**Efficient Attention**, Industry Research Experience

- Sep. 2018 - Jun. 2019.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Research Director, SenseTime.*
- *In collaboration with [Dr. Li Hongsheng](https://www.ee.cuhk.edu.hk/~hsli/), Assistant Professor, [Multimedia Laboratory, Chinese University of Hong Kong](http://mmlab.ie.cuhk.edu.hk/).*
- Proposed *efficient attention*, which reduced the memory and computational complexities of the attention mechanism from quadratic to linear and is applicable to computer vision, natural language processing (NLP), and speech analysis.
- Achieved new states-of-the-art on object detection (41.8→43.1, AP, [COCO 2017](http://cocodataset.org/#detection-2017)) and stereo depth estimation (1.09→0.477, EPE, [Scene Flow](https://lmb.informatik.uni-freiburg.de/resources/datasets/SceneFlowDatasets.en.html)) and significant improvement on instance segmentation (36.6→37.9, AP, [COCO 2017](http://cocodataset.org/#detection-2017)) and image classification (93.0%→93.7%, top-5 accuracy, [ImageNet](https://www.kaggle.com/image-net)).
- Submitted a first-author [paper](#preprints) to CVPR 2020.

**Context Voted Attention Networks**, Industry Research Experience

- Mar. 2019 - Jun. 2019.
- *Supervised by [Zhao Haiyu](https://scholar.google.com/citations?user=oGM5N1kAAAAJ), Senior Research Scientist, SenseTime.*
- Proposed *context voted attention networks*, which use instance-instance attention and pixel-instance attention modules to enhance contextual information for visual relationship detection.
- Set new states-of-the-art on visual relationship detection (52.0→52.9, role AP, [V-COCO](https://arxiv.org/abs/1505.04474); 33.91→38.79, recall@100&k=70, [VRD](https://cs.stanford.edu/people/ranjaykrishna/vrd/)).
- Submitted a [paper](#preprints) to CVPR 2020.

**Visual Embedding of Chinese**, Bachelor's Final-Year Project

- Sep. 2018 - Apr. 2019.
- *Supervised by [Dr. Kwan-Yee Kenneth Wong](https://i.cs.hku.hk/~kykwong/), Associate Professor, [Computer Vision Group, The University of Hong Kong](http://www.visionlab.cs.hku.hk/).*
- Designed *OceanText*, a novel character embedding algorithm for Chinese that extracts a semantic embedding from the image of a Chinese character with a convolutional neural network.
- Developed a PyTorch embedding library. Reduced single-GPU training time from 82 days to 28.1 hours compared to existing open-source implementations.
- Set a new state-of-the-art of 37.6% over the previous 15.6% in Spearman's rho for word similarity estimation on [WordSim-297 Chinese](https://github.com/Leonard-Xu/CWE/blob/master/data/297.txt) with character embedding

**Diabetic Retinopathy Analysis**, Industry Research Experience

- Sep. 2018 – Oct. 2018.
- *Supervised by [Zhao Haiyu](https://scholar.google.com/citations?user=oGM5N1kAAAAJ), Senior Research Scientist, SenseTime*
- Experimented with different hyperparameters and network architectures.
- Improved the accuracy on the [IDRiD](https://idrid.grand-challenge.org/Grading/) dataset from 40.5% to 59.6%.

**Stereo Depth Estimation**, Industry Research Experience

- May 2018 - Sep. 2018.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Research Director, SenseTime.*
- Developed a stereo depth estimator based on PSMNet with improved training procedures.
- Achieved 2x reduction in error rate (EPE) over the previous state-of-the-art on the [Scene Flow](https://lmb.informatik.uni-freiburg.de/resources/datasets/SceneFlowDatasets.en.html) dataset.

# Teaching Experience

**Software Engineering**, Teaching Assistant

- Jan. 2019 - May 2019.
- *Assisted [George Mitcheson](https://www.cs.hku.hk/people/profile.jsp?teacher=georgem), Guest Lecturer, Department of Computer Science, The University of Hong Kong.*
- Developed a [Django server](https://github.com/gibicehr/hrserver) as the external HR server for student projects and deployed it to [Heroku](https://gibice-hrserver.herokuapp.com/).
- Answered questions from and held consultations with students on Git, the Unified Modeling Language, and software design and engineering principles.

# Personal Projects

[**BeautyNet**](https://github.com/cmsflash/beauty-net)

- May 2018 - Oct. 2019.
- *Owner and primary contributor.*
- Developed a PyTorch project template. Applied deduplication, modularization, and a consistent code style to improve maintainability, testability, and analyzability.
- Became the 2nd most popular PyTorch template on GitHub, got 180+ stars, and trended for 3 days.

# Preprints

- Li Y.\*, **Shen Z.**\*, Shan Y. (2019). *Fast Video Object Segmentation using the Global Context Module*. In submission. \*Equal contributions.

- **Shen Z.**, Zhang M., Zhao H., Yi S., Li H. (2019). [*Efficient Attention: Attention with Linear Complexities*](https://arxiv.org/abs/1812.01243). arXiv:1812.01243.

- Zhang M., Wu J., Jin D., **Shen Z.**, Bai X., Zhao H. (2019). *Context Voted Attention Network for Visual Relationship Detection*. In submission.

# Skills

- **Programming**: Python, C, C++, Java, Shell script, Markdown, LaTeX
- **Machine Learning**: PyTorch, TensorFlow, Keras, Sonnet, Caffe, CUDA, NumPy, OpenCV
- **Technologies**: Git, Vim, Slurm, Django, Jekyll, Piper, Blaze, Gin
- **Languages**: Mandarin Chinese (native), English (working proficiency, 116 in TOEFL)

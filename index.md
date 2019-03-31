---
layout: page
---

Shen Zhuoran \(Zhuoran is the first name) is a Computer Science student at [The University of Hong Kong](https://www.cs.hku.hk/) and a Research Intern at [SenseTime](https://www.sensetime.com/). His research interests include computer vision, natural language processing (NLP), and speech analysis with deep learning. Currently, he focuses on the the attention mechanism, especially the application of [decomposed attention](ai/2019/03/23/decomposed-attention.html) in various domains. He also has interests in stereo vision, object recognition, and relation detection.

# Education

**The University of Hong Kong**, Hong Kong

- Sep. 2015 - Present.
- *Bachelor of Engineering* in *Computer Science*.
- CGPA: 3.97/4.30. Standing: 1/111. Major CGPA: 4.13/4.30.

**University of California, Davis**, Davis, CA, Unites States

- Sep. 2017 - Dec. 2017.
- *Bachelor's Reciprocity Student* in *Computer Science*.
- GPA: 4.00/4.00.

# Work Experience

**SenseTime**, Hong Kong

- Jun. 2017 - Present.
- *Research Intern, Intelligent Perception and Services Team, Smart City Group*
- Developed a research project template that facilitated a team of ~40 to transition from Caffe to PyTorch.
- Conducted academic research projects listed in [Research Experience](#research-experience).

# Awards

- **Dean’s Honours Lists 2017-2018**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours Lists 2016-2017**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours Lists 2015-2016**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honor List, Fall Quarter 2017**, *College of Letters and Science, University of California, Davis*
- **YC Cheng Engineering Scholarship, 2017**, *Faculty of Engineering, The University of Hong Kong*

# Programming Contests

- **First Runner-up**, *ACM-HK Programming Contest 2017*
- **Second Runner-up**, *ACM-ICPC Hong Kong PolyU International Invitational 2017*
- **Second Runner-up**, *hackUST 2017 Radica Challenge*
- **Invited to A Day with Google**, *Google Code Jam 2017 Asia-Pacific University Test*
- **First Prize**, *China’s National Olympiad of Informatics in Provinces 2014*

# Research Experience

**Universal Neural Networks** at *SenseTime*

- Jan. 2019 - Present.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Vice Director of Research, SenseTime*
- *In collaboration with [Speech Group, Machine Intelligence Laboratory, Cambridge University](https://mi.eng.cam.ac.uk/Main/Speech/WebHome)*
- Designing a novel, universal network architecture for computer vision, natural language processing, and speech analysis with decomposed attention.

**Human-Object Interaction Detection with Attentive Feature Pyramid and pairNMS** at *SenseTime*

- Mar. 2019.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Vice Director of Research, SenseTime*
- Proposed *attentive feature pyramid*, a feature pyramid with decomposed attention for relation detection.
- Proposed *pairNMS*, an effective non-maximum suppression mechanism for relation detection.
- Improved the baseline role AP of 42.8 to 50.3 on the [V-COCO](https://arxiv.org/abs/1505.04474) dataset for relation detection and set a new state-of-the-art over the previous 48.7.
- Submitted a [paper](#preprint) to ICCV 2019.

**Visual Embedding of Chinese** at *Computer Vision Group, The University of Hong Kong*

- Sep. 2018 - Present.
- *Supervised by [Dr. Kwan-Yee Kenneth Wong](https://i.cs.hku.hk/~kykwong/), Associate Professor, [Computer Vision Group, The University of Hong Kong](http://www.visionlab.cs.hku.hk/)*
- Designing a novel model to improve Chinese embedding accuracy by utilizing visual features.
- Developed a PyTorch embedding library. Reduced single-GPU training time from 82 days to 28.1 hours compared to existing open-source implementations.
- Bachelor’s final year project.

**Decomposed Attention** at *SenseTime*

- Sep. 2018 - Mar. 2019.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Vice Director of Research, SenseTime*
- Proposed *decomposed attention*, which reduced the memory and computational complexities of the self-attention mechanism from quadratic to linear and is applicable to computer vision, NLP, and speech analysis.
- Achieved new states-of-the-art on object detection (43.1 over 41.8 in AP on [MS-COCO 2017](http://cocodataset.org/#detection-2017)) and stereo depth estimation (0.477 over 1.09 in EPE on [Scene Flow](https://lmb.informatik.uni-freiburg.de/resources/datasets/SceneFlowDatasets.en.html)) and significant improvement on instance segmentation (37.9 over 36.6 in AP on MS-COCO 2017) and image classification (93.7% over 93.0% in top-5 accuracy on [ImageNet](https://www.kaggle.com/image-net)).
- Submitted a first-author [paper](#preprint) to ICCV 2019.

**Project on Stereo Depth Estimation** at *SenseTime*

- May 2018 - Aug. 2018.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Vice Director of Research, SenseTime*
- Developed a stereo depth estimator based on PSMNet with improved training procedures.
- Achieved 2x reduction in error rate (EPE) over the previous state-of-the-art on the [Scene Flow](https://lmb.informatik.uni-freiburg.de/resources/datasets/SceneFlowDatasets.en.html) dataset.
- Primary investigator.

# Teaching Experience

**Software Engineering**, Teaching Assistant

- Jan. 2019 - May 2019.
- *Assisting [George Mitcheson](https://www.cs.hku.hk/people/profile.jsp?teacher=georgem), Guest Lecturer, Department of Computer Science, The University of Hong Kong*
- Developed a Django server as the external HR server for student projects and deployed the server on [Heroku](https://gibice-hrserver.herokuapp.com/).

# Other Projects

[**BeautyNet**](https://github.com/cmsflash/beauty-net)

- May 2018 - Present.
- Developed a PyTorch project template. Applied deduplication, modularization, and a consistent code style to improve maintainability, testability, and analyzability.
- Became 2nd most popular PyTorch template on GitHub, got 180+ stars, and trended for 3 days.
- Owner and primary contributor.

# Preprint

- **Shen Z.**, Zhang M., Yi S., Yan J., and Zhao H. (2019). [*Decomposed Attention: Self-Attention with Linear Complexities*](https://arxiv.org/abs/1812.01243). arXiv:1812.01243.
- Zhang M., Wu J., Jin D., **Shen Z.**, Yi S., and Zhao H. (2019). *Human-Object Interaction Detection with Attentive Feature Pyramid and pairNMS*. In submission.

# Skills

- **Programming**: Python, C, C++, Java, Shell script, Markdown, LaTeX
- **Technologies**: PyTorch, Caffe, Git, Slurm, Django, Jekyll, Vim, CUDA, NumPy, OpenCV
- **Languages**: Mandarin Chinese (native), English (working proficiency, 116 in TOEFL)
---
layout: page
---

Shen Zhuoran (Zhuoran is the first name) is an AI Resident at [Google Research](https://research.google/). He holds a BEng in Computer Science from [The University of Hong Kong](https://www.hku.hk/) and has formerly been Research Interns at [Tencent](https://www.tencent.com/en-us/) and [SenseTime](https://www.sensetime.com/en/). He currently focuses on the the attention mechanism, including fully-attentional visual modeling and the application of [efficient attention](ai/2019/12/02/efficient-attention.html) in various domains. He also has interests in large-scale visual pretraining and natural language processing.

# Education

**The University of Hong Kong**, Hong Kong

- Sep. 2015 - Jun. 2019.
- *Bachelor of Engineering* in *Computer Science*.
- GPA: 3.85/4.30. Standing: 1/111.

**University of California, Davis**, Davis, CA, Unites States

- Sep. 2017 - Dec. 2017.
- *Bachelor's Reciprocity Student* in *Computer Science*.
- GPA: 4.00/4.00.

# Work Experience

**Google**, Seattle, WA, United States

- Oct. 2019 - Present.
- *AI Resident, Personal AI, Google AI*
- Working on foundations of fully-attentional visual modeling. Proposed *global self-attention networks*. Details in [Research Experience](#research-experience).

**Tencent**, Shenzhen, Guangdong, China

- Jul. 2019 - Sep. 2019.
- *Research Intern, Applied Research Center, Platform and Content Group*
- Proposed the *global context* module for video object segmentation. Details in [Research Experience](#research-experience).

**SenseTime**, Hong Kong

- Jun. 2017 - Jun. 2019.
- *Research Intern, Intelligent Perception and Services Team, Smart City Group*
- Designed efficient attention that boosted the performance of object detectors in the company’s intelligence infrastructure supporting various teams. Details in [Research Experience](#research-experience).

# Memberships

- [Sigma Xi Full Member](https://www.sigmaxi.org/members/becoming-a-member)
- [ACM Professional Member](https://www.acm.org/membership)
- [IEEE Member](https://www.ieee.org/membership/index.html)
- [IEEE Young Professional](https://yp.ieee.org/)

# Awards

- **Dean’s Honours List 2018-2019**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours List 2017-2018**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours List 2016-2017**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honours List 2015-2016**, *Faculty of Engineering, The University of Hong Kong*
- **Dean’s Honor List, Fall Quarter 2017**, *College of Letters and Science, University of California, Davis*
- **YC Cheng Engineering Scholarship, 2017**, *Faculty of Engineering, The University of Hong Kong*

# Programming Contests

- [**First Runner-up**](https://www.cs.hku.hk/data/news/2017/0717_ACM-HK_2017.htm), *ACM-HK Programming Contest 2017*
- **Second Runner-up**, *ACM-ICPC Hong Kong PolyU International Invitational 2017*
- **Second Runner-up**, *hackUST 2017 Radica Challenge*
- **First Prize**, *National Olympiad of Informatics in Provinces (China) 2014*

# Research Experience

**Global Self-Attention Networks**, Google
- Dec. 2019 - Oct. 2020.
- *Supervised by [Dr. Raviteja Vemulapalli](https://scholar.google.com/citations?user=0OFqm7YAAAAJ), Senior Research Scientist and [Dr. Jia Xuhui](https://scholar.google.com/citations?user=vO0VSSYAAAAJ), Senior Software Engineer, Google Research, Google.*
- Proposed global self-attention networks (GSA-Nets), one of the first to use efficient attention mechanisms to fully replace convolution for computer vision applications.
- Demonstrated superior trade-offs for accuracy vs. parameters, computation, and latency over CNNs.
- Submitted a first-author [paper](#preprints) to ICLR 2021.

**Global Context Module**, Tencent
- Jul. 2019 - Sep. 2019.
- *Supervised by [Dr. Shan Ying](https://scholar.google.com/citations?user=4oXBp9UAAAAJ), Director of Applied Research Center, Platform and Content Group, Tencent.*
- Proposed the global context module, which effectively and efficiently propagates information through an arbitrarily long video with constant complexity w.r.t. video length and linear complexity w.r.t. resolution.
- Developed the first real-time video object segmenter that has state-of-the-art accuracy.
- Presented a first-author [paper](#preprints) at ECCV 2020.

**Efficient Attention**, SenseTime

- Sep. 2018 - Jun. 2019.
- *Supervised by [Dr. Yi Shuai](https://scholar.google.com.hk/citations?user=afbbNmwAAAAJ), Research Director, SenseTime.*
- *In collaboration with [Dr. Li Hongsheng](https://www.ee.cuhk.edu.hk/~hsli/), Assistant Professor, [Multimedia Laboratory, Chinese University of Hong Kong](http://mmlab.ie.cuhk.edu.hk/).*
- Proposed efficient attention, which reduces the memory and computational complexities of the attention mechanism from quadratic to linear.
- Demonstrated significant improvement in performance-cost trade-offs on a variety of tasks including object detection, instance segmentation, and stereo depth estimation.
- To present a first-author [paper](#preprints) to WACV 2021.

**Visual Embedding of Chinese**, Bachelor's Final-Year Project

- Sep. 2018 - Apr. 2019.
- *Supervised by [Dr. Kwan-Yee Kenneth Wong](https://i.cs.hku.hk/~kykwong/), Associate Professor, [Computer Vision Group, The University of Hong Kong](http://www.visionlab.cs.hku.hk/).*
- Designed *OceanText*, a novel character embedding algorithm for Chinese that extracts a semantic embedding from the image of a Chinese character with a convolutional neural network.
- Developed a PyTorch embedding library. Reduced single-GPU training time from 82 days to 28.1 hours compared to existing open-source implementations.
- Significantly improved accuracy for word similarity estimation from character embeddings for Chinese.

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
- Developed the 2nd most popular PyTorch template on GitHub with 190+ stars and very high code quality.

# Publications and Preprints

- **Shen Z.**, Zhang M., Zhao H., Yi S., Li H. (2021). [*Efficient Attention: Attention with Linear Complexities*](https://arxiv.org/abs/1812.01243). WACV 2021.
- **Shen Z.**, I. Bello, R. Vemulapalli, Jia X., Chen C.-H. (2020). [*Global Self-Attention Networks for Image Recognition*](https://arxiv.org/abs/2010.03019). arXiv: 2010.03019.
- Li Y.\*, **Shen Z.**\*, Shan Y. (2020). [*Fast Video Object Segmentation using the Global Context Module*](https://arxiv.org/abs/2001.11243). ECCV 2020. *\*Equal contributions*.

# Skills

- **Programming**: Python, C, C++, Java, Shell script, Markdown, LaTeX
- **Machine Learning**: PyTorch, TensorFlow, Keras, Sonnet, Caffe, CUDA, NumPy, OpenCV
- **Technologies**: Git, Vim, Slurm, Django, Jekyll, Piper, Blaze, Gin
- **Languages**: Mandarin Chinese (native), English (working proficiency, 116 in TOEFL)

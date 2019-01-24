---
layout: post
title:  "Tracking the States-of-the-Art for Deep Learning Tasks"
date:   2019-01-08 21:11:09 +0800
categories: publication
---

TL;DR: [Deep Learning SotA](https://github.com/cmsflash/deep-learning-sota) is a new, actively maintained, neatly formatted project tracking the states-of-the-art for various tasks of deep learning. Star it if you like it.

Deep learning has been exploding in recent years, with more and more results in a wide range of fields coming out at an unprecedented pace. On the one hand, it shows the prosperity of the discipline. On the other hand, it creates difficulties in tracking the states-of-the-art in various fields.

There are several projects trying to track the SotAs for deep learning tasks. However, each of them has drawbacks. [RedditSota](https://github.com/RedditSota/state-of-the-art-result-for-machine-learning-problems) takes a similar approach to this project but: 1) has not been actively maintained recently and 2) does not have a unified format (i.e. each section lists its SotA results in a different and unorganized fashion). [StateOfTheArt.ai](https://www.stateoftheart.ai/) is a website attempting to do the same. However, it is heavily crowdsourced without very good management. Therefore, its lists are messy. For example, it has two entries for the ImageNet dataset (`Imagenet` and `ImageNet ILSVRC 2012 Validation`) and two for Switchboard Hub5'00 (`Switchboard (Hub5)` and `Switchboard; Hub5`). Its list for speech recognition has a column for Word Error Rate, one for WER, and two for Word Error Rate (clean). It is very confusing and makes it hard to compare metrics among different papers.

Therefore, I created a new project on GitHub, [Deep Learning SotA](https://github.com/cmsflash/deep-learning-sota). It aims to be an actively maintained repository recording and tracking the SotAs in various deep learning tasks. These SotAs are organized into three broad categories, computer vision, NLP, and speech. Within each category, the results are sorted by tasks. Each task records its SotAs in a table. Every entry in every table has the same format, recording the dataset, type (single-model, ensemble, etc.), metric, method, paper, and links to open-source implementation.

I created this project so that everyone can easily see what is the best performance recorded to date on a particular dataset for a certain task and what method achieved that. However, I am only a newbie researcher and certainly cannot track all important progresses in the field. You will highly appreciated if you notice some items are outdated or missing in the repository. You can either raise an [issue](https://github.com/cmsflash/deep-learning-sota/issues/new) and start a [pull request](https://github.com/cmsflash/deep-learning-sota/compare) for that.
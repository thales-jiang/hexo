---
title: Dive into deep learning
date: 2020-08-11 16:15:24
tags: AI 人工智能 Python 手动学深度学习
---


# 新的历程



领到了中科院的录取通知书


{% asset_img ems.jpg [录取通知书] %}


现在中科院读研，研究“人工智能与应用”。


老师给出了要学习的书籍——


1. 李沐，《动手学深度学习》，英文版名称：Dive into Deep Learning。Deep Learning for the Layman(为外行准备的深度学习)
2. 周志华，《机器学习》
3. 韩家炜，《数据挖掘》
4. 李航，《统计学习方法》


# Dive into deep learning 《手动学深度学习》


这个书籍应该是最简单的一本，并且有在线的，纸质书籍反而是后来出的


中文网址<https://zh.d2l.ai/>


英文网址<http://www.d2l.ai/>


# 前言 pretext


中文


{% asset_img book-zh.svg [目录] %}


英文


{% asset_img book-en.svg [目录] %}


# 中英文差异


这本书强烈建议中英文一起看，因为有一些差异。


英文不过关的话，可以看了中文之后，再看一下英文版。


眼前来看，英文版比中文版多很多内容。



# AI库


[mxnet](http://mxnet.incubator.apache.org/versions/1.6/)


[pytorch](https://pytorch.org/)


[tensorflow](https://tensorflow.google.cn/)


*本书主要用的mxnet库，其实用啥库都一样，只要思想正确就行*


# 深度学习简介(Introduction)


所有内容都是我自己理解的，如果有错误，我会回来修改。


第一章，我了解机器学习首先要明白一个问题——


机器学习最重要的是多个样本，然后给出正确样本，机器会分析出正确样本的特征，用来分析新的样本是否正确。


所以，人工智能最重要的是给机器足够多的样本，这样机器可以把正确的方式找出来。


记得之前看《机器学习》（西瓜书）的时候，就有这样的例子，西瓜的成熟，在花纹、瓜秧、声响多个样本中，找出符合好瓜的样本。在多个样本录入之后，就会正确找出好瓜。


所以我现在了解，人工智能首先需要大数据的支持，也就是——


**足够多的样本(以及正确样本)**



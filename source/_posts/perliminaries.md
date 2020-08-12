---
title: 手动学深度学习-预备知识
date: 2020-08-12 14:21:13
tags:
---
# 预备知识(perliminaries)


这一章主要是安装需要的软件以及jupyter记事本


# conda


anaconda


英 [ˌænəˈkɒndə]  美 [ˌænəˈkɑːndə]


n. 水蚺(南美洲蟒蛇)


python原意巨蟒，这个anacoda也是一种蟒，联系还是很巧妙的


adaconda是一个包和依赖的管理工具，类似于node.js的npm


**只用安装conda就可以完成各种安装了，不用再单独安装python**


minicoda就是anaconda的缩减版


下载地址 —— [minicoda](https://conda.io/en/master/miniconda.html)



# 安装jupyter记事本


我们的课本是用jupyter记事本写的，所以我们需要conda安装一下依赖


```bash
conda env create -f environment.yml
```


如果觉得国外网站比较慢，可以用国内的源
```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```



眼前遇到第一个问题，按照流程走，并不能打开jupyter记事本


提示错误为
```bash
Warning: you have pip-installed dependencies in your environment file, but you do not list pip itself as one of your conda dependencies.  Conda may not use the correct pip to install your packages, and they may end up in the wrong place.  Please add an explicit pip dependency.  I'm adding one for you, but still nagging you.
```

打开environment.yml看看配置，我理解应该跟package.json类似


```yml
name: gluon
dependencies:
- python=3.6
- pip:
  - mxnet==1.5.0
  - d2lzh==1.0.0
  - jupyter==1.0.0
  - matplotlib==2.2.2
  - pandas==0.23.4
```


我理解是pip的内容没有安装成功


因为我手动安装是可以完成的


但是眼前知识面太窄了，并不知道比较优雅的做法，只好把pip都手动安装了一下


```bash
pip install mxnet
pip install d2lzh
pip install jupyter
pip install matplotlib
pip install pandas
```


但是安装mexnet时候numpy出错


```
pip install mxnet
```


用了各种方法，都过不去，安装numpy的时候出错


单独安装numpy没有问题，但是安装mxnet就报错，今天卡这里了。


后来降级了一下python，用3.7没有问题了，应该是兼容问题，真是麻烦啊。



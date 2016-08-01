---
layout: post
title: 谈谈梯度下降法和牛顿法
date: 2016-08-01
categories: blog
tags: [机器学习]
description: 梯度下降法在机器学习中有着极为广泛的应用,和牛顿法结合在一起理解效果会更好一点
---

# 谈谈梯度下降法和牛顿法

一开始接触梯度下降法是在线性回归里面,求解使损失函数最小化的,参数最优的情况.之后再涉及到牛顿法的时候又有了新的认识,让我们一步一步来进行分析.

## 一、梯度下降法

### 1. 通俗理解

先来看线性回归的损失函数:

![](http://oam2zfeyb.bkt.clouddn.com/1.png)

我们的目的就是以损失函数作为目标函数,来求线性回归的参数,使得目标函数的值最小,即损失最小化,这里就可以使用梯度下降法来使得目标函数最小化,那什么是梯度下降法呢?

我们先不谈公式,想象一下,你目前站在一座山的山腰上面,你想走到山脚下,梯度下降法就可以理解成你从现在这个位置,一步一步的走到山脚下,这个过程就是梯度下降法.

现在我们来看梯度下降法的公式:

![](http://oam2zfeyb.bkt.clouddn.com/2.png)

<u>注:下面一条用了向量的表示方法,因为在更新参数的时候我们要求对所用的参数进行同时更新</u>

上式中a表示步长,从字面上理解就是每一步走了多远,也称为学习速率.

## 2.为什么梯度下降法是下降的?

这句话听上去好像是句废话,实际上是很有门道的,在帮助我们理解牛顿法上有很大的帮助.

### 1. 先验知识,泰勒展开式

泰勒展开式的由来:

![](http://oam2zfeyb.bkt.clouddn.com/3.png)

这是我在知乎上面看到的一个答案,[原文链接](https://www.zhihu.com/question/25627482/answer/32060408)

**泰勒展开式的通项**:

![](http://oam2zfeyb.bkt.clouddn.com/4.png)

**泰勒展开式的目的是原式子太复杂,将它展开成更简单的多项式进行求解.**

### 2. 从泰勒展开式到梯度下降法

![](http://oam2zfeyb.bkt.clouddn.com/5.png)

接下来要证明为什么是下降的以及与梯度下降法的联系

![](http://oam2zfeyb.bkt.clouddn.com/1-6.png)

所以我现在就是求f(x+ad)的最小值(因为要求损失函数最小)

![](http://oam2zfeyb.bkt.clouddn.com/1-7.png)

### 3.梯度下降法的问题

- 梯度下降法可能无法收敛到全局最优值
- a的选择影响迭代速度

## 二、牛顿法

仍然是由泰勒展开式开始,只不过是展开到了二阶导:

![](http://oam2zfeyb.bkt.clouddn.com/1-8.png)

#### 补充:正定矩阵

设M是n阶方阵，如果对任何非零向量z，都有zT*Mz*> 0，其中*zT* 表示z的转置，就称M正定矩阵。

正定矩阵一定可逆。来自[百度百科](http://baike.baidu.com/link?url=_8B3lQv5PrAeOG_R8A86rWyKXp5jm7MJ1yOsJZdzVF2FOvZAHmFlmDZxxjLKtYnvbiEE20nxaklqGxUtNQetG_)

#### 1. 求f(x)极小值

f(x)有极小值的必要条件是在极值点处一阶导数为0,特别是当H(x)是正定矩阵时,函数f(x)的极值为极小值。

![](http://oam2zfeyb.bkt.clouddn.com/1-9.png)

#### 2. 牛顿法的优点

因为是二阶导,收敛速度非常快

## 三、再谈梯度下降法

#### 1.梯度下降法的计算量问题

![](http://oam2zfeyb.bkt.clouddn.com/2.png)

在梯度下降法里,每一次对参数的更新都需要对所有的样本进行求和,所以,一旦数据量很大的话,对所有样本进行求和就会导致效率很低,由此衍生出两个解决办法。

#### 2. 随机梯度下降法

从梯度下降法的目标函数到随机梯度下降法的目标函数:

![](http://oam2zfeyb.bkt.clouddn.com/1-10.png)

现在更新参数就是对CostFunction进行求导:

![](http://oam2zfeyb.bkt.clouddn.com/1-13.png)

可以看到,和原先的梯度下降法比起来,每次只用一个样本对参数θ进行更新,计算量相较而言要小很多,但是随机梯度发<u>不能保证每一步都是在下降的</u>,因为包含了很多的噪声,所以需要画图进行判断,是否参数是在逐渐下降的,一般可以每1000次更新后进行画图,如果图显示没有在下降,可以试试看5000次一画,因为由于噪声的原因,趋势不明显,5000次更新就可以比较好的看出来,如果5000次仍然显示参数没有在下降,这就意味着哪里出了一些问题.

**总结:随机梯度下降法可以求得近似最优解,优点是速度快**

#### 3. 迷你梯度下降法 mini-batch gradient descent

迷你梯度下降法是对梯度下降法的另一种改进办法,在梯度下降法中每次迭代需要进行m次的求和运算,而迷你梯度下降法是每次进行b次的求和运算,2<=b<=100,一般来说取b=10就可以了.

![](http://oam2zfeyb.bkt.clouddn.com/1-12.png)

## 四、关于步长α的问题

不同大小的α会导致不同的迭代情况,α过小迭代速度慢,α过大会来回迭代,同样会出现问题,具体见下图:

![](http://oam2zfeyb.bkt.clouddn.com/1-14.png)

那么我们如何保证能够取得比较合适的α的值呢?

简单举个例子:

![](http://oam2zfeyb.bkt.clouddn.com/1-15.png)

具体请见 [知乎:最爱麦丽素的回答](https://www.zhihu.com/question/19723347/answer/113542871)



参考:博客: [codelast](http://www.codelast.com/%E5%8E%9F%E5%88%9B%E6%9C%80%E9%80%9F%E4%B8%8B%E9%99%8D%E6%B3%95%EF%BC%8C%E7%89%9B%E9%A1%BF%E6%B3%95%EF%BC%8C%E5%85%B1%E8%BD%AD%E6%96%B9%E5%90%91%E6%B3%95%EF%BC%8C%E5%85%B1%E8%BD%AD%E6%A2%AF%E5%BA%A6/)

​	     [统计学习方法 李航](http://baike.baidu.com/link?url=7UwuqAG_Gd7DFf4nJDAX4r9bEXrkJ91mcdSY313FlUBQov7smaBwLHOl9yVTAszEQCRfdyTHUW45tZjpehqtta)

​	    coursera: [机器学习-Andrew Ng](https://www.coursera.org/learn/machine-learning/home/welcome)



预告:下一篇应该会写SVM支持向量机以及一些关于之前一段时间做天池比赛的一些感悟。






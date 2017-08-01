---
layout: post
title: FRM BOOK1 Chapter3
date: 2017-07-24
categories: blog
tags: [FRM]
description: 考试。
---

# FRM Book1:Chapter Ⅲ

## 1.Risk Management Failures:What Are They and When Do They Happen?

Not correctly recognizing,measuring ,and/or monitoring risks as well as not appropriately communicating these risks to top management 

[for the exam ] : understand the use of VaR --> **a useful tool for measuring  and montioring market,credit,and operational risk**

### The role of Risk Management

* assess all risk faced by the firm 
* communicate these risks to risk-taking decision makers
* monitor and manage these risks(make sure the firm only takes the necessary amount of risk )

```
assessing
communicating
monitoring
managing risks
```

<u>realize that large losses are possible and develop contingency plans that deal with such losses if they should occur</u>

[ one key issue  ] : know the occurrence  of extreme events(those events which occur with low frequency,but high severity)

---

Failing to take down and unknown risks into account can take three forms

* igonoring a risk that is known 
* knowing about a risk ,but failing to properly incorporate it into risk models
* failing to discover all risks

```
##几个名词
counterparty risk 交易对手风险
contingency plan 应急计划

##Risk Management can fail if a firm does not do the following
measure risks correctly
recognize some risk
communicate risks to top management
monitor and manage risks
use appopriate metrics
```

### Properly Communicating Risks

[ Purpose of  risk management ] : to allow senior managers of the firm to make the optimal strategic decisions to maximize firm value

### Ongoing Risk Management

[ key element for successful risk management ] :to recognize how quickly and dramatically risk charactertistics can change

[ Heisenberg Principal ] : increasing the certainty for one variable may introduce uncertainty for another variable

**Firms can fail to monitor and manage risk on an ongoing basis by not having an adequate incentive structure and/or culture that promotes effective risk management ** 

就是说需要相应的激励措施

### The Role of Risk Metrics

[ One misuse of VaR ] : choose a time period that does not  correspond to the liquidity of the assets in the portfolio.



### 2. Delineating Efficient Portfolios

[ Focus ] : portfolio return and volatility.Be familiar with the calculations of expected return and volatility for a two-asset portfolio and understand the importance of correlation in portfolio diversification

* the shape of the portfolio possibilities curve
* what is meant by the minimum variance portfolio
* what the efficient frontier looks like and how short sales and riskless borrowing affect it 


![](http://oam2zfeyb.bkt.clouddn.com/frm31.png)

[ The variance of a two-asset portfolio ] :

![](http://oam2zfeyb.bkt.clouddn.com/frm32.png)

![](http://oam2zfeyb.bkt.clouddn.com/frm33.png)

![](http://oam2zfeyb.bkt.clouddn.com/frm34.png)



#### 2.1 The portfolio Possibilities Curve

对于一个two-asset 组合，任何比例的组合都是可能的，所以我们针对不同的配置比例进行画图

![](http://oam2zfeyb.bkt.clouddn.com/frm35.png)

我们需要去寻找方差最小的资产配置比例，即Minimum Variance Portfolio

如果两个资产完全相关，即相关性=1，分散性为0，根据公式

![](http://oam2zfeyb.bkt.clouddn.com/frm36.png)

两个资产相关性越低，组合的波动性就会减小，所以两个资产负相关是最好的 。

当两个资产相关性=0的时候，构建一个0波动性的组合是可能的，w1和w2计算如下：

![](http://oam2zfeyb.bkt.clouddn.com/frm372.jpg)

当两个资产相关性为0的时候，假设每个资产的标准差都大于0，那么不能构建一个方差为0的组合，但是最小方差组合的比例计算还是和上面那张图一样。这里没有想明白。

### 2.2 Efficient Frontier

画出所有风险资产的各种组合，我们可以得到下面一张图：

![](http://oam2zfeyb.bkt.clouddn.com/frm37.png)

在这条线上的点意味着：

* Minimum risk with the same expected return
* Maximum return with the same risk
* start from the global minimum variance portfolio

### 2.3 CML

一般投资者在配置资产组合的时候都会加入无风险资产，所以在加入无风险资产之后，我们的曲线变成了一条直线，这就是Capital Market Line

![](http://oam2zfeyb.bkt.clouddn.com/frm38.png)



* 截距是无风险利率
* 斜率是reward-to-risk ratio for the portfolio

![](http://oam2zfeyb.bkt.clouddn.com/frm39.png)

风险厌恶者会在lending这一部分

风险偏好者会将资产组合配置在borrowing这一段

This result is known as separation theorem.



## 3. The Standard CAPM

[ Focus ] : CML and CAPM

Assumptions of CAPM:

* 无交易费用
* Assets are infinitely divisible.It is possible to hold fractional shares
* 没有税费
* 投资者买卖对市场无影响，这是一个完全竞争市场
* 投资者效用只依据回报率和风险
* 无限卖空
* 投资者可以无限以无风险利率借贷
* 投资者只关心一个single period的回报和风险
* 投资者对回报率，方差，协方差有一致性预期，即 homogeneous expectations
* 所有资产是可以交易的，包括人力

### 3.1 CML

[ key conclusion ] : All investors will optimal investment decisions by allocating between the risk-free asset and the market portfolio .

The CML is useful for computing the expected return for an efficient portfolio,cannot compute for an inefficient portfolio.

CAPM  can be used to compute for any inefficient portfolio or individual security.

### 3.2 Beta

The sensitivity of an asset's return to the market return.

so beta=covirance of asset A's return with the market return/ variance of the market return

![](http://oam2zfeyb.bkt.clouddn.com/frm40.png)

实际中如何计算Beta：

estimate asset betas by regressing returns on the asset on those of the market index.

就是使用了最小二乘法，斜率就是Beta

### 3.3 Portfolio Beta

### 3.4 CAPM

当资产足够分散的时候，非系统风险被认为消除了，只有系统风险



## 4. Applying the CAPM to Performance Measurement : Single-Index Performance Measurement Indicators

![](http://oam2zfeyb.bkt.clouddn.com/frm41.png)

![](http://oam2zfeyb.bkt.clouddn.com/frm42.png)






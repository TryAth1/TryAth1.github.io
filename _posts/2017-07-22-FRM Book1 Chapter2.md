---
layout: post
title: FRM BOOK1 Chapter1
date: 2017-07-22
categories: blog
tags: [FRM]
description: 考试。
---

# FRM Book1:Chapter Ⅱ

## 1.Risk Management,Governance,Culture,And Risk Taking in Banks

[main topic ] : a bank taking risk concerning its optimal level of risk 

### Optimal Level of Risk

[ Determine ] :

- target a certain probability or a specfic credit rating

```python
if credit_rating = AAA :
    bank earns a lower profit withstanding a low risk
# 如果银行的最优风险承受是AA级，那么如果选择了AAA级，即享有了一个较低的收益，
# 选了BBB级，收益高，但是风险也高
```

- Sensitivity analysis or sceneario analysis

determine its optimal level of risk exposure by the impact of specfic shock

（变量的变化可能会导致不同的结果）

### How the Optimal Level of Risk can differ Across Banks

```python
if a bank focusing on deposits,relationship lending customers or both :
    it will set the level of risk lower and prefer a higher credit rating 
###
if a bank takes more risk than its optimal risk level:
    its value will decrease signficantly
elif a bank takes on more risk toward the optimal level :
    its value will increase
```

### Risk-Taking Implications

too little risk -->  suboptimal return 

too muck risk --> unstable financial system

### Why taking risk management

```python
if incremental risk costs much:
    a value in having a risk management 
```

### Risk Management Challenges And Limitations

[ Focus ] : Describe structural challenges and limitations to effective risk management,including <u>VAR</u> in setting limits

------

#### Limitations of Hedging

- risk management technology limitations
- hedging limitations
- risk- taking incentive limitations

```python
if a bank can measure its risk perfectly:
    hedging would reduce risk perfectly
   
```

### Role of Risk Management  Within the bank

- not merely to have a vertification function
- advising whether to accept or reject a risky project based on established risk limits
- if the risk management is viewed  as a form of internal policing ,then a necessary dialogue between risk managers and business unit managers will not exists ,which may leads to an incorrect risk assessment made and not enabling them to propse mitigation procedures timely.
- - 简单来说，就是风险经理和业务经理不沟通，两者互相之间对各自的业务不理解，导致不正确的风险评估以及不能及时转移风险

## Value At Risk

使用VaR的前提条件 ： consider its ability to adjust its Var efficiently(eg: quickly and at a low cost )

[ Bank breaks down risks into 3 categories ] :

- market risk
- credit risk
- operational risk

**In measuring risk at the firm wide ,not all risks included ** : 

such as : operational risk,non-interest income ,interest rate,funding liquidity risk,the risk pertaining to unexpected interest rate and  credit spread changes

```
the higher the correlation estimates between such risks 
the higher the firm_wide 
```

**Different types of risks leads  to different statistical distributions**

- market risk --> the normal distributions despite its fatter tail
- credit and operational risks have distributions that are both fat-tailed and very skewed 

<u>it is much more challenging to add up risks that follow a non-normal distribution</u>

**Having enough history to properly determine if the VaR level is unbiased,biased upward,or biased downward **

```python
if VaR is estimated at extremely low level such as 0.08%:
    unknown risks become as issue
### 这么低的概率，损失将是一个小概率事件，做分析就会很却历史数据
```

## Bank Risk Profile And Performance

[ Incentive structive ] : reward if creating value for the overall bank  when taking risks while penalize for destroying value



## 2.Financial Disasters

[ Focus ] : Case studies

### Misleading Reporting Cases

```
CHase Manhattan Bank : 美国大通银行
by exploiting a flaw in the market's system for computing the value of collateral of Us Government bonds which were oftrn valued without the consideration of accrued interest

###

Kidder Peabody : 基德公司
该公司误报了一系列的交易，导致出现了大量的盈利，虽然这些盈利是虚假的，但是使得GE对此丧失了信任，而没有选择出售该公司，最后拆分了它
```


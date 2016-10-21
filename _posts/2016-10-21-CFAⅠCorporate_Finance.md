---
layout: post
title: CFA Level Ⅰ-3 Corporate Finance(7%)
date: 2016-10-21
categories: blog
tags: [CFA一级]
description: 本篇是对CFA一级学习的总结。
---

# CFA Level Ⅰ -3 Corporate Finance(7%)

**写在前面的话** :

​     复习CFA的时候笔记实际上非常重要,我是用非常快的速度大概2-3天一本的速度扫完了一本Notes之后做的笔记,这是我做的第一篇笔记,如果不足请指正。

[TOC]



## 1.Captal Budgeting

### 1.1  Key points

- Capital budgeting process
- Calculation of NPV,IRR
- How to jugde by NPV and IRR
- When NPV and IRR give a conflicting result,how to judge

### 1.2 Interpretion:Capital budgeting process

#### 1.2.1 Capital budgeting process

[ Definition ]  : Capital budgeting is the process of evaluating capital projects,projects with cash flows over more than one year.

[ Four steps ] : 

- Generate investment ideas
- Analyze project ideas
- - [ a cash flow forecast must be made to determine its profitability ]
- Create firm-wide capital budget 
- - [ attractive individually may not make sense strategically ]
- Monitor decisions and conduct a post-audit 
  - [ compare the actual results to the projections explain why ]
  - [ post audit is used to improve forecasting and operations ]

------

#### 1.2.2 Capital budgeting projects may be divided into five categories

- Replacement projects to maintain the business 
- - without detailed analysis
- - whether the existing operations should continue and if so,whether exsiting procedures or processes should be maintained.
- Expansion projects
- - detailed analysis is needed
- - whether equitment that is obsolete ,but still usable,should be replaced.
- New product or market development
- - detailed analysis is needed 
- Mandatory projects 
- - involve safety-related or environmental concerns
- - generate little to no revenue,but accompany new revenue-producing projects undertaken by the company
- Other projects
  - not easily analyzed through the capital budgeting process
  - include a pet project of senior management(corporate perks 公司津贴) or a high-risk endeavor (research and development projects)  

------

#### 1.2.3 The capital budgeting projects including five key principals

- Decisions are based on cash flows,not accounting income
- - Sunk cost
  - - Costs that cannot avoided ,even if the project is not undertaken


- Externalities
- - - The effects the acceptance of a project may have on other firm cash flows.


- - - a new diet version of an existing beverage may have a negative effect on the existing product
- Conventional cash flow pattern
  - - the sign on the cash flows changes only once
  - Unconventional cash flow pattern
  - - has more than a sign change
- Cash flows are based on opportunity costs
- - for example: when building a plant,even if the company already owns the land,the cost of the land should be charged to the project because it could be sold if not used.
- The timing of the cash flow is important
- - money has time value which means the cash flows reveived earlier are worth more.
- Cash flows are analyzed on an after-tax basis
- Financing costs are reflected in the projects' required rate of return.
- - discount rate used takes account of the company's cost of capital
  - only projects return more than cost increses the value of the company

------

### 1.3 Interpretion:NPV and IRR

#### 1.3.1  Projects

- Independent Project
- - If profits,can both undertake
- Mutually Exclusive Project
- - Can only take one 
- Project Sequencing
- - Some projects must be undertaken in a certain order
- Unlimited Funds vs. Capital Rationing
- - Since many companies have contraints on the amount of the capital,they must use capital rationing.Prioritize the project that achieve the maxmiun increase in value for shareholders given its available capital.

#### 1.3.2 NPV  and IRR calculation and juding criterion

Calculation is so easy that i omit it.

<u>Project that has a positive NPV should be accepted,and rejected with a negative NPV</u>

```python
if IRR > RequiredRateOfReturn:
    return "Accepted"
else:
    return "Rejected"
```

#### 1.3.3 Payback Period

[ Definition ] : the number of years it takes to recover the initial cost of an investment

[Main effect ] : Measuring the liquidity

[ Drawbacks ] : Didn't take time value into consideration

[ Use ] : Firms with limited access to additional liquidity often impose a maxmium payback period and then use a measure of profitability ,such as NPV,IRR.

**Discounted Payback Period**

Take the time value  into consideration differentiate two methods. 

This method takes account of the time value.

#### 1.3.4 Profitablity Index(PI)



![](http://oam2zfeyb.bkt.clouddn.com/cfa-1.png)

```python
if PI > 1:
    return "Accepted"
else:
    return "Rejected"
```

------

#### 1.3.5 A graph about NPV and IRR



![](http://oam2zfeyb.bkt.clouddn.com/cfa-2.png)

------

### 1.4 Interpretion : How to judge by NPV and IRR

#### 1.4.1 The key advantage

- NPV
- - A direct measure of the increase value into the company
- IRR
- - Provides infomation on the margin of safety that the NPV does not

#### 1.4.2 The disadvantages

- NPV
- - include any consideration of the size of the project
- IRR
- - may have more than one IRR or no IRR(results from unconventional cash flow)
  - the possibility that gives the different result compared to the NPV method

------

### 1.5 Interpretion :When NPV and IRR give a conflicting result,how to judge

[ Conventional Cash Flows ] : NPV and IRR give the same result

[ Unconventional Cash Flows ] : have no IRR or multiple IRRs

[ Mutually exclusively Projects ] : Use NPV to rank the projects

BTW: A company's stock price will increase only when the NPV is unanticipated



------

## 2.Cost Of Capital

### 2.1 Key Points

This session required us to know well about how the firm raises its capital to fund its business or finance its growth.The goal is the minimum overall cost of capital and the maxmium increasing value to the firm.

- Understanding of WACC and calculation
- Calculation of the costs of the different ways of rasing capital
- Understanding why the marginal cost of capital increases as greater amounts of capital are raised over a given period

### 2.2 WACC

------

#### 2.2.1 Concept

Discount the cash flows assosciated with a capital budgeting project alse referred as the marginal cost of capital (MCC)

Each investment decision must be made assuming a WACC.

WACC reflects the average risk of the projects that make up the firm,it is not appropriate for evaluating all new projects.

```python
if risk > AverageRisk :
    print "adjusted upward"
else:
    print "adjusted downward"
```

#### 2.2.2 Three components

- Debt(after-tax)
- cost of preferred stock
- cost of common equity

#### 2.2.3 Calculation

![](http://oam2zfeyb.bkt.clouddn.com/cfa-3.png)

If there is a trend in the firm's capital structure,an analysis should make an adjustment.

#### 2.2.4 The optimal Capital Budget Graph

![](http://oam2zfeyb.bkt.clouddn.com/CFA-4.png)

- Upward Curve : A firm's WACC may increases as larger amounts of capital are raised.
- Downward Curve : Ranking the expenditures on additional projects from highest IRR to lowest IRR.

------

### 2.3 Calculation of the costs of the different ways of rasing capital

#### 2.3.1 Debt

Here,we treat all debts as tax-deductible.

The cost of the debt is the market rate(YTM) on new debt,not the coupon rate on the firm's exsiting debt.

![](http://oam2zfeyb.bkt.clouddn.com/CFA-5.png)

#### 2.3.2 Preferred Stock

![](http://oam2zfeyb.bkt.clouddn.com/CFA-6.png)

#### 2.3.3 Common Equity-Three approach

- CAPM

![](http://oam2zfeyb.bkt.clouddn.com/CFA-7.png)

We can find more details about the CAPM approach in the portfolio management.

- The dividend discount model approach  

![](http://oam2zfeyb.bkt.clouddn.com/CFA-8.png)

g=(rotation rate)*(return on equity)=(1-payout rate) * ROE

- Bond yield plus risk premium approach


- - k = bond yield + risk premium

------

### 2.5 Other calculations

#### 2.5.1 calculations of β

steps:

- Find a public company that resembles with the target company
- Calculate the assetβ(get rid of the leverage) 

![](http://oam2zfeyb.bkt.clouddn.com/CFA-9.png)

- Use βasset to calculate the target company's β

![](http://oam2zfeyb.bkt.clouddn.com/CFA-10.png)

<u>For a given set of projects, the greater a firm’s reliance on debt financing, the greater its equity beta</u>

<u>Project beta calculated using the pure-play method is note necessarily related in a predictable way to the beta of the firm that is performing the project.</u>

#### 2.5.2 The revised CAPM approach

![](http://oam2zfeyb.bkt.clouddn.com/CFA-11.png)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-112.png)

#### 2.5.3 The break points

![](http://oam2zfeyb.bkt.clouddn.com/CFA-12.png)

#### 2.5.4 Flotation costs(发行成本)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-13.png)

<u>Some companies have an after-tax flotation cost.</u>

------

## 3. Measures Of Leverage

### 3.1 Key Points

- Financial and operating leverage
- Breakeven quantity of sales
- Understanding how a firm's decisions 
- - regarding its operating structure and scale 
  - and its decisions regarding the use of debt and equity financing(its capital structure) affect its breakeven levels of sales
  - and the uncertainty regarding its operating earnings and net income

------

### 3.2 Some concepts about Risk

- Business risk
- - Sales risk
- - Operating risk
  - - the additional uncertainty about operating earnings caused by fixed operating costs
- Financial risk

------

### 3.3 Some Criterions

#### 3.3.1 Degree Of Leverage(DOL)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-14.png)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-15.png)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-16.png)

When sales go up,DOL will decline.So DOL is highest as low levels of the sales and declines at higher levels of sales.

#### 3.3.2 Degree Of Financial Leverage (DFL)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-17.png)

#### 3.3.3 Degree Of Total Leverage(DTL)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-18.png)

**No fixed costs,no operating leverage**.

**No interest costs,no financial leverage**.

#### 3.3.4 Effect Of The Leverage

More revenue,More risk.

------

### 3.4 Breakeven Calculation

#### 3.4.1 Definition

Revenues equal to total costs,so that net income is zero.

![](http://oam2zfeyb.bkt.clouddn.com/CFA-19.png)

#### 3.4.2 Graph

![](http://oam2zfeyb.bkt.clouddn.com/CFA-20.png)

#### 3.4.3 Operating Breakeven Quantity of Sales

![](http://oam2zfeyb.bkt.clouddn.com/CFA-21.png)

------

## 4.Dividends And Share Repurchase

### 4.1Key Points

- Dividends and Repurchases
- Calculating the EPS and book value after the repurchases

------

### 4.2 Dividends

#### 4.2.1 Cash Dividends

- Regular dividends
- Special dividends
- - Cyclical firms(like automakers) pay dividends when times are good .When profits are down,they maintain the flexibility to converse cash
- Liquidating dividends
- - When a company goes out of business and distributes the proceeds to the shareholders.Taxed as capital gains

#### 4.2.2 Stock Dividends

Dividends paid out in new shares of stock rather than cash

Increase the number of shares outstanding

#### 4.2.3 Stock Splits

- Stock price tends to increase since it is taken as a positive signal from management about future earnings
- But if a report of a good earning doesn't follow a stock split,prices tend to revert to their original levels
- Tend to reduce liquidity because of the higher percentage of brokerage fees on lower-priced stocks

#### 4.2.4 Reverse Stock Splits

Because of the too low price

#### 4.2.5 Effects on Financial Ratios

Cash dividends paid decrease assets(cash) and shareholders' equity.So the company's liquidity ratios will decrease and debt-to-assets ratio,debt-to-equity will increase.

#### 4.2.6 Dividend Payment Chronology

------

### 4.3 Repurchase

#### 4.3.1 Share Repurchase Methods

- Buy in open market
- Buy a fixed number of shares at a fixed price
- Repurchase by direct negotiation

#### 4.3.2 Use Company's excess cash and debt to finance the repurchase

- Use Company's excess cash
- - reduce interest income and earnings
- Use debt
- - incure interest cost,which will reduce earnings directly by the after-tax cost of the borrowed funds

#### 4.3.3 Effects of using debt to finance the repurchase

```python
if AfterTaxCost < EarningsBeforeRepurchase :
    print "EPS will increase"
else:
    print "EPS will decrease"
```

#### 4.3.4 Effects of a repurchase on the BVPS

```python
if RepurchasePrice > BVPS :
    print "BVPS will decrease"
else:
    print "BVPS will increase"
```

------

## 5.Working Capital Management

### 5.1 Key Points

- Management of current assets and liabilities
- Types of short-term bank financing
- The receivables,and payables aging schedule

### 5.2 Sources Of Liquidity

#### 5.2.1 Primary Sources Of Liquidity

*Sources of cash it uses in its normal day-to-day operations*

- cash balances 
- - result from selling goods and services ,collecting receivables,and generating cash from other sources such as short-term investment
- short-term funding
- - trade credit from vendors and lines of credit from banks
- Effective cash flow management of a firm's collections and payment 
- - also be a source of liquidity for a company

#### 5.2.2 Secondary Sources Of Liquidity

- Liquidating short-term or long-lived assets
- Negotiating debt agreements
- Filing for bankruptcy 
- Reorganizing the company

<u>change the company's financial structure and operations signficantly and may indicate that its financial position is deteriorating</u>

#### 5.2.3 Conclusion

*a company's liquidity position improves if it can get cash to flow in more quickly and flow out more slowly*

<u>Factors that weaken a company's liquidity position are called drags and pulls on loquidity</u>

- Drags on liquidity
- - delay or reduce cash inflows
- Pulls on liquidity
- - accelerate cash outflows

------

### 5.3 Ways Of Measuring Liquidity

#### 5.3.1 Ratios

- Current Ratio
- Quick Ratio
- Receivables turnover
- - number of days of receivables
- Inventory turnover
- - number of days of inventory
- Payables turnover
- - number of days of payables

#### 5.3.2 Operating cycle,Cash conversion cycle

```python
OperatingCycle = DaysOfInventory + DaysOfReceivables
CashConversionCycle = DaysOfInventory + DaysOfReceivables - DaysOfPayables
```

#### 5.3.3 Daily Cash Position

Refers to uninvested cash balances a firm has available to make routine purchases and pay expenses as they come due

------

### 5.4 Yield Calculation

![](http://oam2zfeyb.bkt.clouddn.com/CFA-22.png)

#### 5.4.1 Discount-basis Yield(bank discount yield or BDY)

![](http://oam2zfeyb.bkt.clouddn.com/CFA-23.png)

#### 5.4.2 Money Market Yield

![](http://oam2zfeyb.bkt.clouddn.com/CFA-24.png)

#### 5.4.3 Bond Equivalent Yield

![](http://oam2zfeyb.bkt.clouddn.com/CFA-25.png)

------

### 5.5 Cash Management Policy

*objective: generating yield without taking on excessive credit or liquidity risk*

- limitations on the specific types of securities permitted for investment of short-term funds
- limitations on the credit ratings of portfolio serurites
- limitations on the proportions of the total short-term securities portfolio that  can be invested in the various types of permitted securities

------

### 5.6 Aging Schedule and Weighted Average Collection period

<u>The company must always evaluate the  trade-off between stricter credit terms (and borrower creditworthiness) and the ability to make sales</u>

*Terms that are too strict will lead to less-than-optimal sales*

*Terms that are too lenient will increase sales at the cost o longer average days of receivables which must be funded at some cost,and will increase bad accounts,directly affecting profitability*

#### 5.6.1 Inventory Management

*Inventory levels that are too low will result in lost sales due to stock-outs*

*Inventory that is too loarge will have carrying costs because the firm's capital is tied up in inventory*

<u>Comparing average days of inventory and inventory turnover ratios between industries,or even between two firms that have different business strategies,can be misleading</u>

#### 5.6.2 Accounts Payable Management

<u>payables represent a source of  working capital to the firm</u>

<u>Terms"2/10 net 60"</u>:

*if the invoice is paid within 10 days,the company gets a 2% discount on the invoice amount*

*the net amount is due 60 days from the  date of the invoice*

![](http://oam2zfeyb.bkt.clouddn.com/CFA-26.png)

<u>Company with a short payables period</u>:

*may simply be taking advantage of discounts for paying early because it has good low-cost funds available to finance its working capital needs*

------

### 5.7 Sources Of Short-term funding

#### 5.7.1 Bank Sources

- <u>Lines of Credit(信贷额度)</u>:


- - Uncommitted line of credit(未承诺信用额度)
- - Committed line of credit
- - Revolving line of credit
- Banker's acceptances (银行承兑汇票)
- Factoring(保理)

#### 5.7.2 Non-bank Sources

Large, creditworthy companies can issue short-term debt securities called commercial paper.

*the interest costs are slightly less than the rate they could get from the bank*

------

## 6.The Corporate Governance Of Listed Companies:A Manual For Investors

### 6.1 Key Points

- Originating from the collapses of some major corporations and associated investor losses

### 6.2 Corporate Governance

#### 6.2.1 What is required?

- internal controls
- processes and procedures by which firms are managed

#### 6.2.2 Target

Ensure that

- the board director is independent of management 
- the firm and its managers act lawfully,ethcially,and in the interests of shareholders

### 6.3 Takeover Defenses

- golden parachutes 
- - rich severance packages(高额遣散费) for top managers who lose their jobs as a result of takeover
- poison pills
- - provisions that grant rights to existing shareholders in the event a certain percentage of a company's shares are acquired
- greenmail 
- - use of corporate funds to buy back the shares of a hostile acquirer at a premium to their market value




















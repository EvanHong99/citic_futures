# research on bid-ask spread

市场价差与价格/到期时间/delta/vega/虚实值程度的关系；
报多宽。一般不会去确定性的报n档
不同行权价统一起来，行情大市场价可以比较大，可解释性，不要黑盒
一天之内切分可以切分成好几个模型
delta vega 关系，价差的弹性、斜率。无风险利率（机会成本）、交易频率、价格固定的percentage、成交量volume（论文说没有太大作用）
不同时间维度、不同标的价格波动、不同greeks、直接乘以个价格百分比、不同品种之间的相关性
不是日内的周期性，而是随着mat到期的变化他价差可能存在周期性
市场以什么结构在报价，希望每个报价都均匀。
可能比较难用价格的百分比
同一个期权，存续期内他的spread会有什么变化规律
行情来的时候spread会变大吗报价会变宽吗？

对于第二个课题内容比较单薄这个问题，我觉得可以尽量将逻辑缘由讲清楚，可以简单做一下相关内容的survey，然后在之后的模型中有目的地涉及其中部分idea；我对可扩充的内容想了一下，在日内spread规律之外，可能可以加入：

1. 时间维度：历史上bid-ask spread的统计、同一个期权存续期内spread 的变化
2. 期权维度：针对每个期权可以涉及更精细化的建模，每个期权可以通过别的期权的一些特征来进行建模
3. 模型维度：在linear之外，加入另外一些lasso、rf这些仍具有较高可解释性的模型，并可以用cross-validation、grid-search等方式计算aic
   bic挑选最优超参等

模型：

- GMM GeneralizedMethodofMoments广义矩估计

结果呈现：
可以参考 [Business Fin   Account - 2003 - Abhyankar - Bid‐ask Spreads  Trading Volume and Volatility  Intra‐day Evidence from the...](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/高频/日内规律/bid-ask spread/Business Fin Account - 2003 - Abhyankar - Bid‐ask Spreads Trading Volume and Volatility Intra‐day Evidence from the.pdf)
日内最小值spread呈现什么样的统计规律？
一般什么时候spread会收敛到一个模型可信的范围内，即模型什么时候可以被启用
同一个时间段不同Option的spread特点
同一个Option不同时间的spread特点，包括日内和日间
可以画三维散点图，moneyness、mat、spread
一周内的每个日期是否有规律

相关论文：

- [最优买卖一档价格之外的信息](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/高频/日内规律/bid-ask
  spread/American J Agri Economics - 2019 - Arzandeh - Price Discovery in Agricultural Futures Markets Should We Look
  beyond the.pdf)，可能可以帮助建模，甚至预测
- Compound Hawkes Process

争议点：
流动性风险溢价？
之情交易？

## 数据




## 因子

1. [x] Percentage spread
2. [x] call price, call options price = mid-quote of bid-ask spread
3. [x] time to maturity
4. [x] Time to maturity2
5. [x] delta. 是否需要区分c和p. 已经部分包含moneyness的信息。。如果不区分，则需要将他们都转化为正值，或者用dummy来标识delta正负符号的信息
6. [x] implied volatility
7. [-] moneyness。 是否需要区分c和p。Using moneyness measured as the forward stock price divided by the strike price, we
   expect that the more out-of-the-money is the option, the bigger will be the percentage spread since those options
   provide the most leverage. For a call option, moneyness>1 means that the option is in the money, For a put option,
   moneyness>1 means that the option is out of the money,
8. [-] moneyness2。 是否需要区分c和p
9. [-] moneyness * time to maturity。 是否需要区分c和p
10. [-] moneyness * delta。 是否需要区分c和p
11. [x] duration = average duration for 10 transactions
12. [x] duration2
13. [x] volume = average volume for 10 transactions
15. [x] percentage spread of stocks/etf/股指期货/syn期货。针对不同的预测目标进行调整
15. [x] spread of stocks/etf/股指期货/syn期货。针对不同的预测目标进行调整
16. [x] 加入用于识别上午开盘、下午开盘的dummy
17. [ ] 不能同时加入ask1_c/bid1_c这种能直接计算出y的因子
18. [ ] y可以改为volume weighted bid ask spread
19. [ ] todo etf price？
14. [ ] cross-options markets. 同mat和strike的c和p在深虚深实会有非常大的差异，因此不适合作为因子
20. [ ] tick size。国内期权市场好像只能0.0001
21. [ ] 用标的波动率极速变化的时候的平均时间
22. 
23. 

成本型因子
share price,
return volatility,
average time between trades (the determinants of the inventory-holding premium)
inverse of trading volume
the modified Herfindahl index
CBA denotes the call bid-ask spread measured in dollars.
CDUM is a dummy variable that equals one if the call price is greater than or equal to three dollars C is the call price
measured in dollars.
CL is a measure of the liquidity of the option and equals the average time in minutes between transactions during the
day for the call.
T is the maturity of the call in days.
CR is a measure of the relative risk of the call and equais the squared delta for the call computed from the
Black-Scholes formula.
risk free rate

事件型因子
交易频率

时间型因子
滞后的spread等（后期再加，这个因子太变态了，并且容易过拟合，模型只根据这个因子给出下一期的spread）
前一段windows的rv
日期dummy，例如周一、周二

同类型标相关因子
Weighted price standard deviation of the trades
期权组合的特征
如股指期货的spread
syn期货的spread
同strike c和p互相作为因子
同counterpart的moneyness（如对于p来说，是1/moneyness_c的期权的spread，moneyness_p==1/moneyness_c）

LOB因子
不同模型，可以用一些复杂的模型，只要效果好，但最好可解释

法1：直接对spread进行回归
法2：参考`Effective Bid-Ask Spreads in Futures versus Futures Options.pdf`
，先预测iv，在通过bs得到预测的价格，和真实价格作差*2得到spread，并用时间对这个值进行回归，从而排除掉tick级的滞后性带来的估计偏差
对因子也可以进行回归从而去除一些噪声

价差结构
十点半后可能alpha不变
etf和股指期货相关性非常高，syn的相关性也非常高

## 模型

需要训练 t2m（近月远月近季月远季月）\* moneyness（ITM ATM OTM）\* c\/p = 4\*3\*2 = 24种模型，然后在train上（一个完整的存续周期）训练

[//]: # (仅用于y=ax+b形式的回归，即无法使用因子来建模，而是在time-spread的图上拟合出一个曲线)
wing model
spline model

[//]: # (需要确认是否对yrobust)
- robust linear model
- 需要有某些可调参数来方便的修改模型从而适应不同的市场行情。开盘不久，spread会快速下降，此时主要是time2maturity在变，因此或许该阶段time2maturity需要有较大的coef。是否可以通过dummy来构造这个
- 调整系数alpha可能可以是个时变的

## todo

- ema平滑
- 查看某个期权生命周期内的spread变化
- 查看某个strike不同mat的spread变化
- 能否训练一个统一的模型能够适配不同期权合约
- 至少覆盖一个到期周期
- event因子
- 机器学习模型，日度滚动训练？？

## steps

1. 计算syn期货价格，不同strike期权的c和p可以计算不同syn的期货。因此可以通过这个syn的价格通过bs反推出期权的iv，也可以用它去校准市场交易出来的r和\tau（不同公司的r不同，大资金方和普通券商会有不同的r，不能简单地拿无风险利率来算）
2. 不光要考虑r2，也要考虑方差的被解释对象（好像就是r2）。应该用adj r2

## 已解决问题

1. 最终的标的有哪些?：50、300、500
2. 不同mat不同moneyness不同时间段有不同的规律（同一个时间段不同Option的spread特点 同一个Option不同时间的spread特点，包括日内和日间）
3. 研究spread/price好还是直接spread
4. 分红怎么考虑？不考虑. 给的数据集是2023-08-01~2023-10-31，在这期间没有分红，因此也没有期权调整。

## 问题

data
1. 降频？

factors
1. 利率用对应期限的国债收益率，日度?
2. 校对syn/iv/greeks
3. t2m 244
4. 计算moneyness用etf价格还是syn价格，论文用syn，这两者是否有优劣？syn可以做空. 回归中可以用到syn_spread吗
5. 离群点怎么处理？丢掉。怎么样的算是离群点？按照时间切分/按照标准差切分？需要对每天时间段进行切分，怎么切比较好，切多少切多细比较好 5min 0935 1129 1301 1450
6. （和当前任务不相关，由于您给的数据集是2023-08-01~2023-10-31，在这期间没有分红，因此也没有期权调整。）分红修正以后，一般spread会有什么变化，M和A的期权是否有直接联系
7. 需要关注开盘集合竞价阶段吗？后期优化
8. 是否能参考“Effective Bid-Ask Spreads in Futures versus Futures
   Options.pdf”中的方法，先用bs计算iv，然后跑回归将模型归因到几个主要影响因素上（moneyness、maturity、t的dummy、c/p的dummy），并且对iv取log从而去除non-normality
9. 我们的具体交易费用有多少，返佣有多少，保证金比例（网上查）。199x年美国是19cents。AA返佣是5毛，A是3毛


平滑spread，不能来回波动

## 其他

- spearman和kendall都是秩相关性，Kendall更保守，可以捕获非线性相关性。通过该相关性筛选的因子可以用于含有非线性的神经网络等模型
- pearson关注于线性相关性，在线性回归时参考意义较大
- 上午spread较下午宽有可能是私募报撤单用完
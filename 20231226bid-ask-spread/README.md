
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


对于第二个课题内容比较单薄这个问题，我觉得可以尽量将逻辑缘由讲清楚，可以简单做一下相关内容的survey，然后在之后的模型中有目的地涉及其中部分idea；我对可扩充的内容想了一下，在日内spread规律之外，可能可以加入：
1. 时间维度：历史上bid-ask spread的统计、同一个期权存续期内spread 的变化
2. 期权维度：针对每个期权可以涉及更精细化的建模，每个期权可以通过别的期权的一些特征来进行建模
3. 模型维度：在linear之外，加入另外一些lasso、rf这些仍具有较高可解释性的模型，并可以用cross-validation、grid-search等方式计算aic bic挑选最优超参等


模型：
- GMM GeneralizedMethodofMoments广义矩估计


结果呈现：
可以参考[Business Fin   Account - 2003 - Abhyankar - Bid‐ask Spreads  Trading Volume and Volatility  Intra‐day Evidence from the...](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/高频/日内规律/bid-ask spread/Business Fin   Account - 2003 - Abhyankar - Bid‐ask Spreads  Trading Volume and Volatility  Intra‐day Evidence from the.pdf)



相关论文：
- [最优买卖一档价格之外的信息](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/高频/日内规律/bid-ask spread/American J Agri Economics - 2019 - Arzandeh - Price Discovery in Agricultural Futures Markets  Should We Look beyond the.pdf)，可能可以帮助建模，甚至预测
- Compound Hawkes Process


争议点：
流动性风险溢价？
之情交易？

## todo

成本型因子

share price, return volatility, and the average time between trades (the determinants
of the inventory-holding premium) together with the inverse of trading volume and
the modified Herfindahl index as the determinants of spread.
CBA denotes the call bid-ask spread measured in dollars.CDUM is a dummy variable that equals one if the call price is greater than or equal to three dollars
                C is the call price measured in dollars.
                CL is a measure of the liquidity of the option and equals the average time in minutes between transac.
                tions during the day for the call.
                T is the maturity of the call in days.CR is a measure of the relative risk of the cail and equais the squared delta for the cal! computed from
                the Black-Scholes formula.

事件型因子


时间型因子

同类型标相关因子（如股指期货的spread)


法1：直接对spread进行回归
法2：参考`Effective Bid-Ask Spreads in Futures versus Futures Options.pdf`，先预测iv，在通过bs得到预测的价格，和真实价格作差*2得到spread，并用时间对这个值进行回归，从而排除掉tick级的滞后性带来的估计偏差

## steps

1. 计算syn期货价格，不同strike期权的c和p可以计算不同syn的期货。因此可以通过这个syn的价格通过bs反推出期权的iv，也可以用它去校准市场交易出来的r和\tau（不同公司的r不同，大资金方和普通券商会有不同的r，不能简单地拿无风险利率来算）
2. 不光要考虑r2，也要考虑方差的被解释对象（好像就是r2）。应该用adj r2

## 问题

1. 我们的具体交易费用有多少，返佣有多少，保证金比例（网上查）。199x年美国是19cents
2. 需要对每天时间段进行切分，怎么切比较好，切多少切多细比较好
3. 是否能参考“Effective Bid-Ask Spreads in Futures versus Futures Options.pdf”中的方法，先用bs计算iv，然后跑回归将模型归因到几个主要影响因素上（moneyness、maturity、t的dummy、c/p的dummy），并且对iv取log从而去除non-normality
4. 期权bs倒推的iv和syn期货的vol的区别（todo，先自己通过文章搞清楚）
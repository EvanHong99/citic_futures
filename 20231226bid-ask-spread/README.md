# research on bid-ask spread

## Ŀ��
- �г��۲���۸�/����ʱ��/delta/vega/��ʵֵ�̶ȵĹ�ϵ��
- �г���ʲô�ṹ�ڱ��ۣ�ϣ��ÿ�����۶����ȡ�
- �ն�ѵ��ģ�ͣ�test��ÿһ��ÿ����Ȩ��train�϶�Ӧ�ĵĽ���һ��һѵ�����գ��������߼�������������train��ѵ��һ��ͳһ��ģ�ͣ���ttm���̻�ʱ������
- ���ڲ�ͬ��Ȩ�ļ۲�ṹ��ͼ��Ϊ���
- �۲졢ͳ�ơ���ģ��ͬһ����Լ�Ĵ�������spread�ı仯
- �۲졢ͳ�ơ���ģ��ͬһ���������ڲ�ͬ��Լ����ʲô���ļ۲�ṹ
- ������ĵ���ϵ������Ϊ���ٱȽϺ�
- ���ڲ�ͬ��Ȩ�ļ۲�ṹ��ͼ��Ϊ���


�����һ�㲻��ȥȷ���Եı�n��
��ͬ��Ȩ��ͳһ������������г��ۿ��ԱȽϴ󣬿ɽ����ԣ���Ҫ�ںС����������ͨ��moneyness��ͳһ��
һ��֮���зֿ����зֳɺü���ģ��
��ͬʱ��ά�ȡ���ͬ��ļ۸񲨶�����ͬgreeks��ֱ�ӳ��Ը��۸�ٷֱȡ���ͬƷ��֮��������
�������ڵ������ԣ���������mat���ڵı仯���۲���ܴ���������
���ܱȽ����ü۸�İٷֱ�
ͬһ����Ȩ��������������spread����ʲô�仯����
��������ʱ��spread�����𱨼ۻ�����

���ڵڶ����������ݱȽϵ���������⣬�Ҿ��ÿ��Ծ������߼�Ե�ɽ���������Լ���һ��������ݵ�survey��Ȼ����֮���ģ������Ŀ�ĵ��漰���в���idea���ҶԿ��������������һ�£�������spread����֮�⣬���ܿ��Լ��룺

1. ʱ��ά�ȣ���ʷ��bid-ask spread��ͳ�ơ�ͬһ����Ȩ��������spread �ı仯
2. ��Ȩά�ȣ����ÿ����Ȩ�����漰����ϸ���Ľ�ģ��ÿ����Ȩ����ͨ�������Ȩ��һЩ���������н�ģ
3. ģ��ά�ȣ���linear֮�⣬��������һЩlasso��rf��Щ�Ծ��нϸ߿ɽ����Ե�ģ�ͣ���������cross-validation��grid-search�ȷ�ʽ����aic
   bic��ѡ���ų��ε�

ģ�ͣ�

- GMM GeneralizedMethodofMoments����ع���

������֣�
���Բο� [Business Fin   Account - 2003 - Abhyankar - Bid�\ask Spreads  Trading Volume and Volatility  Intra�\day Evidence from the...](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/��Ƶ/���ڹ���/bid-ask spread/Business Fin Account - 2003 - Abhyankar - Bid�\ask Spreads Trading Volume and Volatility Intra�\day Evidence from the.pdf)
������Сֵspread����ʲô����ͳ�ƹ��ɣ�
һ��ʲôʱ��spread��������һ��ģ�Ϳ��ŵķ�Χ�ڣ���ģ��ʲôʱ����Ա�����
ͬһ��ʱ��β�ͬOption��spread�ص�
ͬһ��Option��ͬʱ���spread�ص㣬�������ں��ռ�
���Ի���άɢ��ͼ��moneyness��mat��spread
һ���ڵ�ÿ�������Ƿ��й���

������ģ�

- [��������һ���۸�֮�����Ϣ](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/��Ƶ/���ڹ���/bid-ask
  spread/American J Agri Economics - 2019 - Arzandeh - Price Discovery in Agricultural Futures Markets Should We Look
  beyond the.pdf)�����ܿ��԰�����ģ������Ԥ��
- Compound Hawkes Process

����㣺
�����Է�����ۣ�
֮�齻�ף�

## ����




## ����
y
- [x] Percentage spread
- [x] spread
- [ ] y���Ը�Ϊvolume weighted bid ask spread�����̿ڽ�Ϊ1��tickʱ��ô�죩

static
- [x] call price, call options price = mid-quote of bid-ask spread
- [x] time to maturity
- [x] Time to maturity2
- [x] delta. �Ƿ���Ҫ����c��p. �Ѿ����ְ���moneyness����Ϣ������������֣�����Ҫ�����Ƕ�ת��Ϊ��ֵ��������dummy����ʶdelta�������ŵ���Ϣ
- [x] implied volatility
- [x] moneyness�� �Ƿ���Ҫ����c��p��Using moneyness measured as the forward stock price divided by the strike price, we
   expect that the more out-of-the-money is the option, the bigger will be the percentage spread since those options
   provide the most leverage. For a call option, moneyness>1 means that the option is in the money, For a put option,
   moneyness>1 means that the option is out of the money,
- [x] moneyness2�� �Ƿ���Ҫ����c��p
- [x] moneyness * time to maturity�� �Ƿ���Ҫ����c��p
- [x] moneyness * delta�� �Ƿ���Ҫ����c��p

dynamic
- [x] duration = average duration for 10 transactions
- [x] duration2
- [x] volume = average volume for 10 transactions

cross-market
- [x] percentage spread of stocks/etf/��ָ�ڻ�/syn�ڻ�����Բ�ͬ��Ԥ��Ŀ����е���
- [x] spread of stocks/etf/��ָ�ڻ�/syn�ڻ�����Բ�ͬ��Ԥ��Ŀ����е���

dummies
- [x] ��������ʶ�����翪�̡����翪�̵�dummy
- [x] tick size��������Ȩ�г�����ֻ��-0001
- [ ] �ñ�Ĳ����ʼ��ٱ仯��ʱ���ƽ��ʱ������Ϊ����
- 

ע�⣺
- [x] ����ͬʱ����ask1_c/bid1_c������ֱ�Ӽ����y������
- [x] cross-options markets. ͬmat��strike��c��p��������ʵ���зǳ���Ĳ��죬��˲��ʺ���Ϊ����


�۲�ĵ��ԡ�б�ʡ��޷������ʣ�����ɱ���������Ƶ�ʡ��ɽ���volume������˵û��̫�����ã�

�ɱ�������
share price,
return volatility,
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

�¼�������
����Ƶ��

ʱ��������
�ͺ��spread�ȣ������ټӣ��������̫��̬�ˣ��������׹���ϣ�ģ��ֻ����������Ӹ�����һ�ڵ�spread��
ǰһ��windows��rv
����dummy��������һ���ܶ�

ͬ���ͱ��������
Weighted price standard deviation of the trades
��Ȩ��ϵ�����
���ָ�ڻ���spread
syn�ڻ���spread
ͬstrike c��p������Ϊ����
ͬcounterpart��moneyness�������p��˵����1/moneyness_c����Ȩ��spread��moneyness_p==1/moneyness_c��

LOB����
��ͬģ�ͣ�������һЩ���ӵ�ģ�ͣ�ֻҪЧ���ã�����ÿɽ���

��1��ֱ�Ӷ�spread���лع�
��2���ο�`Effective Bid-Ask Spreads in Futures versus Futures Options.pdf`
����Ԥ��iv����ͨ��bs�õ�Ԥ��ļ۸񣬺���ʵ�۸�����*2�õ�spread������ʱ������ֵ���лع飬�Ӷ��ų���tick�����ͺ��Դ����Ĺ���ƫ��
������Ҳ���Խ��лع�Ӷ�ȥ��һЩ����

�۲�ṹ
ʮ�������alpha����
etf�͹�ָ�ڻ�����Էǳ��ߣ�syn�������Ҳ�ǳ���

## ģ��

��Ҫѵ�� t2m������Զ�½�����Զ���£�\* moneyness��ITM ATM OTM��\* c\/p = 4\*3\*2 = 24��ģ�ͣ�Ȼ����train�ϣ�һ�������Ĵ������ڣ�ѵ��

[//]: # (������y=ax+b��ʽ�Ļع飬���޷�ʹ����������ģ��������time-spread��ͼ����ϳ�һ������)
wing model
spline model

[//]: # (��Ҫȷ���Ƿ��yrobust)
- robust linear model
- ��Ҫ��ĳЩ�ɵ�������������޸�ģ�ʹӶ���Ӧ��ͬ���г����顣���̲��ã�spread������½�����ʱ��Ҫ��time2maturity�ڱ䣬��˻���ý׶�time2maturity��Ҫ�нϴ��coef���Ƿ����ͨ��dummy���������
- ����ϵ��alpha���ܿ����Ǹ�ʱ���

## todo

- [ ] ��colab�ϣ�yӦ�ð���spread��percentage spread��
- 
## steps

1. ����syn�ڻ��۸񣬲�ͬstrike��Ȩ��c��p���Լ��㲻ͬsyn���ڻ�����˿���ͨ�����syn�ļ۸�ͨ��bs���Ƴ���Ȩ��iv��Ҳ��������ȥУ׼�г����׳�����r��\tau����ͬ��˾��r��ͬ�����ʽ𷽺���ͨȯ�̻��в�ͬ��r�����ܼ򵥵����޷����������㣩
2. ����Ҫ����r2��ҲҪ���Ƿ���ı����Ͷ��󣨺������r2����Ӧ����adj r2������ģ�͸��Ӷȶ�r2����������ģ��Խ����r2һ����˵Խ�ߣ����ǿ��ܻ����ϣ������adj r2����������

## �ѽ������

- ���յı������Щ?��50��300��500
- ��ͬmat��ͬmoneyness��ͬʱ����в�ͬ�Ĺ��ɣ�ͬһ��ʱ��β�ͬOption��spread�ص� ͬһ��Option��ͬʱ���spread�ص㣬�������ں��ռ䣩
- �о�spread/price�û���ֱ��spread
- �ֺ���ô���ǣ�������. �������ݼ���2023-08-01~2023-10-31�������ڼ�û�зֺ죬���Ҳû����Ȩ������
- t2m 244
- �����ö�Ӧ���޵Ĺ�ծ�����ʣ��ն�?
- У��syn/iv/greeks����ʱ���ã����ҶԱȹ�������Դ��greeks��
- ��Ⱥ����ô������������ô����������Ⱥ�㣿����ʱ���з�/���ձ�׼���з֣���Ҫ��ÿ��ʱ��ν����з֣���ô�бȽϺã��ж����ж�ϸ�ȽϺ� 5min 0935 1129 1301 1450
- ��Ҫ��ע���̼��Ͼ��۽׶��𣿺����Ż�
- ���ǵľ��彻�׷����ж��٣���Ӷ�ж��٣���֤����������ϲ飩��199x��������19cents��AA��Ӷ��5ë��A��3ë�� ���ǿ��Խ������Ѻ��Բ���
- �ع��п����õ�syn_spread�𣿿��ԣ�������������ʵ��syn spread������ӳ��Option spread�����Ի����ף����Ǳ���
- ���͵�ǰ������أ��������������ݼ���2023-08-01~2023-10-31�������ڼ�û�зֺ죬���Ҳû����Ȩ���������ֺ������Ժ�һ��spread����ʲô�仯��M��A����Ȩ�Ƿ���ֱ����ϵ��ûɶ�仯��һ����A�Ʋֵ�M
- �Ƿ��ܲο���Effective Bid-Ask Spreads in Futures versus Futures Options.pdf���еķ���������bs����iv��Ȼ���ܻع齫ģ�͹��򵽼�����ҪӰ�������ϣ�moneyness��maturity��t��dummy��c/p��dummy�������Ҷ�ivȡlog�Ӷ�ȥ��non-normality�����ڸ��ӣ�֮����˵
- ����moneyness��etf�۸���syn�۸�������syn���������Ƿ������ӣ�syn��������. �����õ�ETF�۸񣨸о����Ǳ�ıȽϣ�
- ��ô�ж�ATM��ETF�۸���syn�۸�. ��ETF���Եģ�ƫ��ǳʵֵ
- ���������train test���Ƚϣ�Ч��һ�� �������ĳһ�죨����ǰ5�죩��������Ȩ�ֲ������ơ���������ն�train��test��Ӧ��ģ�����Ŷ���һЩ��Լ��vega delta moneyness�Ƚ��ȶ�����������Ԥ�⣻�նȹ���Ҳ�У���������ϣ�ʱ��Խ�ñȽϺù�����


## ����


���Ǹ���עʲô�㣿
- �����ATM��spread�����ܱ�һ��tick��
- �����Ҫ�Ա��۱ȽϿ�Ĳ�Ʒ���ж�spread����ô��һ���Ѷ�
- ����spread�ṹ

## ����

- pearson��ע����������ԣ������Իع�ʱ�ο�����ϴ�
- spearman��kendall����������ԣ�Kendall�����أ����Բ������������ԡ�ͨ���������ɸѡ�����ӿ������ں��з����Ե��������ģ��
- ����spread��������п�����˽ļ����������

# research on bid-ask spread

�г��۲���۸�/����ʱ��/delta/vega/��ʵֵ�̶ȵĹ�ϵ��
�����һ�㲻��ȥȷ���Եı�n��
��ͬ��Ȩ��ͳһ������������г��ۿ��ԱȽϴ󣬿ɽ����ԣ���Ҫ�ں�
һ��֮���зֿ����зֳɺü���ģ��
delta vega ��ϵ���۲�ĵ��ԡ�б�ʡ��޷������ʣ�����ɱ���������Ƶ�ʡ��۸�̶���percentage���ɽ���volume������˵û��̫�����ã�
��ͬʱ��ά�ȡ���ͬ��ļ۸񲨶�����ͬgreeks��ֱ�ӳ��Ը��۸�ٷֱȡ���ͬƷ��֮��������
�������ڵ������ԣ���������mat���ڵı仯���۲���ܴ���������
�г���ʲô�ṹ�ڱ��ۣ�ϣ��ÿ�����۶����ȡ�
���ܱȽ����ü۸�İٷֱ�
ͬһ����Ȩ��������������spread����ʲô�仯����


���ڵڶ����������ݱȽϵ���������⣬�Ҿ��ÿ��Ծ������߼�Ե�ɽ���������Լ���һ��������ݵ�survey��Ȼ����֮���ģ������Ŀ�ĵ��漰���в���idea���ҶԿ��������������һ�£�������spread����֮�⣬���ܿ��Լ��룺
1. ʱ��ά�ȣ���ʷ��bid-ask spread��ͳ�ơ�ͬһ����Ȩ��������spread �ı仯
2. ��Ȩά�ȣ����ÿ����Ȩ�����漰����ϸ���Ľ�ģ��ÿ����Ȩ����ͨ�������Ȩ��һЩ���������н�ģ
3. ģ��ά�ȣ���linear֮�⣬��������һЩlasso��rf��Щ�Ծ��нϸ߿ɽ����Ե�ģ�ͣ���������cross-validation��grid-search�ȷ�ʽ����aic bic��ѡ���ų��ε�


ģ�ͣ�
- GMM GeneralizedMethodofMoments����ع���


������֣�
���Բο�[Business Fin   Account - 2003 - Abhyankar - Bid�\ask Spreads  Trading Volume and Volatility  Intra�\day Evidence from the...](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/��Ƶ/���ڹ���/bid-ask spread/Business Fin   Account - 2003 - Abhyankar - Bid�\ask Spreads  Trading Volume and Volatility  Intra�\day Evidence from the.pdf)



������ģ�
- [��������һ���۸�֮�����Ϣ](/Users/hongyifan/Desktop/work/internship/FinancialEngineeringHub/��Ƶ/���ڹ���/bid-ask spread/American J Agri Economics - 2019 - Arzandeh - Price Discovery in Agricultural Futures Markets  Should We Look beyond the.pdf)�����ܿ��԰�����ģ������Ԥ��
- Compound Hawkes Process


����㣺
�����Է�����ۣ�
֮�齻�ף�

## todo

�ɱ�������

share price, return volatility, and the average time between trades (the determinants
of the inventory-holding premium) together with the inverse of trading volume and
the modified Herfindahl index as the determinants of spread.
CBA denotes the call bid-ask spread measured in dollars.CDUM is a dummy variable that equals one if the call price is greater than or equal to three dollars
                C is the call price measured in dollars.
                CL is a measure of the liquidity of the option and equals the average time in minutes between transac.
                tions during the day for the call.
                T is the maturity of the call in days.CR is a measure of the relative risk of the cail and equais the squared delta for the cal! computed from
                the Black-Scholes formula.

�¼�������


ʱ��������

ͬ���ͱ�������ӣ����ָ�ڻ���spread)


��1��ֱ�Ӷ�spread���лع�
��2���ο�`Effective Bid-Ask Spreads in Futures versus Futures Options.pdf`����Ԥ��iv����ͨ��bs�õ�Ԥ��ļ۸񣬺���ʵ�۸�����*2�õ�spread������ʱ������ֵ���лع飬�Ӷ��ų���tick�����ͺ��Դ����Ĺ���ƫ��

## steps

1. ����syn�ڻ��۸񣬲�ͬstrike��Ȩ��c��p���Լ��㲻ͬsyn���ڻ�����˿���ͨ�����syn�ļ۸�ͨ��bs���Ƴ���Ȩ��iv��Ҳ��������ȥУ׼�г����׳�����r��\tau����ͬ��˾��r��ͬ�����ʽ𷽺���ͨȯ�̻��в�ͬ��r�����ܼ򵥵����޷����������㣩
2. ����Ҫ����r2��ҲҪ���Ƿ���ı����Ͷ��󣨺������r2����Ӧ����adj r2

## ����

1. ���ǵľ��彻�׷����ж��٣���Ӷ�ж��٣���֤����������ϲ飩��199x��������19cents
2. ��Ҫ��ÿ��ʱ��ν����з֣���ô�бȽϺã��ж����ж�ϸ�ȽϺ�
3. �Ƿ��ܲο���Effective Bid-Ask Spreads in Futures versus Futures Options.pdf���еķ���������bs����iv��Ȼ���ܻع齫ģ�͹��򵽼�����ҪӰ�������ϣ�moneyness��maturity��t��dummy��c/p��dummy�������Ҷ�ivȡlog�Ӷ�ȥ��non-normality
4. ��Ȩbs���Ƶ�iv��syn�ڻ���vol������todo�����Լ�ͨ�����¸������
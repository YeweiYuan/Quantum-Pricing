**量子风险分析**

​		使用量子振幅估计来对证券定价，在基于门的量子计算机上评估诸如在险价值和条件在险价值之类的风险度量。

定价问题 二次加速 BSM VaR  蒙特卡罗 欧式期权 美式期权 亚式期权

- **布朗运动**

  价格为随机布朗运动

  ![image-20200928183247338](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200928183247338.png)

- **Black-Scholes-Merton（BSM）模型**

  ​		模型包含两类资产，股票（有风险）和债券（无风险）

  ​		有风险（1）：

  ![image-20200928234621012](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200928234621012.png)

  ​		dS/dt = S($\alpha$+$\sigma$dW/dt)  ，边界S0

  

  ​		无风险（2）：

  ![image-20200928234655586](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200928234655586.png)

  ​		相当于增量 = 基数* 利率* 时间

  ​		模型假设参数为常量，资产可连续自由买卖

  ​		解方程（1）

  ![image-20200929002810538](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200929002810538.png)

  ​		解方程（2） 

  ![image-20200929002840518](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200929002840518.png)

- **欧式看涨期权**

  ​		欧洲看涨期权赋予期权的所有者以预定的价格K在时间T≥0时购买股票的权利。

  ![image-20200929165845460](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200929165845460.png)

  ​		其中K为行使价，T为到期日。定价假设不套利，折后资产是鞅过程，未来期望值为股票价格本身。Q: 概率测度

  ![image-20200930154956407](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200930154956407.png)

  ​		结论1：

  ![image-20200930160238509](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200930160238509.png)

  

- **Value at Risk (VaR) and Conditional Value at Risk(CVaR)**

  ​		**VaR**(Value at Risk)按字面解释就是“在险价值”，其含义指：在市场正常波动下，某一金融资产或证券组合的最大可能损失。更为确切的是指，在一定概率水平（置信度）下，某一金融资产或证券组合价值在未来特定时期内的最大可能损失。

  > $VaR_α(X)=−inf\{t∣F_X(t)≥α\}$

  > $VaR_α(X)=−inf\{t∣Pr(x≤t)≥α\}$

  ​		**CVaR**(conditional value at risk)表示金融产品在既定置信水平α下，损失超过 VAR 的**期望损失**

  > $CVaR_α=−\frac{\int_{0}^{α}{VaR_r(X)}dr}{α}$

  ​		当在分析方法中计算风险价值（VAR）时，我们需要假设金融工具的返回遵循一定的概率分布。最常用的是**正态分布**，这也是为什么我们通常称它为delta normal方法。要计算VAR，我们需要找到一个阈值（T），来确定显著性（如95%、99%、99.9%）。使用函数F的标准正态累计分布：![img](https://img-blog.csdn.net/2018040812433190?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1B5RGFycmVu/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

  ​		将逆累积分布函数应用到1-α：

![img](https://img-blog.csdn.net/20180408124345528?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1B5RGFycmVu/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- **历史模拟法**

  ​		计算风险价值最简单的方法是历史模拟法。这里需要假设金融工具的历史回报率等于期望回报率。因此，我们需要找到α值部分的阈值。在统计中，这被称为百分数。例如，如果我们使用95%显著水平的VAR，那么它意味着数据集中较低第五百分位数。

- **蒙特卡罗定价**

  ​		欧洲期权取决于资产价格在未来的某个时间。如果非线性函数是分段线性，该期权可以进行可分析的定价。多个独立的布朗过程动态，价格通常也可以确定分析地。如果收益函数是非线性的，而不是分段线性的，或者在诸如不同资产价格是相关的情况需要蒙特卡罗模拟。美式期权最佳停止问题也要用蒙特卡罗方法。亚式期权同。
  
  ​		假设风险中性概率分布已知或可以从市场变量获取。对分布采样并计算收益。取多个(k)样本平均收益可得近似。
  
  ​		切比雪夫不等式
  
  ![image-20200930234843739](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200930234843739.png)
  
  ​		希望右边->O(1),
  
  ​		![image-20200930234943775](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20200930234943775.png)
  
  ​		得到K树，使用量子算法可以进行二次加速，分母变为一次。

- **量子蒙特卡罗**

  ​		首先是测量期望值。

  ![image-20201001025233186](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001025233186.png)

  ​		假设可以完成一个旋转在伴随qubit上

  ![image-20201001025434218](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001025434218.png)

  ​		过程：

  ![image-20201001033707690](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001033707690.png)

  ​	    测量伴随qubit， 得到1的概率即为期望

  ![image-20201001034020469](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001034020469.png)

  ​		这个概率通过t次重复过程得到的频率得到

  ![image-20201001034824234](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001034824234.png)

  ​		这是一个二次依赖。

  ​		把期望值和一个震荡量子系统的特征频率联系起来然后用其他自由度的作为探测解析特征频率。

  ​		![image-20201001162050170](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20201001162050170.png)

  

# Logistic Regression & Maximun Entropy 逻辑斯蒂回归 & 最大熵模型
## Logistic distribution    逻辑斯蒂分布
分布函数：  
$$F(x)=P(X\leq x)=\frac{1}{1+e^{-(x-\mu)/\gamma}}$$
密度函数：  
$$f(x)=F'(x)=\frac{e^{-(x-\mu)/\gamma}}{\gamma(1+e^{-(x-\mu)/\gamma})^2}$$
$\mu$是位置参数, $\gamma>0$为形状参数
***
## Binomal logistic regression model    二项逻辑斯蒂回归模型
* 由条件概率$P(Y|X)$表示，形式为参数化的逻辑斯谛分布
* 
  $$P(Y=1|X)=\frac{exp(w\cdot x+b)}{1+exp(w\cdot x+b)}$$
  $$P(Y=0|X)=\frac{1}{1+exp(w\cdot x+b)}$$
  input: $x\in R^n$, output: $Y\in\{0,1\}$, para: $w\in R^n$, $b\in R$.  
  $w$: 权值向量, $b$: 偏置, $w\cdot x$: $w$和$x$的内积
* 几率(odds): 一件事发生概率为p, 则这件事的几率是$\frac{p}{1-p}$
  
  对数几率(log odds): 
    $$logit(p)=log\frac{p}{1-p}$$  
  对于逻辑斯蒂回归:
$$log\frac{P(Y=1|x)}{1-P(Y=1|x)}=w\cdot x$$
可知$Y=1$时的对数几率由输入x的线性函数表示，即逻辑斯蒂回归模型
***
## Model parameters estimation  模型参数估计
* 应用极大似然估计法估计参数
  $$P(Y=1|x)=\pi(x),\ P(Y=0|x)=1-\pi(x)$$
  似然函数：
  $$\prod_{i=1}^N [\pi(x_i)]^{y_i}[1-\pi(x_i)]^{1-{y_i}}$$
  对数似然函数: 
  $$
  \begin{aligned}
      L(w)&=\sum_{i=1}^N[y_ilog{\pi(x_i)}+(1-y_i)log(1-\pi(x_i))]\\
      &=\sum_{n=1}^N[y_ilog\frac{\pi(x_i)}{1-\pi(x_i)}+log(1-\pi(x_i))]\\
      &=\sum_{i=1}^N[y_i(w\cdot x_i)+log\frac{1}{1+exp(w\cdot x_i)}]\\
      &=\sum_{i=1}^N[y_i(w\cdot x_i)-log(1+exp(w\cdot x_i))]
  \end{aligned}
  $$
  对$L(w)$求极大值，得到$w$的估计值.
  这样问题就变成了以对数似然函数问题为目标函数的最优化问题。
* 逻辑斯蒂回归学习中通常采用**梯度下降法**和**拟牛顿法**。
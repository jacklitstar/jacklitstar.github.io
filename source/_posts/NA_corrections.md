---
title: 数值分析教材部分修正
date: 2024-12-30
categories: Learn
---
# Some corrections
- p91
4.3.1 少了一个等号: 未知多项式表示为 $p_n(x) = \sum_{i=0}^n c_i \phi_i(x)$
- p100
5.1.5 Richardson 外推法
$$L_{h/2}-L = C_1(h/2)^{\alpha_1}+C_2(h/2)^{\alpha_2}+\cdots$$

- p102
矩阵乘法等式右边应该为：
$$\begin{bmatrix}b-a\\\frac 1 2 (b^2-a^2)\\\vdots\\\frac 1{k+1}(b^{k+1}-a^{k+1})\end{bmatrix}$$

- p104
5.2.1 Newton-Cotes 通过引入变量替换 $x = a + th$，则有 $t = \frac{x-a}h,t\in [0,n]$. 
Newton-Cotes 求积系数分母缺少一个 $n$ , 应该为：$$C_{n,k} = \frac{(-1)^{n-k}}{k!(n-k)!n}\int_0^n\prod_{i=0,i\neq k}^n (t-i) dt,k=0,\ldots n$$

- p111
定理5.5，Gauss型求积公式(5.47)应该为: $$\int_a^b f(x)dx = \sum_{i=1}^n c_i f(x_i),\quad f(x)\in \mathbb{P}_{2n+1}$$
另外, p113 公式(5.50),(5.51) 有同样的问题, 积分公式右端应该为对 $f(x_i)$ 的求和,而不是对 $f(x)$  
<span style="color: red;">p.s. 另外, 本人认为 **定理5.5** 并不正确。Newton-Cotes方法适用于等距节点，其系数为等距节点所用，而Legendre正交多项式的零点并不是等距离的。正确的系数应该回到最原始的定义：$c_i = \int_a^b l_i(x)dx$</span>
- p112
推论5.3, 系数应为$\{c_i\}_{i=0}^n$ .
其证明中有些混乱, 出现了未定义的 $k$ , 以下为一种可能的修正:
证明: 不失一般性，只需证明 $c_0>0. $ 令 $f(x) = \sum_{j=1}^n (x-x_j)^2$, 则有：
$$f(x_i) = \begin{cases}0&i\neq 0\\ \sum_{j=1}^n (x_0 - x_j)^2 & i=0\end{cases}$$
因为 $f(x)\in \mathbb{P}_{2n}$ , 则求积公式精确成立，即有：
$$I(f) = \int_a^b \sum_{j=1}^n (x-x_j)^2dx =\sum_{i=0}^n c_i f(x_i) = c_0f(x_0) = c_0 \sum_{j=1}^n (x_0-x_j)^2$$
由 $$\sum_{j=1}^n (x_0-x_j)^2>0$$
以及$$\int_a^b \sum_{j=1}^n (x-x_j)^2dx >0$$
可得 $c_0>0$

- p119
因为有记号 $x_i$ 存在可能造成混乱，可以在 **定理6.1** 之前强调记号 $x_t, x_{tt}$ 定义为导数。 $x_t = \frac{dx}{dt}, x_{tt} = \frac{d^2x}{dx^2}$ 。

- p121 - 123
这里对局部截断误差 LTE 的定义有冲突，使用了两种定义。前面的定义（p121）中分母有步长 $\tau$ ，而后面定义相容性、稳定性、收敛性的时候（p123）使用了没有步长的定义。进而导致定理 6.2 的证明混乱。建议统一对局部截断误差的定义。
如果保留 p121 的定义，即$$\mathrm{T}_{\tau,i} = \frac{1}{\tau} \|x(t_{i+1})-x_{i+1}\|$$
此时 $p$ 阶相容定义为： $$\mathrm{T}_{\tau,i} = O(\tau^p)$$
那么就需要修改p123中对于相容性的定义。$p$ 阶相容定义为：$$\|x_i - x(t_i) - \tau\Phi(t_i,x(t_i))\| = O(\tau^{p+1})$$
进而修改 **定理6.2** 的证明。
证明：令 $e_i = \|x(t_i)-x_i\|$，则有：
$$
\begin{aligned}
e_{i+1} &= \|x(t_{i+1})-x_{i+1}\|\\
&= \|x(t_{i+1})-x_i-\tau\Phi(t_i,x_i)\|\\
&\leq\|x(t_{i+1})-x(t_i)-\tau\Phi(t_i,x(t_i))\|+\|\tau\Phi(t_i,x(t_i))-\tau\Phi(t_i,x_i)\|+\|x(t_i)-x_i\|\\
&\leq O(\tau^{p+1}) + (\tau L_\Phi+1)e_i
\end{aligned}
$$

- p129
第一排 $J(t)=\frac{\partial f}{\partial x}(t,\bar x(t))$ 中应该指出 $\bar x(t)$ 的意义是精确解。

- p130
稳定区域的示意图中坐标轴应该为 $\tau\lambda$ 而不是 $\lambda x$

- typos & minor errors:
    - p12 图 2.2 中 slope = $f'(x_n)$
    - p23-28 例题2.7,图2.7-2.9 Levenberg-Marquardt
    - p49 Lebesgue 常数
    - p60 RichardBurdenNumericalAnalysis 
    - p60 对于Chebyshev节点的 Lebesgue 常数
    - p74 Gram-Schmidt 正交化
    - p93 4(3) use $\sin$ instead of $sin$
    - p115 7(2) Richardson
    - p131 包括显示Runge-Kutta 方法



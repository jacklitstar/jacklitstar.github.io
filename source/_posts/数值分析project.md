---
title: 数值分析Project
date: 2024-01-09 22:00:00
categories: Learn
---

<center>

# 数值分析大作业 Remez 算法
### 2025年1月9日
</center>

## 算法介绍
Remez算法[2]由苏联数学家 Evgeny Yakovlevich Remez 于1934年提出。这是一个迭代型算法用来求解函数的多项式逼近问题。具体而言，它寻找在Chebyshev空间中 $L_\infty$ 度量下的多项式逼近。我们这里讨论n维Chebeyshev多项式在实连续函数闭区间上的问题。这是一个 minimax 问题，即最小化最大绝对误差。  
我们假设目标函数为 $f$, 逼近多项式为 $p_n$, 区间为 $[a,b]$,初始节点组 $a\leq x_0<x_1<\cdots<x_{n+1}\leq b$ (通常选为 Chebeyshev 节点)。  
算法的核心思想来源于 Chebyshev 震荡定理：如果 $p_n$ 是最佳一致逼近多项式，当且仅当 $f-p_n$ 存在至少 $n+2$ 个等高震荡最值点。即有 $p_n(x_i) - f(x_i) = (-1)^i E$ 。通过找到每个节点附近误差更大的节点并更新进行迭代计算。

## 算法步骤
1. 初始化节点，通常选取 Chebyshev 节点作为初始猜测。
2. 给定节点组 $\{x_i\}_{i=1}^{n+1}$ , 找出多项式 $p_n\in \mathbb{P}_n$ 和实数 $E$，使得$p_n(x_i) - f(x_i) = (-1)^i E$ 。 也就是解线性系统：$a_0 + a_1x_i+\cdots +a_nx_i^n-f(x_i)=(-1)^i E ,\; i= 0,1,\ldots, n+1$
3. 更新节点组：在每个 $x_i$ 附近用一个 $p_n(x_i) - f(x_i)$ 的局部极值点 $\hat x_i$ 代替，使得新节点的误差大于旧节点。
4. 检查停止准则。回到第二步迭代。

停止准则可以使用当最大残差和最小残差的距离小于给定值时停止。也可以使用当新节点与旧节点的差小于某个给定值时停止。另外设置保护准则避免算法无限运行，如最大迭代次数和最长运行时间。  
第三步更新节点组中这里采用了每一步都对所有 $n+2$ 个节点尝试更新。另一种办法是每一步只更新一个节点，使用轮巡的方式更新所有节点。

## 算法分析
### 初始节点的影响
初始节点选取 Chebyshev 节点，因为其具有较好的数值稳定性。在多项式插值中，使用Chebyshev节点插值的多项式具有 Lebesgue 常数：
$$\Lambda_n(X) \leq \frac 2 \pi \log(n+1)+1$$
在尝试使用等距节点的测试中，发现即使在$n$ 很小时也很容易就出现算法失败的情况。

### 计算复杂度
第二步解线性系统问题：
$$a_0 + a_1x_i+\cdots +a_nx_i^n-f(x_i)=(-1)^i E ,\; i= 0,1,\ldots, n+1$$
通常解一次方程的计算复杂度为 $O(n^3)$，但是这里可以降到 $O(n^2)$。[6]
如果迭代次数为 $k$，且忽略由 $x$ 计算 $f(x)$ 的复杂度，总体计算复杂度为 $O(kn^2)$

### $n$ 的大小的影响
测试目标函数：$f(x)=\sin(x^2)+2x^2 \cos(3x)$ ，区间 $[-1,1]$ 上使用 $n = 1,\ldots, 100$, maxError = 1e-6 , maxIter = 100 发现，在 $n = 1,\ldots,11$ 时，先达到maxIter，而当$11<n<41$ 时，先达到maxError。当$n>41$ 时，矩阵表现接近奇异造成计算困难。
$n$ | 达到精度 | 达到最大迭代次数
-|-|-
 1~11 |         0 |                1
12~40 |         1 |                0
41~ |         0 |                0

### 与其他算法的比较
1. 测试目标函数：$f(x)=\sin(x^2)+2x^2 \cos(3x)$，区间 $[-6,6]$ , $n=9$ , maxError = 1e-6, maxIter = 100。将Remez算法与Chebyshev节点上的插值做比较。

| 算法          | 运行时间 (秒)   | 最大误差       |
|---------------|----------------|----------------|
| Remez 算法    | 0.187685       | 0.145861       |
| 插值算法      | 0.000274       | 0.223516       |

![](/img/na1.png)

2. 目标函数 $f(x) = e^x$ 在 $[-1,1]$ 上的三次多项式逼近。与遗传算法和Chebyshev节点上的插值做比较。[3]
   
 | 算法          | 迭代步数   | 最佳逼近     |
|---------------|----------------|----------------|
| Remez 算法    |  7   |    0.005571    |
| 遗传算法    |   90  |   0.005663   |
| 插值算法      |      |  0.006549     |


## 代码实现
输入：$f,n,a,b$ 最大允许误差 maxError，最大迭代次数 maxIter 。  
输出：最佳一致逼近多项式，迭代次数。
```m
function [bestPolynomial, iter] = remesAlgorithm(f, n, a, b, maxError, maxIter)
    % 初始化
    x = chebyshevNodes(n+2, a, b);
    iter = 0;
    error = inf;
    
    % 迭代主体
    while (iter <= maxIter) && (error > maxError)
        pCoeffs = findPolynomial(f, x, n);
        p = @(x) polyval(pCoeffs, x);

        g = @(x) (f(x) - p(x));
        [xNew, error] = findExtrema(g, n, x, a, b);
        
        x = xNew;
        iter = iter + 1;
    end

    % 返回最佳一致逼近多项式和迭代次数
    bestPolynomial = p;
end


% 生成切比雪夫节点
function x = chebyshevNodes(n, a, b)
    k = 1:n;
    x = cos((2*k-1)*pi/(2*n));
    x = 0.5*(b-a)*x + 0.5*(b+a); 
end


%一致逼近多项式
function polynomial = findPolynomial(f,x,n)
    %用解线性方程组的方法 
    A = zeros(n+2, n+2);
    for i = 1:n+2
        for j = 1:n+1
            A(i, j) = x(i)^(n-j+1);
        end
    end
    A(1:n+2,n+2) = (-1).^(0:n+1)';
    b = f(x)';
    a = A\b;
    polynomial = a(1:n+1);
end

%节点的迭代
function  [Extrema,error] = findExtrema(f,n,points,a,b)
    Extrema = zeros(1,n+2);
    root = zeros(1,n+3);
    root(1) = a ; root(n+3) = b;

    %找到零点
    for i = 1:n+1
        root(n+3-i) = findzero(f,points(1,i),points(1,i+1));
    end

    %每个区间找到极值
    for i = 1:n+2
        Extrema(n+3-i) = fminbnd(@(x)-abs(f(x)),root(i),root(i+1));
    end
    error=max(f(Extrema))-min(f(Extrema));
end

%查找零点
function x0 = findzero(f,a,b)
    maxError = 1e-10;
    x0 = (a+b)/2;
    while (abs(f(x0))>maxError)
        if f(a)*f(x0) < 0
            b = x0;
        else
            a = x0;
        end
        x0 = (a+b)/2;
    end
end
```

测试：
```m
% 目标函数
f = @(x) sin(x.^2) + 2*x.^2 .* cos(3*x);

% 区间
a = -1;
b = 1;

% 参数设置
maxError = 1e-6; % 精度要求
maxIter = 100;   % 最大迭代次数

% 存储结果
results = zeros(100, 2); % 第一列记录是否达到精度，第二列记录是否达到最大迭代次数

% 测试 n 从 1 到 40
for n = 1:40
    % 运行 Remez 算法
    [bestPolynomial, iter] = remesAlgorithm(f, n, a, b, maxError, maxIter);
    
    % 检查是否达到精度
    xTest = linspace(a, b, 1000);
    error = max(abs(f(xTest) - bestPolynomial(xTest)));
    if error <= maxError
        results(n, 1) = 1; % 达到精度
    else
        results(n, 1) = 0; % 未达到精度
    end
    
    % 检查是否达到最大迭代次数
    if iter >= maxIter
        results(n, 2) = 1; % 达到最大迭代次数
    else
        results(n, 2) = 0; % 未达到最大迭代次数
    end
    n
end

% 输出结果
disp('n | 达到精度 | 达到最大迭代次数');
disp('-------------------------------');
for n = 1:100
    fprintf('%2d | %9d | %16d\n', n, results(n, 1), results(n, 2));
end

% 绘制结果
figure;
plot(1:100, results(:, 1), 'bo-', 'DisplayName', '达到精度');
hold on;
plot(1:100, results(:, 2), 'rx-', 'DisplayName', '达到最大迭代次数');
xlabel('多项式阶数 n');
ylabel('结果');
title('Remez 算法性能测试');
legend;
grid on;
```

```m
f = @(x) sin(x) + 0.1 * cos(10 * x);
n = 9;
a = -6;b = 6;
maxError = 1e-6;
maxIter = 100;
tic;
bestPolynomialRemez = remesAlgorithm(f, n, a, b, maxError, maxIter);
timeRemez = toc;

tic;
bestPolynomialInterp = findInterpolationPolynomial(f,n,a,b);
timeInterp = toc;

fprintf('Remez 算法的运行时间: %.6f 秒\n', timeRemez);
fprintf('插值算法的运行时间: %.6f 秒\n', timeInterp);
% 定义测试点
xTest = linspace(a, b, 1000);

% 计算 Remez 算法的误差
errorRemez = max(abs(f(xTest) - bestPolynomialRemez(xTest)));

% 计算插值算法的误差
errorInterp = max(abs(f(xTest) - bestPolynomialInterp(xTest)));

% 输出误差
fprintf('Remez 算法的最大误差: %.6f\n', errorRemez);
fprintf('插值算法的最大误差: %.6f\n', errorInterp);

% 绘制 Remez 算法的逼近结果
fplot(bestPolynomialRemez, [a, b], 'g');
hold on;

% 绘制插值算法的逼近结果
fplot(bestPolynomialInterp, [a, b], 'r');

% 绘制目标函数
fplot(f, [a, b], 'k--');
legend('Remez 算法', '插值算法', '目标函数');
title('算法比较');
grid on;
```

## 参考文献
[1] 数值分析教材.

[2] E.Ya. Remez, Sur le calcul effectiv des polynomes d’approximation des Tschebyscheff,
Compt. Rend. Acade. Sc. 199, 337 (1934).

[3] 张春涛,向瑞银,任友俊.遗传算法在数值逼近中的应用[J].重庆三峡学院学报,2010,26(03):27-29+71.DOI:10.13743/j.cnki.issn.1009-8135.2010.03.041.

[4] 吕致君.最优多项式一致逼近[J].山西大学学报(自然科学版),1980,(01):13-18.DOI:10.13451/j.cnki.shanxi.univ(nat.sci.).1980.01.003.

[5] M.J.D. Powell. Approximation theory and methods. Cambridge University
Press, United States of America, 1981

[6] Wikipedia contributors. "Remez algorithm." Wikipedia, The Free Encyclopedia. Wikipedia, The Free Encyclopedia, 16 Jul. 2024. Web. 9 Jan. 2025.

[7] de Groot, E. D. (2017). Finding best minimax approximations with the Remez algorithm (Bachelor's thesis). University of Groningen. Retrieved from https://fse.studenttheses.ub.rug.nl/id/eprint/15985

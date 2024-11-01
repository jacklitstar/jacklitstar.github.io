---
title: Machine Learning
date: 2024-10-05 21:00:00
categories: Learn
---
Notes on Machine Learning. 《机器学习》 周志华 清华大学出版社  
# 0  Maths
Matrix Calculus: [1](https://zhuanlan.zhihu.com/p/24709748), [2](https://zhuanlan.zhihu.com/p/24863977)  
$\bold x \in \mathbb{R^n},\; \bold y \in \mathbb{R^m},\;X \in \mathbb{R}^{m\times n},\;\bold f : \mathbb{R}^n\to \mathbb{R}^m,\; A,B,C\in \mathbb{R}^{n\times n}$
$$\frac{\partial\bold y}{\partial\bold x} \in \mathbb R^{m\times n}$$
$$d \bold f = \frac{\partial \bold f }{\partial \bold x}d\bold x$$
$$J=\nabla_{\bold x}\bold f = \frac{d \bold f}{d\bold x}\in \mathbb{R}^{m\times n}$$
$$d\mathrm{tr}(A)=\mathrm{tr}(dA)$$
$$d(AB)=d(A)B+Ad(B)$$
$$dA^T = (dA)^T$$
$$d\bold f = \sum_i\sum_j \frac{\partial d\bold f }{\partial x_{ij}}dx_{ij} = \mathrm{tr}\left((\frac{\partial \bold f }{\partial X})^TdX\right)$$
$$\frac{\partial \mathrm{tr}(f(x))}{\partial x} = \mathrm{tr}\left(\frac{\partial f(x)}{\partial x}\right)$$
$$\frac{\partial \mathrm{tr}(X^TX)}{\partial X}= 2X$$
$$\mathrm{tr}(ABC) = \mathrm{tr}(BCA)=\mathrm{tr}(CAB)$$
$$\mathrm{tr}(A^TB)=\sum\sum A_{ij}B_{ij}$$
**Frobenius Norm** :
$$\|X\|_F = (\mathrm{tr}(X^TX))^{1/2}=\left(\sum_{i=1}^m\sum_{j=1}^n X_{ij}^2\right)^{1/2}$$
Gradient of Least-Sqaures Loss in Linear Model: $\bold y = \Phi \theta,\; \theta\in \mathbb R^D\;, \Phi \in \mathbb{R}^{N\times D},\; \bold y \in \mathbb R^N$  
Define 
$$ e(\theta) = \bold y - \Phi \theta\qquad  L(e) = \|e\|^2$$
$$\frac{\partial L}{\partial \theta} = -2(\bold y -\Phi \theta)^T\Phi \in \mathbb R^{1\times D}$$


# 3 Linear Models
## 3.1
is learning a linear $\bold w$ and $b$:
$$f( \bold x )= \bold w^T\bold x+b $$
Linear models have good comprehensibility.
## 3.2 Linear Regression
Given a dataset $D = \{(\bold x_1,y_1),\ldots,(\bold x_m,y_m)\}$ 
Using MSE is basically solving Least Squares Problem.  
for a single variate: 
$$f(x_i)=wx_i+b\quad \text{let}\; f(x_i)\to y_i$$
the loss is: $y_i - f(x_i) = y_i-wx_i-b$  
Parameter estimation: calculate $\bold w ,\; b$ to minimize MSE: 
$$E_{(w,b)}=\sum_{i=1}^m(y_i-wx_i-b)^2$$
derivatives:
$$\frac{\partial E_{(w,b)}}{\partial w}=2\left(w\sum_{i=1}^mx_i^2-\sum_{i=1}^m(y_i-b)x_i\right)\\\frac{\partial E_{(w,b)}}{\partial b}=2\left(mb-\sum_{i=1}^m(y_i-wx_i)\right)$$
let the derivatives be 0 to find the **closed-form solution**:
$$w = \frac{\sum_{i=1}^my_i(x_i-\bar x)}{\sum_{i=1}^mx_i^2-\frac{1}{m}\left(\sum_{i=1}^mx_i\right)^2}$$
$$b=\frac{1}{m}\sum_{i=1}^m (y_i-wx_i)$$
see multivariate on book page 56.  
Generalized linear model: pluggin a good **link function** $g$ 
$$y=g^{-1}(\bold w^T\bold x+b)$$
## 3.3 Logit Regression
used as classifier. Apply **Sigmoid** function.   
**Logit** : log odds, the ratio of the possibility of correct vs incorrect.
Example on a binary cluster problem. Use the sigmoid function:
$$ y=\frac{1}{1+e^{-z} }$$
plug in the model's output : $z = f(\bold x) = \bold w^Tx + b$ 
$$ y=\frac{1}{1+e^{-(\bold w^Tx + b)} }$$
$\log$ it:
$$\ln \frac{y}{1-y}=\bold w^Tx+b$$
the odds here is :
$$\frac{p(y=1|x)}{p(y=0|x)} = \frac{y}{1-y}$$
the log odds **logit** is: 
$$\ln\frac{p(y=1|x)}{p(y=0|x)}=\ln \frac{y}{1-y}=\bold w^Tx+b$$
Using Maximum Likelihood Estimattion:
$$L(\bold w, b) = \prod_{i=1}^m p(y_i|\bold x_i)$$
$\log$ it getting a minimization problem **Minimum negative Log Likelihood**
$$\ell(\bold w, b) = -\sum_{i=1}^m \ln p(y_i|\bold x_i)$$

## 3.4 Linear Discriminant Analysis (LDA)
For a given training set, train the algorithm so that the projection of similar samples land close to each other, the projections of different samples lands apart from one another. It projects samples onto a singular line in vector space.  
Given a binary classification dataset $D=\{(\bold x_i,y_i)\}_{i=1}^m\quad y_i\in \{0,1\}$ , let $X_i, \bold\mu_i, \bold\Sigma_i$ be the sample set, average, covariance matrix of which set with property indexed after $i$.

Seems difficult, to be continued....

# 4 Decision Tree
# 4.1
A divide-and-conquer method
```python
input: Traning Set D, Properties Set A
TreeGenerate(D, A):
    Generate Node
    if "all samples in D are in the same class C" :
        Node.type = C
    if "A is empty" or "samples in D have the same property in A":
        Node.type = "most type in sample D"
        Node = old.leaf
    for a_star_v in a_star:
        Node.Create_Branch()
        if D_v.isEmpty():
            Branch = leaf
            Branch.type = "most types in D"
        else:
            TreeGenerate(D_v, A\{a_star})
```

# 4.2
How to choose the most best property distiguisher? Generally, we want the purity of each branch to be higher, that is branches should contain samples within the same class.  
**Information Entropy** quantifies purity in samples. Suppose in the sample $D$ the $k\text{th}$ kind of sample has a portion of $p_k$, the information entropy of $D$ is defined by:
$$ \mathrm{Ent}(D)= - \sum_{k=1}^{|\mathcal Y |}p_k\log_2p_k$$
The less the entropy, the more the purity.  
**Information Gain**
$$\mathrm{Gain}(D,a) = \mathrm{Ent}(D)- \sum_{v=1}^V \frac{|D^v|}{|D|}\mathrm{Ent}(D^v)$$
The more the Gain, the more that using property $a$ in dividing has a higher impact on improving purity.  
In practice, using Gain might have a preference in properties with more choices. To solve this uneveness, Quinlan introduced **Gain Ratio** :
$$\mathrm{Gain\_Ratio}(D,a) = \frac{\mathrm{Gain}(D,a)}{\mathrm{IV}(a)}\qquad \mathrm{IV}(a)=-\sum_{v=1}^V\frac{|D^v|}{|D|}\log_2\frac{|D^v|}{|D|} $$
$\mathrm{IV}$ is the **intrinsic value** of property $a$ . The more choices property $a$ have, the bigger $\mathrm{IV}$ will be.  

Classification and Regression Tree (CART) uses **Gini index** to choose dividing properties.
$$\mathrm{Gini}(D)= \sum_{k=1}^{|\mathcal Y|}\sum_{k'\neq k}p_kp_{k'}=1-\sum_{k=1}^{|\mathcal Y|}p_k^2$$
The less the Gini is, the higher the purity. 
For property $a$, the Gini Index is:
$$\mathrm{Gini\_Index}(D,a)=\sum_{v=1}^V\frac{|D^v|}{|D|}\mathrm{Gini}(D^v)$$

## 4.3 Pruning
**Pruning** is a method to counter overfitting. pre-pruning and post-pruning.
pre-pruning is pruning when generating the tree. If the new branch have negative effect on predictions, the branch is pruned. post-prunining is pruning after the tree is fully generated. If a branch does better when pruned, then it gets pruned.

## 4.4 Continous Properties and Missings


# 6 Support Vector Machine
## 6.1 
Using a hyperplane to classify datasets.
A **Support Vector** are points that lie around the hyperplane margin, they are the points that are hard to distinguish.  
Hyperplane :$w^Tx+b=0$  
The distance of a point to the hyperplane is 
$$ r = \frac{|wx+b|}{\|w\|} $$
The **Margin** :
$$\gamma=\frac{2}{\|w\|}$$
We want to maximize the margin, which is minimizing $\|w\|^2$. This is a **Convex Quadratic Progamming** problem.
$$\min_{w,b} \frac{1}{2}\|w\|^2\quad s.t. y_i(wx_i+b)\geq 1$$

## 6.2 KKT
Consider problem: $\min_x f(x)\quad s.t.\; g_i\leq 0, h_j(x) = 0, i=1,\ldots,m \quad j=1,\ldots,n$  
Using the Lagrangian:
$$L(x,\mu,\lambda) = f(x) + \sum_i \mu_ig_i(x)+ \sum_j\lambda_jh_j(x)$$
KKT conditions:
1. Stationary $$\nabla_xL=\nabla f(x^*) + \sum_{i=1}^{m} \mu_i \nabla g_i(x^*) + \sum_{j=1}^{n} \lambda_j \nabla h_j(x^*) = 0$$
2. Primal feasibility $$g_i(x^*)\leq 0 \;\forall i\qquad h_j(x^*) = 0 \; \forall j$$
3. Dual feasibility $$\mu_i\geq 0,\forall i$$
4. Complementary slackness $$\mu_ig_i(x^*)= 0\;\forall i$$

Using Lagrangian and applying KKT, the SVM problem is transformed into a **dual form**
$$\max_{\bold\alpha}\, \sum_{i=1}^m \alpha_i - \frac{1}{2}\sum_{i=1}^m\sum_{j=1}^m\alpha_i\alpha_j y_iy_jx_i^Tx_j\\s.t.\;\sum_{i=1}^m \alpha_iy_i=0 \; \alpha_i\geq 0$$
The Stationary Gradients conditions are applied during the process.  
**SMO** algorithm

## 6.3 Kernel Function
If the problem cannot be classifed in a low dimension space, there always exits a function $\phi(x)$ that maps to a higher dimension, ensuring that it can be classifed by superplane. Normally we use Hilbert Space. A kernel function computes the similarity (or inner product) between two data points in a higher-dimensional feature space without explicitly computing the coordinates of those points in that space. 
$$\kappa(x_i,x_j) = \phi(x_i) \phi(x_j) $$

## 6.4 Soft Margins
We allow the SVM to make some mistakes.

\[
\min_{w, b, \xi} \quad \frac{1}{2} \|w\|^2 + C \sum_{i=1}^{N} \xi_i
\]
Subject to:
\[
y_i (w \cdot x_i + b) \geq 1 - \xi_i \quad \text{for all } i
\]
\[
\xi_i \geq 0 \quad \text{for all } i
\]

Where:
\(w\) is the weight vector,
\(b\) is the bias term,
\(C\) is the regularization parameter,
\(\xi_i\) are the slack variables.

Given 3 coins A B C, the possibility of flipping heads are: $\pi ,p,q$  
Test: $$
A = \begin{array}{}
B & A \text{ is heads} \\
C & A \text{ is tails}
\end{array}
$$

Proj 7
proof chebyshev points : $$\|f-P_n\|\leq c\rho^{-n}$$ and $$lesbegue_n(X)\leq c\log n$$
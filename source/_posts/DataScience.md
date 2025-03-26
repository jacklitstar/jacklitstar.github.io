Notations:
- $\mathcal X$: input space
- $\mathcal Y$: output space
- $x \in \mathcal X$: input
- $y \in \mathcal Y$: output
- $d$: dimension of parameters
- $\Theta \subset \R^d$: parameter space 
- $\mathcal F$: function space
- $\theta$: parameters that controls the predictor $f$
- $\mathbb{P}$: the joint probabilty distribution of $X$ and $Y$ on $\mathcal X \times \mathcal Y : (X,Y) \sim \mathbb P$
- $f: \mathcal X \to \mathcal Y$: predictor
- $\hat f$: predictor based on the training set(sample)
- $f^* = \argmin \mathcal L (f)$: target function, the optimal predictor based on total set
- $f_0$: solution of the problem
- $\hat y = f(x)$: prediction of $x$
- $\ell(y, \hat y)$: loss function $\ell = \ell(y, \hat y),\, \mathcal{Y}\times \mathcal Y \to \R$
- $\mathcal L (\theta)$ or $\mathcal L (f)$: risk
- $\hat \theta$: empirical risk minimizer



## Set up for supervised learning
Empirical risk minimization:
The goal of supervised learning is to train models so to reliably predict the labels for any given input. A common measure of performance is called **misclassification rate** on the training set.
Given $N$ training samples $(X_1,Y_1), (X_2,Y_2), \cdots, (X_N,Y_N)$ where $(X_i,Y_i) \stackrel{iid}{\sim} \mathbb P$

$$\hat{\mathcal{L}} (\theta) = \frac 1 N \sum_{n=1}^N \mathbb{I}(Y_n \neq f(X_n ; \theta))$$

Most times the cost of misclassification are different for different classes, we replace the indicator function $\mathbb{I}$ by asymetric loss function $\ell(y, \hat y)$.

Definition: **Empirical Risk**  
The average loss of the predictor on the training set.
$$\hat{\mathcal{L}} (\theta) = \frac 1 N \sum_{n=1}^N \ell(Y_n, f(X_n ; \theta))$$

In order to find the best predictor, we need to find the parameters $\theta$ that minimizes the empirical risk.

Definition: **Empirical Risk Minimization**
The goal of empirical risk minimization is to find the predictor that has the smallest empirical risk.

$$\hat \theta = \arg \min_\theta \mathcal{L} (\theta)=\argmin_\theta \frac 1 N \sum_{n=1}^N \ell(Y_n, f(X_n ; \theta))$$

Notice that $f$ is a function of $\theta$, we can aquire the **Emperical Risk Minimizer**  or **ERM**:
$$\hat f = f(X ; \hat \theta)$$

or

$$\hat f \in \argmin_{f \in \mathcal F}\hat {\mathcal L} (f) =  \frac 1 N \sum_{n=1}^N \ell(Y_n, f(X_n ; \theta))$$

Empirical risk focus on the training set, when dealing with the **total set** however, the risk is based on the distribution $\mathbb P$ instead of $N$ samples.
Notice that in the total set $(X,Y) \sim \mathbb P$ , denote the expected loss of the predictor on the true total distribution as the **Population Risk** or **Expected Risk** :
$$\mathcal{L} (\theta) = \mathrm{E}_{(X,Y) \sim \mathbb{P}} [\ell(Y, f(X ; \theta))]$$

Here we aquire the **Target Function** :
Remember that $f = f(x;\theta)$
$$\theta^* = \arg_\theta\min \mathcal{L} (\theta) \\
f^* = f(x ; \theta^*)$$

$$f^*(x) = \argmin_{a\in\mathcal Y}\mathrm E[\ell(Y,a) | X =x]$$

Rewind: The empirical risk focus on the training set, which may not match the distribution $\mathbb P$ in the total set. The population risk focus on the total set with distribution $\mathbb P$.  
Assume the distribution of the training set is $\mathbb D_{train}$ , denote the empirical risk as 
$$\hat{\mathcal L}(\theta;\mathbb D_{train}) = \mathrm E_{(X,Y)\sim \mathbb D_{train}}[\ell(Y,f(X;\theta))]$$

Denote the population risk as
$$\mathcal L(\theta;\mathbb P) =\mathrm E_{(X,Y)\sim \mathbb P}[\ell(Y,f(X;\theta))]$$

The difference between the empirical risk and the population risk is called the **Generalization Gap** :
$$\mathcal L(\theta;\mathbb P) - \hat{\mathcal L}(\theta;\mathbb D_{train})$$or :
$$\mathcal L(f) -\hat{\mathcal L}(f)$$

In reality, we don't know the actuall distribution $\mathbb P$, so we have to split the data into two(actually 3) subsets, the training set and the **test set**. We can only estimate the population risk according to the test set with distribution $\mathbb D_{test}$. Approximate the population risk with the test set as the **Test Risk** :
$$\mathcal L(\theta;\mathbb D_{test})$$

Our goal is to find the best predictor based on the training set. We denote the optimal predictor as $f^*$, its risk $\mathcal L (f^*)$ is the theoretically minimal achievable risk. We want our expected risk $\mathcal L(\hat f)$ to be as close to $f^*$ as possible. The **excess risk** is the difference between the expected risk and the optimal risk:
$$\varepsilon(\hat f) := \mathcal L(\hat f) - \mathcal L (f^*)$$

Now our goal is to bound the excess risk $\varepsilon$ .

| **Aspect**               | **Expected Risk (\(\mathcal{L}(f)\))**                          | **Empirical Risk (\(\hat{\mathcal{L}}(f)\))**                   |
|--------------------------|-----------------------------------------------------------------|-----------------------------------------------------------------|
| **Definition**           | Expectation over true distribution \(\mu_Z\).                    | Average over training data \(\mathbb{D}\).                       |
| **Dependence**           | Population-level (fixed for a given \(f\) and \(\mu_Z\)).        | Sample-dependent (varies with \(\mathbb{D}\)).                   |
| **Optimality**           | Minimized by the **Bayes predictor** \(f^*\).                    | Minimized by the **ERM** \(\hat{f}\).                            |
| **Computability**        | Unknown (requires knowledge of \(\mu_Z\)).                        | Computable from data.                                            |
| **Bias/Variance**        | Ground truth (no sampling noise).                               | Subject to sampling error (may underestimate true risk).         |

### Examples
1. Classification:
Assume we have $K$ classes with labels $\mathcal Y = \{1,2,\cdots, K\}$, the probability of being class $k$ based on feature $x$ is  $P(Y = k|X = x)$. The loss function is: $\ell(y, \hat y) = \mathbb{I}(y \neq \hat y)$
Here the optimal predictor $f^*$ is the Bayes-Optimal Classifier:
$$f^*(x) = \argmax_{k \in \mathcal Y}  \mathbb{I}(Y=k|X=x)$$
For binary classification, $\mathcal Y = \{0,1\}$
$$f^*(x) = \begin{cases}1 &P[Y=1|X =x] \geq 1/2 \\ 0 &P[Y=1|X=x] \leq 1/2\end{cases}$$
ERM reads $$\hat f \in \argmin_{f \in \mathcal F} \mathcal L (f) = \argmin_{f \in \mathcal F} \frac{1}{N} \sum_{n=1}^N \ell(Y,f(Y))$$
2. Regression:
Assume we have a continuous output $y \in \mathcal Y = \R$,  the loss function is: $\ell(y, \hat y) = \frac 1 2(y - \hat y)^2$ 
$$f^*(x) = \mathrm E[Y|X=x]$$ ERM points to least squares

## Nonparametric Esimation Framework
Nonparametric models (instance-based learning) are models that do not have a fixed number of parameters, do not assume a fixed function form and do not make much assumptions about the distribution of the data. The training data is kept rather than thrown away, we focus on the similarity between the training data and the test input. It is a great tool to see how statistics and probability are applied. 

Let $$\begin{aligned}f^*(x) &= {\argmin}_{\text{measurable } f} \mathcal L(f)\\& = {\argmin}_{\text{measurable } f}\mathrm E_Z [\ell (f,Z)]\end{aligned}$$

Where $Z$ is follows probability measure $\mu_Z$ : $Z\sim \mu_Z$ , with the support of $\mu_Z$ in $\R^d$ : $\mathrm{supp}(\mu_Z) \subseteq R^d$ . ( The support is the minimal closed set capturing all possible values $Z$ can take with non-zero probability ) We want to estimate the optimal predictor $f^*$ based on the training data $\mathbb D = \{Z_1,Z_2\ldots,Z_N\} $ with $Z_i \stackrel{iid}{\sim} \mu_Z$.
Define the ERM over $\mathcal F$ :
$$\hat f(x) = \argmin_{f \in \mathcal F} \hat {\mathcal L}(f) = \frac 1 N \sum_{i=1}^N \ell(Z_i,f(Z_i))$$

Instead of exactly solving the ERM for $\hat f$, we use an algorithm or a solver. Given an algorithm $\mathcal A(\tau)$ that will output an approximate solution $f_{\mathcal A (\tau)}$ s.t. 
$$\hat{\mathcal L}(f_{\mathcal A (\tau)}) \leq \hat{\mathcal L}(\hat f) +\tau$$where $\tau > 0 $ is an **optimization tolerance** or the **optimization error**.

The excess risk can be defined as:
$$\varepsilon(f_{\mathcal A (\tau)}) := {\mathcal L}(f_{\mathcal A (\tau)}) - \mathcal L(f^*)$$
it measures how far the approximation $f_{\mathcal A (\tau)}$ is from the optimal solution $f^*$. We want to bound $\mathrm E_{\mathrm D}[\varepsilon(f_{\mathcal A (\tau)})]$

1. **Approximation Error** 
   Let $\bar f\in \arg\inf_{f \in \mathcal F} \hat {\mathcal L}(f)$ , $\bar f$ is an approximation of $f^*$ in $\mathcal F$. Define the **approximation error**:$$\varepsilon_{\text{app}} := \varepsilon(\bar f) = \mathcal L (\bar f) - \mathcal L(f^*)$$ 
   - Since $\hat{\mathcal L}(f_{\mathcal A (\tau)}) \leq \hat{\mathcal L}(\hat f) +\tau$ and $\hat{\mathcal L}(\hat f)\leq \hat{\mathcal L}(\bar f) $ we have
  $$\begin{aligned}\hat{\mathcal L}(f_{\mathcal A (\tau)})  -\tau &\leq \hat{\mathcal L}(\hat f)\\\hat{\mathcal L}(f_{\mathcal A (\tau)})  -\tau - \hat{\mathcal L}( f^*) &\leq \hat{\mathcal L}(\hat f)- \hat{\mathcal L}( f^*)\leq \hat{\mathcal L}(\bar f)- \hat{\mathcal L}( f^*)\\\hat{\mathcal L}(f_{\mathcal A (\tau)}) - \hat{\mathcal L}(\bar f)&\leq \tau\\\hat{\mathcal L}(f_{\mathcal A (\tau)}) - \hat{\mathcal L}(\bar f) +\mathcal L (\bar f) - \mathcal L (f^*)&\leq \tau + \varepsilon_{\text{app}}\\\end{aligned}$$
   - Taking the expectation we get: $$2\mathrm E_{\mathrm D}[\hat{\mathcal L}(f_{\mathcal A (\tau)})  - {\mathcal L}( f^*)] \leq 2\varepsilon_{\text{app}} + 2\tau$$
2. **Statistical Error** 
   Define $$\varepsilon_{\text{sta}}: = \mathrm E_{\mathrm D}[{\mathcal L}(f_{\mathcal A (\tau)})  + {\mathcal L}( f^*) - 2 \hat{\mathcal L}(f_{\mathcal A (\tau)})]$$ as the **statistical error**.
   - Now we get : $$\begin{aligned} \mathrm E_{\mathrm D}[\varepsilon(f_{\mathcal A (\tau)})] & = \mathrm E_{\mathrm D}[{\mathcal L}(f_{\mathcal A (\tau)}) - \mathcal L(f^*)]\\&\leq \varepsilon_{\text{sta}} + 2\varepsilon_{\text{app}} + 2\tau\end{aligned}$$
3. **Optimization Error**
   Define $$\varepsilon_{\text{opt}}:=\hat{\mathcal{L}}(f_{\mathcal A (\tau)}) - \hat{\mathcal{L}}(\hat{f})$$ as the **optimization error**.

In conclusion, denote the result of our algorithm $f_{\mathcal A(\tau)}$ as $f$ we have:
$$\underbrace{\mathcal{L}(f) - \mathcal{L}(f^*)}_{\text{Excess Risk}} = \underbrace{\mathcal{L}(f) - \hat{\mathcal{L}}(f)}_{\text{Generalization Error}} + \underbrace{\hat{\mathcal{L}}(\hat{f}) - \mathcal{L}(f^*)}_{\text{Approximation Error}} +\underbrace{\hat{\mathcal{L}}(f) - \hat{\mathcal{L}}(\hat{f})}_{\text{Optimization Error}}$$
We can bound the expectation of the excess risk as:
$$\mathrm E_{\mathrm D}[\varepsilon(f_{\mathcal A (\tau)})] \leq \underbrace{2\sup_{f\in\mathcal F}|\mathcal L(f) - \hat{\mathcal L} (f)|}_{\varepsilon_{\text{sta}}} +\underbrace{\inf_{f\in\mathcal F}|{\hat{\mathcal{L}}(\hat{f}) - \mathcal{L}(f^*)|}}_{\varepsilon_{\text{app}}} + \underbrace{\hat{\mathcal{L}}(f_{\mathcal A (\tau)}) - \hat{\mathcal{L}}(\hat{f})}_{\varepsilon_{\text{opt}}}$$








# 2
$cv = \frac{\sqrt{var(\hat\theta)}}{E(\hat\theta)}$
$$MSE(\hat{\theta}) = var(\hat{\theta}) + (bias(\hat{\theta}))^2$$

Point Estimation Error Control: MSE(V,C)
When $\hat\theta$ is unbiased, $MSE(\hat\theta) = var(\hat\theta)$ , for a given upper bound of variance $V$, or a given upper bound of $cv: C$, such that $V \geq var(\hat\theta) $ or $C \geq cv(\hat\theta)$

Margin of Error:
If $\hat \theta$ is a point estimator of $\theta$, for a given $\alpha \in (0,1)$, if $$P(|\hat\theta - \theta| \leq d) = 1-\alpha$$ we call $d$ the margin of error of $\hat\theta$ at confidence level $\alpha$. 
Relative Margin of Error:
If $$P(\frac{|\hat\theta - \theta|}{\theta} \leq r) = 1-\alpha$$ we call $r$ the relative margin of error of $\hat\theta$ at confidence level $\alpha$. 

Error Limit (d,r) Estimation Control:
For a given $\alpha \in (0,1)$, for given absolute margin of error $d$ or relative margin of error $r$, such that $P(|\hat\theta - \theta| \leq d) = 1-\alpha$ or $P(\frac{|\hat\theta - \theta|}{\theta} \leq r) = 1-\alpha$.

Assumptions in this course:
1. Consistent Estimation: $\hat \theta_n \xrightarrow{P}\theta,n\to \infty$
Definition: If $\hat\theta$ is a consistent estimator of $\theta$, then for any $\epsilon > 0$,
$$P(|\hat\theta - \theta| > \epsilon) \to 0 \text{ as } n \to \infty$$
2. Asymptotically Normal Distribution CAN: $\frac{\hat\theta_n - E(\hat\theta)}{\sqrt{var(\hat\theta_n)}} \xrightarrow{d} N(0,1)$ 
Denote $\sqrt{var(\hat\theta_n)}$ as $\mathrm{sd}(\hat\theta_n)$

**You need to proof UE or AUE in this course**
Theorem: When $\hat\theta$ is consistent and asymptotically normal, if $\hat \theta$ is an unbiased estimator(UE) or asymptotically unbiased estimator(AUE), then the distribution of $\hat\theta$ is approximately normal.

$$\frac{\hat\theta - \theta}{\sqrt{var(\hat\theta)}} = \frac{\hat\theta - \theta}{\mathrm{sd}(\hat\theta)} \xrightarrow{d} N(0,1)\quad \text{as } n \to \infty$$
Therefore $$P\left(\frac{\hat\theta - \theta}{\mathrm{sd}(\hat\theta)} \leq z_{\alpha/2}\right) = 1-\alpha$$
$d = z_{\alpha/2} \mathrm{sd}(\hat\theta), r = z_{\alpha/2} \frac{\mathrm{sd}(\hat\theta)}{\theta}$

$\hat\theta_L = \hat\theta - z_{\alpha/2} \mathrm{sd}(\hat\theta),\hat\theta_R = \hat\theta + z_{\alpha/2} \mathrm{sd}(\hat\theta)$
If $P(\hat\theta_L \leq \theta \leq \hat\theta_R) = 1-\alpha$, then $\hat\theta_L$ and $\hat\theta_R$ are the endpoints of a $(1-\alpha)$ confidence interval for $\theta$.
When $n$ is large, $$P(\theta \in [\hat\theta \pm z_{\alpha/2} \mathrm{sd}(\hat\theta)]) \approx 1-\alpha$$







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

# 4

```R
# Confidence Interval
conf.interval=function(para.est, SD.est, alpha)
##############    Input     ########################
## para.est = estimator of character
## SD.est   = estimator of sd
## alpha    = confidence level (1-alpha)
##############    Output    ########################
## left     = left of confidence interval
## right    = right of confidence interval
####################################################
{
  quan=qnorm(1-alpha/2) #z_alpha/2  uppper alpha/2
  
  para.left = para.est-quan*SD.est
  para.right = para.est+quan*SD.est
  
  return(list(left=para.left, right=para.right))
}

# Error
dr.error=function(para.est, SD.est, alpha)
##############    Input     ########################
## para.est = estimator of character
## SD.est   = estimator of sd
## alpha    = confidence level (1-alpha)
##############    Output    ########################
## d        = absolute error
## r        = relative error
####################################################
{
  quan=qnorm(1-alpha/2)
  
  d=quan*SD.est
  r=quan*SD.est/para.est

  return(list(d=d, r=r))
}
```

Sample Mean:
```R
sample.mean=function(mydata, alpha)
##############    Input     ########################
## mydata = srs sample vector
## alpha = confidence level 1-alpha
##############    Output    ########################
## mean.est = estimator of sample mean
## sd.est   = estimator of sample sd
## left     = left of confidence interval
## right    = right of confidence interval
## d        = absolute error
## r        = relative error
####################################################
{
  size=length(mydata)
  
  mean.est=mean(mydata)
  sd.est  =sqrt(var(mydata)/size)
  
  ci.result=conf.interval(mean.est, sd.est, alpha)
  left =ci.result$left
  right=ci.result$right
  
  dr.result=dr.error(mean.est, sd.est, alpha)
  d=dr.result$d
  r=dr.result$r
  
  return(list(mean.est=mean.est, sd.est=sd.est, 
              left=left, right=right, d=d, r=r))
}
```


# 5

Review chp2:
 两大假设:
 1. 相合 $\hat \theta_n \xrightarrow{P}\theta,n\to \infty$
 2.  渐进正态 $\sqrt n(\hat \theta - \theta) \xrightarrow{d} N(0,v(\theta))$

若 $\bar y$ 为 UE or UAE
$$CI = [\bar y \plusmn z_{\frac{\alpha}2} \mathrm{var}(\bar y)]$$


总体均值 :
$$ \bar Y = \frac 1 N \sum_{i=1}^N Y_i $$
总体方差 :
$$S^2 = \frac 1 {N-1} \sum_{i=1}^N (Y_i - \bar Y)^2$$
用样本均值估计总体均值,待估计特征$\bar Y = \theta$ 
点估计: $$\bar y = \frac 1 n \sum_{i=1}^n y_i = \hat \theta$$

示性变量: A is the picked set.
$$\xi_i = \begin{cases}1 & \text{if } Y_i \in A\\ 0 & \text{if } Y_i \notin A \end{cases}$$
则 $\xi_i \sim B(1,p)$, where:
$$p = P(\xi_i =1) = n/N $$
for 
$$\bar y = \frac 1 n \sum_{i=1}^n y_i = \frac{1}n \sum_{i=1}^N \xi_i y_i$$

方差的估计 :
$$\hat{\mathrm{Var}} (\bar y) = \frac{1-f}{n} s^2$$
$$s^2 = \frac 1 {n-1} \sum_{i=1}^n (y_i - \bar y)^2$$
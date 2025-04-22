---
title: Quantom Mechanics 5
date: 2025-04-21 19:00:00
categories: Learn
---
# QMHW 6

4.1, 4.19, 4.46, 4.49

# 4.1
## a
$$\begin{aligned}
[r_i,p_j] & = r_ip_j - p_ir_j\\
 &=\begin{cases} r_ip_i - p_ir_i = i\hbar& i=j\\
   r_ip_j - p_ir_j = 0&i\neq j\end{cases}\\
   &=-[p_i,r_j]
\end{aligned}$$

$$\begin{aligned} 
[r_i,r_j] & = r_ir_j -r_jr_i = 0-0=0\\
[p_i,p_j] & = -i\hbar \frac{\partial}{\partial r_i}(-i\hbar \frac{\partial}{\partial r_j}) - (-i\hbar \frac{\partial}{\partial r_j})(-i\hbar \frac{\partial}{\partial r_i}) =0
\end{aligned}$$

## b
$$\begin{aligned}
\frac{d}{dt} \braket r &= \frac{i}\hbar \braket{[\hat H,r]} + \braket{\frac{\partial r}{\partial t}}\\
& = \frac{i}\hbar \braket{(\frac{1}{2}mv^2 +V) r - r(\frac{1}{2}mv^2 +V) } +  \braket{\frac{\partial r}{\partial t}}\\
& =  \braket{\frac{\partial r}{\partial t}} = \braket v\\
& = \frac{1}m\braket p
\end{aligned}$$

$$\begin{aligned}
\frac{d}{dt} \braket p & = \frac{i}\hbar \braket{[\hat H,p]} + \braket{\frac{\partial p}{\partial t}}\\
& = \frac{i}\hbar \braket{\hat H (-i\hbar \nabla) + i\hbar \nabla \hat H} + \braket{\frac{\partial p}{\partial t}}\\
& = \frac{i}\hbar \braket{(\frac{1}{2}mv^2 +V) (-i\hbar \nabla) + i\hbar \nabla (\frac{1}{2}mv^2 +V)} + \braket{\frac{\partial p}{\partial t}}\\
& = -\braket{\nabla V}
\end{aligned}$$

## c
$$ \sigma_x\sigma_{p_x} \geq \hbar/2 ,\quad  \sigma_y\sigma_{p_y} \geq \hbar/2,\quad  \sigma_z\sigma_{p_z} \geq \hbar/2$$

# 4.19
Replace $e^2$ with $Ze^2$ in $V(r)$, we have 
$$\rho_0 = \frac{Zm_e e^2}{2\pi\varepsilon_0\hbar \kappa}$$
Therefore the allowed energies are
$$ E_n(Z) = - \left[\frac{m_e}{2\hbar^2}\left(\frac{Ze^2}{4\pi\varepsilon_0}\right)^2\right]\frac{1}{n^2} =  \frac{Z^2}{n^2}E_1,\quad n = 1,2,3,\ldots$$

$$a(Z) = \frac a Z$$

$$\mathcal R (Z)= Z^2\mathcal R$$

# 4.46
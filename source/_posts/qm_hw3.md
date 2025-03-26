---
title: Quantom Mechanics Week 3
date: 2025-03-10 16:00:00
categories: Learn
---
# QM Week 3
# 2.36
Consider $x\in [-a,a]$, following steps **2.22 ~ 2.31** :
The only changes are the boundary conditions **2.26** : $\psi(-a) = \psi(a) = 0$ :
$$A\sin(-ak) + B\cos(-ak) = A\sin(ak) + B\cos(ak) = 0$$

$$\implies \begin{cases}A\sin(ak) = 0\\ B\cos(ak) = 0 \end{cases}$$
Case 1: if $B = 0,\,A\neq 0,\,\sin (ak) = 0$ 
$$k_n = \frac{n\pi}a,\quad n = 1,2,\ldots$$

$$E_n = \frac{n^2\pi^2\hbar^2}{2ma^2}$$


$$
\int_{-a}^a |A|^2 \sin^2(kx)dx = |A|^2 a = 1 \implies A = \sqrt{\frac 1 a}
$$

$$\psi_n (x)= \sqrt\frac{1}{a} \sin(\frac{n\pi }a x)$$

Case 2: if $A=0,\,B\neq 0,\, \cos(ak) = 0$

$$k_n = \frac{(2n-1)\pi}{2a},\quad n = 1, 2,\ldots$$

$$E_n = \frac{(2n-1)^2 \hbar^2\pi^2}{8ma^2}$$

$$\int_{-a}^a |A|^2 \cos^2(kx)dx = |A|^2 a =1 \implies A = \sqrt\frac{1}a $$

$$\psi_n(x) = \sqrt\frac 1 a \cos(\frac{(2n-1)\pi}{2a}x)$$

# 2.38
## a
**2.18** : 
$$
\Psi_n (x,t) = \sqrt\frac 2 a \sin(\frac{n\pi}a x )\exp \left[-i\left(\frac{n^2\pi^2 \hbar}{2ma^2}\right)t\right ]
$$


$$
\Psi_n (x, 0) = \sqrt\frac 2 a \sin(\frac{n\pi}a x )
$$

$$
\begin{aligned}
\Psi_n (x,T) &= \sqrt\frac 2 a \sin(\frac{n\pi}a x )\exp \left[-i\left(\frac{n^2\pi^2 \hbar}{2ma^2}\right)\frac{4ma^2}{\pi \hbar}\right ]\\
&=\sqrt\frac 2 a \sin(\frac{n\pi}a x ) \exp (-2n^2 \pi i)\\
&=\Psi_n (x,0)
\end{aligned}
$$

$$
\Psi(x,T) = \sum c_n \Psi_n (x,T) = \sum c_n \Psi_n(x,0) = \Psi(x,0)
$$

## b
$E = \frac 1 2 mv^2 ,2a = tv,\;\therefore t = a \sqrt \frac{2m}{E}$

## c 
$t = T$ : 
$$E = \frac{\pi^2\hbar^2}{8ma^2}$$

# 2.40
## a 
$\xi = \sqrt{\frac{m\omega}\hbar}x$
According to **2.86** :
$$
\psi_n (x) = \left(\frac{m\omega}{\pi\hbar}\right)^{1/4}\frac{1}{\sqrt{2^n n!}}H_n(\xi) e^{-\xi^2/2}
$$
Denote $\left(\frac{m\omega}{\pi\hbar}\right)^{1/4}$ as $\alpha$ ,

$$
\psi_0 = \alpha e^{-\xi^2/2}\qquad \psi_1 = \alpha\sqrt 2\xi e^{-\xi^2/2} \qquad \psi_2 = \alpha (\sqrt 2 \xi^2 - \frac{1}{\sqrt 2})e^{-\xi^2/2}
$$

$$
\begin{aligned}
\psi(x,0) &= A \exp(-\frac{m\omega}{2\hbar}x^2) -4A\sqrt{\frac{m\omega}\hbar}x \exp(-\frac{m\omega}{2\hbar}x^2)+ 4A\frac{m\omega}{2\hbar}x^2\exp(-\frac{m\omega}{2\hbar}x^2)\\
& = A e^{- \xi^2/2 } - 4A \xi e^{- \xi^2/2 } + 4A \xi^2 e^{- \xi^2/2 }\\
& = \frac{A}\alpha (3 \psi_0 -2\sqrt 2 \psi_1 + 2\sqrt 2 \psi_2 )
\end{aligned}
$$

$$1 = \sum |c_n|^2 = \frac{A^2}{\alpha^2}(9+8+8)\\\therefore A = \frac{\left(\frac{m\omega}{\pi\hbar}\right)^{1/4}}5;\; c_1 = \frac 3 5,\, c_2 = -\frac{2\sqrt 2}{5},\, c_3 = \frac{2\sqrt 2}{5}$$

## b
The possible energies are: $E_0=\frac 1 2 \hbar\omega, E_1 = \frac 3 2 \hbar \omega , E_2 = \frac 5 2 \hbar \omega$
With probabilities : $ P_0 = |c_0|^2 = \frac{9}{25},P_2 = \frac 8{25},P_3 =\frac 8{25}$
The expectation value of energy is:
$$\langle H \rangle = \sum |c_n|^2 E_n = \frac{73}{50}\hbar \omega$$

## c
$T = \frac \pi\omega$

# 2.41
Since it is impossible for the partical to appear at $x< 0$ , thus there should be no even peaces in the wave function.
$$E_n = (2n-\frac 1 2) \hbar \omega,\quad n = 1,2,\ldots$$

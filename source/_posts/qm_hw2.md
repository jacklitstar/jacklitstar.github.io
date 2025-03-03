---
title: Quantom Mechanics Week 2
date: 2025-03-03 16:30:00
categories: Learn
---
# QM Week 2
# 2.4
## a 
$$\begin{aligned}
<x> &= \int_0^a \Psi_n^* x \Psi_n dx \\
&= \int_0^a \frac{2}{a} x \sin^2\left(\frac{n\pi}{a} x\right) dx \\
&= \frac{a}{2} - \frac{1}{a} \left[\frac{a}{2n\pi} x \sin\left(\frac{2n\pi}{a} x\right) + \left(\frac{a}{2n\pi}\right)^2 \cos\left(\frac{2n\pi}{a} x\right)\right] \Bigg|_0^a\\
&= \frac{a}{2}
\end{aligned}$$
## b 
$$\begin{aligned}
<x^2> &= \int_0^a \Psi_n^* x^2 \Psi_n \, dx \\
&= \int_0^a \frac{2}{a} x^2 \sin^2\left(\frac{n\pi}{a} x\right) dx \\
&= \frac{2}{a} \int_0^a x^2 \left[\frac{1}{2} - \frac{1}{2}\cos\left(\frac{2n\pi}{a} x\right)\right] dx \\
&= \frac{a^2}{3} - \frac{a^2}{2n^2\pi^2}
\end{aligned}$$
## c 
$$<p> = \int_0^a -\frac{2}a\sin(\frac{n\pi}a x)i\hbar \frac{n\pi}a \cos(\frac{n\pi}a x)dx = 0$$
## d 
$$<p^2> = \hbar^2(\frac{n\pi}a)^2 \int_0^a \Psi^*\Psi dx =(\frac{n\hbar\pi}a)^2 $$
## e 
$$\sigma_x = a\sqrt{\frac{1}{12} - \frac{1}{2n^2\pi^2}}$$
## f 
$$\sigma_p = \frac{n\hbar \pi}a$$
## g 
$$\sigma_x\sigma_p = \frac\hbar 2 \sqrt{\frac{n^2\pi^2}3 - 2}\geq \frac\hbar 2,\quad n = 1,2,\ldots$$
When $n = 1$, $\sigma_x\sigma_p$ is the smallest.

# 2.5
## a 
Since $\omega = \pi^2\hbar/2ma^2$ : $$E_n = \frac{n^2\pi^2\hbar^2}{2ma^2} = n^2\omega\hbar$$
$$ 1 = \int A^2 (\psi_1^*\psi_1 + \psi_1^*\psi_2+\psi_2^*\psi_1+\psi_2^*\psi_2)dx = 2A^2\\ A = \frac{1}{\sqrt 2}$$
## b 
$$\begin{aligned}\Psi(x,t) &= \frac 1{\sqrt{2}}[\psi_1 e^{-i\hbar E_1t/\hbar} + \psi_2 e^{-iE_2t/\hbar}]\\
&=\frac 1{\sqrt{2}}[\psi_1 e^{-i\omega t} + \psi_2 e^{-4i\omega t}]\\
&=\frac{1}{\sqrt a}[\sin(\frac{\pi x }a)e^{-i\omega t} + \sin(\frac{2\pi x }a)e^{-4i\omega t}]\end{aligned}$$

$$|\Psi(x,t)|^2 = \frac{1}{a}[\sin^2(\frac\pi a x )+ \sin^2(\frac {2\pi}a x ) +2\sin(\frac\pi a x )\sin(\frac {2\pi}a x )\cos(3\omega t)]$$

## c 
$$\begin{aligned}<x> &= \int \Psi^* x\Psi dx\\
& = \frac{1}2\int x[\psi_1^*\psi_1 + \psi_2^*\psi_2+2\psi_1^*\psi_2 e^{-3i\omega t}]\, dx\\
&= \frac 1 2 \int \psi_1^* x \psi_1 dx + \frac 1 2\int \psi_2^* x \psi_2 dx + \int x\psi_1^*\psi_2 e^{-3i\omega t}\, dx\\
& = \frac a 4+ \frac a 4 -\frac{16a}{9\pi^2}\cos(3\omega t) \\
& = \frac a 2 - \frac{16a}{9\pi^2}\cos(3\omega t)
\end{aligned}$$

## d 
$$<p> = m\frac{d<x>}{dt}= \frac{8\hbar}{3a}\sin(3\omega t)$$

## e 
$$E_n = \frac{n^2\pi^2\hbar^2}{2ma^2} \quad \text{for: } n = 1,2$$
Since $c_1 = c_2 = \frac{1}{\sqrt 2}$, they have the same probability, therefore: 
$$ <H> = \frac{1}2 (E_1+E_2) = \frac{5\pi^2\hbar^2}{4ma^2}$$

# 2.6
Since $e^{i\phi}\psi_2$ is still orthoganal to $\psi_1$ , the results in **2.5 (a)** remains:
$$A = \frac{1}{\sqrt 2} ,\quad \Psi(x,0) = \frac{1}{\sqrt 2}(\psi_1+e^{i\phi}\psi_2)$$
$$\Psi(x,t) = \frac{1}{\sqrt a}[\sin(\frac{\pi x }a)e^{-i\omega t} + \sin(\frac{2\pi x }a)e^{i(\phi - 4\omega t)}]$$
$$|\Psi(x,t)|^2 = \frac{1}{a}[\sin^2(\frac\pi a x )+ \sin^2(\frac {2\pi}a x ) +2\sin^2(\frac\pi a x )\sin^2(\frac {2\pi}a x )\cos(3\omega t-\phi)]$$
$$<x> = C$$
When $\phi = \pi/2$ , $\Psi(x,0) = A[\psi_1 - i\psi_2]$ and $<x>|_{t=0} = a/2$ . 
When $\phi = \pi$ , $\Psi(x,0) = A[\psi_1 - \psi_2]$ and $<x>|_{t=0} = \frac a 2 + \frac{16a}{9\pi^2}$ .

# 2.7
## a 
$$1 = \int_0^a |\Psi|^2 dx = 2\int_0^{\frac a 2} (Ax)^2 dx \implies A = \sqrt{\frac{12}{a^3}}$$
## b 
 $\sum c_n \sqrt\frac{2}{a}\sin(\frac{n\pi}a x)$ is the Fourier Expansion of $\Psi(x,0)$ , therefore: 
$$\begin{aligned}c_n &= \int_0^a \psi_n^* \Psi(x,0) dx\\
&=\int_0^{a/2}  \sqrt\frac{2}{a}\sin(\frac{n\pi}{a}x)Ax \,dx + \int_{a/2}^a  \sqrt\frac{2}{a}\sin(\frac{n\pi}{a}x)A(a-x) dx\\
&\quad \text{let: } y=x-a,\,x = y-a\\
&=\int_0^{a/2}  \sqrt\frac{2}{a}\sin(\frac{n\pi}{a}x)Ax \,dx - \int_0^{a/2}  \sqrt\frac{2}{a}\sin(\frac{n\pi}{a}(a-y))Ay\, dy\\
&=\begin{cases}A\sqrt\frac{2}{a}\int_0^{a/2}  2x\sin(\frac{n\pi}{a}x)\,dx\quad & n \text{ is odd}\\
0 & n \text{ is even}\end{cases} \\
&= \begin{cases}
\frac{4\sqrt 6}{n^2\pi^2}\sin(\frac{n\pi}2) &n \text{ is odd}\\
0 & n \text{ is even}\end{cases}
\end{aligned}$$
## c 
$$c_1 =\frac{4\sqrt 6}{\pi^2}, \quad P_1 = |c_1|^2 = \frac{96}{\pi^4} $$
## d 
$$P_n = |c_n|^2 = \begin{cases}\frac{96}{n^4\pi^4} &n \text{ is odd}\\0 & n \text{ is even}\end{cases}$$

$$\begin{aligned}<H> &= \sum_n P_n E_n\\
&= \sum_{n=1}\frac{96}{\pi^4}\frac{1}{n^4} \frac{n^2\pi^2\hbar^2}{2ma^2} \text{\; for } n = 1,3,5,\ldots\\
&=\frac{48 \hbar^2}{\pi^2 ma^2} \sum_{n=1}\frac{1}{n^2}\text{\; for } n = 1,3,5,\ldots \\
&=\frac{6\hbar^2}{ma^2}
\end{aligned}$$

# 2.8
$$E_1 = \frac{\pi^2\hbar^2}{2ma^2}$$
$$\begin{aligned}c_1 &= \int_0^a \Psi^* \psi_1 dx \\
&= \int_0^{a/2}\sqrt{ \frac{2}{a}}A\sin(\frac{\pi}{a}x) dx\\
&= \frac{A\sqrt{ 2a}}{2}
\end{aligned}$$
$$\int |\Psi|^2 dx =1\implies A = \sqrt{\frac{2}{a}}$$
$$\therefore c_1 = \frac 2 \pi,\quad P_1 = \frac 4 {\pi^2}$$

# 2.9
$$\begin{aligned}
<H> &= \int_0^a \Psi^* \hat H \Psi dx\\
&=\int_0^a A^2 x(a-x) \frac{\hbar^2}{m} dx\\
&=\frac{5\hbar^2}{ma^2}\end{aligned}
$$
Which is the same as the result in **Example 2.21**



---
title: Quantom Mechanics Week 4
date: 2025-03-17 18:00:00
categories: Learn
---
# QM Week 4
# 2.20
## a
$$
\int \psi^* \psi dx = \int A^2 e^{-2a|x|} dx = 1\implies A = \sqrt a
$$

$$\Psi(x,0) = \sqrt a e^{-a|x|}$$
## b
$$\phi(k) = \frac{1}{\sqrt{2\pi}} \int \Psi(x,0) e^{-ikx}\, dx= \frac{2a\sqrt a }{\sqrt{2\pi}(a^2+k^2)}$$

## c

$$
\begin{aligned}
\Psi(x,t) &= \frac{1}{\sqrt{2\pi}}\int \phi(k)e^{i(kx - \frac{\hbar k^2}{2m}t)} \, dk \\
& = \frac{a\sqrt a }{\pi} \int\frac{1}{a^2+k^2} e^{i(kx-\frac{\hbar k^2}{2m}t)} \, dk \\
\end{aligned}$$

## d
$$\lim_{a\to \infty} \phi(k) = \sqrt\frac{2}{\pi a}\simeq 0$$

$$\lim_{a\to0}\phi(k) = \infty $$

# 2.21 
## a
$$1 = \int \Psi^* \Psi dx = A^2 \int e^{-2ax^2} \, dx = A^2\sqrt\frac{\pi}{2a}\\
\implies A = \left(\frac{2a}{\pi}\right)^{1/4}$$

## b
$$\begin{aligned}
\Psi(x,t) &= \frac{1}{\sqrt{2\pi}}\int \phi(k)e^{i(kx - \frac{\hbar k^2}{2m}t)} \, dk \\
& = \frac{1}{\sqrt{2\pi}} \int Ae^{-ax^2} e^{i(kx-\frac{\hbar k^2}{2m}t)} \, dk \\
& = \frac{Ae^{-ax^2}}{\sqrt{2\pi}} \int e^{i(kx-\frac{\hbar k^2}{2m}t)} \, dk \\
& = 
\end{aligned}$$
拼尽全力无法积分

## c
if 

$$\Psi(x,t) = \left(\frac{2a}\pi\right)^{1/4}\frac{1}\gamma e^{-ax^2/\gamma^2}\qquad \gamma = \sqrt{1+(2i\hbar a t/m)}$$

$$|\Psi|^2 = \sqrt \frac{2}{\pi}\omega e^{-2\omega^2 x ^2}$$

## d
$$\langle x \rangle = \int x|\Psi|^2 dx = 0$$

$$\langle p \rangle = m \frac{d\langle x \rangle}{dt} = 0$$

$$\langle x^2 \rangle = \int x^2|\Psi|^2 dx = \frac{1}{4\omega^2}$$

$$\langle p^2 \rangle = a\hbar^2$$

$$\sigma_x = \sqrt{\langle x^2 \rangle - \langle x \rangle^2} = \frac{1}{2\omega}$$

$$\sigma_p = \sqrt{\langle p^2 \rangle - \langle p \rangle^2} = \sqrt{a\hbar^2}$$

$$\sigma_x\sigma_p = \frac{\sqrt a\hbar}{2\omega} = \frac{\hbar \sqrt{1+(2\hbar a t /m )^2}}{2}\geq \frac \hbar 2$$

# 2.24
$$\langle x \rangle = \langle p \rangle = 0$$

$$\langle x^2 \rangle = 2 \int \frac{m\alpha}{\hbar^2} x^2 e^{-2m\alpha/\hbar^2 x} dx = \frac{\hbar^4}{2(m\alpha)^2}$$

$$\sigma_x\sigma_p = \sqrt{\langle x^2 \rangle\langle p^2\rangle} = \frac{\sqrt 2\hbar}2\geq \frac \hbar 2$$

# 2.25 
$$\psi_1(x) = \frac{\sqrt{m\alpha}}\hbar e^{-m\alpha |x| /\hbar^2} = C e^{-m\alpha |x| /\hbar^2}$$

$$\psi_2(x) =A e^{ikx} + B e^{-ikx} = \begin{cases} e^{ikx} + Re^{-ikx} &x \leq 0 \\T e^{ikx} & x > 0\end{cases}$$


$$\begin{aligned}\frac{1}C\langle \psi_1 ,\psi_2 \rangle &= \frac{1}C\int \psi_1^* \psi_2 \,dx\\
&=\int_{-\infty}^0 ( e^{ikx} + Re^{-ikx}) e^{-m\alpha |x| /\hbar^2}\, dx + \int_0^\infty Te^{ikx}e^{-m\alpha |x| /\hbar^2}\, dx\\
&=\frac{-1}{ik + m\alpha /\hbar^2} + \frac{R}{ik - m\alpha /\hbar^2}  + \frac{T}{ik - m\alpha /\hbar^2}\\
 1= R+T\quad &\\
 & = 0
\end{aligned}$$
# 2.27 
## a
Case 1, where the wave function is even:

$$\psi(x) = \begin{cases}
Be^{kx} & x < -a\\
C (e^{kx} + e^{-kx}) & -a<x<a\\
B e^{-kx} & x > a\\
\end{cases}$$

Boundary condition (continuity):

$$Be^{-ak} = C(e^{-ak}+e^{ak})$$

Schorodinger Equation:

$$-\frac{\hbar^2}{2m} \frac{d^2\psi}{dx^2} + \alpha[\delta(x+a)+\delta(x-a)]\psi = E\psi$$

take the integral on $[-a-\varepsilon,-a+\varepsilon]$ and $[a-\varepsilon,a+\varepsilon]$ , and let $\varepsilon \to 0$ :

$$-\frac{\hbar^2}{2m} \frac{d\psi}{dx} + \alpha\int \delta(x+a) dx + \alpha \int \delta(x-a) dx = E\int \psi dx$$

$$\Delta \left(\frac{d\psi}{dx}\right)\Bigg|_{-a} = \frac{2m}{\hbar^2} \lim_{\varepsilon\to 0} \int_{-a-\varepsilon}^{-a+\varepsilon} \alpha \delta(x+a)\psi(x)\, dx = -\frac{2m\alpha}{\hbar^2}\psi(-a)$$

The same applies at $a$ :
$$\Delta \left(\frac{d\psi}{dx}\right)\Bigg|_{a} = -\frac{2m\alpha}{\hbar^2}\psi(a)$$

According to the form of $\psi$ :
$$\frac{d\psi}{dx} = 
\begin{cases}
Bke^{kx} & x < -a\\
C(ke^{kx} -ke^{-kx})& -a<x<a\\
-Bke^{-kx} & x > a\\
\end{cases}$$

$$\begin{aligned}
\frac{d\psi}{dx}\Bigg|_{a^-} &= C(ke^{ak} -ke^{-ak})\\
\frac{d\psi}{dx}\Bigg|_{a^+} &= -Bke^{-ak}\\
\therefore \Delta \left(\frac{d\psi}{dx}\right)\Bigg|_{a} &= -Bke^{-ak} - C(ke^{ak} -ke^{-ak})
\end{aligned}
$$

The same appies at $-a$ :

$$
\Delta \left(\frac{d\psi}{dx}\right)\Bigg|_{-a} = -Bke^{-ak} + C(ke^{-ak} -ke^{ak})\\
$$

Solve the equation: 
$$
\begin{cases}-\frac{2m\alpha}{\hbar^2}\psi(a) =  -Bke^{-ak} - C(ke^{ak} -ke^{-ak})\\
-\frac{2m\alpha}{\hbar^2}\psi(-a) = -Bke^{-ak} + C(ke^{-ak} -ke^{ak}) 
\end{cases}
$$

$$\begin{aligned}\implies \frac{-2m\alpha}{\hbar^2} C(e^{ak}+e^{-ak}) &= -2Cke^{ak}\\
\frac{m\alpha}{\hbar^2}( e^{2ak} +1 ) &= k e^{2ak}\qquad \# 1
\end{aligned}$$

$$E = -\frac{\hbar^2 k^2}{2m}$$

Case 2, where the wave function is odd:

$$\psi(x) = \begin{cases}
Be^{kx} & x < -a\\
C (e^{kx} - e^{-kx}) & -a<x<a\\
-B e^{-kx} & x > a\\
\end{cases}$$

Boundary condition (continuity):
$$Be^{-ak} = C(e^{-ak}-e^{ak})$$

Repeat the steps in case 1, we get:
$$\frac{m\alpha}{\hbar^2}( e^{2ak} -1 ) = k e^{2ak}\qquad \# 2 $$

$$E = -\frac{\hbar^2 k^2}{2m}$$

The number of bound states are the number of solutions to equations #1 and #2 accordingly.

## b
1. When $\alpha = \hbar^2/ma$ :
For case 1: 
$$ak = 1+ e^{-2ak},\quad ak\simeq 1.109$$
For case 2: 
$$ak = 1- e^{-2ak},\quad ak \simeq 0.797$$
2. When $\alpha = \hbar^2/4ma$ :
For case 1:
$$2ak = 1+ e^{-2ak},\quad ak\simeq 0.640$$
For case 2:
$$2ak = 1- e^{-2ak},\quad ak = 0\quad \text{not possible}$$

The according energy states can be caculated with $E = -\hbar^2k^2/2m$ .

## c
1. When $a\to 0$ , there could only be one bound state, which takes the even wave function. 
$$ 1 + e^{-2ak} = \frac{\hbar^2k}{m\alpha}\\
\implies \lim_{a\to 0} k = \frac{2m\alpha}{\hbar^2}\implies E = -\frac{2m\alpha^2}{\hbar^2}$$
The energy is the same to where $V(x) =- 2\alpha\delta(x)$ , as if the two heaps of the delta functions are now merged into one.
1. When $a\to \infty$, there are two bound states.
For case 1: 
$$1 +e^{-2ak} = \frac{\hbar^2k}{m\alpha}\\
\implies \lim_{a\to \infty} k = \frac{m\alpha}{\hbar^2}\implies E = -\frac{m\alpha^2}{2\hbar^2}$$
For case 2:
$$1- e^{-2ak} = \frac{\hbar^2k}{m\alpha}\\
\implies \lim_{a\to \infty} k = \frac{m\alpha}{\hbar^2}\implies E = -\frac{m\alpha^2}{2\hbar^2}$$
# 2.28
Consider the particle traveling from left to right, we have the wave function:
$$\psi(x) = \begin{cases}
Ae^{ikx} + Be^{-ikx} & x < -a\\
C e^{ikx} + De^{-ikx} & -a<x<a\\
F e^{ikx}  & x > a
\end{cases}$$

Boundary conditions(continuity):
$$\begin{aligned}
Ae^{-iak} + Be^{iak} &= C e^{-iak} + De^{iak}\\
Ce^{iak} + De^{-iak} &= Fe^{iak}\end{aligned}$$

let $\beta = e^{-2iak}$

$$\begin{align}\beta A+B &= \beta C+D\\C+\beta D &= F\end{align}$$

$\Delta \psi'|_{-a} = - \frac{m\alpha}{\hbar^2}\psi(-a)$ :

$$(Cik - Aik)e^{-ika} - (Dik -Bik)e^{ika} = -\frac{m\alpha}{\hbar^2}(Ae^{-ika}+Be^{ika})$$

$$
\begin{align} \beta (C-A) - D -B& = \frac{im\alpha}{k\hbar^2}(\beta A+ B)\\\end{align}$$

$\Delta \psi'|_{a} = - \frac{m\alpha}{\hbar^2}\psi(a)$ :
$$(F-C)ike^{ika} + Dike^{-ika} = -\frac{m\alpha}{\hbar^2} F^{ika}$$

$$\begin{align}F-C +\beta D = \frac{im\alpha}{k\hbar^2} F\end{align}$$

let $\gamma = \frac{im\alpha}{k\hbar^2}$

According to equation (1) to (4) and assume $A = 1$ for computational ease:

$$\begin{bmatrix}
1 &-\beta &-1 &0\\
0 &1 &\beta &-1\\
-1-\gamma & \beta &-1 &0\\
0 &-1 &\beta &1-\gamma
\end{bmatrix}
\begin{bmatrix}
B\\
C\\
D\\
F\end{bmatrix}
=\begin{bmatrix}
-\beta\\
0\\
(\gamma+1)\beta\\
0
\end{bmatrix}
$$

$$T = \frac{|F|^2}{|A|^2} = |F^2|$$

这周作业是我抄答案都懒得抄完的level. 最后两题对着答案写的都写不明白 , 用 mathematica 倒腾半天才算出来. 🥲🥲🥲

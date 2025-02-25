---
title: Quantom Mechanics Week 1
date: 2025-02-24 22:30:00
categories: Learn
---
# QM Week 1 
# 1.9 
$$\Psi (x,t) =  A e^{-a[(mx^2/\hbar)+ it]}$$
## a 
$$\int |\Psi|^2 dx = A^2\sqrt{\frac{\pi \hbar}{2am}}=1$$  
$A = \left ({\frac{2am}{\pi \hbar }}\right)^{\frac 1 4}$

## b
$$i \hbar \frac{\partial\Psi}{\partial t} = -\frac{\hbar^2}{2m}\frac{\partial^2\Psi}{\partial x^2}+V\Psi$$
$$\frac{\partial \Psi}{\partial t} = -ia \Psi\qquad \frac{\partial^2 \Psi}{\partial x^2} = \left[-\frac{2am}{\hbar} + \left(\frac{2amx}{\hbar}\right)^2\right] \Psi$$
$$\therefore V(x) = 2a^2 m x^2$$

## c
1. Since $x |\Psi|^2$ is an odd function: 
$$<x> = \int_{-\infty}^\infty x |\Psi|^2 dx =0$$

2. 
$$\begin{aligned}<x^2> &= \int_{-\infty}^\infty \Psi^* x^2 \Psi dx\\&=\int_{-\infty}^\infty A^2 x^2 \exp(-2ax^2/\hbar)dx\\&=\frac{\hbar}{4am}\end{aligned}$$

3. $$<p> = m\frac{d<x>}{dt} = 0$$
4. $$<p^2> = \int_{-\infty}^\infty  \Psi^* (-i\hbar\frac{\partial}{\partial x})^2\Psi dx=am\hbar$$
5. $$\sigma_x^2 = <x^2> - <x>^2 =\frac{\hbar}{4am}$$ $$\sigma_p^2 = <p^2> - <p>^2 = am\hbar$$ $$\sigma_p\sigma_x = \frac{\hbar}2\geq\frac{\hbar}2$$ Which is consistent with the uncertainty principle.

# 1.14
## a
$$P_{ab} = \int_{a}^b \Phi^* \Phi dx$$
$$\frac{dP_{ab}}{dt} = \int_{a}^b \frac{\partial}{\partial t}\Phi^* \Phi dx = \frac{i\hbar}{2m}\left(\Psi^* \frac{\partial \Psi}{\partial x}- \frac{\partial \Psi^*}{\partial x}\Psi\right)\Bigg|_a^b = J(a,t) - J(b,t)$$
$J$ describes the probability at point $x$ time $t$ per unit time. It has the unit: $s^{-1}$
## b
$$J(x,t) = \frac{i\hbar}{2m}\left(-\Psi \frac{2amx}{\hbar}\Psi^*+\Psi^* \frac{2amx}{\hbar}\Psi\right)=0$$
# 1.15
$$\begin{aligned}\frac{d}{dt}\int_{-\infty}^\infty  \Psi_1^*\Psi_2dx & = \int_{-\infty}^\infty  \frac{\partial\Psi_1^*}{\partial t}\Psi_2+ \Psi_1^* \frac{\partial \Psi_2}{\partial t}dx\\
&=\int_{-\infty}^\infty\left(-\frac{i\hbar}{2m}\frac{\partial^2\Psi_1^*}{\partial x^2}+\frac{iV}\hbar \Psi_1^*\right)\Psi_2 + \Psi_1\left(\frac{i\hbar}{2m}\frac{\partial^2\Psi_2}{\partial x^2}- \frac{iV}\hbar\Psi_2\right)dx\\
&=\int_{-\infty}^\infty \frac{i\hbar}{2m}\left(-\frac{\partial^2\Psi_1^*}{\partial x^2}\Psi_2+\Psi_1^*\frac{\partial^2\Psi_2}{\partial x^2}\right)dx\\
&=\frac{i\hbar}{2m}\left(-\frac{\partial\Psi_1^*}{\partial x}\Psi_2+\Psi_1^*\frac{\partial\Psi_2}{\partial x}\right)\Bigg |_{-\infty}^\infty\\
&=0
\end{aligned}$$

# 1.16
## a 
$$\int |\Psi|^2 dx = \int_{-a}^a A^2(a^2-x^2)^2dx =1$$ $$A = \sqrt{\frac{15}{16a^5}}$$
## b
$$<x> = \int_{-a}^a xA^2(a^2-x^2)^2dx=0$$
## c
$$\begin{aligned}<p> &= \int_{-a}^a \Psi^* (-i\hbar \frac{\partial }{\partial x})\Psi dx\\
&=\int_{-a}^a 2i\hbar A^2 x(a^2-x^2)dx\\&=0 \end{aligned}$$
## d
$$<x^2> = \int_{-a}^a x^2A^2(a^2-x^2)^2dx=\frac{a^2}{7}$$
## e
$$\begin{aligned}<p^2> &= \int_{-a}^a A^2(a^2-x^2)(-i\hbar \frac{\partial }{\partial x})^2(a^2-x^2)dx\\
&=\int_{-a}^a 2A^2\hbar^2(a^2-x^2)dx\\
&=\frac{5\hbar^2}{2a^2}
\end{aligned}$$
## f
$$\sigma_x = \sqrt{<x^2> - <x>^2 }= \sqrt\frac{a^2}{7}$$
## g
$$\sigma_p = \sqrt{<p^2>-<p>^2} = \sqrt\frac{5\hbar^2}{2a^2}$$
## h
$$\sigma_p\sigma_x = \sqrt{\frac 5 {14}}\hbar\geq \frac \hbar 2$$

# 1.17
## a
$$\begin{aligned}
\frac{dP}{dt} &= \int \frac{\partial \Psi^*}{\partial x}\Psi+\Psi^* \frac{\partial \Psi}{\partial x}dx\\
&=\int \left(\frac{-\hbar i}{2m}\frac{\partial^2 \Psi^*}{\partial x^2} + \frac{V_0i\Psi^*}{\hbar} - \frac{\Gamma \Psi^*}{\hbar}\right)\Psi + \Psi^* \left(\frac{\hbar i}{2m}\frac{\partial^2 \Psi}{\partial x^2} - \frac{V_0i\Psi}{\hbar} - \frac{\Gamma i \Psi}{\hbar}\right)dx\\
&=\int \frac{i\hbar}{2m}\left(-\frac{\partial^2 \Psi^*}{\partial x^2}\Psi + \Psi^* \frac{\partial^2 \Psi}{\partial x^2}\right) - \frac{2\Gamma}\hbar \Psi^*\Psi dx\\
&=\int \frac{i\hbar}{2m}\left(-\frac{\partial^2 \Psi^*}{\partial x^2}\Psi + \Psi^* \frac{\partial^2 \Psi}{\partial x^2}\right)dx - \frac{2\Gamma}\hbar \int\Psi^*\Psi dx\\
&=- \frac{2\Gamma}\hbar P\end{aligned}$$ 
## b
Solve the ODE of (a):
$$ P(t) = c \exp(-\frac{2\Gamma}\hbar t)$$
assume that $c=1$, the lifespan $\tau$ is: $$\tau =\frac\hbar{2\Gamma}$$
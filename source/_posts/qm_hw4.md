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

# 2.28
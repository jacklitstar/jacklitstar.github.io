# QM Week 2
# 2.4
1. 
$$\begin{aligned}
<x> &= \int_0^a \Psi_n^* x \Psi_n dx \\
&= \int_0^a \frac{2}{a} x \sin^2\left(\frac{n\pi}{a} x\right) dx \\
&= \frac{a}{2} - \frac{1}{a} \left[\frac{a}{2n\pi} x \sin\left(\frac{2n\pi}{a} x\right) + \left(\frac{a}{2n\pi}\right)^2 \cos\left(\frac{2n\pi}{a} x\right)\right] \Bigg|_0^a\\
&= \frac{a}{2}
\end{aligned}$$
2. 
$$\begin{aligned}
<x^2> &= \int_0^a \Psi_n^* x^2 \Psi_n \, dx \\
&= \int_0^a \frac{2}{a} x^2 \sin^2\left(\frac{n\pi}{a} x\right) dx \\
&= \frac{2}{a} \int_0^a x^2 \left[\frac{1}{2} - \frac{1}{2}\cos\left(\frac{2n\pi}{a} x\right)\right] dx \\
&= \frac{a^2}{3} - \frac{a^2}{2n^2\pi^2}
\end{aligned}$$
3. 
$$<p> = \int_0^a -\frac{2}a\sin(\frac{n\pi}a x)i\hbar \frac{n\pi}a \cos(\frac{n\pi}a x)dx = 0$$
4. 
$$<p^2> = \hbar^2(\frac{n\pi}a)^2 \int_0^a \Psi^*\Psi dx =(\frac{n\hbar\pi}a)^2 $$
5. 
$$\sigma_x = a\sqrt{\frac{1}{12} - \frac{1}{2n^2\pi^2}}$$
6. 
$$\sigma_p = \frac{n\hbar \pi}a$$
7. 
$$\sigma_x\sigma_p = \frac\hbar 2 \sqrt{\frac{n^2\pi^2}3 - 2}\geq \frac\hbar 2,\quad n = 1,2,\ldots$$
When $n = 1$, $\sigma_x\sigma_p$ is the smallest.

# 2.5
1. 
Since $\omega = \pi^2\hbar/2ma^2$ : $$E_n = \frac{n^2\pi^2\hbar^2}{2ma^2} = n^2\omega\hbar$$
$$ 1 = \int A^2 (\psi_1^*\psi_1 + \psi_1^*\psi_2+\psi_2^*\psi_1+\psi_2^*\psi_2)dx = 2A^2\\ A = \frac{1}{\sqrt 2}$$
2. 
$$\begin{aligned}\Psi(x,t) &= \frac 1{\sqrt{2}}[\psi_1 e^{-i\hbar E_1t/\hbar} + \psi_2 e^{-iE_2t/\hbar}]\\
&=\frac 1{\sqrt{2}}[\psi_1 e^{-i\omega t} + \psi_2 e^{-4i\omega t}]\\
&=\frac{1}{\sqrt a}[\sin(\frac{\pi x }a)e^{-i\omega t} + \sin(\frac{2\pi x }a)e^{-4i\omega t}]\end{aligned}$$

$$|\Psi(x,t)|^2 = \frac{1}{a}[\sin^2(\frac\pi a x )+ \sin^2(\frac {2\pi}a x ) +2\sin(\frac\pi a x )\sin(\frac {2\pi}a x )\cos(3\omega t)]$$

3. 
$$\begin{aligned}<x> &= \int \Psi^* x\Psi dx\\
& = \frac{1}2\int x[\psi_1^*\psi_1 + \psi_2^*\psi_2+2\psi_1^*\psi_2 e^{-3i\omega t}]\, dx\\
&= \frac 1 2 \int \psi_1^* x \psi_1 dx + \frac 1 2\int \psi_2^* x \psi_2 dx + \int x\psi_1^*\psi_2 e^{-3i\omega t}\, dx\\
& = \frac a 4+ \frac a 4 -\frac{16a}{9\pi^2}\cos(3\omega t) \\
& = \frac a 2 - \frac{16a}{9\pi^2}\cos(3\omega t)
\end{aligned}$$

4. $$<p> = m\frac{d<x>}{dt}= \frac{8\hbar}{3a}\sin(3\omega t)$$

5. $$E_n = \frac{n^2\pi^2\hbar^2}{2ma^2} \quad \text{for: } n = 1,2$$
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
1. 
$$1 = \int_0^a |\Psi|^2 dx = 2\int_0^{\frac a 2} (Ax)^2 dx \implies A = \sqrt{\frac{12}{a^3}}$$
2. $\sum c_n \sqrt\frac{2}{a}\sin(\frac{n\pi}a x)$ is the Fourier Expansion of $\Psi(x,0)$ , therefore: 
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
3. 
$$c_1 =\frac{4\sqrt 6}{\pi^2}, \quad P_1 = |c_1|^2 = \frac{96}{\pi^4} $$
4. $$<H> = \sum_n P_n E_n$$

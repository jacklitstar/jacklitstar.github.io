---
title: Quantom Mechanics 5
date: 2025-04-07 23:00:00
categories: Learn
---

# QMHW 5

2.34, 2.47, 2.52
3.2, 3.4, 3.13, 3.32
3.23, 3.26, 3.37, 3.46

# 2.34
## a
The schrodinger equation is 
$$ \begin{cases}-\frac{\hbar^2}{2m} \nabla^2 \psi  = E \psi & x<0 \\-\frac{\hbar^2}{2m} \nabla^2 \psi  + V_0 \psi = E \psi & x>0
\end{cases}$$
1. $E \leq 0$
   - When $x<0$, let $\kappa = \frac{\sqrt{-2mE}}{\hbar}$, the wave function is $\psi(x) = Be^{\kappa x}$ , there is no reflection for a wave traveling from left to right.
   - When $x>0$, let $l = \frac{\sqrt{2m(V_0 -E)}}{\hbar}$, the wave function is $\psi(x) = Ce^{-lx}$, there is no reflection.
2. $E > 0$
   - When $x<0$, let $k = \frac{\sqrt{2mE}}{\hbar}$, the wave function is $\psi(x) = Ae^{ikx} + Be^{-ikx}$.
   - When $x>0$, let $l = \frac{\sqrt{2m(V_0 -E)}}{\hbar}$, the wave function is $\psi(x) = Ce^{-lx}$.  
The continuity of $\psi, d\psi/dx$ shows: 
$$A+B = C\\ ikA -ikB = -lC$$ The reflection coefficient is $R = 1$

## b 
$E> V_0$
- $x< 0, \psi = Ae^{ikx} +Be^{-ikx}$
- $x>0,\psi = C^{ilx} + D^{-ilx}$
The continuity of $\psi, d\psi/dx$ shows:
$$A+B = C+D \\ Ak - Bk = Cl - Dl$$ Assume that $D = 0$, then we have $R = (\frac{k-l}{k+l})^2$

## c
1. $E> V_0$
The speed of the quantom is 
$$\begin{cases}v_0 = \sqrt\frac{E - V_0}{2m}& x>0\\v_1 = \sqrt\frac{E}{2m} & x<0\end{cases}$$
$$T = \frac {\int \psi^* \psi dx}{\int \psi^* \psi dx} =  \frac {\int_{t_0}^{t_0 + \delta t} \psi^* \psi \,v_0dt}{\int_{t_0}^{t_0 + \delta t} \psi^* \psi \,v_1dt} = \frac{v_0}{v_1} \frac{|C|^2}{|A|^2}$$
2. $E<V_0$
   Since $T+R =1$ and $R = 1$, then $T=0$
## d
$$T = \frac{4lk}{(k+l)^2}\\ R = \frac{(k-l)^2}{(k+l)^2}\\
T+R = 1$$

# 2.47

# 2.52
$\mathrm{sech} (x) = \frac{2}{e^x + e^{-x}}$
## a

## b
$$A^2 \int_{-\infty}^\infty \mathrm{sech}^2(ax) dx = 2 A^2/a\implies A = \sqrt \frac{a}2$$

$\psi_0$ does satsify the schrodinger equation.

## c
The derivitive formula of $\mathrm{sech}$ is $\frac{d}{dx}\mathrm{tanh}(ax) = a\mathrm{sech}^2(ax)$

$$\frac{d\psi_k}{dx} = \frac{A e^{ikx}}{ik+a} [-a^2 \mathrm{sech}^2(ax) - k^2 - aik\tanh (ax)]$$

$$\frac{d^2\psi_k}{dx^2} =\frac{A e^{ikx}}{ik+a}[-a^2ik \mathrm{sech} (ax) - ik^3 +ak^2\tanh(ax) +2a^3 \mathrm{sech}^2(ax)\tanh(ax) -a^2 ik \mathrm{sech}^2(ax)] $$

It satisfies the schrodinger equation.

# 3.2
## a
$f$ needs  to be square integrable in $(0,1)$ , $f^2(x) = x^{2v}$ , 
$$\int_0^1 x^{2v} dx < \infty \implies -\frac 1 2<v$$
## b
$v = 1/2 > -1/2$, $f$ is in Hilbert space.
$v = 3/2 > -1/2$, $f$ is in Hilbert space.
$v = -1/2 \leq -1/2$, $f$ is not in Hilbert space.

# 3.4
## a
for hermitian $Q_1,Q_2$ and $ \forall f,g$ 
$$ \braket{f|(Q_1+Q_2)g} = \braket{f|Q_1g}+ \braket{f,Q_2g} = \braket{Q_1f|g}+\braket{Q_2f|g} = \braket{(Q_1+Q_2)f|g}$$

## b
$$\alpha (\hat Q f)^* = (\alpha\hat Q f)^*\implies \alpha\in \R$$

## c
$$\hat Q_1\hat Q_2 = \hat Q_2 \hat Q_1$$

## d

$\hat x = x $ is real, thus a hermitian operator.
$$\begin{aligned}\braket{f|\hat H g} &=\int f^* (-\frac{\hbar^2}{2m}\nabla^2 g + Vg) \, dx \\
& = \int V f^* g -( \frac{\hbar^2}{2m}\nabla^2 f)^*gdx \\
& = \braket{\hat H f|g}
\end{aligned}$$

# 3.13
Notice that 
$$\Psi(x,t) = \frac{1}{\sqrt{2\pi\hbar}}\int_{-\infty}^\infty e^{ipx/\hbar}\Phi(p,t) dp$$

$$\begin{aligned}
\braket x & = \int \Psi^* x \Psi dx \\
& =\frac{1}{2\pi\hbar} \int\left\{ \left[\int e^{ip_1x/\hbar}\Phi dp_1\right]^* x \left[\int e^{ipx/\hbar}\Phi dp\right] \right\}dx\\
& = \frac{1}{2\pi\hbar} \int\left\{ \left[\int e^{-ip_1x/\hbar}\Phi^* dp_1\right] \left[\int xe^{ipx/\hbar}\Phi dp\right] \right\}dx\\
& = \frac{1}{2\pi\hbar} \int\left\{ \left[\int e^{-ip_1x/\hbar}\Phi^* dp_1\right] \left[\int (-i\hbar \frac{\partial}{\partial p})e^{ipx/\hbar}\Phi dp\right] \right\}dx\\
& \qquad \text{since } i\hbar \frac{\partial}{\partial p} \text{is hermitan, therefore:}\\
& = \frac{1}{2\pi\hbar} \int\left\{ \left[\int e^{-ip_1x/\hbar}\Phi^* dp_1\right] \left[\int e^{ipx/\hbar}(i\hbar \frac{\partial}{\partial p})\Phi dp\right] \right\}dx\\
&= \int\frac{1}{2\pi} e^{i(p-p_1)(x/\hbar)}d(x/\hbar) \;\int\int  \Phi^* (i\hbar \frac{\partial}{\partial p})\Phi dp_1dp\\
&=\int\int  \delta(p-p_1)\Phi^* (i\hbar \frac{\partial}{\partial p})\Phi dp_1dp\\
& = \int \Phi^* (i\hbar \frac{\partial}{\partial p})\Phi  dp \qquad \square
\end{aligned}
$$



# 3.32
$\hat Q^\dag = - \hat Q$
## a
$$\braket {\hat Q} = \braket{\psi|\hat Q\psi}= \braket{\hat Q^\dag\psi|\psi} = \braket{-\hat Q\psi|\psi}\\
\braket {\hat Q}^* = \braket{-\hat Q\psi|\psi}^* = \braket{-\hat Q^*\psi^*|\psi^*} = \braket{\psi | -\hat Q\psi} = -\braket{\psi|\hat Q\psi} = -\braket{\hat Q}$$

if $\braket{\hat Q} = c$ and $c^* = -c$ , then $c = a i ,a \in \R$

## b
$\psi$ is an eigenfunction and $\lambda$ being its eigenvalue.
$$\hat Q \psi = \lambda\psi\\
\begin{aligned}
\braket {\psi| \hat Q \psi } &= \braket{-\hat Q \psi| \psi} = -\lambda^* \braket{\psi|\psi}\\
&=\braket{\psi| \lambda\psi} = \lambda\braket{\psi|\psi}\end{aligned}
$$

$\therefore \lambda = -\lambda^*$

## c
$\hat Q \psi_1 = \lambda_1\psi_1,\hat Q\psi_2 = \lambda_2\psi_2$
$$\braket{\psi_1|\psi_2} = \frac{1}{\lambda_2} \braket{\psi_1|\lambda_2\psi_2}=\frac{1}{\lambda_2}\braket{\psi_1|\hat Q\psi_2} = \frac{1}{\lambda_2}\braket{-\hat Q\psi_1|\psi_2} = \frac{\lambda_1}{\lambda_2} \braket{\psi_1|\psi_2}$$

This remains true for any eigenfunctions $\psi_1,\psi_2$ , therefore $\braket{\psi_1|\psi_2} = 0$ is needed when $\lambda_1 \neq \lambda_2$

## d
$$\begin{aligned}
\braket{\psi|(\hat H \hat K - \hat K\hat H)\psi} &= \braket{\psi|\hat H \hat K \psi - \hat K \hat H \psi}\\
&= \braket{\psi|\hat H \hat K \psi} - \braket{\psi|\hat K \hat H \psi}\\
&= \braket{\hat H \psi| \hat K \psi} - \braket{\hat K \psi| \hat H \psi}\\
&=\braket{\hat K\hat H \psi| \psi} - \braket{\hat H \hat K \psi| \psi}\\
&= \braket{(\hat K\hat H - \hat H\hat K)\psi| \psi}\\
\text{notice }&: (\hat H \hat K - \hat K\hat H) = -(\hat K\hat H - \hat H\hat K)
\end{aligned}$$

## e
if $\hat Q = \hat A + \hat B$
$$\braket{\hat Q^\dag \psi | \psi} = \braket{\psi| \hat Q\psi} = \braket{\psi|\hat A \psi}+\braket{\psi|\hat B \psi} = \braket{\hat A\psi|\psi}+\braket{-\hat B \psi|\psi} = \braket{(\hat A - \hat B) \psi|\psi}\\
\implies \hat Q^\dag = \hat A - \hat B\qquad$$

$$\therefore \hat A = \frac{\hat Q + \hat Q^\dag }2,\; \hat B = \frac{\hat Q - \hat Q^\dag}{2}$$

# 3.23
notice that $\braket{\alpha|\alpha} = 1 , \quad \hat P^2 = (\ket{\alpha}\bra{\alpha})(\ket{\alpha}\bra{\alpha}) = \ket{\alpha}\braket{\alpha|\alpha}\bra{\alpha} = \ket{\alpha}\bra{\alpha} = \hat P$
$\lambda^2\psi = \hat P^2 \psi = \hat P \psi = \lambda \psi\implies \lambda^2 = \lambda\implies \lambda = 0 \text{ or } 1$
when $\lambda = 0$, $\psi \in \mathrm{span}\{\ket{\alpha}\}^{\bot}$
when $\lambda = 1$, $\psi \in \mathrm{span}\{\ket{\alpha}\}$

# 3.26
## a
the bra is the conjugate transpose of ket, therefore:
$\bra{\alpha} = -i \bra 1 - 2 \bra 2 + i \bra 3 $
$\bra \beta = -i \bra 1 + 2 \bra 3$

## b
$$\braket{\alpha | \beta} = -1 + 2i , \quad \braket{\beta|\alpha} = -1 -2i \implies \braket{\beta|\alpha} = \braket{\alpha | \beta}^*  $$

## c
$$
A = \begin{bmatrix}
1 & 0 &2i\\
2i &0 &-4\\
-1 &0 &-2i
\end{bmatrix}
$$
it is not hermitian.

# 3.37

# 3.46
改天补上 😭
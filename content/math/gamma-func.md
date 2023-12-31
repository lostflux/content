---
title: The Gamma Function
description: |
  The Gamma function, $\Gamma$, is at the heart of important results in mathematics
  including the [Riemann hypothesis](https://en.wikipedia.org/wiki/Riemann_hypothesis).
  
  It is defined as follows:

  ```math
  \begin{aligned}
    \Gamma \;\colon \CC &\to \CC \\
    s &\mapsto \int_0^\infty t^{s-1} e^{-t} \, \dd t
  \end{aligned}
  ```
  
  What does it represent, and why is it touted as an
  [analytic continuation][analytic-continuation]
  of the factorial function?

  [riemann-hypothesis]: https://en.wikipedia.org/wiki/Riemann_hypothesis
  [analytic-continuation]: https://en.wikipedia.org/wiki/Analytic_continuation

date: 2023-12-30 23:00:00
---


where $\Gamma$ is the _Gamma function_, a generalization of the factorial
function to the complex numbers:

```math
\begin{aligned}
\Gamma(s) &= \int_0^\infty t^{s-1} e^{-t} \, \dd t
\end{aligned}
```


For $n \in \NN$, $\Gamma(n) = (n-1)!$.

## Special Case

Consider $\Gamma(n)$ for $n = 1$.
The integral has a surprisingly simple simplification:
  
```math
\begin{aligned}
\Gamma(1) &= \int_0^\infty t^{1-1} e^{-t} \, \dd t \\

&= \int_0^\infty e^{-t} \, \dd t \;\; \text{(since $t^0 = 1$)} \\

&= \biggl [ -e^{-t} \biggr ]_0^\infty \\

&= 0 - (-1) \\

&= 1

\end{aligned}
```

## General Case

Take $n$ to be an arbitrary positive integer, i.e. $n \in \NN$ and $n > 1$.
To prove that $\Gamma$ is indeed equivalent to the factorial function
(albeit shifted by $1$), we need to show that $\Gamma(n+1) = n \Gamma(n)$.

Revisit the definition of $\Gamma$, applied to $n+1$:

```math
\begin{aligned}
\Gamma(n+1) &= \int_0^\infty t^{n} e^{-t} \, \dd t \\
\end{aligned}
```

This integral can be simplified using the rule for integration by parts:

```math
\begin{aligned}
\int u \, \dd v = uv - \int v \, \dd u
\end{aligned}
```

Take $u = t^n$ and $\dd v = e^{-t} \, \dd t$; then:

```math
\begin{aligned}
\dd u &= \frac{\dd}{\dd t} t^n = n t^{n-1} \\
v &= \int e^{-t} \, \dd t = -e^{-t} \\ \\

\mathrm{Thus,} \\ \\

\int_0^\infty \underbrace{t^n}_{u} \cdot \underbrace{\left(e^{-t} \, \dd t \right)}_{\dd v}
&= \underbrace{\biggl [ -t^n e^{-t} \biggr ]_0^\infty}_{uv}
- \int_0^\infty \underbrace{nt^{n-1}}_{v} \cdot \underbrace{\left(- e^{-t}  \, \dd t  \right)}_{\dd u}\\ \\

&= (0 - 0) - \int_0^\infty -nt^{n-1} e^{-t} \, \dd t \\

&= n \int_0^\infty t^{n-1} e^{-t} \, \dd t \\ \\

&= n \Gamma(n) \\
\end{aligned}
```

## Proof by Induction

So far, we have seen the following results:

```math
\begin{aligned}
\Gamma(1) &= 1 \\
\Gamma(n+1) &= n \Gamma(n) \; \; \text{for $n \in \NN_{>1}$}
\end{aligned}
```

By [induction][induction] on $n$, we have:,
for $n \in \NN$ (i.e. $n$ is a _positive integer_) we have:
  
```math
\begin{aligned}
\Gamma(n+1) &= (n) \Gamma(n) \\
&= n \cdot (n-1) \Gamma(n-1) \\
&= n \cdot (n-1) \cdot (n-2) \Gamma(n-2) \\
&\vdots\\
&= n \cdot (n-1) \cdot (n-2) \cdot \ldots \cdot 2 \cdot 1 \Gamma(1) \\
&= n \cdot (n-1) \cdot (n-2) \cdot \ldots \cdot 2 \cdot 1 \cdot 1 \\
&= n!
\end{aligned}
```

::alert
$\Gamma$ was not intended to be a generalization of the factorial function.
The result was a somewhat accidental one, albeit useful.
::

## Analytic Continuation

### Positive Non-integer Inputs

What happens when non-integer inputs are provided to $\Gamma$?

```math
\begin{aligned}
\Gamma(s) &= \int_0^\infty t^{s-1} e^{-t} \, \dd t
\end{aligned}
```

Recall the simplification we made using integration by parts:

```math
\begin{aligned}
\int u \, \dd v = uv - \int v \, \dd u

\end{aligned}
```

```math
\begin{aligned}
\Gamma(x) &= \frac{1}{x} \Gamma(x+1)
\end{aligned}
```

[analytic-continuation]:  https://en.wikipedia.org/wiki/Analytic_continuation
[riemann-hypothesis]:     https://en.wikipedia.org/wiki/Riemann_hypothesis
[induction]:              https://en.wikipedia.org/wiki/Mathematical_induction

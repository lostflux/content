---
title: The Riemann Hypothesis
description: |
  The Riemann zeta function, $\zeta$,  is at the heart of the famed Riemann hypothesis,
  one of the millenium prize problems by the
  [Clay Mathematics Institute](https://www.claymath.org/millennium-problems).
  It is defined as follows:

  ```math
  \begin{aligned}
    \zeta \;\colon \CC &\to \CC \\
    s &\mapsto \sum_{n=1}^\infty \frac{1}{n^s}
    = \frac{1}{1^s} + \frac{1}{2^s} + \frac{1}{3^s} + \dotsi \\
  \end{aligned}
  ```
  
  Yet, the hypothesis remains unproven.
  What makes this function so interesting?

date: 2023-12-30 23:00:00
---

The complex field, denoted $\CC$, is the set of all the complex
numbers of the form $\sigma + it$, where $\sigma$ and $t$ are real numbers.
Addition and multiplication over the field are defined as follows:

```math
\begin{aligned}
  (a + ib) + (c + id) &= (a + c) + i(b + d) \\
  (a + ib) \times (c + id) &= (ac - bd) + i(ad + bc)
\end{aligned}
```

<!-- Exponentiation is defined as follows:

```math
\begin{aligned}
  (a + ib)^n &= \sum_{k=0}^n \binom{n}{k} a^{n-k} (ib)^k \\
  (a + ib)^{c + id} &= e^{(c + id) \ln(a + ib)} \\
\end{aligned}
``` -->

Over $\CC$, we define the real function $\mathrm{Re}(s)$ as follows:

```math
\begin{aligned}
\Re \ \colon \CC &\to \RR \\
a + ib &\mapsto a.
\end{aligned}
```

For $\Re(s) > 1$, $\zeta$ is then defined as such:

```math
\begin{aligned}
\zeta(s) &= \sum_{n=1}^\infty \frac{1}{n^s}
= \frac{1}{1^s} + \frac{1}{2^s} + \frac{1}{3^s} + \dotsi. \\
\end{aligned}
```

But this equation diverges for $\Re(s) \leq 1$ and
has a singularity at $\Re(s) = 1$.
We instead use _analytic continuation_ to define $\zeta$ over the entire $\CC$
as follows:

```math
\begin{aligned}
\zeta(s) &= \sum_{n=1}^\infty \frac{1}{n^s}
= \frac{1}{\Gamma(s)} \int_0^\infty \frac{x^{s-1}}{e^x - 1} \,\dd x
\end{aligned}
```

where $\Gamma$ is the _Gamma function_, a generalization of the factorial
function to the complex numbers:

```math
\begin{aligned}
\Gamma(s) &= \int_0^\infty t^{s-1} e^{-t} \, \dd t
\end{aligned}
```

::alert
For $n \in \NN$, $\Gamma(n) = (n-1)!$.

### Proof

First, note that $\Gamma(1) = 1$:
  
```math
\begin{aligned}
\Gamma(1) &= \int_0^\infty t^{1-1} e^{-t} \, \dd t = \biggl [ e^{-t} \biggr ]_0^\infty = 1 \\
\Gamma(n+1) &= \int_0^\infty t^{n} e^{-t} \, \dd t \\

\end{aligned}
```

We can then use integration by parts to show that $\Gamma(n+1) = n \Gamma(n)$:

```math
\begin{aligned}
\Gamma(n+1) &= \int_0^\infty t^{n} e^{-t} \, \dd t \\
\end{aligned}
```

Integration by parts:
```math
\begin{aligned}
\int u \, \dd v = uv - \int v \, \dd u
\end{aligned}
```

Taking $u = t^n$ and $\dd v = e^{-t} \, \dd t$:

```math
\begin{aligned}
\int_0^\infty \biggl( t^n \cdot \left(e^{-t} \, \dd t \right) \biggr) &= \biggl [ -t^n e^{-t} \biggr ]_0^\infty
- \int_0^\infty \biggl( \left( nt^{n-1} \right) \left(- e^{-t} \right) \, \dd t \biggr) \\

&= (0 - 0) - \int_0^\infty \biggl( -nt^{n-1} e^{-t} \, \dd t \biggr) \\

&= n \int_0^\infty t^{n-1} e^{-t} \, \dd t \\ \\

&= n \Gamma(n) \\
\end{aligned}
```

Thus, [by induction](https://en.wikipedia.org/wiki/Mathematical_induction):
  
```math
\begin{aligned}
\Gamma(n) &= (n-1) \Gamma(n-1) \\
&= (n-1) (n-2) \Gamma(n-2) \\
&\vdots\\
&= (n-1) (n-2) \dotsm 2 \cdot 1 \cdot \Gamma(1) \\
&= (n-1) (n-2) \dotsm 2 \cdot 1 \cdot 1 \\
&= (n-1)!
\end{aligned}
```

::

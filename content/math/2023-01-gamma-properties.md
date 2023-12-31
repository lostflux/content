---
title: the gamma extensions
description: |
  The Gamma function, $\Gamma$, is at the heart of important results in mathematics
  including the [Riemann hypothesis][riemann-hypothesis].
  
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

  [riemann-hypothesis]:    /math/2023-02-riemann-zeta-properties
  [analytic-continuation]: https://en.wikipedia.org/wiki/Analytic_continuation

date: 2023-12-29 23:00:00
---

The Gamma function, $\Gamma$, is a curious mathematical creature
that pops up in many, seemingly unrelated places.
Yet it defies naive intuition;

1. Over the positive integers, it simplifies to the factorial function,
shifted by $1$.
2. Over the negative integers, it diverges.
3. At $0$, it diverges.
4. It has even more interesting behavior over non-integer
   fractions and complex numbers.

What makes $\Gamma$ so interesting?

## Definition

The Gamma function is defined as follows:

```math
\begin{aligned}
\Gamma \;\colon \CC &\to \CC \\ \\
\Gamma(s) &= \int_0^\infty t^{s-1} e^{-t} \, \dd t
\end{aligned}
```

It converges for all complex numbers $s$ with positive real part
(i.e. $\Re(s) > 0$). It also converges for complex numbers with
negative real part (i.e. $\Re(s) < 0$) except where
$\Re(s)$ is a negative integer or $0$.

When $\Re(s)$ is zero or a negative integer and the imaginary part
of $s$ is $0$, then $\Gamma(s)$ diverges and is undefined.

## Over the Positive Integers

Note that the integers are embedded in the complex numbers
as the subset obtained by setting the imaginary part to $0$
and restricting the real part accordingly.

Over the positive integers, $\Gamma$ has two general properties,
outlined below.

### Special Case

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

### General Case: Positive Integers

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

\Gamma(n+1) &= \int_0^\infty t^{n} e^{-t} \, \dd t \\
&= \int_0^\infty \underbrace{t^n}_{u} \cdot \underbrace{e^{-t}}_{\dd v} \, \dd t \\
&= \underbrace{\biggl [ -t^n e^{-t} \biggr ]_0^\infty}_{uv}
- \int_0^\infty \underbrace{nt^{n-1}}_{v} \cdot \underbrace{\left(- e^{-t}\right)}_{\dd u}  \, \dd t\\ \\

&= (0 - 0) - \int_0^\infty -nt^{n-1} e^{-t} \, \dd t \\

&= n \int_0^\infty t^{n-1} e^{-t} \, \dd t \\ \\

&= n \cdot \Gamma(n) \\
\end{aligned}
```

This is an important identity, usually expressed in any
of the following two forms:
  
```math
\begin{aligned}
\Gamma(n+1) &= n \Gamma(n) \\
\Gamma(n) &= \frac{1}{n} \Gamma(n+1)
\end{aligned}
```

### Proof by Induction

So far, we have seen the following results:

```math
\begin{aligned}
\Gamma(1) &= 1 \equiv 0! \\
\Gamma(n+1) &= n \Gamma(n) \; \; \text{for $n \in \NN_{>1}$}
\end{aligned}
```

By [induction][induction] on $n$,
suppose we know that $\Gamma(n) = (n-1)!$
(with the base-case being $\Gamma(1) = 0!$).
We can compute $\Gamma(n+1)$ as follows:
  
```math
\begin{aligned}
\Gamma(n+1) &= n \cdot \Gamma(n) \\
&= n \cdot (n-1) ! \\
&= n!
\end{aligned}
```

::alert
$\Gamma$ was not intended to be a generalization of the factorial function.
The result was a somewhat accidental one, albeit useful.
::

## Over the Reals

By restricting $\Gamma$ to the positive integers, we discovered that:
  
```math
\begin{aligned}
\Gamma(n) &= (n-1)! \; \; \text{for $n \in \NN$}
\end{aligned}
```

But what happens when we plug in a fraction, say $\displaystyle \frac{3}{2}$?

```math
\begin{aligned}
\Gamma \left( \frac{3}{2} \right) &= \Gamma(\frac{1}{2} + 1) \\
&= \frac{1}{2} \cdot \Gamma(\frac{1}{2}) \\
&= \frac{1}{2} \int_0^\infty t^{-\frac{1}{2}} e^{-t} \, \dd t \\
\end{aligned}
```

To simplify the integral, let's try to get rid of the $\displaystyle t^{-\frac{1}{2}}$ term
by substituting $t = x^2$:

```math
\begin{aligned}
\Gamma\left(\frac{3}{2}\right) &= \frac{1}{2} \int_0^\infty t^{-\frac{1}{2}} e^{-x^2} \cdot 2t^\frac{1}{2} \, \dd x \\
&= \int_0^\infty e^{-x^2} \, \dd x \\
\end{aligned}
```

This is a familiar integral, known as the [Gaussian integral][gaussian-integral]:

```math
\begin{aligned}
I(a) &= \int_a^a e^{-x^2} \, \dd x \\ \\
I(\infty) &= \int_\infty^\infty e^{-x^2} \, \dd x \\ \\

I^2(\infty) &= \left( \int_{-\infty}^\infty e^{-x^2} \, \dd x \right) \cdot \left( \int_{-\infty}^\infty e^{-y^2} \, \dd y \right) \\

&= \int_{-\infty}^\infty \int_{-\infty}^\infty e^{-(x^2 + y^2)} \, \dd x \, \dd y \\

&= \int_{-\infty}^\infty \int_{-\infty}^\infty e^{-r^2} \, r\,  \dd r \, \dd \theta \\

&= \int_0^{2\pi} \int_0^\infty e^{-r^2} \, r\,  \dd r \, \dd \theta \\

&= 2\pi \int_0^\infty e^{-r^2} \, r\,  \dd r \\

&= 2\pi \int_{-\infty}^0 \frac{1}{2} e^{u} \, \dd u \;\; \text{(substituting $u = -r^2$)} \\

&= \pi \biggl [ e^u \biggr ]_{-\infty}^0 \\

&= \pi (e^0 - e^{-\infty}) \\

&= \pi (1 - 0) \\ &= \pi
\end{aligned}
```

Since $\Gamma(\frac{3}{2})$ restricts the integration to $[0, \infty)$
and the function is [even][even-function]:

```math
\begin{aligned}
\Gamma\left(\frac{3}{2}\right) &= \frac{1}{2} \int_{-\infty}^\infty e^{-x^2} \, \dd x \\
&= \frac{1}{2} \cdot \sqrt{I^2(\infty)} \\
&= \frac{\sqrt{\pi}}{2} \\
\end{aligned}
```
  
Other fractions of the form $\displaystyle \left(n + \frac{1}{2} \right),\, n \in \NN$ have similar results simplifications:

```math
\begin{aligned}
\Gamma\left(\frac{1}{2}\right) &= \sqrt{\pi} \\
\Gamma\left(\frac{3}{2}\right) &= \frac{1}{2} \sqrt{\pi} \\
\Gamma\left(\frac{5}{2}\right) &= \frac{3}{4} \sqrt{\pi} \\
\Gamma\left(\frac{7}{2}\right) &= \frac{15}{8} \sqrt{\pi} \\
\Gamma\left(\frac{9}{2}\right) &= \frac{105}{16} \sqrt{\pi} \\
\vdots
\end{aligned}
```

In general,

```math
\begin{aligned}
\Gamma\parens{\frac{1}{n}} \sim n - \gamma
\end{aligned}
```

where $\gamma$ is the [Euler-Mascheroni constant](https://en.wikipedia.org/wiki/Euler%E2%80%93Mascheroni_constant) and $\sim$ denotes
[asymptotic equivalence][asymptotic-equivalence].

but unfortunately
the integral has to be computed or simplified directly for each case.

## Over the Complexes

$\Gamma$ has a [meromorphic](https://en.wikipedia.org/wiki/Meromorphic_function)
extension to the complex numbers, with simple poles at the non-positive integers
and $0$. It is defined with the same rules and the relation
```math
\displaystyle \Gamma(s+1) = s \Gamma(s)
```
holds for all complex numbers $s$.
For example;

```math
\begin{aligned}
\Gamma(i) &= \parens{-1 + i}! \approx -0.1549 - 0.4980i
\end{aligned}
```

Various values of $\Gamma$ are tabulated [here][gamma-selected-values].

For some useful applications of $\Gamma$ in the Riemann zeta function,
see [this post][riemann-hypothesis].

[analytic-continuation]:  https://en.wikipedia.org/wiki/Analytic_continuation
[riemann-hypothesis]:     /math/2023-02-riemann-zeta-properties
[induction]:              https://en.wikipedia.org/wiki/Mathematical_induction
[gaussian-integral]:      https://en.wikipedia.org/wiki/Gaussian_integral
[even-function]:          https://en.wikipedia.org/wiki/Even_and_odd_functions
[asymptotic-equivalence]: https://en.wikipedia.org/wiki/Asymptotic_equivalence
[gamma-selected-values]:  https://en.wikipedia.org/wiki/Particular_values_of_the_gamma_function

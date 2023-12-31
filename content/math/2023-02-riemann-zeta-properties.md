---
title: the riemann hypothesis
description: |
  The Riemann hypothesis is considered one of the most important unsolved problems
  in pure mathematics, with wide-ranging applications across quantum physics,
  cryptography, number theory, and other fields.
  It is one of the [millenium prize problems][millenium-prize] by the
  [Clay Mathematics Institute][clay-institute].

  At the heart of the hypothesis is the Riemann zeta function;

  ```math
  \begin{aligned}
    \zeta \;\colon \CC &\to \CC \\
    s &\mapsto \sum_{n=1}^\infty \frac{1}{n^s}
    = \frac{1}{1^s} + \frac{1}{2^s} + \frac{1}{3^s} + \dotsi \\
  \end{aligned}
  ```
  
  What makes this function so interesting and consequential across
  scientific fields?

  [millenium-prize]: https://www.claymath.org/millennium-problems
  [clay-institute]:  https://www.claymath.org/

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

## Real Part Function

Over $\CC$, we define the real function $\mathrm{Re}(s)$ as follows:

```math
\begin{aligned}
\Re \ \colon \CC &\to \RR \\
a + ib &\mapsto a.
\end{aligned}
```

## Riemann Zeta Definition

For $\Re(s) > 1$, $\zeta$ is defined as an [absolutely convergent][abs-convergence]
infinite series that maps values from $\CC$ unto itself,
with the exception of $s = 1$ where the sum diverges
and $\zeta$ has a pole[^pole].

```math
\begin{aligned}
\zeta(s) &= \sum_{n=1}^\infty \frac{1}{n^s}
= \frac{1}{\Gamma(s)} \int_0^\infty \frac{x^{s-1}}{e^x - 1} \,\dd x
\end{aligned}
```

where $\Gamma$ is the [Gamma function][gamma-func], a particularly useful analytic
continuation of factorials to non-integral points.

```math
\begin{aligned}
\Gamma(s) &= \int_0^\infty t^{s-1} e^{-t} \, \dd t
\end{aligned}
```

::alert
---
title: side quest
---
Show that $\displaystyle \sum_{n=1}^\infty \frac{1}{n^s}$ and 
$\displaystyle \frac{1}{\Gamma(s)} \int_0^\infty \frac{x^{s-1}}{e^x - 1} \,\dd x$
are indeed equivalent.

Here's some further context about [gamma extensions][gamma-func]
that might be useful.
::

## The Riemann Hypothesis

The [zeta zeroes][zeta-zeroes] are what make the zeta function particularly interesting.
$\zeta$ has trivial zeros[^1] at $s = -2, -4, -6, \dotsc$.
Besides these, all the other zeroes, so far, have been found to have real part $\frac{1}{2}$.

The [Riemann hypothesis][riemann-hypothesis], which remains unproven,
asserts that indeed **ALL** the non-trivial zeroes have $\Re(s) = \frac{1}{2}$.

::alert
---
type: warning
title: relevance
---
Countless theories in fields as far apart as number theory, quantum mechanics,
and cryptography assume that the Riemann hypothesis is true.
::

## Relevance to Primes

### Globality of Primes

In $1737$, [Leonhard Euler][euler] proved that
$\displaystyle \sum_{n=1}^\infty \frac{1}{n^s}$
is equivalent to
$\displaystyle \prod_{p \text{ prime}} \frac{1}{1 - \frac{1}{p^s}}$,
which directly relates the zeta function to the prime numbers.
For example, this result can be used to construct a
[direct proof][direct-proof] of Euclid's theorem,
which posits that there are infinitely many primes,
by equating the two equations at $s = 1$;
  
```math
\begin{aligned}
\zeta(1) =  \sum_{n=1}^\infty \frac{1}{n} &= \prod_{p \text{ prime}} \frac{1}{1 - \frac{1}{p}},
\end{aligned}
```
where $\displaystyle  \sum_{n=1}^\infty \frac{1}{n}$
is the [harmonic series][harmonic-series] that diverges to infinity.
Thus, the product must also diverge to infinity,
which implies an infinite number of terms terms in the product that are greater than $1$.


::alert
---
title: side quest
---
Can you think of an alternative proof of Euclid's theorem?

### Euclid's Alternate Proof

Suppose there are only finitely many primes.
Let $p$ be the largest prime.
Take $\displaystyle N~=~(2~\times~3~\times~5~\times~\dotsm~\times~p)~+~1$.
Then $N-1$ is divisible by all primes less than $p$, so $N$ _must not_ be divisible
by any of those primes (since it would leave a remainder of $1$).

Therefore, $N$ is either **prime** or **divisible by a prime greater than $p$**,
which contradicts the fact that we picked $p$ to be the largest possible such prime.

::


### Locality of Primes

The above equation gives an estimate of the global distribution of primes
and them being unbounded.
However, a much stronger result which directly relates to the Reimann hypothesis
itself estimates the locality of primes.

Gauss[^gauss] posited the prime-counting function $\pi(x)$ as follows:

```math
\begin{aligned}
\pi(x) &= \sum_{p \in \mathcal{P}_{\leq x}} 1
\end{aligned}
```

where $\mathcal{P}_{\leq x}$ is the set of all prime numbers less than $x$.
This $\pi$ is more commonly referred to as the _prime-counting_ function.
That is, it is a step function over $\RR_{\geq 0}$ that starts at $0$
and increases by $1$ at each prime number.

Riemann developed a _prime-power counting_ function
$\displaystyle \Pi_0(x)~=~\frac{1}{2} \parens{ \sum_{p^n < x} \frac{1}{n} + \sum_{p^n \leq x} \frac{1}{n} }$.
Riemann then showed that the zeta zeroes can be used to very accurately
approximate the locality of primes.
[Here's a nice discussion of the consequences][riemann-consequence].




[gamma-func]:           /math/2023-01-gamma-properties
[abs-convergence]:      https://en.wikipedia.org/wiki/Absolute_convergence
[zeta-zeroes]:          http://www.plouffe.fr/simon/constants/zeta100.html
[riemann-hypothesis]:   https://www.claymath.org/millennium/riemann-hypothesis/
[direct-proof]:         https://www.mathcentre.ac.uk/resources/uploaded/mathcentre-direct.pdf
[euler]:                https://en.wikipedia.org/wiki/Leonhard_Euler
[harmonic-series]:      https://en.wikipedia.org/wiki/Harmonic_series_(mathematics)
[riemann-consequence]:  https://math.stackexchange.com/questions/1079485/importance-of-the-zero-free-region-of-riemann-zeta-function/1081598#1081598

[^1]: A zero of a function $f$ is a value $z$ such that $f(z) = 0$.
  A trivial zero is a zero that is particularly uninteresting.

[^pole]: A pole of a function $f$ is a point in the domain of $f$ where
  the value of $f$ is undefined.

[^gauss]: Riemann was, in fact, Gauss's student.

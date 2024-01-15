---
title: gamma derivation
description: |
  There are few creatures in mathematics as interesting yet, somehow,
  useful as the Gamma function,

  ```math
  \begin{aligned}
    \Gamma \colon \CC &\to \CC \\ \\
    s &\mapsto \int\limits_0^\infty x^{s-1} e^{-x} \, \d x.
  \end{aligned}
  ```

  An interesting result about this function is that
  $\Gamma(n)~=~(n-1)!$ for positive integers $n \in \NN$.
  But why is that so?
  Better yet, why is the gamma function defined so,
  how is it related to factorials,
  and what does its values at non-integers mean?

date: 2024-01-14 23:00:00
---

There are few creatures in mathematics as interesting yet, somehow,
useful as the Gamma function,

```math
\begin{aligned}
  \Gamma \colon \CC &\to \CC \\ \\
  s &\mapsto \int\limits_0^\infty x^{s-1} e^{-x} \, \d x.
\end{aligned}
```

An interesting result about this function is that
$\Gamma(n)~=~(n-1)!$ for positive integers $n \in \NN$.
But why is that so?
Better yet, why is the gamma function defined so,
how is it related to factorials,
and what does its values at non-integers mean?

## An interesting integral

First, consider the integral

```math
\begin{aligned}
  I(x) &= \int \ln x \, \d x.
\end{aligned}
```

It is not a polynomial function, so we cannot use the power rule.
However, if you remember your calculus well, you may recall integration
by parts:

```math
\begin{aligned}
  \int u \, \d v &= uv - \int v \, \d u.
\end{aligned} 
```

Write $u~=~\ln x$ and $\d v~=~\d x$.
Then $\displaystyle \d u~=~\frac{1}{x} \, \d x$ and $v~=~x$.
So

```math
\begin{aligned}
  I(x) &= \int \ln x \, \d x \\
       &= x \ln x - \int x \frac{1}{x} \, \d x \\
       &= x \ln x - x + C.
\end{aligned}
```

## Power TWO

What happens if we have higher powers of $\ln x$?

```math
\begin{aligned}
I_2(x) &= \int \ln^2 x \, \d x
\end{aligned}
```

Substitute $u~=~\ln^2 x$ and $\d v~=~\d x$.
Then $\displaystyle \d u~=~\frac{2 \ln x}{x} \, \d x$ and $v~=~x$.

Using integration by parts;

```math
\begin{aligned}
I_2(x) &= \int \ln^2 x \, \d x \\
       &= x \ln^2 x - \int x \frac{2 \ln x}{x} \, \d x \\
       &= x \ln^2 x - 2 \int \ln x \, \d x
\end{aligned}
```

Interestingly, we get $I(x)$ as part of the integration result of $I_2(x)$.
If we fully integrate the result, we get:
  
```math
\begin{aligned}
I_2(x) &= x \ln^2 x - 2 \int \ln x \, \d x \\
       &= x \ln^2 x - 2 \left( x \ln x - x \right) + C \\
       &= x \ln^2 x - 2 x \ln x + 2 x + C.
\end{aligned}
```

## Power THREE

What happens with the third power?
Take a guess, you're probably right.

```math
\begin{aligned}
I_3(x) &= \int \ln^3 x \, \d x \\
\end{aligned}
```

Take $u~=~\ln^3 x$ and $\d v~=~\d x$.
Then $\displaystyle \d u~=~\frac{3 \ln^2 x}{x} \, \d x$ and $v~=~x$.

```math
\begin{aligned}
I_3(x) &= \int \ln^3 x \, \d x \\
       &= x \ln^3 x - \int x \cdot 3 \ln^2 x \cdot \frac{1}{x} \, \d x \\
       &= x \ln^3 x - 3 \int \ln^2 x \, \d x \\
\end{aligned}
```

Again, we have $I_2(x)$ as part of the integration result of $I_3(x)$.
Evaluating the integral fully gives:

```math
\begin{aligned}
I_3(x) &= x \ln^3 x - 3 \int \ln^2 x \, \d x \\
       &= x \ln^3 x - 3 \left( x \ln^2 x - 2 x \ln x + 2 x \right) + C \\
       &= x \ln^3 x - 3 x \ln^2 x + 6 x \ln x - 6 x + C.
\end{aligned}
```

## A pattern in the chaos?

Indeed, it always occurs that
$\displaystyle I_n(x)~=~x \ln^n x - n I_{n-1}(x)$.
But why is this a useful result?

Take a look at the coefficients of the last term, $x$.

```math
\begin{aligned}
I(x) &= x \ln x - x + C \\
I_2(x) &= x \ln^2 x - 2 x \ln x + 2 x + C \\  
I_3(x) &= x \ln^3 x - 3 x \ln^2 x + 6 x \ln x - 6 x + C \\
I_4(x) &= x \ln^4 x - 4 x \ln^3 x + 12 x \ln^2 x - 24 x \ln x + 24 x + C \\
I_5(x) &= x \ln^5 x - 5 x \ln^4 x + 20 x \ln^3 x - 60 x \ln^2 x + 120 x \ln x - 120 x + C \\
       &\vdots
\end{aligned}
```

Those _are_ factorials, with alternating signs (positive, negative).

## Recovering the factorial

Our goal is two-fold:

- To get rid of the leading terms involving $\ln x$.
- To get rid of the alternation in signs.

### Removing the Leading Terms

The leading terms have one thing in common: they are all a product of $x$ and a power of $\ln x$.
Thus, they all tend to zero at both $x~=~1$ (since $\ln 1~=~0$) and at $x~=~0$.
We need to retain the last term with just $x$, which we can do by evaluating the integral
over the interval $(0, 1)$.

```math
\begin{aligned}
  \brackets{I_n}_0^1~=~\int \limits_0^1 \ln^n x \, \d x &= \brackets{(-1)^n \cdot n! \cdot x}_0^1 &= (-1)^n \cdot n! \\
\end{aligned}
```

### Removing the Sign Alternation

To do this, we need to negate the result for odd $n$.
This is easily achieved by dividing the result by $(-1)^n$,
giving the integral

```math
\begin{aligned}
  n!  &= \frac{1}{(-1)^n} \int\limits_0^1 \ln^n x \, \d x \\
      &= \int\limits_0^1  \frac{\ln^n x}{(-1)^n} \, \d x\\
      &= \int\limits_0^1 \parens{\frac{\ln x}{-1}}^n \, \d x \\
      &= \int\limits_0^1 \parens{-\ln x}^n \, \d x \\
      &= \int\limits_0^1 \ln^n \frac{1}{x} \, \d x.
\end{aligned}
```

## The Gamma Function

But the integral now looks complicated.
Can we simplify it?

Substitute $\displaystyle u~=~\ln \frac{1}{x}$, so that:

```math
\begin{aligned}
  u     &= \ln \frac{1}{x} \\
  -u    &= \ln x \\
  x     &= e^{-u} \\
  \d x  &= -e^{-u} \, \d u
\end{aligned}
```

Note that as $x \rightarrow 0^+$, $\displaystyle \frac{1}{x} \rightarrow \infty^+$,
therefore $u \rightarrow \infty^+$,
and when $x \rightarrow 1$, $\displaystyle \frac{1}{x} \rightarrow 1$, so $u \rightarrow 0$.

Thus;

```math
\begin{aligned}
\int\limits_0^1 \ln^n \frac{1}{x} \, \d x
  &= \int\limits_\infty^0 u^n \cdot (- e^{-u}) \, \d u \\
  &= -\int\limits_\infty^0 u^n \cdot e^{-u} \, \d u \\
  &= \int\limits_0^\infty u^n \cdot e^{-u} \, \d u \\
\end{aligned}
```

This is the exact form of the gamma function, evaluated at $s~=~n + 1$.

::alert
Why is the gamma function shifted by $1$?

The ideas behind the function started being developed
by [Bernoulli][bernoulli] and [Goldbach][goldbach] in the early 1700s,
and [Euler][euler] [defined the eventual function in 1729][euler-gamma-function]
(Euler was Bernoulli's student).

However, the function, in its current form and name,
was defined by [Legendre][legendre] in 1811.
He most likely shifted the function by $1$ to make it easier to work with
by giving it a pole[^pole] at the origin instead of at $s~=~-1$.
::

## The Gamma Extensions

The gamma function has various useful properties.
For example, although it collapses to the factorial function at positive integers,
it is well-defined for all complex numbers except zero and the non-negative integers.
It is sometimes used as an [analytic continuation][analytic-continuation] of the factorial function
to fractional and complex values.
Over non-integers, the logarithmic terms are consequential in the value
giving rise to the [gamma extensions][gamma-extensions].

As an ode to its relevance, $\Gamma$ appears in multiple areas of mathematics,
including:

- Complex analysis (definition of the [Riemann zeta function][riemann-zeta-function]):

```math
\begin{aligned}
  \zeta(s) &= \sum\limits_{n=1}^\infty \frac{1}{n^s} \\
           &= \frac{1}{\Gamma(s)} \int\limits_0^\infty \frac{x^{s-1}}{e^x - 1} \, \d x.
\end{aligned}
```

- Probability theory (definition of the [beta distribution][beta-distribution]):

```math
\begin{aligned}
  \beta(a, b) &= \int\limits_0^1 x^{a-1} (1-x)^{b-1} \, \d x \\
              &= \frac{\Gamma(a) \Gamma(b)}{\Gamma(a+b)}.
\end{aligned}
```

- Number theory (the functional equation of the [Riemann zeta function][riemann-zeta-function]):

```math
\begin{aligned}
  \pi^{-s/2} \Gamma\parens{\frac{s}{2}} \zeta(s) &= \pi^{-(1-s)/2} \Gamma\parens{\frac{1-s}{2}} \zeta(1-s).
\end{aligned}
```

- And many more, left as an [exercise to the reader][exercise-to-reader].

[euler-gamma-function]: https://web.archive.org/web/20160303173538/http://home.sandiego.edu/%7Elangton/eg.pdf
[bernoulli]: https://en.wikipedia.org/wiki/Johann_Bernoulli
[goldbach]: https://en.wikipedia.org/wiki/Christian_Goldbach
[euler]: https://en.wikipedia.org/wiki/Leonhard_Euler
[legendre]: https://en.wikipedia.org/wiki/Adrien-Marie_Legendre
[beta-distribution]: https://en.wikipedia.org/wiki/Beta_distribution
[exercise-to-reader]: /math/2024-03-exercise-for-the-reader
[gamma-extensions]: /math/2023-01-gamma-properties
[riemann-zeta-function]: /math/2023-02-riemann-zeta-properties
[analytic-continuation]: https://en.wikipedia.org/wiki/Analytic_continuation

[^pole]: A pole of a function $f$ is a point in the domain of $f$ where
  the value of $f$ is undefined.

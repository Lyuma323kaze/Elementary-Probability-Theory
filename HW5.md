---
title: HW5
author: Zhen Wu
---

## Prob. 1

To determine the cumulative distribution function (CDF) of Jane’s waiting time, denoted as $W$, we must account for the two mutually exclusive scenarios she encounters upon entering the bank.

Let $N$ be the number of customers ahead of Jane, where $N \in \{0, 1\}$.

According to the problem, Jane is equally likely to find zero or one customer, implying:

$$
P(N=0) = 0.5, \quad P(N=1) = 0.5
$$

If Jane finds no customers ($N=0$), her waiting time is $W = 0$.

If Jane finds one customer ($N=1$), her waiting time $W$ is equal to the remaining service time of that customer, which follows an exponential distribution with parameter $\lambda$.

We denote this service time as $S \sim \text{Exp}(\lambda)$, with a CDF given by $P(S \le w) = 1 - e^{-\lambda w}$ for $w \ge 0$.

By applying the Law of Total Probability, we can express the CDF of the waiting time, $F_W(w) = P(W \le w)$, as the weighted sum of the conditional probabilities:

$$
P(W \le w) = P(W \le w \mid N=0)P(N=0) + P(W \le w \mid N=1)P(N=1)
$$

For any $w < 0$, the waiting time cannot be negative, so the probability is zero:

$$
F_W(w) = 0, \quad w < 0
$$

For $w \ge 0$, we evaluate the conditional components.

In the first case, if $N=0$, the waiting time is definitely less than or equal to $w$ because $0 \le w$.

In the second case, if $N=1$, the probability is defined by the exponential distribution:

$$
P(W \le w) = (1) \cdot (0.5) + (1 - e^{-\lambda w}) \cdot (0.5)
$$

Expanding and simplifying this expression yields the final form of the CDF:

$$
F_W(w) = 0.5 + 0.5 - 0.5 e^{-\lambda w} = 1 - 0.5 e^{-\lambda w}
$$

Therefore, the complete CDF of Jane's waiting time is defined piecewise as follows:

$$
F_W(w) = \begin{cases} 0, & w < 0 \\ 1 - \frac{1}{2}e^{-\lambda w}, & w \ge 0 \end{cases}
$$

Note that there is a discrete "jump" or atom at $w=0$ of size $0.5$, representing the $50\%$ chance that Jane has no wait at all.

For $w > 0$, the function behaves like a scaled exponential distribution.

## Prob. 2

To determine the cumulative distribution function (CDF) of the score $S$, we first define the distribution of the distance $X$.

Since the dart is equally likely to hit any point in the circular target of radius $r$, the probability that the dart lands within a distance $x$ from the center is proportional to the area of the circle with radius $x$.

For $0 \le x \le r$, the CDF of $X$ is given by:

$$
F_X(x) = \mathbb{P}(X \le x) = \frac{\pi x^2}{\pi r^2} = \frac{x^2}{r^2}
$$

The score $S$ is defined as a transformation of the random variable $X$:

$$
S = \begin{cases} 1/X & \text{if } X \le t \\ 0 & \text{if } X > t \end{cases}
$$

We assume that $t \le r$.

The range of $S$ consists of the single value $\{0\}$ and the interval $[1/t, \infty)$.

To find the CDF $F_S(s) = \mathbb{P}(S \le s)$, we consider different ranges for $s$.

For $s < 0$, it is impossible for the score to be negative, thus:

$$
F_S(s) = 0, \quad s < 0
$$

For $0 \le s < 1/t$, the only way for $S$ to be less than or equal to $s$ is if $S = 0$.

This occurs when the dart hits outside the inner circle:

$$
F_S(s) = \mathbb{P}(S = 0) = \mathbb{P}(X > t) = 1 - F_X(t) = 1 - \frac{t^2}{r^2}
$$

For $s \ge 1/t$, the event $S \le s$ includes both the case where $S=0$ and the case where $1/t \le S \le s$.

Using the definition of $S$, the latter case is equivalent to $1/s \le X \le t$:

$$
F_S(s) = \mathbb{P}(X > t) + \mathbb{P}(1/s \le X \le t) = \left( 1 - \frac{t^2}{r^2} \right) + \left( \frac{t^2}{r^2} - \frac{(1/s)^2}{r^2} \right)
$$

Simplifying the expression, we obtain:

$$
F_S(s) = 1 - \frac{1}{r^2 s^2}, \quad s \ge 1/t
$$

Summarizing the results, the CDF of $S$ is:

$$
F_S(s) = \begin{cases} 0 & s < 0 \\ 1 - \frac{t^2}{r^2} & 0 \le s < 1/t \\ 1 - \frac{1}{r^2 s^2} & s \ge 1/t \end{cases}
$$

To determine if $S$ is a continuous random variable, we examine the continuity of its CDF at $s = 0$.

The limit from the left is:

$$
\lim_{s \to 0^-} F_S(s) = 0
$$

The value at $s=0$ (and the limit from the right) is:

$$
F_S(0) = 1 - \frac{t^2}{r^2}
$$

If $t < r$, there is a jump discontinuity at $s=0$ with magnitude $1 - t^2/r^2$.

Because a continuous random variable must have a CDF that is continuous at every point, $S$ is not a continuous random variable (unless $t=r$, in which case the jump at 0 vanishes, but there may still be a discontinuity at $1/r$).

## Prob. 3

### (a)

The random variable $X$ is a mixture of $Y$ and $Z$.

Let $A$ be the event that $X$ takes the value of $Y$, with $P(A) = p$, and let $A^c$ be the event that $X$ takes the value of $Z$, with $P(A^c) = 1 - p$.

We define the CDF of $X$ as:

$$
F_X(x) = P(X \le x)
$$

Using the Law of Total Probability, we can partition this probability based on the events $A$ and $A^c$:

$$
F_X(x) = P(X \le x \mid A)P(A) + P(X \le x \mid A^c)P(A^c)
$$

Substituting the given probabilities and the definitions of the conditional variables, we obtain:

$$
F_X(x) = p P(Y \le x) + (1-p) P(Z \le x)
$$

$$
F_X(x) = p F_Y(x) + (1-p) F_Z(x)
$$

To find the PDF, we differentiate the CDF with respect to $x$:

$$
f_X(x) = \frac{d}{dx} F_X(x) = \frac{d}{dx} [p F_Y(x) + (1-p) F_Z(x)]
$$

Since differentiation is a linear operator, we apply it to each term individually:

$$
f_X(x) = p \frac{d}{dx} F_Y(x) + (1-p) \frac{d}{dx} F_Z(x)
$$

$$
f_X(x) = p f_Y(x) + (1-p) f_Z(x)
$$

### (b)

We define the CDF $F_X(x)$ as the integral of the PDF from negative infinity to $x$:

$$
F_X(x) = \int_{-\infty}^x f_X(t) dt
$$

We evaluate this integral by considering two distinct cases for the value of $x$.

Case 1: $x < 0$.

In this region, the PDF is defined as $f_X(t) = p\lambda e^{\lambda t}$.

The integral is:

$$
F_X(x) = \int_{-\infty}^x p\lambda e^{\lambda t} dt
$$

$$
F_X(x) = p [e^{\lambda t}]_{-\infty}^x = p(e^{\lambda x} - 0) = p e^{\lambda x}
$$

Case 2: $x \ge 0$.

In this region, the integral must be split at the boundary $t=0$:

$$
F_X(x) = \int_{-\infty}^0 p\lambda e^{\lambda t} dt + \int_0^x (1-p)\lambda e^{-\lambda t} dt
$$

The first term is the total probability accumulated in the negative region, which we found to be $F_X(0) = p$.

We then evaluate the second integral:

$$
F_X(x) = p + (1-p) [-e^{-\lambda t}]_0^x
$$

$$
F_X(x) = p + (1-p) (1 - e^{-\lambda x})
$$

Expanding and simplifying the terms:

$$
F_X(x) = p + 1 - p - (1-p)e^{-\lambda x}
$$

$$
F_X(x) = 1 - (1-p)e^{-\lambda x}
$$

Combining both cases, the final CDF of the two-sided exponential distribution is:

$$
F_X(x) = \begin{cases} p e^{\lambda x}, & x < 0 \\ 1 - (1-p) e^{-\lambda x}, & x \,\ge 0 \end{cases}
$$

## Prob. 4

### (a)

Since $X$ is already a standard normal random variable, we can directly use the standard normal cumulative distribution function, $\Phi(z)$.

For the first probability:

$$
\mathbf{P}(X \le 1.5) = \Phi(1.5)
$$

Using a standard normal table, we find:

$$
\mathbf{P}(X \le 1.5) \approx 0.9332
$$

For the second probability, we utilize the symmetry property of the normal distribution, $\Phi(-z) = 1 - \Phi(z)$:

$$
\mathbf{P}(X \le -1) = \Phi(-1) = 1 - \Phi(1)
$$

Consulting the table for $\Phi(1) \approx 0.8413$:

$$
\mathbf{P}(X \le -1) \approx 1 - 0.8413 = 0.1587
$$

### (b)

Let $Z = \frac{Y - 1}{2}$.

We determine the distribution of $Z$ by calculating its mean and variance through the linearity properties of expectation and variance.

The expected value of $Z$ is:

$$
E[Z] = E\left[ \frac{Y - 1}{2} \right] = \frac{1}{2}(E[Y] - 1) = \frac{1}{2}(1 - 1) = 0
$$

The variance of $Z$ is:

$$
Var(Z) = Var\left( \frac{Y - 1}{2} \right) = \frac{1}{2^2} Var(Y - 1) = \frac{1}{4} Var(Y) = \frac{1}{4} \cdot 4 = 1
$$

Since $Y$ is normally distributed, any linear transformation of $Y$ is also normally distributed.

Thus, $Z \sim N(0, 1)$, meaning $(Y - 1)/2$ is a standard normal random variable.

The probability density function (PDF) of a standard normal variable is given by:

$$
f_Z(z) = \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}}
$$

### (c)

To calculate this probability, we standardize the variable $Y$ using the transformation from part (b), $Z = (Y - 1)/2$.

We transform the boundaries of the interval as follows:

$$
-1 \le Y \le 1 \implies \frac{-1 - 1}{2} \le \frac{Y - 1}{2} \le \frac{1 - 1}{2}
$$

$$
-1 \le Z \le 0
$$

The probability is then:

$$
\mathbf{P}(-1 \le Y \le 1) = \mathbf{P}(-1 \le Z \le 0) = \Phi(0) - \Phi(-1)
$$

We know that $\Phi(0) = 0.5$ and we previously calculated $\Phi(-1) \approx 0.1587$:

$$
\mathbf{P}(-1 \le Y \le 1) = 0.5 - 0.1587 = 0.3413
$$

## Prob. 5

To find the probability distribution of $Y = X^2$, we begin by identifying the characteristics of the initial random variable $X$, which is uniformly distributed over the interval $(-1, 2)$.

The probability density function (PDF) of $X$ is defined as follows:

$$
f_X(x) = \begin{cases} \frac{1}{3}, & -1 < x < 2 \\ 0, & \text{otherwise} \end{cases}
$$

The cumulative distribution function (CDF) of $X$ is given by:

$$
F_X(x) = \frac{x - (-1)}{2 - (-1)} = \frac{x+1}{3}, \quad x \in (-1, 2)
$$

We first determine the range of values for $Y$.

Since $x$ ranges from $-1$ to $2$, $x^2$ ranges from $0$ (at $x=0$) to $4$ (at $x=2$).

Therefore, the support of $Y$ is the interval $[0, 4]$.

To find the distribution of $Y$, we calculate its CDF, $F_Y(y) = \mathbb{P}(Y \le y)$.

For $y \in [0, 4]$, we have:

$$
F_Y(y) = \mathbb{P}(X^2 \le y) = \mathbb{P}(-\sqrt{y} \le X \le \sqrt{y})
$$

Because the support of $X$ is $(-1, 2)$, the bounds of the interval $[-\sqrt{y}, \sqrt{y}]$ relative to the support of $X$ depend on the value of $y$.

Specifically, we must distinguish between the cases where $-\sqrt{y}$ is inside or outside the interval $(-1, 2)$.

### Case 1: $0 \le y \le 1$

In this interval, $\sqrt{y} \le 1$, which implies that the entire interval $[-\sqrt{y}, \sqrt{y}]$ is contained within the support $(-1, 2)$.

The CDF is calculated as:

$$
F_Y(y) = F_X(\sqrt{y}) - F_X(-\sqrt{y}) = \frac{\sqrt{y} + 1}{3} - \frac{-\sqrt{y} + 1}{3} = \frac{2\sqrt{y}}{3}
$$

Differentiating with respect to $y$ gives the PDF in this region:

$$
f_Y(y) = \frac{d}{dy} \left( \frac{2\sqrt{y}}{3} \right) = \frac{1}{3\sqrt{y}}
$$

### Case 2: $1 < y \le 4$

In this interval, $\sqrt{y} > 1$, which means that $-\sqrt{y} < -1$.

The lower boundary of the event $\{-\sqrt{y} \le X \le \sqrt{y}\}$ is truncated by the lower limit of $X$'s support.

The probability becomes:

$$
F_Y(y) = \mathbb{P}(-1 < X \le \sqrt{y}) = F_X(\sqrt{y}) - F_X(-1) = \frac{\sqrt{y} + 1}{3} - 0 = \frac{\sqrt{y} + 1}{3}
$$

Differentiating with respect to $y$ gives the PDF in this region:

$$
f_Y(y) = \frac{d}{dy} \left( \frac{\sqrt{y} + 1}{3} \right) = \frac{1}{6\sqrt{y}}
$$

Combining these results, the final PDF of $Y$ is:

$$
f_Y(y) = \begin{cases} \frac{1}{3\sqrt{y}}, & 0 < y \le 1 \\ \frac{1}{6\sqrt{y}}, & 1 < y < 4 \\ 0, & \text{otherwise} \end{cases}
$$

This distribution illustrates how a linear uniform distribution is stretched and weighted toward lower values through the non-linear squaring process.

## Prob. 6

### (1)

The definition of the CDF for a continuous random variable is:

$$
F_X(x) = \int_{-\infty}^x f(t) dt
$$

Substituting the provided Cauchy PDF:

$$
F_X(x) = \int_{-\infty}^x \frac{1}{\pi(1+t^2)} dt = \frac{1}{\pi} \int_{-\infty}^x \frac{1}{1+t^2} dt
$$

Using the fundamental theorem of calculus and the standard integral for the inverse tangent function:

$$
F_X(x) = \frac{1}{\pi} \left[ \arctan(t) \right]_{-\infty}^x = \frac{1}{\pi} \left( \arctan(x) - \lim_{t \to -\infty} \arctan(t) \right)
$$

Since the limit of $\arctan(t)$ as $t$ approaches negative infinity is $-\pi/2$, the expression becomes:

$$
F_X(x) = \frac{1}{\pi} \left( \arctan(x) - \left( -\frac{\pi}{2} \right) \right) = \frac{\arctan(x)}{\pi} + \frac{1}{2}
$$

Thus, the CDF of $X$ is $F_X(x) = \frac{1}{\pi} \arctan(x) + \frac{1}{2}$ for all $x \in \mathbb{R}$.

### (2)

To find the distribution of $Y = \arctan(X)$, we first note the range of the transformation.

Since $X$ can take any real value in $(-\infty, \infty)$, the range of $Y = \arctan(X)$ is the open interval $(-\pi/2, \pi/2)$.

We determine the CDF of $Y$ by expressing the event $Y \le y$ in terms of $X$:

$$
F_Y(y) = P(Y \le y) = P(\arctan(X) \le y)
$$

Because the arctangent function is strictly increasing, the inequality is preserved when we apply the tangent function to both sides:

$$
F_Y(y) = P(X \le \tan(y)) = F_X(\tan(y))
$$

Substituting the expression for $F_X$ derived in the first part:

$$
F_Y(y) = \frac{\arctan(\tan(y))}{\pi} + \frac{1}{2}
$$

For $y$ in the interval $(-\pi/2, \pi/2)$, the identity $\arctan(\tan(y)) = y$ holds.

Therefore:

$$
F_Y(y) = \frac{y}{\pi} + \frac{1}{2}, \quad -\frac{\pi}{2} < y < \frac{\pi}{2}
$$

To obtain the PDF of $Y$, we differentiate the CDF with respect to $y$:

$$
f_Y(y) = \frac{d}{dy} F_Y(y) = \frac{d}{dy} \left( \frac{y}{\pi} + \frac{1}{2} \right) = \frac{1}{\pi}
$$

The resulting PDF is constant over its support:

$$
f_Y(y) = \begin{cases} \frac{1}{\pi}, & -\frac{\pi}{2} < y < \frac{\pi}{2} \\ 0, & \text{otherwise} \end{cases}
$$

i.e $Y \sim U(-\pi/2, \pi/2)$.

## Prob. 7

The CDF of $X$ is:

$$
F_X(x) = \Phi\left(\frac{x}{\sigma}\right)
$$

We begin by finding the CDF of $Y$, denoted as $F_Y(y) = \mathbb{P}(Y \le y)$.

Since the square root of a maximum with zero is non-negative, the range of $Y$ is $[0, \infty)$.

Thus, for any $y < 0$, the probability is zero:

$$
F_Y(y) = 0, \quad y < 0
$$

For $y \ge 0$, the event $Y \le y$ is equivalent to $\sqrt{\max(X, 0)} \le y$.

Squaring both sides of the inequality within the probability (which is valid since both sides are non-negative) yields:

$$
F_Y(y) = \mathbb{P}(\max(X, 0) \le y^2)
$$

This event $\max(X, 0) \le y^2$ is satisfied if and only if $X \le y^2$.

This is because if $X \le 0$, then $\max(X, 0) = 0$, and $0 \le y^2$ is always true for $y \ge 0$.

If $X > 0$, then $\max(X, 0) = X$, and we require $X \le y^2$.

Therefore, for $y \ge 0$:

$$
F_Y(y) = \mathbb{P}(X \le y^2) = \Phi\left(\frac{y^2}{\sigma}\right)
$$

This distribution is a mixed random variable because it contains both a discrete and a continuous component.

The discrete component is an "atom" at $y=0$, representing the probability that $X$ was non-positive:

$$
\mathbb{P}(Y = 0) = F_Y(0) = \Phi(0) = \frac{1}{2}
$$

For $y > 0$, the distribution is continuous.

We find the probability density function (PDF) $f_Y(y)$ by differentiating the CDF:

$$
f_Y(y) = \frac{d}{dy} \Phi\left(\frac{y^2}{\sigma}\right) = \phi\left(\frac{y^2}{\sigma}\right) \cdot \frac{d}{dy}\left(\frac{y^2}{\sigma}\right)
$$

Substituting the standard normal density $\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2/2}$:

$$
f_Y(y) = \frac{1}{\sqrt{2\pi}} \exp\left( -\frac{(y^2/\sigma)^2}{2} \right) \cdot \frac{2y}{\sigma}
$$

Simplifying the expression, we obtain the density for the continuous part:

$$
f_Y(y) = \frac{2y}{\sqrt{2\pi}\sigma} \exp\left( -\frac{y^4}{2\sigma^2} \right), \quad y > 0
$$

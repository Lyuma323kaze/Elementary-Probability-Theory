---
title: HW7
author: Zhen Wu
---

## Prob. 1

To determine the distribution of the sum $Z = X + Y$, where $X \sim \mathcal{P}(3)$ and $Y \sim \mathcal{P}(6)$ are independent Poisson random variables, we employ the convolution formula for discrete random variables.

The probability mass function (PMF) of $Z$ is given by:

$$
P(Z = k) = \sum_{i=0}^k P(X = i) P(Y = k - i)
$$

Substituting the PMFs of $X$ and $Y$:

$$
P(Z = k) = \sum_{i=0}^k \left( \frac{e^{-3} 3^i}{i!} \right) \left( \frac{e^{-6} 6^{k-i}}{(k-i)!} \right)
$$

Factoring out the constant terms and rearranging the expression inside the summation:

$$
P(Z = k) = e^{-9} \sum_{i=0}^k \frac{3^i 6^{k-i}}{i! (k-i)!} = \frac{e^{-9}}{k!} \sum_{i=0}^k \frac{k!}{i! (k-i)!} 3^i 6^{k-i}
$$

Recognizing the term within the summation as the binomial expansion of $(3 + 6)^k$:

$$
P(Z = k) = \frac{e^{-9}}{k!} \sum_{i=0}^k \binom{k}{i} 3^i 6^{k-i} = \frac{e^{-9} 9^k}{k!}
$$

The resulting PMF corresponds to a Poisson distribution with parameter $\lambda = 9$.

Therefore, $Z \sim \mathcal{P}(9)$.

## Prob. 2

We are given independent random variables $X \sim \Gamma(\alpha, \lambda)$ and $Y \sim \Gamma(\beta, \lambda)$. Their joint probability density function (PDF) is the product of their individual densities:

$$
f_{X,Y}(x, y) = \frac{\lambda^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\lambda x} \cdot \frac{\lambda^\beta}{\Gamma(\beta)} y^{\beta-1} e^{-\lambda y} = \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha)\Gamma(\beta)} x^{\alpha-1} y^{\beta-1} e^{-\lambda(x+y)}
$$

To find the distribution of $Z = X + Y$, we introduce an auxiliary variable $U = \frac{X}{X+Y}$. The inverse transformations are $X = ZU$ and $Y = Z(1-U)$. The Jacobian of this transformation is:

$$
J = \begin{vmatrix} \frac{\partial x}{\partial z} & \frac{\partial x}{\partial u} \\ \frac{\partial y}{\partial z} & \frac{\partial y}{\partial u} \end{vmatrix} = \begin{vmatrix} u & z \\ 1-u & -z \end{vmatrix} = -uz - z(1-u) = -z
$$

The joint PDF of $Z$ and $U$ is:

$$
f_{Z,U}(z, u) = f_{X,Y}(zu, z(1-u)) \cdot |J| = \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha)\Gamma(\beta)} (zu)^{\alpha-1} (z(1-u))^{\beta-1} e^{-\lambda z} \cdot z
$$

$$
f_{Z,U}(z, u) = \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha)\Gamma(\beta)} z^{\alpha+\beta-1} e^{-\lambda z} \cdot u^{\alpha-1} (1-u)^{\beta-1}
$$

To find the marginal PDF of $Z$, we integrate over $u \in (0, 1)$:

$$
f_Z(z) = \frac{\lambda^{\alpha+\beta} z^{\alpha+\beta-1} e^{-\lambda z}}{\Gamma(\alpha)\Gamma(\beta)} \int_0^1 u^{\alpha-1} (1-u)^{\beta-1} du
$$

The integral is the Beta function $B(\alpha, \beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$. Substituting this yields:

$$
f_Z(z) = \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha+\beta)} z^{\alpha+\beta-1} e^{-\lambda z}
$$

This is the PDF of a Gamma distribution with parameters $(\alpha+\beta, \lambda)$.

Thus, $Z \sim \Gamma(\alpha+\beta, \lambda)$.

## Prob. 3

Let $X$ and $Y$ be independent exponential random variables with parameters $\lambda$ and $\mu$, respectively. We define $Z = \min\{X, Y\}$.

To find the distribution of $Z$, we consider its survival function:

$$
P(Z > z) = P(\min\{X, Y\} > z)
$$

The minimum of two values is greater than $z$ if and only if both values are greater than $z$:

$$
P(Z > z) = P(X > z, Y > z)
$$

Due to independence, we can multiply the individual survival probabilities:

$$
P(Z > z) = P(X > z) P(Y > z) = e^{-\lambda z} e^{-\mu z} = e^{-(\lambda + \mu)z}
$$

The cumulative distribution function (CDF) is therefore:

$$
F_Z(z) = 1 - P(Z > z) = 1 - e^{-(\lambda + \mu)z}, \quad z \ge 0
$$

Differentiating the CDF with respect to $z$ gives the PDF:

$$
f_Z(z) = (\lambda + \mu) e^{-(\lambda + \mu)z}
$$

This is the PDF of an exponential distribution with parameter $\lambda + \mu$.

Therefore, $Z \sim \text{Exp}(\lambda + \mu)$.

## Prob. 4

Given $X \sim \text{Exp}(1)$ and $Y \sim N(0, 1)$ are independent, we seek the PDF of $Z = \sqrt{2X} |Y|$.

Let $W = |Y|$. The PDF of $W$ is $f_W(w) = \frac{2}{\sqrt{2\pi}} e^{-w^2/2}$ for $w > 0$. We compute the CDF of $Z$:

$$
P(Z \le z) = \int_0^\infty f_W(w) P(\sqrt{2X}w \le z) dw = \int_0^\infty \frac{2}{\sqrt{2\pi}} e^{-w^2/2} (1 - e^{-z^2/(2w^2)}) dw
$$

The PDF $f_Z(z)$ is the derivative of the CDF:

$$
f_Z(z) = \int_0^\infty \frac{2}{\sqrt{2\pi}} e^{-w^2/2} \frac{d}{dz} (1 - e^{-z^2/(2w^2)}) dw = \int_0^\infty \frac{2z}{\sqrt{2\pi} w^2} e^{-(w^2 + z^2/w^2)/2} dw
$$

Applying the substitution $u = z/w$, we have $dw = -z/u^2 du$:

$$
f_Z(z) = \frac{2z}{\sqrt{2\pi}} \int_\infty^0 \frac{u^2}{z^2} e^{-(z^2/u^2 + u^2)/2} \left(-\frac{z}{u^2}\right) du = \frac{2}{\sqrt{2\pi}} \int_0^\infty e^{-(u^2 + z^2/u^2)/2} du
$$

Using the integral identity $\int_0^\infty e^{-(ax^2 + b/x^2)} dx = \frac{1}{2}\sqrt{\frac{\pi}{a}} e^{-2\sqrt{ab}}$ with $a=1/2$ and $b=z^2/2$:

$$
f_Z(z) = \frac{2}{\sqrt{2\pi}} \cdot \frac{1}{2} \sqrt{2\pi} e^{-2\sqrt{z^2/4}} = e^{-z}, \quad z > 0
$$

Thus, $Z$ follows an exponential distribution with parameter 1.

## Prob. 5

Given $X_1 \sim \mathcal{U}(1, 2)$ and $f_{X_2}(x_2) = \frac{3}{8}x_2^2$ for $x_2 \in [0, 2]$. Let $Y_1 = X_1^2$ and $Y_2 = X_1 + X_2$.

The inverse transformations are $X_1 = \sqrt{Y_1}$ and $X_2 = Y_2 - \sqrt{Y_1}$. The Jacobian is:

$$
J = \begin{vmatrix} \frac{1}{2\sqrt{y_1}} & 0 \\ -\frac{1}{2\sqrt{y_1}} & 1 \end{vmatrix} = \frac{1}{2\sqrt{y_1}}
$$

The joint PDF of $Y_1$ and $Y_2$ is:

$$
f_{Y_1, Y_2}(y_1, y_2) = f_{X_1}(\sqrt{y_1}) f_{X_2}(y_2 - \sqrt{y_1}) \cdot |J|
$$

Substituting the densities:

$$
f_{Y_1, Y_2}(y_1, y_2) = 1 \cdot \frac{3}{8}(y_2 - \sqrt{y_1})^2 \cdot \frac{1}{2\sqrt{y_1}} = \frac{3(y_2 - \sqrt{y_1})^2}{16\sqrt{y_1}}
$$

The support is defined by $1 < \sqrt{y_1} < 2$ and $0 < y_2 - \sqrt{y_1} < 2$:

$$
1 < y_1 < 4, \quad \sqrt{y_1} < y_2 < \sqrt{y_1} + 2
$$

## Prob. 6

### (a)

Let $X_1 \sim \chi^2_{r_1}$ and $X_2 \sim \chi^2_{r_2}$ be independent. Their joint PDF is:

$$
f(x_1, x_2) = C x_1^{r_1/2-1} x_2^{r_2/2-1} e^{-(x_1+x_2)/2}
$$

Let $Y_1 = X_1/X_2$ and $Y_2 = X_1 + X_2$. Then $X_1 = \frac{Y_1 Y_2}{1+Y_1}$ and $X_2 = \frac{Y_2}{1+Y_1}$. The Jacobian is $|J| = \frac{Y_2}{(1+Y_1)^2}$.

$$
f(y_1, y_2) = C \left( \frac{y_1 y_2}{1+y_1} \right)^{r_1/2-1} \left( \frac{y_2}{1+y_1} \right)^{r_2/2-1} e^{-y_2/2} \frac{y_2}{(1+y_1)^2}
$$

$$
f(y_1, y_2) = \left[ C_1 \frac{y_1^{r_1/2-1}}{(1+y_1)^{(r_1+r_2)/2}} \right] \cdot \left[ C_2 y_2^{(r_1+r_2)/2-1} e^{-y_2/2} \right]
$$

The factorization shows $Y_1$ and $Y_2$ are independent. The density of $Y_2$ corresponds to $\chi^2_{r_1+r_2}$.

### (b)

$F_1 = \frac{X_1/r_1}{X_2/r_2} = \frac{r_2}{r_1} Y_1$ follows an F-distribution $F(r_1, r_2)$ by definition.

$F_2 = \frac{X_3/r_3}{(X_1+X_2)/(r_1+r_2)}$ follows $F(r_3, r_1+r_2)$ because $X_3 \sim \chi^2_{r_3}$ and $X_1+X_2 \sim \chi^2_{r_1+r_2}$ are independent.

Since $Y_1$ is independent of $Y_2$, $F_1$ (a function of $Y_1$) is independent of $F_2$ (a function of $Y_2$ and $X_3$).

## Prob. 7

Let $X_1, \dots, X_n$ be i.i.d. with PDF $f(x)$ and CDF $F(x)$. The joint PDF of the first $r$ order statistics $X_{(1)}, \dots, X_{(r)}$ for $x_1 < x_2 < \dots < x_r$ is given by:

$$
f_{(1), \dots, (r)}(x_1, \dots, x_r) = \frac{n!}{(n-r)!} \left[ \prod_{i=1}^r f(x_i) \right] [1 - F(x_r)]^{n-r}
$$

This formula accounts for the $r!$ permutations of the first $r$ selected items, the choice of these $r$ items from $n$ ($\binom{n}{r}$), and the probability that the remaining $n-r$ items are all greater than $x_r$.

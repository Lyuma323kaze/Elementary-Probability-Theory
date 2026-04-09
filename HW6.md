---
title: HW6
author: Zhen Wu
---

## Prob. 1

### (1)

To determine the joint probability mass function (PMF) of $X$ and $Y$, we characterize the process as a multinomial experiment with $n=4$ independent trials.

In each trial, there are three mutually exclusive categories of outcomes: rolling a 1 (with probability $p_1 = 1/6$), rolling a 2 (with probability $p_2 = 1/6$), and rolling any other number from $\{3, 4, 5, 6\}$ (with probability $p_3 = 4/6$).

The joint PMF of $X$ and $Y$, denoted as $P_{X, Y}(x, y)$, represents the probability of obtaining exactly $x$ ones and $y$ twos in 4 rolls.

According to the multinomial distribution formula, the joint PMF is defined as:

$$
P_{X, Y}(x, y) = \frac{4!}{x! y! (4 - x - y)!} \left( \frac{1}{6} \right)^x \left( \frac{1}{6} \right)^y \left( \frac{4}{6} \right)^{4 - x - y}
$$

The support of this joint PMF consists of all pairs of non-negative integers $(x, y)$ that satisfy the constraint of the total number of rolls:

$$
\{(x, y) \in \mathbb{Z}^2 \mid x \ge 0, y \ge 0, x + y \le 4\}
$$

For any values of $x$ and $y$ outside of this set, the joint PMF is equal to zero.

### (2)

To find the conditional PMF of $X$ given $Y=2$, we consider the scenario where it is already known that exactly two of the four rolls resulted in a 2.

Because the rolls are independent, the condition $Y=2$ implies that the remaining $4 - 2 = 2$ rolls must have resulted in outcomes other than a 2, specifically from the set $\{1, 3, 4, 5, 6\}$.

The conditional distribution of $X$ given $Y=2$ is therefore a binomial distribution, where the number of trials is $n' = 2$.

The success probability $p'$ for this binomial distribution is the conditional probability of rolling a 1 given that the result was not a 2:

$$
p' = P(\text{roll is 1} \mid \text{roll is not 2}) = \frac{P(\text{roll is 1})}{P(\text{roll is not 2})} = \frac{1/6}{5/6} = \frac{1}{5}
$$

The conditional PMF $P_{X|Y}(x \mid 2)$ is thus given by the binomial PMF formula with $n'=2$ and $p'=1/5$:

$$
P_{X|Y}(x \mid 2) = \binom{2}{x} \left( \frac{1}{5} \right)^x \left( \frac{4}{5} \right)^{2-x}
$$

The support for this conditional PMF is $x \in \{0, 1, 2\}$.

We can evaluate the specific probabilities for each possible value of $X$ as follows:

$$
P_{X|Y}(0 \mid 2) = \binom{2}{0} \left( \frac{1}{5} \right)^0 \left( \frac{4}{5} \right)^2 = \frac{16}{25}
$$

$$
P_{X|Y}(1 \mid 2) = \binom{2}{1} \left( \frac{1}{5} \right)^1 \left( \frac{4}{5} \right)^1 = \frac{8}{25}
$$

$$
P_{X|Y}(2 \mid 2) = \binom{2}{2} \left( \frac{1}{5} \right)^2 \left( \frac{4}{5} \right)^0 = \frac{1}{25}
$$

## Prob. 2

To solve this problem, we must define the random variables representing the cutting process and then determine the joint probability density function (PDF) based on the specified conditions.

Let the total length of the stick be $L = 1$, represented by the interval $[0, 1]$.

Let $X$ denote the position of the first cut, which is distributed uniformly across the stick's length.

The PDF of $X$ is given by:

$$
f_X(x) = 1, \quad x \in (0, 1)
$$

This first cut divides the stick into two segments: the "first" segment $[0, X]$ and the second segment $[X, 1]$.

According to the problem, we then cut the first segment at a position $Y$.

Since this cut is "randomly" placed within the first segment, $Y$ follows a uniform distribution over the interval $(0, X)$.

The conditional PDF of $Y$ given $X = x$ is:

$$
f_{Y|X}(y|x) = \frac{1}{x}, \quad 0 < y < x
$$

The joint PDF of $X$ and $Y$ is the product of the marginal and conditional densities:

$$
f_{X, Y}(x, y) = f_X(x) f_{Y|X}(y|x) = 1 \cdot \frac{1}{x} = \frac{1}{x}
$$

The domain of this joint PDF is the triangular region $D = \{(x, y) \in \mathbb{R}^2 \mid 0 < y < x < 1\}$.

The lengths of the resulting three pieces are $L_1 = Y$, $L_2 = X - Y$, and $L_3 = 1 - X$.

For these segments to form a triangle, they must satisfy the triangle inequality, which states that the sum of any two sides must be strictly greater than the third side:

$$
L_1 + L_2 > L_3 \implies Y + (X - Y) > 1 - X \implies X > 1/2
$$

$$
L_1 + L_3 > L_2 \implies Y + (1 - X) > X - Y \implies 2Y > 2X - 1 \implies Y > X - 1/2
$$

$$
L_2 + L_3 > L_1 \implies (X - Y) + (1 - X) > Y \implies 1 - Y > Y \implies Y < 1/2
$$

These inequalities define the successful region $S \subset D$.

Combining the constraints, we find that for a given $x \in (1/2, 1)$, the variable $y$ must fall within the interval $(x - 1/2, 1/2)$.

The probability $P$ that the three segments form a triangle is the integral of the joint PDF over the region $S$:

$$
P = \iint_S f_{X, Y}(x, y) dA = \int_{1/2}^1 \int_{x-1/2}^{1/2} \frac{1}{x} \, dy \, dx
$$

We first compute the inner integral with respect to $y$:

$$
\int_{x-1/2}^{1/2} \frac{1}{x} \, dy = \frac{1}{x} \left[ \frac{1}{2} - \left(x - \frac{1}{2}\right) \right] = \frac{1 - x}{x} = \frac{1}{x} - 1
$$

Now, we integrate the resulting expression with respect to $x$:

$$
P = \int_{1/2}^1 \left( \frac{1}{x} - 1 \right) dx = \left[ \ln x - x \right]_{1/2}^1
$$

Evaluating the definite integral at the boundaries:

$$
P = (\ln 1 - 1) - \left( \ln \frac{1}{2} - \frac{1}{2} \right) = -1 - (-\ln 2 - 0.5) = \ln 2 - \frac{1}{2}
$$

Therefore, the probability that the three segments can form a triangle is $\ln 2 - 1/2$, which is approximately $0.1931$.

## Prob. 3

To solve these problems, we first derive the joint probability density function (PDF) $f_{X,Y}(x,y)$ using the relationship between marginal and conditional densities:

$$
f_{X,Y}(x,y) = f_X(x) f_{Y|X}(y|x) = \frac{6}{7}(2x^2 + x) \cdot \frac{2x+y}{4x+2}
$$

By factoring the term in $f_X(x)$ as $2x^2+x = x(2x+1)$, we can simplify the expression:

$$
f_{X,Y}(x,y) = \frac{6}{7}x(2x+1) \cdot \frac{2x+y}{2(2x+1)} = \frac{3x(2x+y)}{7} = \frac{6x^2 + 3xy}{7}
$$

The support of the joint PDF is $0 < x < 1$ and $0 < y < 2$.

### (1)

We use the provided conditional PDF $f_{Y|X}(y|x)$ and evaluate it at $x = 1/2$:

$$
f_{Y|X}(y \mid 1/2) = \frac{2(1/2) + y}{4(1/2) + 2} = \frac{1+y}{4}
$$

The conditional probability is found by integrating this density over the interval $(0, 1)$:

$$
\mathbb{P}(Y < 1 \mid X = 1/2) = \int_0^1 \frac{1+y}{4} \, dy = \left[ \frac{y}{4} + \frac{y^2}{8} \right]_0^1 = \frac{1}{4} + \frac{1}{8} = \frac{3}{8}
$$

### (2)

The marginal PDF $f_Y(y)$ is obtained by integrating the joint PDF over all possible values of $X$:

$$
f_Y(y) = \int_0^1 \frac{6x^2 + 3xy}{7} \, dx = \left[ \frac{2x^3}{7} + \frac{3x^2y}{14} \right]_0^1 = \frac{2}{7} + \frac{3y}{14}
$$

Rearranging the terms, we get the marginal PDF for $0 < y < 2$:

$$
f_Y(y) = \frac{4+3y}{14}
$$

### (3)

This probability is the integral of the joint PDF over the region where $x > y$.

Since $x$ is bounded by 1, the region of integration is $0 < y < x < 1$.

$$
\mathbb{P}(X > Y) = \int_0^1 \int_0^x \frac{6x^2 + 3xy}{7} \, dy \, dx = \int_0^1 \left[ \frac{6x^2y + \frac{3}{2}xy^2}{7} \right]_0^x dx
$$

$$
\mathbb{P}(X > Y) = \int_0^1 \frac{6x^3 + \frac{3}{2}x^3}{7} \, dx = \int_0^1 \frac{15x^3}{14} \, dx = \left[ \frac{15x^4}{56} \right]_0^1 = \frac{15}{56}
$$

### (4)

By the definition of conditional probability:

$$
\mathbb{P}(Y > 1/2 \mid X < 1/2) = \frac{\mathbb{P}(Y > 1/2, X < 1/2)}{\mathbb{P}(X < 1/2)}
$$

First, we calculate the denominator:

$$
\mathbb{P}(X < 1/2) = \int_0^{1/2} \frac{6}{7}(2x^2 + x) \, dx = \left[ \frac{4x^3}{7} + \frac{3x^2}{7} \right]_0^{1/2} = \frac{4/8}{7} + \frac{3/4}{7} = \frac{5}{28}
$$

Next, we calculate the numerator:

$$
\mathbb{P}(Y > 1/2, X < 1/2) = \int_0^{1/2} \int_{1/2}^2 \frac{6x^2 + 3xy}{7} \, dy \, dx = \int_0^{1/2} \left[ \frac{6x^2y + \frac{3}{2}xy^2}{7} \right]_{1/2}^2 dx
$$

$$
\mathbb{P}(Y > 1/2, X < 1/2) = \int_0^{1/2} \frac{9x^2 + \frac{45}{8}x}{7} \, dx = \left[ \frac{3x^3}{7} + \frac{45x^2}{112} \right]_0^{1/2} = \frac{3}{56} + \frac{45}{448} = \frac{69}{448}
$$

Finally, we compute the ratio:

$$
\mathbb{P}(Y > 1/2 \mid X < 1/2) = \frac{69/448}{5/28} = \frac{69}{448} \cdot \frac{28}{5} = \frac{69}{80} = 0.8625
$$

## Prob. 4

To solve this problem, we will proceed by determining the marginal density of X, applying the transformation of variables for conditional distributions, and finally setting up the integral for the marginal density of T.

### (1)

The conditional PDF is defined as the joint PDF divided by the marginal PDF of the conditioning variable.

We first calculate $f_X(x)$ by integrating the joint density $f(x,y)$ with respect to $y$ over its support $0 < y < x$.

$$
f_X(x) = \int_0^x 120y(x-y)(1-x) \, dy = 120(1-x) \int_0^x (xy - y^2) \, dy
$$

Evaluating this integral yields:

$$
f_X(x) = 120(1-x) \left[ \frac{1}{2}xy^2 - \frac{1}{3}y^3 \right]_0^x = 120(1-x) \left( \frac{1}{2}x^3 - \frac{1}{3}x^3 \right) = 20x^3(1-x)
$$

For $0 < x < 1$, the marginal PDF is $f_X(x) = 20x^3(1-x)$.

We now find the conditional PDF:

$$
f(y|x) = \frac{f(x,y)}{f_X(x)} = \frac{120y(x-y)(1-x)}{20x^3(1-x)} = \frac{6y(x-y)}{x^3}
$$

The conditional density is $f(y|x) = \frac{6y(x-y)}{x^3}$ for $0 < y < x$.

### (2)

When $X=x$ is fixed, $T$ is a linear transformation of the random variable $Y$.

We let $y = t\sqrt{x}$, which implies the Jacobian $\frac{dy}{dt} = \sqrt{x}$.

The bounds for $t$ are derived from $0 < y < x$, resulting in $0 < t\sqrt{x} < x$, or $0 < t < \sqrt{x}$.

Using the change of variables formula:

$$
f(t|x) = f_Y(t\sqrt{x}|x) \cdot \left| \frac{dy}{dt} \right| = \frac{6(t\sqrt{x})(x - t\sqrt{x})}{x^3} \cdot \sqrt{x}
$$

By factoring out $\sqrt{x}$ from the term $(x - t\sqrt{x})$, we can simplify the expression:

$$
f(t|x) = \frac{6t\sqrt{x} \cdot \sqrt{x}(\sqrt{x}-t)}{x^3} \cdot \sqrt{x} = \frac{6tx(x - t\sqrt{x})}{x^2}
$$

Thus, for $0 < t < \sqrt{x}$, the conditional density is $f(t|x) = \frac{6t(x - t\sqrt{x})}{x^2}$.

### (3)

To find the marginal PDF $f_T(t)$, we integrate the product of the conditional PDF and the marginal PDF of $X$.

Since $x$ must satisfy $x < 1$ and the condition from the support of $f(t|x)$ is $t < \sqrt{x}$ (implying $x > t^2$), the integration limits for $x$ are $[t^2, 1]$.

The general formula is:

$$
f_T(t) = \int_{t^2}^1 f(t|x) f_X(x) \, dx
$$

Substituting our results from the previous parts:

$$
f_T(t) = \int_{t^2}^1 \left[ \frac{6t(x - t\sqrt{x})}{x^2} \right] \left[ 20x^3(1-x) \right] \, dx
$$

Simplifying the terms inside the integral, we get:

$$
f_T(t) = \int_{t^2}^1 120t(x - t\sqrt{x})x(1 - x) \, dx
$$

This integral formula defines the density of $T$ for the range $0 < t < 1$.

## Prob. 5

Because the random variables $X$ and $Y$ are independent, the joint probability of their intersection is simply the product of their individual marginal probabilities:

$$
\mathbb{P}(X \le 1, Y \le 1) = \mathbb{P}(X \le 1) \cdot \mathbb{P}(Y \le 1)
$$

We now calculate the probability for the binomial random variable $X \sim B(4, 0.5)$.

The probability mass function is given by $P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$.

$$
\mathbb{P}(X \le 1) = \mathbb{P}(X = 0) + \mathbb{P}(X = 1)
$$

Substituting $n=4$ and $p=0.5$:

$$
\mathbb{P}(X \le 1) = \binom{4}{0} (0.5)^4 + \binom{4}{1} (0.5)^1 (0.5)^3 = \frac{1}{16} + \frac{4}{16} = \frac{5}{16}
$$

Next, we calculate the probability for the Poisson random variable $Y \sim \mathcal{P}(1)$.

The probability mass function is given by $P(Y=k) = \frac{e^{-\lambda} \lambda^k}{k!}$.

$$
\mathbb{P}(Y \le 1) = \mathbb{P}(Y = 0) + \mathbb{P}(Y = 1)
$$

Substituting $\lambda=1$:

$$
\mathbb{P}(Y \le 1) = \frac{e^{-1} \cdot 1^0}{0!} + \frac{e^{-1} \cdot 1^1}{1!} = e^{-1} + e^{-1} = 2e^{-1} = \frac{2}{e}
$$

Finally, we multiply the two marginal probabilities together to obtain the desired result:

$$
\mathbb{P}(\max\{X, Y\} \le 1) = \left( \frac{5}{16} \right) \left( \frac{2}{e} \right) = \frac{5}{8e}
$$

The exact value is $\frac{5}{8e}$, which is approximately 0.2299.

This result confirms that when variables act independently, we can dismantle a complex joint event into its constituent parts with relative ease.

## Prob. 6

To determine whether the random variables $X$ and $Y$ are independent, we apply the fundamental criterion for independence: two continuous random variables are independent if and only if their joint probability density function (PDF) can be expressed as the product of their marginal PDFs for all $(x, y) \in \mathbb{R}^2$.

$$
f_{X, Y}(x, y) = f_X(x) f_Y(y)
$$

For a point $(X, Y)$ uniformly distributed in the unit disk $D = \{(x, y) \mid x^2 + y^2 \le 1\}$, the joint PDF is constant over the area of the disk.

Since the area of the unit disk is $\pi$, the joint PDF is:

$$
f_{X, Y}(x, y) = \begin{cases} \frac{1}{\pi}, & x^2 + y^2 \le 1 \\ 0, & \text{otherwise} \end{cases}
$$

A quick way to check for independence is to examine the support of the joint PDF.

If $X$ and $Y$ are independent, the support of the joint distribution must be a rectangular region (the Cartesian product of the supports of $X$ and $Y$).

The support here is a circle, which is not a rectangle.

This geometric constraint immediately suggests that $X$ and $Y$ are dependent.

To prove this formally, we calculate the marginal PDF $f_X(x)$ by integrating the joint PDF with respect to $y$.

For a fixed $x \in [-1, 1]$, the variable $y$ ranges from $-\sqrt{1-x^2}$ to $\sqrt{1-x^2}$:

$$
f_X(x) = \int_{-\sqrt{1-x^2}}^{\sqrt{1-x^2}} \frac{1}{\pi} \, dy = \frac{2\sqrt{1-x^2}}{\pi}, \quad -1 \le x \le 1
$$

By symmetry, the marginal PDF of $Y$ is:

$$
f_Y(y) = \frac{2\sqrt{1-y^2}}{\pi}, \quad -1 \le y \le 1
$$

We now test the product $f_X(x) f_Y(y)$ against the joint PDF $f_{X, Y}(x, y)$.

Consider a point near the "corners" of the bounding box, such as $(x, y) = (0.8, 0.8)$.

For this point, $x^2 + y^2 = 0.64 + 0.64 = 1.28$, which is outside the unit disk.

Therefore:

$$
f_{X, Y}(0.8, 0.8) = 0
$$

However, evaluating the product of the marginals at this point gives:

$$
f_X(0.8) f_Y(0.8) = \left( \frac{2\sqrt{1-0.64}}{\pi} \right) \left( \frac{2\sqrt{1-0.64}}{\pi} \right) = \frac{2(0.6)}{\pi} \cdot \frac{2(0.6)}{\pi} = \frac{1.44}{\pi^2} \neq 0
$$

Since $f_{X, Y}(0.8, 0.8) \neq f_X(0.8) f_Y(0.8)$, the factorization criterion fails.

We conclude that $X$ and $Y$ are not independent.

Intuitively, knowing that $X$ is very large (close to 1) restricts the possible values of $Y$ to a very small interval around zero, whereas if $X=0$, $Y$ can be any value between $-1$ and $1$.

This dependency on the value of $X$ confirms that the variables are coupled.

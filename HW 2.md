---
~
---
### Prob. 1
Firstly, $\forall A_{i}$, we have
$$
A_{i}\in \mathscr{F}, \forall i = 1,2, \dots, n
$$
Therefore, $\forall 0\le k\le n$, take
$$
S_{j}^{k} \subset 2_{k}^{\{1,2,\dots, n\}}, \quad0\le j \le \binom{n}{k}
$$
which is a subset of $2^{\{1,2,\dots, n\}}$ with $|S_{j}^{k}| = k$, and $2_{k}^{\{1,2,\dots, n\}}=\{S_{j}^{k}| 0\le j \le \binom{n}{k} \}$ as their collection. As completion, we define
$$
S_{1}^{0} \triangleq \varnothing
$$
Now it's easy to find that 
$$
\bigcup_{p\in S_{j}^{k}}A_{p}\triangleq A_{S_{j}^{k}} \in \mathscr{F}, \quad\forall S_{j}^{k}\subset 2_{k}^{\{1,2,\dots, n\}}
$$
Denote that 
$$
\{1,2,\dots, n\}\setminus S_{j}^{k} \triangleq (S_{j}^{k})^{c}
$$
where it's evident that
$$
(S_{j}^{k})^{c}\subset 2_{n-k}^{\{1,2,\dots, n\}}
$$
Moreover, by $A_{i}\cap A_{j} = \varnothing \quad(\forall i\ne j)$, $\bigcup_{i=1}^{n}A_{i}=\Omega$,  we could find that
$$
(A_{S_{j}^{k}})^{c}= A_{\{1,\dots, n\}\setminus S_{j}^{k}}\triangleq A_{(S_{j}^{k})^{c}}
$$
When $k=1$, $A_{S_{j}^{k}}=A_{j}$, so
$$
\begin{align*}
\mathscr{F} =& \left\{A_{S_{j}^{k}}|0\le k\le n, 1\le j \le \binom{n}{k} \right\}\\
=& 2^{\Omega}\\
\implies |\mathscr{F}| =& 2^{n}
\end{align*}
$$

### Prob. 2
The existence of $\lim_{n\to\infty}A_{n}$ leads to
$$
\limsup_{n\to \infty} A_{n} = \liminf_{n\to \infty} A_{n} = \lim_{n\to \infty}A_{n}
$$
By the properties of upper and lower limit, we have
$$
\begin{gathered}
P(\limsup_{n\to \infty} A_{n}) \ge \limsup_{n\to \infty} P(A_{n})
\\
P(\liminf_{n\to \infty}A_{n})\le \liminf_{n\to \infty}P(A_{n})
\end{gathered}
$$
and by definition
$$
	\limsup_{n\to \infty}P(A_{n}) \le \limsup_{n\to \infty} P(A_{n}) 
$$
Then we can find that
$$
\begin{gathered}
	\limsup_{n\to \infty}P(A_{n})\le P(\limsup_{n\to \infty} A_{n}) = P(\lim_{n\to \infty} A_{n}) = P(\liminf_{n\to \infty}A_{n}) \le \liminf_{n\to \infty}P(A_{n})\\
	\limsup_{n\to \infty}P(A_{n}) \le \limsup_{n\to \infty} P(A_{n}) 
	\\
	\implies P(\lim_{n\to \infty}A_{n}) = \lim_{n\to \infty}P(A_{n})
\end{gathered}
$$
Q.E.D.

### Prob. 3
Define events
$$
A_{i}, \quad i = 1,2
$$
which means the $i$th toss is a head. Then the statement of Alice becomes that
$$
\begin{gathered}
P(A_{1}A_{2}|A_{1}) = {P(A_{1}A_{2})\over P(A_{1})}\\
P(A_{1}A_{2}|A_{1}\cup A_{2}) = {P(A_{1}A_{2})\over P(A_{1}\cup A_{2})}
\end{gathered}
$$
And by the additivity
$$
\begin{align*}
P(a_{1}\cup A_{2}) =& P(A_{1}) + P(A_{2}\setminus A_{1}) \ge P(A_{1})\\
\implies P(A_{1}A_{2}|A_{1}) \ge& P(A_{1}A_{2}|A_{1}\cup A_{2})
\end{align*}
$$
Note that we'd never used the condition that the coin is fair, so the conclusion remains.
The generalization of Alice's reasoning could be that:
$$
\forall A\subset B\subset C, P(A|B)\ge P(A|C)
$$

### Prob. 4
Define events
$$
A_{i}, \quad i = 1,2,3
$$
The target case could be expressed as
$$
A_{1}A_{2}A_{3}\cup A_{1}^{c}A_{2}^{c}A_{3}^{c}
$$
It's evident that
$$
A_{1}A_{2}A_{3}\cap A_{1}^{c}A_{2}^{c}A_{3}^{c} = \varnothing
$$
and 
$$
\begin{align*}
P(A_{1}A_{2}A_{3}) =& P(A_{3}|A_{1}A_{2})P(A_{1}A_{2})\\
=& {1\over 2} \cdot {1\over 4} = {1\over 8}
\end{align*}
$$
By symmetry and additivity, 
$$
P(A_{1}A_{2}A_{3}\cup A_{1}^{c}A_{2}^{c}A_{3}^{c}) = 2\times {1\over 8} = {1\over 4}
$$
So the statement is wrong from the respect of conditional probability.

### Prob. 5
#### (1)
Define events
$$
\begin{gathered}
A_{i},\quad i = 1,2,3
\\
B_{i} \quad i = 1,2
\end{gathered}
$$
where the former indicates the class choice, and the latter indicates the $i$th choice of male.
The probability of target event could be calculated as
$$
\begin{align*}
P(B_{1}) =& \sum_{i=1}^{3}P(B_{1}|A_{1}) P(A_{i})\\
=& {3\over 10}\times{1\over 5} + {7\over 20}\times{2\over5} + {12\over 20}\times {2\over 5}\\
=& {11\over 25}
\end{align*}
$$
#### (4)
The conditional probability could be calculated as
$$
P(B_{1}| B_{2}^{c}) = {P(B_{1}B_{2}^{c})\over P(B_{2}^{c})}
$$
The numerator:
$$
\begin{align*}
P(B_{1}B_{2}^{c}) =& \sum_{i=1}^{3}P(B_{1}B_{2}^{c}|A_{i})A_{i}\\
=& {3\over 10}\times{7\over9}\times{1\over 5} + {7\over 20}\times{13\over 19}\times{2\over5}+{12\over20}\times{8\over19}\times{2\over5}\\
=& {347\over1425}
\end{align*}
$$
The denominator
$$
\begin{align*}
P(B_{2}^{c}) = & \sum_{i=1}^{3}P(B_{1}B_{2}^{c}\cup B_{1}^{c}B_{2}^{c}|a_{i})\\
=& \left(
{3\over 10}\times{7\over9}+{7\over10}\times{6\over9} 
\right){1\over5} + \left(
{7\over20}\times{13\over19}+{13\over20}\times{12\over19} 
\right){2\over5} + \left(
{12\over20}\times{8\over19}+{8\over20}\times{7\over19} 
\right){2\over5}\\
=& {14\over25}
\end{align*}
$$
Therefore,
$$
\begin{align*}
P(B_{1}| B_{2}^{c}) = {P(B_{1}B_{2}^{c})\over P(B_{2}^{c})} = {347\over798} = 0.4348
\end{align*}
$$

### Prob. 6
Define events
$$
A_{i}, \quad i= 1,\dots k
$$
which means white ball is chosen in the $i$th draw.
We can find that 
$$
P(A_{1}) = {m\over m+n}
$$
and 
$$
\begin{align*}
P(A_{2}) = & P(A_{2}|A_{1})P(A_{1})+P(A_{2}|A_{1}^{c})P(A_{1}^{c})\\
=& {m+1\over m+n+1} \cdot {m\over m+n} + {m\over m+n+1} \cdot{n\over m+n}\\
=& {m(m+n+1)\over (m+n) (m+n+1)}\\
=& {m\over m+n}
\end{align*}
$$
Suppose that 
$$
P(A_{s}) = {m\over m+n}, \quad \forall1\le s\le k-1
$$
so that we have
$$
\begin{align*}
P(A_{k}) =& P(A_{k}|A_{k-1})P(A_{k-1}) + P(A_{k}|A_{k-1}^{c})P(A_{k-1}^{c})
\end{align*}
$$
By induction on $k-1$
$$
\begin{align*}
P(A_{k}) =& P(A_{k}|A_{k-1})P(A_{k-1}) + P(A_{k}|A_{k-1}^{c})P(A_{k-1}^{c})\\
=& {m+1\over m+n+1} \cdot {m\over m+n} + {m\over m+n+1} \cdot{n\over m+n}\\
=& {m(m+n+1)\over (m+n) (m+n+1)}\\
=& {m\over m+n}
\end{align*}
$$
Then by the induction hypothesis, $P(A_{k})={m\over m+n}$.

### Prob. 7
#### (a)
The urn could be described as
$$
U = \{R_{1},\dots, R_{m}, W_{1},\dots W_{n} \}
$$
by which the sample space could be defined as
$$
\Omega_{1} = \{S \subset U \ | \ |S| = 2 \}
$$
According to the discrete uniform law, the probability should be calculated as
$$
\begin{align*}
P_{1}=& P(\{R_{i}W_{j}|\forall 1\le i\le m, 1\le j\le n \}\cup \{W_{i}R_{j}| \forall1\le i \le n, 1\le j\le m \})\\
=& {\binom{m}{1}\binom{n}{1}\over \binom{m+n}{2}}\\
=& {2mn\over (m+n)(m+n-1)}
\end{align*}
$$
By sequential approach, the sample space should be described as
$$
\Omega_{2} = \{RR, RW, WR, WW \}
$$
by which the probability
$$
\begin{align*}
P_{2}=& P(WR) + P(RW)\\
=& P(WR|W)P(W) + P(RW|R) P(R)\\
=& {m\over m+n-1}\cdot{n\over m+n} + {n \over m+n-1}\cdot{m \over m+n }\\
=& {2mn \over (m+n)(m+n-1)}
\end{align*}
$$
#### (b)
Using the description of the urn in (a), the sample space
$$
\Omega = \{S \subset U \ |\ |S|=k, k=1,2,3 \}
$$
Then the target probability
$$
\begin{align*}
P_{3}=& P(k=1)+ P(RR|k=2)P(k=2) + P(RRR|k=3)P(k=3)\\
=& {1\over 3}\times{m \over m+n} + {1\over3}\times {\binom{m}{2}\over m+n} + {1\over3}\times {\binom{m}{3}\over m+n}\\
=& {m+{m(m-1)\over 2}+{m(m-1)(m-2)\over 3}\over 3(m+n)} \\
=& {m(m-2)(2m+1)\over 18(m+n)}
\end{align*}
$$

### Prob. 8
According to the graph, the pagerank could be described as a linear equation
$$
(A-I)\begin{bmatrix}
\pi(1) \\ \pi(2) \\ \pi(3) \\ \pi(4) \\ \pi(5)
\end{bmatrix} = 0
$$
where
$$
A = \begin{bmatrix}
0 & 0 & 1 & 3 & 0 \\
{1\over 2} & 0 & 0 & {1\over3} & {1\over2} \\ 
0 & 1 & 0 & 0 & {1\over2} \\ 
{1\over2} & 0 & 0 & 0 & 0 \\ 
0 & 0 & 0 & {1\over3} & 0
\end{bmatrix}
$$
The final result of Gaussian elimination of $A-I$:
$$
\begin{bmatrix}
-1 & 0 & 1 & {1\over3} & 0 \\ 
0 & -1 & {1\over2} & {1\over2} & {1\over2} \\ 
0 & 0 & -{1\over2} & {1\over2} & 1 \\ 
0 & 0 & 0 & -{1\over3} & 1 \\ 
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
combining with the given condition
$$
\sum_{j=1}^{5}\pi(j)= 1
$$
we get the final linear equations
$$
\begin{cases}
\pi(4) = 3\pi(5) \\
2\pi(5) +\pi(4) -\pi(3) =0 \\
\pi(5) + \pi(4) + \pi(3) = 2\pi(2) \\
\pi(4) + 3\pi(3) =3\pi(1) \\
\sum_{j=1}^{5}\pi(j) =1
\end{cases}
$$
and the final result:
$$
\begin{bmatrix}
\pi(1) \\ \pi(2) \\ \pi(3) \\ \pi(4) \\ \pi(5)
\end{bmatrix} = \begin{bmatrix}
{12\over39} \\ {9\over 39} \\ {10\over39} \\ {6\over39} \\ {2\over39}
\end{bmatrix}
$$
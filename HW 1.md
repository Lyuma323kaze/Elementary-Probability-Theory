### Question 3

The conditions where the red ones are mismatched are listed as below:
- 2 red saucers with 2 white cups
- 2 red saucers with 1 white cup and 1 starred cup
- 2 red saucers with 2 starred cups
The probabilities of each condition can be shown as below:
- 2 white cups: $P(WW)={\frac{\binom{2}{2}}{ \binom{2}{4}}}={1\over 6}$
- 1 white cup and 1 starred cup: $P(WS)=\frac{\binom{2}{1}\binom{2}{1}}{\binom{4}{2}}={2\over 3}$
- 2 starred cups: $P(SS)=\frac{\binom{2}{2}}{\binom{4}{2}}={1\over 6}$
Considering the first case, when the 2 white cups are all placed onto red saucers, the probability that white saucers are mismatched is:
$$
P(M|WW)={\binom{2}{2}\over \binom{4}{2}}={1\over 6}
$$
Similarly, $P(M|SS)={1\over 6}$.
Considering the second case. Now the white ones should be mismatched, so the probability that white saucers are mismatched is
$$
P(M|WS)={\binom{3}{2}\over \binom{4}{2}}={1\over 2}
$$
The target probability
$$
\begin{align*}
P(M)=&2P(WW)P(M|WW)+P(WS)P(M|WS)\\
=&2\times {1\over 6}\times {1\over 6} + {2\over3}\times{1\over2}\\
=&{7\over18}
\end{align*}
$$

### Question 4

Defining the events
$$
s_i=\{
{\rm outcome\ is\ i}
\}\qquad i=1,\dots,6
$$
According to the descriptions, assume that
$$
P(s_i)=\begin{cases}
p & {\rm i\ is\ even} \\
p/2 & {\rm i\ is\ odd}
\end{cases}
$$
By additivity, we know that
$$
\begin{align*}
&3p+3p/2=1\\
\implies& p={2\over 9}\\
\implies& P(s_i)=\begin{cases}
{2\over 9} & {\rm i\ is\ even} \\
{1\over 9} & {\rm i\ is\ odd}
\end{cases}
\end{align*}
$$
The target event
$$
\{ {\rm outcome < 4} \}=s_{1}\cup s_{2}\cup s_{3}
$$
Since $s_{i}\cap s_{j}= \varnothing \quad (i\ne j)$, we have
$$
\begin{align*}
P(s_{1}\cup s_{2}\cup s_{3}) =& P(s_{1}) + P(s_{2}) + P(s_{3})\\
=& {1\over 9} + {2\over 9} + {1\over 9}\\
=& {4\over 9}
\end{align*}
$$

### Question 5

S could be denoted as
$$
S = \{ 0_{i}1|i\in \mathbb{N} \}
$$

(i) Xiao Qing wins, 
$$
A = \{0_{i}1 | i=3k, k\in \mathbb{N} \}
$$

(ii) Xiao Hua wins,
$$
B = \{ o_{i}1 | i=3k+1,k\in \mathbb{N}\}
$$

(iii)
$$
\begin{align*}
(A\cup B)^{c}=&\{ 0_{i}1 | i=3k,3k+1,k\in\mathbb{N} \}^c\\
=& \{0_{i}1|i=3k+2,k\in\mathbb{N} \}\\
=&\{{\rm Xiao\ Zi\ wins} \}
\end{align*}
$$

### Question 6

It's obvious that the target event could only occur when $n\ge24$.
Denote the target event as $A_{n}$, when $A_{n}$ occurs, there must be a subset consisting of 24 different bookmarks within the $n$ bookmarks.
Let the set containing 24 different bookmarks be denoted as $S$, and the set consisting of the $n$ bookmarks obtained be denoted as $B$, then the event $A$ could be defined as
$$
A = \{S\subset B \}
$$
So by classical model, the probability of $A$ should be
$$
\begin{align*}
P(A)=&\binom{n}{24}\binom{24}{1}\binom{23}{1}\cdots\binom{2}{1}\left({1\over 24}\right)^{24}\cdot \left({1\over 24} \right)^{n-24}\\
=&\binom{n}{24}\left(\prod_{i=1}^{24}i \right)\cdot \left({1\over 24} \right)^{n}
\end{align*}
$$

### Question 9

#### Part 1 (Bonferroni's inequality)
$$
P(\bigcup_{i=1}^{n}A_{i})\ge \sum_{1\le i \le n}P(A_{i}) - \sum_{1\le i<j \le n}P(A_{i}\cap A_{j})
$$
**Proof.** By principle of inclusion-exclusion,
$$
\begin{align*}
P(\bigcup_{i=1}^{n}A_{i}) =& \sum_{k=1}^{n}(-1)^{k-1}P_{k}\\
=& \sum_{1\le i\le n}P(A_{i})- \sum_{1\le i<j \le n}P(A_{i}\cap A_{j}) + \sum_{k=3}^{n}(-1)^{k-1}P_{k}
\end{align*}
$$
When $n=2$, the 3rd term above vanishes, and the original inequality holds trivially. 
When $n>2$, by induction, assume that the inequality holds when $n=m$, i.e.
$$
P(\bigcup_{i=1}^{m}A_{i})\ge \sum_{1\le i \le m}P(A_{i}) - \sum_{1\le i<j \le m}P(A_{i}\cap A_{j})
$$
Then when $n=m+1$, 
$$
\begin{align*}
P(\left(\bigcup_{i=1}^{m}A_{i}\right)\cup A_{m+1})=&
P(\bigcup_{i=1}^{m}A_{i})+P(A_{m+1})-P(\left(\bigcup_{i=1}^{m}A_{i} \right)\cap A_{m+1})\\
\ge& \sum_{1\le i\le m+1}P(A_{i}) - \sum_{a\le i<j\le m}P(A_{i}\cap A_{j}) - P(\left(\bigcup_{i=1}^{m} A_i \right)\cap A_{m+1})\\
=& \sum_{1\le i \le n}P(A_{i}) - \sum_{1\le i<j \le n}P(A_{i}\cap A_{j})- P(\bigcup_{i=1}^{m} (A_i \cap A_{m+1}))\\
\ge& \sum_{a\le i\le m+1} P(A_{i}) - \sum_{1\le i<j \le m}P(A_{i}\cap A_{j}) - \sum_{i=1}^{m}P(A_{i}\cap A_{m+1})\\
=&\sum_{a\le i\le m+1} P(A_{i}) - \sum_{1\le i<j\le m+1}P(A_{i}\cap A_{j})
\end{align*}
$$

in which the last inequality follows from Boole's inequality:
$$
P(\bigcup_{i=1}^{n}A_{i})\le \sum_{i=1}^{n}P(A_{i})
$$
Now we've proved that Bonferroni's inequality holds for $n=m+1$. Hence by inductive hypothesis, Bonferroni's inequality is established.

#### Part 2 (Kounia's inequality)
$$
P(\bigcup_{i=1}^{n}A_{i})\le \min_{k}\left\{
\sum_{a\le i \le n}P(A_{i})-\sum_{i\ne k}P(A_{i}\cap A_{k})
\right\}
$$
**Proof.**  $\forall 1\le k \le n$, we have
$$
\begin{align*}
P(\bigcup_{i=1}^{n}A_{i})=& P\left((\bigcup_{i\ne k}A_{i})\cup A_{k} \right)\\
\le& P(A_{k}) + \sum_{i\ne k}P(A_{i}\setminus A_{k})\\
=& P(A_{k}) + \sum_{i\ne k}P(A_{i}) - \sum_{i\ne k} P(A_{i}\cap A_{k})\\
=& \sum_{i=1}^{n}P(A_{i}) - \sum_{i\ne k} P(A_{i}\cap A_{k})
\end{align*}
$$
Hence we know
$$
P(\bigcup_{i=1}^{n}A_{i})\le \min_{k}\left\{
\sum_{a\le i \le n}P(A_{i})-\sum_{i\ne k}P(A_{i}\cap A_{k})
\right\}
$$
Q.E.D.

### Question 10

Let $m$ be the number of events occurring simultaneously, then the subjective probability of $A_{r}$ should be
$$
p=P(A_{r}) = {m\over n}
$$
Similarly, the subjective probability of $A_{r}\cap A_{s}\ (r\ne s)$ should be
$$
q=P(A_{r}\cap A_{s})={\binom{m}{2}\over \binom{n}{2}}
$$
According to the description, $1\le m\le 2$, therefore
$$
\begin{align*}
p\ge& {1\over n}\\
q\le& {2\over n(n-1)}\\
\le {2\over n}
\end{align*}

$$
Q.E.D.
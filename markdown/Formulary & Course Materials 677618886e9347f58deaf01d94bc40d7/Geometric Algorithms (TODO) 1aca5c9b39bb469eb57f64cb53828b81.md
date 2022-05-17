# Geometric Algorithms (TODO)

# Smallest Enclosing Circle

Let $P$ be a given set of $n$ points on a plane. We want to find the circle $C(P)$ such that $C(P)$ encloses all points in $P$ and such that the radius of $C(P)$ is as small as possible. For a circle $C$ we denote by $C^\bullet$ the circular disk which is enclosed by $C$ (closed, thus including $C$). We allow points in $P$ to also lie on $C(P)$ - they do not have to lie strictly within the circle.

<aside>
📌 *For every (finite) set of points $P$ in $\mathbb{R}^2$ there exists a unique smallest enclosing circle $C(P)$.*

</aside>

<aside>
📌 *For every (finite) set of points $P$ in $\mathbb{R}^2$ with $\lvert P \rvert \geq 3$ there exists a subset $Q \sube P$ such that $\lvert Q \rvert = 3$ and $C(Q) = C(P)$.*

</aside>

This lemma immediately allows a $O(n^4)$-time algorithm for computing $C(P)$. We can then introduce a bit of randomization to the algorithm to try to optimize it a little, which fails however as they still both have the same asymptotic time complexity:

![Untitled](Geometric%20Algorithms%20(TODO)%201aca5c9b39bb469eb57f64cb53828b81/Untitled.png)

![Untitled](Geometric%20Algorithms%20(TODO)%201aca5c9b39bb469eb57f64cb53828b81/Untitled%201.png)

We could try to draw more than just 3 points in each iteration to have a higher chance of including the 3 defining points, to for example 11 points instead. This however effects no change in the asymptotic runtime, as one can verify. To really speed up the computation we can introduce another key idea: we weight the points outside the of $C(Q)$ doubly in every iteration.

![Untitled](Geometric%20Algorithms%20(TODO)%201aca5c9b39bb469eb57f64cb53828b81/Untitled%202.png)

<aside>
📌 *Let $n_1,...,n_t$ be natural numbers and $N = \sum_{i=1}^tn_i$.*

*We generate $\Chi \in \{1,...,t\}$ randomly as follows:*

![Untitled](Geometric%20Algorithms%20(TODO)%201aca5c9b39bb469eb57f64cb53828b81/Untitled%203.png)

*It then holds that $\Pr[\Chi = i]=\frac{n_i}{N}$ for all $i=1,...,t$.*

</aside>

With this lemma we can thus draw points from $P$ in such a way that the probability of a point is proportional to the number of its copies. If we now respect points we’ve already drawn then we can compute our desired subset $Q$ consisting of 11 points of $P$ in $O(n)$.

<aside>
📌 *Let $P$ be a set of $n$ (not necessarily distinct) points and for $r \in \mathbb{R}$ let $R$ be randomly, uniformly distributed in $\binom{P}{r}$. Then the expected number of points of $P$ that are outside of $C(R)$ is at max $3\frac{n-r}{r+1} \leq 3 \frac{n}{r+1}$.*

</aside>

<aside>
📖 *The algorithm $\text{Randomized\_CleverVersion}$ computes the smallest enclosing circle of $P$ in expected time $O(n \log n)$.*

</aside>

This algorithm is a variation of the algorithm of Clarkson. There exist randomized algorithms that compute $C(P)$ optimally in linear time.

## Sampling Lemma

<aside>
💡 Let $S$ be a finite set with $n$ elements and let $\phi$ be an arbitrary function on $2^S$ into an arbitrary codomain. We define

$$
\begin{align*}
V(R)=V_\phi(R) & = \{s \in S \space \vert \space \phi(R \cup \{s\}) \neq \phi(R)\} \\
X(R) = X_\phi(R) & = \{s \in R \space \vert \space \phi(R \setminus \{s\}) \neq \phi(R)\}.
\end{align*}
$$

We call elements in $V(R)$ *destroyers* of $R$ and elements in $X(R)$ *extreme* in $R$.

</aside>

<aside>
📌 (Sampling Lemma).

*Let $k \in \mathbb{N}, 0 \leq k \leq n$. We set $v_k = \mathbb{E}[\lvert V(R)\rvert]$ and $x_k = \mathbb{E}[\lvert X(R) \rvert]$, where $R$ is a subset of $S$ with $k$ elements that is random, uniformly distributed from $\binom{S}{k}$. The for $r \in \mathbb{N}, 0 \leq r \lt n$ it holds that* 

$$
\frac{v_r}{n-r} = \frac{v_{r+1}}{r+1}.
$$

</aside>

# Convex Closure
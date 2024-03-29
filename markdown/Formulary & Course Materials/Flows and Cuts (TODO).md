# Flows and Cuts (TODO)

# Flows

<aside>
💡 A *network* is a tuple $N = (V,A,c,s,t)$, where the following hold:

1. $(V,A)$ is a directed graph,
2. $s\in V$ is the *source*,
3. $t \in V \setminus \{s\}$ is the *target* and,
4. $c : A \longrightarrow \mathbb{R}^+_0$ is the *capacity function*.
</aside>

<aside>
💡 Let $N = (V,A,c,s,t)$ be a network. A *flow* in $N$ is a function $f: A \longrightarrow \mathbb{R}$ with the conditions

1. $0 \leq f(e) \leq c(e)$ for all $e \in A$, the *admissibility*, and
2. for all $v \in V \setminus \{s,t\}$ it holds that 
    
    $$
    \sum_{u\in V: (u,v) \in A}f(u,v) = \sum_{u\in V: (v,u)\in A}f(v,u)
    $$
    
    which is called the *flow conservation*.
    

The *value* of a flow $f$ is defined by 

$$
\text{val}(f) = \text{netoutflow}(s) = \sum_{u \in V: (s,u)\in A}f(s,u) - \sum_{u \in V: (u,s)\in A}f(u,s).
$$

</aside>

<aside>
📌 *The net inflow of the target equals the value of the flow, i.e.,*

$$
\text{netinflow}(t)=\sum_{u\in V:(u,t) \in A}f(u,t) - \sum_{u \in V:(t,u) \in A}f(t,u) = \text{val}(f).
$$

</aside>

# Cuts

<aside>
💡 An $s$-$t$-*cut* for a network $(V,A,c,s,t)$ is a partition $(S,T)$ of $V$ (i.e., $S \cup T = V$ and $S \cap T = \varnothing$) with $s \in S$ and $t \in T$. The *capacity* of an $s$-$t$-cut $(S,T)$ is defined by

$$
\text{cap}(S,T) = \sum_{(u,w)\in(S \times T) \cap A} c(u,w).
$$

</aside>

<aside>
📌 *Let $f$ be a flow and $(S,T)$ be an $s$-$t$-cut in a network $(V,A,c,s,t)$. It then holds that*

$$
\text{val}(f) \leq \text{cap}(S,T).
$$

</aside>

<aside>
📖 (Max-Flow-Min-Cut Theorem).

*Every network $N = (V,A,c,s,t)$ fulfills* 

$$
\max_{f \space \text{flow in $N$}} \text{val}(f) = \min_{(S,T) \space \text{$s$-$t$-cut in $N$}} \text{cap}(S,T).
$$

</aside>

# Augmenting paths

The fundamental concept behind many max-flow algorithms is to start with an arbitrary flow (e.g., $f$ constant $0$ is good for basically all cases) and improving it successively. A first approach to this could look as follows. Assume we find a directed path $P$ from source to target, where the flow has not used the full capacity of all the edge, i.e., $f(e) \lt c(e)$ for all $e$ in $P$. Now let $\delta = \min_{e \in P} c(e) - f(e)$. If we now increase the value of the flow by $\delta$ in all edges of $P$, we do not break flow conservation and the value of the flow has increased by $\delta$. Sadly, there do exist flows that can not be improved with this scheme even though they are not optimal. One can not only increase flow in an outgoing edge, but also decrease flow in another incoming edge to increase the resulting flow. In this sense we can entertain paths from source to target in which edges can be directed both forwards and backwards. Let us assume, that we can increase flow in every edge that is directed in forwards direction by $\delta$ without breaking admissibility, and that we can decrease the flow in every edge that is directed in backwards direction by $\delta$ without having negative flow. Then we can modify flow along such a path without breaking flow conservation. If we successively optimize flow with these so-called *augmenting paths* one can only get stuck in maximal flows. Interestingly, this “algorithm” only has finitely many steps when the capacities of a flow are rational.

# Residual Network

<aside>
💡 Let $N = (V,A,c,s,t)$ be a network without opposing edges and let $f$ be a flow in $N$. The *residual network* $N_f=(V,A_f,r_f,s,t)$ is defined as follows:

1. If $e \in A$ with $f(e) \lt c(e)$, then $e$ is also an edge in $A_f$ with $r_f(e) = c(e)-f(e)$.
2. If $e \in A$ with $f(e) \gt 0$, then $e^\text{opp}$ is in $A_f$ with $r_f(e^\text{opp}) = f(e).$
3. Only edges ad defined in points 1 and 2 are in $A_f$.

$r_f(e)$, $e \in A_f$, is called the *residual capacity* of edge $e$.

</aside>

<aside>
📖 *A flow $f$ in a network $N$ is a maximal flow if and only if there does not exist a directed path from the source $s$ to the target $t$ in the residual network $N_f$. For every such maximum flow there does exist an $s$-$t$-cut $(S,T)$ with $\text{val}(f) = \text{cap}(S,T)$.*

</aside>

# Algorithms

## Ford-Fulkerson

By searching for augmenting paths in the residual network we can find a max-flow in $O(mnU)$.

<aside>
📖 *If all capacities are integer values and at max as large as some $U$ and there are no opposing edges in a network then there exists an integer maximum flow that can be found in $O(mnU)$, where $n$ is the number of nodes and $m$ is the number of edges of the network.*

</aside>

### Pseudocode

![Untitled](Flows%20and%20Cuts%20(TODO)/Untitled.png)

## Other Algorithms

<aside>
💡 (Capacity-Scaling, Dinitz-Gabow, 1973).

If in a network all capacities are integers and at max as large as some $U$, then there exists an integer maximum flow, that can be found in $O(mn(1+\log U))$, where $n$ is the number of nodes and $m$ is the number of edges of the network.

</aside>

<aside>
💡 (Dynamic Trees, Sleator-Tarjan, 1983).

A maximal flow of a network can be found in $O(mn\log n)$, where $n$ is the number of nodes and $m$ is the number of edges of the network.

</aside>

# Bipartite Matching as a Flow Problem

<aside>
📌 *The maximum size of a matching in a bipartite graph equals the value of a maximum flow in network $N$.*

</aside>

# Edge- and Node-Disjoint Paths

<aside>
💡 Recall Menger’s Theorems:

<aside>
📖 Menger’s Theorem (Vertices):

*Let $G = (V, E)$ be a graph. Then it holds that $G$ is $k$-connected if and only if $\forall u, v \in V, u \neq v$ there exist $k$ disjoint $u$-$v$-paths.*

</aside>

<aside>
📖 Menger’s Theorem (Edges):

*Let $G=(V, E)$ be a graph. Then it holds that $G$ is $k$-edge-connected if and only if $\forall u, v \in V, u \neq v$ there exist $k$ edge-disjoint $u$-$v$-paths.*

</aside>

By cleverly converting a graph to a network we can turn the connectivity problem into a max-flow problem: 

- Edges:
    
    We split the undirected edges of the original graph into two opposing edges, both with capacity 1. If we now add new vertices $s$ and $t$ to some vertices $u,v$ of the original graph via one outgoing (in the case of $s$) and one incoming edge (in the case of $t)$, as shown in the picture. The value of a max-flow directly corresponds to the number of edge-disjoint $u$-$v$-paths.
    
    ![Untitled](Flows%20and%20Cuts%20(TODO)/Untitled%201.png)
    
- Nodes:
    
    We transform the graph to a network exactly the same way as before, only this time we also split any node $x$ of the original graph that is not $u$ or $v$ into $x_\text{in}$ and $x_\text{out}$ and add an extra edge from $x_\text{in}$ to $x_\text{out}$ with capacity $1$, as shown in the picture. The value of a max-flow equals the number of disjoint $u$-$v$-paths.
    
    ![Untitled](Flows%20and%20Cuts%20(TODO)/Untitled%202.png)
    
</aside>

# Image Segmentation as a Cut-Problem

# Flows and Convex Sets

# Minimum Cuts in Graphs
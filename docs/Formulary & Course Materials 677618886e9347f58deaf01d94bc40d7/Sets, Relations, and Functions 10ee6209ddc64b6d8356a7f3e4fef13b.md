# Sets, Relations, and Functions

# Sets and Operations on Sets


💡 The number of elements of a finite set $A$ is called its cardinality and is denoted $\lvert A \rvert$.




💡 $A = B \stackrel{\mathrm{def}}{\iff} \forall x \space (x \in A \leftrightarrow x \in B).$




📌 *For any $a$ and $b$, $\{a\} = \{b\} \implies a = b$.*




💡 The set $A$ is a subset of the set $B$, denoted $A \sube B$, if every element of $A$ is also an element of $B$, i.e.,

$$
A \sube B \stackrel{\mathrm{def}}{\iff} \forall x \space (x \in A \rightarrow x \in B).
$$




💡 $A = B \iff (A \sube B) \land (B \sube A)$.




💡 $A \sube B \land B \sube C \implies A \sube C$. (transitivity of $\sube$)




💡 A set is called *empty* if it contains no elements and is ofent denoted as $\varnothing$ or $\{\}$. In other words, $\forall x \space (x \notin \varnothing)$.




📌 *There is only one empty set.*




📌 *The emtpy set is a subset of every set, i.e., $\forall A \space (\varnothing \sube A)$.*




💡 The *power set* of a set $A$, denoted $\mathcal{P}(A)$, is the set of all subsets of $A$:

$$
\mathcal{P}(A) \stackrel{\mathrm{def}}{=} \{S \space | \space S \sube A \}.
$$




💡 The *union* of two sets $A$ and $B$ is defined as

$$
A \cup B \stackrel{\mathrm{def}}{=} \{x \space | \space x \in A \lor x \in B \},
$$

and their *intersection* is defined as

$$
A \cap B \stackrel{\mathrm{def}}{=} \{x \space | \space x \in A \land x \in B \} .
$$




💡 For a given universe $U$, the *complement* of a set $A \sube U$, denoted $\overline{A}$, is

$$
\overline{A} \stackrel{\mathrm{def}}{=} \{x \in U \space | \space x \notin A \}
$$

or simply $\overline{A} = \{x \space | \space x \notin A \}$.




💡 The *difference* of sets $B$ and $A$, denoted $B \setminus A$ is the set of elements of $B$ without those that are elements of $A$:

$$
B \setminus A \stackrel{\mathrm{def}}{=} \{x \in B \space | \space x \notin A \}.
$$




📖 *For any sets $A$, $B$ and $C$, the following laws hold:*

*Idempotence:* $A \cap A = A$ and $A \cup A = A$

*Commutativity: $A \cap B = B \cap A$ and* $A \cup B = B \cup A$

*Associativity: $A \cap (B \cap C) = (A \cap B) \cap C$ and* $A \cup (B \cup C) = (A \cup B) \cup C$

*Distributivity: $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ and* $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$

*Consistency: $A \sube B \iff A \cap B = A \iff A \cup B = B$*




💡 The *Cartesian product* $A \times B$ of two sets $A$ and $B$ is the set of all ordered pairs with the first component from $A$ and the second component from $B$:

$$
A \times B = \{(a, b) \space | \space a \in A \land b \in B \}.
$$



# Relations


💡 A *(binary) relation $\rho$ from a set $A$ to a set* $B$ (also called an $(A, B)$-*relation*) is a subset of $A \times B$. If $A = B$, then $\rho$ is called a relation *on* $A$.




💡 Instead of $(a, b) \in \rho$ one usually writes

$$
a \space \rho \space b,
$$

and sometimes we write $a \space \cancel \rho \space b$ if $(a, b) \notin \rho$.




💡 For any set $A$, the *identity relation* on $A$, denoted $\text{id}_A$ (or $\text{id}$), is the relation $\text{id}_A = \{(a, a) \space | \space a \in A\}$.




💡 The *inverse* of a relation $\rho$ from $A$ to $B$ is the relation $\hat{\rho}$ from $B$ to $A$ defined by

$$
\hat{\rho} \stackrel{\mathrm{def}}{=} \{(a, b) \space | \space (b, a) \in \rho \}.
$$




💡 Let $\rho$ be a relation from $A$ to $B$ and let $\sigma$ be a relation from $B$ to $C$. Then the *composition* of $\rho$ and $\sigma$, denoted $\rho \circ \sigma$ (or also $\rho \sigma$), is the relation from $A$ to $C$ defined by

$$
\rho \circ \sigma \stackrel{\mathrm{def}}{=} \{(a, c) \space | \space \exists b \space ((a, b) \in \rho \land (b, c) \in \sigma )\}.
$$

The $n$-fold composition of a relation $\rho$ on a set $A$ with itself is denoted $\rho^n$.




📌 *The composition of relations is associative, i.e., we have $\rho \circ (\sigma \circ \phi) = (\rho \circ \sigma) \circ \phi$.*




📌 *Let $\rho$ be a relation from $A$ to $B$ and let  $\sigma$ be a relation from $B$ to $C$. Then the inverse $\widehat{\rho \sigma}$ of $\rho \sigma$ is the relation $\hat{\sigma} \hat{\rho}$.*




💡 A relation $\rho$ on a set $A$ is called *reflexive* if

$$
a \space \rho \space a
$$

is true for all $a \in A$, i.e., if

$$
\text{id} \sube \rho.
$$




💡 A relation $\rho$ on a set $A$ is called *irreflexive* if $a \space \cancel \rho \space a$ for all $a \in A$, i.e., if $\rho \cap \text{id} = \varnothing$.




💡 A relation $\rho$ on a set $A$ is called *symmetric* if

$$
a \space \rho \space b \iff b \space \rho \space a
$$

is true for all $a, b \in A$, i.e., if

$$
\rho = \hat{\rho}.
$$




💡 A relation $\rho$ on a set $A$ is called *antisymmetric* if

$$
a \space \rho \space b \land b \space \rho \space a \implies a = b
$$

is true for all $a, b \in A$, i.e., if

$$
\rho \cap \hat{\rho} \sube \text{id}.
$$




💡 A relation $\rho$ on a set $A$ is called *transitive* if

$$
a \space \rho \space b \land b \space \rho \space c \implies a \space \rho \space c
$$

is true for all $a, b, c \in A$.




📌 *A relation $\rho$ is transitive if and only if $\rho^2 \sube \rho$.*




💡 The *transitive closure of a relation $\rho$ on a set $A$, denoted $\rho^*$, is*

$$
\rho^* = \bigcup_{n \in \mathbb{N} \setminus \{0 \}} \rho^n.
$$



# Equivalence Relations


💡 An *equivalence relation* is a relation on a set $A$ that is reflexive, symmetric and transitive.




💡 For an equivalence relation $\theta$ on a set $A$ and for $a \in A$, the set of elements of $A$ that are equivalent to $a$ is called the *equivalence class of $a$* and is denoted as $[a]_\theta$:

$$
[a]_\theta \stackrel{\mathrm{def}}{=} \{b \in A \space | \space b \space \theta \space a \}.
$$




📌 *The intersection of two equivalence relations is an equivalence relation.*




💡 A *partition* of a set $A$ is a set of mutually disjoint subsets of $A$ that cover $A$, i.e., a set $\{S_i \space | \space i \in \mathcal{I} \}$ of sets $S_i$ (for some index set $\mathcal{I}$) satisfying

$$
S_i \cap S_j = \varnothing \space \text{for} \space i \neq j \space \text{and} \space \bigcup_{i \in \mathcal{I}} S_i = A.
$$




💡 The set of equivalence classes of an equivalence relation $\theta$, denoted by

$$
A / \theta \stackrel{\mathrm{def}}{=} \{[a]_\theta \space | \space a \in A\},
$$

is called the quotient set of $A$ by $\theta$, or simply $A$ modulo $\theta$, or $A \text{ mod } \theta$.




📖 *The set $A / \theta$ of equivalence classes of an equivalence relation $\theta$ on $A$ is a partition of $A$.*



# Partial Order Relations


💡 A *partial order* (or simply an *order relation*) on a set $A$ is a relation that is reflexive, antisymmetric, and transitive. A set $A$ together with a partial order $\preceq$ on $A$ is called a *partially ordered set* (or simply *poset*) and is denoted as $(A; \preceq)$.




💡 For a poset $(A; \preceq)$, two elements $a$ and $b$ are called *comparable* if $a \preceq b$  or $b \preceq a$; otherwise they are called *incomparable.*




💡 If any two elements of a poset $(A; \preceq)$ are comparable, then $A$ is called *totally ordered* (or *linearly ordered*) by $\preceq$.




💡 In a poset $(A; \preceq)$ an element $b$ is said to *cover* an element $a$ if $a \prec b$ and there exists no $c$ with $a \prec c$ and $c \prec b$ (i.e., between $a$ and $b$).




💡 The *Hasse diagram* of a (finite) poset $(A; \preceq)$ is the directed graph whose vertices are labeled with the elements of $A$ and where there is an edge from $a$ to $b$ if and only if $b$ covers $a$.




💡 For given posets $(A; \preceq)$ and $(B; \sqsubseteq)$, their direct product, denoted $(A; \preceq) \times (B; \sqsubseteq)$, is the set $A \times B$ with the relation $\leq$ (on $A \times B$) defined by

$$
(a_1, b_1) \leq (a_2, b_2) \stackrel{\mathrm{def}}{\iff} a_1 \preceq a_2 \land b_1 \sqsubseteq b_2. 
$$




📖 $*(A;\preceq) \times (B;\sqsubseteq)$ is a partial order relation.*




📖 *For given posets $(A;\preceq)$ and $(B; \sqsubseteq)$, the relation $\leq_\text{lex}$ defined on $A \times B$ by*

$$
(a_1, b_1) \leq_\text{lex} (a_2, b_2) \stackrel{\mathrm{def}}{\iff} a_1 \prec a_2 \lor (a_1 = a_2 \land b_1 \sqsubseteq b_2) 
$$

*is a partial order relation.*




💡 The relation $\leq_\text{lex}$ is the so-called *lexicographic order* of pairs, usually considered when both posets are identical. The lexicographic order $\leq_\text{lex}$ is useful because if both $(A; \preceq)$ and $(B;\sqsubseteq)$ are totally ordered (eq. the alphabetical order of the letters), then so is the lexicographic order on $A \times B$.




💡 Let $(A; \preceq)$ be a poset, and let $S \sube A$ be some subset of A. Then

1. $a \in A$ is a *minimal (maximal) element* of $A$ if there exists no $b \in A$ with $b \prec a$ ($b \succ a$).
2. $a \in A$ is the *least (greatest) element* of $A$ if $a \preceq b$ ($a \succeq b$) for all $b \in A$.
3. $a \in A$ is a *lower (upper) bound* of $S$ if $a \preceq b$ ($a \succeq b$) for all $b \in S$.
4. $a \in A$ is the *greatest lower bound (least upper bound)* of $S$ if $a$ is the greatest (least) element of the set of all lower (upper) bounds of $S$.



💡 A poset $(A; \preceq)$ is *well-ordered* if it is totally ordered and if every non-empty subset of $A$ has a least element.




💡 Let $(A; \preceq)$ be a poset. If $a$ and $b$ (i.e., the set $\{a, b \} \sube A$) have a greatest lower bound, then it is called the *meet* of $a$ and $b$, often denoted as  $a \land b$.
If $a$ and $b$ have a least upper bound, then it is called the *join* of $a$ and $b$, often denoted $a \lor b$.




💡 A poset $(A; \preceq)$ in which every pair of elements has a meet and a join is called a *lattice*.



# Functions


💡 A *function* $f : A \longrightarrow B$ from a *domain* $A$ to a *codomain* $B$ is a relation from $A$ to $B$ with the special properties (using the relation notation $a \space f \space b$):

1. $\forall a \in A \space \exists b \in B \space a \space f \space b$ ($f$ is totally defined)
2. $\forall a \in A \space \forall b, b' \in B \space (a \space f \space b \land a \space f \space b' \rightarrow b = b')$ ($f$ is well-defined).



💡 The set of all functions $A \longrightarrow B$ is denoted as $B^A$.




💡 A *partial function* $A \longrightarrow B$ is a relation from $A$ to $B$ such that condition 2. above holds.




💡 For a function $f : A \longrightarrow B$ and a subset $S$ of $A$, the *image* of $S$ under $f$, denoted $f(S)$, is the set

$$
f(S) \stackrel{\mathrm{def}}{=} \{f(a) \space | \space a \in S \}.
$$




💡 The subset $f(A)$ of $B$ is called the *image* (or *range*) of $f$ and is also denoted $\text{Im}(f)$.




💡 For a subset $T$ of $B$, the *preimage* of $T$, denoted $f^{-1}(T)$, is the set of values in $A$ that map into $T$:

$$
f^{-1}(T) \stackrel{\mathrm{def}}{=} \{a \in A \space | \space f(a) \in T \}.
$$




💡 A function $f : A \longrightarrow B$ is called

1. *injective* (or *one-to-one* or an *injection*) if for $a \neq b$ we have $f(a) \neq f(b)$, i.e., no two distinct values are mapped to the same function value (there are no “collisions”).
2. *surjective* (or *onto*) if $f(A) = B$, i.e., if for every $b \in B, b = f(a)$ for some $a \in A$ (every value in the codomain is taken on for some argument).
3. *bijective* (or a *bijection*) if it is both injective or surjective.



💡 For a bijective function $f$, the *inverse relation* is called the inverse function of $f$, usually denoted as $f^{-1}$.




💡 A function between two finite sets of equal cardinality is injective if and only if it is surjective.




💡 The *composition* of a function $f : A \longrightarrow B$ and a function $g : B \longrightarrow C$, denoted by $g \circ f$ or simply $gf$, is defined by $(g \circ f )(a) = g(f(a))$.




📌 *Function composition is associative, i.e., $(h \circ g) \circ f = h \circ (g \circ f)$.*




💡 A function $f : X \longrightarrow X$ is *idempotent* if $f(x) = f(f(x))$ for all $x \in X$



# Countable and Uncountable Sets


💡 Countability of Sets:

1. Two sets $A$ amd $B$ are *equinumerous*, denoted $A \sim B$, if there exists a bijection $A \longrightarrow B$.
2. The set $B$ *dominates* the set $A$, denoted $A \preceq B$, if $A \sim C$ for some subset $C \sube B$ or, equivalently, if there exists an injective function $A \longrightarrow B$.
3. A set $A$ is called *countable* if $A \preceq \mathbb{N}$, and *uncountable* otherwise.



📌 *Transitivity:*

1. *The relation $\preceq$ is transitive: $A \preceq B \land B \preceq C \implies A \preceq C$.*
2. $A \sube B \implies A \preceq B$.



📖 *Bernstein-Schröder Theorem:*

$$
A \preceq B \land B \preceq A \implies A \sim B.
$$




📖 *A set $A$ is countable if and only if it is finite or if $A \sim \mathbb{N}$.*




📖 *The set $\{0, 1\}^* \stackrel{\mathrm{def}}{=} \{\epsilon, 0, 1, 00, 01, 10, 11, 000, 001,...\}$ of finite binary sequences is countable.*




📖 *The set $\mathbb{N} \times \mathbb{N}$ ($= \mathbb{N}^2$) of ordered pairs of natural numbers is countable.*




📎 *The Cartesian product $A \times B$ of two countable sets $A$ and $B$ is countable, i.e., $A \preceq \mathbb{N} \land B \preceq \mathbb{N}$.*




📎 *The rational numbers $\mathbb{Q}$ are countable.*




📖 *Let $A$ and $A_i$ for $i \in \mathbb{N}$ be countable sets.*

1. *For any $n \in \mathbb{N}$, the set $A^n$ of $n$-tuples over $A$ is countable.*
2. *The union $\bigcup_{i\in\mathbb{N}} A_i$ of a countable list $A_0, A_1, A_2,...$ of countable sets is countable.*
3. *The set $A^*$ of finite sequences of elements from $A$ is countable.*



💡 Let $\{0, 1 \}^\infty$ denote the set of semi-infinite binary sequences.




📖 *The set $\{0, 1 \}^\infty$ is uncountable.*




💡 A function $f : \mathbb{N} \longrightarrow \{0, 1 \}$ is called *computable* if there is a program that, for every $n \in \mathbb{N}$, when given $n$ as input, outputs $f(n)$.




📎 *There are uncomputable functions $\mathbb{N} \longrightarrow \{0, 1 \}$.*


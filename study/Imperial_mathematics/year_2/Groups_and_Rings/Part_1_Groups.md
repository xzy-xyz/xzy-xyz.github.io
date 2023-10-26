---
title: Part I Groups
layout: simple
---

$$\gdef\R{\mathbb{R}}$$
$$\gdef\C{\mathbb{C}}$$
$$\gdef\Z{\mathbb{Z}}$$ 
$$\gdef\N{\mathbb{N}}$$
$$\gdef\Q{\mathbb{Q}}$$
$$\gdef\F{\mathcal{F}}$$
$$\gdef\iso{\overset{\sim}{=}}$$
$$\gdef\ke{\operatorname{Ker}}$$
$$\gdef\im{\operatorname{Im}}$$

#### *Based on the notes and lectures by [Professor Alexei Skorobogatov](https://www.ma.ic.ac.uk/~anskor/)*

> For the following we assume that $$G$$ and $$H$$ are groups, $$f$$ is a function, $$f: G \rightarrow H$$ and $$e$$ is the unit element in a group.

## 1. Homomorphisms and normal subgroups

### 1.1 Homomorphisms, isomorphisms and automorphisms

#### Definition 1.1 (Homomorphism)

A function $$f: G \rightarrow H$$ is called a **homomorphism** if for any $$a, b \in G$$ we have $$f(a b)=f(a) f(b)$$.

#### Proposition 1.2 (Homorphism preserves identity and inverses)

If we $$e_G$$ to denote the unit element of $$G$$ and $$e_H$$ to denote the unit element of $$H$$ and assume $$f: G \rightarrow H$$ is a homomorphism, then $$f(e_G)=e_H$$.

For any $$g \in G$$ the image of the inverse $$g^{-1}$$ is $$f(g^{-1})=f(g)^{-1}$$.

**Proof**:

$$f$$ is a homomorphism, we have:

$$
f(e_G)=f(e_G e_G)=f(e_G) f(e_G)
$$

If we multiply both sides by $$f(e_G)^{-1}$$ on the right, then we get

$$
f(e_G)=e_H
$$

By the axioms of groups, for any $$g \in G$$, we have:

$$
g^{-1} \in G \text{ and } g g^{-1}=e_G
$$

Since $$f$$ is a homomorphism, we have:

$$
f(e_G) = f(g g^{-1}) = f(g) f(g^{-1}) = e_H
$$

Since $$f(g) \in H$$, the inverse of $$f(g)$$ is $$f(g)^{-1}$$ is unique. Therefore, we have:

$$
f(g^{-1}) = f(g)^{-1}
$$

#### Examples

1. Let $$Mat(n,\R)$$ be the group of $$n\times n$$ matrices with real entries with the operation of matrix addtion. The trace $$tr: Mat(n,\R) \rightarrow \R$$ is a homomorphism.

    **Proof**:

    Let $$A, B \in Mat(n,\R)$$, then we have:

    $$
    tr(A + B) = \sum_{i=1}^n (a_{ii} + b_{ii}) = \sum_{i=1}^n a_{ii} + \sum_{i=1}^n b_{ii} = tr(A) + tr(B)
    $$

2. (1) Let $$\mathrm{GL}(n, \mathbb{R})$$ be the group of invertible $$n \times n$$-matrices with real entries with respect to multiplication of matrices. The determinant det: $$\operatorname{GL}(n, \mathbb{R}) \rightarrow \mathbb{R}^{\times}$$is a homomorphism to the multiplicative group $$\mathbb{R}^{\times}=\mathbb{R} \backslash\{0\}$$.

    **Proof**:

    Let $$A, B \in GL(n, \R)$$, then we have:

    $$
    det(AB) = det(A) det(B)
    $$

3. Let $$S_n$$ be the symmetric group of permutations of $$\{1,2,...,n\}$$. Then the sigh of a permuation $$sgn: S_n \rightarrow \{\pm 1\}$$ is a homomorphism to a cyclic group of order 2.

    **Proof**:

    We could regard $$\{\pm 1\}$$ as a cyclic group of order 2 with respect to multiplication, i.e. $$\{e^0 ,e^{\pi}\}$$, where $$e^0 = 1$$ and $$e^{\pi} = -1$$.

    Let $$\sigma, \tau \in S_n$$, then we have:

    $$
    sgn(\sigma \tau) = \begin{cases}
        1 & \text{if } \sigma \tau \text{ are both even or both odd} \\
        -1 & \text{if one of } \sigma \tau \text{ is even and the other is odd} 
    \end{cases}
    $$

    For $$sgn(\sigma) sgn(\tau)$$, we have:

    $$
    sgn(\sigma) sgn(\tau) = \begin{cases}
        1 & \text{if } \sigma \text{ and } \tau \text{ are both even or both odd} \\
        -1 & \text{if one of } \sigma \text{ is even and the other is odd}
    \end{cases}
    $$
    
#### Proposition 1.3 (Composition of homomorphisms)

If $$f: G \to H$$ and $$g: H \to K$$ are homomorphisms, then the compostion $$g \circ f: G \to K$$ is also a homomorphism.

**Proof**:

Let $$a, b \in G$$, since $$f$$ is a homomorphism, we have:

$$
f(a b) = f(a) f(b)
$$

Since $$g$$ is a homomorphism, we have:

$$
g(f(a b)) = g(f(a) f(b)) = g(f(a)) g(f(b))
$$

Therefore, we have:

$$
g \circ f(a b) = (g \circ f)(a) (g \circ f)(b)
$$

#### Definition 1.4 (Isomorphism)

A function $$f: G \rightarrow H$$ is called an **isomorphism** if it is a homomorphism and a bijection.

and if $$f$$ is a isomorphism, we write

$$
f: G \overset{\sim}{\rightarrow} H
$$

if $$G$$ and $$H$$ are isomorphic groups, we write

$$
G \overset{\sim}{=} H
$$

##### Remark

The identify map $$id_G: G \rightarrow G$$ is clearly an isomorphism.

#### Proposition 1.5 (Inverse of an isomorphism)

If $$f: G \overset{\sim}{\rightarrow} H$$ is an isomorphism, since it is a bijection, then there exists a inverse map $$f^{-1}: H \rightarrow G$$, defined by $$f^{-1}(y) = x$$ if and only if $$f(x) = y$$, which is also an isomorphism and $$f^{-1} \circ f = id_G$$ and $$f \circ f^{-1} = id_H$$.

**Proof**:

1. Assume $$h_1, h_2 \in H$$ be arbitrary. Since $$f$$ is a bijection, there exists $$g_1, g_2 \in G$$ such that $$f(g_1) = h_1$$ and $$f(g_2) = h_2$$. Since $$f$$ is a homomorphism, we have:

    $$
    h_1h_2 = f(g_1)f(g_2)
    $$

    Then, we have

    $$
    f^{-1}(h_1h_2) = f^{-1}(f(g_1)f(g_2)) = f^{-1}(f(g_1g_2)) = g_1g_2 = f^{-1}(h_1)f^{-1}(h_2)
    $$

    Therefore, $$f^{-1}$$ is a homomorphism. Since $$f$$ is a bijection, then its inverse $$f^{-1}$$ is also a bijection. Therefore, $$f^{-1}$$ is an isomorphism.

2. Since $$f$$ is a bijection, then for any $$g \in G$$, there exists $$h \in H$$ such that $$f(g) = h$$. Therefore, we have:

    $$
    f^{-1}(f(g)) = f^{-1}(h) = g
    $$

    Therefore, we have $$f^{-1} \circ f = id_G$$.

    It is the same for $$f \circ f^{-1} = id_H$$.

#### Remark

1. Isomorphism is an equivalence relation on the set of all groups.

   **Proof**:

   1. (Reflexive) Let $$G$$ be a group, then the identity map $$id_G: G \rightarrow G$$ is an isomorphism, therefore, $$G \overset{\sim}{=} G$$.

   2. (Symmetric) Let $$G \overset{\sim}{=} H$$, then there exists an isomorphism $$f: G \rightarrow H$$. Since $$f$$ is a bijection, then its inverse $$f^{-1}: H \rightarrow G$$ is also a bijection. Since $$f$$ is a homomorphism, then $$f^{-1}$$ is also a homomorphism. Therefore, $$f^{-1}$$ is an isomorphism and $$H \overset{\sim}{=} G$$.

   3. (Transitive) Let $$G \overset{\sim}{=} H$$ and $$H \overset{\sim}{=} K$$, then there exists isomorphisms $$f: G \rightarrow H$$ and $$g: H \rightarrow K$$. Since $$f$$ and $$g$$ are bijections, then the composition $$g \circ f: G \rightarrow K$$ is also a bijection. Since $$f$$ and $$g$$ are homomorphisms, then the composition $$g \circ f$$ is also a homomorphism. Therefore, $$g \circ f$$ is an isomorphism and $$G \overset{\sim}{=} K$$.

2. Isomorphic groups means we could not distinguish them by their algebraic properties.

    Example:

    A cyclic group of order $$nm$$ 

    $$
    C_n = \{a^0, a^1, a^2, ..., a^{n-1}\}
    $$

    and the group of residues modulo $$n$$ denoted by 

    $$
    \Z \backslash n = \{0, 1, 2, ..., n-1\}
    $$

    with the group law written additively, that is, $$a + b$$ is the remainder of $$a + b$$ modulo $$n$$. Therefore, the function

    $$
    f: \Z\backslash n \rightarrow C_n
    $$

    where $$f(i) = a^i$$ is an isomorphism.

#### Definition 1.6 (Automorphism)

Let $$G$$ be a group. An isomorphism $$f: G \stackrel{\sim}{\longrightarrow} G$$ is called an **automorphism** of $$G$$.

#### Examples

1. Let $$G$$ be a group. The identity map $$id_G: G \rightarrow G$$ is an automorphism.

2. The self-map $$G \to G$$ that sends $$g$$ to $$g^{-1}$$ is an automorphism if and only if $$G$$ is Abelian.

    **Proof**:

    $$\Rightarrow$$: Assume $$f: G \to G$$ with $$f(g) = g^{-1}$$ is an an automorphism and let $$a ,b \in G$$ be arbitrary then

    $$
    f(a b) = (a b)^{-1} = b^{-1} a^{-1} = f(b) f(a)
    $$

    Since $$f$$ is an automorphism, then $$f$$ is a homomorphism. 

    $$
    f(a b) = f(a) f(b)
    $$

    Therefore, we have $$f(a) f(b) = f(b) f(a)$$ since $$f$$ is an bijection,its image is the whole group $$G$$. Therefore, $$G$$ is abelian.

    $$\Leftarrow$$: Assume $$G$$ is Abelian and $$f: G \to G$$ with $$f(g) = g^{-1}$$. We need to show that $$f$$ is a homomorphism and a bijection.

    1. (Homomorphism) Let $$a, b \in G$$ be arbitrary, then we have:

        $$
        f(a b) = (a b)^{-1} = b^{-1} a^{-1} = f(b) f(a) = f(a) f(b)
        $$

        since $$G$$ is Abelian.

    2. (Bijection) 
        1. (Injective) The uniquness of the inverse of an element in a group implies that $$f$$ is injective.
        
        2. (Surjective) By the axioms of groups, for any element in $$G$$, there exists an inverse. Therefore, $$f$$ is surjective.


#### Proposition 1.7 (The group of automorphisms on a group)

Let $$G$$ be a group, then the set of all automorphisms of $$G$$ forms a group with the unit element $$id_G$$ and the operation of composition. The groups is denoted by 

$$
Aut(G)
$$

Thus, for any group $$G$$, we associated another group $$Aut(G)$$.

**Proof**:

1. (Closure) Let $$f, g \in Aut(G)$$, then $$f \circ g$$ is also an automorphism.(From the following proposition)

2. (Associativity) Since composition of functions is associative, then the composition of automorphisms is also associative.

3. (Unit element) The identity map $$id_G$$ is an automorphism.

4. (Inverse) Let $$f \in Aut(G)$$, then $$f^{-1}$$ is also an automorphism. (From the following proposition)

Therefore, the set of all automorphisms of $$G$$ forms a group with the unit element $$id_G$$ and the operation of composition.

#### Examples

1. $$Aut(\Z) = \{f(x) | f(x) = x + n, x\in \Z, n \in \Z\}$$

2. $$Aut(\Z \backslash n) = \{f(s)| f(s) = \{ nk + a | a \in (0, n), k \in \Z \} , s \in \Z \backslash n\}$$

#### Definition 1.8 (Conjugation)

Let $$G$$ be a group and take $$g \in G$$. The function $$G \to G$$ defined by $$x \mapsto g x g^{-1}$$ is called **conjugation** by $$g$$.

#### Proposition 1.9 (Conjugation is an automorphism)

Let $$G$$ be a group and take $$g \in G$$. The function $$G \to G$$ defined by $$x \mapsto g x g^{-1}$$ is an automorphism.

**Proof**:

1. (Homomorphism) Let $$x, y \in G$$ be arbitrary and $$f$$ denote the conjugation by $$g$$, then we have:

    $$
    f(xy) = g(xy)g^{-1} = gx(g^{-1} g) y g^{-1} = (gxg^{-1})(gyg^{-1}) = f(x)f(y)
    $$

2. (Bijection) 
   1. (Injective) Let $$x, y \in G$$ be arbitrary and $$f$$ denote the conjugation by $$g$$, then we have:

        $$
        f(x) = f(y) \Rightarrow gxg^{-1} = gyg^{-1} \Rightarrow x = y
        $$

        Therefore, $$f$$ is injective.
    
    2. (Surjective) Let $$x \in G$$ be arbitrary and $$f$$ denote the conjugation by $$g$$, then we have:

        $$
        f(g^{-1} x g) = g(g^{-1} x g) g^{-1} = x
        $$

        Therefore, $$f$$ is surjective.

### 1.2. Normal subgroups, quotient groups and the isomorphism theorem

#### Definition 1.10 (Stable under conjugation)

Let $$G$$ be a group and $$H$$ be a subgroup of $$G$$. We say that $$H$$ is **stable under conjugation** if for any $$g \in G$$ we have $$g h g^{-1} \in H$$ for any $$h \in H$$.

#### Definition 1.11 (Normal subgroup)

Let $$G$$ be a group. A subgroup $$S \subset G$$ is called **normal** if it is stable under the conjugation by any element of $$G$$.


#### Definition 1.12 (Image and kernel of a homomorphism)

To a homomorphism $$f: G \rightarrow H$$ we associate its image

$$
\operatorname{Im}(f)=f(G)=\{f(x) \mid x \in G\} \subset H
$$

and its kernel

$$
\operatorname{Ker}(f)=\left\{x \in G \mid f(x)=e_{H}\right\}
$$

#### Lemma 1.13 (A homomorphism is injective if and only if its kernel is trivial)

Let $$f: G \rightarrow H$$ be a homomorphism. Then $$f$$ is an injective if and only if $$\operatorname{Ker}(f)=\{e_{G}\}$$.

**Proof**:

$$\Rightarrow$$: Since $$f$$ is homomorphism, then $$f(e_G) = e_H$$, so $$e_G \in \ke(f)$$. Since $$f$$ is injective, then $$|\ke(f)| \leq 1$$. Therefore, $$\ke(f) = \{e_G\}$$.

$$\Leftarrow$$: Assume $$\ke(f) = \{e_G\}$$ and $$f(g_1) = f(g_2)$$, then we have:

$$
f(g_1) = f(g_2) \Rightarrow f(g_1) f(g_2)^{-1} = e_H \Rightarrow f(g_1 g_2^{-1}) = e_H \Rightarrow g_1 g_2^{-1} \in \ke(f) \Rightarrow g_1 g_2^{-1} = e_G \Rightarrow g_1 = g_2
$$


#### Proposition 1.14 (Kernel of a homomorphism is a normal subgroup)

Let $$f: G \rightarrow H$$ be a homomorphism of a group. Then $$\operatorname{Im}(f)$$ is a subgroup of $$H$$ and $$\operatorname{Ker}(f)$$ is a subgroup of $$G$$. Moreover, $$\operatorname{Ker}(f)$$ is a normal subgroup of $$G$$.

**Proof**:

1. (Image is subgroup) To prove this, we check the defintion of subgroups.  

    1. (Identity) Since $$f$$ is a homomorphism, then $$f(e_G) = e_H$$. Therefore, $$e_H \in \operatorname{Im}(f)$$.

    2. (Closure) Let $$h_1, h_2 \in \operatorname{Im}(f)$$ be arbitrary, then there exists $$g_1, g_2 \in G$$ such that $$f(g_1) = h_1$$ and $$f(g_2) = h_2$$. Since $$f$$ is a homomorphism, then we have:

        $$
        f(g_1 g_2) = f(g_1) f(g_2) = h_1 h_2
        $$

        Therefore, $$h_1 h_2 \in \operatorname{Im}(f)$$.

    3. (Inverse) Let $$h \in \operatorname{Im}(f)$$ be arbitrary, then there exists $$g \in G$$ such that $$f(g) = h$$. Since $$f$$ is a homomorphism, then we have:

        $$
        f(g^{-1}) = f(g)^{-1} = h^{-1}
        $$

        Therefore, $$h^{-1} \in \operatorname{Im}(f)$$.

2. (Kernel is subgroup)

    1. (Identity) Since $$f$$ is a homomorphism, then $$f(e_G) = e_H$$. Therefore, $$e_G \in \operatorname{Ker}(f)$$.

    2. (Closure) Let $$g_1, g_2 \in \operatorname{Ker}(f)$$ be arbitrary, then we have:

        $$
        f(g_1 g_2) = f(g_1) f(g_2) = e_H e_H = e_H
        $$

        Therefore, $$g_1 g_2 \in \operatorname{Ker}(f)$$.

    3. (Inverse) Let $$g \in \operatorname{Ker}(f)$$ be arbitrary, then we have:

        $$
        f(g^{-1}) = f(g)^{-1} = e_H^{-1} = e_H
        $$

        Therefore, $$g^{-1} \in \operatorname{Ker}(f)$$.

3. (Kernal is normal)

    Assume $$x \in \ke(f)$$ be arbitrary and $$g \in G$$ be any element, then we have:

    $$
    f(g x g^{-1}) = f(g) f(x) f(g^{-1}) = f(g) e_H f(g^{-1}) = f(g) f(g^{-1}) = f(g g^{-1}) = f(e_G) = e_H
    $$

    then $$g x g^{-1} \in \ke(f)$$. Therefore, $$\ke(f)$$ is a normal subgroup of $$G$$.

#### Definition 1.15 (Simple group)

A group $$G$$ is called **simple** if it has no normal subgroups other than $$\{e\}$$ and $$G$$.

#### Examples

1. If $$p$$ is a prime number, then the cyclic group $$C_p$$ is a simple group.

    **Proof**:

    Assume $$H$$ is a normal subgroup of $$C_p$$, then $$H$$ is a subgroup of $$C_p$$ and $$H \neq \{e\}$$ and $$H \neq C_p$$. Since $$C_p$$ is a cyclic group, then $$H = \langle a^k \rangle$$ for some $$k \in \{1, 2, ..., p-1\}$$. Since $$H$$ is a normal subgroup of $$C_p$$, then for any $$g \in C_p$$, we have $$g H g^{-1} = H$$. Therefore, we have:

    $$
    g H g^{-1} = \{g h g^{-1} | h \in H\} = \{g a^k g^{-1} | k \in \{1, 2, ..., p-1\}\} = \{a^k | k \in \{1, 2, ..., p-1\}\} = H
    $$

    which is a contradiction. Therefore, $$C_p$$ is a simple group.

    Actually, there is a strong result that every cyclic group with prime order has no subgroup other than $$\{e\}$$ and itself.

    **Proof**:

    Assume $$H$$ is a subgroup of $$C_p$$ and $$H \neq \{e\}$$ and $$H \neq C_p$$. Since $$C_p$$ is a cyclic group, then $$H = \langle a^k \rangle$$ for some $$k \in \{1, 2, ..., p\}$$. Since $$H \neq \{e\}$$, then $$k \neq 1$$. Since $$H \neq C_p$$, then $$k \neq p$$. Therefore, $$k$$ is a proper divisor of $$p$$. Since $$p$$ is a prime number, then $$p$$ has no proper divisors. Therefore, $$H$$ does not exist.


2. If $$G$$ is Abelian, then any subgroup of $$G$$ is simple.

   **Proof**:

   Assume $$H$$ is a subgroup of $$G$$ and let $$h \in H$$ and $$g \in G$$ be arbitrary. Since $$G$$ is Abelian, then we have:

   $$
   g h g^{-1} = g g^{-1} h = h \in H
    $$

    Therefore, $$H$$ is a normal subgroup of $$G$$. Since $$G$$ is Abelian, then $$H$$ is a subgroup of $$G$$ and $$H \neq \{e\}$$ and $$H \neq G$$. Therefore, $$H$$ is a simple group.

3. Consider the symmetric groups $$S_3$$, and let $$G =\{e, (1 2) \}\subset S_3$$. It is clearly that $$G$$ is a subgroup of $$S_3$$. But $$G$$ is not a normal subgroup of $$G$$.

$$
(13) (12) (13) = (13) (12) (13) = (23) \notin G
$$

#### Lemma 1.16 (Left coset and right coset equal means normal subgroup)

If $$H \subset G$$ is a subgroup of $$G$$, and $$g H = H g$$ for every $$g \in G$$, then $$H$$ is a normal subgroup of $$G$$.

**Proof**:

Let $$h \in H$$ and $$g \in G$$ be arbitrary, since the left coset and right coset are equal, then we have:

$$
g h = h g
$$

We multiply both sides by $$g^{-1}$$ on the right, then we have:

$$
g h g^{-1} = h
$$

Therefore, $$H$$ is a normal subgroup of $$G$$.

#### Definition 1.17 (The product of left cosets of a normal subgroup)

Assume $$N$$ is a normal subgroup of $$G$$ and let $$g_1, g_2 \in G$$, then we define a group structure on the set $$G / N$$ of left cosets of $$N$$ in $$G$$ by setting

$$
(g_1N)(g_2N) = \{ab| a \in g_1N, b\in g_2 N\}
$$

which is the set of all the products of an element from $$g_1N$$ and an element from $$g_2N$$.

#### Lemma 1.18

Let $$N$$ be a normal subgroup of $$G$$. For any $$g_{1}, g_{2} \in G$$ we have

$$
(g_1N)(g_2 N) = g_1g_2N
$$

**Proof**:

Let $$x, y \in N$$ be arbitrary, then $$(g_1 x)(g_2 y) = g_1(g_2 g_2^{-1}xg_2)y$$. Since $$N$$ is a normal subgroup of $$G$$, then $$g_2^{-1}xg_2 \in N$$. Therefore, we could find a $$z \in N$$ such that $$g_2^{-1}xg_2 = z$$. Therefore, we have:

$$
(g_1x) (g_2y) = g_1(g_2 g_2^{-1}xg_2)y = g_1 g_2 z y
$$

If we set $$y = e_G$$, then the proof is done.

#### Definition 1.19 (Quotient group)

Let $$N$$ be a normal subgroup of $$G$$, then the set of all the left cosets of $$N$$ in $$G$$ is denoted by $$G / N = \{gN | g \in G\}$$ and is called the **quotient group** of $$G$$ by $$N$$. The group law on $$G / N$$ is given by $$(g_1 N)(g_2 N) = g_1 g_2 N$$.

We show that the quotient group is well-defined.

1. (Closure) Let $$g_1, g_2 \in G$$ be arbitrary, then we have:

    $$
    (g_1 N)(g_2 N) = g_1 g_2 N
    $$

    Since $$N$$ is a normal subgroup of $$G$$, then $$g_1 g_2 \in G$$. Therefore, $$g_1 g_2 N \in G / N$$.

2. (Associativity) Since $$G$$ is a group, then the product of two elements in $$G$$ is associative. Therefore, the product of two elements in $$G / N$$ is associative.

3. (Unit element) Since $$N$$ is a normal subgroup of $$G$$, then $$e_G \in N$$. Therefore, $$e_G N = N$$ is the unit element of $$G / N$$.

4. (Inverse) Let $$gN \in G/N$$ be arbitrary, since $$N$$ is a normal subgroup. The inverse of $$gN$$ is $$g^{-1}N$$ .i.e.

$$
(gN)(g^{-1}N) = g g^{-1} N = e_G N
$$


#### Proposition 1.20

Let $$N$$ be a normal subgroup of $$G$$. The function $$f: G \rightarrow G / N$$ given by $$g \mapsto g N$$ is a surjective homomorphism with kernel $$\operatorname{Ker}(f)=N$$.

**Proof**:

1. (Homomorphism) Let $$g_1, g_2 \in G$$ be arbitrary, then we have:

    $$
    f(g_1 g_2) = g_1 g_2 N = (g_1 N)(g_2 N) = f(g_1) f(g_2)
    $$

    Therefore, $$f$$ is a homomorphism.

2. The surjectivity of $$f$$ is obvious.

3. (Kernel) Let $$g \in \ke(f)$$ be arbitrary, then we have:

    $$
    f(g) = g N = N \Rightarrow g \in N
    $$

    Therefore, $$\ke(f) = N$$.

#### Theorem 1.21 (First isomorphism theorem)

Let $$f: G \rightarrow H$$ be a homomorphism. The map $$\phi:g \operatorname{Ker}(f) \mapsto f(g)$$ is an isomorphism of groups

$$
G / \operatorname{Ker}(f) \stackrel{\sim}{\longrightarrow} f(G) .
$$

and 

$$
G/ \ke(f) \iso \im(f)
$$

**Proof**:

Since $$\ke(f)$$ is a normal subgroup, then $$g\ke(f)$$ is a group.


Next, we check $$\phi$$ is isomorphism.

1. (Homomorphism) Let $$g_1 \ke(f)$$ and $$g_2\ke(f) \in G/\ke(f)$$ be arbitrary. Then we

    $$
    \phi(g_1\ke(f)g_2\ke(f)) = \phi(g_1g_2\ke(f)) = f(g_1g_2) = f(g_1)f(g_2) = \phi(g_1\ke(f))\phi(g_2\ke(f))
    $$

2. (Bijectivity)

    1. (Surjective) The surjectivity of $$\phi$$ is obvious.

    2. (Injective) It we could show that the $$\ke(\phi) = \{e_{G/\ke(f)}\}$$, then $$\phi$$ is injective.

        Let $$g \in \ke(\phi)$$ be arbitrary, then we have:

        $$
        \phi(g) = f(g) = e_H
        $$

        Therefore, $$g \in \ke(f)$$, then $$g\ke(f) = \ke(f)$$. Therefore, $$\ke(\phi) = \{e_G \ke(f)\}$$.


#### Remark

Assume $$f: G \rightarrow H$$ is a homomorphism, then we have:

- (Homorphism preserves subgroups of images and preimages)
  
  - If $$A \subset G$$ is a subgroup, then $$f(A) \subset H$$ is a subgroup.

    - Since the homomorphism preserves the group law. Therefore, $$f(A)$$ is closed under the group law.

  - If $$B \subset H$$ is a subgroup, then $$f^{-1}(B) \subset G$$ is a subgroup.
  
    -  (Unit element)$$e_G \in f^{-1}(B)$$ since $$f(e_G) = e_H \in B$$.
    -  (Closed under inverse) If $$g \in f^{-1}(B)$$, then $$f(g) \in B$$. Since $$B$$ is a subgroup, then $$f(g)^{-1} \in B$$. We know that $$f^{-1}(g) = f(g^{-1})$$, then $$g^{-1} \in f^{-1}(B)$$.

- (Homomorphism preserves normal subgroups of preimages) If $$N \subset H$$ is a normal subgroup, then $$f^{-1}(N) \subset G$$ is a normal subgroup.

    - (Normal) Let $$x \in f^{-1}(B)$$ and $$g \in G$$ be arbitrary. Then,

        $$
        f(x) \in N
        $$

        Since $$N$$ is normal,

        $$
        f(g)f(x)f(g)^{-1} \in N \Longrightarrow f(gxg^{-1}) \in N \Longrightarrow gxg^{-1} \in f^{-1}(N) 
        $$

        Therefore, $$f^{-1}(N)$$ is a normal subgroup of $$G$$.

- The image of a normal subgroup of a homomorphism does not have to be normal subgroup. E.g.

    - $$G = S_3 \text{ and } A = S_2 \subset S_3$$. $$A$$ is not a normal subgroup of $$S_3$$ but $$A$$ is the normal subgroup of itself. Consider the identity homomorphism $$id: A \to G$$. Then $$id(A) = A$$ is not a normal subgroup of $$G$$.

    If $$f: G \to H$$ is a surjective homomorphism, then if $$A$$ is a normal subgroup of $$G$$, then $$f(A)$$ is a normal subgroup of $$H$$.

    **Proof**: 

    Since $$f$$ is surjective, then $$f(A) = H$$. We could have this:\

    $$
    f(g)f(A)f(g)^{-1} = f(gAg^{-1}) \in f(A)
    $$

    Therefore, $$f(A)$$ is a normal subgroup of $$H$$.

#### Proposition 1.22 (Correspondece theorem)

Let $$N$$ be a normal subgroup of $$G$$. Let $$f:G \to G/N$$ be the surjective homomorphism $$g \mapsto gN$$. Then f is a bijection:

$$
G_1 = \left\{\text{subgroups } S \subset G \text { that contain } N\right\} \stackrel{\stackrel{f}{\sim}}{\longrightarrow}\left\{\text{subgroups of } G / N\right\} = G_2
$$

Moreover, $$S$$ is normal in $$G$$ if and only if $$S/N$$ is normal in $$G/N$$.

**Proof**:

1. Since $$N$$ is a normal subgroup in $$G$$, in particular, $$N$$ is a subgroup of $$S$$. As $$N = \ke(f)$$, then $$S/N = f(S)$$ is a subgroup of $$G/N$$ by the first isomorphism theorem.  

2. To show there is a bijection, we need to show that there is a map which composition is the identity map from both sides of domain and codomain meaning that we need to find $$f^{-1}$$. We notice that $$S$$ is the disjoint union of the cosets $$gN, g\in S$$.

    $$
    S = \bigcup_{g \in S} gN \text{ (disjoin union)}
    $$

    - $$f^{-1} \circ f = id_{G_1}$$: Let $$S \in G_1$$ be a subgroup that contains $$N$$, then we have:

        $$
        f^{-1}(f(S)) = f^{-1}\left(f\left(\bigcup_{g \in S} gN\right)\right) = \bigcup_{g \in S} f\circ f^{-1}(gN) = \bigcup_{g \in S} gN = S
        $$

    - $$f \circ f^{-1} = id_{G_2}$$: Let $$H \in G_2$$ be arbitrary, then we have:

        $$
        f (f^{-1}(H)) = H
        $$

3. By previous remark, since $$f$$ is a surjective homomorphism, then $$S$$ is normal if and only if $$f(S)$$ is normal. Therefore, $$S$$ is normal in $$G$$ if and only if $$S/N$$ is normal in $$G/N$$.

### 1.3 Group-theoretic constructions

#### Definition 1.31 (Group of Inner automorphism)

The set of the conjugations by the elements of $$G$$ forms a subgroup of $$Aut(G)$$, called the **group of inner automorphisms** of $$G$$ and denoted by $$Inn(G)$$, it is also called conjugation group of $$G$$.

**Proof**: 

We show that the inner automorphisms form a subgroup of $$Aut(G)$$.

- (Closure) Let $$f_1, f_2 \in Inn(G)$$ and $$x \in G$$ be arbitrary, then we have:

    $$
    f_1 \circ f_2 (x) = f_1(f_2(x)) = f_1([x \to g_2 x g_2^{-1}]) = [x \mapsto g_1 g_2 x g_2^{-1} g_1^{-1}] =[x\mapsto (g_1 g_2) x (g_1 g_2)^{-1}]
    $$
    Therefore, $$f_1 \circ f_2 \in Inn(G)$$.

- (Identity) The identity map $$id_G$$ is an inner automorphism.

- (Inverse) Let $$f \in Inn(G)$$ be arbitrary, if $$f(x) = [x \mapsto g x g^{-1}]$$, then $$f^{-1}(x) = [x \mapsto g^{-1} x g] =[x \mapsto g^{-1}x(g^{-1})^{-1}]$$. Therefore, $$f^{-1} \in Inn(G)$$.

#### Lemma 1.32

Let $$G$$ be a group and $$Aut(G)$$ be the associated automorphism group. The map $$\phi: G \to Inn(G)$$ sending the element $$g$$ of $$G$$ to the conjugation by $$g$$ is a homomorphism. Moreover, $$\ke(\phi) = \{g \in G| gx = xg, \forall x \in G\}$$.

**Proof**:

1. (Homomorphism) We have to show that for any $$a, b \in G$$ the conjugation by $$a b$$ is the composition of the conjugation by $$a$$ and the conjugation by $$b$$.
   
   Let $$x \in G$$ be arbitrary.

    $$
    \phi(a b) = [x \mapsto (a b) x (a b)^{-1}] = [x \mapsto a (b x b^{-1}) a^{-1}] = [x \mapsto a x a^{-1}] \circ [x \mapsto b x b^{-1}] = \phi(a) \circ \phi(b)
    $$

2. (Kernel) Let $$x \in \ke(\phi)$$ and $$g \in G$$ be arbitrary, then we have:

    $$
    \phi(x) = [x \mapsto x] \Longrightarrow  gxg^{-1} = x \Longrightarrow gx = xg
    $$

    Therefore, $$\ke(\phi) = \{g \in G| gx = xg, \forall x \in G\}$$.

#### Definition 1.33 (Center of a group)

Let $$G$$ be a group. The **center** of $$G$$ is the set of elements of $$G$$ that commute with all elements of $$G$$:

$$
Z(G) = \ke(\phi) = \{g\in G| gxg^{-1}, \forall x\in G\}=\{g \in G| gx = xg, \forall x \in G\}
$$

where $$\phi: G \to Inn(G)$$.

#### Remark

1. $$Z(G)$$ is a normal subgroup of $$G$$ since it is the kernel of the homomorphism $$\phi: G \to Inn(G)$$.

2. The first isomomorphism theorem tells us that $$G/Z(G) \iso Inn(G)$$.

3. $$Z(G) = G$$ if and only if $$G$$ is Abelian.

#### Definition 1.34 (Communtator)

Let $$G$$ be a group. For $$a, b \in G$$ we define the **commutator** of $$a$$ and $$b$$ as

$$
[a, b] = a b a^{-1} b^{-1}
$$

#### Remark

1. $$[a, b] = e_G$$ if and only if $$a b = b a$$.

2. $$[a, b] = [b, a]^{-1}$$. 

#### Lemma 1.36 (The intersection of subgroups is a subgroup)

Let $$I$$ be a set and $$G$$ be a group. Suppose that for each $$i \in I$$ we are given a subgroup $$G_{i} \subset G$$. Then the intersection $$\bigcap_{i \in I} G_{i}$$ is a subgroup of $$G$$.

**Proof**:

1. (Identity) Since $$e_G \in G_i$$ for all $$i \in I$$, then $$e_G \in \bigcap_{i \in I} G_{i}$$.

2. (Closure under group operation) Let $$x, y \in \bigcap_{i \in I} G_{i}$$ be arbitrary, then $$x, y \in G_i$$ for all $$i \in I$$. Since $$G_i$$ is a subgroup of $$G$$, then $$x y \in G_i$$ for all $$i \in I$$. Therefore, $$x y \in \bigcap_{i \in I} G_{i}$$.

3. (Closure under inverse) Let $$x \in \bigcap_{i \in I} G_{i}$$ be arbitrary, then $$x \in G_i$$ for all $$i \in I$$. Since $$G_i$$ is a subgroup of $$G$$, then $$x^{-1} \in G_i$$ for all $$i \in I$$. Therefore, $$x^{-1} \in \bigcap_{i \in I} G_{i}$$.

#### Definition 1.37 (Generated subgroup)

Let $$G$$ be a group and $$S$$ be a subgroup of $$G$$. The intersection of all subgroups of $$G$$ that contains $$S$$ (which is a subgroup of $$G$$ by the previous lemma) is called the **subgroup generated by $$S$$**. If the subgroup is $$G$$ itself, we say that $$S$$ **generates** $$G$$.

#### Definition 1.38 (Commutator subgroup)

Let $$G$$ be a group. The subgroup of $$G$$ generated by all commutators of $$G$$ is called the **commutator subgroup** of $$G$$ and is denoted by $$[G, G]$$.

#### Remark

$$[G, G] = \{e_G\}$$ if and only if $$G$$ is Abelian.

#### Lemma 1.39 (The commutator subgroup is a normal subgroup and the quotient group of modulo the commutator subgroup is Abelian)

Let $$G$$ be a group. The commutator subgroup $$[G, G]$$ is a normal subgroup of $$G$$ and $$G / [G, G]$$ is Abelian.

**Proof**:


































  



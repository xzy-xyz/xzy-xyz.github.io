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

#### Based on the notes and lectures by [Professor Alexei Skorobogatov](https://www.ma.ic.ac.uk/~anskor/)

##### For the following we assume that $$G$$ and $$H$$ are groups, $$f$$ is a function, $$f: G \rightarrow H$$ and $$e$$ is the unit element in a group.

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
        1 & \text{if one of } \sigma \tau \text{ is even and the other is odd} 
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

#### Definition 1.12 (Simple group)

A group $$G$$ is called **simple** if it has no normal subgroups other than $$\{e\}$$ and $$G$$.










  



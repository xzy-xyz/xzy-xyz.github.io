---
title: Vector Calculus
layout: simple
---

$$\gdef\R{\mathbb{R}}$$
$$\gdef\C{\mathbb{C}}$$
$$\gdef\Z{\mathbb{Z}}$$ 
$$\gdef\N{\mathbb{N}}$$
$$\gdef\Q{\mathbb{Q}}$$
$$\gdef\F{\mathcal{F}}$$
$$\gdef\inner#1#2{\langle #1, #2 \rangle}$$
$$\gdef\norm#1{\left\| #1 \right\|}$$
$$\gdef\abs#1{\left| #1 \right|}$$
$$\gdef\set#1{\left\{ #1 \right\}}$$
$$\gdef\ve{\varepsilon}$$
$$\gdef\va{\mathbf{a}}$$
$$\gdef\vb{\mathbf{b}}$$
$$\gdef\vc{\mathbf{c}}$$

#### based on the notes and lectures of [Dr. Andrew Walton](https://www.ma.ic.ac.uk/~agw/)

## 1.1 Preliminarry ideas and some revision of vectors

### 1.1.1 The Einstein summation convention

Throughout these notes, we frequently use the Einstein summation convention. This convention is a shorthand for writing sums of the form

$$
a_{i} x_{i} \text { is shorthand for } \sum_{i=1}^{3} a_{i} x_{i}.
$$

### 1.1.2 The Kronecker delta

This is the quantity $$\delta_{i j}$$ and is defined such that

$$
\delta_{i j}= \begin{cases}1, & i=j \\ 0, & i \neq j\end{cases}
$$

#### Example

$$
\delta_{i j}a_j = \sum_{j=1}^{3}\delta_{i j}a_j = \delta_{i 1}a_1 + \delta_{i 2}a_2 + \delta_{i 3}a_3 = a_i.
$$

### 1.1.3 The permutation symbol

This is the quantity $$\varepsilon_{i j k}$$, defined as

$$
\varepsilon_{i j k}=\left\{\begin{array}{cc}
0, & \text { if any two of } i, j, k \text { are the same; } \\
1, & \text { if } i, j, k \text { is a cyclic permutation of } 1,2,3 \\
-1, & \text { if } i, j, k \text { is an acyclic permutation of } 1,2,3
\end{array}\right.
$$

#### Remark

We could show that the Kronecker delta and the permutation symbol are connected by the formala

$$
\varepsilon_{i j k} \varepsilon_{k l m}=\delta_{i l} \delta_{j m}-\delta_{i m} \delta_{j l} .
$$

sum over k.

**Proof**:

The quantities $$\delta_{i l}$$ and $$\varepsilon_{j k m}$$ are called **tensors**.

### 1.1.4 Vector product

We could define the vector product as a third vector, perpendicular to the first two vectors. It could be written in the form of a determinant:

$$
\mathbf{a} \times \mathbf{b}=\left|\begin{array}{ccc}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
a_{1} & a_{2} & a_{3} \\
b_{1} & b_{2} & b_{3}
\end{array}\right|
$$

#### Remark

If $$\va \times \vb = 0$$, then the two vectors are parallel and it is easy to see that 

$$
\va \times \vb = - \vb \times \va.
$$

by the properties of the determinant.

If we use the notation that we introduce before, we could write

$$
\begin{array}{r}
a_{2} b_{3}-a_{3} b_{2}=\ve_{123}a_2b_3 + \ve{132}a_3b_2 \\
\end{array}
$$

since $$\varepsilon_{123}=1, \varepsilon_{132}=-1$$, and $$\varepsilon_{1 i j}=0$$ for all other $$i$$ and $$j$$. In general we can write the $$i$$ th component of $$a \times b$$ as

$$
[a \times b]_{i}=
$$

### 1.1.5 Scalar product

This is defined as

$$
\mathbf{a} \cdot \mathbf{b}= a_1b_1 + a_2b_2 + a_3b_3
$$

$$
=a_i b_i
$$

using the summation convention. Recall that if $$\mathbf{a} \cdot \mathbf{b}=0$$ then the vectors $$\mathbf{a}$$ and $$\mathbf{b}$$ are orthogonal.

### 1.1.6 Triple scalar product

This is the quantity

$$
\begin{array}{r}
\va \cdot (\vb) \times \vc & = a_i [\vb \times \vc]_i = a_i \ve_{ijk}b_jc_k \\
& = \ve_{ijk}a_ib_jc_k \\
\end{array}
$$

sum over $$i, j, k$$.

#### Remark

- If this quantity is zero, then the three vectors are coplanar.

- A useful property of the triple scalar product is that the dot and cross can be swapped without changing the value, provied that the order of the vectors is not changed:

$$
\mathbf{a} \cdot(\mathbf{b} \times \mathbf{c})=(\mathbf{a} \times \mathbf{b}) \cdot \mathbf{c} .
$$

**Proof**:

$$
\va \cdot (\vb \times \vc) = \ve_{ijk}a_ib_jc_k = (\ve_{kij}a_ib_j)c_k  = [\va \times \vb]_k c_k = (\va \times \vb) \cdot \vc.
$$

### 1.1.7 Triple vector product

This is defined as

$$
\mathbf{a} \times(\mathbf{b} \times \mathbf{c}) .
$$

#### Remark

Since $$\vb \times \vc$$ is perpendicular to $$\vb$$ and $$\vc$$, and $$\va \times (\vb \times \vc)$$ is perpendicular to $$\vb \times \vc$$. It follows that the triple vector product must lie in the plane of $$\vb$$ and $$\vc$$. If we write it as the notations that we introduced before, we could write

$$
\begin{aligned}
{[\mathbf{a} \times(\mathbf{b} \times \mathbf{c})]_{i} } & = \ve_{ijk} \va_j[\vb \times \vc]_k\\
& = \ve_{ijk}a_j \ve_{klm}\vb_l\vc_m\\
& = \ve_{ijk}\ve_{klm}a_j\vb_l\vc_m\\
& = (\delta_{il}\delta_{jm} - \delta_{im}\delta_{jl})\va_j\vb_l\vc_m\\
& = \va_j\vb_i\vc_j - \va_j\vb_j\vc_i\\
& = (\va \cdot \vc)\vb_i - (\va \cdot \vb)\vc_i\\
\end{aligned}
$$

and so we conclude that

$$
\mathbf{a} \times(\mathbf{b} \times \mathbf{c})=(\mathbf{a} \cdot \mathbf{c}) \mathbf{b}-(\mathbf{a} \cdot \mathbf{b}) \mathbf{c},
$$

which confirms explicitly that the triple vector product indeed lies in the plane of $$\mathbf{b}$$ and c. 

## 1.2 Gradient

We consider the equation $$\phi =$$ constant defines a surface in space. If we vary the constant, we could define a famliy of surfaces called '**level surfaces**' or '**equi - $$\phi$$ surfaces**'. The surface through a **specific point** $$P$$ is $$\phi = \phi(P)$$. Let $$Q$$ be a neighbouring point on the surface. The 









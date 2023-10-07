---
title: Matrix
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
$$\gdef\va{\mathbf{a}}$$
$$\gdef\vb{\mathbf{b}}$$
$$\gdef\vc{\mathbf{c}}$$

##### based on the notes and lectures of [Prof. Martin Liebeck](https://www.ma.ic.ac.uk/~mwl/)

## 1. Course Overview

For now, we assume $$\F$$ is a field.

### 1.1 Matrix results

#### Similar matrices
##### Definition (Similar matrices)

Let $$A$$ and $$B$$ be $$n \times n$$ matrices over $$\F$$, then we say that $$A$$ and $$B$$ are **similar** if there exists an invertible $$n \times n$$ matrix $$P$$ such that

$$
B = P^{-1}AP
$$

then we write $$A \sim B$$.

Notice that the $$\sim$$ defines an equivalence relation. (Proof in Problem Sheet 1)
##### Proposition (Eigen-stuffs,ranks, traces, and determinants are the same for similar matrices)

Let $$A$$ and $$B$$ be $$n \times n$$ matrices over a field $$\F$$. If $$A \sim B$$, then $$A$$ and $$B$$ have the same

1. ranks(Multiplications by invertible matrices do not change the rank of a matrix)
2. characteristic polynomials -- implies the following 3, 4 and 5.
3. eigenvalues
4. determinant
5. trace

**Proof**:

##### Major Aim

The major aim of the part of the course is to find a 'nice' matrix $$B$$ such that $$A \sim B$$ for an arbitrary $$n \times n$$ matrix $$A$$ and we will prove some theorems to show what 'nice' means. 

#### Diagonalization

We start from the easiest case: diagonalization. Recall the definition of diagonalization:
##### Definition (Diagonalization)

An $$n \times n$$ matrix $$A$$ over $$\F$$ is **diagonalizable** if $$A \sim D$$ where $$D = diag(\lambda_1, \dots, \lambda_n)$$ is a diagonal matrix with diagonal entries $$\lambda_1, \dots, \lambda_n \in \F$$, which are the eigenvalues of $$A$$.

##### Remark

- We could use the property of similarity of diagonal matrices to calculuate any power $$A^k$$.
  
    $$
    A^k = (PDP^{-1})^k = PD^kP^{-1}
    $$

    where $$D^k = diag(\lambda_1^k, \dots, \lambda_n^k)$$.

However, most matrices are not diagonalizable. However, every complex matrix could be **triangularised**.
#### Triangularisation
##### Theorem 1.4 (Triangularization)

If $$A$$ is an $$n \times n$$ matrix over $$\mathbb{C}$$, then $$A$$ is similar to an upper triangular matrix, i.e. there exists $$P$$ such that

$$
P^{-1} A P=\left(\begin{array}{cccccc}
\lambda_{1} & & & & \\
0 & \lambda_{2} & & & * & \\
& & \cdot & & & \\
0 & 0 & & & \lambda_{n}
\end{array}\right) .
$$

**Proof**:

##### Remark

1. This does not always hold for any field $$\F$$.

2. This upper triangular matrix is not unique since we can always do some row operations to make it more 'nice'. For example, we can make the diagonal entries to be $$1$$ by dividing the $$i$$-th row by $$\lambda_i$$.

It is diserable to have a unique matrix of a nice form that is similar to $$A$$ and we have the next following form.

#### Jordan Canonical Form
##### Definition (Jordan block)

A **Jordan block** of size $$k$$ is a $$k \times k$$ matrix of the form

$$
J_k(\lambda) = \begin{pmatrix}
\lambda_i &1 &0 &\dots &0 \\
0 &\lambda_i &1 &\dots &0 \\
\vdots &\vdots &\vdots &\ddots &\vdots \\
0 &0 &0 &\dots &\lambda_i
\end{pmatrix}
$$
##### Theorem (Jordan Canonical Form Theorem)

If $$A$$ is an $$n \times n$$ matrix over $$\C$$, $$A$$ is similar to a unique matrix

$$
A \sim J
$$

where

$$
J = \begin{pmatrix}
J_{k_1}(\lambda_1) &0 &\dots &0 \\
0 &J_{k_2}(\lambda_2) &\dots &0 \\
\vdots &\vdots &\ddots &\vdots \\
0 &0 &\dots &J_{k_r}(\lambda_r)
\end{pmatrix}
$$

The collection of *Jordan blocks* in $$J$$ is uniquely determined by $$A$$ and we call matrix $$J$$ the **Jordan canonical form(JCF)** of $$A$$.

**Proof**:



##### Hand calculuation algorithm of Jordan Canonical Form
##### Remark

- The uniqueness of $$J$$ is a vital part of this theorm since it gives a powerful test for the similarity of two complex matrices. i.e. $$A \sim B$$ if and only if $$A$$ and $$B$$ have the same Jordan canonical form.
  
- Notice that the Jordan Canonical Form does not always exist for any field $$\F$$, such as $$\R, \Q, \F_p$$. For more general fields, we have the following theorem.




#### Rational Canonical Form theorm

To see this, we need to introduce a bit of new notaiton:

- $$\F[x]$$ is the set of all polynomials in $$x$$ over $$\F$$

- We call a polynomial $$f(x) \in \F[x]$$ **monic** if it has degree $$r \geq 1$$ and the coefficient of $$x^r$$ is $$1$$. i.e.

    $$
    f(x) = x^r + a_{r-1}x^{r-1} + \dots + a_1x + a_0
    $$
    
    where $$a_i \in \F$$ for $$i = 0, \dots, r-1$$.


##### Definition (Companion matrix)

Let $$p(x)$$ be a monic polynomial of degree $$r$$. The **companion matrix** of $$p(x)$$ is the $$r \times r$$ matrix $$C(p(x))$$ defined as follows:

$$
C(p(x)) = \begin{pmatrix}
0 &0 &\dots &0 &-a_0 \\
1 &0 &\dots &0 &-a_1 \\
0 &1 &\dots &0 &-a_2 \\
\vdots &\vdots &\ddots &\vdots &\vdots \\
0 &0 &\dots &1 &-a_{r-1}
\end{pmatrix}
$$

Note that the characteristic polynomial of $$C(p(x))$$ is $$p(x)$$.

##### Theorem (Rational Canonical Form Theorem)

Let $$A$$ be an $$n \times n$$ matrix over $$\F$$, with characteristic polynomial $$p(x)$$.

1. There exists a factorization $$p(x) = p_1(x) \dots p_k(x)$$ such that $$A$$ is similar to a block diagonal matrix with blocks $$C(p_i(x))$$ for $$i = 1, \dots, k$$.\

2. Under some conditions(To be completed), the polynomial $$p_1(x), \dots, p_k(x)$$ are uniquely determined by $$A$$ and we call the matrix in 1 the **rational canonical form(RCF)** of $$A$$. 

### 1.2 Geometry

##### Definition (Dot product)

If $$u = (u_1, \dots, u_n), v = (v_1, \dots, v_n) \in \R$$, then

$$
u \cdot v = u v^T = u_1v_1 + \dots + u_nv_n
$$

##### Definition (Length)

If $$v \in \R^n$$, then the **length** of $$v$$ is

$$
\norm{v} = \sqrt{v \cdot v} = \sqrt{v_1^2 + \dots + v_n^2}
$$

##### Definition (Distance)

If $$u, v \in \R^n$$, then the **distance** between $$u$$ and $$v$$ is

$$
d(u, v) = \norm{u - v}
$$

##### Orthogonality and symmetry

- P is orthogonal if $$P^TP = I$$, which implies that $$Pu \cdot Pv = u \cdot v$$ for all $$u, v \in \R^n$$.
  
- P is symmetric if $$P^T = P$$, which implies that $$Pu \cdot Pv = u \cdot Pv$$ for all $$u, v \in \R^n$$.

##### Definition (Inner Product Space)

An **inner product space** is a vector space $$V$$ with a map sending any two pair of vectors $$u, v \in V$$ to a scalar $$\inner{u}{v}$$ satisfying the following axioms:

1. The map is linear in each variable $$u$$ and $$v$$.

2. The map is symmetric, i.e. $$\inner{u}{v} = \inner{v}{u}$$.

3. $$\inner{u}{u} \geq 0$$ and $$\inner{u}{u} = 0$$ if and only if $$u = 0$$.

## 2. Some revision from 1st Year Linear Algebra

Next, we assume $$V$$ is a finite-dimensional vector space over $$\F$$.

### Basis

##### Definition (Matrix of a linear map)

Let $$T:V \to V$$ be a linear map. Let $$B = \{v_1, \dots, v_n\}$$ be a basis of $$V$$, let

$$
\begin{aligned}
T\left(v_{1}\right) & =a_{11} v_{1}+\ldots+a_{n 1} v_{n}, \\
& \vdots \\
T\left(v_{n}\right) & =a_{1 n} v_{1}+\ldots+a_{n n} v_{n}
\end{aligned}
$$

where all the coefficients $$a_{ij} \in \F$$. Then the **matrix of $$T$$ with respect to $$B$$** is the $$n \times n$$ matrix

$$
[T]_B = (a_{ij}) =
\left(\begin{array}{cccc}
a_{11} & a_{12} & \ldots & a_{1 n} \\
a_{21} & a_{22} & \ldots & a_{2 n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n 1} & a_{n 2} & \ldots & a_{n n}
\end{array}\right)
$$

##### Proposition (The matrix of a composition of linear maps is the product of the matrices)

Let $$S: V \rightarrow V$$ and $$T: V \rightarrow V$$ be linear transformations and let $$B$$ be a basis of $$V$$. Then

$$
[S T]_{B}=[S]_{B}[T]_{B},
$$

where $$S T$$ is the composition of $$S$$ and $$T$$.

**Proof**:

##### Remark

The propostion above gives us a lot nice properties of matrices. For example, if $$[T]_B = A$$ then $$[T^{k}]_B = A^{k}$$ for any positive integer $$k$$. More generally, if we are give such a polynomial $$q(x) = a_0 + a_1x + \dots + a_kx^k (a_i \in \F)$$, and define

$$
q(A) = a_0I + a_1A + \dots + a_kA^k
$$

and

$$
q(T) = a_0I + a_1T + \dots + a_kT^k
$$

where $$I$$ is the identity map. Then we have

$$
[q(T)]_B = q([T]_B) = q(A)
$$

#### Change of basis

##### Definition (Change of basis matrix)

Let bases $$E = \{e_1, \dots, e_n\}$$ and $$F = \{f_1, \dots, f_n\}$$ of $$V$$ be given and we write

$$
\begin{aligned}
f_{1} & =p_{11} e_{1}+\cdots+p_{n 1} e_{n}, \\
& \vdots \\
f_{n} & =p_{1 n} e_{1}+\cdots+p_{n n} e_{n} .
\end{aligned}
$$

and define $$P$$ to be the $$n \times n$$ matrix $$\left(p_{i j}\right)$$. We call $$P$$ **the change of basis matrix** from $$E$$ to $$F$$.

##### Proposition

1. The change of basis matrix $$P$$ is invertible.
   
2. If $$T: V \rightarrow V$$ is a linear map, then

    $$
    [T]_{F}=P^{-1}[T]_{E} P
    $$

    So, $$[T]_E$$ and $$[T]_F$$ are similar.

**Proof**:

#### Determinant

As we mentioned before, if $$A$$ and $$B$$ are similar, then they have the same determinant. Hence, if $$T: V \rightarrow V$$ is a linear map, and $$E$$, $$F$$ are two bases of $$V$$, then the matrices $$[T]_E$$ and $$[T]_F$$ are similar and hence have the same determinant. So, we can define the determinant of $$T$$ to be the determinant of $$[T]_E$$ for any basis $$E$$ of $$V$$.

##### Remark

It is easy to notice that the matrix are just the expression of a linear map with respect to a basis. So, we can define the determinant of a linear map $$T$$ to be the determinant of $$[T]_E$$ for any basis $$E$$ of $$V$$ and the determinant of a linear transformation is invariant under change of basis.

#### Eigen-stuffs

##### Definition (Characteristic polynomial)

The **characteristic polynomial** of $$T$$ is defined to be

$$
\chi_{T}(x)=\operatorname{det}(x I-T)
$$

This is a polynomial in $$x$$ of degree $$n = \dim V$$.

##### Proposition

1. The eigenvalues of $$T$$ are the roots of the characteristic polynomial $$\chi_T(x)$$.

2. If $$\lambda$$ is an eigenvalue of $$T$$, the eigenvectors corresponding to $$\lambda$$ are the non-zero vectors in

    $$
    E_{\lambda} = \{v \in V: (\lambda I_V - T)(v) = 0\} = \operatorname{Ker}(\lambda I_V - T)
    $$

3. The matrix $$[T]_B$$ is diagonal if and only if $$B$$ consists of eigenvectors of $$T$$.

##### Defintion (Eigenspace)

We call $$E_{\lambda}$$ the **$$\lambda$$-eigenspace** of $$T$$. Note that $$E_{\lambda}$$ is a subspace of $$V$$ since it is the kerel of the linear map $$\lambda I_V - T$$.

##### Proposition (Any linear transformation has eigenvalue(s))

Let $$V$$ be a finite-dimentional vector space over $$\C$$, and let $$T: V \rightarrow V$$ be a linear map. Then $$T$$ has an eigenvalue $$\lambda \in \C$$.

**Proof**: The fundamental theorem of algebra.

It is not always true for any field $$\F$$. For example, the linear transformation $$T: \R^2 \rightarrow \R^2$$ defined by

$$
T\left(\left(\begin{array}{l}
x_1 \\
x_2
\end{array}\right)\right)=\left(\begin{array}{l}
x_2 \\
-x_1
\end{array}\right)
$$

has the characteristic polynomial $$x^2 + 1$$ which has no roots in $$\R$$.

#### Diagonalisation

##### Definition (Diagonalizable)

A linear map $$T: V \rightarrow V$$ is **diagonalizable** if there exists a basis $$B$$ of $$V$$ consisting of eigenvectors of $$T$$.

##### Proposition

Let $$T: V \rightarrow V$$ be a linear map. Suppose $$v_{1}, \ldots, v_{k}$$ are eigenvectors of $$T$$ corresponding to distinct eigenvalues $$\lambda_{1}, \ldots, \lambda_{k}$$. Then $$v_{1}, \ldots, v_{k}$$ are linearly.

**Proof**:

##### Corollary

Let $$V$$ be $$n$$-dimensional over $$F$$, and let $$T: V \rightarrow V$$ a linear map. Suppose the characteristic polynomial of $$T$$ has $$n$$ distinct roots in $$F$$. Then $$T$$ is diagonalisable.

**Proof**:











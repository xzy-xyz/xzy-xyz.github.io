---
layout: simple
title: Chapter 1 Vector, Matrices, and Derivatives
---

$$\gdef\rr{\mathbb{R}}$$
$$\gdef\cc{\mathbb{C}}$$
$$\gdef\zz{\mathbb{Z}}$$
$$\gdef\nn{\mathbb{N}}$$
$$\gdef\qq{\mathbb{Q}}$$
$$\gdef\vv{\vec{\mathbb{v}}}$$
$$\gdef\vw{\vec{\mathbb{w}}}$$
$$\gdef\vx{\vec{\mathbb{x}}}$$
$$\gdef\vy{\vec{\mathbb{y}}}$$
### 1.1 Introducing the actors: points and vectors

#### Points and vectors: Positional data versus incremental data

##### Definition 1.1.1 (Points, vectors, and coordinates)

The element of $$\mathbb{R}^n$$ with coordinates $$x_1, \cdots, x_n$$ can be interpreted as the *point*

$$
\mathbf{x} = \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix}
$$

or, as the *vector*

$$
\vec{\mathbf{x}} = \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix}
$$

which represents an increment.

#### Subtraction and addition of points and vectors

Vectors are added by adding the corresponding coordinates:

$$
\vec{\mathbf{x}} + \vec{\mathbf{y}} = \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix} + \begin{pmatrix} y_1 \\ \vdots \\ y_n \end{pmatrix} = \begin{pmatrix} x_1 + y_1 \\ \vdots \\ x_n + y_n \end{pmatrix}
$$

The result is a vector. Similarly, vectors are subtracted by subtracting the corresponding coordinates.

#### Multiplying vectors by scalars

Multiplication of a vector by a *scalar* is straightforward:

$$
\lambda \vec{\mathbf{x}} = \lambda \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix} = \begin{pmatrix} \lambda x_1 \\ \vdots \\ \lambda x_n \end{pmatrix}
$$

#### Subsets and subspace of $$\mathbb{R}^n$$

##### Definition 1.1.5 (Subspace of $$\mathbb{R}^n$$)

A nonempty subset $V \subset \mathbb{R}^n$ is a *subspace* if it is closed under addition and scalar multiplication by scalars; that is, $$V$$ is a subspace if when

$$
\vec{\mathbf{x}}, \vec{\mathbf{y}} \in V \text{ then } \vec{\mathbf{x}} + \vec{\mathbf{y}} \in V \text{ and } \lambda \vec{\mathbf{x}} \in V
$$

##### Remark

Roughly, a subspace is a flat subset that goes through the origin.

##### Example

What is the subsapace of $$\mathbb{R}^2$$? There are exactly treee kinds: line through the origin, and two trivial subspaces, the origin and the whole space. Intutively, it is clear that a line through the origin is a subspace of dimension 1 and a plane through the origin is a subspace of dimension 2: it takes one number to locate a point on a line, and two numbers to locate a point on a plane.

#### The standard basis vectors

##### Definition 1.1.7 (Standard basis vectors)

The *standard basis vectors* in $$\mathbb{R}^n$$ are the vectors $$\vec{\mathbf{e}}_j$$ with $$n$$ entries, the $$j$$th entry $$1$$ and the others zero.

#### Vector fields

##### Definition 1.1.8 (Vector field)

A *vector field* is a function whose input in $$\mathbb{R}^n$$ and whose output is a vector in $$\mathbb{R}^n$$ emanating from that point.

##### Example

By "field", we mean data that varies from point to point. Some fields, like temperature or pressure distribution, are scalar fields: they associate a number to every point. Some fields, like the Newtonian gravitational field, are best modeled by vector fields, which associate a vector to every point. Others, like electromagnetic field and charge distributions, are best modeled by form field. Still others, like the Einsteinian gravitational field of general relativity, are none of the above.

### 1.2 Introducing the actors: matrices

##### Definition 1.2.4 (Matrix Multiplication)

If $$A$$ is an $m \times n$ matrix whose $$(i,j)$$th entry is $$a_{i,j}$$ is $$B$$ is an $$n \times p$$ matrix whose $$(i,j)$$th entry is $$b_{i,j}$$, then $$C = AB$$ is the $$m \times p$$ matrix whose $$(i,j)$$th entry is

$$
c_{i,j} = \sum_{k=1}^n a_{i,k} b_{k,j} = a_{i,1}b_{1,j} + \cdots + a_{i,n}b_{n,j}
$$

Matrix multiplication is associative and distributive, but not commutative.

#### Matrix inverses

##### Definition 1.2.13 (Invertible matrix)

An *invertible matrix* is a matrix that has both a left inverse and a right inverse.

##### Proposition and definition 1.2.14 (Matrix inverse)

If a matrix $$A$$ has both a left and a right inverse, then it has only one left inverse and one right inverse, and they are identical; such a matrix is called the *A* of $$A$$ and is denoted by $$A^{-1}$$.

##### Proposition 1.2.15 (The inverse of the product of matrices)

If $$A$$ and $$B$$ are invertible matrices, then $$AB$$ is invertible and the inverse is given by the formula:

$$
(AB)^{-1} = B^{-1}A^{-1}
$$

#### The transpose

##### Definition 1.2.16 (Transpose)

The *transpose* $$A^T$$ of a matrix $$A$$ is the matrix whose $$(i,j)$$th entry is the $$(j,i)$$th entry of $$A$$.

##### Theorem 1.2.17 (The transpose of a product)

The transpose of a product is the product of the transpose in reverse order:

$$
(AB)^T = B^T A^T
$$

#### Special kinds of matrices

##### Definition 1.2.18 (Symmetric matrix and antisymmetric matrix)

A symmetric matrix is a matrix that is equal to its transpose. An antisymmetric matrix is a matrix that is equal to the negative of its transpose.

##### Definition 1.2.19 (Triangular matrix)

An *upper triangular matrix* is a matrix whose entries below the main diagonal are all zero. A *lower triangular matrix* is a matrix whose entries above the main diagonal are all zero.

#### Applications: Probabilities and graphs

##### Proposition 1.2.23. 

For any graph formed of vertices connected by edges, the number of possible walks of length $$n$$ from vertex $$V_i$$ to vertex $$V_j$$ is given by the $$(i,j)$$th entry of the matrix $$A^n$$ formed by taking the $$n$$th power of the graph's adjacency matrix $$A$$.

**Proof:**(Wait to be finished)

### 1.3 What the Actors do: Matrix Multiplication as a Linear Transformation

##### Definition 1.3.2 (Linear transformation from $$\mathbb{R}^n$$ to $$\mathbb{R}^m$$)

A *linear transformation* $$T: \mathbb{R}^n \to \mathbb{R}^m$$ is a mapping such that for all scalars $$a$$ and all $$\vec{v}$$ and $$\vec{w}$$ in $$\mathbb{R}^n$$,

$$
T(\vec{v} + \vec{w}) = T(\vec{v}) + T(\vec{w})\quad \text{and} \quad T(a\vec{v}) = aT(\vec{v})
$$

##### Theorem 1.3.4 (Matrices and linear transformations)

1. Any $$m \times n$$ matrix $$A$$ defines a linear transformation $$T:\mathbb{R}^n \to \mathbb{R}^m$$ by matrix multiplication:

$$
T(\vec{v}) = A\vec{v}
$$

2. Every linear transformation $$T:\mathbb{R}^n \to \mathbb{R}^m$$ is given by multiplication by an $$m \times n$$ matrix $[T]$$$:

$$
T(\vec{v}) = [T]\vec{v}
$$

where the $$i$$th column of $$[T]$$ is $$T(\vec{e}_i)$$.

**Proof**:

Start with a linear transformation $$T: \mathbb{R}^n \to \mathbb{R}^m$$, let $$\vec{v} \in \mathbb{R}^n$$ be any vector. We could write $$\vec{v}$$ as a linear combination of the standard basis vectors:

$$
\vec{v} = \sum_{i=1}^n v_i \vec{e}_i
$$

Then, by the linearity of $$T$$, we have

$$
T(\vec{v}) = T(\sum_{i=1}^n v_i \vec{e}_i) = \sum_{i=1}^n v_i T(\vec{e}_i)
$$

which is precisely the column vector $$[T]\vec{v}$$. If we tranlate it into sum notation:

$$
T(\vec{v}) = \sum_{i=1}^n v_i T(\vec{e}_i) = v_1 T(\vec{e}_1) + \cdots + v_n T(\vec{e}_n) = [T] \left[\begin{array}{c} v_1 \\ \vdots \\ v_n \end{array}\right] = [T]\vec{v}
$$

##### Theorem 1.3.10 (Composition corresponds to matrix multiplication)

Suppose $$S: \rr^n \to \rr^m$$ and $$T: \rr^m \to \rr^l$$ are linear transformation given by the matrices $$[S]$$ and $$[T]$$ respectively. Then the composition $$T \circ S: \rr^n \to \rr^l$$ is linear and given
by

$$
[T \circ S] = [T][S]
$$

**Proof**:
Apply the definition of linear transformation to $$T \circ  S$$. Therefore, it is linear.

The equation is a statement about matrix multiplication. We will use the following fact derived from the definition of matrix multiplication:

1. $$A \vec{e}_i$$ is the $$i$$th column of $$A$$.
2. The $$i$$the column of $$AB$$ is $$A(B\vec{e}_i)$$.

$$
[T \circ S] \vec{e}_i = T(S(\vec{e}_i)) = T([S]\vec{e}_i) = [T][S]\vec{e}_i
$$

Since $$T \circ S$$ is linear, it is given by the matrix $$[T \circ S]$$. while the definition of composition given the second equlity.

##### Theorem 1.3.12 (Matrix multiplication is associative)

If $$A, B, C$$ are matrices such that the products $$AB$$ and $$BC$$ are defined, then

$$
(AB)C = A(BC)
$$

#### Invertibility of matrices and linear transformation

Recall that a mapping is invertible if it is one to one and onto.

##### Proposition 1.3.14 

A linear transformation $$T: \rr^n \to \rr^m$$ is invertible if and only if its matrix $$[T]$$ is invertible, and

$$
[T^{-1}] = ([T])^{-1}
$$

**Proof**:

- $$\Rightarrow$$:
  We suppose that $$T$$ is invertible. Then $$T$$ is one to one and onto. We will show that $$T^{-1}$$ is also linear. Let $$\vec{v}, \vec{w} \in \rr^n$$, then 

  $$
    T(a T^{-1}(\vec{v}) + b T^{-1}(\vec{w})) = a T(T^{-1}(\vec{v})) + b T(T^{-1}(\vec{w})) = a \vec{v} + b \vec{w} = T \circ T^{-1} (a \vec{v} + b \vec{w})
$$

Since $$T$$ is one to one and onto, $$T^{-1}$$ is linear. Therefore, $$T^{-1}$$ has matrix $$[T^{-1}]$$. We now check that

$$
[T^{-1}] = ([T])^{-1}
$$

Since $$T$$ is invertible, $$[T]$$ is invertible. Therefore, $$[T]^{-1}$$ exists. We have

$$
[TT^{-1}] = [I] = [T][T]^{-1} = [T][T^{-1}]
$$

Thus $$[T]$$ is invertible and its inverse $$[T]^{-1}$$ is $$[T^{-1}]$$.

- $$\Leftarrow$$:
  We suppose that $$[T]$$ is ivertible and we let $$S: \rr^m \to \rr^n$$ be the linear transformation such that $$S = [T]^{-1}$$. We need to show that $$T$$ is one to one and onto. For onto, for any $$\vy \in \rr^m$$, we have

  $$
  \vy = I \vy = [T][T]^{-1} \vy = [T] S \vy = T(S (\vy))
$$

It showing that $$T$$ is onto. For one to one, we need to show that $$T(\vec{v}) = T(\vec{w})$$ implies $$\vec{v} = \vec{w}$$. 

$$
\vv = I \vv = ([S][T]) \vv = S(T(\vv)) = S(T(\vw)) = ([S][T]) \vw = I \vw = \vw
$$

Therefore, $$T$$ is one to one and onto, which means $$T$$ is invertible.

### 1.4 The Gemoetry of $$\rr^n$$

#### The dot product

##### Definition 1.4.1 (Dot product)

The *dot product* of two vectors $$\vec{v}$$ and $$\vec{w}$$ in $$\rr^n$$ is the number
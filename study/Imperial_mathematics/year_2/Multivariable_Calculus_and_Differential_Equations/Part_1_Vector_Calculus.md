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
$$\gdef\abs#1{\left| #1 \right|}$$
$$\gdef\pap#1{\frac{\partial \phi }{\partial #1}}$$
$$\gdef\va{\mathbf{a}}$$
$$\gdef\vb{\mathbf{b}}$$
$$\gdef\vc{\mathbf{c}}$$
$$\gdef\ve{\varepsilon}$$
$$\gdef\nvi{\widehat{\mathbf{i}}}$$
$$\gdef\nvj{\widehat{\mathbf{j}}}$$
$$\gdef\nvk{\widehat{\mathbf{k}}}$$
$$\gdef\nve{\widehat{\mathbf{e}}}$$
$$\gdef\ns{\widehat{\mathbf{s}}}$$
$$\gdef\nn{\widehat{\mathbf{n}}}$$
$$\gdef\d{\operatorname{div}}$$
$$\gdef\cu{\operatorname{curl}}$$
$$\gdef\g{\nabla}$$
$$\gdef\vf{\mathbf{A}}$$

For this part, we only consider less or equal to three dimensions and assume that $$\mathbf{A}$$ is a vector field and $$\phi$$ is a scalar field.

## 1.1 Preliminarry ideas and some revision of vectors

### 1.1.0 Scalar and vector fields

#### Definition (Scalar field)

A **scalar field** is a function $$\phi$$

$$
\phi: \R^n \to \R
$$

#### Definition (Vector field)

A **vector field** is a function $$\mathbf{A}$$

$$
\mathbf{A}: \R^n \to \R^m
$$

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
\varepsilon_{i j k} \varepsilon_{k l m} = \delta_{i l} \delta_{j m}-\delta_{i m} \delta_{j l}
$$

$$(1.1)$$ is sum over $$k$$. 

**Proof**: 

Firstly, we write the left hand side of $$(1.1)$$ with its full summation over $$k$$:

$$
\varepsilon_{i j k} \varepsilon_{k l m} = \varepsilon_{i j 1} \varepsilon_{1 l m} + \varepsilon_{i j 2} \varepsilon_{2 l m} +\varepsilon_{i j 3} \varepsilon_{3 l m}
$$

If $$i = j$$ or $$l = m$$, then the left hand side are all $$0$$ and the right hand side is $$0$$. Therefore,we only need to consider the case that $$i \neq j$$ and $$l \neq m$$. Next, we notice that if we swap the $$i$$ & $$j$$ in the left hand side, the sign of both sides will change. Therefore, we only need to consider the case that $$i < j$$ and $$l < m$$. The cases that we need to consider are

$$
(i, j) = (1, 2), (1, 3), (2, 3)
$$

For $$(i, j) = (1, 2)$$, the left hand side of $$(1.1)$$ is

$$
    \varepsilon_{1 2 k} \varepsilon_{k l m} = \varepsilon_{1 2 1} \varepsilon_{1 l m} + \varepsilon_{1 2 2} \varepsilon_{2 l m} +\varepsilon_{1 2 3} \varepsilon_{3 l m} = \varepsilon_{1 2 3} \varepsilon_{3 l m} =  \varepsilon_{3 l m} = \begin{cases} 0  \text{ if } l \text{ or } m = 3 \\ 1 \text{ if } (l, m) = (1, 2) \\ \end{cases}
$$

The right hand side of $$(1.1)$$ is

$$
    \delta_{1 l} \delta_{2 m}-\delta_{1 m} \delta_{2 l} = \begin{cases} 0  \text{ if } l \text{ or } m = 3 \\ 1 \text{ if } (l, m) = (1, 2) \\ \end{cases}
$$

The left cases are similar. Therefore, we have proved $$(1.1)$$.
    
The quantities $$\delta_{i l}$$ and $$\varepsilon_{j k m}$$ are called **tensors**.

There is an alternative form:

$$
\varepsilon_{i j k} \varepsilon_{k l m} = \delta_{j l} \delta_{k m}-\delta_{j m} \delta_{k l}
$$

which is sum over $$i$$. The proof is similar to $$(1.1)$$.

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
\begin{aligned}
a_{2} b_{3}-a_{3} b_{2} & = \ve_{123}a_2b_3 + \ve_{132}a_3b_2 \\
                     & = \ve_{ijk}a_jb_k \\
\end{aligned}
$$

since $$\varepsilon_{123}=1, \varepsilon_{132}=-1$$, and $$\varepsilon_{1 i j}=0$$ for all other $$i$$ and $$j$$. In general we can write the $$i$$ th component of $$a \times b$$ as

$$
[a \times b]_{i} = \ve_{1jk}a_jb_k
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

### Definition (Level surfaces)

The equation $$\phi = constant$$ defines a surface in $$3$$ dimensions. Varying the constant, we could define a family of surfaces. The surfaces are called the **level surfaces** of $$\phi$$ or **equi-$$\phi$$** surfaces. 

### Definition (Directional derivative)

Assume there is a specific point $$P$$ such that $$\phi = \phi(P)$$ and $$Q$$ is a neighbouring point. The equation of the level surface through $$Q$$ is $$\phi = \phi(Q)$$. We draw the normal line to $$\phi = \phi(P)$$ at $$P$$ and the normal line intersects the level surface $$\phi = \phi(Q)$$ at $$N$$. Since $$N$$ is on the level surface, $$\phi(N) = \phi(Q)$$. Let $$s$$ denote the length along $$PQ$$ and let $$n$$ denote the length along $$PN$$. Use unit vectors $$\widehat{\mathbf{s}}$$ and $$\widehat{\mathbf{n}}$$ in these two directions. We define $$\partial \phi / \partial s$$ to be the **directional derivative** of $$\phi$$ in the direction $$\widehat{\mathbf{s}}$$ :

$$
\begin{aligned}
\frac{\partial \phi}{\partial s} & = \lim_{PQ \to 0} \frac{\phi(Q) - \phi(P)}{|PQ|}\\
& = \lim_{Q \to P} \frac{\phi(N) - \phi(P)}{|PN|}\cdot \frac{|PN|}{|PQ|}\\
& = \lim_{N \to P} \frac{\phi(N) - \phi(P)}{|PN|}\cdot \lim_{Q \to P}\frac{|PN|}{|PQ|}\\
& = \frac{\partial \phi}{\partial n} \cdot \lim_{Q \to P}\frac{|PN|}{|PQ|}\\
& = \frac{\partial \phi}{\partial n} \cdot \cos \theta \\
& = \frac{\partial \phi}{\partial n} \cdot (\widehat{\mathbf{n}} \cdot \widehat{\mathbf{s}}) \\
\end{aligned}
$$

since $$\cos \theta \leq 1$$, the maximum directional derivative at $$P$$ occurs along the normal to $$\phi = \phi(P)$$.

### Definition (Gradient)

The vector $$\widehat{\mathbf{n}} \partial \phi / \partial n$$ is called the gradient of $$\phi$$ at $$P$$. We write it as $$\operatorname{grad} \phi$$ or $$\nabla \phi$$. The operator grad or $$\nabla$$ is known as the vector gradient operator. We have

$$
\frac{\partial \phi}{\partial s}=\widehat{\mathbf{s}} \cdot \nabla \phi .
$$

### 1.2.1 Cartesian Components of $$\nabla \phi$$

$$
\begin{aligned}
\nabla \phi & =  \pap{x}\widehat{\mathbf{i}} + \pap{y}\widehat{\mathbf{j}} + \pap{z}\widehat{\mathbf{k}} \\

\end{aligned}
$$

### 1.2.2 Cylindrical polar components of $$\nabla \phi$$

The cylindrical polar coordinates are $$(r, \theta, z)$$.

$$
\begin{aligned}
\widehat{\mathbf{r}} & = \cos \theta \widehat{\mathbf{i}} + \sin \theta \widehat{\mathbf{j}} \\
\widehat{\theta} & = -\sin \theta \widehat{\mathbf{i}} + \cos \theta \widehat{\mathbf{j}} \\
\widehat{\mathbf{k}} & = \widehat{\mathbf{k}} \\
\end{aligned}
$$

We assume $$\g \phi = A_{1} \widehat{\mathbf{r}}+A_{2} \widehat{\theta}+A_{3} \widehat{\mathbf{k}}$$.

$$
\begin{aligned}
A_{1} & =\widehat{\mathbf{r}} \cdot \nabla \phi \\
& = \widehat{\mathbf{r}} \left(\pap{x} \widehat{\mathbf{i}} + \pap{y} \widehat{\mathbf{j}} + \pap{z} \widehat{\mathbf{k}}\right) \\
& = \cos \theta \pap{x} + \sin \theta \pap{y}\quad(\widehat{r} \cdot \widehat{k} = 0) \\
& = \frac{\partial x}{\partial r} \frac{\partial \phi}{\partial x}+\frac{\partial y}{\partial r} \frac{\partial \phi}{\partial y} \\
& = \frac{\partial \phi}{\partial r} \\
\end{aligned}
$$

Notice that it is not twice, since it is distributed to the two components.

$$
\begin{aligned}
A_{2} & =\widehat{\theta} \cdot \nabla \phi \\
& = \widehat{\theta} \left(\pap{x} \widehat{\mathbf{i}} + \pap{y} \widehat{\mathbf{j}} + \pap{z} \widehat{\mathbf{k}}\right) \\
& = -\sin \theta \pap{x} + \cos \theta \pap{y}\quad(\widehat{\theta} \cdot \widehat{k} = 0) \\
& = \frac{1}{r}\frac{\partial x}{\partial \theta} \frac{\partial \phi}{\partial x}+\frac{1}{r}\frac{\partial y}{\partial \theta} \frac{\partial \phi}{\partial y} \\
& = \frac{1}{r}\frac{\partial \phi}{\partial \theta} \\
\end{aligned}
$$

$$
A_3 = \widehat{\mathbf{k}} \cdot \nabla \phi = \pap{z}
$$

Hence,

$$
\nabla \phi=\widehat{\mathbf{r}} \frac{\partial \phi}{\partial r}+\frac{\widehat{\theta}}{r} \frac{\partial \phi}{\partial \theta}+\widehat{\mathbf{k}} \frac{\partial \phi}{\partial z} .
$$

### 1.2.3 Equation of a tangent plane to $$\phi = \phi(P)$$

The equation of the tangent plane is

$$
(\mathbf{r} - \mathbf{r}_p)(\nabla \phi)_p = 0.
$$

i.e.

$$
\left(\frac{\partial \phi}{\partial x}\right)_{P}\left(x-x_{P}\right)+\left(\frac{\partial \phi}{\partial y}\right)_{P}\left(y-y_{P}\right)+\left(\frac{\partial \phi}{\partial z}\right)_{P}\left(z-z_{P}\right)=0 .
$$

where $$(\pap{x})_P, (\pap{y})_P, (\pap{z})_P$$ are constants.

## 1.3 Divergence and Curl

### Definition (Divergence)

The **divergence** of a vector field $$\mathbf{A}$$ is defined as the scalar product,

$$
\operatorname{div} \mathbf{A} = \g \cdot \mathbf{A}
$$

### Definition (Curl)

The **curl** of a vector field $$\mathbf{A}$$ is defined as the vector product,

$$
\operatorname{curl} \mathbf{A}=\nabla \times \mathbf{A}
$$

### Remark

- The divergence of a vector field is a **scalar field**.
  
- The curl of a vector field is a **vector field**.

- **Divergence** is related to the **flux** of a vector field through a surface.

- **Curl** is related to the **circulation** of a vector field around a curve.

### 1.3.1 Cartesian form

$$
\begin{aligned}
\operatorname{div} \mathbf{A} & = (\frac{\partial}{\partial x}\widehat{\mathbf{i}} + \frac{\partial}{\partial y}\widehat{\mathbf{j}} + \frac{\partial}{\partial z}\widehat{\mathbf{k}}) \cdot (A_1\widehat{\mathbf{i}} + A_2\widehat{\mathbf{j}} + A_3\widehat{\mathbf{k}}) \\
& = \frac{\partial A_1}{\partial x} + \frac{\partial A_2}{\partial y} + \frac{\partial A_3}{\partial z} \\
& = \sum_{i=1}^{3} \frac{ \partial A_i}{\partial x_i}
\end{aligned}
$$

$$
\begin{aligned}
\operatorname{curl} \mathbf{A} & = \left|\begin{array}{ccc}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\
A_{1} & A_{2} & A_{3}
\end{array}\right|\\
& = \left(\frac{\partial A_3}{\partial y} - \frac{\partial A_2}{\partial z}\right)\widehat{\mathbf{i}} + \left(\frac{\partial A_1}{\partial z} - \frac{\partial A_3}{\partial x}\right)\widehat{\mathbf{j}} + \left(\frac{\partial A_2}{\partial x} - \frac{\partial A_1}{\partial y}\right)\widehat{\mathbf{k}} \\
& = \sum_{i=1}^{3} \ve_{ijk} \frac{\partial A_k}{\partial x_j} \\
\end{aligned}
$$

#### Remark

- The divergence of a vector field is a scalar field.
  
- The curl of a vector field is a vector field.

- These simple form for div and curl are only valid in Cartesian coordinates since $$\mathbf{i}, \mathbf{j}, \mathbf{k}$$ are constant vectors. 

- They are not commutative, i.e.

    $$
    \vf \cdot \g \neq \g \cdot \vf
    $$

    The left hand side is a **scalar operator** and the right hand side is divergence of a vector field, which is a **scalar**.

    $$
    \vf \times \g \neq \g \times A \text{ or } -\g \times \vf
    $$

    The left hand side is a **vector operator** and the right hand side is curl of a vector field, which is a **vector**.


## 1.4 Operations with the gradient operator

### 1.4.1 Impportant sum and product formulae

$$\g, \d, \cu$$ are linear operators, i.e.

$$
\begin{aligned}
& \text { (i) } \nabla\left(\phi_{1}+\phi_{2}\right) =\nabla \phi_{1}+\nabla \phi_{2}, \\
& \text { (ii) } \operatorname{div}(\mathbf{A}+\mathbf{B}) =\operatorname{div} \mathbf{A}+\operatorname{div} \mathbf{B}, \\
&\text { (iii) } \operatorname{curl}(\mathbf{A}+\mathbf{B}) =\operatorname{curl} \mathbf{A}+\operatorname{curl} \mathbf{B} .
\end{aligned}
$$

$$\g, \d, \cu$$ satisfy the product rule, i.e.

$$
\begin{aligned}
& \mathrm{ (iv) } \nabla(\phi \psi) =\phi \nabla \psi+\psi \nabla \phi \\
& \mathrm{ (v) } \operatorname{div}(\phi \mathbf{A}) =\phi \operatorname{div} \mathbf{A}+\nabla \phi \cdot \mathbf{A} .
\end{aligned}
$$


#### Remark

$$
\g \phi \cdot \vf = \vf \cdot \g \phi = (\vf \cdot \g) \phi
$$

**Proof**:

- (v)

    $$
    \begin{aligned}
    \d(\phi \vf) & = \left(\nvi \frac{\partial}{\partial x} + \nvj \frac{\partial}{\partial y} + \nvk \frac{}{z}\right) \cdot \left(\phi A_1 \nvi +\phi A_2 \nvj + \phi A_3 \nvk\right) \\
    & = \frac{\partial \phi A_1}{\partial x} + \frac{\partial \phi A_2}{\partial y} + \frac{\partial \phi A_3}{\partial z} \\
    & = \phi \left(\frac{\partial A_1}{\partial x} + \frac{\partial A_2}{\partial y} + \frac{\partial A_3}{\partial z}\right) + A_1 \frac{\partial \phi}{\partial x} + A_2 \frac{\partial \phi}{\partial y} + A_3 \frac{\partial \phi}{\partial z} \\
    & = \phi \d \vf + \g \phi \cdot \vf \\
    \end{aligned}
    $$

    If we use the **summation convention**, we could write

    - $$\g \phi = \nve_i \frac{\partial \phi}{\partial x_i}$$
  
    - $$\d \vf = \frac{\partial A_i}{\partial x_i}$$
  
    - $$[\g \phi]_i = \frac{\partial \phi}{\partial x_i}$$
  
    - $$[\cu \vf]_i = \ve_{ijk} \frac{\partial A_k}{\partial x_j}$$


    where $$[\:\;]_i$$ denotes the $$i$$ th component of the vector.

    Therefore, 

    $$
    \begin{aligned}
    \d (\phi \vf) & = \frac{\partial \phi A_i}{\partial x_i} \\
    & = \phi \frac{\partial A_i}{\partial x_i} + A_i \frac{\partial \phi}{\partial x_i} \\
    & = \phi \d \vf + (\vf \cdot \g) \phi \\
    \end{aligned}
    $$

#### Other important result

$$
\begin{aligned}
& \text { (vi) } \operatorname{curl}(\phi \mathbf{A})  =\phi \operatorname{curl} \mathbf{A}+\nabla \phi \times \mathbf{A}, \\
& \text { (vii) } \operatorname{div}(\mathbf{A} \times \mathbf{B}) =\mathbf{B} \cdot \operatorname{curl} \mathbf{A}-\mathbf{A} \cdot \operatorname{curl} \mathbf{B}, \\
& \text { (viii) } \operatorname{curl}(\mathbf{A} \times \mathbf{B})  =(\mathbf{B} \cdot \nabla) \mathbf{A}-\mathbf{B} \operatorname{div} \mathbf{A}-(\mathbf{A} \cdot \nabla) \mathbf{B}+\mathbf{A} \operatorname{div} \mathbf{B}, \\
& \text { (ix) } \nabla(\mathbf{A} \cdot \mathbf{B})  =(\mathbf{B} \cdot \nabla) \mathbf{A}+(\mathbf{A} \cdot \nabla) \mathbf{B}+\mathbf{B} \times \operatorname{curl} \mathbf{A}+\mathbf{A} \times \operatorname{curl} \mathbf{B} .
\end{aligned}
$$

**In the following, we assume that our vector and scalar fields are sufficiently smooth that we can interchange the order of differentiation.**

### 1.4.2 The divergence of a gradient: the Laplacian

#### Definition (Laplacian)

The **Laplacian** is the divergence of the gradient:


For a scalar field $$\phi$$, we have


$$
\begin{aligned}
\nabla^{2} \phi & = \d(\g \phi) \\
& = \left(\frac{\partial}{\partial x} \nvi + \frac{\partial}{\partial y} \nvj + \frac{\partial}{\partial z} \nvk\right) \cdot \left(\frac{\partial \phi}{\partial x} \nvi + \frac{\partial \phi}{\partial y} \nvj + \frac{\partial \phi}{\partial z} \nvk\right) \\
& = \frac{\partial^{2} \phi}{\partial x^{2}}+\frac{\partial^{2} \phi}{\partial y^{2}}+\frac{\partial^{2} \phi}{\partial z^{2}} \\
& = \g^2 \phi \\
& = \frac{\partial^2 \phi}{\partial x_i \partial x_i}\\
& = \frac{\partial^2 \phi}{\partial x_i^2} 
\end{aligned}
$$

For a vector field $$\vf$$, we have

$$
\begin{aligned}
\nabla^{2} \mathbf{A} & = \d(\g \vf) \\
& = \left(\frac{\partial}{\partial x} \nvi + \frac{\partial}{\partial y} \nvj + \frac{\partial}{\partial z} \nvk\right) \cdot \left(\frac{\partial A_1}{\partial x} \nvi + \frac{\partial A_2}{\partial y} \nvj + \frac{\partial A_3}{\partial z} \nvk\right) \\
& = \frac{\partial^{2} A_{1}}{\partial x^{2}}+\frac{\partial^{2} A_{2}}{\partial y^{2}}+\frac{\partial^{2} A_{3}}{\partial z^{2}} \\
& = \g^2 \vf \\
& = \frac{\partial^2 A_i}{\partial x_i \partial x_i}\\
& = \frac{\partial^2 A_i}{\partial x_i^2}
\end{aligned}
$$

### 1.4.3 The curl of a gradient

$$
\operatorname{curl}(\nabla \phi) = 0
$$

**Proof**:

$$
\begin{aligned}
[\operatorname{curl}(\nabla \phi)]_i & = \ve_{ijk} \frac{\partial}{\partial x_j} (\g \phi)_k \\
& = \ve_{ijk} \frac{\partial}{\partial x_j} \frac{\partial \phi}{\partial x_k} \\
& = \frac{1}{2} \ve_{ijk} \frac{\partial}{\partial x_j} \frac{\partial \phi}{\partial x_k} + \frac{1}{2} \ve_{ikj} \frac{\partial}{\partial x_k} \frac{\partial \phi}{\partial x_j} \\
& = \frac{1}{2} \ve_{ijk} \frac{\partial}{\partial x_j} \frac{\partial \phi}{\partial x_k} - \frac{1}{2} \ve_{ijk} \frac{\partial}{\partial x_k} \frac{\partial \phi}{\partial x_j} \\
& = \frac{1}{2} \ve_{ijk} \left(\frac{\partial}{\partial x_j} \frac{\partial \phi}{\partial x_k} - \frac{\partial}{\partial x_j} \frac{\partial \phi}{\partial x_k}\right) \\
& = 0 \\
\end{aligned}
$$

### 1.4.4 The divergence of a curl

$$
\operatorname{div}(\operatorname{curl} \mathbf{A}) = 0
$$

**Proof**:

$$
\begin{aligned}
\d = (\cu \vf) & = \frac{\partial }{\partial x_i}(\cu \vf)_i\\
& = \ve_{ijk} \frac{\partial}{\partial x_i} \frac{\partial A_k}{\partial x_j} \\
& = \ve_{ijk} \frac{\partial}{\partial x_i} \frac{\partial A_k}{\partial x_j} + \ve_{jik} \frac{\partial}{\partial x_j} \frac{\partial A_k}{\partial x_i} \\
& = \ve_{ijk} \frac{\partial}{\partial x_i} \frac{\partial A_k}{\partial x_j} - \ve_{ijk} \frac{\partial}{\partial x_i} \frac{\partial A_k}{\partial x_j} \\
& = 0 \\
\end{aligned}
$$

### 1.4.5 The curl of a curl

$$
\operatorname{curl}(\operatorname{curl} \mathbf{A})=\nabla(\operatorname{div} \mathbf{A})-\nabla^{2} \mathbf{A}
$$

**Proof**:

$$
\begin{aligned}
[\operatorname{curl}(\operatorname{curl} \mathbf{A})]_i & = \ve_{ijk} \frac{\partial}{\partial x_j} (\cu \vf)_k \\
& = \ve_{ijk} \frac{\partial}{\partial x_j}\left(\ve_{klm} \frac{\partial A_m}{\partial x_l}\right) \\
& = (\delta_{il} \delta_{jm} - \delta_{im}\delta_{jl}) (\frac{\partial}{\partial x_j} \frac{\partial A_j}{\partial x_l}) \\
& = \frac{\partial^2 A_j}{\partial x_j \partial x_i} - \frac{\partial^2 A_i}{\partial x_j \partial x_j} \\
& = \frac{\partial}{\partial x_i}\left(\frac{\partial \vf_j}{\partial x_j}\right) - \frac{\partial^2 A_i}{\partial x_j^2} \\
& = [\g(\d \vf)]_i - [\g^2 \vf]_i \\
\end{aligned}
$$

### 1.4.6. Scalar and vector fields

### Definition (Irrotational vector field)

If $$\vf$$ is a vector field such that $$\cu \vf = 0$$, then $$\mathbf{A}$$ is called an **irrotational vector field**.

### Definition (Solonoidal vector field)

If $$\mathbf{A}$$ is a vector field such that $$\d \vf = 0$$, then $$\mathbf{A}$$ is called a **solonoidal vector field**.

### Conclusion

$$
\begin{aligned}
\mathbf{r} & =x \mathbf{i}+y \mathbf{j}+z \mathbf{k} \\
\operatorname{div} \mathbf{r} & = 3\\
\operatorname{curl} \mathbf{r} & = 0\\
|\mathbf{r}| & =r=\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2} \\
\nabla r & =\nabla\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2} \\
& = \left(\frac{\partial}{\partial x}\nvi + \frac{\partial}{\partial y }\nvj + \frac{\partial}{\partial z}\nvk\right) \cdot \left(\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}\right) \\
& = \frac{x}{\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}} \nvi + \frac{y}{\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}} \nvj + \frac{z}{\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}} \nvk \\
& = (x \nvi + y \nvj + z \nvk) \frac{1}{\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}} \\
& = \frac{\mathbf{r}}{r} \\
& = \widehat{\mathbf{r}} \\
\end{aligned}
$$

### Example

Calculate

$$
\d^2 \left(\frac{1}{r}\right)
$$

**Solution**:

$$
\begin{aligned}
\d \left(\frac{1}{r}\right) & = \d (x^2 + y^2 + z^2)^{-1/2} \\
& = \left(\frac{\partial}{\partial x}\nvi + \frac{\partial}{\partial y}\nvj + \frac{\partial}{\partial z}\nvk\right) \cdot \left(\frac{1}{\left(x^{2}+y^{2}+z^{2}\right)^{1 / 2}}\right) \\
& = - (x \nvi + y \nvj + z \nvk) \frac{1}{\left(x^{2}+y^{2}+z^{2}\right)^{3 / 2}} \\
& = - \frac{\mathbf{r}}{r^3} \\
\end{aligned}
$$

$$
\begin{aligned}
\d^2 \left(\frac{1}{r}\right) & = - \left(\frac{\partial}{\partial x}\left(\frac{x}{(x^2+y^2+z^2)^{\frac{3}{2}}}\right) + \frac{\partial}{\partial y}\left(\frac{y}{(x^2+y^2+z^2)^{\frac{3}{2}}}\right) + \frac{\partial}{\partial z}\left(\frac{z}{(x^2+y^2+z^2)^{\frac{3}{2}}}\right)\right)  \\
& = -\frac{3}{(x^2 + y^2 z^2)^{\frac{3}{2}}} + \left(\frac{3x^2}{(x^2+y^2+z^2)^{\frac{5}{2}}} + \frac{3y^2}{(x^2+y^2+z^2)^{\frac{5}{2}}} + \frac{3z^2}{(x^2+y^2+z^2)^{\frac{5}{2}}}\right) \\
& = -\frac{3}{(x^2 + y^2 z^2)^{\frac{3}{2}}} + \frac{3}{(x^2+y^2+z^2)^{\frac{3}{2}}} \\
& = 0 \\
\end{aligned}
$$

Therefore, $$\d^2 (1/r) = 0$$, $$\frac{1}{r}$$ satisfies the **Laplace equation**: $$\d^2 \phi = 0$$.
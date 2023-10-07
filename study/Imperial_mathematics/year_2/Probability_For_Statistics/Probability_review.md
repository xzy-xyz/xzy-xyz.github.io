---
title: Probability Review
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
$$\gdef\bo{\mathcal{B}}$$

##### based on notes of [Dr. Chris Hallsworth](https://www.imperial.ac.uk/people/c.hallsworth) and lectcure of [Dr. Ciara Pike-Burke](https://www.ma.imperial.ac.uk/~cpikebur/)

#### Definition 1.1 (Experiment)

An **experiment** is any fixed procedure with a variable outcome.

#### Definition 1.2 (Sample Space)

The **sample space** is the set of possible outcomes of an experiment. We denote the sample space by $$\Omega$$.

#### Definition 1.3 (Event)

An **event** is a subset of the sample space. We denote an event by $$E$$.

#### Definition 1.4 (Algebra)

Let $$\F$$ be a collection of subsets of $$\Omega$$. $$\F$$ is said to be an algebra if

1. $$\varnothing \in \F$$.

2. If $$A \in \F$$ then $$A^{c} \in \F$$.

3. If $$A$$ and $$B \in \F$$ then $$A \cup B \in \F$$.

By induction, 3 implies that $$\F$$ is closed under finite unions, i.e.

$$
\text { if } A_{1}, A_{2}, \ldots, A_{n} \in \mathcal{F} \text {, then } \bigcup_{i=1}^{n} A_{i} \in \mathcal{F} \text {. }
$$

#### Definition 1.5 ($$\sigma$$-algebra)

If $$\F$$ is an algebra that is closed under countable unions, i.e.,

$$
\text { if } A_{1}, A_{2}, \cdots \in \mathcal{F} \text {, then } \bigcup_{i=1}^{\infty} A_{i} \in \mathcal{F} \text {. }
$$

then $$\F$$ is said to be a $$\sigma$$-algebra. An element of a $$\sigma$$-algebra $$\F$$ is said to be an **event**.

#### Exercise 1.6

Show that a $$\sigma$$-algebra is closed under countable intersections.

#### Example 1.7

For any set $$\Omega$$, the simplest $$\sigma$$-algebra is the trival one:

$$
\mathcal{F}_0=\{\varnothing, \Omega\}
$$

For any set $$\Omega$$, the power set of $$\Omega$$ is a $$\sigma$$-algebra, called the **discrete $$\sigma$$-algebra**.

#### Exercise 1.10 (An algebra that is not a $$\sigma$$-algebra)

Suppose $$\Omega = \N = \{1, 2, 3, \ldots\}$$ and $$\F = \{A \subset \N \mid A \text { is finite or } A^{c} \text { is finite }\}$$.

1. Identify a subset of $$\Omega$$ that lies in $$\mathcal{F}$$, and a subset that is not in $$\mathcal{F}$$.

2. Show that $$\mathcal{F}$$ is an algebra.

3. Show that $$\mathcal{F}$$ is not a sigma algebra.

#### Remark

When we work with uncountable sample spaces, we choose work with a smaller sigma algebra of events than the power set. To consider the impression of measurement, we at least want the open intervals in $$\R$$ to be events. To be previse about the sense in which our choice is smallest, we need the following propostion:

#### Proposition 1.12. (The intersection of sigma algebras is a sigma algebra)

Suppose $$\mathcal{F}_{i}, i \in I$$ is a non-empty collection of sigma algebras on a set $$\Omega$$. Then $$\cap_{i \in I} \mathcal{F}_{i}$$ is a sigma algebra.

**Proof**:

There are three properties to check.

1. Certainly $$\varnothing, \Omega \in \mathcal{F}_{i}$$ for each $$i \in I$$, so these sets are contained in the intersection.

2. If $$E \in \cap_{i \in I} \mathcal{F}_{i}$$ then for each $$i \in I, E \in \mathcal{F}_{i}$$, so $$E^{c} \in \mathcal{F}_{i} \forall i \in I$$. Hence $$E^{c} \in \cap_{i \in I} \mathcal{F}_{i}$$.

3. If $$E_{1}, E_{2}, \ldots \cap_{i \in I} \mathcal{F}_{i}$$, then for each $$i \in I$$, each set $$E_{j} \in \mathcal{F}_{i}$$, so $$\cup_{j=1}^{\infty} E_{j} \in$$ $$\cap_{i \in I} \mathcal{F}_{i}$$.

Hence $$\cap_{i \in I} \mathcal{F}_{i}$$ is a sigma algebra.

#### Definition 1.13. (Borel $$\sigma$$-algebra)

Let $$\F_i,i \in I$$ be a collection of all sigma algebras that contain all open intervals of $$\R$$. This collection is clearly non-empty, because the power set of $$\R$$ is such a sigma algebra. By Proposition 1.12, the intersection $$\F=\cap_{i \in I} \F_i$$ is a sigma algebra. The **Borel $$\sigma$$-algebra** is defined as

$$
\mathcal{B}=\bigcap_{i \in I} \mathcal{F}_{i}
$$


#### Remark 1.14

- $$\bo$$ contains all open intervals along with their complements, contable union and intersection.

- If $$\F$$ is any sigma algebra containing all open interval, then $$\bo \subset \F$$. It follows that $$\bo$$ is the smallest sigma algebra containing all open intervals.

- Sets in $$\bo$$ are called **Borel sets**.

- We will not attempt to define probabilities for subsets of $$\mathbb{R}$$ that are not in $$\mathcal{B}$$. It is extremely difficult to construct explicitly a set that is not in $$\mathcal{B}$$.

#### Examples 1.15 (Some Borel sets)

Using the properties of sigma algebras as needed, for $$a, b \in \mathbb{R}$$ and $$n \in \mathbb{N}$$, all sets of the following form are Borel sets.

- $$(a, \infty)=\bigcup_{n=1}^{\infty}(a, n)$$,

- $$[a, b]=((-\infty, a) \cup(b, \infty))^{c}$$,

- $$a=[a, a]$$,

- $$\mathbf{N}=\bigcup_{n=1}^{\infty}\{n\}$$.

#### Definition 1.16(Kolmogorov Axioms)

Given a set $$\Omega$$ and a sigma algebra $$\mathcal{F}$$ on $$\Omega$$, a probability function or probability measure is a function $$\operatorname{Pr}: \mathcal{F} \rightarrow[0,1]$$ such that 

1. $$\operatorname{Pr}(A) \geq 0$$, for all $$A \in \mathcal{F}$$.

2. $$\operatorname{Pr}(\Omega)=1$$.

3. Countable additivity: If $$A_{1}, A_{2}, \ldots \in \mathcal{F}$$ are pairwise disjoint, then $$\operatorname{Pr}\left(\bigcup_{i=1}^{\infty} A_{i}\right)=\sum_{i=1}^{\infty} \operatorname{Pr}\left(A_{i}\right)$$

#### Definition 1.17 (Probability Space)

The triple $$(\Omega, \mathcal{F}, \operatorname{Pr}(\cdot))$$, consisting of a sample space $$\Omega$$, a sigma algebra $$\mathcal{F}$$ of subsets of $$\Omega$$ and a probability function $$\operatorname{Pr}(\cdot)$$ on $$\mathcal{F}$$ is called a **probability space**.






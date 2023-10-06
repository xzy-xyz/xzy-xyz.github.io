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

based on notes and lectures by [Dr. Ciara Pike-Burke](https://www.ma.imperial.ac.uk/~cpikebur/)

#### Definition 1.1 (Experiment)

An **experiment** is any fixed procedure with a variable outcome.

#### Definition 1.2 (Sample Space)

The **sample space** is the set of possible outcomes of an experiment. We denote the sample space by $\Omega$.

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

#### Exercise 1.10 (An algebra that is not a $$\sigma$$-algebra)

Suppose $$\Omega = \N = \{1, 2, 3, \ldots\}$$ and $$\F = \{A \subset \N \mid A \text { is finite or } A^{c} \text { is finite }\}$$.

1. Identify a subset of $$\Omega$$ that lies in $$\mathcal{F}$$, and a subset that is not in $$\mathcal{F}$$.

2. Show that $$\mathcal{F}$$ is an algebra.

3. Show that $$\mathcal{F}$$ is not a sigma algebra.



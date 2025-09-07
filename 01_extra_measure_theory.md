---
marp: true
---

## Introduction to Measure Theory and Probability Theory

---
###  Introduction to Measure Theory and Probability Theory

Measure theory is a foundational branch of mathematics that generalizes the concepts of **length**, **area**, and **volume**. It provides a rigorous framework for integration and probability. In essence, it defines what can be "measured" within a given set.

Key questions measure theory addresses:
* How can we define the **"size"** of a set?
* How do we extend this concept from simple intervals or geometric shapes to more complex, abstract sets?
* How do we formalize probability and expectation?

---

###  What is a Sigma-Algebra?

A **sigma-algebra**, or $\sigma$-algebra, is a collection of subsets of a set $X$ that satisfy specific properties. It is denoted by $\Sigma$ (capital sigma). The pair $(X, \Sigma)$ is called a **measurable space**.

The purpose of a sigma-algebra is to define the sets for which we can assign a **measure**. These are the "measurable sets."

A collection of subsets $\Sigma$ of a set $X$ is a $\sigma$-algebra if it satisfies the following three conditions:
1.  **The empty set is in $\Sigma$**: $\emptyset \in \Sigma$.
2.  **It's closed under complementation**: If a set $A$ is in $\Sigma$, then its complement $A^c = X \setminus A$ is also in $\Sigma$.
3.  **It's closed under countable unions**: If a sequence of sets $A_1, A_2, A_3, \ldots$ are all in $\Sigma$, then their union $\bigcup_{i=1}^{\infty} A_i$ is also in $\Sigma$.

A direct consequence of these rules is that a $\sigma$-algebra is also closed under countable intersections.



---

###  The Borel Sigma-Algebra

The **Borel $\sigma$-algebra**, denoted by $\mathcal{B}$, is a crucial example. It's the **smallest $\sigma$-algebra** on the set of real numbers, $\mathbb{R}$, that contains all open intervals.

* **Generator**: The open intervals $(a, b)$ where $a, b \in \mathbb{R}$ generate the Borel $\sigma$-algebra.
* **Significance**: The Borel $\sigma$-algebra contains almost every set you'd encounter in analysis, including:
    * Open sets
    * Closed sets
    * Countable unions and intersections of these sets
* **Intuition**: The Borel $\sigma$-algebra is the collection of "well-behaved" subsets of $\mathbb{R}$ that we can hope to measure. 

---

### On the Borel Sigma-Algebra 

* Every individual point ${x}$ is a Borel set. This is because we can express a single point as the intersection of a decreasing sequence of open intervals:
  $${x} = \bigcap_{n=1}^{\infty} \left(x - \frac{1}{n}, x + \frac{1}{n}\right)$$
  Since each open interval is in the Borel $\sigma$-algebra, and $\sigma$-algebras are closed under countable intersections, the single point set ${x}$ is also in the Borel $\sigma$-algebra.

* Every interval of the form $(-\infty, a]$ is a Borel set. This is because we can express it as the intersection of a decreasing sequence of open intervals (similar to the above). 

In fact, we could have taken as basis for the Borel Sigma-Algebra the collection of all intervals of the form $(-\infty, a]$ for $a \in \mathbb{R}$.

---

###  What is a Measure?

A **measure** is a function $\mu$ that assigns a non-negative value (a "size" or "volume") to each set in a $\sigma$-algebra $\Sigma$.

For a measurable space $(X, \Sigma)$, a function $\mu: \Sigma \to [0, \infty]$ is a measure if it satisfies the following conditions:
1. $\mu(\emptyset) = 0$ (the measure of the empty set is zero).
1.  **Non-negativity**: $\mu(A) \ge 0$ for all $A \in \Sigma$.
2.  **Countable additivity**: For any countable collection of disjoint sets $A_1, A_2, A_3, \ldots$ in $\Sigma$, the measure of their union is the sum of their individual measures:
    $$\mu\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} \mu(A_i)$$

---

###  Key Examples of Measures

1.  **Lebesgue Measure** ($m$): This is the standard measure on the real numbers. It generalizes length.
    * For an interval $[a, b]$, its Lebesgue measure is $m([a,b]) = b-a$.
    * It's the foundation for Lebesgue integration, which is more powerful than Riemann integration.
1.  **Counting Measure**: This measure simply counts the number of elements in a set.
    * For a finite set $A$, the counting measure $\mu(A)$ is the number of elements in $A$, denoted $|A|$.
    * For an infinite set, the measure is $\infty$.

---

### Probability Space

**Probability Measure** ($P$): A probability measure is a measure where the total measure of the entire set is 1.
* For a sample space $\Omega$, the probability measure $P$ on the $\sigma$-algebra $\mathcal{F}$ satisfies $P(\Omega) = 1$.
* This formalizes the axioms of probability theory.

A probability space is a special case of a measure space where the measure is a probability measure: 

$(\Omega, \mathcal{F}, P)$, where $\Omega$ is the sample space, $\mathcal{F}$ is the sigma-algebra of events, and $P$ is the probability measure.

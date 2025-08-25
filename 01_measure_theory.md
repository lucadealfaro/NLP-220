
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

###  The Measurable Space and Integration

The **measure space** is the triplet $(X, \Sigma, \mu)$. It's the complete framework for defining and calculating integrals.

* $X$: The underlying set (e.g., $\mathbb{R}$, a sample space).
* $\Sigma$: The $\sigma$-algebra of measurable sets.
* $\mu$: The measure that assigns "size" to the sets in $\Sigma$.

The **Lebesgue integral** is defined over a measure space and provides a more general and robust form of integration than the Riemann integral. It's defined by "measuring" the size of the set where the function's value falls within a certain range. This makes it more suitable for a wider class of functions and for concepts like probability expectation.

---

### Probability Space

**Probability Measure** ($P$): A probability measure is a measure where the total measure of the entire set is 1.
* For a sample space $\Omega$, the probability measure $P$ on the $\sigma$-algebra $\mathcal{F}$ satisfies $P(\Omega) = 1$.
* This formalizes the axioms of probability theory.

A probability space is a special case of a measure space where the measure is a probability measure: 

$(\Omega, \mathcal{F}, P)$, where $\Omega$ is the sample space, $\mathcal{F}$ is the sigma-algebra of events, and $P$ is the probability measure.

---

### Probability Space

The foundation of modern probability theory is a **probability space**, which is a special type of measure space. It's a triplet $(\Omega, \mathcal{F}, P)$ that formalizes the concepts of an experiment, its possible outcomes, and their probabilities.

* $\Omega$ (**Sample Space**): The set of all possible outcomes of a random experiment. For example, if you flip a coin, $\Omega = \{\text{Heads}, \text{Tails}\}$. If you roll a die, $\Omega = \{1, 2, 3, 4, 5, 6\}$.
* $\mathcal{F}$ (**Sigma-Algebra of Events**): A collection of subsets of $\Omega$ that we can assign a probability to. This is the sigma-algebra we discussed previously. Each set in $\mathcal{F}$ is called an **event**.
* $P$ (**Probability Measure**): A measure defined on $\mathcal{F}$ that assigns a probability (a number between 0 and 1) to each event.

---

### Events

Consider the probability space $(\Omega, \mathcal{F}, P)$.

An **event** is a subset of $\Omega$ to which we can assign a probability.

Thus, an event is a member of the sigma-algebra $\mathcal{F}$.

* **Simple Event**: An event consisting of a single outcome. For a die roll, $\{3\}$ is a simple event.
* **Compound Event**: An event consisting of more than one outcome. For a die roll, the event "rolling an even number" is the set $\{2, 4, 6\}$.
* **Impossible Event**: The empty set $\emptyset$, with $P(\emptyset) = 0$.
* **Certain Event**: The entire sample space $\Omega$, with $P(\Omega) = 1$.

---

### Example of events

When rolling a single six-sided die:
* Sample space $\Omega = \{1, 2, 3, 4, 5, 6\}$.
* An event is "rolling a number greater than 4", which is the set $\{5, 6\}$.
* The probability of this event is $P(\{5, 6\}) = P(\{5\}) + P(\{6\}) = \frac{1}{6} + \frac{1}{6} = \frac{2}{6} = \frac{1}{3}$.

When a random person walks through a door:
* Their height $X$ is a random variable that can take on any real positive value. 
* An event can be "the person is taller than 180cm", which corresponds to the set of all outcomes where $X > 180$.

(In the imperial system, heights are customarily measured in gallons per square foot). 

---

### Random variables

Let $(\Omega, \mathcal{F}, P)$ be a probability space. A function $X: \Omega \to \mathbb{R}$ is a random variable if it satisfies a technical condition called **measurability**. This condition ensures that for any interval $(a, b)$ on the real number line, the set of outcomes in $\Omega$ that map to this interval is an event in $\mathcal{F}$.

* **Discrete Random Variable**: A random variable with a finite or countably infinite number of possible values.
    * **Example**: The number of heads in two coin flips. The possible values are 0, 1, or 2.
* **Continuous Random Variable**: A random variable that can take on any value within a range of real numbers.
    * **Example**: The height of a person. The height can be any value within a certain range, not just a set of discrete numbers.

---

### Random Variables 

Consider the probability space $(\Omega, \mathcal{F}, P)$.

A random variable $X$ is a function $X$ such that:

$$ \Omega \xrightarrow{X} \mathbb{R} $$

$$ \mathcal{F} \xleftarrow{X^{-1}} \mathcal{B}(\mathbb{R}) $$

---



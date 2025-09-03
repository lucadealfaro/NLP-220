---
marp: true
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

Let $(\Omega, \mathcal{F}, P)$ be a probability space. A function $X: \Omega \to \mathbb{R}$ is a random variable if, for any open interval $(a, b) \subseteq \mathbb{R}$, the preimage $X^{-1}((a, b)) is an event in $\mathcal{F}$.

$$ \Omega \xrightarrow{X} \mathbb{R} $$

$$ \mathcal{F} \xleftarrow{X^{-1}} \mathcal{B}(\mathbb{R}) $$

So you can measure the probability of the random variable falling within any interval $(a, b)$.

---

### Discrete and continuous random variables

* **Discrete Random Variable**: A random variable with a finite or countably infinite number of possible values.
    * **Example**: The number of heads in two coin flips. The possible values are 0, 1, or 2.
* **Continuous Random Variable**: A random variable that can take on any value within a range of real numbers.
    * **Example**: The height of a person. The height can be any value within a certain range, not just a set of discrete numbers.

---

### Independence

Two events $A$ and $B$ in a probability space $(\Omega, \mathcal{F}, P)$ are said to be **independent** if the occurrence of one event does not affect the probability of the occurrence of the other event. Formally, $A$ and $B$ are independent if:

$$ P(A \cap B) = P(A) \cdot P(B) $$

This means that the probability of both events happening together is equal to the product of their individual probabilities.

> **Independence means multiply!**

---

### Independence of Random Variables

Two random variables $X$ and $Y$ defined on the same probability space $(\Omega, \mathcal{F}, P)$ are said to be **independent** if for every pair of Borel sets $A, B \in \mathcal{B}(\mathbb{R})$, the events $\{X \in A\}$ and $\{Y \in B\}$ are independent. Formally, $X$ and $Y$ are independent if:

$$ P(X \in A, Y \in B) = P(X \in A) \cdot P(Y \in B) $$

---

### Expectation

The **expectation** (or expected value) of a random variable $X$, denoted by $E[X]$, is the "average" value of $X$:

$$E[X] = \int_{\Omega} X(\omega) dP(\omega) $$

For a discrete random variable $X$ with values $a_1, a_2, \ldots$ and probabilities $p_1, p_2, \ldots$, the expectation is:

$$ E[X] = \sum_{i} a_i \cdot P(X = a_i) = \sum_{i} a_i p_i $$

---

### Linearity of Expectation

The expectation operator is linear, meaning that for any random variables $X$ and $Y$, and any constants $a$ and $b$, the following holds:

$$ E[aX + bY] = aE[X] + bE[Y]$$

---

### Expectation of product of independent random variables

If $X$ and $Y$ are independent random variables, then the expectation of their product is the product of their expectations:

$$ E[XY] = E[X] \cdot E[Y] $$
---

### Variance and Covariance

$$Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$$

$$Cov(X, Y) = E[(X - E[X])(Y - E[Y])] = E[XY] - E[X]E[Y]$$

### Standard deviation

$$\sigma(X) = \sqrt{Var(X)}$$

---

### Variance and independence

If $X$ and $Y$ are independent:

$$Cov(X, Y) = 0$$

$$Var(X + Y) = Var(X) + Var(Y)$$

**Very important.  Remember this.**

---

Proof: 
$$Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$$

So:
$$Var(X + Y) = E[(X + Y)^2] - (E[X + Y])^2$$

One piece at a time: 
$$E[(X + Y)^2] = E[X^2 + 2XY + Y^2] = E[X^2] + 2E[XY] + E[Y^2]$$
$$(E[X + Y])^2 = (E[X] + E[Y])^2 = (E[X])^2 + 2E[X]E[Y] + (E[Y])^2$$

But $E[XY] = E[X]E[Y]$ if $X$ and $Y$ are independent, and so: 

$$E[(X + Y)^2] - (E[X + Y])^2 = E[X^2] + E[Y^2] - (E[X])^2 - (E[Y])^2$$
$$= Var(X) + Var(Y)$$

---
### Slide 4: Putting it All Together
Now, let's substitute the expanded terms back into the variance equation:
$Var(X + Y) = (E[X^2] + 2E[XY] + E[Y^2]) - ((E[X])^2 + 2E[X]E[Y] + (E[Y])^2)$
$Var(X + Y) = E[X^2] - (E[X])^2 + E[Y^2] - (E[Y])^2 + 2E[XY] - 2E[X]E[Y]$
We can group the terms to recognize the individual variances:
$Var(X + Y) = [E[X^2] - (E[X])^2] + [E[Y^2] - (E[Y])^2] + 2(E[XY] - E[X]E[Y])$
$Var(X + Y) = Var(X) + Var(Y) + 2(E[XY] - E[X]E[Y])$

---
### Slide 5: The Role of Independence
This is where the **independence** of $X$ and $Y$ becomes crucial.
For **independent random variables**, the expected value of their product is the product of their expected values:
$E[XY] = E[X]E[Y]$
Let's substitute this into our previous equation:
$Var(X + Y) = Var(X) + Var(Y) + 2(E[X]E[Y] - E[X]E[Y])$
$Var(X + Y) = Var(X) + Var(Y) + 2(0)$
$Var(X + Y) = Var(X) + Var(Y)$

---
### Slide 6: Conclusion
We have successfully proven that the **variance of the sum of two independent random variables** is the **sum of their variances**. This property is incredibly useful in statistics and probability theory, especially in areas like the **Central Limit Theorem** and **statistical inference**. It simplifies the calculation of the spread of a combined random process when the individual components don't influence each other. 

---

### Standard deviation of repeated experiments

Imagine you repeat $N$ times an experiment, with outcome $X_i$, $1 \leq i \leq N$.  You compute the average outcome: 

$$E[X] = \frac{1}{N} \sum_{i=1}^N X_i$$

The variance of the average is:

$$Var(E[X]) = Var\left(\frac{1}{N} \sum_{i=1}^N X_i\right) = \frac{1}{N^2} \sum_{i=1}^N Var(X_i) = \frac{1}{N} Var(X)$$

And the standard deviation is: 

$$\sigma(E[X]) = \frac{1}{\sqrt{N}} \sigma(X)$$

So the precision improves with the square root of the number of experiments.

---

### Sample Variance vs. Population Variance

When computing the variance as: 

$$Var(X) = E[(X - E[X])^2] = \min_{\mu} E[(X - \mu)^2]$$

we are computing the **population variance**.
This in a way underestimates the variance, because it assumes the mean $E[X]$ is known exactly.

But normally we don't know $E[X]$ exactly, we only have a sample of $N$ values $X_i$, $1 \leq i \leq N$.

---

### Population and Sample Variance

The **population variance** is computed as:

$$Var(X) = E[(X - E[X])^2] = \frac{1}{N} \sum_{i=1}^N (X_i - E[X])^2$$


The **sample variance** is computed as:

$$S^2 = \frac{1}{N-1} \sum_{i=1}^N (X_i - E[X])^2$$

---

### Probability Distribution Function (PDF)

A **probability distribution function** (PDF) describes how the values of a random variable are distributed. It provides the probabilities of different outcomes for both discrete and continuous random variables.

* For a **discrete random variable**, the PDF is often called the **probability mass function** (PMF). It assigns a probability to each possible value of the random variable.
    * Example: For a fair six-sided die, the PMF is:
      $$ P(X = k) = \frac{1}{6} \quad \text{for } k = 1, 2, 3, 4, 5, 6 $$

* For a **continuous random variable**:

$$ P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx $$

---

### Properties of a PDF

A valid probability distribution function (PDF) must satisfy the following properties:

1.  **Non-negativity**: $f(x) \geq 0$ for all $x$ in the domain of $X$.
2.  **Normalization**: The total area under the PDF curve must equal 1:
    $$ \int_{-\infty}^{\infty} f(x) \, dx = 1 $$

---

### Cumulative Distribution Function (CDF)

The **cumulative distribution function** (CDF) of a random variable $X$, denoted by $F(x)$, gives the probability that $X$ will take a value less than or equal to $x$. It is defined as:

$$ F(x) = P(X \leq x) $$

For a continuous random variable, the CDF is related to the PDF by:

$$ F(x) = \int_{-\infty}^{x} f(t) \, dt $$

---


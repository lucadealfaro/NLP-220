---
marp: true
paginate: true
---

## Introduction to Probability Theory

### Luca de Alfaro, UC Santa Cruz

---

### Probability Space

The foundation of probability theory is a **probability space**: a triplet $(\Omega, \mathcal{F}, P)$, where: 

* $\Omega$ (**Sample Space**): The set of all possible outcomes of a random experiment. For example, if you flip a coin, $\Omega = \{\text{Heads}, \text{Tails}\}$. If you roll a die, $\Omega = \{1, 2, 3, 4, 5, 6\}$.
* $\mathcal{F}$ (**Sigma-Algebra of Events**): A collection of subsets of $\Omega$ that we can assign a probability to. Each set in $\mathcal{F}$ is called an **event**.
* $P$ (**Probability Measure**): A measure defined on $\mathcal{F}$ that assigns a probability (a number between 0 and 1) to each event.

---

### Examples of Probability Spaces

1. **Flipping a Coin**:
   * $\Omega = \{\text{Heads}, \text{Tails}\}$
   * $\mathcal{F} = \{\emptyset, \{\text{Heads}\}, \{\text{Tails}\}, \{\text{Heads}, \text{Tails}\}\}$
   * $P(\{\text{Heads}\}) = 0.5$, $P(\{\text{Tails}\}) = 0.5$, $P(\emptyset) = 0$, $P(\{\text{Heads}, \text{Tails}\}) = 1$

---

### Examples of Probability Spaces

2. **Rolling a Die**:
   * $\Omega = \{1, 2, 3, 4, 5, 6\}$
   * $\mathcal{F}$ includes all subsets of $\Omega$ (the power set of $\Omega$).
   * $P(\{k\}) = \frac{1}{6}$ for each $k \in \{1, 2, 3, 4, 5, 6\}$.
   * For $A \subseteq \Omega$, $P(A) = \frac{|A|}{6}$.

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

### Continuous Sample Spaces

The sample space $\Omega$ can be more complex.  Of particular interest to us, $\Omega$ can be the set of real numbers $\mathbb{R}$, or the set of $n$-dimensional vectors $\mathbb{R}^n$.

In the case of $\Omega = \mathbb{R}$, the sigma-algebra $\mathcal{F}$ of measurable sets is the **Borel sigma-algebra** $\mathcal{B}(\mathbb{R})$, which includes: 

* all open intervals, and 
* all the sets that can be constructed from open intervals using countable unions, countable intersections, and complements.

---

### Random variables

Let $(\Omega, \mathcal{F}, P)$ be a probability space. A function $X: \Omega \to \mathbb{R}$ is a random variable if, for any open interval $(a, b) \subseteq \mathbb{R}$, the preimage $X^{-1}((a, b)) is an event in $\mathcal{F}$.

$$ \Omega \xrightarrow{X} \mathbb{R} $$

$$ \mathcal{F} \xleftarrow{X^{-1}} \mathcal{B}(\mathbb{R}) $$

**In practice this means:** $X$ is a random variable if you can measure the probability of the random variable falling within any interval $(a, b)$.

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

<br>

$$Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$$

<br>

$$Cov(X, Y) = E[(X - E[X])(Y - E[Y])] = E[XY] - E[X]E[Y]$$

<br>

### Standard deviation

$$\sigma(X) = \sqrt{Var(X)}$$

---

### Computing statistics of stream data

$$E[X] = \frac{1}{N} \sum_{i=1}^N X_i$$

$$Var(X) = \frac{1}{N} \sum_{i=1}^N (X_i - E[X])^2 = \frac{1}{N} \sum_{i=1}^N X_i^2 - (E[X])^2$$

So it suffices to remember: 

* $N$
* $\sum_{i=1}^N X_i$
* $\sum_{i=1}^N X_i^2$

---

### Discounted statistics of streaming data

If you have streaming data, and want to emphasize recent data, you can use **discounted statistics**.  For a discount factor $0 < \alpha < 1$, you compute:

$$E_\alpha[X] = (1 - \alpha) \sum_{i=0}^{\infty} \alpha^i X_{N-i}$$

$$Var_\alpha(X) = (1 - \alpha) \sum_{i=0}^{\infty} \alpha^i (X_{N-i} - E_\alpha[X])^2$$

---

### Incremental computation of discounted statistics

<br>

$$S := \alpha S + X$$

$$Q := \alpha Q + X^2$$

$$W := \alpha W + 1$$

<br>

$$E_\alpha[X] = \frac{S}{W} \qquad \qquad E_\alpha[X^2] = \frac{Q}{W} - E^2_\alpha[X]$$

---

### Some properties of variance

<br>

$$Var(aX) = a^2 Var(X)$$

Proof:

$$Var(aX) = E[(aX - E[aX])^2] = E[(aX - aE[X])^2] = E[a^2(X - E[X])^2] = a^2 Var(X)$$

<br>
<br>

$$Var(X + a) = Var(X)$$

(prove it).

---

### Variance and independence

If $X$ and $Y$ are independent:

$$Cov(X, Y) = 0$$

$$Var(X + Y) = Var(X) + Var(Y)$$

**Very important.  Remember this.**

---

### Proof: (part 1) 
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
### Proof: (part 2)

Let's substitute the expanded terms back into the variance equation:
$Var(X + Y) = (E[X^2] + 2E[XY] + E[Y^2]) - ((E[X])^2 + 2E[X]E[Y] + (E[Y])^2)$
$Var(X + Y) = E[X^2] - (E[X])^2 + E[Y^2] - (E[Y])^2 + 2E[XY] - 2E[X]E[Y]$
We can group the terms to recognize the individual variances:
$Var(X + Y) = [E[X^2] - (E[X])^2] + [E[Y^2] - (E[Y])^2] + 2(E[XY] - E[X]E[Y])$
$Var(X + Y) = Var(X) + Var(Y) + 2(E[XY] - E[X]E[Y])$

---
### Proof: (part 3)

This is where the **independence** of $X$ and $Y$ becomes crucial.
For **independent random variables**, the expected value of their product is the product of their expected values:
$E[XY] = E[X]E[Y]$
Let's substitute this into our previous equation:
$Var(X + Y) = Var(X) + Var(Y) + 2(E[X]E[Y] - E[X]E[Y])$
$Var(X + Y) = Var(X) + Var(Y) + 2(0)$
$Var(X + Y) = Var(X) + Var(Y)$

---

### Conclusion

We have successfully proven that the **variance of the sum of two independent random variables** is the **sum of their variances**. 

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


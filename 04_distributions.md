---
marp: true
paginate: true
---

## Some Noteworthy Distributions
### Luca de Alfaro, UC Santa Cruz

---

### Exponential distribution

Consider an event that occurs continuously and independently at a constant average rate, $\lambda$. The **exponential distribution** describes the time before its first occurrence. It is defined by the probability density function (PDF) $p(t)$, which gives the likelihood of the event occurring at time $t$. 

We derive first $P(t)$, which is the probability that the event has **not** occurred by time $t$.

---

$$P(t + \Delta t) = P(t) \cdot (1 - \lambda \Delta t)$$
$$\frac{P(t + \Delta t) - P(t)}{\Delta t} = -\lambda P(t)$$

For $\Delta t \to 0$, this becomes the differential equation $\dot{P}(t) = -\lambda P(t)$, which has solution: 

$$P(t) = e^{-\lambda t}$$

For the probability of the event occurring at time $t$ exactly, we have: 

$$p(t) = -\frac{dP(t)}{dt} = \lambda e^{-\lambda t}$$

---

### Poisson distribution

A Poisson process models a series of random, independent events occurring at a constant average rate, $\lambda$.
* The **exponential distribution** gives the probability of the waiting time between consecutive events.
* The **Poisson distribution** gives the probability of a given number of events occurring in a fixed time interval.

---

### Applications of Poisson distribution

Some examples: 

**Ecology.**  You know that in a region, the density of individuals for a given species of bird is such that a birdwatcher will will see $\alpha$ birds every hour.  In time $t$, what is the probability that $n$ birds will be seen?  

Call this $P(n \mid \alpha)$. 

Then, if you have a prior on $\alpha$, you can update it using Bayes via: 

$$P(\alpha \mid n) \propto P(n \mid \alpha) P(\alpha)$$

Note that $P(n \mid \alpha) = Poisson(n, \alpha t)$. 

---

The distribution: 

$$Poisson(k, \lambda) = P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

where $\lambda$ is the average number of events in the interval, and $k$ is the actual number of events that occur.

---

### First derivation of the Poisson Distribution

The Poisson distribution can be derived as a limiting case of the binomial distribution under specific conditions.

The derivation starts with the **binomial distribution**, which models the number of successes in a fixed number of independent trials. The probability of $k$ successes in $n$ trials with probability $p$ is given by:

$P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$

Now, we introduce the conditions for the Poisson approximation:
* The number of trials, $n$, becomes very large ($n \to \infty$).
* The probability of success in a single trial, $p$, becomes very small ($p \to 0$).
* The product of $n$ and $p$, which represents the average number of successes, remains constant. We call this average rate $\lambda$ (lambda), so $\lambda = np$.

---

From $\lambda = np$, we have $p = \frac{\lambda}{n}$.

We substitute this into the binomial probability mass function and take the limit as $n \to \infty$.

$P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$

$P(X=k) = \lim_{n \to \infty} \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1-\frac{\lambda}{n}\right)^{n-k}$

Let's break down each part of this expression.

---

### Part 1: The binomial coefficient

The binomial coefficient $\binom{n}{k}$ can be written as $\frac{n!}{k!(n-k)!}$.
We can rewrite this as:
$\frac{n(n-1)(n-2)...(n-k+1)}{k!}$

As $n \to \infty$, the terms $n-1, n-2, ..., n-k+1$ all approach $n$. Therefore, the numerator approaches $n^k$.

So, $\lim_{n \to \infty} \frac{n(n-1)...(n-k+1)}{k!} = \frac{n^k}{k!}$

---

### Part 2: The probability term

The term $(\frac{\lambda}{n})^k$ can be written as $\frac{\lambda^k}{n^k}$.

### Part 3: The exponential term

We need to evaluate the limit of the term $(1-\frac{\lambda}{n})^{n-k}$. We can split this into two parts:

$\lim_{n \to \infty} (1-\frac{\lambda}{n})^{n-k} = \lim_{n \to \infty} (1-\frac{\lambda}{n})^n \cdot \lim_{n \to \infty} (1-\frac{\lambda}{n})^{-k}$

The first part, $\lim_{n \to \infty} (1-\frac{\lambda}{n})^n$, is a standard limit that evaluates to $e^{-\lambda}$.

The second part, $\lim_{n \to \infty} (1-\frac{\lambda}{n})^{-k}$, approaches $(1-0)^{-k} = 1^{-k} = 1$.

So, the whole exponential term approaches $e^{-\lambda} \cdot 1 = e^{-\lambda}$.

---

**Combining all the parts**

Now, we multiply the simplified parts together:

$P(X=k) = \left(\frac{n^k}{k!}\right) \cdot \left(\frac{\lambda^k}{n^k}\right) \cdot (e^{-\lambda})$

The $n^k$ terms cancel out, leaving us with the final form of the **Poisson distribution**:

$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$

This is the probability of observing exactly $k$ events in a fixed interval, where $\lambda$ is the average number of events in that interval.

---

### Second derivation of the Poisson Distribution

We can derive the Poisson probability mass function also in an alternative fashion, by solving a differential equation that describes how the probability of having a certain number of events changes over time.

Let $P_k(t)$ be the probability of having exactly $k$ events in a time interval of length $t$. Our goal is to find a formula for $P_k(t)$.

The derivation relies on three fundamental assumptions of a Poisson process:
1.  The probability of a single event in a very small time interval $\Delta t$ is approximately $\lambda \Delta t$.
2.  The probability of two or more events in $\Delta t$ is negligible ($\rightarrow 0$ faster than $\Delta t$).
3.  Events are independent.

---

Consider the probability of having $k$ events in the interval $[0, t + \Delta t]$. This can happen in two mutually exclusive ways:
* You had **$k$ events** in $[0, t]$ AND **no events** in $[t, t+\Delta t]$.
* You had **$k-1$ events** in $[0, t]$ AND **one event** in $[t, t+\Delta t]$.

We can write this as an equation:
$P_k(t + \Delta t) \approx P_k(t) \cdot (1 - \lambda \Delta t) + P_{k-1}(t) \cdot (\lambda \Delta t)$

Now, we rearrange the terms to form a differential equation.

$\frac{P_k(t+\Delta t) - P_k(t)}{\Delta t} = -\lambda P_k(t) + \lambda P_{k-1}(t)$

Taking the limit as $\Delta t \to 0$ gives us a system of differential equations:

$\frac{d P_k(t)}{dt} = -\lambda P_k(t) + \lambda P_{k-1}(t)$

We solve this system iteratively for $k=0, 1, 2, ...$

---

#### Step 1: Solving for $k=0$ events

The equation becomes: $\frac{d P_0(t)}{dt} = -\lambda P_0(t)$.
The solution to this first-order linear differential equation is of the form $P_0(t) = C e^{-\lambda t}$.
We know that at $t=0$, there are no events with certainty, so $P_0(0) = 1$. This implies $C = 1$.
Therefore, $P_0(t) = e^{-\lambda t}$.
This is the survival function of the exponential distribution, which confirms the probability of waiting longer than time $t$ for the first event.

---

#### Step 2: Solving for $k=1$ event

Using the result for $P_0(t)$, the equation for $k=1$ is:
$\frac{d P_1(t)}{dt} = -\lambda P_1(t) + \lambda e^{-\lambda t}$
This can be solved using an integrating factor. The solution is:
$P_1(t) = (\lambda t)e^{-\lambda t}$

---

#### Step 3: Solving for $k=2$ events

Substituting the result for $P_1(t)$, the equation for $k=2$ is:
$\frac{d P_2(t)}{dt} = -\lambda P_2(t) + \lambda [(\lambda t)e^{-\lambda t}]$
Solving this yields:
$P_2(t) = \frac{(\lambda t)^2}{2}e^{-\lambda t}$

---

#### General solution

A pattern emerges. By mathematical induction, the general solution for any $k$ is:

$P_k(t) = \frac{(\lambda t)^k e^{-\lambda t}}{k!}$

Let $\mu = \lambda t$ represent the average number of events in the time interval $t$. Substituting this into the equation gives us the final form of the Poisson probability mass function:

$P(X=k) = \frac{\mu^k e^{-\mu}}{k!}$

---

### The Binomial Distribution

Imagine you have a random coin with **bias** $p$ (the probability of heads). You flip it $n$ times.  What is the probability of getting exactly $k$ heads?

The answer is given by the **binomial distribution**:

$$Binomial(k, n, p) = P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$$

where 

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$ 

is the binomial coefficient, which counts the number of ways to choose $k$ successes (heads) from $n$ trials (flips).

---

### The Bernoulli Distribution

Imagine someone gives you a coin.  It might well be biased, with probability $p$ of heads.  So you want to test it.  To do so, you flip it $n$ times, and get $k$ heads. 

What is the bias $p$ of the coin? 

Let: 

$$P(X=H) = p$$

$$P(p=x) = Q(x)$$

Here, $Q$ is the probability distribution over the **bias** $p$ of the coin. 

---

### Bernoulli distribution (cont.)

Initially, we know nothing about the coin. 
The least-knowledge assumption we can make on its prior is that $Q(p=x) = 1$ for $x \in [0,1]$; in other words, all bias values are equally likely.
(Note: for a metal coin this would be unreasonable.  But if the coin models an experiment with boolean outcome of unknown rate, this is very reasonable). 

---

### Bernoulli distribution (cont.)

Prior: $Q(p=x) = 1$ for $x \in [0,1]$.

Suppose we see an $H$ (head).  We can use Bayes' theorem to update our belief about $p$:

$$P(p=x \mid H) \propto P(H \mid p=x) Q(p=x) = x \cdot 1$$

If we then see another head, we can update again:

$$P(p=x \mid HH) \propto P(H \mid p=x) P(p=x \mid H) \propto x \cdot x \cdot 1 = x^2$$

If after this we see a Tail, we have: 

$$P(p=x \mid THH) \propto P(T \mid p=x) P(p=x \mid HH) \propto (1-x) \cdot x^2 \cdot 1 = x^2(1-x)$$

---

### Bernoulli distribution (cont.)

In general, if you see $k$ heads and $n-k$ tails, you have:

$$P(p=x \mid kH, (n-k)T) \propto x^k (1-x)^{n-k}$$

This is called the **Beta distribution** with parameters $\alpha = k+1$ and $\beta = n-k+1$.  Why the $+1$?  I truly wonder too.  

The Beta distribution is a conjugate prior for the Bernoulli distribution, which means that if your prior on $p$ is a Beta distribution, and you observe Bernoulli trials, your posterior on $p$ will also be a Beta distribution.

---

### Bernoulli distribution and crowdsourcing

Suppose you have a sentence, and you ask 10 people whether it is true or false.  8 say true, 2 say false. What can you say? 

You can model it via a Bernoulli distribution, with $k=8$ and $n=10$.  The posterior on the truth of the sentence is then a Beta distribution with parameters $\alpha = 9$ and $\beta = 3$.

You get: 

Mean: $E[p] = \frac{\alpha}{\alpha + \beta} = \frac{9}{12} = 0.75$

Variance: $Var(p) = \frac{\alpha \beta}{(\alpha + \beta)^2 (\alpha + \beta + 1)} = \frac{9 \cdot 3}{12^2 \cdot 13} = 0.0144$. 

So you can say that the sentence is true with probability 0.75, with a standard deviation of 0.12. Having a measure of uncertainty is very useful! You can prioritize checking sentences with high uncertainty.

---

### Gaussian distribution

The **Gaussian distribution** (or normal distribution) is a continuous probability distribution characterized by its bell-shaped curve. It is defined by two parameters: 
* $\mu$: the mean
* $\sigma$: the standard deviation

The probability density function (PDF) of a Gaussian distribution is given by:

$$p(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$$

---

### Gaussian distribution

The Gaussian distribution importance is due to the **Central Limit Theorem**, which states that the sum of a large number of independent random variables, regardless of their individual distributions, will tend to follow a Gaussian distribution.

Moreover, in a sense that can be made precise, the Gaussian distribution is the maximum entropy distribution for a given mean and variance.
This means that, among all distributions with a specified mean and variance, the Gaussian distribution is the one that makes the fewest assumptions about the data beyond those constraints.

---

### Gaussian distribution: properties

There is a further aspect that makes the Gaussian distribution special.  Consider a Gaussian distribution with mean 0: 

$$p(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{x^2}{2\sigma^2}}$$

Its Fourier transform is:

$$\hat{p}(\omega) = e^{-\frac{\sigma^2 \omega^2}{2}}$$

which is also a Gaussian distribution, with mean 0 and standard deviation $1/\sigma$.

So if the Gaussian distribution is the maximal-entropy distribution in the space domain, it is also the maximal-entropy distribution in the frequency domain.  No other distribution has this property.

---

### An aside on Gaussian distributions and Darwin - Mendel evolution

Darwin's theory of evolution by natural selection was inspired by the work of Gregor Mendel on genetics.  Mendel discovered that traits are inherited in discrete units (genes), and that the combination of these genes from parents leads to variation in offspring.

Initially, a strong objection to Darwin's theory was that if traits were inherited in discrete units, how could the continuous variation observed in nature be explained?

For example: why is human height distributed continuously, more or less in Gaussian fashion, rather than in discrete steps?

The resolution to this paradox came with the understanding that many traits are influenced by multiple genes, each contributing a small effect. This is known as polygenic inheritance. When multiple genes contribute to a trait, the combined effect can produce a Gaussian distribution of phenotypes, due to the central limit theorem.



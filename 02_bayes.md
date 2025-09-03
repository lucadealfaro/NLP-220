---
marp: true
---

## Conditional Probability and Bayes' Theorem

---

### Joint Probability

**Joint Probability** is the probability of two events happening at the same time. It is denoted as 

$$P(A \cap B)$$ 

or 

$$P(A, B)$$

If $A$ and $B$ are independent events, then $P(A \cap B) = P(A) \cdot P(B)$.

---

### Conditional Probability 

**Conditional Probability** is the probability of an event occurring given that another event has already occurred:

$$ P(A|B) = \frac{P(A \cap B)}{P(B)} $$

Note that if $A$ and $B$ are independent, then $P(A|B) = P(A)$.

---

### Bayes' Theorem

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

Interpretation:

* $A$ is some "state of reality" that we want to know about.
* $B$ is some observation we can make.

---

### Bayes' Theorem

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

Use: 

* $P(A)$: probability of $A$ if we know nothing else.  This is called the **prior** probability of $A$ (prior = before we see other things).
* $P(B|A)$: if $A$ is true, how likely is the observation $B$?  This is called the **likelihood** of $B$ given $A$, and is often easy to estimate from the state of reality $A$. 
* $P(A|B)$: how likely is $A$, given that we have seen $B$? This is called the **posterior** probability of $A$ (posterior = after we see other things).

Thus, Bayes' theorem is an update rule, telling us how to update $P(A)$ to $P(A|B)$ after seeing $B$.

---

### How Bayes' theorem is often used in practice

Assume $A$ has various possible values, $a_1, a_2, \ldots, a_N$. 

$$P(A = a_i | B) \propto P(B|A=a_i) \cdot P(A=a_i)$$

One computes $P(A = a_i | B)$ for all $a_i$, and then normalizes so that the probabilities sum to 1.

---

### Example: Crowdsourcing

Is $A$ fake news?  Two values for $A$: $T$ and $F$. 

Prior: $P(A=T) = 0.8$, $P(A=F) = 0.2$.

Moderators: 

* For true news: $P(B=T|A=T) = 0.9$, $P(B=F|A=T) = 0.1$.
* For fake news: $P(B=T|A=F) = 0.3$, $P(B=F|A=F) = 0.7$.

A moderator tells us $B=F$.  Then: 

$$P(A=T|B=F) \propto P(B=F|A=T) \cdot P(A=T) = 0.1 \cdot 0.8 = 0.08$$
$$P(A=F|B=F) \propto P(B=F|A=F) \cdot P(A=F) = 0.7 \cdot 0.2 = 0.14$$

Normalize: $P(A=T|B=F) = 0.08/(0.08+0.14) = 0.36$, $P(A=F|B=F) = 0.14/(0.08+0.14) = 0.64$.

---

### Example: Medical Diagnosis

A person goes to the doctor, and a blood test comes up positive for disease $D$. 

The blood test is 99% accurate.

But the disease is rare: only 1 in 1,000,000 people have it.

What is the probability that the person actually has the disease?

---

### Back-of-the-envelope solution (often good enough)

Take 1,000,000 people. 

10 will have the disease. 

10,000 will have a positive test outcome. 

So the probability of having $D$ after a positive test is still 1/1000. 
This is called the **base rate fallacy**: ignoring the prior probability of $D$.

Even crazier: if you repeat the test, and it **again** comes up positive, the probability of having $D$ is still only about 1/10.

This also tells us: **it's hard to detect a rare event, with a test that has higher positive rate than the event positive rate.**

---

### Exact solution using Bayes' theorem

$P(D) = 10^{-5}$. 
$P(T|D) = 0.99$.
$P(T|\neg D) = 0.01$.

$P(D|T) \propto P(T|D) \cdot P(D) = 0.99 \cdot 10^{-5} = 9.9 \cdot 10^{-6}$.
$P(\neg D|T) \propto P(T|\neg D) \cdot P(\neg D) \approx 10^-2$.

P(D|T) $\approx 9.9 \cdot 10^{-6}/(9.9 \cdot 10^{-6} + 10^{-2}) \approx 0.99 \cdot 10^{-3}$.

(The "back-of-the-envelope" solution was $10^{-3}$.)





---
marp: true
paginate: true
---

## A Primer on Information Theory
### Luca de Alfaro, UC Santa Cruz

---

### How to Measure Information?

When one sends a message, one conveys information.  How to measure it? 

Assume that we are using the usual ASCII alphabet.  
And assume that all I send are 'a's. 

As in, 

    aaaaa... 

forever.  Well, then clearly, I cannot communicate very much. 

---

### How to Measure Information?

Assume now that I splurge, and I decide I can send both 'a' and 'b'.  Consider the difference between these two cases: 

1.  I send mostly 'a's, but quite rarely I send a 'b'.

    aaaaaaaabaaaaa... ...aaaaaabaaaa

2.  I send 'a's and 'b's with equal frequency.

    abbabbaababbab... ...baababbaab

Am I sending the same amount of information? 

---

1.  I send mostly 'a's, but quite rarely I send a 'b'.

    aaaaaaaabaaaaa... ...aaaaaabaaaa

In this case, I can send a shorter message.  Here is a way. I replace every sequence of up to 9 'a's with a number, indicating how many 'a's there are, and I leave 'b's as they are. 

    8b5... ...5b4

Now, I can encode 'b', and the digits 1..9, using 4 bits each (since $2^4 = 16$), and for the bits, I use 'a' for 0 and 'b' for 1. The above is: 

       8    b    5 ...    5    b    4
    baaa 0000 abab ... abab 0000 abaa

Assume I send on average a 'b' every 1,000,000 characters.  Then this allows me to summarize 10 'a' into 4 symbols, compressing by a factor of 2.5.

---

2.  I send 'a's and 'b's with equal frequency.

    abbabbaababbab... ...baababbaab

In this case, there are no long sequences of anything -- in fact, a sequence of length $n$ is likely to reoccur on average every $2^n$ characters, so all subsequences are (equally) rare. 

---

### Information has to do with Probability

The above suggests that information and probability are somehow related.  Let's see how can they be. 

Assume I have an alphabet $\{a_i\}$, $1 \leq i \leq N$, and that each symbol $a_i$ is sent with probability $p_i$, $1 \leq i \leq N$. 

When I send the sequence $a_i a_j$, the probabilities multiply: 

$$P(a_i a_j) = P(a_i) \cdot P(a_j) = p_i \cdot p_j$$

I want an information that is **additive**, so that the information of $a_i a_j$ is equal to the one of $a_i$ plus the one of $a_j$.

$$I(a_i a_j) = I(a_i) + I(a_j)$$

What is $I(a_i)$?

---

### Definition of Information

$$P(a_i a_j) = P(a_i) \cdot P(a_j) = p_i \cdot p_j$$

I want an information that is **additive**, so that the information of $a_i a_j$ is equal to the one of $a_i$ plus the one of $a_j$.

$$I(a_i a_j) = I(a_i) + I(a_j)$$

We need to turn multiplication into addition.  The logarithm does that.  So we can take: 

$$I(a_i) = \log(p_i)$$

and write: 

$$I(a_i a_j) = \log(p_i \cdot p_j) = \log(p_i) + \log(p_j) = I(a_i) + I(a_j)$$

It works except for one thing: $\log(p_i)$ is negative, since $p_i \leq 1$.  So... we just take the ***negative*** of the logarithm as our information! 

---

### Definition of Information

$$I(a_i) = -\log(p_i)$$

$$I(a_i a_j) = -\log(p_i \cdot p_j) = -\log(p_i) - \log(p_j) = I(a_i) + I(a_j)$$

This is the **information** of symbol $a_i$.  

It has the following properties:

1.  The less likely a symbol is, the more information it conveys.  If $p_i$ is small, then $I(a_i)$ is large.
2.  If a symbol is certain, it conveys no information.  If $p_i = 1$, then $I(a_i) = 0$.
3.  The information of a sequence of symbols is the sum of the information of each symbol.

---

### Definition of Entropy

The **entropy** of a source that emits symbols $a_i$ with probabilities $p_i$ is the expected information of a symbol emitted by the source.

$$H = E[I] = \sum_{i=1}^N p_i \cdot I(a_i) = \sum_{i=1}^N p_i \cdot (-\log(p_i)) = -\sum_{i=1}^N p_i \log(p_i)$$

Entropy = average information per symbol.
The entropy has the following properties:

1.  The entropy is maximized when all symbols are equally likely, $p_i = 1/N$.  In this case, $H = \log(N)$.

2.  The entropy is minimized (0) when one symbol is certain, $p_i = 1$ for some $i$.  In this case, $H = 0$.

---

### Example

What is the entropy of a random binary source? 

$$H = - \frac{1}{2} \cdot \log\left(\frac{1}{2}\right) + \frac{1}{2} \cdot \log\left(\frac{1}{2}\right) = \frac{1}{2} \log 2 + \frac{1}{2} \log 2 = \log 2$$

Now, $\log_2 x = \log x / \log 2$, so if we use a base of logarithm different than $e$, just the "unit of measure" of entropy changes. 
It is customary to measure entropy in **bits**, which means using base 2 logarithms.

The above becomes then: 

$$H = \log_2 2 = 1$$

Indicating how a random bit carries, well, 1 bit of information.

---

### Conditional Entropy

The conditional entropy $H(Y|X)$, measures the additional information provided by $Y$ after you know the value of a related variable $X$.

This means: if you know $X$, how much information does $Y$ still carry? 

We start from: 

$$H(Y|X) = \sum_{x \in \mathcal{X}} p(x)H(Y|X=x)$$

Here, $\mathcal{X}$ is the set of all possible outcomes for $X$, and $p(x)$ is the probability of $X$ taking on the value $x$.

---

### Conditional Entropy

$$H(Y|X) = \sum_{x \in \mathcal{X}} p(x)H(Y|X=x)$$

We note that: 

$$H(Y|X=x) = -\sum_{y \in \mathcal{Y}} p(y|x)\log p(y|x)$$

Thus,

$$H(Y|X) = \sum_{x \in \mathcal{X}} p(x)\left(-\sum_{y \in \mathcal{Y}} p(y|x)\log p(y|x)\right)$$

---

### Conditional Entropy

$$H(Y|X) = \sum_{x \in \mathcal{X}} p(x)\left(-\sum_{y \in \mathcal{Y}} p(y|x)\log p(y|x)\right)$$


$$H(Y|X) = -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x)p(y|x)\log p(y|x)$$

And finally: 

$$H(Y|X) = -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log p(y|x)$$

---

### Chain Rule for Entropy

$$H(X,Y) = H(X) + H(Y|X)$$

Proof: 

$$H(X,Y) = -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log p(x,y)$$

$$H(X,Y) = -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log (p(x)p(y|x))$$ 

$$H(X,Y) = -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log p(x) -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log p(y|x)$$

$$H(X,Y) = -\sum_{x \in \mathcal{X}} p(x)\log p(x) -\sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y)\log p(y|x)$$

---

### Mutual Information

The mutual information $I(X;Y)$ between two random variables quantifies their shared information. 

$$I(X;Y) = \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y) \log \frac{p(x,y)}{p(x)p(y)}$$

This can be rewritten in terms of entropy and conditional entropy:

$$I(X;Y) = H(X) - H(X|Y) = H(Y) - H(Y|X)$$

---

### Mutual Information and Independence

$$I(X;Y) = H(X) - H(X|Y) = H(Y) - H(Y|X)$$

If two variables are independent (like rolling two different dice), their mutual information is zero because knowing one gives you no information about the other.

If two variables are perfectly correlated, then their mutual information is equal to the entropy of either variable.

---

## Distance between distributions

Measuring the distance between two probability distributions is an important task in statistics and information theory, and in machine learning. 

For example: one distribution can be the truth (1 for the correct class, 0 for the others), and the other distribution can be the output of a classifier (a probability distribution over the classes). We want to make the classifier's output as close as possible to the truth.

There are various ways to measure the distance between two distributions:

1. Information-theoretic: 
 * Kullback-Leibler divergence
 * Cross-entropy
2. Geometric: Earth-Mover's distance


---

### Kullback-Leibler Divergence

The Kullback-Leibler (KL) divergence measures how one probability distribution diverges from a second, expected probability distribution.

$$D_{KL}(P || Q) = \sum_{x \in \mathcal{X}} P(x) \log \frac{P(x)}{Q(x)}$$

It is always non-negative and is zero if and only if $P$ and $Q$ are identical distributions.
Note also that **it is not symmetrical**: in general, $D_{KL}(P || Q) \neq D_{KL}(Q || P)$.

---

### Proof of Non-Negativity of KL Divergence

The non-negativity of KL divergence is a direct consequence of **Jensen's Inequality**, which states that for a convex function $f$ and a random variable $X$, $E[f(X)] \ge f(E[X])$.


Step 1. We want to prove that $D_{KL}(P||Q) \ge 0$. Let's start with the discrete case and use the negative of the KL divergence:

$$-D_{KL}(P||Q) = -\sum_{i} P(i) \log \left(\frac{P(i)}{Q(i)}\right) = \sum_{i} P(i) \log \left(\frac{Q(i)}{P(i)}\right)$$

By Jensen's inequality, since the logarithm is a concave function, we have:

$$\sum_{i} P(i) \log \left(\frac{Q(i)}{P(i)}\right) \le \log \left(\sum_{i} P(i) \left(\frac{Q(i)}{P(i)}\right)\right)$$

---

We obtained: 

$$\sum_{i} P(i) \log \left(\frac{Q(i)}{P(i)}\right) \le \log \left(\sum_{i} P(i) \left(\frac{Q(i)}{P(i)}\right)\right)$$

We can simplify the right hand side: 

$$\log \left(\sum_{i} P(i) \left(\frac{Q(i)}{P(i)}\right)\right) = \log \left(\sum_{i} Q(i)\right) = \log 1 = 0$$

Putting it all together, we have:

$$-D_{KL}(P||Q) = \sum_{i} P(i) \log \left(\frac{Q(i)}{P(i)}\right) \le 0$$

QED.

---

### Cross-Entropy

The cross-entropy between two probability distributions $P$ and $Q$ over the same underlying set of events measures the average number of bits needed to identify an event from a set of possibilities if a coding scheme is used that is optimized for an estimated probability distribution $Q$, rather than the true distribution $P$.

$$H(P, Q) = -\sum_{x \in \mathcal{X}} P(x) \log Q(x)$$

In ML: 
* $P$ is the true distribution (the truth)
* $Q$ is the predicted distribution (the output of the classifier)

---

### Relation between KL Divergence, Cross-Entropy, and Entropy

Cross-Entropy:

$$H(P, Q) = -\sum_{x \in \mathcal{X}} P(x) \log Q(x)$$

The cross-entropy can be expressed in terms of KL divergence: 

$$H(P, Q) = H(P) + D_{KL}(P || Q)$$

So you can see that cross entropy is not really a measure of distance: in particular, it's not 0 if $P = Q$. 

But because $H(P)$ is constant (it does not depend on $Q$), minimizing cross-entropy is equivalent to minimizing KL divergence.

---

### Notes: 

* KL divergence is not a true distance metric because it is not symmetric and does not satisfy the triangle inequality.

* Sorry for the overloaded use of $H$ for both entropy and cross-entropy.  Did I mention that ML people are super sloppy? 

* In ML, cross-entropy is often used as a loss function for classification problems, especially in logistic regression and neural networks.  Why not KL distance?  Again see above; $H(P)$ is constant, and, ML people are sloppy. 

---

### Special case: $P$ is a one-hot distribution

In classification problems, it will be common to have $P(x^*) = 1$ for the correct class, and $P(x) = 0$ for all other classes.
In this case, the cross-entropy reduces to:

$$H(P, Q) = -\sum_{x \in \mathcal{X}} P(x) \log Q(x) = -\log Q(x^*)$$

So the cross-entropy is just the negative logarithm of the predicted probability of the correct class.

Cross-entropy will be only sensitive to the probability of the correct class; it will not care about precisely how you get wrong the other classes. 

---

### Earth-Mover's Distance

The Earth-Mover's Distance (EMD), also known as the Wasserstein distance, is another commonly used measure of distance between distributions. 

It is defined as the minimum cost of transforming one distribution into another, where the cost is defined in terms of the amount of "earth" (probability mass) that needs to be moved and the distance it needs to be moved.

---

### Earth-Mover's Distance

Consider two distributions $P$ and $Q$ over a finite set $\mathcal{X}$.  We can define the Earth-Mover's Distance between $P$ and $Q$ in two different ways; thinking about the flow, and thinking about the distributions themselves. 

---

### Earth-Mover's Distance

There are two definitions. Distance-Based: 

$$EMD(P, Q) = \frac{1}{2} \sum_i |P(i) - Q(i)|$$

Flow-Based: Minimum transshipping cost: 

$$EMD(P, Q) = \min_{i \neq j} t_{ij}$$

subject to: 

$$\sum_j t_{ij} = P(i) \qquad \sum_i t_{ij} = P(j) \qquad  \forall i, j: t_{ij} \geq 0$$

---

### Earth-Mover's Distance

Note that the distance-based definition is just the $L_1$ distance between the two distributions, divided by 2.  It is a true distance, unlike KL-divergence and cross-entropy. 

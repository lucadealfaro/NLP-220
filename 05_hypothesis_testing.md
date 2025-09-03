---
marp: true
---

## Hypothesis Testing

---

### What is Hypothesis Testing?

It is, at the same time, 

* The foundation for science
* What computer scientists typically do not excel in. 

---

### A typical CS paper

Look, I trained this model, and it has 2% better accuracy than the previous one.  Look at me, I am so great!  Neurips, here comes my paper! 

Another story: 

You toss two tennis balls.  One goes 15.6m and the other, 16.1m.  You pick up the second ball, mark it with a sharpie, and declare it as the better ball. 

---

### How can we tests whether one thing is better than another? 

Fortunately, statisticians and doctors have put more work into it than computer scientists! 

The basic idea is to use **hypothesis testing**.

You have: 

* A null hypothesis $H_0$ (e.g., "the two balls are equally good"). 

* An alternative hypothesis $H_1$ (e.g., "the second ball is better than the first").

You then collect data, and see whether the data supports $H_0$ or $H_1$.
The idea is the test is asymmetric: $H_0$ is the default knowledge, and you want to see whether the data provides enough evidence to reject $H_0$ in favor of $H_1$. 

---

### The p-value

The p-value is the probability of observing data favorable to $H_1$, even though it's actually $H_0$ that is true.

That is, the $p$-value is the probability of getting a false positive: of accepting $H_1$ due to randomness. 

Example: in the tennis balls example, the $p$-value is $1/2$, as the balls are identical (the probability of the second ball traveling farther is 1/2, even though the balls are identical).  

The question is, which $p$-value are you willing to tolerate? 

---

### Type I and Type II errors

* A **Type I error** is rejecting $H_0$ when it is actually true.  The probability of a Type I error is the $p$-value.

* A **Type II error** is accepting $H_0$ when it is actually false.  The probability of a Type II error is called $\beta$.

The power of a test is $1 - \beta$, the probability of correctly rejecting $H_0$ when it is false.

---

### Choosing a significance level

You choose a significance level $\alpha$, which is the maximum $p$-value you are willing to tolerate.  

In papers, common choices are $\alpha = 0.05$ or $\alpha = 0.01$.
The choice of $\alpha = 0.05$ is due to the fact that, a gaussian 2-standard deviations interval covers 95% of the probability mass (of course, the $p$-value associated with a 2-standard deviation event would be more like 0.025, as you would care about one-sided error).

Physicists, who are more serious people, use $\alpha = 2.87 \cdot 10^{-7}$ (or 1 in 3.5 million), which corresponds to a 5-standard deviation event.

--- 

### Welch's t-test

A common test to compare the means of two distributions is **Welch's t-test**.
You have two sets of samples, $X = \{x_1, \ldots, x_n\}$ and $Y = \{y_1, \ldots, y_m\}$.  You want to test whether the means of the two distributions are different.

You compute the sample means $\bar{X}$ and $\bar{Y}$, and the sample variances $s_X^2$ and $s_Y^2$.  The test statistic is

$$t = \frac{\bar{X} - \bar{Y}}{\sqrt{\frac{s_X^2}{n} + \frac{s_Y^2}{m}}}$$

$t$ is the number of standard deviations by which the two means differ.  You then compute the $p$-value associated with $t$ (using the Student's t-distribution with a certain number of degrees of freedom), and see whether it is below your significance level $\alpha$.

---

### p-Hacking

A common malpractice is to try multiple tests, and only report the one that gives a low $p$-value.  This is called **p-hacking**.

For example: you come up with 100 harebrained ideas, and try them all.  One of them gives a $p$-value of 0.01, so you report that one.  But the probability of getting at least one $p$-value below 0.01 in 100 tries is actually about 0.63!

Indeed, if you work with $p$-value 0.01, just test 1000 ideas, and almost surely you will have a paper! 

---

### How to combat p-hacking

There are not many easy defenses. 
Some publications require you to register the experiments you intend to do ahead of time, so that they can check how many experiments you have done before you found the one that worked.

Another approach is to split your data into two parts: one part to explore and find a good hypothesis, and the second part to test the hypothesis.  This is not always possible, as you may not have enough data.

---

### Reproducibility

***Reproducible*** research is fundamental.  

This is why: 

* Making data and code available for papers is important. 

* **Notebooks**: at last, you can see **both** the code **and** the results in one place, and reproduce the results easily. 

Open science! 


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

---

### T-tests and Student's t-distribution

The t-test gives us a ratio between the difference of means and the standard error of the difference.

Informally, and in many uses in computer science, we can understand the $t$ value in terms of the number of standard deviations by which the two means differ, and think of a Gaussian. 

However, if you want to be fully precise, you have to consider that the standard deviation of the two original measurements has been also estimated from the data.  This means that the distribution of the $t$ statistic is not a Gaussian, but rather a **Student's t-distribution**, and this is important because the Student's t-distribution has "fatter tails" than the Gaussian, meaning that extreme values are more likely.

---

### Student's t-Distribution

* The **Student's t-distribution** is a probability distribution used for estimating population parameters from a **small sample size** or when the **population standard deviation is unknown**.
* It's a family of distributions, not just one. The specific shape of the distribution is determined by a parameter called **degrees of freedom ($df$)**.
* It was developed by William Sealy Gosset, a Guinness Brewery employee who published under the pseudonym "Student" because his employer restricted him from publishing.

---

### The t-Distribution vs. The Normal Distribution

* Both are **symmetric and bell-shaped**, with a mean of 0.
* The t-distribution has **"fatter" tails** than the standard normal (Z) distribution. This means it has a higher probability of producing values far from the mean, reflecting the greater uncertainty that comes with a small sample size.
* As the degrees of freedom increase, the t-distribution becomes more and more like the standard normal distribution. This is because a larger sample size provides a better estimate of the population standard deviation, reducing the uncertainty. When $df > 30$, the two distributions are very similar.


* The variance of the t-distribution is always greater than 1, but it approaches 1 as the degrees of freedom increase. The variance of the standard normal distribution is exactly 1.

---

### Degrees of Freedom ($df$)

* Degrees of freedom is a value that indicates the amount of **independent information** available to estimate a parameter.
* For a single sample t-test, the degrees of freedom are calculated as: $df = n - 1$, where $n$ is the sample size.
* The concept is that once the sample mean is fixed, only $n-1$ of the observations can vary freely. The last observation is "fixed" by the value of the mean.
* A larger $df$ means more data, less uncertainty, and a distribution that is closer to the normal curve.

---

### Key Applications of Student Distribution

The t-distribution is used when:
* The **sample size is small** ($n < 30$).
* The **population standard deviation ($\sigma$) is unknown**.

It is the foundation for several statistical analyses, including:
* **t-tests:** Used to test for a significant difference between two group means.
* **Confidence intervals:** Used to construct an interval estimate for a population mean when the population standard deviation is unknown.
* **Linear regression:** Used to test the significance of regression coefficients.

---

### The Probability Density Function of Student's t-Distribution

The probability density function of the Student's t-distribution for $x \in (-\infty, \infty)$ is given by:

$$f(x) = \frac{\Gamma\left(\frac{\nu+1}{2}\right)}{\sqrt{\nu\pi}\ \Gamma\left(\frac{\nu}{2}\right)} \left(1 + \frac{x^2}{\nu}\right)^{-\frac{\nu+1}{2}}$$

Where:
* $x$ is the value of the random variable.
* $\nu$ (Greek letter nu) is the **degrees of freedom** ($df$). This parameter determines the shape of the distribution.
* $\Gamma$ is the **gamma function**, a generalization of the factorial function to real and complex numbers. For a positive integer $n$, $\Gamma(n) = (n-1)!$.

---

### Understanding the t-Distribution

The Student's t-distribution arises as the **probability distribution of a t-statistic**, which is a quantity calculated from a sample to estimate a population mean. It's the exact distribution you get when you standardize a normally distributed variable using an estimated sample variance instead of the true population variance.

---

### The Derivation

Let's break down the mathematical components that lead to the t-distribution.

#### Start with two independent random variables:
* Let $Z$ be a standard normal random variable, $Z \sim N(0, 1)$. This represents a normally distributed sample mean (after standardization using the true population standard deviation $\sigma$). The PDF of $Z$ is $\frac{1}{\sqrt{2\pi}}e^{-z^2/2}$.
* Let $V$ be a chi-squared random variable with $\nu$ degrees of freedom, $V \sim \chi^2(\nu)$. A chi-squared distribution is the sum of the squares of $\nu$ independent standard normal variables. Its PDF is $f_V(v) = \frac{v^{(\nu/2)-1}e^{-v/2}}{2^{\nu/2}\Gamma(\nu/2)}$.

---

#### Form the t-statistic:

The t-statistic, denoted by $T$, is a ratio of these two variables:
$$T = \frac{Z}{\sqrt{V/\nu}}$$
This structure is not arbitrary; it mirrors the real-world t-statistic used in hypothesis testing:
* The numerator $Z$ corresponds to $\frac{\bar{X} - \mu}{\sigma/\sqrt{n}}$, where $\bar{X}$ is the sample mean, $\mu$ is the population mean, and $\sigma/\sqrt{n}$ is the standard error of the mean.
* The denominator $\sqrt{V/\nu}$ corresponds to the sample standard deviation divided by the true population standard deviation, i.e., $\frac{S}{\sigma}$. The random variable $V$ is mathematically equivalent to $\frac{(n-1)S^2}{\sigma^2}$.

 ---

* Substituting these into the formula for $T$ gives $T = \frac{(\bar{X} - \mu)/(\sigma/\sqrt{n})}{\sqrt{((n-1)S^2/\sigma^2)/(n-1)}} = \frac{(\bar{X} - \mu)}{S/\sqrt{n}}$, which is the familiar t-statistic.

---

#### Find the Distribution of the Ratio:

The final step is to determine the probability distribution of this new variable $T$. This is done using a change of variables and integration. The joint PDF of $Z$ and $V$ is the product of their individual PDFs, as they are independent: $f_{Z,V}(z,v) = f_Z(z)f_V(v)$.

A standard method for finding the distribution of a ratio of random variables is to use a change of variables. Let $T = g(Z,V) = Z/\sqrt{V/\nu}$. The resulting PDF of $T$ is found to be the Student's t-distribution with $\nu$ degrees of freedom.

The derivation is intricate but fundamentally a matter of probability theory. It shows that the t-distribution is the **exact distribution** of the t-statistic when the underlying population is normal. The "extra uncertainty" from using the sample standard deviation ($S$) instead of the population standard deviation ($\sigma$) is what makes the t-distribution have fatter tails than the normal distribution. 

---

### Estimating the Tails

The "size" of the tails refers to the probability of observing a value beyond a certain point. This is usually calculated as a **p-value** or a **critical value** for a given significance level ($\alpha$).

To estimate the tail size, you need to use the **cumulative distribution function (CDF)**. The CDF, $F(t; \nu)$, gives the probability that a random variable with $\nu$ degrees of freedom is less than or equal to a value $t$.

$$F(t; \nu) = P(X \le t) = \int_{-\infty}^{t} f(u) du$$

Since the t-distribution is symmetric, the probability in the upper tail (for a given value $t$) is $P(X \ge t) = 1 - F(t; \nu)$. The probability in both tails is $P(|X| \ge t) = 2 \times P(X \ge t)$.

**In practice, you don't calculate these integrals by hand.** Instead, you use software or a t-table to find these values.

---

* **P-value:** Given a test statistic $t$ from your data, you look up the corresponding probability in the t-distribution with the correct degrees of freedom. This probability is your p-value, which represents the size of the tail(s) beyond your test statistic. A small p-value (e.g., less than 0.05) means your result is in the extreme tail, suggesting it's statistically significant.

* **Critical Value:** Given a desired significance level $\alpha$ (e.g., $\alpha = 0.05$), you look up the value of $t$ for which the area in the tail(s) is equal to $\alpha$. This value of $t$ is the critical value. If your test statistic is more extreme than the critical value, you reject the null hypothesis.

The "size" of the tails decreases as the degrees of freedom increase. As the t-distribution approaches the normal distribution, the critical values get smaller, meaning you don't need to observe as extreme a result to achieve statistical significance. 

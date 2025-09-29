---
marp: true
paginate: true
---

# Measuring Correlation
### Luca de Alfaro, UC Santa Cruz

### Content

* Pearson correlation
* Spearman correlation
* Kendall correlation
* Coefficient of determination

---

### What is Correlation?

* Correlation is a statistical measure that quantifies the **strength** and **direction** of a relationship between two variables.
* The correlation coefficient is a single number between -1 and +1.
    * **+1** indicates a perfect positive correlation (as one variable increases, the other increases).
    * **-1** indicates a perfect negative correlation (as one variable increases, the other decreases).
    * **0** indicates no correlation.
* **Important Note:** Correlation does **not** imply causation. It only shows that a relationship exists.

---

### Pearson's Correlation

* **What it Measures:** The strength and direction of a **linear relationship** between two variables.
* **Key Assumptions:**
    * The relationship is linear.
    * The data is continuous and approximately normally distributed.
* **When to Use It:**
    * When your data forms a straight line on a scatter plot.
    * For parametric data (e.g., height, temperature, test scores).
* **Sensitivity:** It is highly sensitive to **outliers**, which can significantly skew the result.

---

### Pearson's correlation

The formula for the **sample** Pearson correlation coefficient, $r$, is calculated as the covariance of the two variables divided by the product of their standard deviations.
<br>

$$r = \frac{Cov(X,Y)}{\sigma_X \sigma_Y} =
\frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n}(x_i - \bar{x})^2}\sqrt{\sum_{i=1}^{n}(y_i - \bar{y})^2}}$$

* $n$: Number of data pairs
* $x_i$ and $y_i$: Individual data points
* $\bar{x}$ and $\bar{y}$: Mean (average) of the $x$ and $y$ variables

---

### Definition of Pearson's correlation. 

The **Pearson correlation coefficient**, denoted by $\rho$ for a population or $r$ for a sample, is a statistical measure of the **linear relationship** between two variables, $X$ and $Y$. It's a normalized version of covariance, so its value is always between -1 and +1.

The formula for the population Pearson correlation coefficient using expectations is:

$$\rho_{X,Y} = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y} = \frac{E[(X - E[X])(Y - E[Y])]}{\sqrt{E[(X - E[X])^2]}\sqrt{E[(Y - E[Y])^2]}}$$

Where:
* $E$ is the expectation operator.
* $\text{Cov}(X,Y)$ is the **covariance** of $X$ and $Y$.
* $\sigma_X$ and $\sigma_Y$ are the **standard deviations** of $X$ and $Y$, respectively.

---

### Interpreting Pearson's Correlation Coefficient

The value of $\rho$ indicates the **strength** and **direction** of the linear relationship between $X$ and $Y$. 

* **$\rho = +1$**: A perfect positive linear relationship. As $X$ increases, $Y$ increases proportionally.
* **$\rho = -1$**: A perfect negative linear relationship. As $X$ increases, $Y$ decreases proportionally.
* **$\rho = 0$**: No linear relationship exists between the variables. This does not mean there is no relationship at all; a strong non-linear relationship could still be present.
* **Values between -1 and +1**: The closer the value is to zero, the weaker the linear relationship. The sign determines the direction.

---

### Key Properties of Pearson's Correlation

1.  **Bounded Range**: The coefficient's value always falls within $[-1, 1]$. 

2.  **Symmetry**: The correlation between $X$ and $Y$ is the same as the correlation between $Y$ and $X$.
    * $\rho_{X,Y} = \rho_{Y,X}$

3.  **Invariance to Linear Transformations**: The correlation coefficient is not affected by changes in the origin or scale of the variables.
    * For constants $a, b, c, d$ (with $b,d \neq 0$), if $U = a+bX$ and $V = c+dY$, then $\rho_{U,V} = \rho_{X,Y}$.

---

### Key Properties of Pearson's Correlation (cont.)

4.  **Independence vs. Zero Correlation**:
    * If $X$ and $Y$ are **independent**, then $\rho_{X,Y} = 0$.
    * However, if $\rho_{X,Y} = 0$, it **does not** imply that $X$ and $Y$ are independent. It only signifies the absence of a linear relationship.

---

### Spearman's Correlation

* **What it Measures:** The strength and direction of a **monotonic relationship** between two variables. A monotonic relationship means the variables tend to move in the same direction, but not necessarily at a constant rate (it doesn't have to be a straight line).
* **When to Use It:**
    * When the relationship is not linear.
    * When you have **ordinal data** (e.g., rankings like first, second, third place).
    * When your data contains outliers.
* **How it Works:** It calculates the Pearson correlation coefficient on the **ranks** of the data, rather than the raw data itself. This makes it a non-parametric test and less sensitive to outliers.

---

### Pearson vs. Spearman: Key Differences

| Aspect | Pearson's Correlation | Spearman's Correlation |
| :--- | :--- | :--- |
| **Relationship Type** | Linear | Monotonic |
| **Data Type** | Continuous (Interval/Ratio) | Continuous or Ordinal (Ranked) |
| **Assumptions** | Assumes normality and linearity | No normality assumption; less sensitive to outliers |
| **Calculation** | Uses the raw data values | Uses the **ranks** of the data values |
| **Ideal for** | Linear relationships, normally distributed data | Non-linear relationships, ranked data, or data with outliers |

---


### Spearman's Correlation: The Core Idea

Spearman's correlation is just Pearson's correlation of the ***ranks*** of the data.

Just to add to the confusion (don't you love statisticians?) it is indicated by $\rho$ or $r_s$.  It is a **non-parametric** measure of the **monotonic relationship** between two variables.

* **Non-parametric:** Doesn't assume the data comes from a particular distribution (like a normal distribution).
* **Monotonic:** Assesses if the relationship is consistently increasing or decreasing, not necessarily in a straight line.

---

## Spearman's Correlation: Definition

The calculation is based on the **ranks** of the data, not the raw values.

### Simple Case (no tied ranks)

$r_s = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}$

$d_i = \text{rank}(x_i) - \text{rank}(y_i)$

### General Case (with tied ranks)

$$r_s = \frac{Cov(\text{rank}_x, \text{rank}_y)}{\sigma_{\text{rank}_x} \sigma_{\text{rank}_y}}$$


---

## Interpreting Spearman's Correlation

The coefficient's value tells you about the strength and direction of the relationship.

* **$\rho = +1$**: Perfect positive monotonic relationship.
* **$\rho = -1$**: Perfect negative monotonic relationship.
* **$\rho = 0$**: No monotonic relationship.
* Values between -1 and +1 indicate a weaker relationship.

For example, $\rho=0.8$ signifies a strong positive monotonic relationship.

---

## Kendall's Tau

Kendall's Tau (τ) is a non-parametric rank correlation coefficient that measures the strength and direction of the association between two variables.

Similar to Spearman's correlation, it uses ranks to assess whether the renationship between two variables is monotonic.

---

### Definition of Kendall's Tau

* **Concordant Pairs (C):** A pair of observations is concordant if their ranks are in the same relative order for both variables.
* **Discordant Pairs (D):** A pair of observations is discordant if their ranks are in the opposite relative order for the two variables.

Kendall's Tau (specifically Tau-A) is:

$$\tau = \frac{2(C - D)}{n(n-1)}$$

Remember: if there are no ties, 

$$ C + D = \frac{n(n-1)}{2}$$


---

### Properties of Kendall's Tau

* **Robustness:** Kendall's Tau is robust to outliers and is a more stable and reliable measure than other methods like Spearman's rho, especially with smaller sample sizes.
* **Interpretability:** It has a direct probabilistic interpretation: it represents the difference between the probability of a concordant pair and the probability of a discordant pair.
* **Comparison to other methods:**
    * **vs. Pearson's Correlation:** Kendall's Tau measures monotonic relationships, whereas Pearson's correlation measures linear relationships.
    * **vs. Spearman's Rho:** Both are non-parametric rank correlations. However, Kendall's Tau is often preferred when there are many tied ranks in the data.

---

### Coefficient of Determination ($R^2$)

* The **Coefficient of Determination**, or **R-squared** ($R^2$), is a statistical measure that tells you the proportion of the variance in the dependent variable that is predictable from the independent variable(s).
* In simpler terms, it measures how well your regression model explains the variability of the output data.
* $R^2$ is a value between **0 and 1** (or 0% and 100%).
* A high $R^2$ indicates that the model's predictions closely match the actual data points. A low $R^2$ suggests the model doesn't explain much of the variability.

---

### Measuring $R^2$

* To calculate R-squared, we compare two key measures of variability.
* The formula is:
    $R^2 = 1 - \frac{SSR}{SST}$
* Where:
    * **$SST$** is the **Total Sum of Squares**.
    * **$SSR$** is the **Residual Sum of Squares**.

---

### Components of R-Squared

* **Total Sum of Squares (SST):**
    * Measures the total variability in the dependent variable ($y$) around its mean ($\bar{y}$).
    * It represents the error you would have if your model simply predicted the mean for every single data point.
    * **Formula:** $SST = \sum_{i=1}^{m} (y^{(i)} - \bar{y})^2$
* **Residual Sum of Squares (SSR):**
    * Measures the variability that is **unexplained** by the model.
    * It's the sum of the squared differences between the actual data points ($y$) and your model's predictions ($\hat{y}$).
    * **Formula:** $SSR = \sum_{i=1}^{m} (y^{(i)} - \hat{y}^{(i)})^2$

---

### Interpreting the R-squared Value

* **$R^2 = 1$ (or 100%):**
    * Your model perfectly explains all the variability in the dependent variable.
    * The SSR would be 0, meaning there is no difference between the actual data and the model's predictions.
* **$R^2 = 0$ (or 0%):**
    * Your model explains none of the variability. It's no better than simply predicting the mean.
    * In this case, the SSR would be equal to the SST.
* **$0 < R^2 < 1$:**
    * The value represents the percentage of variance explained by your model.
    * Example: An $R^2$ of 0.75 means the model explains 75% of the variability in the dependent variable.

---

### A Simple Example

* Imagine a model that predicts student exam scores based on hours studied.
* **SST** is the total variability in scores among all students.
* **SSR** is the remaining variability in scores after accounting for the hours they studied.
* If our model has an $R^2$ of 0.71, we can say that **71%** of the variation in student exam scores can be explained by the amount of time they spent studying. The other 29% is unexplained, likely due to other factors like prior knowledge or test-taking ability.

---

### Limitations of R-squared

* One major limitation is that $R^2$ **always increases** as you add more independent variables to the model, even if those variables are not statistically significant.
* This can be misleading and lead to **overfitting**, where a model becomes too complex and fits the random noise in the training data rather than the underlying pattern.
* A high $R^2$ doesn't necessarily mean the model is good or that the variables have a causal relationship.

---

## Appendix

The common formula for Spearman's correlation, $r_s = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}$, is a simplified version derived from the **Pearson correlation coefficient applied to ranked data**. This derivation is only valid when there are **no tied ranks**.

Let's start with the definition of Pearson's correlation coefficient, $r$, on two variables, $X$ and $Y$.

$$r = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \bar{x})^2 \sum_{i=1}^{n} (y_i - \bar{y})^2}}$$

For Spearman's correlation, we apply this formula to the ranks of the data. Let the ranks for variable $X$ be $R_x$ and the ranks for variable $Y$ be $R_y$. If there are no ties, the ranks for both variables are simply a permutation of the integers $1, 2, 3, \dots, n$.

---

## Step-by-Step Derivation

### 1. Calculate the means of the ranks:
The mean of the first $n$ integers is given by the formula for the sum of an arithmetic series, $\frac{n(n+1)}{2}$, divided by $n$.
$$\bar{R_x} = \bar{R_y} = \frac{\sum_{i=1}^{n} i}{n} = \frac{n(n+1)}{2n} = \frac{n+1}{2}$$

### 2: Calculate the variance of the ranks:

The variance of the first $n$ integers is given by the formula $\frac{n^2-1}{12}$. Since the set of ranks for both $X$ and $Y$ are the same set of numbers, their variances are equal.
$$\sigma_{R_x}^2 = \sigma_{R_y}^2 = \frac{n^2-1}{12}$$

---

### 3: Apply Pearson's formula to the ranks:
Substitute the rank notation into the Pearson formula.
$$r_s = \frac{\sum_{i=1}^{n} (R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y})}{\sqrt{\sum_{i=1}^{n} (R_{x_i} - \bar{R_x})^2 \sum_{i=1}^{n} (R_{y_i} - \bar{R_y})^2}}$$
Since the variances of the ranks are equal, the denominator simplifies:
$$r_s = \frac{\sum_{i=1}^{n} (R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y})}{\sum_{i=1}^{n} (R_{x_i} - \bar{R_x})^2}$$

---

### 4.  Introduce the difference in ranks ($d_i$):

Let $d_i = R_{x_i} - R_{y_i}$. The squared difference is $d_i^2 = (R_{x_i} - R_{y_i})^2$.
Expand this expression:
$$d_i^2 = (R_{x_i} - \bar{R_x}) - (R_{y_i} - \bar{R_y})]^2 = (R_{x_i} - \bar{R_x})^2 + (R_{y_i} - \bar{R_y})^2 - 2(R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y})$$
Now, sum both sides from $i=1$ to $n$:
$$\sum d_i^2 = \sum (R_{x_i} - \bar{R_x})^2 + \sum (R_{y_i} - \bar{R_y})^2 - 2\sum (R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y})$$
Since $\sum (R_{x_i} - \bar{R_x})^2 = \sum (R_{y_i} - \bar{R_y})^2$, we can simplify:
$$\sum d_i^2 = 2 \sum (R_{x_i} - \bar{R_x})^2 - 2 \sum (R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y})$$
From step 3, we know that the numerator of the Pearson formula is $\sum (R_{x_i} - \bar{R_x})(R_{y_i} - \bar{R_y}) = r_s \sum (R_{x_i} - \bar{R_x})^2$.

---

Substitute this into the equation:
$$\sum d_i^2 = 2 \sum (R_{x_i} - \bar{R_x})^2 - 2 r_s \sum (R_{x_i} - \bar{R_x})^2$$
Factor out the common term:
$$\sum d_i^2 = 2 (1 - r_s) \sum (R_{x_i} - \bar{R_x})^2$$
Solve for $r_s$:
$$r_s = 1 - \frac{\sum d_i^2}{2 \sum (R_{x_i} - \bar{R_x})^2}$$

---

### 5: Substitute the variance of the ranks:
Recall that $\sum (R_{x_i} - \bar{R_x})^2$ is the sum of squared deviations, which is related to the variance by $\sum (R_{x_i} - \bar{R_x})^2 = (n-1)\sigma_{R_x}^2$. However, we can use the identity for the sum of squares of the first $n$ integers:
$$\sum_{i=1}^{n} (R_{x_i} - \bar{R_x})^2 = \frac{n(n^2-1)}{12}$$
Substitute this into the formula for $r_s$:
$$r_s = 1 - \frac{\sum d_i^2}{2 \left( \frac{n(n^2-1)}{12} \right)} = 1 - \frac{\sum d_i^2}{\frac{n(n^2-1)}{6}} = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}$$

This final equation is the well-known simplified formula for Spearman's correlation, derived directly from the Pearson correlation applied to the ranks.

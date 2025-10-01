---
marp: true
---


## Linear Regression
### Luca de Alfaro

Linear regression consists in interpolating a line through a set of data points, in such a way that the line best represents the data.
---

### Linear Regression

The linear regression model is generally expressed as $Y = \beta_0 + \beta_1 X + \epsilon$, where $Y$ is the dependent variable, $X$ is the independent variable, $\beta_0$ is the $Y$-intercept, $\beta_1$ is the slope, and $\epsilon$ is the error term.

The estimated linear regression coefficients, $\hat{\beta}_0$ (the intercept) and $\hat{\beta}_1$ (the slope), are calculated using the **Ordinary Least Squares (OLS)** method.

---

### 1. The Slope ($\hat{\beta}_1$)

The slope $\hat{\beta}_1$ quantifies the change in $Y$ for a one-unit change in $X$. It can be expressed in terms of the **covariance** and the **variance** or through a sum-of-squares formulation.

$$\hat{\beta}_1 = \frac{\text{Cov}(X, Y)}{\text{Var}(X)} = \frac{\sum_{i=1}^{n} (X_i - \bar{X})(Y_i - \bar{Y})}{\sum_{i=1}^{n} (X_i - \bar{X})^2}$$

* **$\text{Cov}(X, Y)$** is the sample covariance between $X$ and $Y$.
* **$\text{Var}(X)$** is the sample variance of $X$.
* $X_i$ and $Y_i$ are individual data points.
* $\bar{X}$ and $\bar{Y}$ are the sample means of $X$ and $Y$, respectively.
* $n$ is the number of data points.

***

### 2. The Intercept ($\hat{\beta}_0$)

The intercept $\hat{\beta}_0$ is the expected value of $Y$ when $X$ is zero. It's calculated using the estimated slope and the means of $X$ and $Y$.

$$\hat{\beta}_0 = \bar{Y} - \hat{\beta}_1 \bar{X}$$

* $\bar{Y}$ is the mean of the dependent variable.
* $\hat{\beta}_1$ is the estimated slope (calculated above).
* $\bar{X}$ is the mean of the independent variable.

***

### The Estimated Regression Line

Once $\hat{\beta}_0$ and $\hat{\beta}_1$ are calculated, the **estimated regression line** (or the line of best fit) is:

$$\hat{Y} = \hat{\beta}_0 + \hat{\beta}_1 X$$

where $\hat{Y}$ is the predicted value of the dependent variable.

---


### Slide 4: Deriving the Coefficients

* To find the values of $\theta_0$ and $\theta_1$ that minimize the cost function, we can use calculus.
* We take the partial derivative of the cost function with respect to each coefficient and set it to zero.
* This gives us two equations, which we can then solve for our two unknowns.
* **Goal:**
    $\frac{\partial J}{\partial \theta_0} = 0 \qquad 
    \frac{\partial J}{\partial \theta_1} = 0$

---

### Slide 5: Derivation for the Intercept ($\theta_0$)

* Start with the partial derivative of $J$ with respect to $\theta_0$:

    $\frac{\partial J}{\partial \theta_0} = \frac{\partial}{\partial \theta_0} \frac{1}{2m} \sum_{i=1}^{m} (\theta_0 + \theta_1x^{(i)} - y^{(i)})^2 = \frac{1}{2m} \sum_{i=1}^{m} 2(\theta_0 + \theta_1x^{(i)} - y^{(i)}) \cdot 1$
* Set the derivative to zero and solve for $\theta_0$:
    $0 = \frac{1}{m} \sum_{i=1}^{m} (\theta_0 + \theta_1x^{(i)} - y^{(i)})$
    $0 = \sum_{i=1}^{m} \theta_0 + \sum_{i=1}^{m} \theta_1x^{(i)} - \sum_{i=1}^{m} y^{(i)}$
    $0 = m\theta_0 + \theta_1 \sum_{i=1}^{m} x^{(i)} - \sum_{i=1}^{m} y^{(i)}$
* Rearrange the terms to get the final formula for $\theta_0$:
    $\theta_0 = \frac{1}{m} \sum_{i=1}^{m} y^{(i)} - \theta_1 \frac{1}{m} \sum_{i=1}^{m} x^{(i)}$
    $\theta_0 = \bar{y} - \theta_1\bar{x}$
    * This shows the regression line passes through the mean of the data points $(\bar{x}, \bar{y})$.

---

### Slide 6: Derivation for the Slope ($\theta_1$)

* Now, we do the same for the slope, $\theta_1$:
    $\frac{\partial J}{\partial \theta_1} = \frac{\partial}{\partial \theta_1} \frac{1}{2m} \sum_{i=1}^{m} (\theta_0 + \theta_1x^{(i)} - y^{(i)})^2$
* Apply the chain rule:
    $= \frac{1}{2m} \sum_{i=1}^{m} 2(\theta_0 + \theta_1x^{(i)} - y^{(i)}) \times x^{(i)}$
* Set the derivative to zero and substitute $\theta_0 = \bar{y} - \theta_1\bar{x}$:
    $0 = \frac{1}{m} \sum_{i=1}^{m} (\bar{y} - \theta_1\bar{x} + \theta_1x^{(i)} - y^{(i)})x^{(i)}$
    $0 = \sum_{i=1}^{m} (\bar{y} - y^{(i)} - \theta_1\bar{x} + \theta_1x^{(i)})x^{(i)}$
* This simplifies to:
    $0 = \sum_{i=1}^{m} (\bar{y} - y^{(i)})x^{(i)} - \theta_1 \sum_{i=1}^{m} (\bar{x} - x^{(i)})x^{(i)}$
* Solving for $\theta_1$, we get:
    $\theta_1 = \frac{\sum_{i=1}^{m} (x^{(i)} - \bar{x})(y^{(i)} - \bar{y})}{\sum_{i=1}^{m} (x^{(i)} - \bar{x})^2}$

---

### Slide 7: Summary of the Formulas

* The analytical solution for the coefficients is known as the **Normal Equation**.
* **Slope ($\theta_1$):**
    $\theta_1 = \frac{\sum_{i=1}^{m} (x^{(i)} - \bar{x})(y^{(i)} - \bar{y})}{\sum_{i=1}^{m} (x^{(i)} - \bar{x})^2}$
* **Intercept ($\theta_0$):**
    $\theta_0 = \bar{y} - \theta_1\bar{x}$
* These formulas allow us to directly calculate the coefficients that minimize the MSE, giving us the line of best fit without needing an iterative process like gradient descent.
---
marp: true
---


### Slide 1: Title Slide

# Simple Linear Regression
### Predicting continuous values with one variable.

---

### Slide 2: What is Simple Linear Regression?

* **Simple Linear Regression** is a model with a single input feature.
* Its goal is to find a straight line that best represents the relationship between the independent variable ($x$) and the dependent variable ($y$).
* **Hypothesis Function:**
    $h_\theta(x) = \theta_0 + \theta_1x$
    * $\theta_0$ is the **y-intercept** (where the line crosses the y-axis).
    * $\theta_1$ is the **slope** of the line.
* The model's job is to learn the optimal values for $\theta_0$ and $\theta_1$ from the training data.

---

### Slide 3: The Cost Function (MSE)

* To determine the "best" line, we need a way to measure the error between our model's predictions and the actual data.
* We use the **Mean Squared Error (MSE)**, which calculates the average of the squared differences between the predicted values ($h_\theta(x)$) and the actual values ($y$).
* **Cost Function ($J$):**
    $J(\theta_0, \theta_1) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$
* The coefficients that minimize this function will give us the line of best fit.

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
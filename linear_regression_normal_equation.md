### Slide 1: Title Slide

# Multiple Linear Regression
### Predicting continuous values with multiple variables.

***

### Slide 2: The Hypothesis with Multiple Variables

* Multiple linear regression is a model with multiple input features ($x_1, x_2, ..., x_n$).
* The hypothesis function, which predicts the output, is a linear combination of all features.
* **Vectorized Hypothesis:**
    $h_\theta(x) = \theta_0x_0 + \theta_1x_1 + ... + \theta_nx_n = \theta^T x$
* In this form:
    * $\theta$ is the **coefficient vector** containing all parameters ($\theta_0, \theta_1, ..., \theta_n$).
    * $x$ is the **feature vector** for a single example ($x_0, x_1, ..., x_n$), where $x_0$ is set to 1 for the intercept term.
    * $\theta^T$ is the transpose of the coefficient vector.

***

### Slide 3: The Cost Function (MSE)

* We still use the **Mean Squared Error (MSE)** to measure the difference between our model's predictions and the actual values.
* The goal is to find the coefficient vector $\theta$ that minimizes this function.
* **Vectorized Cost Function:**
    $J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2 = \frac{1}{2m} (X\theta - y)^T (X\theta - y)$
* In the vectorized form:
    * $X$ is the **design matrix**, where each row is a feature vector for a training example.
    * $y$ is the **target vector** of all actual outputs.

***

### Slide 4: Computing Coefficients with the Normal Equation

* With multiple variables, we can still use Gradient Descent, but there's also a direct, non-iterative method called the **Normal Equation**.
* The Normal Equation is an analytical solution that finds the optimal $\theta$ in a single step.
* It works by solving the optimization problem directly using matrix calculus.
* **The Goal:** Find the value of $\theta$ that makes the partial derivative of the cost function with respect to $\theta$ equal to zero.
    $\frac{\partial J(\theta)}{\partial \theta} = 0$

***

### Slide 5: Deriving the Normal Equation - Step 1

* We begin with the vectorized cost function:
    $J(\theta) = \frac{1}{2m} (X\theta - y)^T (X\theta - y)$
* We can expand the term to make it easier to differentiate:
    $J(\theta) = \frac{1}{2m} (\theta^T X^T - y^T)(X\theta - y)$
    $J(\theta) = \frac{1}{2m} (\theta^T X^T X \theta - \theta^T X^T y - y^T X \theta + y^T y)$
* Note that $\theta^T X^T y$ and $y^T X \theta$ are both scalars, so they are equal.
    $J(\theta) = \frac{1}{2m} (\theta^T X^T X \theta - 2\theta^T X^T y + y^T y)$

***

### Slide 6: Deriving the Normal Equation - Step 2

* Now, we take the derivative of the simplified cost function with respect to the vector $\theta$.
* Using rules of matrix calculus:
    $\frac{\partial}{\partial \theta} \left( \frac{1}{2m} (\theta^T X^T X \theta - 2\theta^T X^T y + y^T y) \right)$
    $= \frac{1}{2m} (2X^T X \theta - 2X^T y + 0)$
    $= \frac{1}{m} (X^T X \theta - X^T y)$
* Set the derivative to zero to find the minimum:
    $\frac{1}{m} (X^T X \theta - X^T y) = 0$
    $X^T X \theta - X^T y = 0$

***

### Slide 7: Deriving the Normal Equation - Step 3

* Solve for $\theta$ using matrix algebra.
* Add $X^T y$ to both sides:
    $X^T X \theta = X^T y$
* Multiply both sides by the inverse of the matrix $(X^T X)$:
    $(X^T X)^{-1} X^T X \theta = (X^T X)^{-1} X^T y$
* The term $(X^T X)^{-1} X^T X$ simplifies to the identity matrix, leaving us with the final formula.
* **The Final Normal Equation:**
    $\theta = (X^T X)^{-1} X^T y$

***

### Slide 8: Summary & Comparison

* **The Normal Equation** gives us a direct solution for the optimal coefficients:
    $\theta = (X^T X)^{-1} X^T y$
* **Pros:**
    * No need to choose a learning rate ($\alpha$).
    * No need to iterate; it's a one-step solution.
* **Cons:**
    * Requires computing the inverse of the $(X^T X)$ matrix.
    * This is computationally expensive if the number of features ($n$) is very large (e.g., $n > 10,000$).
* **Conclusion:** The Normal Equation is a great option for datasets with a small number of features. For large-scale problems, Gradient Descent is usually more efficient.
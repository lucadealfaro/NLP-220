### Slide 1: Title Slide

# Gradient Descent for Multiple Linear Regression
### An iterative approach to finding the coefficients.

---

### Slide 2: The Goal of Gradient Descent

* **Gradient descent** is a powerful optimization algorithm used to minimize the cost function.
* The goal is to find the coefficient vector $\theta$ that minimizes the **Mean Squared Error (MSE)**.
* We can visualize this as a a multi-dimensional bowl-shaped function, where we want to find the lowest point. 🥣
* Gradient descent works by starting at a random point on this "bowl" and taking repeated steps down the steepest slope until it reaches the bottom.

---

### Slide 3: The Cost Function and Update Rule

* The cost function for multiple linear regression is the Mean Squared Error:
    $J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$
* The general **update rule** for each coefficient $\theta_j$ is:
    $\theta_j := \theta_j - \alpha \frac{\partial J(\theta)}{\partial \theta_j}$
* This rule tells us to update each coefficient by subtracting the **learning rate** ($\alpha$) times the **gradient** (the partial derivative of the cost function).

---

### Slide 4: Deriving the Gradient

* To get the specific update rule, we need to find the partial derivative of the cost function with respect to each coefficient $\theta_j$.
* Using the chain rule:
    $\frac{\partial J(\theta)}{\partial \theta_j} = \frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)}$
* This tells us that the gradient is the average of the errors for all training examples, multiplied by the value of the feature $x_j$.

---

### Slide 5: The Final Update Rules

* The final gradient descent algorithm involves repeatedly and simultaneously applying this update rule to all coefficients.
* **Update for all coefficients:**
    * Repeat until convergence:
    $\theta_j := \theta_j - \alpha \frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)}$
* This update is performed for every coefficient $j = 0, 1, ..., n$.

---

### Slide 6: Vectorized Implementation (for efficiency)

* In practice, we use a vectorized approach to make the calculations much faster, especially for large datasets.
* **The vectorized update rule is:**
    $\theta := \theta - \alpha \frac{1}{m} X^T(X\theta - y)$
* Here, $X$ is the design matrix, $\theta$ is the coefficient vector, and $y$ is the target vector.
* This allows us to perform all updates at once, without a loop over individual features.

---

### Slide 7: Choosing a Learning Rate ($\alpha$)

* The learning rate is a critical hyperparameter.
* If $\alpha$ is too **small**, gradient descent will be very slow to converge.
* If $\alpha$ is too **large**, gradient descent can overshoot the minimum and fail to converge or even diverge.
* We often start with a small value (e.g., 0.01, 0.001) and adjust as needed. 

---

### Slide 8: Summary of Gradient Descent

* **Algorithm:** An iterative optimization method.
* **Goal:** Minimize the Mean Squared Error cost function.
* **How it works:** It takes steps in the direction of the steepest descent (the negative gradient).
* **Key Components:**
    * **Learning Rate ($\alpha$)**: Controls the step size.
    * **Gradient**: The partial derivatives of the cost function.
* **Advantages:** Works well for large datasets where the Normal Equation is too slow.
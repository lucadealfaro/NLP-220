---
marp: true
---

# Logistic Regression

## Luca de Alfaro, University of California, Santa Cruz
---


# What is Logistic Regression?

* **Not a regression model!** It's a **classification** algorithm used for predicting a binary outcome.
* The model outputs a **probability** (a value between 0 and 1) that an observation belongs to a specific class.
* **Examples:**
    * Will a customer click on an ad? (Yes/No)
    * Is an email spam? (Spam/Not Spam)
    * Does a patient have a disease? (Positive/Negative)


---

##  The Core Mathematical Idea

* Logistic regression uses a special function to **"squeeze"** the output of a linear equation into a probability.
* The process has two main parts:
    1.  **A linear equation** to combine the input features:
        $z = w_1x_1 + w_2x_2 + ... + w_nx_n + b$
        or in vector form: $z = w^T x + b$. 

        Where $z$ is a real number that can range from $-\infty$ to $+\infty$.
    2.  **The sigmoid function**, which maps $z$ to a probability:
        $\sigma(z) = \frac{1}{1 + e^{-z}}$

---

## The Sigmoid Function

![w:8in](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logistic-curve.svg/1200px-Logistic-curve.svg.png)

---

## The Sigmoid Function

* The **Sigmoid Function** is the heart of the model, also known as the logistic function.
* **Formula:**
    $\sigma(z) = \frac{1}{1 + e^{-z}}$
* **Key properties:**
    * Takes any real number as input and outputs a value between **0 and 1**.
    * The curve is S-shaped, becoming steeper around the decision boundary and flatter at the extremes.
    * When $z = 0$, the output is exactly 0.5.

--- 

## Derivative of Sigmoid function

* The derivative of the sigmoid function is crucial for optimization.
* Prediction: $\hat{y} = \sigma(z)$
* **Derivative Formula:**

    $\frac{d\hat{y}}{dz} = \hat{y} (1 - \hat{y})$

Very useful to remember.  Maximum is for $\hat{y} = 0.5$, where it equals 0.25.

---

## The Hypothesis and Decision Boundary

* The final model is called the **hypothesis**, which combines the linear and sigmoid parts.
* **Hypothesis Formula:**
    $h_\theta(x) = \sigma(w^T x + b)$
    where $\theta = (w, b)$ are the parameters of the model.
* We classify the output by setting a **decision boundary** (a threshold).
    * If $h_\theta(x) \geq 0.5$, predict **Class 1**.
    * If $h_\theta(x) < 0.5$, predict **Class 0**.

Note that $h_\theta(x)$ is a probability, so the decision boundary is at 0.5; note also that  $h_\theta(x) < 0.5$ is equivalent to $w^T x + b < 0$.

---

## The Cost Function (Log Loss)

* The model learns by minimizing its error, measured by a **cost function**.
* For logistic regression, we use **Log Loss** (or Cross-Entropy). It's a convex function, which is ideal for optimization.
* The formula for a single training example is designed to penalize confident, incorrect predictions heavily:
    $Cost(\hat{y}, y) = \begin{cases} - \log(\hat{y}) & \text{if } y = 1 \\ - \log(1 - \hat{y}) & \text{if } y = 0 \end{cases}$
* The overall goal is to find the parameters that minimize this cost across all training examples.

---

### Slide 7: Gradient Descent

* **Gradient Descent** is the optimization algorithm that finds the best parameters ($w$ and $b$) to minimize the cost function.
* It's an iterative process that repeatedly takes small steps in the direction of the steepest descent of the cost function.
* **The General Update Rule:**
    $parameter := parameter - \alpha \times \frac{\partial J}{\partial parameter}$
    * $\alpha$ is the **learning rate**, controlling the size of each step.

---

### Slide 8: The Update Rules (Derived)

* The specific update rules are derived by taking the partial derivatives of the Log Loss function.
* **Weight Update:**
    $w_j := w_j - \alpha \frac{1}{m} \sum_{i=1}^{m} [(\hat{y}^{(i)} - y^{(i)})x_j^{(i)}]$
* **Bias Update:**
    $b := b - \alpha \frac{1}{m} \sum_{i=1}^{m} [(\hat{y}^{(i)} - y^{(i)})]$
* These rules are applied in each iteration to adjust the parameters and reduce the model's error.

---



### Slide 2: Introduction to the Problem

* **Heading:** What are we trying to do?
* **Content:**
    * Explain the goal of logistic regression: to find a function that predicts a probability between 0 and 1.
    * Introduce the key components:
        * **Linear Equation ($z$):** $z = w^T x + b$
        * **Sigmoid Function ($\hat{y}$):** $\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}$
        * **Cost Function ($J$):** Log Loss, which measures the error.
    * State the ultimate goal: Use gradient descent to find the parameters ($w$ and $b$) that minimize the cost function $J$.

---

### Slide 3: The Cost Function (Log Loss)

* **Heading:** The Cost Function: Measuring Error
* **Content:**
    * Present the formula for the Log Loss cost function for a single example:
        $Cost(\hat{y}, y) = \begin{cases} - \log(\hat{y}) & \text{if } y = 1 \\ - \log(1 - \hat{y}) & \text{if } y = 0 \end{cases}$
    * Explain why this function is used instead of Mean Squared Error.
    * Show the combined formula for the total cost over all $m$ training examples:
        $J(w,b) = - \frac{1}{m} \sum_{i=1}^{m} [y^{(i)}\log(\hat{y}^{(i)}) + (1-y^{(i)})\log(1-\hat{y}^{(i)})]$
    * 

---

### Slide 4: The General Gradient Descent Rule

* **Heading:** How We Update Parameters
* **Content:**
    * Explain the general concept of gradient descent: iteratively taking steps in the direction opposite to the gradient.
    * Show the general update rule:
        $parameter := parameter - \alpha \times \frac{\partial J}{\partial parameter}$
    * Define the terms:
        * **Parameter:** $w_j$ or $b$.
        * **Learning Rate ($\alpha$):** The step size.
        * **Gradient ($\frac{\partial J}{\partial parameter}$):** The slope of the cost function with respect to the parameter.
    * State the task: We need to derive the gradient for both $w_j$ and $b$.

---

### Slide 5: Derivation - Step 1 (The Chain Rule)

* **Heading:** The Chain Rule
* **Content:**
    * Explain that we will use the chain rule to break down the complex derivative.
    * Show the breakdown for a single weight ($w_j$):
        $\frac{\partial L}{\partial w_j} = \frac{\partial L}{\partial \hat{y}} \times \frac{\partial \hat{y}}{\partial z} \times \frac{\partial z}{\partial w_j}$
    * Explain what each term represents:
        * $\frac{\partial L}{\partial \hat{y}}$: How the cost changes with the prediction.
        * $\frac{\partial \hat{y}}{\partial z}$: How the prediction changes with the linear input.
        * $\frac{\partial z}{\partial w_j}$: How the linear input changes with the weight.

---

### Slide 6: Derivation - Step 2 (Calculating the Derivatives)

* **Heading:** Calculating Each Piece
* **Content:**
    * **Derivative 1:** $\frac{\partial L}{\partial \hat{y}} = \frac{\hat{y}-y}{\hat{y}(1-\hat{y})}$
        * Briefly show the steps or state the simplified result.
    * **Derivative 2:** $\frac{\partial \hat{y}}{\partial z} = \hat{y}(1-\hat{y})$
        * Explain that this is a key property of the sigmoid function.
    * **Derivative 3:** $\frac{\partial z}{\partial w_j} = x_j$ and $\frac{\partial z}{\partial b} = 1$
        * This is the simplest part of the derivation, based on the linear equation.

---

### Slide 7: Derivation - Step 3 (Putting it all together)

* **Heading:** Combining the Pieces
* **Content:**
    * Show the substitution for the weight derivative:
        $\frac{\partial L}{\partial w_j} = \left( \frac{\hat{y}-y}{\hat{y}(1-\hat{y})} \right) \times (\hat{y}(1-\hat{y})) \times x_j$
    * Show the simplification:
        $\frac{\partial L}{\partial w_j} = (\hat{y}-y)x_j$
    * Show the substitution for the bias derivative:
        $\frac{\partial L}{\partial b} = \left( \frac{\hat{y}-y}{\hat{y}(1-\hat{y})} \right) \times (\hat{y}(1-\hat{y})) \times 1$
    * Show the simplification:
        $\frac{\partial L}{\partial b} = \hat{y}-y$

---

### Slide 8: The Final Update Rules

* **Heading:** The Final Gradient Descent Rules
* **Content:**
    * Present the final update rules, averaged over all $m$ examples.
    * **Weight Update Rule:**
        $w_j := w_j - \alpha \frac{1}{m} \sum_{i=1}^{m} [(\hat{y}^{(i)} - y^{(i)})x_j^{(i)}]$
    * **Bias Update Rule:**
        $b := b - \alpha \frac{1}{m} \sum_{i=1}^{m} [(\hat{y}^{(i)} - y^{(i)})]$
    * Explain that these are the equations used in every iteration of training to improve the model.

---

### Slide 9: Summary

* **Model Type:** A **classification** algorithm.
* **Key Component:** The **Sigmoid function** maps a linear combination of features to a probability.
* **Optimization:** **Log Loss** is used as the cost function, and **Gradient Descent** is the algorithm for minimizing it.
* **Application:** A powerful and fundamental algorithm used for binary classification in various fields.
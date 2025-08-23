### Slide 1: Title Slide

# The Coefficient of Determination
### Understanding how well your model explains the data.

---

### Slide 2: What is R-squared?

* The **Coefficient of Determination**, or **R-squared** ($R^2$), is a statistical measure that tells you the proportion of the variance in the dependent variable that is predictable from the independent variable(s).
* In simpler terms, it measures how well your regression model explains the variability of the output data.
* $R^2$ is a value between **0 and 1** (or 0% and 100%).
* A high $R^2$ indicates that the model's predictions closely match the actual data points. A low $R^2$ suggests the model doesn't explain much of the variability.

---

### Slide 3: The Formula Behind R-squared

* To calculate R-squared, we compare two key measures of variability.
* The formula is:
    $R^2 = 1 - \frac{SSR}{SST}$
* Where:
    * **$SST$** is the **Total Sum of Squares**.
    * **$SSR$** is the **Residual Sum of Squares**.

---

### Slide 4: Understanding the Components

* **Total Sum of Squares (SST):**
    * Measures the total variability in the dependent variable ($y$) around its mean ($\bar{y}$).
    * It represents the error you would have if your model simply predicted the mean for every single data point.
    * **Formula:** $SST = \sum_{i=1}^{m} (y^{(i)} - \bar{y})^2$
* **Residual Sum of Squares (SSR):**
    * Measures the variability that is **unexplained** by the model.
    * It's the sum of the squared differences between the actual data points ($y$) and your model's predictions ($\hat{y}$).
    * **Formula:** $SSR = \sum_{i=1}^{m} (y^{(i)} - \hat{y}^{(i)})^2$

---

### Slide 5: Interpreting the R-squared Value

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

### Slide 6: A Simple Example

* Imagine a model that predicts student exam scores based on hours studied.
* **SST** is the total variability in scores among all students.
* **SSR** is the remaining variability in scores after accounting for the hours they studied.
* If our model has an $R^2$ of 0.71, we can say that **71%** of the variation in student exam scores can be explained by the amount of time they spent studying. The other 29% is unexplained, likely due to other factors like prior knowledge or test-taking ability.

---

### Slide 7: Limitations of R-squared

* One major limitation is that $R^2$ **always increases** as you add more independent variables to the model, even if those variables are not statistically significant.
* This can be misleading and lead to **overfitting**, where a model becomes too complex and fits the random noise in the training data rather than the underlying pattern.
* A high $R^2$ doesn't necessarily mean the model is good or that the variables have a causal relationship.

---

### Slide 8: Adjusted R-squared

* To address the limitation of $R^2$, we use **Adjusted R-squared**.
* It penalizes the model for adding useless independent variables.
* **Adjusted $R^2$ only increases if a new variable improves the model more than would be expected by chance**. If the new variable is not helpful, Adjusted $R^2$ will decrease.
* This makes it a more reliable metric for comparing models with different numbers of predictors.

---
This video discusses the derivation of the intercept and slope coefficients in simple linear regression.
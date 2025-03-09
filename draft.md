# Linear Regression

## [model representation](https://github.com/imteekay/linear-regression/blob/main/model_representation.ipynb)

- [ ]  problem: house prediction
- [ ]  example of data points: two points
- [ ]  divide into two parts: feature (X) and target (Y)
- [ ]  plotting the data
- [ ]  model function for linear regression f(x) = xw + b
- [ ]  trying a random w and b to see if the mode fits the data
- [ ]  finding the best w and b that fit the data
- [ ]  plotting the new function
- [ ]  making a prediction for a new input

```
- `Linear function`: with random Ws and Bs, the model produces a function. For linear regression, the function is a line
  - Draw a line describing the data points (dataset behavior)
  - The line is a function built by the learning algorithm (model)
  - The function receives an input (features) and output a prediction (y-hat), the estimated value of y
  - The idea of the model is to ask what's the math formula for `f`
```

## [cost function](https://github.com/imteekay/linear-regression/blob/main/cost_function.ipynb)

- [ ]  The cost equation provides a measure of how well your predictions match your training data.
- [ ]  squared error cost function: sum of the square difference between the prediction and the real target over m training examples
- [ ]  For all the training examples, what's the cost of using a given W and B
- [ ]  Minimizing the cost can provide optimal values of w and b.

```markdown
- `Cost function`: it measures how well the model is performing
  - The model fits the data and we measure with the cost function if it's performing well
  - Model fitting is the process of choosing weights and biases so y-hat is close to the target value y
    - It will find best weights and biases
  - The cost function `J(w, b)` is the measure of the difference between the y-hat and the target value y
  - One way to computing the cost function is to use MSE or mean squared error
    - sum of the squared differences of y-hat and y
  - The goal of the model is to minimize the cost function `J(w, b)`
```

## [Gradient Descent](https://github.com/imteekay/linear-regression/blob/main/gradient_descent_for_linear_regression.ipynb)

- [ ]  compute the cost
- [ ]  compute the gradient for the cost
    - [ ]  chain rule (derivative of the cost function)
    - [ ]  compute for each training example
- [ ]  gradient descent using iterations to compute the cost and gradient
    - [ ]  update the weight and bias
    - [ ]  iteration is used for gradient convergence
        - [ ]  in each iteration, the cost should get smaller

```markdown
- `Gradient Descent`
  - Update the weight parameter relative to the cost function `J`
  - If `J` is a concave up parabola and the initial weight draws the point on the left side of the parabola, gradient descent will increase the weight because it has a negative slope because `w = w - alpha * (negative number)`
  - If the initial weight is on the right side, gradient descent will decrease the weight because the the slope is a positive number
  - Near the local minimum, the derivative becomes smaller because the update steps become smaller
  - Gradient descent stops at the local minimum
    - For a convex function (parabola), the local minimum is the global minimum
  - Checking gradient descent for convergence
    - Make sure gradient descent is working by seeing the cost getting minimized with more iterations (learning curve)
    - When the curve gets flattened, gradient descent converged and stopped learning
    - If the cost J increases with more iterations, it usually means the learning rate alpha was chosen poorly, it can be too large, or a bug in the code
```

```markdown
- `Learning rate`
  - Small alpha: small baby steps in the gradient descent when updating the weight. slow to converge
  - Big alpha: large steps and the cost function can not reach the most optimized weight
  - range of values: 0.001, 0.003, 0.01, 0.03, 0.1, 0.3, 1
```

## Vectorization

- [ ]  element-wise operations
    
    ```python
    a = np.array([ 1, 2, 3, 4])
    b = np.array([-1,-2, 3, 4])
    print(f"Binary operators work element wise: {a + b}")
    # Binary operators work element wise: [0 0 6 8]
    ```
    
- [ ]  vector dot-product: input x times the weight vector
- [ ]  speed up the process

## Multiple Variable Linear Regression

- [ ]  New problem: multiple variables
    - [ ]  features: size number of bedrooms, number of floors, age of home
    - [ ]  output: price
    - [ ]  example
    
    ```python
    X_train = np.array([[2104, 5, 1, 45], [1416, 3, 2, 40], [852, 2, 1, 35]])
    y_train = np.array([460, 232, 178])
    ```
    
    - [ ]  show the latex example for the matrix
- [ ]  parameters
    - [ ]  bias is a scalar value, a single value
    - [ ]  weight should be a vector of n values, where each weight is for a given feature (n features, n is 4 for this dataset)
- [ ]  model prediction
    - [ ]  illustrated as a function: f(x) = w0x0 + w1x1 + …
    - [ ]  illustrated as a vector dot product: f(x) = W X + b
- [ ]  showing a single prediction
    - [ ]  fixed bias and weights and 1 example
    - [ ]  loop through the n features and sum the product of x and w and then add b
    - [ ]  this gives a prediction for the chosen parameters
    - [ ]  single prediction using vectorization (dot product)
- [ ]  Compute the cost for multiple variables
    - [ ]  equation for the cost J = 1/2m sum(f(x) - y)^2
    - [ ]  show f(x) equation: f(x) = wx + b
        - [ ]  w and x are vectors to support multiple variables
    - [ ]  cost implementation using loop
    - [ ]  cost implementation using vectorization
- [ ]  Multiple variables gradient descent
    - [ ]  The first part is to compute the gradients (derivative) for the weight and bias
        - [ ]  one weight for each variable (or feature)
        - [ ]  update each weight in the gradient descent. show the update repetition math formula
        - [ ]  math formula on how to compute the cost function J gradient
        - [ ]  show the non-vectorized code
            - [ ]  for each training example, we should compute the error (m examples)
            - [ ]  compute the gradient for the weight: we need to do it for each feature (n features)
            - [ ]  compute the gradient for the bias
        - [ ]  vectorized code
            - [ ]  compute the error for all examples in one operation
            - [ ]  compute the gradient for the bias in one operation
            - [ ]  compute the gradient for the weight for all features in one operation
    - [ ]  In gradient descent, we have a loop that will iterate `num_iters` times, where `num_iters` is a hyperparameter we can pass to the model
        - [ ]  in each step of the loop, we get the gradients and update the bias and the weight
        - [ ]  in this loop, we can store the cost history in an array passing the `X`, `Y`, `w`, and `b` to the `cost_function`
        - [ ]  show the cost getting smaller with more iterations
        - [ ]  prediction for the examples using the new parameters b and w:
            prediction: 426.19, target value: 460
            prediction: 286.17, target value: 232
            prediction: 171.47, target value: 178
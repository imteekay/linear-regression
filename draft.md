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
# 第六周作业记录

## 解决Overfiting(high variance)

1. Using a smaller set of features.
2. Getting more training examples.
3. Increasing the regularization parameter λ.

## 解决Underfitting(high bias)

1. Trying to obtain and use additional features.
2. Adding polynomial features.
3. Decreasing the regularization parameter λ.

## Tips for applying for Machine Learning

1. Suppose you are training a regularized linear regression model. The recommended way to choose what value of regularization parameter to use is to choose the value of which gives the lowest **cross validation error**.

2. We should shuffle the data before spliting it into training / cross validation / test set.

3. A model with more parameters is more prone to overfitting and typically has higher variance.

4. For solving high bias problem, adding more features useful but adding more training example won’t help.

5. Adding more training data solves the high variance problem.

* linearRegCostFunction.m代码

```MATLAB
h_x = X * theta; % 12x1
J = (1/(2*m))*sum((h_x - y).^2) + (lambda/(2*m))*sum(theta(2:end).^2); % scalar

grad(1) = (1/m)*sum((h_x-y).*X(:,1)); % scalar == 1x1
grad(1) = (1/m)*(X(:,1)'*(h_x-y)); % scalar == 1x1
grad(2:end) = (1/m)*(X(:,2:end)'*(h_x-y)) + (lambda/m)*theta(2:end); % n x 1
```

* learningCurve.m代码

```MATLAB
for i = 1:m
    Xtrain = X(1:i,:);
    ytrain = y(1:i);

    theta = trainLinearReg(Xtrain, ytrain, lambda);

    error_train(i) = linearRegCostFunction(Xtrain, ytrain, theta, 0); %for lambda = 0;
    error_val(i)   = linearRegCostFunction(Xval, yval, theta, 0); %for lambda = 0;
end
```

* validationCurve.m代码

```MATLAB
for j = 1:length(lambda_vec)
    lambda = lambda_vec(j);

    theta = trainLinearReg(X, y, lambda);
    error_train(j) = linearRegCostFunction(X, y, theta, 0); % lambda = 0;
    error_val(j)   = linearRegCostFunction(Xval, yval, theta, 0); % lambda = 0
end
```

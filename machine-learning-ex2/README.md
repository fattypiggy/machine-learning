# 第三周作业记录

## ex2.m

* plotData.m代码

```MATLAB
pos = find(y==1); neg = find(y == 0);
% Plot Examples
plot(X(pos, 1), X(pos, 2), 'k+','LineWidth', 2, ...
'MarkerSize', 7);
plot(X(neg, 1), X(neg, 2), 'ko', 'MarkerFaceColor', 'y', ...
    'MarkerSize', 7);
```

* sigmoid.m代码

```MATLAB
g = 1 ./ (1 + e .^ -z);
```

* costFunction.m代码

```MATLAB
h_theta = sigmoid(X*theta);
J = (-1/m) * sum(y .* log(h_theta) + (1-y) .* log(1-h_theta));
grad = (1/m)*(X') * (h_theta - y);
```

* predict.m代码

```MATLAB
p = round(sigmoid(X * theta));
% round()四舍五入
```

## ex2_reg.m

costFunctionReg.m代码

```MATLAB
h_theta = sigmoid(X*theta);
J = (-1/m) * sum(y .* log(h_theta) + (1-y) .* log(1-h_theta)) + lambda/2/m * sum(theta(2:length(theta)) .^ 2);
grad(1) = (1/m)*(X'(1,:))*(h_theta - y);
grad(2:size(theta, 1)) = (1/m) * (X'(2:size(X',1),:)) * (h_theta - y) + lambda/m * theta(2:size(theta,1),:);
% grad(1)要单独处理
```

## Summary

这是第二次作业，代码难度不大。逻辑回归和上一节学到的线性回归有些不同，主要是逻辑回归不再需要梯度下降来学习参数。

# 第四周作业记录

* lrCostFunction.m代码

```MATLAB
H = sigmoid(X*theta);
T = y.*log(H) + (1 - y).*log(1 - H);
J = -1/m*sum(T) + lambda/(2*m)*sum(theta(2:end).^2);

ta = [0; theta(2:end)];
grad = X'*(H - y)/m + lambda/m*ta;
```

* oneVsAll.m代码

```MATLAB
for c = 1 : num_labels,
    initial_theta = zeros(n + 1 , 1);
    options = optimset('GradObj' , 'on' , 'MaxIter' , 50);
    [theta] = ...
        fmincg(@(t)(lrCostFunction(t , X , (y == c) , lambda)), ...
            initial_theta , options);
    all_theta(c,:) = theta';
end
```

* predictOneVsAll.m代码

```MATLAB
    C = sigmoid(X*all_theta');
    [M , p] = max(C , [] , 2);
```

* predict.m代码

```MATLAB
a1 = [ones(m, 1) X];
%size(a1)
%size(Theta1)

z2 = a1 * Theta1';
a2 = sigmoid(z2);
%size(a2)

a2 = [ones(size(a2,1), 1) a2];

z3 = a2 * Theta2';
a3 = sigmoid(z3);
%size(a3)

[val, index] = max(a3,[],2);

p = index;
```

## Summary

这是第三次作业，终于学到了神经网络这一块，继续努力。

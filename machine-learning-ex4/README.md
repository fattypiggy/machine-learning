# 第五周作业记录

* sigmoidGradient.m代码

```MATLAB
    g = sigmoid(z) .* (1 - sigmoid(z));
```

* randInitializeWeights.m代码

```MATLAB
    epsilon_init = 0.12;
    W = rand(L_out, 1 + L_in) * 2 * epsilon_init - epsilon_init;
```

* nnCostFunction.m代码

```MATLAB
    Z2 = [ones(m, 1), X] * Theta1';
    a2 = sigmoid(Z2);
    Z3 = [ones(m, 1), a2] * Theta2';
    H = a3 = sigmoid(Z3);
    [val, ind] = max(H, [], 2);
    for k = 1 : num_labels
        yy = y == k;
        hh = H(: , k);
        err = -yy .* log(hh) - (1 - yy) .* log(1 - hh);
        J = J + sum(err);
    end
    J = J / m;

    J = J + lambda / (2 * m) * (sum(sum(Theta1(:, 2 : end) .^ 2)) + sum(sum(Theta2(:, 2 : end) .^2)));

    for t = 1 : m
        a_1 = X(t, :); % [1 * 400]
        z_2 = [1, a_1] * Theta1'; % [1 * 401] * [401 * 25]
        a_2 = sigmoid(z_2); % [1 * 25]
        z_3 = [1, a_2] * Theta2'; % [1 * 26] * [26 * 10]
        a_3 = sigmoid(z_3); % [1 * 10]

        delta3 = a_3; % [1 * 10]
        delta3(y(t)) = delta3(y(t)) - 1;

        delta2 = delta3 * Theta2; % [1 * 10] * [10*26]
        delta2 = delta2(2 : end); % [1 * 25]
        delta2 = delta2 .* sigmoidGradient(z_2); % [1 * 25] .* [1 * 25]

        Theta2_grad = Theta2_grad + delta3' * [1, a_2]; % [26 * 1] * [1 * 10]
        Theta1_grad = Theta1_grad + delta2' * [1, a_1]; % [401 * 1] * [1 * 25]
    end
    Theta2_grad = Theta2_grad / m;
    Theta1_grad = Theta1_grad / m;

    Theta2_tmp = Theta2;
    Theta1_tmp = Theta1;
    Theta2_tmp(:, 1) = 0;
    Theta1_tmp(:, 1) = 0;
    Theta2_grad = Theta2_grad + lambda / m * Theta2_tmp;
    Theta1_grad = Theta1_grad + lambda / m * Theta1_tmp;
```

## Summary

这是第五次作业，还是有一定难度的，尤其是计算损失函数的时候。

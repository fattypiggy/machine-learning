# 第九周作业记录

* estimateGaussian.m代码

```MATLAB
mu = ((1/m)*sum(X))';
sigma2 = ((1/m)*sum((X-mu').^2))';
```

* selectThreshold.m代码

```MATLAB
cvPredictions = (pval < epsilon);     % m x 1
tp = sum((cvPredictions == 1) & (yval == 1)); % m x 1
fp = sum((cvPredictions == 1) & (yval == 0)); % m x 1
fn = sum((cvPredictions == 0) & (yval == 1)); % m x 1
prec = tp/(tp+fp);
rec = tp/(tp+fn);
F1 = 2*prec*rec / (prec + rec);
```

* cofiCostFunc.m代码

```MATLAB
%% %%%%% WORKING: Without Regularization %%%%%%%%%%
Error = (X*Theta') - Y;

J = (1/2)*sum(sum(Error.^2.*R));

X_grad = (Error.*R)*Theta;   % Nm x n
Theta_grad = (Error.*R)'*X;  % Nu x n

%% %%%%% WORKING: With Regularization
Reg_term_theta = (lambda/2)*sum(sum(Theta.^2));
Reg_term_x = (lambda/2)*sum(sum(X.^2));

J = J + Reg_term_theta + Reg_term_x;

X_grad = X_grad + lambda*X;             % Nm x n
Theta_grad = Theta_grad + lambda*Theta; % Nu x n
```

## Summary

本周实现异常检测算法(anomaly detection algorithm)，其特点是更多的正常数据，而异常数据较少，注意和监督学习有一定的区别。

第二个任务是协同过滤算法(collaborative filtering)来实现推荐算法。

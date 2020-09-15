# 第七周作业记录

* gaussianKernel.m代码

```MATLAB
sim = exp(-1*sum(abs(x1-x2).^2)/(2*sigma^2));
```

* dataset3Params.m代码

```MATLAB
C_list     = [0.01 0.03 0.1 0.3 1 3 10 30]';
sigma_list = [0.01 0.03 0.1 0.3 1 3 10 30]';
  
prediction_error = zeros(length(C_list), length(sigma_list));
result = zeros(length(C_list)+length(sigma_list),3);
row = 1;
  
for i = 1:length(C_list)
    for j = 1: length(sigma_list)
        C_test = C_list(i);
        sigma_test = sigma_list(j);

        model = svmTrain(X, y, C_test, @(x1, x2) gaussianKernel(x1, x2, sigma_test));
        predictions = svmPredict(model, Xval);
        prediction_error(i,j) = mean(double(predictions ~= yval));

        result(row,:) = [prediction_error(i,j), C_test, sigma_test];
        row = row + 1;
    end
end

% Sorting prediction_error in ascending order
sorted_result = sortrows(result, 1);
  
% C and sigma corresponding to min(prediction_error)
C = sorted_result(1,2);
sigma = sorted_result(1,3);
```

* processEmail.m代码

```MATLAB
% find index of the word in vocabList (if Exist)
index = find(strcmp(str,vocabList),1);

% Add the index in the vector word_indices
word_indices = [word_indices; index];
```

* emailFeatures.m代码

```MATLAB
for i = 1:length(word_indices)
    x(word_indices(i)) = 1;
end
```

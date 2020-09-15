# 第八周作业记录

* pca.m代码

```MATLAB
Sigma = (1/m)*(X'*X); % n x n
[U, S, V] = svd(Sigma);
```

* projectData.m代码

```MATLAB
U_reduce = U(:,[1:K]);   % n x K
Z = X * U_reduce;        % m x k
```

* recoverData.m代码

```MATLAB
U_reduce = U(:,1:K);   % n x k
X_rec = Z * U_reduce'; % m x n
```

* computeCentroids.m代码

```MATLAB
for i = 1:K
    idx_i = find(idx==i);
    centroids(i,:) = mean(X(idx_i,:));
end
```

* findClosestCentroids.m代码

```MATLAB
for i = 1:size(X,1)
    temp = zeros(K,1);
    for j = 1:K
        temp(j)=sqrt(sum((X(i,:)-centroids(j,:)).^2));
    end
    [~,idx(i)] = min(temp);
end
```

* kMeansInitCentroids.m代码

```MATLAB
randidx = randperm(size(X, 1));
centroids = X(randidx(1:K), :);
```

## Summary

本周学习了非监督算法: K-means和PCA算法。其中K-means是一种聚类算法，PCA(主成分分析)可用来降维，以加快机器学习的速度和效率。

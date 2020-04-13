# 第二周作业记录

* warmUpExercise.m代码

```octave
    A = eye(5);
```

* plotData.m代码

```octave
    plot(x, y, 'rx', 'MarkerSize', 10);
    ylabel('Profit in &10,000s');
xlabel('Population of City in 10,000s');
```

* gradientDescent.m代码(multi版相同)

```octave
    error = (X * theta) - y;
    theta = theta - ((alpha/m) * X'*error);
```

* computeCost.m代码(multi版相同)

```octave
    J = 1 / (2 * m) *sum((X*theta - y) .^ 2);
```

## Optional Assignments

featureNormalize.m代码

```octave
    mu = mean(X);
    sigma = std(X);
    X_norm = (X - mu) ./ sigma;
```

* normalEqn.m代码

```octave
    theta = inv(X' * X) * X' * y;
```

## Summary

这是我第一次学习[机器学习](https://www.coursera.org/learn/machine-learning)课程，非常喜欢[Andrew Ng](https://www.coursera.org/instructor/andrewng)教授的由浅入深授课风格。这也是我第一次使用Octave来进行机器学习的编程，说实在的，使用Octave编程和其他我学过的语言(比如C++)对比的话，尽早适应vectorization编程不仅会减少代码量，还能提升程序的效率，所以这一点和C++的for循环有着很大区别。

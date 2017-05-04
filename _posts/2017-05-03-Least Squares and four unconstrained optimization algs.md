---
layout: post
title:  "Least Squares and four unconstrained optimization algs"
categories: Machine_Learning
tags:  algorithms machine_learning optimization gradient_descent gauss_newton newton_metod Levenberg_Marquardt
author: Ziwei Zhu
---

* content
{:toc}


This article is for the lab seminar. I gave a presentation about least squares, and two solutions to the non-linear least squares. I also introduced the Levenberg-Marquardt algorithm and Newton' s method. Here I will explain them again.


## Definition of Least Squares

![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/definition%20of%20ls.png)

### Linear Least Squares
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/linear_ls.png)

### Non-linear Least Squares
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/non-linear%20ls.png)

## Gradient Descent

The main idea is the function decreases at the fastest speed towards the opposite direction of the gradient.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gradient descent.png)

## Gauss Newton Method

### Vectorize objective function
First vectorize the cost function.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton1.png)

### Zero gradient
Then, based on the main idea that the optimal parameters 𝒂 that minimize the cost function 𝜀 has to satisfy the equation that the gradient vector is equal to zero, we get the followings.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton2.png)

Rewrite the expressions.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton3.png)

### Iterative rule from Taylor expansion and zero gradient
It is very hard to find a closed form solution to this expression. So we need a iterative method to find the optimal solution. The basic idea of iterative is adding some changes to the current coefficients to get better ones closer to the optimum ones.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton4.png)

![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton5.png)
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton6.png)
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton7.png)

Now we have two important expressions.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton8.png)

Combine these two expressions together to generate the iterative method for finding the optimal 𝒂 to make the gradient of 𝜀 to be zero.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton9.png)

Now we got the rule of updating.
∆𝒂= 𝑱^− (𝒚 −𝒇(𝒂^((𝒌))))

### Algorithm
The algorithm can be summerized as belowing.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/gauss-newton11.png)

## Levenberg-Marquardt Algorithm
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/LM.png)

## Newton Method

### Solve euqations

At the first beginning, the newton method was introduced to solve f(x) = 0 which does not have closed-form solution. So we need an iterative method.

When it is the univariate case,
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/newton1.png)

When it is the multivariate case, the problem can be written as solving f(x) = 0 where f = {f1, …,fm}, x = {x1,..xn} 
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/newton2.png)

### Solve optimization problem

When it is the univariate case for optimization problem, we still use the newton method to solve an equation.
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/newton3.png)

When it is the multivariate case for optimization problem,
![]({{ site.url }}/resources/2017-05-03-Least%20squares%20and%20four%20unconstrained%20optimization%20algs/newton4.png)

## Conclusion and discussion
Least squares is a very popular method in many areas. In my recent project, I used it to achieve the ellipsoid fitting for the magnetometer calibration. And it can also be applied to estimate coefficients for models. The gradient descent and gauss-newton are two basic ways to solve non-linear least squares. Gradient descent is easy to implemented, and requires less computational power and time, but it has a bad performance at the aspect of converging. Gauss-newton can perform better than gradient descent, but it is more complecated and requires a lot of matrix multiplications and derivitive calculations. LM algorithm is one of the most popular method for least squares, which I think is based on a dynamic trade off between gradient descent and gauss-newton. Gauss-newton is from newton method, the difference between them is the order of derivitive they use. Gauss-newton uses the first order derivitive to calculate the updated value of the function, while newton uses the second order derivitive. More specifically, newton is to minimize the f(x + ∆x), while gauss-newton is to minimize f(x) + ∆xf'(x). However, the second order derivitive cost too much time to compute, so using first order derivitive is a good replacement.



## Reference

- [Gauss-Newton algorithm for nonlinear models](http://fourier.eng.hmc.edu/e176/lectures/NM/node36.html)
- [Newton-Raphson method (multivariate)](http://fourier.eng.hmc.edu/e176/lectures/NM/node21.html)
- [Levenberg-Marquardt algorithm](http://fourier.eng.hmc.edu/e176/lectures/NM/node37.html)
- [Gauss-Newton算法学习](http://www.voidcn.com/blog/jinshengtao/article/p-6004352.html)
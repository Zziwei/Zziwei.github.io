---
layout: post
title:  "HMM and Baum Welch Algorithm"
categories: Machine Learning
tags:  algorithms, Machine Learning
author: Ziwei Zhu
---

* content
{:toc}


This article is for the lab seminar. I gave a presentation about the paper ' [Fusion of Inertial and Depth Sensor Data for Robust Gesture Recognition](https://www.dropbox.com/s/imwdujgf4kdat04/Fusion%20of%20Inertial%20and%20Depth%20Sensor%20Data%20for%20Robust%20Hand%20Gesture%20Recognition.pdf?dl=0)'. The most important part of this paper is Hidden Markov Model and the algorithm of training the model which named Baum Welch algorithm. Here I will explain them.


## Hidden Markov Model (HMM) Definition

A Hidden Markov Model is a probabilistic model of the joint probability of a collection of random variables {O1,…OT, Q1,…QT}. The Ot variables are discrete observations and the Qt variables are “hidden” and discrete. 

1. Qt is a discrete random variable with N possible values {1….N}.
2. The observation is one of L possible observation symbols, Ot ∈ { o1 . . . oL }. 
3. Transition matrix A = {aij} = P(Qt = j | Qt-1 = i}, is an N by N matrix.
4. The special case of time t = 1 is described by the initial state distribution πi = P(Q1 = i).
5. The probability of a particular observation vector at a particular time t for state j is described by: 
<p align='center'>bj(Ot) = P(Ot = ot | Qt = j). (B={bij} is an L by N matrix).</p>

Therefore, we can describe a HMM by: λ = (A,B,π ).
![](http://gekkoquant.com/wp-content/uploads/2014/05/hidden-markov-model.png)


## Conditional Independence Assumptions
![](https://github.com/Zziwei/Zziwei.github.io/blob/master/_resources/2017-02-24-HMM-and-Baum-Welch-Algorithm/conditional%20independence%20assumptions.PNG)

## Model Training
![](https://github.com/Zziwei/Zziwei.github.io/blob/master/_resources/2017-02-24-HMM-and-Baum-Welch-Algorithm/model%20training%20objective%20formular.PNG)
that is, find the HMM λ, that maximizes the probability of the observation sequence O.

### Two probabilities for training

The probability of the t-th state Qt = i, given the observation sequence O and model λ.
Compute P(Qt = i | O, λ) denoted as 𝛾𝑖(𝑡).

The probability of the t-th state Qt = i and t+1th state Qt+1 = j, given the observation sequence O and model λ.
Compute P(Qt = i, Qt+1 = j | O, λ) denoted as 𝜉𝑖𝑗(𝑡).

## Forward Algorithm
Compute P(Qt = i, O1…t | λ), denoted as α𝑖(𝑡).
The probability of seeing the partial sequence O1…Ot and the tth state Qt = i, given the model λ

![](https://github.com/Zziwei/Zziwei.github.io/blob/master/_resources/2017-02-24-HMM-and-Baum-Welch-Algorithm/forward%20alg..PNG)

## Backward Algorithm
Compute P(Ot + 1 … T | Qt = i, λ), Marked as 𝛽𝑖(𝑡).
The probability of seeing the ending partial sequence Ot + 1…OT , given the tth state Qt = i and the model λ.

![](https://github.com/Zziwei/Zziwei.github.io/blob/master/_resources/2017-02-24-HMM-and-Baum-Welch-Algorithm/backward%20alg..PNG)

## Baum Welch Algorithm
![](https://github.com/Zziwei/Zziwei.github.io/blob/master/_resources/2017-02-24-HMM-and-Baum-Welch-Algorithm/baum%20welch%20alg..PNG)

## Reference

- [Hidden Markov Model From Wikipedia](https://en.wikipedia.org/wiki/Hidden_Markov_model)
- [The Baum–Welch algorithm for estimating a Hidden Markov Model](http://www.ph.biu.ac.il/faculty/kanter/BW.pdf)
---
layout: post
title:  "P and NP Problem"
categories: Algorithms
tags:  algorithms p&np
author: Ziwei Zhu
---

* content
{:toc}

This article is for the lab seminar. I gave a presentation about the P & NP problem. Here I will simply explain the definitions about these problems.


## P Problem

The class P consists of all those decision problems that can be solved on a deterministic sequential machine in an amount of time that is polynomial in the size of the input


## NP Problem

The class NP consists of all those decision problems whose positive solutions can be verified in polynomial time given the right information

As a result, we can know that 

<p align='center'>P ⊆ NP</p>


## NP-Complete
1. An NP problem.
2. NP-complete problems are a set of problems to each of which any other NP-problem can be <b>reduced</b> in polynomial time.

<b>Reduced</b> means that one the solution of one problem (A) can be used to another problem (B). So problem A is harder than B.
e.g. the solution of quadratic equation with one unknown can be used to solve linear equation with one unknown

## NP-hard

NP-hard problems are those at least as hard as NP problems, i.e., all NP problems can be reduced (in polynomial time) to them. NP-hard problems need not be in NP.

## Relationships Among Four Problems

![](https://i.stack.imgur.com/CFDuq.png)


## Reference

- [P vs NP problem From Wikipedia](https://en.wikipedia.org/wiki/P_versus_NP_problem)

---
layout: post
title:  "Synchronous Dynamic View Learning for Activity Recognition"
categories: Machine_Learning
tags:  transfer_learning machine_learning
author: Ziwei Zhu
---

* content
{:toc}


This article will present an IPSN 2017 paper named "[Synchronous Dynamic View Learning: A Framework for Autonomous Training of Activity Recognition Models using Wearable Sensors](http://epsl.eecs.wsu.edu/wp-content/uploads/2017/03/IPSN-Rokni.pdf)" about an autonomous training algorithm for human activity recognition by wearable IMUs. It was initialy for the ESP lab seminar. I will concisely explain the algorithm of the paper here.


## Motivation
* Human activities recognition is increasingly popular with the emerging of the concept of the Internet of Things.
* Wearables are deployed in highly dynamic and uncontrolled environments
* Machine learning algorithms learn a model based on a set of training data that is collected in a controlled environment. The outcome of the algorithms, however, changes significantly, when the system is utilized in a situation different than that of the training.
* Activities recognition algorithms need to be reconfigured (i.e., retrained) upon any changes in configuration of the system, such as addition/ removal of a sensor to/ from the network, displacement/ misplacement/ mis-orientation of the sensors, replacement/ upgrade of the sensors, adoption of the system by new users, or changes in physical/ behavioral status of the user.


## Objectives
* This paper focuses on cases where a new sensor is added to the system and the new sensor is worn/used on various body locations.
* Addressing the problem of expanding pattern recognition capabilities from a single setting algorithm with a predefined configuration to a dynamic setting where sensors can be added, displaced and used unobtrusively.


## Innovations
* The proposed approach allows to transfer machine learning knowledge from an existing sensor, called static view, to a new dynamic sensor, called dynamic view, and these capabilities are calibrated through the sensing observations made in the dynamic view. And refer to this problem as Synchronous Dynamic View Learning (SDVL).
* The paper formulates SDVL problem using Linear Programming, introduces a similarity graph modeling of the problem, and propose an iterative updating approach to solve the problem.


## Proposed Approach

### SDVL Framework Overview
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/SDVLframework.png)

### Term and Symbol Definitions
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/TermandSymbolDefinitions.png)

### SDVL Problem Formulations
The paper models the SDVL problem as a linear programming problem. And because in the linear programming model, there are some parameters are unknown for the system, it is difficult to solve the problem. The proposed algorithm does not refer to the model, thus, in this article, I will not show the mathmatics.


### Ambiguity Relation
Define Ambiguity Relation to assist to represent the misclassification for static views.
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/AmbiguityRelation.png)

### Likelihood Deficiency
Define Likelihood Deficiency to represent the probability distribution of the misclassification for static views.
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/LikelihoodDeficiency.png)

### Semi-Label
Define semi-lable for the transfer learning. The Dynamic views will use the semi-lables rather than ground truth lables.
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/SemiLabel.png)

### Synchronous Dynamic View Learning Algorithm
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/SynchronousDynamicViewLearningAlg.png)

### Minimum Disagreement and Similarity Graph
Define the Minimum Disagreement and Similarity Graph to represent the relationship among each training data sample with a semi-label. Based on the Minimum Disagreement and Similarity Graph, the semi-label can be refined.
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/MinimumDisagreementandSimilarityGraph.png)
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/MinimumDisagreementandSimilarityGraph2.png)

### Label Refinement Algorithm
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/LabelRefinementAlg.png)
![]({{ site.url }}/resources/2017-07-14-Synchronous%20Dynamic%20View%20Learning%20for%20Activity%20Recognition/LabelRefinementAlg2.png)

## Experiments
This paper introduce two public databases of human activity and one dataset of their own. The researchers did very comprehensive experiments to show the performances with different parameter settings, different databases, different classification algorithms, different sensor settings, and different feature sets. They also investigated many existing algorithms and compared the performances. The result is that the proposed algorithm outperformed other methods. 


## Conclusion and discussion
This paper is very interesting. The research topic is significant and has practical values. The proposed algorithm is not that innovative and complex, but it is very inspiring. And it gives a satisfactory explanation of its method. The most important things I learn from this paper is its way to presenting algorithms and mathematics, and how the paper illustrate the values of its work. Besides, a comprehensive and explainable experiment can also powfully improve the quality of the paper and the research work.

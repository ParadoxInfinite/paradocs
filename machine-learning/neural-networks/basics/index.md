---
author:
    name: Samarth
    avatar: /paradox.jpg
    email: s.samarthkulkarni@gmail.com
    link: https://github.com/ParadoxInfinite/
date: 2026-03-19T11:03
title: Basics of Neural Networks
categories: [neural-networks, ai, machine learning, data structures]
description: Notes for the future about the basics of neural networks 
image: 
---
# Basics of Neural Networks

## Neural Network
This will just be a few definitions that I think are important to know and understand. Most of these will be based on my short-comings and lack of knowledge that lead them to be classified as important.

Most of these notes are derived/written after watching and understanding [3Blue1Brown's video series' first video](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi). More notes will follow along as I watch and understand more.

### Actuation value
Any data point will have some value that makes it active or inactive. There are multiple ways to find this value, notably:
>>>Sigmoid function
It is an increasing value from 0 to 1. It works on the basis where >0.5 is active and <=0.5 is inactive.
!!!
This supposedly contributes to slower learning rates in models. Hence ReLU is the preferred function. 
!!!
![|500](/imgs/sigmoid-function.png)
>>>ReLU (Rectified Linear Unit)
It is a flat value until 0 and then increasing after, basically `max(0, activation_value)`. This is only active when the value is >0, anything <=0 is considered inactive.
![|500](/imgs/relu-function.png)
>>>

### Weights

Neural networks are comprised of multiple layers (input -> N hidden layers -> output), there are a number of neurons in each of these layers. Each neuron in each layer has a weight associated with it so that the model can be finetuned to get the optimal result. Weights represent the significance of whatever attribute that layer's neuron is representing.

## Bias
Bias is a value similar to weights but it is more subtractive than additive. Instead of highlighting the significance, bias introduces the difference until which the activation should be ignored. Example: For a sigmoid function, the bias can be -0.03 (anything >-0.03 can be considered active), or for a ReLU function, the bias can be 0.4 (Any value <0.4 will be considered inactive). This in conjunction with weights allow for greater finetuning.

### Actuation value calculation
Down the layers of neural network, you need to calculate a value between 0-1 for the neuron to hold, so, the function that the neuron uses to compute this value from all the previous inputs is:
$$
\displaystyle a^{(n)}_{1...n} = Sigmoid/ReLU of (\left( \sum_{m=0, n=0}^{m,n} w_{m,n} \right) + \left( \sum{a^{(n-1)}_{0...n-1}} \right) \left( \sum_{n=0}^n b_n \right)
\\\\[2ex]
Where \\ a^{(n)}_{1...n} = The\: actuation\: value\: from\: layer\: 1\: onwards \\
\sum_{m=0, n=0}^{m,n} w_{m,n} = The\: weight\: of\: each\: neuron\: in\: each\: layer \\
\sum{a^{(n-1)}_{0...n-1}} = The\: actuation\: value\: from\: the\: previous\: layer\: (starts\: from\: layer\: 0) \\
\sum_{n=0}^n b_n = The\: bias\: added\: to\: each\: neuron\: in\: each\: layer
$$

### Vectors
!!!
The vectors in Physics are similar in concept, but the understanding is very different.
!!!
In Physics, a vector is defined as a value that has both magnitude and direction. In computer science/math/machine learning, a vector is a list/array of ***ordered*** values (values = magnitude, order = direction).

Vector DBs are something I'll have to look into soon, since they are quite effective here.

For now, this is all. I'll update more here (if it is suitable, or if not I'll create a different page as I learn more)
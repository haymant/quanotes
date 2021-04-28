==========================
``Notes of Deep Learning``
==========================


Introduction
============

- Knowledge Base (hard coded Knowledge)
- Machine Learning (extract own knowledge/pattern from raw data)
 
 * Methods
   
  a. Logistic Regression
  b. Naive Bayes

 * Heavily based on Representation

  Feature Engeering goal is usually to separate `factors of variation`  

  a. Manual Feature Engineering
  b. Representation Learning (e.g., AutoEncoder)

    When it's hard to get Representation or at same hard level to solve the problem,
    this step doesn't help. Deep Learning solves the problem.

- Deep Learning

 * e.g., Feedforward network (Multilayer perceptron MLP): A perceptron is
   is a math function mapping input to output, thus providing new Representation.
 * Depth could be considered as steps of a program to learn. It implies later layers
   can refer to earlier layers, e.g., AI can find an eye with clear shape, this
   will help to find the face, and then the detected face would help to find
   another eye with blurred shape.

Sample Applications
===================

Simplest case: input (size), neuron (ReLu, Linear Regression), output (house price)

A bit more complex:

- input: x1 (house size), x2 (room number), x3 (zip code), x4 (wealth)
- hidden layer of neurons: family size, school qualityu, walkability
- output: house price

Supervised Learning

+---------------+---------------------+---------+
| Input         | Output              | NN      |
+===============+=====================+=========+
| Hose Features | Price               | Standard|
+---------------+---------------------+---------+
| Ad User Info  | Click Ad            | Standard|
+---------------+---------------------+---------+
| Image         | Object name         | CNN     |
+---------------+---------------------+---------+
|Audio(sequence)| Text Scripts        | RNN     |
+---------------+---------------------+---------+
| English       | Chinese             | RNN     |
+---------------+---------------------+---------+
| Radar, Images | Position of others  | Custom  |
+---------------+---------------------+---------+

Scale Drives Deep Learning Progress
===================================

- Data
- Computation (Sigmoid switch to ReLu, due to slow change of Sigmoid sloop)
- Algorithms

Key Topics
==========

- Neural Network and Deep Learning
- Improvement Directions
  
  1. Hyperparameter tuning
  2. Regularization
  3. Optimization

- Machine Learning Project Structure
- CNN convolutional NN
- NLP: sequence models
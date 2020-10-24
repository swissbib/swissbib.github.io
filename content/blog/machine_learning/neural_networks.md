---
title: "An Attempt to Copy Human Learning with the Help of Artificial Neural Networks"
author: "Andreas Jud"
description: "using neural networks"
date: 2020-10-24T17:43:00+02:00
draft: false

tags: [neural networks, english, 2020]
categories: [Machine Learning]
---


Besides the availability of data, one additional reason why Machine Learning has become a popular topic has to do with publicly available code libraries that simplify the implementation of machines. One such library is <a href="https://www.tensorflow.org/?hl=en" target="_blank">TensorFlow</a>, an open-source platform written by <a href="https://en.wikipedia.org/wiki/Google_Brain" target="_blank">Google Brain</a>. TensorFlow can be used for implementing Neural Networks. Since end of 2019 a library called <a href="https://keras.io/" target="_blank">keras</a> has been integrated on top of TensorFlow. This library makes the code implementation of Neural Networks even easier. The swissbib project at hand is as far as known the first implementation of a Neural Network for deduplication based on keras. This blog article explains Neural Networks and compares the results of its implementation with the results of the preceding blog articles.

The strength of a conventional computing machine is its ability to execute arithmetic and logical operations extremely fast. This is due to its hardware, consisting of semiconductor transistors as building blocks. A conventional computing machine needs a sequence of precise and syntactically correct commands for executing a task. Any error or inaccuracy in such a sequence of commands will bring the machine to fail its execution. For this lack of fault tolerance, conventional machines have no ability to learn from data. The human brain on the other hand, is strong in learning and transferring learnt patterns to new and unknown conditions. This ability helps in handling errors and inaccuracies, it is even able to predict results under unknown situations. It is a strength of solving semantic tasks. Its abilities are based on its building blocks, the <a href="https://en.wikipedia.org/wiki/Neuron" target="_blank">electrically excitable nerve cells</a> called neurons together with their network structure. A neuron is a biological cell with the ability to propagate an electrical signal to its neighbouring cells. Artificial Neural Networks are the attempt to copy the functionality of a system of biological nerves with the goal of making use of the strengths of such systems.

With regard to the specific swissbib problem at hand, the <a href="/blog/machine_learning/support_vector_machines/" target="_blank">second blog article</a> talks about a boundary, separating the records of pairs of uniques from the records of pairs of duplicates. As soon as the position of this boundary is determined, a conventional computing machine can decide very quickly to which side a new and unknown record is to be associated. It is the learning process on where to place the best boundary in the training data set, that is best resolved with the help of statistical learning like e.g. an artificial Neural Network. The building blocks of an artificial Neural Network are a try to copy the mode of operation of the building blocks of a biological neural network. The signal processing of a biological nerve cell is described with the help of a physical model which can be read <a href="https://en.wikipedia.org/wiki/Hodgkin-Huxley_model" target="_blank">elsewhere</a>. Besides the mode of operation of its building blocks, the network topology is fundamental for the abilities of a Neural Network. In Computer Science, there are several known topologies used for the network structure of neurons. Certain topologies have been invented, developed, and used for specific kinds of problems to solve. A nice animation is shown in the youtube video below.
{{< youtube 3JQ3hYko51Y >}}  

As for the topology of an artificial Neural Network, one set of neurons forms an input layer for the data records to be processed, see figure 1. Another set of neurons forms an output layer for classifying the input record to either a record of uniques or a record of duplicates for the swissbib data. In between these boundary layers, the so called hidden layers may be found. Each artificial neuron of one specific layer is connected to each neuron of its neighbouring layers. Each connection between two neurons has a weight which multiplies the output signal of a source neuron to generate one of the input signals of a target neuron. The training process adjusts these connections continuously together with a threshold value that determines the output of a neuron as a function of its input. This is done, comparing the answer of the network with its expected result after applying the signal of a record to the input layer. The training process can be terminated when any further adjustments do not significantly improve the output compared to the expected results anymore. The specific values of the weights together with the thresholds of the artificial neurons are the result of the training process.

<a href="/image/ml/neural_network.png" target="_blank"><img style=" width: 100%; height: 100%;" src="/image/ml/neural_network.png"/></a>
------------------------

figure 1, neural network
-----------------------
<br/>
<br/>

For the swissbib project at hand, a Neural Network with two hidden layers between the input and the output layers has been implemented, see figure 1. The input layer consists of twenty neurons, one for each distinct similarity of a feature record, described in the <a href="/blog/machine_learning/ensemblemethods" target="_blank">first blog article</a>. The output layer holds two neurons, one that fires a signal if the input record is identified as a record of pairs of duplicates and another one that fires a signal if the input record is identified as a record of pairs of uniques. The first hidden layer that is connected to the input layer as its input and to the second layer as its output layer, consists of 40 neurons in the best topology found for the project. The second hidden layer that is connected to the first hidden layer as its input and to the output layer as its output layer, consists of 75 neurons in the topology of the Neural Network found with the best performance values. In terms of accuracy, a value of 99.93% has shown to be an upper limit that no Neural Network tested could exceed. This maximum accuracy is lower than the best accuracy values of the best Random Forests model of the <a href='/blog/machine_learning/ensemblemethods/' target="_blank">first blog article</a> but it is higher than the best accuracy values of the Support Vector Machine approach described in the <a href="/blog/machine_learning/support_vector_machines/" target="_blank">second blog article</a>. This maximum accuracy for the Neural Network means a number of wrong predictions of close to 30 on a total of 51'886 validation records.

It is remarkable to point out the big amount of artificial neurons of the hidden layers used for the project at hand. This big amount of neurons may hint to a strong need of interactions between the features for the Neural Network to be a successful classifier. The project tries topologies of one, two, and three hidden layers and observes that a two layer network generates the best results in relation to its training duration. One property found for the Neural Network eventually related to the high number of neurons is its low learning rate value of ideally 0.002 which makes the learning process very slow but gives more stability to the network during its learning phase. This is expressed in a slowly converging learning curve during the training process, see figure 2.

<a href="/image/ml/converging_learning.png" target="_blank"><img style=" width: 100%; height: 100%;" src="/image/ml/converging_learning.png"/></a>
------------------------

figure 2, converging learning curve
-----------------------
<br/>
<br/>

Comparing the accuracy of the Neural Network solution described here with the <a href='/blog/machine_learning/ensemblemethods/' target="_blank">results of a Random Forests model</a> and with the <a href='/blog/machine_learning/support_vector_machines/' target="_blank">results of a Support Vector Machine</a>, the project finds Neural Networks that rank in between the two former described methods. Although all models are close together in their accuracy values, this ranking seems to be reproducible in a stable manner. This observation that Random Forests outperform even big Neural Networks might be a hint to the nature of deduplicating records. When deciding on whether a pair of records is a record of duplicates, a series of decisions on a sequence of attributes is taken. At each step, a decision is taken on whether the attributes are close to or far away from each other. A Decision Tree and eventually its statistically more sophisticated Random Forests implementation may be the most adequate algorithm for taking this series of decisions.

By the end of the project, a doubt has arisen that this might be the only reason, though. This doubt is caused by the data used for training. Some suspicion on the reliability of the training data has appeared and human assessment of wrongly predicted records have generated a positive doubt that the prediction of the artificial machine may be better than the label of the training record. This is surprising and points out the requirement of looking closely at the process of generating the data and at the data itself. The scenario to be explored is to improve the quality of the training data by looking at the results of an artificial machine and hence learn from this machine about the data. Before doing so, a close look has to be taken at how the data is processed. After all methods are described, time is up to have a close look at the data, a look at how the data is processed, generated and at its final quality for training and performance assessment. This will be done in the next blog article.


[Einführungsartikel: warum beschäftigen wir uns mit Methoden des Maschinellen Lernens](/blog/machine_learning/background_de)  
[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)  
[Part1: ensemble methods](/blog/machine_learning/ensemblemethods)  
[Part2: support vector machines](/blog/machine_learning/support_vector_machines)


<a href="https://www.linkedin.com/in/andreas-jud-2a39a770/" target="_blank">Author: Andreas Jud</a>

---
title: "NN"
author: "Andreas Jud"
description: "using neural networks"
date: 2020-09-13T13:31:00+02:00
draft: true

tags: [neural networks, english, 2020]
categories: [Machine Learning]
---


Besides the availability of data, one additional reason why Machine Learning has become a popular topic has to do with publicly available code libraries that simplify the implementation of machines. One such library is <a href='https://www.tensorflow.org/?hl=en', target="_blank">TensorFlow</a>, an open-source platform written by <a href='https://en.wikipedia.org/wiki/Google_Brain', target="_blank">Google Brain</a>. TensorFlow can be used for implementing Neural Networks. Since end of 2019 a library called <a href='https://keras.io/', target="_blank">keras</a> has been integrated on top of TensorFlow. This library makes the code implementation of Neural Networks even easier. The swissbib project at hand is as far as known the first implementation of a Neural Network for deduplication based on keras. This blog article explains Neural Networks and compares the results of its implementation with the results of the preceding blog articles.

The strength of a conventional computer machine is its ability to execute arithmetic and logical operations extremely fast. This is due to its hardware, consisting of semiconductor transistors as building blocks. For executing a wanted task, a conventional computer machine needs a sequence of precise and correct commands. Any error in such a sequence of commands will bring the machine to fail its execution. So, there is no fault tolerance and the conventional machines have no ability to learn from data and apply the learnt patterns to unknown data. One great advantage of the human brain, on the other side is its ability to learn unknown patterns from data and apply these to unknown data. In the preceding blog articles, different algorithms have been presented to use statistical methods for having the same effect of learning patterns and applying them to unknown situations with the goal to predict a result. Neural Networks are the attempt to copy a system of biological nerves with the goal of making use of the strengths of such systems. In order to understand this analogy, it is helpful to fist understand the mode of operation of a biological neural network.

A <a href='https://en.wikipedia.org/wiki/Neuron', target="_blank">neuron or a nerve cell is an electrically excitable cell</a>. It roughly consists of the cell body, called soma and an axon for carrying an electric signal. At the end of the axon, there are several synapses that connect to neighbouring neurons, forming a network structure. The synapses serve as communication channels with its connected neighbouring target neurons. A neuron is a biological cell with the ability to propagate an electrical signal to its neighbouring cells. This propagation process is described with the physical model of <a href='https://en.wikipedia.org/wiki/Hodgkin-Huxley_model', target="_blank">Hodgkin-Huxley</a>. When an electrical signal arrives at a neuron, it propagates this signal only if it is strong enough which means the electrical strength of the incoming signal is above an activation threshold of the cell. If the activation threshold has been exceeded, the neuron propagates the signal via the axon and the synapses to all its connected neighbours. The synapses can have different connection strengths, generating input signal strengths in their target cells out of their connection outputs. The connection strengths between neurons constitute what the neural network has learnt.



There are several <a href='https://www.youtube.com/watch?v=3JQ3hYko51Y', target="_blank">topologies</a> => notion of complexity. The incredible abilities of the human brain originate from the complexity of the neural network.


Results of swissbib project at hand...
* discussion and interpretation of parameters


With Neural Networks, too, it is about Machine Learning, based on statistical methods. Nothing mystical!


Final summary :
* Compare different methods described in all three blog articles.
* Now, the data processing part has to be understood much better and deeper!


[Einführungsartikel: warum beschäftigen wir uns mit Methoden des Maschinellen Lernens](/blog/machine_learning/background_de)
[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)
[Part1: ensemblemethods](/blog/machine_learning/ensemblemethods)
[Part2: support vector machines](/blog/machine_learning/support_vector_machines)


<a href="https://www.linkedin.com/in/andreas-jud-2a39a770/" target="_blank">Author: Andreas Jud</a>

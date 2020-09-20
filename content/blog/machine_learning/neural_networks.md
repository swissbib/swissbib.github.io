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

The strength of a conventional computer machine is its ability to execute arithmetic and logical operations extremely fast. This is due to its hardware, consisting of semiconductor transistors as building blocks. For executing a wanted task, a conventional computer machine needs a sequence of precise and correct commands. Any error in such a sequence of commands will bring the machine to fail its execution. So, there is no fault tolerance and the conventional machines have no ability to learn from data and apply the learnt patterns to unknown data. One great advantage of the human brain, on the other side is its ability to learn unknown patterns from data and apply these learnt patterns to unknown data. In the preceding blog articles, different algorithms have been presented to use statistical methods for having the same effect of learning patterns and applying them to unknown situations with the goal to predict a result. Neural Networks are the attempt to copy the functionality of a system of biological nerves with the goal of making use of the strengths of such systems. In order to understand this analogy, it is helpful to first understand how a biological neural network works.

A <a href='https://en.wikipedia.org/wiki/Neuron', target="_blank">neuron or a nerve cell is an electrically excitable cell</a>. It roughly consists of the cell body, called soma and an axon for carrying an electric signal. At the end of the axon, there are several synapses that connect to neighbouring neurons, forming a network structure. The synapses serve as communication channels with its connected neighbouring target neurons. A neuron is a biological cell with the ability to propagate an electrical signal to its neighbouring cells. This propagation process is described with the physical model of <a href='https://en.wikipedia.org/wiki/Hodgkin-Huxley_model', target="_blank">Hodgkin-Huxley</a>. When an electrical signal arrives at a neuron, it propagates this signal only if it is strong enough which means the electrical strength of the incoming signal is above an activation threshold of the cell. If the activation threshold has been exceeded, the neuron propagates the signal via the axon and the synapses to all its connected neighbours. The synapses can have different connection strengths, generating input signal strengths in their target cells out of their connection outputs. The connection strengths between neurons constitute what the neural network has learnt.

Neural Networks in Computer Science are the attempt to copy the very building blocks of a biological neural network together with their behaviour. This is done with the goal of making use of the power in functionality of a biological neural network. The building blocks of a Neural Network are units called artificial neurons. Each neuron gets one or more input signals a number that the neuron sums up to a total input signal strength. Each neuron has its own specific threshold that is the triggering threshold for firing a signal if the input signal exceeds the threshold or remains quiet if the input signal remains below. The artificial neurons are connected with each other building a specific network topology. In such a topology, one set of neurons has to form an input layer for the data records to be processed and one set of neurons form an output layer for the classification result. An arbitrary amount of layers with an arbitrary amount of artificial neurons in between these two boundary layers constitute the specific topology of the network. Each connection between two neurons has a weight which multiplies the output signal of a source neuron to generate one of the input signals of a target neuron. During the training process, a network of neurons of a predefined topology processes an input record through the network and compares the output of the network with the expected result of the network, the target value of the record. If the network happens to have found the correct class for the training record, no change of the values is needed and the next record can be processed. If the network classifies the training record wrongly, the weights and thresholds of the network are adjusted in order to reproduce a result closer to the expected result. At the end of the training process, the specific values of the weights together with the thresholds of the artificial neurons are its result. Applying a new and unknown record to this trained network from its input layer processes this record in the same way to its output layer, computing the correct classification for the record in the ideal case.

In Computer Science, there are several known topologies used for the network structure of neurons. A certain topology has been invented, developped and used for specific kinds of problems to solve. A nice animation is given in the <a href='https://www.youtube.com/watch?v=3JQ3hYko51Y', target="_blank">YouTube animation, shown here</a>. It may be a challenge for a developper to find the best network topology for a specific problem at hand. The network character of a neural network brings the notion of <a href='https://en.wikipedia.org/wiki/Complex_system', target="_blank">complexity</a> into play. Looking at the human brain as a neural network with an incredible amount and range of abilities of functionality, it becomes clear, why the human brain must be the most complex network known at the time being. The complexity of the human neural network is unrivalled by any artificial neural network at least for the moment. For this reason, the results presented here address the specific problem of identifying duplicates in a record of pairs of swissbib data, cp. the description of the <a href='/blog/machine_learning/ensemblemethods' target="_blank">first blog article</a>. The solution can handle a big mass of data and process it quickly depending on computational power and although it is based on the functioning of a biological brain, it remains a method for solving exactly the specific problem of deduplication of the given swissbib data. Again, with Neural Networks, it is about Machine Learning which is based on statistical methods and there is <a href='/blog/machine_learning/support_vector_machines' target="_blank">nothing mystical</a> about it.

For the swissbib project at hand, a Neural Network has been implemented with two layers between the input and the output layers has been implemented, see figure. These two layers are called hidden layers. The input layer consists of twenty neurons, one for each distinct similarity of a feature record, described in the <a href='/blog/machine_learning/ensemblemethods' target="_blank">first blog article</a>. The output layer holds two neurons, one that fires a signal if the input record is identified as a record of pairs of duplicates and another one that fires a signal if the input record is identified as a record of pairs of uniques. The first hidden layer that is connected to the input layer as its input and to the second layer as its output layer, consists of 40 neurons in the best topology found for the project. The second hidden layer that is connected to the first hidden layer as its input and to the output layer as its output layer, consists of 75 neurons in the topology of the Neural Network found with the best performance values. In terms of accuracy, a value of 99.93% has shown to be an upper limit that no Neural Network tested could exceed. This maximum accuracy is lower than the best accuracy values of the best Random Forests model of the <a href='/blog/machine_learning/ensemblemethods/' target="_blank">first blog article</a> but it is higher than the best accuracy values of the Support Vector Machine approach described in the <a href='/blog/machine_learning/support_vector_machines/' target="_blank">second blog article</a>. This maximum accuracy for the Neural Network is close means about ??? ??? ??? wrong predictions on a total of 51'886 validation records.

It is remarkable to point out the big amount of artificial neurons of the hidden layers used for the project at hand. This big amount of neurons may hint to a strong need of interactions between the features for the Neural Network to be a successful classifier. The project has tried topologies of one, two, and three hidden layers and observes that a two layer network generates the best results in relation to its training duration. One property found for the Neural Network eventually related to the high number of neurons is its low learning rate value of ideally 0.002 which makes the learning process very slow but gives more stability to the network during its learning phase. This is expressed in a slowly converging learning curve, see figure during the training process.



Final summary :
* Compare different methods described in all three blog articles.
* Now, the data processing part has to be understood much better and deeper!


[Einführungsartikel: warum beschäftigen wir uns mit Methoden des Maschinellen Lernens](/blog/machine_learning/background_de)
[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)
[Part1: ensemble methods](/blog/machine_learning/ensemblemethods)
[Part2: support vector machines](/blog/machine_learning/support_vector_machines)


<a href="https://www.linkedin.com/in/andreas-jud-2a39a770/" target="_blank">Author: Andreas Jud</a>
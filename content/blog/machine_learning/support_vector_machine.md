---
title: "What Humans Learn about the Data from a Support Vector Machine"
author: "Andreas Jud"
description: "using Support Vector Machine"
date: 2020-08-20T16:07:50+02:00
draft: false

tags: [support vector machine, english, 2020]
categories: [Machine Learning]
---




Machine Learning may look mystical, although it is based on the mathematical discipline of statistics. If the learning process is done with a fixed data set, Machine Learning can be structured into two distinct groups of tasks, supervised and unsupervised learning. In supervised learning, the artificial machine is trained with a set of training data with a target value, each. In the <a href='/blog/machine_learning/ensemblemethods' target="_blank">first blog article</a>, the feature records and their associated target value have been introduced for the swissbib project at hand. The target value on a feature record declares wether the record is a record of a pair of duplicates or a record of a pair of uniques. Support Vector Machines are a popular method in the area of supervised learning, with its origins in the computer sciences community. In this blog, the results of a Support Vector Machine are presented. In Machine Learning, there are also methods for training artificial machines on data with missing target values. These methods are grouped as unsupervised learning, where k-means is a representative method. Both models, Support Vector Machine and k-means give some deeper insight into the underlying data.

In the <a href='/blog/machine_learning/ensemblemethods' target="_blank">first blog article</a>, the notion of a feature record has been introduced. From a mathematical point of view one single feature record can be considered a point in an n-dimensional space, with n equal to the number of twenty features in the swissbib project at hand. The deduplication problem of swissbib is a classification task. Explicitly, the artificial machine is trained to assign each point in the feature space to one of the two target classes, either the target value pair of uniques or the target value pair of duplicates. During the training process, a Support Vector Machine searches a boundary which separates the records of pairs of uniques from the records of pairs of duplicates. If this boundary is useful it clusters the points of the feature space that belong to the same class. If the feature space is 2-dimensional, it is a plane and the boundary is a line. This line need not necessarily be straight but may have an arbitrary shape which may make its mathematical representation arbitrarily complicated. In an n-dimensional space, this boundary is called a <a href='https://en.wikipedia.org/wiki/Hyperplane' target="_blank">hyperplane</a>. The best hyperplane for separating the records into its two classes may have a complicated mathematical representation. To avoid this issue and with the goal of separating the points with the help of a linear hyperplane, a Support Vector Machine can transform the feature space, instead. This transformation from a linear space to a non-linear space is done with a <a href='https://en.wikipedia.org/wiki/Kernel_method' target="_blank">kernel transformation</a> of the machine. The kernel transformation ideally separates the data points of the two classes. This trick is called the <a href='https://datamites.com/blog/support-vector-machine-algorithm-svm-understanding-kernel-trick/' target="_blank">kernel trick</a>. (There are several blogs in the internet, explaining the kernel trick visually. Search for Images on "kernel trick of support vector machine" in Google.)

In the project described, a Support Vector Machine is trained with the help of swissbib training data, using <a href='https://en.wikipedia.org/wiki/Cross-validation_(statistics)' target="_blank">cross-validation</a>. For the parameters of the classifier, a kernel with a <a href='https://en.wikipedia.org/wiki/Degree_of_a_polynomial' target="_blank">polynomial transformation of third degree</a> is found to generate the best results. With this classifier, an accuracy value of 99.88% can be reached. This accuracy is lower than the best accuracy values of the best Random Forests model of the <a href='/blog/machine_learning/ensemblemethods/' target="_blank">first blog article</a>. It means explicitly 60 wrong predictions on a total of 51'886 validation records.

A Support Vector Machine predicts the belonging of a data point to a class according to a probability value in the range of the interval from 0 to 1. The threshold value of 0.5 is the separator between the two classes. If the Support Vector Machine calculates a probability value in the interval from 0 to 0.5, then the classifier model assigns the feature record to the class of pairs of uniques. If the classifier model calculates a probability value in the interval from 0.5 to 1, then the machine assigns the feature record to the class of pairs of duplicates. Figure 1 shows the distribution of the records for some part of swissbib training data. The green line in the figure represents the threshold of 0.5, separating the data into its two classes.

<a href="/image/ml/svc_probability.opt.svg" target="_blank"><img style=" width: 100%; height: 100%;" src="/image/ml/svc_probability.png"/></a>
-----
Figure 1. Probability distribution of swissbib training data
------

<br/>
<br/>


Looking at figure 1, it is very interesting to observe the distance of the points from the classes separating threshold. It looks like most of the pairs of uniques lie on a line with a probability value of 1, while many of the pairs of duplicates lie on a line with a probability value of 0. These extreme points with probabilities at the probability boundaries 0 and 1 are the easy cases. More interesting are the points that have probability values between 1 and 0. These are the cases expressing some uncertainty. Even more interesting are the cases which are located on the wrong side of their class. These are the wrong predictions of the Support Vector Machine. Figure 1 shows some pairs of uniques in the domain area of duplicates and some pairs of duplicates in the domain area of uniques. These points have to be investigated deeper to understand why they are wrongly assigned. This task has to be done manually and will be subject of a later blog to come.

In spite of the wrong predictions, figure 1 proves that the Support Vector Machine trained is a useful model for predicting the class on swissbib data. There seems to be some criteria in the data that separate the two classes. Machine Learning offers several methods of unsupervised learning to investigate and eventually confirm this assumption. As an example, the capstone project uses the method of <a href='https://en.wikipedia.org/wiki/K-means_clustering' target="_blank">k-means</a> for further analysing the data. This method tries to cluster data without any target value information, generating a number of k clusters. For the swissbib project at hand, k=2 is suggested, namely for the class of records of pairs of uniques and the other class of records of pairs of duplicates. After training a k-means model with k=2 on the training data where having removed the target values from the feature records for training the model, the points predicted by the model can be coloured subsequently according to their target values known in truth from the training data. Assigning the colour red to records of pairs of duplicates and the colour of blue to records of uniques to the predictions of the trained k-means model, generates the graph of figure 2. Looking at figure 2, it shows the red points well clustered and separated from the cluster of blue points.

<a href="/image/ml/kmeans_traindata.opt.svg" target="_blank"><img style=" width: 50%; height: 50%;" src="/image/ml/kmeans_traindata.png"/></a>
--------------------------------
Figure 2. k-means clustering on training data
--------------------------------
<br/>
<br/>

Comparing figure 1 with figure 2, it is interesting to observe, that independent of wether either a supervised learning method or an unsupervised learning method is used, the data allows a clear separability between the classes. The patterns in the data, allowing for separability is learnt when training the models with the training data. On the other hand, the separability is neither complete or absolute. There are points that are wrongly classified, wrongly according their class-belonging in the training data. There are blue dots in the red domain and vice versa red dots in the blue domain. Those wrongly classified feature records have to be investigated deeper, they are the subject of discussion with swissbib data experts. Both figures, though, confirm that the data has some properties that help separating pairs of uniques from pairs of duplicates.

This blog article offers some insight into the properties of swissbib training data. This insight can be deepened analysing the underlying models and its statements. With this view, the trained machines talk to humans illustrating their mathematical background in a compacted manner. Discussing these results of different aspects helps humans to improve their understanding of the data. Humans can learn from the models, they can learn from the trained machines. This aspect of interaction between the two entities humans and machines is an important aspect, hardly discussed in the debate on Machine Learning and artificial intelligence.

When talking about intelligence, the human brain is considered to be its domicile. The human brain is an incredibly powerful network of neurons and therefore, Machine Learning tries to find results with the help of networks that simulate the human brain. The next blog article will explain the results of a Neural Network.

[Einführungsartikel: warum beschäftigen wir uns mit Methoden des Maschinellen Lernens](/blog/machine_learning/background_de)
[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)
[Part1: ensemble methods](/blog/machine_learning/ensemblemethods)


<a href="https://www.linkedin.com/in/andreas-jud-2a39a770/" target="_blank">Author: Andreas Jud</a>

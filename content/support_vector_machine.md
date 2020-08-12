---
title: "Support_vector_machine"
date: 2020-08-01T16:07:50+02:00
draft: true
---


# What Humans Can Learn about the Data from a Support Vector Machine
## What a Support Vector Machine Teaches Us about the Data



Machine Learning may look mystical, although it is based on the mathematical discipline of statistics. If the learning process is done with a fixed data set, Machine Learning can be structured into two distinct groups of tasks, supervised and unsupervised learning. In supervised learning, the artificial machine is trained with a set of labelled training data. In the first blog article, the feature records and their associated target value have been introduced. The target value on a feature record is the label, declaring wether the record is a record of a pair of duplicates or a record of a pair of uniques. Discarding the target value information from each feature record, the training data becomes unlabelled. In Machine Learning, there are also methods for training artificial machines on unlabelled data. These are called unsupervised learning. Support Vector Machines are a popular method, with its origins in the computer sciences community. Support Vector Classifiers are a method in the area of supervised learning. In this blog, the results of a Support Vector Classifier are presented together with a model of unsupervised learning. This gives some deeper insight into the underlying data.

In the first blog, the notion of a feature record has been introduced. From a mathematical point of view one single feature record can be considered a point in an n-dimensional space, with n equal to the number of twenty features in the swissbib project at hand. The deduplication problem of swissbib is a classification task. Explicitly, the artificial machine is trained to assign each point in the feature space to one of the two target classes, either the label pair of uniques or the label pair of duplicates. During the training process, a Support Vector Machine searches a boundary which separates the records of pairs of uniques from the records of pairs of duplicates. If this boundary is useful it clusters the points of the feature space that belong to the same class. In an n-dimensional space, this boundary is called a hyperplane. The best hyperplane for separating the records into its two classes may have a complicated mathematical representation. To avoid this issue and with the goal of separating the points with the help of a linear hyperplane, a Support Vector Classifier transforms the feature space, instead. This transformation from a linear space to a non-linear space is done with a kernel transformation of the machine. The kernel transformation ideally separates the data points of the two classes. This trick is called the kernel trick.

In the project described, a Support Vector Classifier is trained with the help of swissbib training data, using cross-validation. For the parameters of the classifier, a kernel with a polynomial transformation of third degree is found to generate the best results. With this classifier, an accuracy value of 99.88% can be reached. This accuracy is lower than the best accuracy values of the best Random Forests Classifier of the first blog article. It means explicitly 60 wrong predictions on a total of 51'886 validation records.

A Support Vector Classifier predicts the belonging of a data point to a class according to a probability value in the range of the interval from 0 to 1. The threshold value of 0.5 is the separator between the two classes. If the Support Vector Classifier calculates a probability value in the interval from 0 to 0.5, then the classifier model assigns the feature record to the class of pairs of uniques. If the classifier model calculates a probability value in the interval from 0.5 to 1, then the machine assigns the feature record to the class of pairs of duplicates. Figure 1 shows the distribution of the records for some part of swissbib training data. The green line in the figure represents the threshold of 0.5, separating the data into its two classes.

-----
es fehlt das Bild svc_prediction.png
Figure 1. Probability distribution of swissbib training data
------



Looking at figure 1, it is very interesting to observe the distance of the points from the classes separating threshold. It looks like most of the pairs of uniques lie on a line with a probability value of 1, while many of the pairs of duplicates lie on a line with a probability value of 0. These extreme points with probabilities at the probability boundaries 0 and 1 are the easy cases. More interesting are the points that have probablity values between 1 and 0. These are the cases expressing some uncertainty. Even most interesting are the cases which are located on the wrong side of their class. These are the wrong predictions of the Support Vector Classifier. Figure 1 shows some pairs of uniques in the domain area of duplicates and some pairs of duplicates in the domain area of uniques. These points have to be investigated deeper to understand why they are wrongly assigned. This task has to be done manually and will be subject of a later blog to come.

Despite of the wrong predictions, figure 1 proves that the Support Vector Classifier trained is a useful model for predicting the class on swissbib data. There seems to be some criteria in the data that separate the two classes. Machine Learning offers several methods of unsupervised learning to investigate and eventually confirm this assumption. As an example, the capstone project uses the method of k-means for further analysing the data. This method tries to cluster unlabelled data generating a number of k clusters. For the swissbib project at hand, k=2 is suggested, namely for one class of records of pairs of uniques and the other class of records of pairs of duplicates. After training a k-means model with k=2 on the unlabelled training data, the predicted points can be relabelled as the target values for the training data is known. Assigning the color of red to records of pairs of duplicates and the color of blue to records of uniques to the predictions of the trained k-means model, generates the graph of figure 2. This figure shows the red points well clustered in a separated way from the cluster of blue points. This confirms that the data has some properties that help separating pairs of uniques from pairs of duplicates.

-----
es fehlt: Figure 2. k-means clustering on training data (k-means_clusters.png)
----



This blog article offers some insight into the properties of swissbib training data. This insight can be deepened analysing the underlying models and its statements. In this manner, the trained machines talk to humans explaining their mathematical background in a compacted manner. Discussing these results of different aspects helps humans to improve their understanding of the data. Humans can learn from the models, they can learn from the trained machines. This aspect of interaction between the two entities humans and machines is an important aspect, hardly discussed in the debate on Machine Learning and artificial intelligence.

When talking about intelligence, the human brain is considered to be its domicile. The human brain is an incredibly powerful network of neurons and therefore, Machine Learning tries to find results with the help of networks that simulate the human brain. The next blog article will explain the results of a Neural Network.

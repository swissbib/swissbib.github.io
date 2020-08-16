---
title: "Why machine learning in the swissbib project"
description: "Why machine learning"
date: 2020-07-18T15:50:09+02:00
draft: false

tags: [project information, english, 2020]
categories: [Machine Learning]

---


 For what feels like two or three years now, it has been almost impossible to find articles on the subject of data and information in which terms such as "Machine Learning", "Artificial Intelligence" (AI) or "Neural Networks" are not mentioned at least once and described as the recipe for success for the future. Should this mean that what we have been doing over the last 12 years is outdated and no longer relevant? The swissbib team is not known to shy away from new software technologies. We have always thought outside the box to see if new methods can be combined with our classic methods. The problem with this is that before you can choose, try out and perhaps productively use something promising from the multitude of possible options, you first have to fight your way through the basics and terminology of the new topic. Not so easy for a swissbib team that is not lavishly staffed with people and has to keep the shop (i.e. the "green, orange or whatever colored services") running.


In such a situation, sometimes enthusiasm for the subject, openness (also about software) and a network of people from outside our library organisations who can be made curious about cool projects with our data can help. This is what happened to Andreas Jud, a swissbib friend who studied Machine Learning methods in a continuing education course at EPF Lausanne. As part of his final project, he investigated which of the numerous methods can be used for clustering bibliographic metadata. On this blog series he will introduce the selected methods and results. The complete project work is freely available as a series of Jupyter notebooks.

In the swissbib project, the essence of all our activities is the handling and processing of (meta-) data. Normalizing, enriching, clustering (merging) as well as linking of information and all this on a machine basis is the foundation for our ability to offer services such as different discoveries, different APIs or services for third parties. Especially for the machine clustering of data we use the (commercial) software of a partner, which enables us to prepare data in a flexible way so that it can be used for different purposes. Over the years, this has not been a one-off process with a static result, but an iterative process in which we (in recent years especially our colleague Silvia Witzig) from the user side and our partner contributed mutual knowledge to the process of improving data preparation. Data preparation activities remain central to the quality of the services provided by swissbib.

Machine learning is based on data. Data from swissbib is therefore the foundation of Andreas' thesis at EPFL. With the data Andreas received in its raw form from the swissbib team, the resulting clusters are already of convincing quality. This is already anticipated at this point. After completion of the work, however, there are still areas that need to be worked on in order to transfer the results into a productive operation.

- The project work of Andreas focused on the comparison of different methods of machine learning. Questions concerning the scaling of data volumes (as we have to cope with in the swissbib project with 45 million recordings) could not be considered. This open point still needs to be addressed.
- The formation of so-called pre-clusters on the content level and the use of frameworks for distributed processing such as Apache Flink on the technical level are promising approaches here.
- Even if the results of the thesis are promising and the possibilities of modern open software are still cool, the old saying "garbage in, garbage out" remains. Machine learning models must be trained and the data used in the models must be of the best possible quality.  This process requires both people who are familiar with data, its formats and contents, and people on the software side. With our swissbib experience, we are contributing know-how on both sides, and in the coming months we will also try to document even better the expertise we have gained with our productive component, which continues to deliver excellent results. In this way, we hope to preserve and pass on knowledge. In addition, we would of course like to be able to use this knowledge in various processes, such as machine learning, and thus also take advantage of the opportunity for libraries to develop further.
- The raw data, which were used for the training of machines, do not yet have the characteristics and quality as we could build them up in years on our productive machine. The next step must be to build on our swissbib data standard.
- Launched as a leisure project, the results obtained offer entry opportunities for people with different backgrounds. It was gratifying to observe how Andreas, who holds a doctorate in physics, studied the MARC rules of the LOC with interest and perseverance and took up the input from our swissbib team for his work. The result now available on how machine learning can be applied to the field of aggregation of bibliographic metadata (clusters) offers the opportunity to better grasp the magic that goes along with machine learning and AI. This also applies to people with an information science and less technical background.


We would be pleased if you follow our blog series on the topic of deduplication of bibliographic data using machine learning methods. We are even more pleased about the active participation in and discussion of the topic.
Under these links you can access the individual parts of the three-part blog series, in which the different methods and their results are evaluated and compared.

[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)  
[Part1: ensemblemethods](/blog/machine_learning/ensemblemethods)  
[Part 2: support vector machine](/blog/machine_learning/support_vector_machine)  
Part 3: coming soon


A closing anecdote. While defending the project at the EPFL, Andreas sat across from examiners who said that he had worked with a "great data set". Of course, we were pleased about that, too. But perhaps this is also a sentence that makes you think about whether our data didn't deserve more than just being put into a library system with a relational database system.

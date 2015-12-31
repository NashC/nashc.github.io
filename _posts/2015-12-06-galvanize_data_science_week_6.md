---
layout: post
title:  "Week 6 - NLP and Unsupervised Learning"
date:   2015-12-06 12:00:00
categories: feature
tags: featured datascience galvanize bootcamp
image:
---

#Week 6 - NLP and Unsupervised Learning

Rough time getting started again after nearly a week off. Luckily, we only have a few more weeks until Christmas break. It really feels like I’m in school again now that I’m heavily looking forward to time off based on academic calendars.

This week we are focusing on [Natural Language Processing (NLP)] (https://en.wikipedia.org/wiki/Natural_language_processing) and [Unsupervised Learning] (https://en.wikipedia.org/wiki/Unsupervised_learning).

**Day 23: Web Scraping and MongoDB**  
The morning was spent giving an intro to [MongoDB] (https://en.wikipedia.org/wiki/MongoDB). Mongo had a new syntax to learn, but had enough similarity to SQL, that most students were able to pick it up quickly. [The pre-reading for today] (http://openmymind.net/mongodb.pdf) had you install MongoDB and do some basic exercises. Due to that prep, my machine was up and running, but many students had install problems which took me about 45 minutes when I installed everything over the weekend.

The afternoon gave an intro to web scraping. It started with basic HTML and CSS to explain how we would be identifying the data (by HTML tag, div, class, etc) that we wanted to scrape from the webpage. We then learned how to use MongoDB in a python document using the [PyMongo library] (https://api.mongodb.org/python/current/). The problem set had us begin by scraping some images from a local html file. We then graduated to pulling New York Times articles using their [Article Search API] (http://developer.nytimes.com/docs/read/article_search_api_v2). We had to use the python libraries [Request] (http://docs.python-requests.org/en/latest/) and [JSON] (https://docs.python.org/2/library/json.html) to scrape and manipulate the website data. The biggest challenge was figuring out what type of data you had at each stage of the web scraping process. It varied quite a bit between JSON objects, Javascript objects, and Python dictionaries and lists. Since I originally learned javascript prior to python, I got to use some of that knowledge by implementing javascript methods and function syntax.

**Day 24: Natural Language Processing (NLP)**  
Today we got our first taste of NLP. This is the technology used to analyze text. For example, you might run a news website and want to sort your articles based on the topic. You could use NLP to scan and classify each of your articles, so you don’t have to read each one yourself. Or, when you ask Siri to read you a text out loud from your iPhone, she’s using NLP to scan and interpret the words, and then formulates them into a sentence with the proper vocal pace and inflections. A future use of NLP that I’m particularly excited about is in the medical field. Imagine ‘visiting’ an A.I. bot online instead of your doctor. You tell the bot your symptoms, it then uses NLP to scan all of the available medical texts, and gives you a preliminary diagnosis. This would be more cost efficient, and likely more accurate, than a traditional in-person doctor visit.

NLP uses different methods to encode text into vectors of numbers. These numbers in some way represent the frequency and/or importance of each word in the document. We can then plug these vectors into our standard machine learning models to make and analyze predictions. Today we used [tf-idf] (term frequency-inverse document frequency, https://en.wikipedia.org/wiki/Tf-idf) to convert our text documents into number vectors.

**Day 25: Clustering**  
[Clustering] (https://en.wikipedia.org/wiki/Cluster_analysis) is an unsupervised learning method for grouping like observations together. This is in an effort to illuminate patterns or similarities among data which you don’t have an target variable. We spent most of the day focusing on [K-means clustering] (https://en.wikipedia.org/wiki/K-means_clustering). The ‘k’ represents the number of clusters in which you want to divide the set.

For an example, let’s say k=8. This means we want our data to be divided into eight different clusters. The algorithm begins by choosing eight random points from the data to be the ‘centroid’ of each cluster. It then assigns each of the observations to one of the clusters based on the closest centroid. The centroid values are then updated to be the minimum mean distance from the recently assigned points. This process of assigning and re-centering is repeated until another iteration doesn’t change any of the cluster labels. We had to program this from scratch in the morning before we got to use [scikit-learn’s version] (http://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) in the afternoon.

The afternoon started with K-Means, then moved into [Hierarchical Clustering (HC)] (https://en.wikipedia.org/wiki/Hierarchical_clustering). Instead of telling the algorithm how many clusters we want, HC determines an optimal number of clusters based on the parameters of the model. After some matrix transformations, we plugged the output of our HC algorithm into [scikit-learn’s dendrogram module] (http://docs.scipy.org/doc/scipy-0.16.0/reference/generated/scipy.cluster.hierarchy.dendrogram.html) to produce a visual representation of our clusters in the form of a dendrogram. You can see an example dendrogram on [this stack overflow post] (http://stackoverflow.com/questions/16883412/how-do-i-get-the-subtrees-of-dendrogram-made-by-scipy-cluster-hierarchy).

**Day 26: Dimensionality Reduction**  
Dimensionality Reduction is pretty much what the name implies. In many data science problems you will have data sets with 100, 1,000 or maybe 1,000,000 features. Running machine learning algorithms on very large datasets can be computationally expensive (i.e. take a really long time to run). One method of attacking this problem is to reduce the number of features being analyzed. To do this, we must determine which features are most important in explaining the variance of the data. Then we can eliminate a good amount of features which don’t give us much information. An example of an unimportant feature would be one that is simply a multiple of another feature. Imagine you have one column that states inches and another in centimeters. These give the same info and therefore one can be eliminated without losing any information in the model. In the afternoon exercise we had a dataset with 2500 features. We found we could explain 90% of the variance using only 440 of those features. With that in mind, you can begin to see how useful this technique can be. Once we have our reduced data, we can then plug the revised set into our supervised or unsupervised learning model.
 
[Principal Component Analysis] (https://en.wikipedia.org/wiki/Principal_component_analysis) is one of the most popular methods of of dimensionality reduction. The procedure finds the ‘principal components’ of the data that explain the maximum amount of the variance.

[Singular Value Decomposition] (https://en.wikipedia.org/wiki/Singular_value_decomposition) is another method of dimensionality reduction. This method works by breaking the data matrix into three different sub-matrices that represent different aspects of the original matrix. There is a lot of high level linear algebra used in the background to calculate the sub-matrices. Not having taken a math class since college, I’ve been having some trouble following the lectures. However, I eventually get most of my understanding during the exercises.

In the problem sets we used the [scikit-learn PCA module] (http://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) and the [scipy SVD module] (http://docs.scipy.org/doc/numpy/reference/generated/numpy.linalg.svd.html).

**Day 27: Non-Negative Matrix Factorization (NMF)**  
Similar to how non-prime numbers can have several factors (i.e. the factors of 12 are 1, 2, 3, 4, 6 and 12), matrices can also be broken up into multiple matrices that, when multiplied together, return the original matrix. However, unlike the factors of regular numbers, the factors of a matrix can provide information about the row or column values of the original matrix, depending on how the factorization is achieved. This topic is a continuation of the dimensionality reduction, PCA and SVD material covered yesterday. It has popular applications in image recognition, document analysis and recommendation systems.

This was another day where the lecture was a bit tough for me to follow due to the heavy use of matrix manipulations, but it all came together during the exercises and now I feel I have a pretty good handle on it. You can read more about NMF h[ere](https://en.wikipedia.org/wiki/Non-negative_matrix_factorization).

We also started talking about ideas for our capstone projects. We spent time bouncing ideas of the instructors and other classmates. The biggest things to consider are can you get the data, will it be clean, and can you complete your project within two weeks. The instructors said as long as you keep those things in mind, you’ll probably be alright.

*A few top ideas I have for projects are:*  

* Looking at historical NBA team data to find our which team stats are most significant in contributing to wins and championships. I then want to incorporate team salary data to find which teams have over and underpaid for championships in the past.
* Analyzing data from [Crunchbase] (www.crunchbase.com) on different startups, funding rounds, industry, venture capital firms invested, founders, and other data to predict future company success (IPO, next funding round, acquisition).
* Use historical economic indicator data on multiple countries from the [WorldBank] (data.worldbank.org) to figure out the most important factors in predicting Per Capita GDP, Employment Rate, Educational Rates, Lifespan, or some other interesting predictions.

**Summary**  
Web scraping on Monday was pretty easy as I was already familiar with HTML/CSS. I also did a [practice project] (www.nashcollins.com/stockmarket) this past summer  where I pulled data from the Yahoo Finance API to update a quote and price graph for a given stock. However, after Monday it got a little tougher. NLP is a pretty interesting topic. We interact with it online so often, it was cool to get an introduction to how it works behind the scenes. For several exercises we analyzed articles from the New York Times. The topic that is most challenging for me, and the one for which I wish I had more preparation, is working with large matrices of information. For the entire week we turned text into vectors of numbers. Then assembled those vectors into large matrices. Then we broke down the big matrix into smaller ones using PCA, SVD or NMF. I’d usually start to get a solid grasp on each day’s topic near the end of the afternoon sprint. For someone who hasn’t taken a math class in over 10 years, working on problems in code is the most effective teacher.

They tell you coding bootcamps are like drinking from a firehouse. I can definitely attest to that. We spend one day on a topic on which you could spend a whole month. But I’m still enjoying it and am learning faster than I thought I could.
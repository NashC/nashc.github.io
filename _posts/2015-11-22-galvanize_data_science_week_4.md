---
layout: post
title:  "Week 4 - Supervised Learning"
date:   2015-11-22 12:00:00
categories:
tags: datascience galvanize bootcamp
image:
---

**Day 16: K-Nearest-Neighbors and Decision Trees**  
This week we continue our exploration of supervised learning models. [Supervised Learning](https://en.wikipedia.org/wiki/Supervised_learning) is used when we know the desired outcomes in our training set. For example, we have a dataset full of variables around different emails and then a classification whether the email was spam or not. We could then train our model on this dataset and use cross-validation to determine if our model can predict the proper classification on another part of our dataset. Last week’s topics of Linear Regression, Logistic Regression and Gradient Descent were all used on supervised learning problems.

[K-Nearest-Neighbors](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) is a simple algorithm for predicting the value of a given data point by gathering the value of the k nearest data points and returning the average of their values. KNN can be used for classification or regression models.

[Decision Tree learning] (https://en.wikipedia.org/wiki/Decision_tree_learning) is a method for finding the most important variables, and appropriate variable values, to split your data on, that gives you the greatest impact towards predicting your desired outcome. Decision Trees can also be used for both regression and classification.


**Day 17: Random Forests**  
Following our introduction to decision trees yesterday, we moved into [Bagging] (https://en.wikipedia.org/wiki/Bootstrap_aggregating) and [Random Forests] (https://en.wikipedia.org/wiki/Random_forest). Decision trees are a very simple method; so simple that it is usually easily explained to a non-quant colleague. However, a single decision tree does not always produce actionable insights as there is a high amount of variance in the results. What can we do to reduce this variance without increasing bias too much? Answer: Bagging, at first, and then random forests after you understanding what bagging is.

Bagging is [bootstrap sampling] (https://en.wikipedia.org/wiki/Bootstrapping_(statistics)) several decision trees to reduce our variance. This is better than a single decision tree, but not as good as a random forest. A random forest is constructed using Bagging for the sampling, but then selects a random fixed number of variables to train upon for each node in the decision tree. This randomization of variable training delivers more normal results due to the [central limit theorem] (https://en.wikipedia.org/wiki/Central_limit_theorem).

In the morning, we built bagging and random forest functions from scratch. Then later we were allowed to learn the sklearn library with the built-in functions.

In the afternoon pair exercise, we compared the accuracy, [precision and recall] (https://en.wikipedia.org/wiki/Precision_and_recall) of four different models: random forest, decision tree, [logistic regression] (https://en.wikipedia.org/wiki/Logistic_regression) and k nearest neighbors. In every test, the random forest performed best on mostly every measure.

**Day 18: Support Vector Machines (SVM)**  
[SVM’s] (https://en.wikipedia.org/wiki/Support_vector_machine) are another way to create decision boundaries between variables for classification or regression. Whereas decision trees can only draw decision rectangular decision boundaries, SVM’s can create curved lines resulting in much more accurate predictors. There are several different parameters that can be adjusted during the SVM model creation to adjust the sensitivity of the predictors, error acceptance range, and variable weighting, among others.

After building an SVM model from scratch in the morning to ensure our understanding, we used [scikit learn’s SVM module] (http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html) for the afternoon pair exercise. In the pair problems, we varied several of the parameters and plotted the cross validated accuracy of the model at different parameter values. This allowed us to get a good feel for what these inputs can do to help, or harm, your model.

On a less technical note, I’m getting much more comfortable, and efficient, implementing different models from scikit learn. Through exercises like today’s I’m also starting to get some intuition on the strengths and weaknesses of different model types; and what models and inputs to use depending on the type of data and analysis you’d like to perform.

**Day 19: Boosting**  
In machine learning there are many different models with different parameters that you can apply to the problem at hand. [Boosting] (https://en.wikipedia.org/wiki/Boosting_(machine_learning)) in its various forms is a way of attempting to improve decision tree type models. In the bagging and random forest variations we learned recently, we improve upon basic decision trees by sampling a random sample or subset of the variables for each split. With boosting, instead of fitting to the variables, we fit to the residuals of the previous tree. This has a way of reducing bias and variance. The Wikipedia page discusses the ideas of weak and strong learners, which I don’t yet completely understand, so I won’t comment on that aspect.

**Day 20: Profit Curves**  
Now we’re talking about profit, which being a finance guy, is something I like to talk about. To give an example, let’s say you run a business and you have a new promotion on your product you’re about to run. You printed out this nice flyer and you’re trying to decide which customers in your database you’ll mail the flyer to, in the hopes they place a new order. You make \$100 profit each time you sell the product, but it also costs you \$5 to design, print and mail the flyer. Since it costs you money to send a flyer, you’d ideally like to send it only to people you think will order. And since you run a data driven business, you have all the data on past conversion rates of your mailings for different customers. Using both of these pieces of information, profit curves allow you to combine the costs and benefits associated with a particular action, with the estimated probabilities of each scenario coming true. You can then compute the optimal split of people to mail the flyer to in order to maximize your expected profit.

Not that all of our exercises don’t have some real world application, but it was nice to work on one that was simple to understand and relevant to many business decisions I’ve made in the past.

**Weekly Summary**  
Each week is going by faster than the last one. As we briefly touched on several different machine learning algorithms each day this week, ones that could easily take a week or month to study independently, I found the lectures becoming less useful. Even when I do the pre-reading and have some idea what we’re talking about, the theory and high level math can be tough to grasp and integrate on the white board. However, when we get into the sprints, that’s where it all becomes clear to me. By working through some actual problems myself, my brain can begin to combine what was discussed in lecture with the exercises. Speaking with one of the Data Scientists in Residence, he said most students either learn better in the classroom or the exercises. We have several Ph.D’s in our class and I’m sure many of them are very comfortable with the theoretical lectures. I’m finding this true of coding in general as well. When I read about a problem or coding technique, I kind of get it. But when I try to solve some of the problems myself, that’s when I really start to understand.

To wrap up, this week was a lot of fun and I’m still pushing the limits of what I can learn. Next week is Thanksgiving, so we only have two days of class. This should allow many of the students, including myself, a chance to do some deeper review on the material we’ve covered to date. I’m also going to use the Thanksgiving break to launch this blog. I need to pick a template, edit the drafts I’ve written so far, upload it to some hosting service and get it out there for people like you to read. I already have several classmates asking me when they can read it. I’ll be interested to get their feedback.
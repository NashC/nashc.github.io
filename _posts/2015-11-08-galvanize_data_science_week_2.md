---
layout: post
title:  "Week 12 - Statistics and Probability"
date:   2015-11-08 12:00:00
categories: feature
tags: featured datascience galvanize bootcamp
image:
---

#Week 2 - Statistics and Probability


>**"Do or do not. There is no try." _- Yoda_**


For me, the second week was more comfortable than the first. During the first week, we were all trying to get our bearings, meet our classmates, adjust to our new schedule and figure out if we even belonged in this program. Well, I now know most of my classmates; I know the daily routine and have made sure I’m ready for each day’s quiz and topic; and I learned that even though I don’t have an extensive background in coding or statistics, that I can keep up and excel in this class. This week focused on probability and statistics. I studied these topics very heavily for the technical interviews only a few weeks back, so most of the material was still fresh in my head. After last week’s work with Pandas and this week’s new tools of Frequentist and Bayesian analysis, I’m now confident I can do some basic data analysis of a given data set on my own. I can put the data into a Pandas Dataframe, clean and organize it, calculate some averages, min/max, correlation or some other statistics of interest, and lastly evaluate whether or not I can act on my findings by determining their statistical significance. Believe it or not, I feel like I’m on my way to becoming a Data Scientist.


**Day 6: Probability and Pandas**  
First day back from what felt like a very short weekend. This week we are focusing on probability and statistics. Instead of a quiz, we had our weekly assessment (test) for the first hour of the day. It focused on all of last week’s material (Python, SQL, Pandas). I felt pretty good for most of it, even though I couldn’t get the test file to work well with all my answers. The morning sprint was short with a few questions on basic probability (combinatorics, permutations, conditional probabilities). The afternoon lecture went deep on statistics (population, sample, mean, variance, standard deviation, covariance, correlation). The afternoon pair exercise wasn’t really difficult, but it did take a long time. We had to lookup several new methods for Scipy and Numpy to do the problems. The longest part was building a python function from scratch that calculated the covariance matrix of a dataframe. We could then check our answers against a built in pandas method for doing just the same thing.

**Day 7: Sampling, MLE, Bootstrapping, Confidence Intervals**  
Today we continued with more statistics. We covered various sampling distributions (normal, poisson, gamma, binomial, exponential), Maximum Likelihood Estimates, Confidence Intervals and Bootstrapping. Bootstrapping appears to be a very important tool in the practical data science world. It’s used when you have a small sample with which to work. You then take many sub-samples (i.e. 5000, 10000, etc) with replacement from your original sample and compute the test statistic for each one. These sub-sample stats begin to represent a normal distribution as the number of samples increases. We can then draw more statistically significant conclusions from the bootstrap process. The morning solo exercise was way too long and I barely finished half of it before time ran out. The afternoon pair exercise was a lot of fun. I had worked with my partner a couple times before and we have a good rapport when working together. We built a Bootstrap function from scratch and used it to compute some stats on a few sample data sets.

**Day 8: Frequentist Hypothesis Testing, Z-tests and t-tests**  
Hypothesis testing is one of the primary tools of a data scientist and is the cornerstone of the Frequentist school of statistics. Today we covered the basics of this material and how to apply it to some introductory problems on A/B Testing for website optimization. A/B Testing is a common term and practice at most companies. However, to run the test properly, you have to know whether or not your conclusions are statistically significant. Hypothesis testing allows us to compare some assumption about a population to the data in hand, and determine if our new data is different enough from our assumptions to warrant our taking action on them. I’m told these methods will be used repeatedly throughout the rest of the program.

**Day 9: Bayesian Statistics**  
Next we moved on to cover the basic of Bayesian Statistics and their approach to analyzing a problem. Bayesian’s use the Bayes’ Formula to combine prior assumptions about a sample and combine them with the sample data, to develop posterior conclusions about the sample statistics of interest. They then might use the new posterior inferences as the prior assumption for a new analysis. Apparently Bayesian’s and Frequentist’s are the two major schools of thought in the statistics community. Bayesian’s believe in applying prior assumptions, while Frequentist’s believe they know nothing and only rely on data to develop their conclusions. The day’s problems had us develop Bayesian functions in Python to deduce probabilities of various multi-sided dice. We then wrote the code to play the famous Monty Hall (add wikipedia link here) problem in Python.

**Day 10: Bayes and Multi-Armed Bandits**  
The morning was focused on more Bayes’ lectures and problems. We then spent the afternoon learning about Multi-Armed Bandits (MAB). This is a family of algorithms designed to optimize A/B Testing. Instead of running a simple A/B test on a control and treatment group, the MAB’s develop some dynamically updating statistics on the success of each version being tested and then recursively selects the optimal version based on the target metric. (Add some links). We tested several different MAB’s by running 10,000 simulations of a website change A/B test, and then compared which algorithm performed the best on based on website conversion rates.
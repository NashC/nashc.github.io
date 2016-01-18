---
layout: post
title:  "Week 5 - Thanksgiving"
date:   2015-11-29 12:00:00
categories:
tags: datascience galvanize bootcamp
image:
---

I certainly am thankful that we get several days off for Thanksgiving. I was mentioning to a classmate the other day how nicely the holidays fit into our class schedule. We have Thanksgiving about one month in, and then Christmas and New Years a month later. This effectively segments our course into thirds with a multi-day break each time.

I’m writing this on the Friday after Thanksgiving at my Mom’s house. We had tons of food and football. During the break, I’ve been re-watching [Andrew Ng’s famous Machine Learning Course on Coursera] (https://www.coursera.org/learn/machine-learning). I first watched several of the class videos back in September when I was preparing for the admissions interviews. The difference now is that I understand pretty much everything he’s talking about. The lectures really do feel like review instead of new topics.

I’m slightly in awe at the amount and difficulty of new material my classmates and I have learned in the areas of probability, statistics, python and machine learning in the past four weeks. The instructors say most people in the class come from either a computer science or math/stats background. But then there are the few outliers like myself, from business or finance, that have virtually zero programming experience and haven’t taken a math or stats class since college. Judging from my experience so far and that of other bootcamp graduates, I really think these topics can be taught in three month programs; whether that’s data science or web development.

**Day 21: Case Study**  
Since it was more or less a lost week due to the holiday, today was used for an all day case study. We had an informal lecture where one of the instructors covered her personal [EDA] (exploratory data analysis; https://en.wikipedia.org/wiki/Exploratory_data_analysis) or [IDA] (initial data analysis; http://onlinelibrary.wiley.com/doi/10.1002/0471667196.ess0309.pub2/abstract) process. This is what she does when she first gets a new dataset and is asked to answer a specific question or simply find something interesting.

#####Here’s a summary of her process:
1. *Listen*  
You need to listen to the person (client, boss) asking for the analysis. However, instead of having that person tell her exactly what to find, she asks them to tell her about the problem they’re trying to solve. The analyst can then get creative about the problem at hand and not be boxed in by the client’s or her own preconceptions.

	At this stage, she also starts thinking about the implementation of the final results of the analysis.
	* Who will it be presented to and what is their level of competence with data science practices?
	* Will I have to convince people of a particular course of action based on my findings?
	* What will be the best way to present the findings to the end audience?
	* She’ll use questions like these to guide her through the entire process by keeping the end product in mind.
2. *Cleaning and Munging: Is the data what I think it is?*  
Get an overview of the dataset, so you know what you’re getting into.
	* Data types: numerical, categorical (how many levels?)
	* Missing values: What percent of values are missing for each variable? What am I going to do about this? (drop observations, fill in with mean or median, use model to predict and fill in)
	* At this point, the instructor also likes to start her diary or journal of the project. This will serve to record her findings and thoughts as they happen. This is important because you will often get sidetracked doing some model or plotting, and then forget something important you found prior to that. By having a journal, it makes it easier to keep track of for yourself, the analyst, and potentially for others you present the work to later.
3. *Get ‘intimate’ with the data*  
At this point the data should be clean enough following the previous stage. This is the EDA stage
	* Run a random forest to get variable importances
	* Be aware of domain specific (finance, medical, tech) things to pay attention to
	* Know thy target - plot, get max/min/quartiles/etc
	* Plotting
		* Our instructor personally prefers R for plotting, as she thinks it’s faster to get through the process
		* Univariates - single variable plots (i.e. histograms, bar charts)
			* Watch out for small values and outliers/fat tails. We can take care of these by setting min or max value for that variable
			* Put some ’n_size’ charts below your histogram. This will tell you if you have a large enough number of observations in that bar to care about the result.
		* Bivariates - two variable plots (i.e. scatter, scatter matrix)
			* View all variables, dependent/independent, against each other. What do you see?
	* Go back and forth between plotting and pondering about the problem. This will usually lead to good insights about the data.
4. *Let’s Model*  
Now let’s start building some real models to make predictions
	* Linear Regression: maybe use Lasso or Ridge for regularization
	* Logistic Regression
	* Feature engineering and missing values
	* Random Forest: get predicted error
	* Missing Values
		* Use random forest or some other method to predict and fill in missing values. Using a model to predict missing values can be much better than simply using mean or median.
	* Should I have just one model or multiple?
5. *Some Results*  
What do they mean? Put them in context of the domain.
6. *Tell Stories, Present It Well!!!*  
Know your audience: If you audience doesn’t understand, doesn’t care or doesn’t like you, then it was all for nothing.

Wow! Writing that all down provided a pretty thorough review for myself. After the lecture, we broke up into teams. We were given a dataset containing user information about a service app and asked to give the reasons for customer [churn] (https://en.wikipedia.org/wiki/Churn_rate ) based on the data available.

At the end of the day, each group had to go in front of the class and present their findings. Every group, more or less, found the same interesting things in the dataset and had similar theories about the source of the customer churn. Granted, the dataset was not too big with less than 10 variables; so it’s not surprising most of us came to similar conclusions.

It was interesting going through the entire process of trying to gain useful insights on a new dataset from start to finish. Up until this point, all of our exercises were some smaller portion of this process with specific instructions on what to do at each step. I have to admit I was a bit lost at times when there weren’t any instructions. But it was good to get a feel for the kind of work we’d be doing in the real world for a client or company.

**Day 22: Review (Optional Day)**  
I choose to start my Thanksgiving break early and take today off. The instructors said it was an optional day as they were going to be doing review. I find I don’t get too much out of lecture style review sessions, as I learn this type of material better when doing projects/exercises.

**Weekly Summary**  
I’ve still got two and half more days to rest until class restarts and I begin dreaming about python code and scatter matrix plots. I was talking to my mom this morning about some of the things I’ve been studying. She was in awe of the skills we’ve been learning and that we can learn them in such a short period of time. This later turned to a discussion of unemployment in the United States and how we often read that it’s not that there aren’t enough jobs, it’s that there aren’t enough qualified workers. I know in the San Francisco Bay Area there are tons of openings for data scientists and web developers, but there aren’t enough applicants with the skills to fill them. It’s companies like [Galvanize] (www.galvanize.com), [Hack Reactor] (www.hackreactor.com), [Dev Bootcamp] (www.devbootcamp.com), [Metis] (www.thisismetis.com), [General Assembly] (https://generalassemb.ly) and many others, that are helping to fill this skill gap, at least in the areas of computer science. I believe these courses, along with MOOC’s on [Coursera] (www.coursera.com), [Khan Academy] (www.khanacademy.org), [Udemy] (www.udemy.com), [Udacity] (www.udacity.com), are the beginning of the evolution of the educational system in the United States and the world at large. I’m grateful to be one of the early adopters of these new methods and have 2-3 standard deviations of confidence it will turn out to have been a good choice.
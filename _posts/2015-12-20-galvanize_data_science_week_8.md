---
layout: post
title:  "Week 8 - Big Data"
date:   2015-12-20 12:00:00
categories: feature
tags: featured datascience galvanize bootcamp
image:
---

**Day 33: Amazon Web Services, Parallel and Concurrent Programming**  
We all know we can buy books, movies, computers, clothes and several other items we don’t need on Amazon. Something else Amazon sells is storage and computing power on its vast array of servers under the name Amazon Web Services (AWS). AWS allows us to store very large files or datasets in the cloud. It also allows us to use multiple computers/processors in the cloud to scale our computing power much higher than we could on our local machine.

We spent the morning creating S3 and EC2 instances on AWS. We then had to upload a file, read data from that file, run some functions on that data, and finally upload the outputs of those functions. I spent a long time getting my AWS authentication credentials to work, but it was pretty easy after that. We used the Python library [Boto] (https://github.com/boto/boto) to interact with AWS.

In the afternoon we learned about splitting a program’s work among multiple CPU’s, and then among multiple threads within each CPU. We created a simple script to scrape business data from yelp.com. We put each of the four cities we wanted to search on a separate CPU, then each business we wanted to search in its own thread. This decreased the total scrape time to approximately 5-20% of the sequentially processed request. I can see how this would be very beneficial for large files at scale.

**Day 34: MapReduce**  
[MapReduce] (https://en.wikipedia.org/wiki/MapReduce) is a programming model and an associated implementation for processing and generating large data sets with a parallel, distributed algorithm on a cluster. MapReduce is surprisingly simple in that it breaks up programming tasks into a Map() function, which performs filtering and sorting, and a Reduce() function, which performs a summary operation. These are the typical map, reduce, filter, apply type functions you find in most programming languages.

We used the [mrjob] (https://github.com/Yelp/mrjob) python library to run the MapReduce functions in our exercises. You create a mrjob class and then write mapper and reducer methods within your class to perform each step. Mrjob takes care of all the distributed computing optimization of your tasks in the background. We only worked on local datasets, but mrjob easily scales to using AWS or other cloud computing infrastructure.

**Day 35: Spark**  
[Apache Spark] (https://en.wikipedia.org/wiki/Apache_Spark) is an open source cluster computing framework. On Monday, we learned how to parallelize our computing work among multiple CPU’s and threads, allowing for greatly improved processing times. However, we had to manually specify how to parallelize the work. Spark takes care of the distributed computing assignments/optimization is the background, allowing the user to take advantage of cluster computing without having to possess all the specialized knowledge of how to manually execute it. Spark can be run locally on your machine, but is meant to be used on multiple machines such as those available using AWS. We used the [pyspark] (http://spark.apache.org/docs/latest/api/python/) python library to allow us to use Spark in a native Python environment. Spark uses the same MapReduce programming format to operate on data. After creating a Spark instance, the user can perform a series of mapping and reducing operations to transform or extract the data.

In the morning exercise, each student installed Spark. This was a more difficult task for some than others, as Spark is continually releasing new updates. After the install, we did a simple exercise reading a text file into a Spark instance, and performing some MapReduce operations on it. In the afternoon, we downloaded NY Times articles from AWS, and performed some Term Frequency and Naive Bayes analysis using pyspark’s built-in machine learning libraries.

**Day 36: Spark and AWS**  
The morning was spent doing some more Spark work on our local machines. We downloaded some Yelp business data from AWS and loaded it into a Spark RDD (Resilient Distributed Dataset). The RDD is Spark’s default dataset object. We then used the SQL functionality of RDD’s to allow us to query our data using SQL commands passed as strings.

The afternoon was supposed to be stepping up to the big leagues by launching a 20 cluster instances on AWS to run our programs. However, we ran into some serious launch issues stemming from the wrong version of Spark, AWS instance limit reached, and some AWS credential issues. We used the command line to create the clusters, which has a lot more nuance than using the AWS GUI on their website. We eventually did get the 20 clusters instances to launch, but it took about 30-45 mins from the time we initiated the command. Lesson of the day was AWS can be a pain to get running, but once you get the hang of it, it’s not so bad. However, I heard several students say they will do their best not to use AWS for their projects unless they absolutely have to.

**Day 37: Data Products**  
Today we used [Flask] (http://flask.pocoo.org/), which is a web framework for making websites using Python. We also used [twitter bootstrap] (http://getbootstrap.com/) for our HTML and CSS template. In the morning, we made a basic three page site. The homepage redirected to a page with an HTML form. The user can submit text and then an NLP classifier we built presents what NY Times article topic the text should be from. In the afternoon, each team built whatever web app they wanted to and presented the site to the class at the end of the day. My team built a site about flipping houses. But it takes an unexpected twist when you get into it.

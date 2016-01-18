---
layout: post
title:  "Week 10 - Capstone Project: Part 1"
date:   2016-01-10 12:00:00
categories:
tags: featured datascience galvanize bootcamp
image:
---

After a week and a half off, we're back at it full speed working on our capstone projects. We are finished with the structured part of the curriculum. Each student will spend every day of the next two weeks working on his or her project. We meet in the morning with the instructors to review the previous day and set a gameplan for that day's work.

I'm feeling a bit anxious as a deadline is approaching and this project feels so important to my short term future as a data scientist. I know I'm blowing it out of proportion in my head, but the little voice is still there. Along with several other students, I'm concerned whether potential employers will find my project impressive and if it will be a good illustration of my newly acquired skills. However, at the end of the day, all I can do is give it my best effort and let the chips fall where they may. I'm cautiously optimistic I'll have a solid data science project to show off in two weeks time.


**Day 41: Capstone Project**  
First day back from Christmas break was a little rough in the morning, but I was feeling good by lunch time. I originally wanted to do my project on analyzing Crunchbase company data. However, after speaking with someone at Crunchbase last week, I found I won't be granted access to their API as they've been burned by too many bad actors in the past. An additional aspect to the Crunchbase project was to do apply NLP (Natural Language Processing) techniques to press releases from startups. After speaking with one of our instructors, he believes I could do an entire project on only this portion. Therefore, I'm going to move forward with this plan.

The first step was to acquire the press releases. Before the break, I got access to the PR Newswire API. Here I can download old press releases based on certain criteria. Crunchbase did help me out by granting me access to their [Open Data Map](https://data.crunchbase.com/page/crunchbase-open-data-map-odm). This has a list of companies and people in the Crunchbase corpus. I loaded the 'Companies' csv file into the Pandas dataframe and was able to use this as my base list of startup companies.

Unfortunately, the PR Newswire API documentation is not very detailed and the API query parameters are somewhat limiting. I spent several hours each day last week during the break trying to create a program to query the API based on certain inputs and write those files to a local MongoDB database. I was able to easily query the database a few times with fixed inputs. The difficult part was creating several functions to download all press releases based on all my company names. There were several times I got a few thousand companies into my list and then got some error. However, after working on my API request pipeline today, I think I have a good setup to do a large download tonight while I'm asleep.

In the afternoon I was able to get some basic topic modeling (LINK HERE) done on a couple thousand press releases I had downloaded already. I could see some similarities in the topic clusters and top words for each cluster, so this was encouraging to see the project is probably going to work.

Next steps are to download a larger amount of press releases and do further NLP analysis on the texts I have.

**Day 42: Capstone Project**  
As noted above, yesterday went pretty well. I continued downloading more press releases from the PR Newswire API and reached my daily query limit without any errors after running my program for a few hours. I spoke with someone from Data Support at PR Newswire today on the phone to see if I could get a older releases and a higher daily limit. The man I spoke with said they received my email from Monday and that he would make sure my request got forwarded to the appropriate person and they would call me back. That phone call was at 1030a this morning and I did not receive a call back today. Hopefully I'll hear from them tomorrow with good news.

Other than more successful downloads, I made progress on a few other elements of the project. While downloading, I watched some [Coursera lectures on Sentiment Analysis](https://class.coursera.org/nlp/lecture) to learn more about how I could apply this technique to my data. It was surprisingly easy to understand the basic concept. You make or download a vocabulary of words that each have a positive, negative or neutral rating. Then count the number of times each word occurs in your text and sum the scores. Of course, it can get more complex, but that's the basic premise.

After downloading my third large set of press releases, I had them in three separate collections in a single MongoDB database. I wanted to merge them into a single large collection, this would be more convenient and make the code easier to follow. After reading some [Stack Overflow](http://stackoverflow.com/) posts about similar issues and asking one of our TA's, I still couldn't figure it out. An hour later, I came across [this MongoDB function](https://docs.mongodb.org/manual/reference/method/db.collection.copyTo/) which lets you copy from one collection to another. The first copy worked fine. I was worried the second copy would overwrite or do something else bad to the first copy. However, it appended it to the bottom as I hoped. I checked the number of entries and it worked perfectly. Now, I have one master collection with all the data I've downloaded so far.

Each entry in the database contains the press release and other metadata. Two of these meta items are the 'Subjects' and 'Industries' associated with each release as classified by PR Newswire. I wanted to create [Dummy Variables](https://en.wikipedia.org/wiki/Dummy_variable_(statistics)) for each of these items. The problem was each release might have multiple meta tags stored in an [array](https://en.wikipedia.org/wiki/Array_data_structure). [Pandas 'Get Dummies' function](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.get_dummies.html) usually does this automatically, but can't operate on arrays. Luckily, after much googling, and trial and error, I got the dummy columns I was after.

In the late afternoon I wanted to start doing some [Sentiment Analysis](https://en.wikipedia.org/wiki/Sentiment_analysis). This technique is the process of trying to distill the positive or negative sentiment from a piece of text. A common example is product reviews on Amazon. If someone liked a product, they are likely to use words such as 'great', 'amazing' or 'good'. Contrariwise, a negative review is likely to contain words such as 'bad', 'horrible' or 'stupid'. I planned to use [NLTK's Sentiment Analyzer module](http://www.nltk.org/api/nltk.sentiment.html). However, after trying to find some examples online, I couldn't figure it out too quickly. I therefore decided to leave it to tomorrow. I'll update on my progress in tomorrow's post.

**Day 43: Capstone Project**  
Following up immediately on the Sentiment Analysis topic from yesterday. After asking around, I found another student had used the python library [TextBlob](https://textblob.readthedocs.org/en/dev/) for this task. The module was easy to use and the documentation was 
clear. I had the sentiment analysis for all of my press releases within 15 minutes.

In an effort to get more data, I got on the phone with someone from PR Newswire's data support team. Unfortunately, I found that without paying a large fee or partnering with a major news publication, I won't be able to get any greater amount of data than the standard API allows. The woman did point me in the direction of a few other companies that might be able to help, but she said I'd likely get the same answer. At the moment, I have about 6300 unique press releases. I decided I'm going to move forward with the other parts of the project and then try to get more data at the end if I have time.

Most of the releases have URL's in them. I wanted to find a way to strip these out as my models think that 'http' and 'www' are important words since they appear so often in the text. I spent some time crafting a [regular expression](https://en.wikipedia.org/wiki/Regular_expression) to remove these and eventually got it to work. I had some experience with regular expressions in the past, but this was by far the most complicated one I had put together. For reference, here's the line of code I used for this:

{% highlight python %}
df['release_text'] = df['release_text'].apply(lambda x: re.sub(r'\(?(https?:\/\/)?(www\.)?[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&//=]*)\)?', '', x, flags=re.M))
{% endhighlight %}

Lastly, I was speaking with one of the instructors today about how I could product-ize my project. I'd like to have something people could use to provide a useful function. This would also show to potential employers I can brainstorm about products, design them and build them. We came up with the idea of having a web app where a user could type in their press release on the left half of the page. As they typed, the right side would display the sentiment analysis of what they typed, comparing it to the baseline sentiment of the releases in my corpus. I also plan to display other NLP type info on the page that updates in real time as the user types. I think this could be useful to people who write press releases and provide a good 'Wow' factor for my presentation.

**Day 44: Capstone Project**  
**NEED TO ADD LINKS AND MORE EXPLANATION ON NMF, GRID SEARCH, ETC**  
We had an event with Galvanize alumni in the evening, so I wasn't able to get the blog post written. I'm therefore writing Day 44 and 45's entries on Friday evening.

I finished downloading all the press releases from my list of companies. I now have 6,584 unique documents. I have a few other potential sources for more articles, but I'm going to focus on the rest of the project and try to get more next week if I have time.

At the beginning of every release text is the City and Date sources for the document. A classmate told me about this really cool python library [geograpy](https://pypi.python.org/pypi/geograpy/0.3.7) that can identify cities, states and countries in text and automatically pull them out. However, I had some trouble installing it based on its dependencies on old libraries. After speaking with one of the instructors, he had heard of a similar install problem and advised me not too invest too much time as I might spend several hours and still not successfully install the library. Based on that opinion and previous install frustrations, I decided not to pursue it and instead craft a custom function to scrape the location data. However, due to inconsistencies in how the locations are presented, this proved a tall order as well.

The previous evening I had tried to run a Grid Search to find the optimal value for the n\_components parameter in my NMF model. The problem is you can't run a grid search for this type unsupervised method. The Grid Search tries all the parameter values you input, but it needs some type of scoring method to figure out the best one. With NMF, there is no score, like in a linear regression, for the model to use. I therefore wrote a custom grid search function that loops through several parameter values, stores the 'mean squared error' of the NMF approximated reconstruction matrix. However, instead of finding an optimal n\_components, the MSE kept decreasing with each component added in a linear fashion. Therefore, I couldn't decide which is best. I decided I'll talk with my instructor tomorrow to come up with a strategy.

I also spent about an hour working on my resume. We had a lecture from the Director of Outcomes, the woman who helps get us jobs after graduation, on Monday. She discussed how to craft your resume and sales pitch of each person's strengths and weaknesses. The revised resumes are due Monday, but I want to get mine in by end of day Friday. I made some progress, but will have to continue tomorrow.

**Day 45: Capstone Project**  
First thing in the morning was to address the grid search issue. My instructor suggested doing cross validation on each n\_component test, to ensure my outcomes were valid. He also thought this would solve the problem of the MSE continually decreasing with each additional component. Similar to how grid search can't handle NMF, sklearn's cross validation module can't handle tf-idf sparse matrices. The reason is you can't do a traditional train-test-split on a tf-idf sparse matrix. If you remove 20% of the rows for a 5-fold split, you can't reconstruct and approximation of the original matrix because the dimensions aren't the same. My instructor found an [academic paper](https://www.cs.umd.edu/~bhargav/nips2010.pdf) online suggesting another method. You therefore, can't get an MSE score to optimize. I then had to create a custom train-test-split function that would set to zero a random 20% of the tf-idf entries. This would form the training set. I then plugged that output into the NMF model and compared the reconstructed matrix to the test set to get my MSE. I spent three quarters of the day getting this function to work.

In the late afternoon, while my custom grid search was running in the background, I spent another 90 minutes on my resume and submitted the final version. I look much more like a data scientist now, than only a Finance professional.

Next week I need to confirm my grid search results, finish extracting the location data, find the topic strength for each industry/location and build the web app for live user input.

We only have three weeks left in the bootcamp. Topics we learned in the first few weeks feel like years ago. Another cohort started this week. I can imagine myself in their place. I'm not sure any of them have a good grasp on the journey they're about to start.

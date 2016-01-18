---
layout: post
title:  "Week 7 - Special Topics"
date:   2015-12-13 12:00:00
categories:
tags: datascience galvanize bootcamp
image:
---

**Day 28: Recommendation Systems**  
If you use the internet, chances are you’ve ran into at least one recommendation system. If you’ve bought a book on Amazon, it shows you other books that people who bought that book also like. On Netflix, it will show you other movies that people who liked specific movie also have liked. On your iPhone, it will suggest other Apps to download based on ones you already have. Therefore, we’re all at least peripherally familiar with recommendation systems; or at least their output. How they are generated is another story.

Recommendation engines work by suggesting other items that have received high ratings by other users who have highly rated items similar to yours. For example, if you gave a high rating to the Matrix and Aliens, chances are you’ll probably like Star Wars. The recommendation engine will see you have high ratings for the first two movies. It will also see that other users who have high ratings for the first two have rated Star Wars highly. Based on those inputs, it will suggest Star Wars to you. This is, of course, a very simple representation of the behind the scenes mechanics, but you get the idea.

One of the largest problems facing recommendation engines is data sparsity. This is because most users don’t rate any items, and users who do rate, have only rated a small portion of items any way. We have to find a way to estimate the missing ratings. We built this from scratch in the morning, then used the Graphlab library from [Dato] (https://dato.com/) to automate it in the afternoon.

**Day 29: Capstone Projects and Recommendation System Case Study**  
We spent the morning lecture period discussing the parameters for selecting project ideas. We also reviewed several past student projects, and discussed the good and bad aspects of each. Virtually every student in the class is stressing about their project. What should the topic be? What type of analysis will I do? What questions am I trying to answer? Will anyone (i.e. potential employers) care about my topic/questions? These are the questions we are all wrestling with at the moment.

#####I have a few top prospects for my projects which I’ll outline my thoughts on here:

1. **_Data on startups from [Crunchbase.com](www.crunchbase.com)_**  

	*Topic/Questions:* I wanted to explore the data on different startups, funding rounds, Venture Capital firms invested, founders past companies and schools, etc. Then I could try to predict future company fundings, acquisitions or exits based on the past data. There could also be interesting visualizations of valuations over time, by VC firm, by industry and so on.

	*The Good:* I’m sure just about every potential employer will be interested in startups. Cruchbase has an API that will make the data easy to acquire.

	*The Bad:* This has been done several times before. I’m not yet sure if I could add something new. The data is user sourced, so accuracy of entries for smaller startups could be questionable.

2.  **_Economic data on different countries since 1960 from [data.worldbank.org](data.worldbank.org)_**  
*Topic/Questions:* There is a ton of historical data for many different countries of many different economic measures. I’m not sure of the exact questions to be answered, but I’m sure there are some interesting insights or stories to be told from the data.

	*The Good:* The data is very easy to acquire and is clean. People interested in economics, history, travel, and/or sociology might like the findings. Because the dataset is so large, there is bound to be some good findings in there.

	*The Bad:* Not everyone will be interested in this. The findings likely won’t have a business application.

3. **_NBA team and player data from stats.nba.com_**  

	*Topic/Questions:* I’d like to take historical team stats from the last 30-40 years and see which stats are the best predictors of wins and championships. There is also player movement tracking data available for the past season or two for some teams. This could provide some interesting findings. I could also incorporate team salary history to see if teams are over or under paying for wins.

	*The Good:* Data is very easy to scrape from NBA stats website. I would enjoy doing this project as I’m very interested in basketball.

	*The Bad:* The feedback I’ve gotten from our instructors and that also was my initial concern, is that potential employers might view it as a juvenile or novelty type project, and won’t take it seriously. On the same lines, unless I get someone on the other side of the table that really likes sports, they definitely won’t care about my findings. And engineers and HR people likely don’t have a majority of sports enthusiasts in their ranks.

4. **_Historical Stock or Option data_**  

	*Topic/Questions:* Can I predict future prices based historical inputs? I could also do some interesting back testing on options strategies to show predicted versus realized win rates.

	*The Good:* I trade options in my own account and am following the financial markets every day. Therefore, I’d enjoy doing this project. The findings are very business related.

	*The Bad:* Options data is only available for purchase. Many large hedge funds employ very smart people and pay them a lot of money, and those people still can’t always predict future prices.


Those are my top ideas to date. At the moment, I’m leaning towards the World Bank data unless something better pops into my mind.

For the afternoon, we built a recommendation model using [Graphlab Create](https://dato.com/products/create/) from [Dato](https://dato.com/). We broke into teams of 3-4 people and then compared scores at the end of the day.

**Day 30: Time Series**  
Have you ever looked at a graph of [Apple’s stock price] (http://yhoo.it/1UaaCqX)? Then you have some experience with time series data. [Time Series analysis] (https://en.wikipedia.org/wiki/Time_series) is the process of analyzing data with a temporal component in order to extract meaningful statistics from the data and/or project its value into the future. Since I trade stocks and options in my own account, this topic was of extra interest to me.

#####We learned that all time series data can be broken down into the following components:

*Trend:* Long term upward or downward movement of the series. Think of the consistent growth in the number of new users for a service like Facebook or Twitter.

*Seasonal Variations:* Patterns in the data that follow yearly cycles. Think of seasonal temperatures or increase in retail sales around the holidays.

*Cycle:* Upward or downward movement of the series around the trend; similar to a wave. These are similar to seasonal, but are usually much longer. These could be 5/10/20 year cycles, instead of annually.

*Random Variations:* This is the white noise or randomness that fluctuates around the other components.

![Time Series Decomposition](http://nashc.github.io/assets/images/time_series_decomposition.png)

In the exercises we used [Statsmodels time series module] (http://statsmodels.sourceforge.net/devel/tsa.html) to analyze ride sharing data. The implementation of this was kind of difficult. Our instructor said R is much better than Python for time series analysis. If you’ve learned this much Python, then learning how to do it in R shouldn’t be too hard. I’m excited to dig into this topic more after the class finishes and see if I can apply it to developing algorithms to automate stock and option trading.

**Day 31: Graphs**  
We’re not talking about the normal type of graphs you’re thinking about. In math, a [graph] (https://en.wikipedia.org/wiki/Graph_(mathematics)) is a representation of links and vertices. We used the example of Facebook friends in class. Each person is a vertex and every friend connection is a link between those two vertices. Below is a picture of all the friend connections on Facebook, based on the user’s location.

In the exercises, we used the NetworkX library (https://networkx.github.io/) to develop and analyze our graphs. We then used the software [Gephi] (http://gephi.org/) to visualize the graphs we made. This was a pretty interesting topic, but some of the math around calculating the connections can get a little crazy.

![Facebook Friend Graph](http://nashc.github.io/assets/images/facebook_graph.png)

**Day 32: Data Visualization**  
Everyone loves a good data visualization. It allows even non-tech, non-data people to consume information. As a data scientist, visualizations allow you to communicate your findings to others. It is therefore a very valuable skill in our toolbox.

Being a finance guy, [this is one of my favorite visualizations] (http://www.nytimes.com/interactive/2012/05/17/business/dealbook/how-the-facebook-offering-compares.html) that puts the Facebook IPO into perspective versus other past offerings. If you like history, international studies and/or economics, I also really enjoy [this] (www.gapminder.org/world) interactive visualization.

Today we used the following libraries to create a variety of visualizations:

* [Matplotlib] (www.matplotlib.org) 
* [Seaborn] (http://stanford.edu/~mwaskom/software/seaborn/)
* [Bokeh] (http://bokeh.pydata.org/)
* [D3] (http://d3js.org)
---
layout: post
title: Insights with lean analytics
comments: true
permalink: "insights-with-lean-analytics"
---

I remember stopped working in consulting because all i created was concepts and slides. The truth is, i was a powerpoint bitch.
When i started to work with large amounts of data, naturally the first thing i did was a lot of descriptive data analysis and visualization. I was hired as an analyst in a startup and became a reporting bitch soon. Was that the hands-on work i expected from working in a young startup? It just didn't feel right, so i decided to make a change.

In this post i'll share my expierences of the last two years on building an insights team in a startup and how we did the transition from data analysts to data scientists to generate actionable insights that matter. The areas i'll touch are [setting the goals](#setting-the-goals), [building a team, structures and culture](#building-a-team-and-structures), [building a technical infrastructure](#building-a-technical-infrastructure), [defining a lean process](#defining-a-lean-process), [choosing the right metrics](#choosing-the-right-metrics) and [making predictions](#making-predictions).

While reading i'd appreciated your feedback and feel free to challenge every single word i'm writing.

## Setting the goals

Everything you do should have an explicit goal before you start. Write it down, communicate and approve it, then start the planning. To me the three most important goals for an Insights team are:

##### Identify the "real" problems

> What problem are you trying to solve?

is the single first question you should ask. Often there are different people requesting some analysis without knowing which problem they are actualy trying to solve. If there is one thing to remember from this post - it should be this.

##### Define and validate hypothesis

Once the real problems are identified it's important to transform vague questions into measurable hypothesis that can be validated. This only works if you define hypothesis in the first place. A simple product hypothesis could be something like:

> If we change the call to action for our signup from "Signup" to "Get fucking started" we increase the signup rate (conversion) from 3% to 5%.

The rest is specifying the success metric further, designing the experiment (A/B test) and tracking the hell out of it. I'll explain this part more detailed in the [defining a lean process](#defining-a-lean-process) section.

##### Ingest data in the companies DNA

Data informed thinking has to start with the CEO and go all the way through to every single engineer, otherwise you'll have a hard time fighting to help others. I didn't give this a single thought when i started but it turned out that half of my efforts ended up beeing educating others to think with data and eventually using tools to validate or falsify their initial hypothesis.

## Building a team and structures

As the first hire for data analysis i was lucky enough to have full control on how to scope and design the insights team and structure. Depanding on what the expectations of your role are you should define the responsibilies and tasks. This is what we came up with:

![Insights Strategy](/assets/posts/2014-10-14-insights-with-lean-analytics/insights-strategy.png)

##### Understanding the business

To get the most out of our data, we decided that it's key to cover many different areas and connect them. Contentwise, it turned out that focus was to work on the product as much as possible. We used attribution data from marketing and sent it with our user data. We didn't work much on the financial perspective as we made a strategic decision to cut off advertising from our app and focus on growth. To retrieve meaningful insights from this data, an important requirement is a solid business understanding for all those different areas. A data scientist should know how the business model works and how the different departments are connected to each other.

##### Understanding the technology

I realized the opinions about the technical perspective differ a lot. Personally, i believe that despite the fact that the goals are identifying the real problems, validating hypothesis etc. there needs to a solid foundation of technical understanding. If you have engineering ressources that can build the data-pipeline for you, you shouldn't deal with Hadoop or Kafka nodes. If you don't have engineering ressources but money, you're better of integrating a third-party SDK which does all the technical work and lets you focus on the insight generation rather than maintaining clusters. In any case however, you need to be able to have an overview of the data sources available, fetch data from API's or pull it with SQL from another source. A big chunk of the work will be getting and cleaning the data. Sometimes it might be necesarry to transform it, so technicall skills are crucial when building a team.

##### Telling a story

Data itself is worth nothing, to the contrary it creates costs. It only becomes valuable if you know how to properly use it. When we hide all the technical challanges and statistical methods it require it comes down to one thing - telling a story. By telling a story i don't refer to creating analogies to real world situations or anything similar but rather on understanding where to come from (initial problem), what to do to solve it (hypothesis) and to check if it worked (validation). When going through all these steps it becomes a story that can be told. Let's stick to our example:

Initial problem
> We get a ton of users to our app, but have a really low conversion rate regarding the signups.

Hypothesis
> If we change the call to action for our signup from "Signup" to "Get fucking started" we increase the signup rate (conversion) from 3% to 5%.

Validation
> The signup rate dropped from 3% to 2% and the users felt offended and complained about the call to action text so we stopped the experiment and come up with something else.

So telling a story when communicating the results is an essential skill required for a data scientist.

##### Crunching numbers

I'm not a math genius neither was i the best in class in statistics. However one thing you eventually have to do after getting, cleaning and transforming the data is to do calculation or run simple statisticall models like a regression to do predictions. Don't worry you don't need a PhD for that, there are a lot of ressources where this knowledge can be learned or refreshed. I can recommend the [data science specializaton](https://www.coursera.org/specialization/jhudatascience/1) and [machine learning course](https://www.coursera.org/course/ml) both on Coursera. If you search [machine learning](https://www.youtube.com/results?search_query=machine+learning) on youtube , thats another good way to start. In any case i'd recommend everyone to either learn or hire this skillset into the insights team.

## Building a technical infrastructure

In general there are two ways of building a tracking infrastructure

1. You build your own trackers, collectors, processing, storage and visualization (make)
2. You implement a third-party solution that does all that for you (buy)

I love engineering and sometimes tend to always build everything in-house. Why not setup a [kafka](https://github.com/apache/kafka) messaging system, use [hadoop](https://github.com/apache/hadoop) for processing and then store it on HDFS or something similar. A perfectly distributed systems using open-source technologies.

Well, thats not even half of the story. One challange of such a system is building suitable trakers send the events or logs. Especially in mobile there is caching, dispatching and it shouldn't affect the performance. The biggest challenge however, is the visualization piece. It takes at least a full month an a data scientist to build all the queries and charts needed on answer certain questions and i'm not talking about the basic reporting piece of MAUs and DAUs. To cap it all every single piece in this pipeline can brake and needs to be maintained. That concludes to an initial two months project with one full-time data engineer and one data scientist dedicated to building basic reports for the team, without probably answering a single relevant question.

The simpler way, especially for small startups is the third-party solution. At the end it probably costs less, works better and scales with the company growth. I'm not saying don't build your own pipeline, if you can you should go for it. In reallity however, most companies can't but they can still generate insights. At the end its a business model and costs consideration. If you're business model is based on the data and you're using it for a bunch of different stuff you probably build you own pipeline anyway. If not you can do the calculation on a spreadsheet and decide.

I created two curated lists on github, one for [bigdata technologies](https://github.com/onurakpolat/awesome-bigdata) and building your own infrastructure and another one for third-party [analytics tools](https://github.com/onurakpolat/awesome-analytics).

![Awesome bigdata](/assets/posts/2014-10-14-insights-with-lean-analytics/awesome-bigdata.png)

## Defining a lean process

## Choosing the right metrics

## Making predictions

## Where to go from here?



{% include twitter_plug.html %}

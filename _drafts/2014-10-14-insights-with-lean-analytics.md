---
layout: post
title: Insights with lean analytics
comments: true
permalink: "insights-with-lean-analytics"
---

PLACEHOLDER TITLE IDEAS:
GET STARTED WITH LEAN INSIGHTS
LEAN INSIGHTS OVERVIEW
THE ULTIMATE APPROACH TO LEAN INSIGHTS
LEAN DATA PIPELINE AND HYPOTHESIS DRIVEN ANALYTICS

Input: http://radar.oreilly.com/2015/08/what-it-means-to-go-pro-in-data-science.html

PLACEHOLDER IMPLEMENT FAILS!
PLACEHOLDER WHOLE DATA FUNNEL STARTING FROM QUESTION IN UNTIL VIZ + ACTION
START WITH QUESTION END WITH ACTION (BETWEEN DATA RAW PROCESS PIPELINE MODEL VIZ)
Question - Hypothesis - Tracking (RAW) - Analytica Data (Processed) - Model Selection - Model (Computation ML) - Visualization (Tables/Figure) - Action (Recommendation)

![DatascienceLand](http://www.dataiku.com/static/img/blog/technoslavia/technoslavia-map-dataiku-800.png)

http://i2.wp.com/sciencereview.berkeley.edu/wp-content/uploads/2014/04/spring_2014_azam_01.jpg

http://i0.wp.com/sciencereview.berkeley.edu/wp-content/uploads/2014/04/spring_2014_azam_05.jpg

FYI - http://www.datasciencecentral.com/profiles/blogs/best-solution-to-a-problem-data-science-versus-statistical-paradi

question -> input data -> features -> algorithm -> parameters -> evaluation

Covariate creation from Raw data to tidy data set (keep only relevant information)

Data only exists within a framework of a vision you are building to

unsupervised learning can be use-ful as pre-processing step for supervised learning.

In this post i'll share my expierences of the last two years on building an insights team in a startup and how we did the transition from data analysts to data scientists to generate actionable insights that matter. The areas i'll touch are [setting the goals](#setting-the-goals), [building a team and structures](#building-a-team-and-structures), [building a technical infrastructure](#building-a-technical-infrastructure), [defining a lean process](#defining-a-lean-process), [choosing the right metrics](#choosing-the-right-metrics) and [making predictions](#making-predictions).

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

PLACEHOLDER data pipeline (Trackers - RAW data - processed data - analysis - report - viz) FUNNEL
Garbage in garbage out

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

PLACEHOLDER VENN DIAGRAM WITH ALL 4 SKILLS

## Building a technical infrastructure

PLACEHOLDER RENAME BUILD TRACKING
PLACEHOLDER DEFINE SAMPLE EVENTS
Build a "transparent box" especially when you process data

In general there are two ways of building a tracking infrastructure

1. You build your own trackers, collectors, processing, storage and visualization (make)
2. You implement a third-party solution that does all that for you (buy)

I love engineering and sometimes tend to always build everything in-house aka facebooks "hack everything" culture. Why not setup a [kafka](https://github.com/apache/kafka) message bus or [hadoop](https://github.com/apache/hadoop) and then store it on HDFS or something similar. A perfectly distributed large-scale system using open-source technologies. There are other technologies like Googles Bigquery or Amazons Redshift which can be used for fast quering large amount of data.

Well, thats not even half of the story. One challange of such a system is building suitable trakers send the events or logs. Especially in mobile there is caching, dispatching and it shouldn't affect the performance. The biggest challenge however, is the visualization piece. It takes at least a full month an a data scientist to build all the queries and charts needed on answer certain questions and i'm not talking about the basic reporting piece of MAUs and DAUs. To cap it all every single piece in this pipeline can brake and needs to be maintained. That concludes to an initial two months project with one full-time data engineer and one data scientist dedicated to building basic reports for the team, without probably answering a single relevant question.

The simpler way, especially for small startups is the third-party solution. At the end it probably costs less, works better and scales with the company growth. I'm not saying don't build your own pipeline, if you can you should go for it. In reallity however, most companies can't but they can still generate insights. At the end its a business model and costs consideration. If you're business model is based on the data and you're using it for a bunch of different stuff you probably build you own pipeline anyway. If not you can do the calculation on a spreadsheet and decide.

I created two curated lists on github, one for [bigdata technologies](https://github.com/onurakpolat/awesome-bigdata) and building your own infrastructure and another one for third-party [analytics tools](https://github.com/onurakpolat/awesome-analytics).

PLACEHOLDER REPLACE IMAGE WITH TABLE OR TWO TABLES FOR MOST COMMON TOOLS ETC.

![Awesome bigdata](/assets/posts/2014-10-14-insights-with-lean-analytics/awesome-bigdata.png)

## Defining a lean process

Choosing the right metrics

## Analyzing data

BE Critical - every data can be noisy or even wrong

Write code for your anaysis don't use guis for more reproducibility

Automate as much as possible

Don't do things by hand

It initially takes longer but prevents hassle in the end

Use version control (Git)



## DO: Keep track of your software environment

* Computer architecture
* Operating system
* Software toolchain
* Support software (packages etc.)
* External dependencies
* Version numbers

## Making predictions

## Take action

If action needs to be taken make suggestions

If question needs to be adressed, try to make them

## Conclusion



{% include twitter_plug.html %}

# Building lean insights for product companies

Lean analytics is a tool used by small and medium businesses that measure very specific factors that would analyze the growth and success of the business. It’s a perfect mix of lean startup and analytics. Lean insight is the collecting, processing and analyzing of data to produce actionable insights that matter. 

The first step in building lean insights is setting your goals and deciding what should be your end results. Lean insights are usually developed in a team so before starting set your goals, discuss them and effectively communicate with others and get all the necessary approvals. There are three most important things to keep in mind when setting goals. Firstly identify the problems and issues you are looking to solve. If you start the process without identifying the problem, chance of failure increase significantly. Once you have identified the problem, define and set your hypothesis to be tested. Your hypothesis needs to be solid and credible which could be tested by statistics and scientific research. 

Once your hypothesis is established, design a test for your hypothesis, similar to that done in the study of econometrics. The most important thing at this stage is to inform everyone in the company to understand the data and learn to think through it. This process has to start from the top of the management, i.e. CEO and work its way down and all efforts should be made to either falsify or validate the established hypothesis. 

The next step is to finalize the team, the structure and the hierarchy of command. The long term strategy is made up for four different perspectives. The first is product perspective which is basically web and mobile analytics. Under this you define and validate product related hypothesis. Next is the financial perspective under which you determine and estimate all costs. Next up is the marketing perspective which focuses on all the marketing and promotional aspects of the business. From this point of strategy you analyze all market competitors and marketing options to optimize output. The last tool is the technical perspective under which you build a robust and consistent analytics infrastructure and aggregate sources. 

The product is the most crucial aspect and all other factors revolve around it so it only makes sense that majority of the time is spent on it to better understand and execute the data. All decisions that are being made need to be coherent and synchronized with each other just like the marketing mix. For instance the financial decisions need to match with the decisions made regarding marketing and promotions etc. A data analytic should have deep understanding of the business model in order to execute the lean analysis. 

As far as the technical aspect is concerned, every person has their own preferences depending on which software they are comfortable with. People with engineering background would not feel comfortable with using Hadoop or Kafka nodes. Similarly, if you have an economics background using Stata would be a better option. Most of the time at this stage would be sent at collecting and cleaning the data. Technical skills are a must to have so it is important to have an expert in the team. 

The general perception is that quantitative data is worth much but the truth is, alone it isn’t worth a penny. It will only be valuable to the company if your team knows how to use and manipulate it effectively to study your hypothesis. You need to structure your findings and give coherence to it by first defining the initial problem then proposing your hypothesis and finally checking for validation all the while supporting your findings with the data you have collected. The most important thing is to present your findings in a manner that people with even little or basic background regarding the subject could easily understand your findings. 

As previously mentioned, technical background is important to have. Once you have your data collected it is important to run some basic tests and regressions to check your data for validity. These tests can be run on any number of software systems and one does not need to be an expert in running these tests, basic knowledge is sufficient enough to make it work for instance crash courses such as data science specialization and machine learning course which are both on Coursera.

Moreover when we previously talked about coherence it is advisable to build a technical infrastructure. There are two basic ways in which to build an effective tracking infrastructure. Firstly you build or make your own trackers, processors, collectors and storage space etc. or secondly you implement a solution developed by a third party in which case you buy it. Some technologies available in the market are Googles Bigquery or Amazons Redshift which can be used for large amount of data. Many people with an engineering background are also fond of following what is known as “hack everything” culture.  The most challenging aspect of this infrastructure is building suitable trackers and the events or logs. In the case of mobile phones this is especially crucial as there is caching, dispatching which sometimes does slow the performance but doesn’t significant effect it much. Moreover, the visualization piece is also another major challenge faced by many people. For a data scientist it takes about a whole month of developing an effective system of all queries and charts in order to answer certain questions. Every single piece in the pipeline is vulnerable and can break; hence it needs to be maintained. Hence the whole process takes about two months with the help of a full time data engineer working alongside with one data scientist whose sole responsibility is building basic reports for the entire team.

The process mentioned above is all about when you need to develop your own system from scratch. Naturally, building your own technical infrastructure is expensive thus for smaller businesses it is much easier and simpler to buy a third party solution. Not only does it costs less but it is a tested system which works better and scales with the company growth. However, this is not to suggest that companies should not build their own pipeline. If you have the finances and the skill, building your own infrastructure should always be an option however, realistically speaking not a lot of companies can build their own but they still manage to generate insights. At the end of the day the decision lies on the business model and the estimated costs and budgets. For instance, if your entire business model is based on a data set which is being used for different things than building your own pipeline would seem like a more viable option.

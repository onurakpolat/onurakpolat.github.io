---
layout: post
title: Make predictions with localytics data
comments: true
permalink: "make-predictions-with-localytics-data"
---

## Intro

As a product company using data to inform our product development has always been a goal for us. To avoid most of the complexity when dealing with event data we implemented localytics for tracking and processing our data. It turns out that has been very benefitial so we could focus on insights generation rather than data munging.

## What we do

After implementing the Localytics SDK's and setting up the screens, events and custom attributes we were pretty much done. The only thing we built on top of that was a simple script that copies the raw data to our Amazon S3 buckets and copies them to Redshift. With that simple process we are able to provide anybody in the company with insights and still be able to dive deeper into the raw data.

## Diving deper

As we have defined the first session of a user as the most critical experience we need to optimize we came up with several hypothesis we wanted to test and validate with data. One question we asked ourselves is what usage patterns that we translate into variables impacts the number of sessions a user has in their first week the most?
Alone and especially in short term this might not be the best question but we felt like it was a good starting point.

## Methodology

Our approach was as simple as you could think of. We wrote a SQL query and loaded the data of new users we looked at over a week into an R data-frame. As the data is provided perceftly clean by localytics, we didn't need to clean or process it much. Running the regression analysis in R was literally just one line of code and the results were amazing. The first model we've built explained 50% of what impacts the number of session in the first week. We found out that setting the favourite football team had by far the highest impact on the number of sessions. The signup process and activating push were other important features we found. Now it might be a correlation between heavy users and behaviour pattern in the app rather than causal finding, however we'll continues A/B testing and running experiments to find the causes within our product.

## Where to go from here

The regression analysis was the first simple analysis we perfomed. We'll continue analysis other discrete variables such as retention using a logistic regression from our data. We also throgh in different variables into our model to get a more statistically significant and reliable model.

## Conclusion

Our goal is to create insights, not deal with massive amounts of data and building systems to handle it. Localytics works out great for us and free us from all the pain and engineering effort to do so. We now start to learn more about data science and use statistics on our data to learn how to build our product.

{% include twitter_plug.html %}

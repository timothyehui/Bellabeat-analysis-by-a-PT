# Bellabeat-analysis-by-a-PT
This is the Bellabeat case study from the Google Analytics course.  Of course, I'm also a Physical Therapist, so there's more than just an analysis of the Fitbit data.

In the Google Data Analytics course, the final project is a case study for students to demonstrate skills they have learned.  One such case study is for Bellabeat, a company that sells fitness trackers targeted to women.  Students are to analyze open source data from Fitbit to provide recommendations to the co-founders and the marketing analytics team.

But I am not typical student in this case.  Along with the courses in the Google Analytics certificate program, I have…

Doctorate in Physical Therapy
Doctorate in Chiropractic
BS in Physiological Science

So, any analysis I do must also utilize my 20 years of patient experience focusing on orthopedic and sports injuries as well as fitness regiments to prevent these injuries.

But let’s start by going through the steps.

Step 1: Ask

Background – Bellabeat is a manufacturer of wearables, aimed toward women.  Urška Sršen and Sando Mur are the co-founders and members of the executive team.  The Marketing analytics team is also involved.

Srsen asks that I look at trends in smart device usage, how these trends apply to customers, and how this could affect marketing.

Let’s look at Bellabeat’s products.

Bellabeat offers Leaf – a wearable tracker, Time – a wristwatch tracker, and Spring – a water bottle.

I will pick the Leaf, Bellabeat’s wearable tracker.  The problem is how to have one fitness tracker stand out in a field of fitness trackers.  So, can trends in smart device use could influence marketing strategy.

 
Step 2: Prepare
FitBit has loaded data from 30 users into a public domain file on Kaggle.  Kaggle: FitBit Fitness Tracker Data.  This was from 2016 where Fitbit user gave consent to data including physical activity, heart rate, and sleep monitoring.  There is also information about daily activity, steps, and heart rate.  This data was gathered through a survey.

The acronym to analyze data is ROCCC

Reliable – Poor- Thirty users, likely self-selected do not result in a representative population

Original – Poor – This is third party data from Amazon Mechanical Turk

Comprehensive – Some would say this could be comprehensive, but I will say this is poor and discuss this later.

Current – the data is from 2016.  Do people wear fitness trackers differently now?  To answer this, I ask if any fundamentally new technology has appeared in the fitness market since then.  The answer is no, so the data is likely current.

Cited – This is not a scientific article.  From everything previously listed, this would not pass muster in most scientific journals, so this is poor.


In conclusion – the data is not good.  But perhaps some knowledge can still be gleaned from this.



Step 3: Process
First, I installed the tidyverse package

install.packages("tidyverse")
library(tidyverse)
library(readr)

Then I uploaded data.  I focused on the dailyIntensities

##upload data to R
dailyIntensities ← read_csv(“dailyIntensities_merged.csv”)
View(dailyIntensities)


Then I selected that data I waned to graph

##select specific data
Activity <- dailyIntensities %>%
rename(c("ActivityDay"="Date")) %>%
select(Id,Date,SedentaryMinutes,LightlyActiveMinutes,FairlyActiveMinutes,VeryActiveMinutes)





Step 4:Analyze

I decided to eliminate SedentaryMinutes because I want to see what people are doing, not how much they are not doing.

So, I made graphs of LightlyActiveMinutes, FairlyActiveMinutes, and VeryActiveMinutes by date.









ggplot (data=Activity)%>%
     +     geom_point(mapping=aes(x=Date, y=LightlyActiveMinutes)) %>%
      +    theme(axis.text.x = element_text(angle = 90))





+     +   






















ggplot (data=Activity)%>%
+     +    geom_point(mapping=aes(x=Date, y=FairlyActiveMinutes)) %>%
+     +   theme(axis.text.x = element_text(angle = 90))




























ggplot (data=Activity)%>%
+     +     geom_point(mapping=aes(x=Date, y=VeryActiveMinutes)) %>%
+     + theme(axis.text.x = element_text(angle = 90))




















Step 5 - Share




Now, this shows something interesting.  Look at where the minutes are evenly distributed



Time distribution
LightlyActiveMinutes
0-400
FairlyActiveMinutes
0-50
VeryActiveMinutes
0-125


I did not use statistical analysis because these trends can easily been seen visually and the data quality lends to more qualitative versus quantitative analysis.


Light activity is the most common which is expected.  However, activity considered “Very Active” comes in second, significantly more than “Fairly Active.”  The intuitive answer would be that time spent on activity should be inversely proportional to intensity; why would people want to do more of something that’s hard?  However, it does appear that people will spend a proportional greater time on very active ex

Therefore, our population is most likely to spend their day being lightly active or very active.  So, we should look at what exercises would be in these categories.





Dancing, ballroom			219
Bicycling, < 10 mph, leisure		292
Golfing, carrying clubs		314
Skiing, downhill			314
Walking, 3.5 mph			314
Aerobics, low-impact			365
Elliptical trainer, moderate effort	365
Aerobics, water			402
Swimming laps, light or moderate	423
Hiking					438
Running, 5 mph			606


Based on Ainsworth BE, et al. 2011 compendium of physical activities: A second update of codes and MET values. Medicine & Science in Sports & Exercise. 2011;43:1575.

This  data was inputted and sorted on Excel.
So, looking at this chart.  The LightlyActive exercise would be Cycling, FairlyActive would be Aerobics, and VeryActive would be running.




I believe that focusing our product towards these activities would be an effective marketing strategy.






Step 6: Act 


Looking at the Fitbit data, what jumps out to me is how activity is categorized.

There is activity.

There is intensity of that activity.

Even though the quality of our data is poor, I believe that these qualitative observations are accurate enough to be useful to Bellabeat.


Therefore:

I believe that providing customers with a product specialized to their exercise of choice would produce a market differntiator.  Tell people that they can get not only an activity tracker, but one that’s designed for their chosen activities.



Although it may be nice to use trackers as all-in-one products, I believe it would be advantageous to offer different products to different market segments.

Here are three possible options.

Runners – tracker offers GPS capabilities to more accurately measure running distance, running speed, incline, and elevation change.  This can be done by interfacing with the mobile device.  This tracker should also accurately measure running cadence, and provide an immediate alert or notification when a runner breaks their cadence, meaning that they are not holding a consistent pace.  
 - I believe this is the best option.  There are many running clubs and stores.  A running population can explain why VeryActiveMinutes is greater than FairlyActiveMinutes.



Cycling/spin – Although cyclists may disagree, this is lightly active per the research data.  One options is for the Bellabeat devices to interface with the bike or ergometer to provide accurate intensity.  The tracking device could also interface with spin classes, measuring time out of saddle and additional upper body exercises.  Partnership with companies like Peleton or Soul Cycle would be ideal.

Bootcamp – This is likely fairly active exercise.  Here, the tracker interfaces with equipment to provide an accurate measurement of intensity, but also ensure that exercises are balanced between upper and lower extremities as well as right and left sides of the body.  Equipment examples would be weights, kettle bells, and jump rope.  Partnership with Orangetheory or other exercise chains would be ideal.
 - this could potentially require the most work and that other equipment manufacturers create “smart” equipment which can interface.


Another potential benefit is that the caloric burning measurements for each activity can be studied and optimized for each exercise market, providing Bellabeat with a clear market differentiator.  


To summarize, the fitness tracker industry is saturated.  To grow, fitness trackers must open new markets, and this will require partnership with other fitness organizations and other companies.  An all-in-one product makes for easier supply chains, but it also makes it virtually impossible to stand out amongst the crowd.  

Based on my analysis of Fitbit data and other sources, I believe that focusing on runners offers the best potential for growth.  

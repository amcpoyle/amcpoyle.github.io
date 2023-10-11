---
layout: post
title:  "450 Supercross Rankings: Who is the Greatest SX Rider Ever? Version 0."
date:   2023-10-10 20:51:17 -0400
categories: supercross
---
**Introduction**
In 2006, the 450 class was introduced as the new premier class for AMA Supercross. One of the most common questions among all sports globally is, 
“Who is the greatest ever?” Using a linear mixed-effects models (the statistical package “lme4” in R), 
we can begin to see who emerges at the top of this debate.

**Method**
First, data was scraped from the RacerX website for all 450 SX races (2006-2023). Then, the points method was applied to the finish position. 
There were 2 iterations of the model, both using the same linear mixed-effects formula. The first iteration used all of a rider’s results from 
their 450sx career, the second iteration used the 3 consecutive best years based on sum of points (the 3 consecutive years where the rider 
scored the most points). The formula is the following: 

points ~ rider + (1|race). 

So race is the random effect and rider is the fixed effect. 
To be fair, having race as a random effect is not ideal, I would much prefer to have team as the random effect that we control for. However, data for 
every rider’s team from 2006-2023 is not readily available, so it will take some time to compile this information. An updated method will be written
whenever this compilation is complete.

**Results**
![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_1.png)

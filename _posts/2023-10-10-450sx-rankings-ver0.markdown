---
layout: post
title:  "450 Supercross Rankings: Who is the Greatest 450SX Rider Ever? Version 0."
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
scored the most points). The formula is the following: points ~ fixef(rider) + ranef(race).

So race is the random effect and rider is the fixed effect. 
To be fair, having race as a random effect is not ideal, I would much prefer to have team as the random effect that we control for. However, data for 
every rider’s team from 2006-2023 is not readily available, so it will take some time to compile this information. An updated method will be written
whenever this compilation is complete.

One more thing to note is that the R2M (fraction of variance explained by fixed effects) is .625 for this model, and the R2C (fraction of variance explain by random effects is 0.631, so adding in race data does little to change a rider's points scored (i.e., what race they are at really shouldn't matter for how many points a rider will score).

**Results**

![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_1.png)
![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_2.png)
![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_3.png)
![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_4.png)

And there is more, but here are the riders at the bottom of the rankings:

![ranking best](/images/450sx_ranking_ver0/450sx_ver0_rank_worst.png)

**Comments About the Rankings**
I think generally the rankings are pretty accurate to the commonly held beliefs of supercross fans, but there are always some generated rankings that are debateable. From the top 25, some potentially debateable rankings are the following:

1. James Stewart ranked as the greatest 450SX rider ever.
2. Dungey over Villopoto.
3. Musquin over Roczen.

**James Stewart: The Greatest 450SX Racer?**
The 3 best years for JS7 are 2007, 2008, 2009. He completed 35 races during this time, with a mean finish position of 2.029 (median 1), so this was a dominant interval of time for him. He won the title in 2007 and 2009, and was injured in 2008 when Chad Reed won. It’s impressive that his 3 best years include one that was almost entirely wiped out by injury (scoring only 47 points), however, Stewart was injured frequently during his career, and having 3 consecutive seasons without injury was unheard of for him.

In 2007, he won 13/16 races.

In 2008, he raced only 2 races, but placed 2nd and 1st respectively.

In 2009, he won 11/17 races, with an outlier 19th in the first race of the season, one 7th, three 2nd places, and one 3rd in a closely contested championship with Chad Reed.

Given his dominance in 2007 and 2009, and his dominance in 2008 until he got injured, JS7 as number one seems like a fair ranking. Most riders do not stay healthy for 3 consecutive supercross seasons, let alone 3 dominant consecutive seasons. Also, the point of the multilevel model is to try and improve on ranking by total points, and, in essence, try to measure a rider's "talent" level.

**Battle of the Ryans: Dungey over Villopoto**
It’s important to clarify that Ryan Dungey’s 3 best years were 2015, 2016, and 2017, just after Villopoto’s retirement and when Dungey first began working with Aldon Baker. On the contrary, Villopoto’s best years were 2012, 2013, and 2014. I think this is a good example of why a competition effect is required in any sort of ranking. For sure, Dungey was always the second best rider pre-2015, but after Villopoto left the class, it was evident how far ahead the two of them were to everyone else (on a consistent basis, at least).

I was writing this section and realized a more in-depth analysis of the Ryans warrants another article, given that I think it is one of the most interesting rivalries in all of supercross/motocross.

**Marvin Musquin vs Ken Roczen**
Musquin’s best years are calculated as 2017, 2018, 2019. In 49 total races during these 3 years, Musquin won 8 races, podiumed 34 races (including wins), and was top 5 in 41 races (including wins and podiums). It’s generally forgotten how fast and consistent he was during this interval of time. He finished 3rd overall in the championship in 2017 behind Dungey and Tomac, and 2nd overall in 2018 behind Jason Anderson (arguably Musquin’s year to win the championship). In 2019, he was again 3rd overall, in a close battle with Webb and Tomac.

On the contrary, Roczen’s supercross career has been plagued by injuries which creates an inconsistency for him. His best years are 2019, 2020, and 2021, just after his devastating arm injury in 2018 (and his other traumatic arm injury in 2017). He completed 51 races with 8 wins, 26 podiums, and 37 top 5s. Although their 3 year intervals are close statistically, Musquin was slightly more consistent with more podiums and more top 5s, although he may not be seen as the more “talented” rider, in general.

**Things to Improve**
No ranking model is perfect, and this one surely is nowhere near perfect. Here are a few things that came to mind while programming the model and looking at the results it produced:

- A competition effect. Perhaps Dungey was better in the span of his 3 years than Villopoto, but if Villopoto’s competition was more difficult (i.e., he had Dungey to compete against), then how do we quantify that and factor it into our ranking? Multilevel modeling with a competition effect has been used to rank Formula One drivers, so perhaps something similar can be employed here.
- Have the random effect be for teams, not races. It would be more interesting to see how teams effect the outcome of rider points scored, rather than how changing races effects it.

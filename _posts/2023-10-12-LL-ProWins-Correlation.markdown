---
layout: post
title:  "Correlation Between Pro Supercross/Motocross Wins and Loretta Lynn's Titles"
date:   2023-10-10 20:51:17 -0400
categories: supercross
---

Note: I looked at this data in August, 2023 after this year's Amateur National Championships.
**Introduction**
Every year in the first week of August, the Amateur National Motocross Championships at Loretta Lynn’s takes place. It is by far the biggest amateur motocross race of the year, and by some standards, it is the only race that matters. Every 450 Supercross or Motocross Champion in history has won a title at Loretta Lynn’s in their amateur career, and good showings at this race are virtually the only way to secure a ride with a top team to begin a professional career. Amateur racers can qualify for up to three classes at the race, paying three entry fees along the way. Naturally, the race organizers want to make as much money as possible, so they create innumerable classes. Classes are broken up based on engine size of the bike and age. There exist historically prestigious classes where the top amateurs–those who are going to be the next stars of the sport–battle it out for sponsorships and recognition.

A question that arises is: which classes are most highly correlated with pro wins? Certainly not the 50+ age range, but maybe we overrate classes that are traditionally thought of as decent stepping stones to a pro career. The announcers always like to mention that anyone 	could be the next star of the sport, even in the less prestigious classes, but is this actually true?

**Method**
I scraped the names of all riders with professional race entries from RacerX. I then scraped each rider’s Loretta Lynn’s results from RacerX’s LL Vault archives. I stored these historical results in a Pandas dataframe, and exported them to CSV. I then used the list of riders to scrape each rider’s professional race results from RacerX, also, and stored and exported this to a separate CSV.

I then compiled all riders who have a 450 MX or SX overall victory in their career, and then used their Loretta Lynn’s results to create a correlation matrix that correlates pro wins against the LL class. I realized that classes at Loretta’s change over time, and that some classes have been gone for years. I created an “edited classes correlation” where I only include classes that have been raced by professional racers (examples that were eliminated: all senior classes, WMX, 250 All-Star A/B 14+ (not raced anymore)) (new_ll_corr)lation matrix only using data for riders that are currently racing so that there were less historical outliers (e.g. Ricky Carmichael, the greatest rider of all time, raced LL in the 1990s and raced some classes that are no longer around, but these classes have high position correlation because Carmichael has so many wins) (current_riders_correlation).

**Results**
![correlation best](/images/ll_prowins_corr/ll_correlation_top25.png)
![correlation worst](/images/450sx_ranking_ver0/ll_correlation_bottom25.png)
![current correlation best](/images/450sx_ranking_ver0/current_ll_top25.png)
![current_correlation_worst](/images/450sx_ranking_ver0/current_ll_bottom25.png)

**Comments**
The correlations support the idea that the classes traditionally thought of as the most "prestigious" or important to sponsors at Loretta Lynn's are generally the ones most highly correlated to pro wins. However, an interesting question comes up: are these classes the most correlated because they are already thought of as the most important, and hence the most resources get thrown into them and the riders that are in them? Talent is attracted to these classes because historically, a lot of talent has come out of them. That's probably the case, but it is still indicative of what classes to watch for the next champions of the sport. It is also interesting to note the number of limited classes at the bottom of the correlation. Limited classes typically feature riders with less support from sponsors and less personal financial resources. Seeing these classes at the bottom is also a reminder of how essential financial backing is to do well in the sport, and that most sponsors would rather see their products in the modified classes. There are quite a few stock classes that are high in correlation, but no limited classes and there are no modified classes at the bottom of the correlation.

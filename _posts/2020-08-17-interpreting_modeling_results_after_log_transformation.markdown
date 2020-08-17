---
layout: post
title:      "Interpreting Modeling Results after Log Transformation"
date:       2020-08-17 11:30:26 -0400
permalink:  interpreting_modeling_results_after_log_transformation
---


Using log transformation to normalize my data significantly improved my model's prediction accuracy. As you can see below, my actual vs. predicted values significantly improved after using a log base of 10. 


Before log transformation: 
![](https://github.com/stones-1130/dsc-mod-2-project-online-pt-041320/blob/master/output_56_0.png)


After log transformation:
![](https://github.com/stones-1130/dsc-mod-2-project-online-pt-041320/blob/master/output_77_0.png)

Unfortuantely, extracting meaning from these results can be a challenge because the data is no longer in it's original form. I used multiple articles and other blog posts to help me make sense of my newly log transformed data. Specifically, I wanted to be able to interpret the coefficient score from the model. 

```
#BACK-TRANSFORMATION CALCULATION FOR TOP THREE COEFFICIENTS

print('loggrade:', round(((2.36**1.36)-1)*100) , '%')
print('logsqft_living:', round(((1.53**.53)-1)*100) ,'%')
print('logsqft_condition:', round(((1.35**.35)-1)*100) ,'%')

```
Output: 

loggrade: 221 %
logsqft_living: 25 %
logsqft_condition: 11 %

To do this, I had to think about the coefficient value as the percent increase in the dependent variable for every 1% increase in the independent variable (price).

Explained another way, for x percent increase, calculate 1.x to the power of the coefficient, subtract 1, and multiply by 100.

Using this method, I was able to explain the meaning of the new coefficent values:

**1. loggrade:** For every 136% increase in price, the grade (builing construction and design quality) of a house increases by about 221%

**2. logsqft_living:** For every 53% increase in price, the internal square foot of a house increases by about 25%

**2. logsqft_condition:** For every 35% increase in price, the overall condition of a house increases by about 11%



Citation: https://data.library.virginia.edu/interpreting-log-transformations-in-a-linear-model/



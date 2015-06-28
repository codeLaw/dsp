[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

First babies are slightly lighter (mean = 7.20) than non-first babies (mean = 7.33).  Cohen's d, however, revealed that this difference was only -0.09 standard deviations. Values of .2, .5, and .8 are considered small, medium, and large, respectively.  This small value is similarly small as that derived from the same calculation on mean pregnancy length for the same group comparison (0.029).

Code

import nsfg
import math
from numpy import mean, var

def CohenEffectSize(group1, group2):
	diff = group1.mean() - group2.mean()
	
	var1 = group1.var()
	var2 = group2.var()
	n1,n2 = len(group1), len(group2)
	
	pooled_var = (n1 * var1 + n2 * var2)/(n1+n2)
	d = diff/math.sqrt(pooled_var)
	return d

df = nsfg.ReadFemPreg() 

live = df.outcome == 1

live.first = df.birthord == 1
live.others = df.birthord != 1

firstWeight = df.totalwgt_lb[live.first] #8.8125
otherWeight = df.totalwgt_lb[live.others] #7.8750

print 'First Born Birth Weight:', round(firstWeight.mean(),3)
print 'Non First Born Birth Weight:', round(otherWeight.mean(),3)

d = CohenEffectSize(firstWeight, otherWeight)
print 'Cohens d:', round(d,3)

Output
First Born Birth Weight: 7.201
Non First Born Birth Weight: 7.326
Cohens d: -0.089






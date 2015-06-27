[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

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

df = nsfg.ReadFemPreg() #ThinkStats2

live = df.outcome == 1

live.first = df.birthord == 1
live.others = df.birthord != 1

firstWeight = df.totalwgt_lb[live.first] #8.8125
otherWeight = df.totalwgt_lb[live.others] #7.8750

print firstWeight.mean()
print otherWeight.mean()
print CohenEffectSize(firstWeight, otherWeight)

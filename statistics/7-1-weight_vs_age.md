[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

REPLACE THIS TEXT WITH YOUR RESPONSE


```
import nsfg
import numpy as np

import first
import thinkplot
import thinkstats2

df = nsfg.ReadFemPreg()
df = df.dropna(subset=['agepreg', 'totalwgt_lb'])

live = df.outcome == 1

ages = df.agepreg[live]
weights = df.totalwgt_lb[live]
print('thinkstats2 Corr', thinkstats2.Corr(ages, weights))
print('thinkstats2 SpearmanCorr', 
thinkstats2.SpearmanCorr(ages, weights))

thinkplot.Scatter(ages, weights, alpha=0.1)
thinkplot.Show(xlabel='Age of Mother (years)',ylabel='Weight of Baby (lbs)')

bins = np.arange(10, 45, 5) 
indices = np.digitize(df.agepreg, bins) #computes bin num for each value
groups = df.groupby(indices)

#for i, group in groups: #print num rows for each group
#	print(i, len(group))

ages = [group.agepreg.mean() for i, group in groups]
cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups]

thinkplot.PrePlot(3)

for percent in [75, 50, 25]:
    weights = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    thinkplot.Plot(ages, weights, label=label)

thinkplot.Show(xlabel='Age of Mother (years)',ylabel='Weight of Baby (lbs)')
```

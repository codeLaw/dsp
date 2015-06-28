[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

Because the CDF plot is essentially a straight line, we can conclude that the distribution is uniform.

Code

import random
import thinkstats2
import thinkplot
sample = []

for i in xrange(1000):
	sample.append(random.random())

pmf = thinkstats2.Pmf(sample)
thinkplot.Pmf(pmf, linewidth=0.2)
thinkplot.Show()

cdf = thinkstats2.Cdf(sample)
thinkplot.Cdf(cdf, linewidth=1.0)
thinkplot.Show()

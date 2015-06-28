[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

I used the InterpolateSample function.

```
import numpy as np
import thinkstats2

import hinc
import density

def InterpolateSample(df, log_upper):
    """Makes a sample of log10 household income.

    Assumes that log10 income is uniform in each range.

    df: DataFrame with columns income and freq
    log_upper: log10 of the assumed upper bound for the highest range

    returns: NumPy array of log10 household income
    """
    # compute the log10 of the upper bound for each range
    df['log_upper'] = np.log10(df.income)

    # get the lower bounds by shifting the upper bound and filling in
    # the first element
    df['log_lower'] = df.log_upper.shift(1)
    df.log_lower[0] = 3.0

    # plug in a value for the unknown upper bound of the highest range
    df.log_upper[41] = log_upper

    # use the freq column to generate the right number of values in
    # each range
    arrays = []
    for _, row in df.iterrows():
        vals = np.linspace(row.log_lower, row.log_upper, row.freq)
        arrays.append(vals)

    # collect the arrays into a single sample
    log_sample = np.concatenate(arrays)
    return log_sample

df = hinc.ReadData()
log_sample = InterpolateSample(df, log_upper=6.0) # set as 6.0 or 7.0

log_cdf = thinkstats2.Cdf(log_sample)
sample = np.power(10, log_sample)
mean, median = density.Summarize(sample)

cdf = thinkstats2.Cdf(sample)
print 'cdf mean:', cdf[mean]

pdf = thinkstats2.EstimatedPdf(sample)
```

Ouput:  log_upper = 6.0
```
mean 74278.7075312
std 93946.9299635
median 51226.4544789
skewness 4.94992024443
pearson skewness 0.736125801914
cdf mean: 0.660005879567
```
And with log_upper = 7.0:
```
mean 124267.397222
std 559608.501374
median 51226.4544789
skewness 11.6036902675
pearson skewness 0.391564509277
cdf mean: 0.856563066521
```

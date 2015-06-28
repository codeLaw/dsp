[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

The mean of the actual pmf was 1.02, while the mean of the biased pmf was 2.40.  I used Pmf and BiasPmf (from the book) to obtain the distributions/means as well as thinkplot to plot the data.

Code
```
import chap01soln
response = chap01soln.ReadFemResp()

import thinkstats2
pmf = thinkstats2.Pmf(response.numkdhh)

import thinkplot
thinkplot.Pmf(pmf, label='actual')

def BiasPmf(pmf, label=''):
    """Returns the Pmf with oversampling proportional to value.

    If pmf is the distribution of true values, the result is the
    distribution that would be seen if values are oversampled in
    proportion to their values; for example, if you ask students
    how big their classes are, large classes are oversampled in
    proportion to their size.

    Args:
      pmf: Pmf object.
      label: string label for the new Pmf.

     Returns:
       Pmf object
    """
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

biasedpmf = BiasPmf(pmf, label='biased') 

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biasedpmf])
thinkplot.Show()

print pmf.Mean()
print biasedpmf.Mean() 
```

Ouput
```
1.02420515504
2.40367910066
```

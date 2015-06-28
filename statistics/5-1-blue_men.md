[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

As suggested, I used scipy.stats for this problem.  I used scipy.stats.norm(loc=mu, scale=sigma) (with mu and sigma parameters from the BFRFFS survey), along with the cdf function to determine the percentage of males between 5'10 and 6'1, which was approximately 34.2%.

Code
```
import scipy.stats

mu = 178
sigma = 7.7

heightDist = scipy.stats.norm(loc=mu, scale=sigma)

shortest = heightDist.cdf(177.8) # 5'10 = 177.8
tallest = heightDist.cdf(185.4) # 6'1 = 185.4

percentInterval = tallest-shortest
print percentInterval
```

Output
```
0.342094682946
```

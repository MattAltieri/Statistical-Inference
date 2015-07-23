# P-values

## P-values

- Most common measure of "statistical significance"
- Their ubiquity, along with concern over their interpretation and use makes them controversial among statisticians
    - [http://warnercnr.colostate.edu/~anderson/thompson1.html](http://warnercnr.colostate.edu/~anderson/thompson1.html)
    - Also see _Statistical Evidence: A Likelihood Paradigm_ by Richard Royall
    - _Toward Evidence-Based Medical Statistics. 1: The P Value Fallacy_ by Steve Goodman
    - The hilariously titled: _The Earth is Round (p < .05)_ by Cohen
- Some positive comments
    - [simply statistics](http://simplystatistics.org/2012/01/06/p-values-and-hypothesis-testing-get-a-bad-rap-but-we/)
    - [normal deviate](https://normaldeviate.wordpress.com/2013/03/14/double-misunderstandings-about-p-values/)
    - [Error statistics](http://errorstatistics.com/2013/06/14/p-values-cant-be-trusted-except-when-used-to-argue-that-p-values-cant-be-trusted/)
    
## What is a P-value?

**Idea:** Suppose nothing is going on -- how unusual is it to see the estimate we got?

**Approach:**

1. Define the hypothetical distribution of a data summary (statistic) when "nothing is going on" (null hypothesis)
2. Calculate the summary/statistic with the data we have (test statistic)
3. Compare what we calculated to our hypothetical distribution and see if the value is "extreme" toward the alternative hypothesis (p-value)

## P-values

### An example

- Suppose that you get a $T$ statistic of 2.5 for 15 df testing $H_0 : \mu = mu_0$ versis $H_\alpha : \mu > \mu_0$
    - What's the probability of getting a $T$ statistic as large as 2.5?
    

```r
pt(2.5, 15, lower.tail=F)
```

```
## [1] 0.0122529
```

- So either the null hypothesis is true and we've seen a very rare event, or the null hypothesis is false

### Another example

- The P-value is the probability under the null hypothesis of obtaining evidence as extreme or more extreme than would be observed by chance alone
- If the P-value is small, then either $H_0$ is true and we have observed a rare event or $H_0$ is false
- In our example the $T$ statistic was 0.8
    - What's the probability of getting a $T$ statistic as large as 0.8?
    

```r
pt(0.8, 15, lower.tail=F)
```

```
## [1] 0.218099
```

- Therefore, the probability of seeing evidence as extreme or more extreme than that actually obtained under $H_0$ is 0.2181

## The attained significance level

- Our test statistic was 2 for $H_0 : \mu_0 = 30$ versus $H_\alpha : \mu > 30$
- Notice that we rejected the one sided test when $\alpha = 0.05$, would we reject if $\alpha = 0.01$? How about $\alpha = 0.001$?
- Therefore, the P-value can also be thought of as the smallest value for alpha that you still reject the null hypothesis is called the _attained significance level_
- By communicating it, you allow the reader to test against whatever $\alpha$ level they see fit
- This is equivalent, but philosophically a little different from, the _P-value_

## Notes

- By reporting a P-value the reader can perform the hypothesis test at whatever $\alpha$ level he or she chooses
- If the P-value is less than $\alpha$ you reject the null hypothesis
- For two sided hypothesis test, double the smaller of the two one sided hypothesis test P-values

## Revisiting an earlier example

- Suppose a friend has 8 children, 7 of which are girls and none are twins
- If each gender has an independent 50% probability for each birth, what's the probability of getting 7 or more girls out of 8 births?


```r
choose(8, 7) * 0.5^8 + choose(8, 8) * 0.5^8
```

```
## [1] 0.03515625
```

```r
pbinom(6, size=8, prob=0.5, lower.tail=F)
```

```
## [1] 0.03515625
```

- To get the two sided P-value of a binomial test, you calculate the probability of the lower & upper tails, take the smaller of the two values, and double it


```r
p1 <- pbinom(6, size=8, prob=0.5, lower.tail=F)
p2 <- pbinom(6, size=8, prob=0.5)
if (p1 < p2) {
    p1 * 2
} else {
    p2 * 2
}
```

```
## [1] 0.0703125
```

## Poisson example

- Suppose that a hospital has an infection rate of 10 infections per 100 person/days at risk (rate of 0.1) during the last monitoring period
- Assume that an infection rate of 0.05 is an important benchmark
- Given themodel, could the observed rate being larger than 0.05 be attributed to chance?
- Under $H_0 : \lambda = 0.05 \mbox{ -or- } \lambda_0 \times 100 = 5$
- Consider $H_\alpha : \lambda > 0.05 \mbox{ -or- } \lambda \times 100 > 5$


```r
ppois(9, 5, lower.tail=F)
```

```
## [1] 0.03182806
```

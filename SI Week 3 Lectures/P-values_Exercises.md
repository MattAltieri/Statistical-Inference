# P-values Exercises

## Question 1

P-values are probabilities that are calculated assuming which hypothesis is true?

- The alternative
- The null **<-- ANSWER**

## Question 2

You get a P-value of 0.06. Would you reject for a type I error rate of 0.05?

- Yes you would reject the null
- No you would not reject the null **<-- ANSWER**
- It depends on information not given

## Question 3

The proposed procedure for getting a two sided P-value for the exact binomial test considered here is what?

- Multiplying the one sided P-value by one half
- Doubling the larger of the two one sided P-values
- Doubling the smaller of the two one sided P-values **<-- ANSWER**
- No procedure exists

## Question 4

Consider again the `mtcars` dataset. Use a two group t-test to test the hypothesis that the 4 and 6 cyl cars have the same mpg. Use a two sided test with unequal variances. Give a P-value


```r
library(datasets)
data(mtcars)
mpg46 <- subset(mtcars, cyl %in% c(4,6))
t.test(mpg ~ cyl, data=mpg46)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  mpg by cyl
## t = 4.7191, df = 12.956, p-value = 0.0004048
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##   3.751376 10.090182
## sample estimates:
## mean in group 4 mean in group 6 
##        26.66364        19.74286
```

**ANSWER:** 0.0004048

## Question 5

You believe the coin that you're flipping is biased towards heads. You get 55 heads out of 100 flips. Give an exact P-value for the hypothesis that the coin is fair


```r
pbinom(54, size=100, prob=0.5, lower.tail=F)
```

```
## [1] 0.1841008
```

**ANSWER:** 0.1841008

## Question 6

A web site was monitored for a year and it received 520 hits per day. In the first 30 days in the next year, the site received 15,800 hits. Assuming that web hits are Poisson. Give an exact one sided P-value to the hypothesis that web hits are up this year over last.


```r
ppois(15799, lambda=520 * 30, lower.tail=F)
```

```
## [1] 0.05533114
```

**ANSWER:** 0.05533114

Do you reject?

**ANSWER:** No

## Question 7

Suppose that in an AB test, one advertising sheme led to an average of 10 purchases per day for a sample of 100 days, while the other led to 11 purchases per day, also for a sample of 100 days. Assuming a common standard deviation of 4 purchases per day. Assuming that the groups are independent and that the days are iid, perform a Z test for equivalence. Give a P-value for that test


```r
mu1 <- 10
n1 <- 100
mu2 <- 11
n2 <- 100
mudiff <- mu1 - mu2
sp <- 4
se <- 4 * sqrt(1/n1 + 1/n2)
ts <- mudiff / se
2 * pnorm(ts)
```

```
## [1] 0.07709987
```

**ANSWER:** 0.07709987

## Question 8

Consider the `mtcars` dataset

- Give the p-value for a t-test comparing mpg for 6 and 8 cylinder cars assuming equal variance, as a proportion to 3 decimal places


```r
library(datasets)
data(mtcars)
mpg6 <- mtcars[mtcars$cyl == 6,"mpg"]
mpg8 <- mtcars[mtcars$cyl == 8,"mpg"]
t.test(mpg6, mpg8, paired=F, var.equal=T, data=mpg68)
```

```
## 
## 	Two Sample t-test
## 
## data:  mpg6 and mpg8
## t = 4.419, df = 19, p-value = 0.0002947
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  2.443809 6.841905
## sample estimates:
## mean of x mean of y 
##  19.74286  15.10000
```

**ANSWER:** 0

- Give the associated p-value for a z test


```r
round(2 * pnorm(-4.419), 3)
```

```
## [1] 0
```

```r
# or
mu6 <- mean(mpg6)
mu8 <- mean(mpg8)
sd6 <- sd(mpg6)
sd8 <- sd(mpg8)
n6 <- length(mpg6)
n8 <- length(mpg8)
sp <- sqrt(((n6 - 1)*sd6^2 + (n8 - 1)*sd8^2)/(n6 + n8 - 2))
round(2 * pnorm(-((mu6 - mu8) / (sp * sqrt(1/n6 + 1/n8)))), 3)
```

```
## [1] 0
```

**ANSWER:** 0

- Give the common standard deviation estimated to mpg across cylinders to 3 decimal places


```r
round(sp, 3)
```

```
## [1] 2.27
```

**ANSWER:** 3

- Would the t test reject at the two sided 0.05 level?

**ANSWER:** Yes

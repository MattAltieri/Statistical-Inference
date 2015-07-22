# Hypothesis Testing Exercises

## Question 1

Which hypothesis is typically assumed to be true in hypothesis testing?

- The null **<-- ANSWER**
- The alternative

## Question 2

The type I error rate controls what?

**ANSWER:** The % of incorrect rejections of the null

## Question 3

Load the data set `mtcars` in the `datasets` R package. Assume that the data set `mtcars` is a random sample. Compute the mean MPG, $\bar x$, of this sample. You want to test whether the true MPG is $\mu_0$ or smaller using a one sided 5% level test ($H_0 : \mu = \mu_0$ versus $H_\alpha : \mu < \mu_0$). Using that data set and a Z test: Based on the mean MPG of the sample $\bar x$, and by using a Z test: what is the smallest value of $\mu_0$ that you would reject for (to two decimal places)

$$
H_0 : \mu = \mu_0 \\
H_\alpha : \mu < \mu_0 \\ \\
\begin{eqnarray}
\frac{\bar X - \mu_0}{\frac{s}{\sqrt n}} & = & Z_\alpha \\
\bar X - \mu_0 & = & Z_\alpha\frac{s}{\sqrt n} \\
\mu_0
& = & \bar X - Z_\alpha\frac{s}{\sqrt n} \\
& = & \bar X + 1.645\frac{s}{\sqrt n}
\end{eqnarray}
$$


```r
library(datasets)
data(mtcars)
mu <- mean(mtcars$mpg)
s <- sd(mtcars$mpg)
z <- qnorm(.05)
mu - z * s / sqrt(nrow(mtcars))
```

```
## [1] 21.84309
```

## Question 4

Consider again the `mtcars` dataset. Use a two group t-test to test the hypothesis that the 4 and 6 cyl cars have the same mpg. Use a two sided test with unequal variances. Do you reject?


```r
library(datasets)
data(mtcars)
mpg46 <- subset(mtcars, cyl %in% c(4,6))
t.test(mpg ~ cyl, data = mpg46)
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

**ANSWER:** Yes

## Question 5

A sample of 100 men yielded and average PSA level of 3.0 with a sd of 1.1. What are the complete set of values that a 5% two sided Z test of $H_0 : \mu = \mu_0$ would fail to reject the null hypothesis for?


```r
mu <- 3
s <- 1.1
n <- 100
mu + c(-1,1) * qnorm(.975) * 1.1 / sqrt(100)
```

```
## [1] 2.784404 3.215596
```

## Question 6

You believe the coin that you're flipping is biased towards heads. You get 55 heads out of 100 flips. Do you reject at the 5% level that the coin is fair?

$$
H_0 : p = .5 \\
H_\alpha : p > .5
$$


```r
pbinom(54, size=100, prob=.5, lower.tail=F)
```

```
## [1] 0.1841008
```

**ANSWER:** No

## Question 7

Suppose that in an AB test, one advertising scheme led to an average of 10 purchases per day for a sample of 100 days, while the other led to 11 purchases per day, also for a sample of 100 days. Assuming a common standard deviation of 4 purchases per day. Assuming that the groups are independent and that the days are iid, perform a Z test of equivalence. Do you reject at the % level?


```r
mu1 <- 10
mu2 <- 11
md <- mu1 - mu2
sp <- 4
se <- sp * sqrt(1/100 + 1/100)
z <- md / se
2 * pnorm(z)
```

```
## [1] 0.07709987
```

**ANSWER:** No

## Question 8

A confidence interval for the mean contains:

- All of the values of the hypothesized mean for which we would fail to reject with $\alpha = 1 - Conf.Level$ **<-- ANSWER**
- All of the values of the hypothesized mean for which we would fail to reject with $2\alpha = 1 - Conf.Level$
- All of the values of the hypothesized mean for which we would reject with $\alpha = 1 - Conf.Level$
- All of the values of the hypothesized mean for which we would reject with $2\alpha = 1 - Conf.Level$

## Question 9

In a court of law, all things being equal, if via policy you require a lower standard of evidence to convict people then

- Less guilty people will be convicted
- More innocent people will be convicted **<-- ANSWER**
- More innocent people will not be convicted

# SI Week 4 Homework

## Question 1

Load the dataset `mtcars` in the `datasets` R package. Assume that the dataset `mtcars` is a random sample. Compute the mean MPG, $\bar x$, of this sample

You want to test whether the true MPG is $\mu_0$ or smaller using a one-sided 5% level test. ($H_0 : \mu = \mu_0$ versus $H_\alpha : \mu < \mu_0$). Using that dataset and a Z test

1. Based on the mean MPG of the sample $\bar x$, and by using a Z test: what is the smallest value $\mu_0$ that you would reject for (to two decimal places)

$$
H_0 : \mu = \mu_0 \\
H_\alpha : \mu < \mu_0 \\
Z_\alpha = -1.645 \\
\frac{\bar X-\mu_0}{\frac{s}{\sqrt n}} \le Z_\alpha \\
\mbox{Need to turn to an equality to solve for} \\
\mbox{the smallest value for which we would reject} \\
\bar X-\mu_0=Z_\alpha \times \frac{s}{\sqrt n} \\
\begin{eqnarray*}
\mu_0
& = & \bar X - Z_\alpha \frac{s}{\sqrt n} \\
& = & \bar X + 1.645 \frac{s}{\sqrt n}
\end{eqnarray*}
$$


```r
library(datasets)
data(mtcars)
mt <- mtcars
mu <- mean(mt$mpg)
s <- sd(mt$mpg)
n <- nrow(mt)
se <- s / sqrt(n)
z <- qnorm(.05)
round(mu - z * se, 2)
```

```
## [1] 21.84
```

**ANSWER:** 21.84

## Question 2

Consider again the `mtcars` dataset. Use a two-group t-test to test the hypothesis that the 4 and 6 cyl cars have the same mpg. Use a two-sided test with unequal variances


```r
mt4 <- mt[which(mt$cyl == 4),"mpg"]
mt6 <- mt[which(mt$cyl == 6), "mpg"]
t.test(mt4, mt6)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  mt4 and mt6
## t = 4.7191, df = 12.956, p-value = 0.0004048
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##   3.751376 10.090182
## sample estimates:
## mean of x mean of y 
##  26.66364  19.74286
```

1. Do you reject at the 5% level

**ANSWER:** Yes

2. What is the P-value to 4 decimal places expressed as a proportion:?

**ANSWER:** 0.0004

## Question 3

A sample of 100 men yielded an average PSA level of 3.0 with a sd of 1.1. What are the complete set of values that a 5% two-sided Z test of $H_0 : \mu = \mu_0$ would fail to reject the null hypothesis for?


```r
n <- 100
mu <- 3
s <- 1.1
se <- s/sqrt(n)
round(mu + c(-1,1) * qnorm(.975) * se, 2)
```

```
## [1] 2.78 3.22
```

**ANSWER:** 2.78 - 3.22

## Question 4

You believe the coin that you're flipping is biased towards heads. You get 55 heads out of 100 flips

1. What's the exact relevant $p$-value to 4 decimal places?


```r
round(pbinom(54, size=100, prob=0.5, lower.tail=F), 4)
```

```
## [1] 0.1841
```

**ANSWER:** .1356

2. Would you reject a one-sided hypothesis at $\alpha = .05$?

**ANSWER:** No

## Question 5

A website was monitored for a year and it received 520 hits per day. In the first 30 days in the next year, the site received 15,800 hits. Assuming that web hits are Poisson

1. Give an exact one-sided $p$-value to the hypothesis that web hits are up this year over last to four significant digits.


```r
round(ppois(15800, 520*30, lower.tail=F), 4)
```

```
## [1] 0.0544
```

**ANSWER:** .0544

2. Does the one-sided test reject?

**ANSWER:** No

## Question 6

Suppose that in an AB test, one advertising scheme led to an average of 10 purchases per day for a sample of 100 days, while the other led to 11 purchases per day, also for a sample of 100 days. Assuming a common standard deviation of 4 purchases per day. Assuming that the groups are independent and that the days are iid, perform a Z test of equivalence


```r
mua <- 10
na <- 100
mub <- 11
nb <- 100
s <- 4
se <- s * sqrt(1/na + 1/nb)
round(2*pnorm((mua - mub)/se), 3)
```

```
## [1] 0.077
```

1. What is the $p$-value reported to 3 digits expressed as a proportion?

**ANSWER:** .077

2. Do you reject the test?

**ANSWER:** No

## Question 7

A confidence interval for the mean contains:

- All of the values of the hypothesized mean for which we would fail to reject with $\alpha =1-Conf.Level$ **<-- ANSWER**
- All of the values of the hypothesized mean for which we would fail to reject with $2\alpha =1-Conf.Level$
- All of the values of the hypothesized mean for which we would reject with $\alpha =1-Conf.Level$
- All of the values of the hypothesized mean for which we would reject with $2\alpha =1-Conf.Level$

## Question 8

Consider two problems previous. Assuming that 10 purchases per day is a benchmark null value, that days are iid and that the standard deviation is 4 purchases per day. Suppose that you plan on sampling 100 days. What would be the power for a one-sided 5% Z mean test that purchases per day have increased under the alternative of $\mu = 11$ purchases per day?

Round to 3 deimal places


```r
alpha <- .05
z <- qnorm(1 - alpha)
n <- 100
mu0 <- 10
mua <- 11
s <- 4
se <- 4/sqrt(n)
round(pnorm(mu0 + z * se, mean=mua, sd=se, lower.tail=F), 3)
```

```
## [1] 0.804
```

**ANSWER:** 0.804

## Question 9

Researchers would like to conduct a study of healthy adults to detect a four year mean brain volume loss of .01 mm$^3$. Assume that the standard deviation of four year loss in this population is .04 mm$^3$.

1. What is necessary sample size for the study for a 5% one-sided test versus a null hypothesis of no volume loss to achieve 80% power?

Round up.

$$
H_0 : \mu = 0 \\
H_\alpha : \mu > 0 \\
s = 0.04 \\
power = 80\% \\
Z_{1-\alpha} = 1.645 \\
\mu_0 = 0 \\
\mu_\alpha = 0.01 \\ \\
\mbox{Under } H_0 \\
\begin{eqnarray*}
\bar X
& \sim & N(\mu_0, \frac{s}{\sqrt n}) \\
& \sim & N(0, \frac{0.04}{\sqrt n}) \\
\end{eqnarray*}
$$

$$
\mbox{Under } H_\alpha \\
\begin{eqnarray*}
\bar X
& \sim & N(\mu_\alpha, \frac{s}{\sqrt n}) \\
& \sim & N(0.01, \frac{0.04}{\sqrt n})
\end{eqnarray*}
$$

$$
\mbox{Reject if} \\
\begin{eqnarray*}
\bar X
& > & \mu_0 + Z_{1-\alpha} * \frac{s}{\sqrt n} \\
& > & 0 + 1.645 * \frac{0.04}{\sqrt n} \\
& > & 0.0658 * \frac{1}{\sqrt n}
\end{eqnarray*}
$$


```r
for (i in 1:1000) {
    n <- i
    pwr <- pnorm(0.0658 / sqrt(n), mean=0.01, sd=0.04/sqrt(n), lower.tail=F)
    if (pwr >= .8) break
}
n
```

```
## [1] 99
```

**ANSWER:** 99

## Question 10

In a court of law, all things being equal, if via policy you require a lower standard of evidence to convict people then

- Less guilty people will be convicted
- More innocent people will be convicted **<-- ANSWER**
- More innocent people will be acquitted

## Question 11

Consider the `mtcars` datasete

1. Give the $p$-value for a $t$-test comparing MPG for 6 and 8 cylinder cars assuming equal variance, as a proportion to 3 decimal places


```r
library(datasets)
data(mtcars)
mt <- mtcars
mpg6 <- mt[which(mt$cyl == 6),"mpg"]
mpg8 <- mt[which(mt$cyl == 8),"mpg"]
tt <- t.test(mpg6, mpg8, var.equal=T)
round(tt$p.value, 3)
```

```
## [1] 0
```

**ANSWER:** 0.000

2. Give the associated $p$-value for a $Z$-test


```r
# You can cheat this by taking t from the t test and using it as the test statistic in our z test
round(2 * pnorm(tt$statistic, lower.tail=F), 3)
```

```
## t 
## 0
```

```r
# Or to calculate it by hand
mn6 <- mean(mpg6)
mn8 <- mean(mpg8)
s6 <- sd(mpg6)
s8 <- sd(mpg8)
n6 <- length(mpg6)
n8 <- length(mpg8)
sp <- sqrt(((n6 - 1) * s6^2 + (n8 - 1) * s8^2) / (n6 + n8 - 2))
ts <- (mn6 - mn8) / (sp * sqrt(1/n6 + 1/n8))
round(2 * pnorm(ts, lower.tail=F), 3)
```

```
## [1] 0
```

**ANSWER:** 0.000

3. Give the common standard deviation estimate for MPG across cylinders to 3 decimal places


```r
round(sp, 3)
```

```
## [1] 2.27
```

**ANSWER:** 1.507

4. Would the $t$-test reject at the two-sided 0.05 level?


```r
tt
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

**ANSWER:** Yes

## Question 12

The Bonferonni correction controls this

- False discovery rate
- The family-wise error rate **<-- ANSWER**
- The rate of true rejections
- The number of true rejections

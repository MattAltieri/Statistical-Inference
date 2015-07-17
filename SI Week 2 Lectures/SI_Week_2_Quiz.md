# SI Week 2 Quiz

## Question 1

What is the variance of the distribution of the average an IID draw of $n$ observations from a population with mean $\mu$ and variance $\sigma^2$?

- $\sigma^2$
- $\frac{\sigma^2}{n}$ **ANSWER**
- $\sigma / n$
- $2\sigma / \sqrt n$

## Question 2

Suppose that diastolic blood pressures (DBPs) for men aged 25-44 are normally distributed with a mean of 80 (mm Hg) and a standard deviation of 10. About what is the probability that a random 35-44 year old has a DBP less than 70?

- 16% **ANSWER**
- 8%
- 22%
- 32%


```r
mu <- 80
sd <- 10
paste0(round(pnorm(70, mean=mu, sd=sd) * 100), '%')
```

```
## [1] "16%"
```

## Question 3

Brain volume for adult women is normally distributed with a mean of about 1,100 cc for women with a standard deviation of 75 cc. What brain volume represents the 95th percentile?

- approximately 1247
- approximately 1175
- approximately 1223 **ANSWER**
- approximately 977


```r
mu <- 1100
sd <- 75
round(qnorm(.95, mean=mu, sd=75))
```

```
## [1] 1223
```

## Question 4

Refer to the previous question. Brain volume for adult women is about 1,100 cc for women with a standard deviation of 75 cc. Consider the sample mean of 100 random adult women from this population. What is the 95th percentile of the distribution of that sample mean?

- approximately 1110 cc
- approximately 1112 cc **ANSWER**
- approximately 1088 cc
- approximately 1115 cc


```r
mu <- 1100
sd <- 75
n <- 100
se <- sd / sqrt(n)
round(qnorm(.95, mean=mu, sd=se))
```

```
## [1] 1112
```

## Question 5

You flip a fair coin 5 times, about what's the probability of getting  or 5 heads?

- 3%
- 6%
- 19% **ANSWER**
- 12%


```r
round(pbinom(3, siz =5, prob=.5, lower.tail=F) * 100)
```

```
## [1] 19
```

## Question 6

The respiratory disturbance index (RDI), a measure of sleep disturbances, for a specific population has a mean of 15 (sleep events per hour) and a standard deviation of 10. They are not normally distributed. Give your best estimate of the probability that a sample mean RDI of 100 people is between 14 & 16 events per hour.

- 47.5%
- 95%
- 34%
- 68% **ANSWER**


```r
mu <- 15
sd <- 10
n <- 100
se <- sd / sqrt(n)
se
```

```
## [1] 1
```

Standard error of the mean (standard dev of the average of means) is one, so 14 & 16 are 1 sd away from the mean, 15. So the answer is 68%.

## Question 7

Consider a standard uniform density. The mean for this density is .5 and the variance is 1/12. You sample 1,000 observations from this distribution and take the sample mean, what value would you expect it to be near?

- 0.10
- 0.75
- 0.5 **ANSWER**
- 0.25

## Question 8

The number of people showing up at a bus stop is assumed to be Poisson with a mean of 5 people per hour. You watch the bus stop for 3 hours. About what's the probability of viewing 10 or fewer people?

- 0.03
- 0.06
- 0.12 **ANSWER**
- 0.08


```r
round(ppois(10, lambda=3*5), 2)
```

```
## [1] 0.12
```

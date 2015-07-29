# Power Exercises

## Question 1

Power is a probability calculation assuming which is true?

- The null hypothesis
- The alternative hypothesis **<-- ANSWER**
- Both the null and alternative

## Question 2

As your sample size gets bigger, all else equal, what do you think would happen to power?

- It would get larger **<-- ANSWER**
- It would get smaller
- It would stay the same
- It cannot be determined from the information given

## Question 3

What happens to power as $\mu_\alpha$ gets further away from $\mu_0$

- Power decreases
- Power increases **<-- ANSWER**
- Power stays the same
- Power oscillates

## Question 4

In the context of calculaing power, the effect size is?

- The null mean divided by the standard deviation
- The alternative mean divided by the standard deviation
- The difference between the null and alternative means divided by the standard deviation **<-- ANSWER**
- The standard error divided by the null mean

## Question 5

Recall this problem: "Suppose that in an AB test, one advertising scheme led to an average of 10 purchases per day for a sample of 100 days, while the other led to 11 purchases per day, also for a sample of 100 days. Assuming a common standard deviation of 4 purchases per day." Assuming that 10 purchases per day is a benchmark null value, that days are iid and that the standard deviation is 4 purchases per day. Suppose that you plan on sampling 100 days. What would be the power of a one-sided 5% Z mean test that purchases per day have increased under the alternative of $\mu$=11 purchases per day


```r
alpha <- 0.05
z <- qnorm(1 - alpha)
mu0 <- 10
mua <- 11
sd <- 4
n <- 100
se <- sd/sqrt(n)
pnorm(mu0 + z * se, mean=mua, sd=se, lower.tail=F)
```

```
## [1] 0.8037649
```

**ANSWER:** 0.804

## Question 6

Researchers would like to conduct a study of healthy adults to detect a four year mean brain volume loss of .01 mm$^3$. Assume that the standard deviation of four year volume loss in this population is 0.04 mm$^3$. What is the necessary sample size for the study for a 5% one-sided test versus a null hypothesis of no volume loss to achieve 80% power?


```r
power.t.test(power=0.8, delta=.01, sd=.04, type="one.sample", alt="one.sided")$n
```

```
## [1] 100.2877
```

**ANSWER:** 101

# T Confidence Intervals - Exercises

## Question 1

For iid Gaussian data, the statistic $\frac{\bar X - \mu}{s / \sqrt n}$ must follow a:

- Z distribution
- t distribution **<-- ANSWER**

## Question 2

Paired differences T confidence intervals are useful when:

- Pairs of observations are linked, such as when there is subject level matching or in a study with baseline and follow-up measurements on all participants **<-- ANSWER**
- When there was randomization of a treatment between two independent groups

## Question 3

The assumption that the variances are equal for the independent group T interval means that:

- The sample variances have to be nearly identical
- The population variances are identical, but the sample variances may be different **<-- ANSWER**

## Question 4

Load the data set `mtcars` in the `datasets` R package. Calculate a 95% confidence interval to the nearest MPG for the variable `mpg`


```r
library(datasets)
data(mtcars)
t.test(mtcars$mpg)$conf
```

```
## [1] 17.91768 22.26357
## attr(,"conf.level")
## [1] 0.95
```

## Question 5

Suppose that standard deviation of 9 paired differences is 1. What value would the average difference have to be so that the lower end point of a 95% student's t confidence interval touches 0

$$
n = 9 \\
sd = 1 \\ \\
\begin{eqnarray*}
\bar Y_d - t_{.975} \times \frac{sd}{\sqrt n} & = & 0 \\
\bar Y_d - t_{.975} \times \frac{1}{3} & = & 0 \\
\bar Y_d & = & t_{.975} \times \frac{1}{3} \\
\bar Y_d & = & \frac{t_{.975}}{3}
\end{eqnarray*}
$$


```r
qt(.975, 8) / 3
```

```
## [1] 0.768668
```

## Question 6

An independent group Student's T interval is used instead of a paired T interval when:

- The observations are paired between the groups
- The observations between the groups are naturally assumed to be statistically independent **<-- ANSWER**
- As long as you do it correctly, either is fine
- More details are needed to answer this question

## Question 7

Consider the `mtcars` dataset. Construct a 95% T interval for MPG comparing 4 to 6 cylinder cars (subtracting in the order of 4 - 6). Assume a constant variance


```r
library(datasets)
data(mtcars)
sub_mtcars <- subset(mtcars, cyl %in% c(4, 6))
t.test(mpg ~ cyl, paired=F, var.equal=T, data=sub_mtcars)$conf
```

```
## [1]  3.154286 10.687272
## attr(,"conf.level")
## [1] 0.95
```

## Question 8

If someone put a gun to your head and said "Your confidence interval must contain what it's estimating or I'll pull the trigger", what would be the smart thing to do?

- Make your interval as wide as possible **<-- Statistical ANSWER**
- Make your interval as small as possible
- Call the authorities **<-- Real World ANSWER**

## Question 9

Refer back to comparing MPG for 4 versus 6 cylinders. What do you conclude

- The interval is above zero, suggesting 6 is better than 4 in terms of MPG
- The interval is above zero, suggesting 4 is better than 6 in terms of MPG **<-- ANSWER**
- The interval does not tell you anything about the hypothesis test; you have to do the test
- The interval contains 0 suggesting no difference

## Question 10

Suppose that 18 obese subjects were randomized, 9 each, to a new diet pill and a placebo. Subjects body mass indices (BMIs) were measured at a baseline and again after having received the treatment or placebo for four weeks. The average difference from follow-up to the baseline (followup - baseline) was 3 kg/m2 for the treated group and 1 kg/m2 for the placebo group. The corresponding standard deviations of the differences was 1.5 kg/m2 for the treatment group and 1.8 kg/m2 for the placebo group. The study aims to answer whether the change in BMI over the four week period appears to differ between the treated and placebo groups. What is the pooled variance estimate?

$$
X = \mbox{Test group} \\
Y = \mbox{Control group} \\
\bar X = 3 \\
S_x = 1.5 \\
n_x = 9 \\
\bar Y = 1 \\
S_y = 1.8 \\
n_y = 9 \\ \\
\begin{eqnarray*}
S_p^2
& = & \frac{(n_x - 1) \times S_x^2 + (n_y - 1) \times S_y^2}{n_x + n_y - 2} \\ \\
& = & \frac{(9 - 1) \times 1.5^2 + (9 - 1) \times 1.8^2}{9 + 9 - 2} \\ \\
& = & \frac{8 \times 2.25 + 8 \times 3.24}{16} \\ \\
& = & \frac{18 + 25.92}{16} \\ \\
& = & \frac{43.92}{16} \\ \\
& = & 2.745
\end{eqnarray*}
$$


```r
mu_x <- 3
sd_x <- 1.5
n_x <- 9
mu_y <- 1
sd_y <- 1.8
n_y <- 9
((n_x - 1) * sd_x^2 + (n_y - 1) * sd_y^2)/(n_x + n_y - 2)
```

```
## [1] 2.745
```

```r
# or this, since the sample sizes are the same

(sd_x^2 + sd_y^2)/2
```

```
## [1] 2.745
```

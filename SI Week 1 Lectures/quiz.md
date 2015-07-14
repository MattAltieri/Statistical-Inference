# SI Week 1 Quiz

## Question 1

Consider influenza epidemics for two parent heterosexual families. Suppose that the probability is 17% that at least one of the parents has contracted the disease. The probability that the father has contracted influenza is 12% while the probability that both the mother and the father have contracted the disease is 6%. What is the probability that the mother has contracted influenza?

- 6%
- 17%
- 11%
- 5%

$$
F = Father \\
M = Mother \\
P(M) = ? \\
P(F) = 0.12 \\
P(M \cup F) = 0.17 \\
P(M \cap F) = 0.06
$$

$$
\begin{eqnarray*}
P(M \cup F) & = & P(M) + P(F) - P(M \cap F) \\
0.17 & = & P(M) + 0.12 - 0.06 \\
-P(M) & = & 0.12 - 0.06 - 0.17 \\
P(M) & = & 0.17 + 0.06 - 0.12 \\
P(M) & = & 0.11
\end{eqnarray*}
$$

## Question 2

A random variable, $X$, is uniform, a box from 0 to 1 of height 1. (So that its density is $f(x) = 1$ for $0 \leq x \leq 1$). What is its 75th percentile?

Intuitively it should be 0.75


```r
qunif(0.75, 0, 1)
```

```
## [1] 0.75
```

## Question 3

You are playing a game with a friend where you flip a coin and if it comes up heads you give her $X$ dollars and if it comes up tailes she gives you $Y$ dollars. The probability that the coin is heads is $p$ (some number between 0 and 1). What ahs to be true about X and Y to make it so that both of your expected total earnings is 0. The game would then be called "fair".

- $\frac{p}{1-p} = \frac{Y}{X}$
- $\frac{p}{1-p} = \frac{X}{Y}$
- $X = Y$
- $p = \frac{X}{Y}$

$$
\begin{eqnarray*}
0 & = & Y \times (1 - p) - X \times p \\
X \times p & = & Y \times (1 - p) \\
\frac{1}{1 - p} \times X \times p & = & Y \\
\frac{1}{1 - p} \times p & = & \frac{Y}{X} \\
\frac{p}{1 - p} & = & \frac{Y}{X}
\end{eqnarray*}
$$

## Question 4

A density that looks like a normal density (but may or may not be exactly normal) is exactly symmetric about zero. What is the median?

The median must be zero

## Question 5

Consider the following PMF shown below in R


```r
x <- 1:4
p <- x/sum(x)
temp <- rbind(x, p)
rownames(temp) <- c("X", "Prob")
temp
```

```
##      [,1] [,2] [,3] [,4]
## X     1.0  2.0  3.0  4.0
## Prob  0.1  0.2  0.3  0.4
```

What is the mean?

- 1
- 2
- 4
- 3


```r
sum(x * p)
```

```
## [1] 3
```

## Question 6

A website (http://www.medicine.ox.ac.uk/bandolier/band64/b64-7.html) for home pregnancy tests cites the following: "When the subjects using the test were women who collected and tested their own samples, the overall sensitivity was 75%. Specificity was also low, in th erange 52% to 75%." Assume the lower value for the specificity. Suppose a subject has a positive test and that 30% of the women taking pregnancy tests are actually pregnant. What number is closest to the probability of pregnancy given a positive test?

- 30%
- 10%
- 40%
- 20%

$$
P(+ ~|~ B) = 0.75 \\
P(- ~|~ B^C) = 0.52 \\
P(B) = 0.30
$$

$$
\begin{eqnarray*}
P(B ~|~ +) & = & \frac{P(+ ~|~ B)P(B)}{P(+ ~|~ B)P(B) +  P(+ ~|~ B^C)P(B^C)} \\
& = & \frac{P(+ ~|~ B)P(B)}{P(+ ~|~ B)P(B) + (1 - P(- ~|~ B))(1 - P(B))} \\
& = & \frac{0.75 \times 0.30}{0.75 \times 0.30 + (1 - 0.52) \times (1 - 0.30)} \\
\end{eqnarray*}
$$


```r
sensitivity <- 0.75
specificity <- 0.52
prevalence <- 0.30
specificity_comp  <- 1 - specificity
prevalence_comp <- 1 - prevalence
(sensitivity * prevalence)/((sensitivity * prevalence) + (specificity_comp * prevalence_comp))
```

```
## [1] 0.4010695
```
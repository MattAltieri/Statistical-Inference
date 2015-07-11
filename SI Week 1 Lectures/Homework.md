# Statistical Inference Homework Week 1

## HW 1

Consider influenza epidemics for two parent heterosexual families. Suppose that the probability is 15% that at least one of the parents has contracted the disease. The probability that the father has contracted influenza is 10% while that the mother contracted the disease is 9%. What is the probability that both contract influenza expressed as a whole number percentage?

- 15%
- 10%
- 9%
- 4%

$$
\begin{eqnarray*}
P(F) = 0.10 \\
P(M) = 0.09 \\
P(F \cup M) = 0.15 \\
P(F \cap M) = ? \\ \\
P(F \cup M) = P(F) + P(M) + P(F \cap M) \\
0.15 = 0.10 + 0.09 - P(F \cap M) \\
0.15 = 0.19 - P(F \cap M) \\
0.15 - 0.19 = -P(F \cap M) \\
-0.04 = -P(F \cap M) \\
0.04 = P(F \cap M)
\end{eqnarray*}
$$

## HW 2

A random variable, $X$, is uniform, a box from 0 to 1 of height 1. (So that its density is $f(x) = 1 \mbox{ for } 0 \leq x \leq 1$.) What is its median expressed to two decimal places?

- 1.00
- 0.75
- 0.50
- 0.25

$$
\begin{eqnarray*}
F(x) & = & \frac{1}{2}b \times h \\
& = & \frac{1}{2}1 \times 1 \\
& = & \frac{1}{2}1 \\
& = & 0.50
\end{eqnarray*}
$$

## HW 3

You are playing a game with a friend where you flip a coin and if it comes up heads you give her $X$ dollars and if it comes up tails she gives you $Y$ dollars. The odds that the coin is heads is $d$. What is your expected earnings?

- $-X \frac{d}{1 + d} + Y \frac{1}{1 + d}$
- $X \frac{d}{1 + d} + Y \frac{1}{1 + d}$
- $X \frac{d}{1 + d} - Y \frac{1}{1 + d}$
- $-X \frac{d}{1 + d} - Y \frac{1}{1 + d}$

$$
\begin{eqnarray*}
d = \frac{p}{1-p} \\
d(1-p) = p \\
d - dp = p \\
d - dp + p = 0 \\
d - p(1 + d) = 0 \\
-p(1 + d) = -d \\
p(1 + d) = d \\
p = \frac{d}{1 + d} \\ \\
\therefore 1 - p = \frac{1}{1 + d}
\end{eqnarray*}
$$

$$x$$ |$$p$$
:----:|:-----------------:
$$-X$$|$$\frac{d}{1 + d}$$
$$Y$$ |$$\frac{1}{1 + d}$$

$$
F(x) = -X \times \frac{d}{1 + d} + Y \times \frac{1}{1 + d}
$$

## HW 4

A random variable takes the value of -4 with probability .2 and 1 with probability .8. What is the variance of this random variable?

- 0
- 4
- 8
- 16

$$
Var(X) = E[X^2] - E[X]^2
$$

$$x^2$$|$$x$$|$$p$$
:-----:|:---:|:---:
16     |-4   |.2
1      |1    |.8


```r
x <- c(-4, 1)
p <- c(.2, .8)
x_sqr <- x^2
sum(x_sqr * p) - sum(x * p)^2
```

```
## [1] 4
```

## HW 5

If $\bar X$ and $\bar Y$ are comprised of $n$ iid random variables arising from distributions having means $\mu_x$ and $\mu_y$ respectively and common variance $\sigma^2$, what is the variance $\bar X - \bar Y$?

- 0
- $2 \sigma^2 / n$
- $\mu_x - \mu_y$
- $2 \sigma^2$

$$
\begin{eqnarray*}
Var(\bar X - \bar Y) & = & Var(\bar X) + Var(\bar Y) \\
& = & \sigma^2 / n + \sigma^2 / n \\
& = & \frac{2 \sigma^2}{n}
\end{eqnarray*}
$$

## HW 6

Let $X$ be a random variable having standard deviation $\sigma$. What can be said about $X / \sigma$?

- Nothing
- It must have variance 1
- It must have mean 0
- It must have variance 0

$$
\begin{eqnarray*}
Sd(X) = \sigma \\
Var(X) = \sigma^2 \\ \\
Var(\frac{X}{\sigma}) & = & \frac{1}{\sigma^2}Var(X) \\
& = & \frac{1}{\sigma^2} \times \sigma^2 \\
& = & 1
\end{eqnarray*}
$$

## HW 7

If a continuous density that never touches the horizontal axis is symmetric about zero, can we say that its associated median is zero?

- Yes
- No
- It can not be determined given the information provided

The answer is yes intuitively

## HW 8

Consider the following pmf given in R


```r
p <- (1:4)/10
x <- 2:5
```

What is the variance expressed to 1 decimal place?

- 1.0
- 4.0
- 6.0
- 17.0


```r
x_sqr <- x^2
sum(x_sqr * p) - sum(x * p)^2
```

```
## [1] 1
```

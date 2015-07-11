# Scratch

If you roll ten standard dice, take their average, then repeat this process over and over and construct a histogram, what would be its variance expressed to 3 decimal places


```r
n <- 10
x <- 1:6
p <- rep(1/6, times = 6)
mu <- sum(x * p)
mu2 <- sum(x^2 * p)
sigma2 <- mu2 - mu^2
s2 <- sigma2 / n
sigma2
```

```
## [1] 2.916667
```

```r
s2
```

```
## [1] 0.2916667
```

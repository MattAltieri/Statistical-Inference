# Conditional Probability

## Conditional probability, motivation

- The probability of getting a one when rolling a (standard) die is usually assumed to be one sixth
- Suppose you were given the extra information that the die roll was an odd number (hence 1, 3, or 5)
- _Conditional on this new information, the probability is now one third_

## Conditional probability, defined

- Let $B$ be an event so that $P(B) > 0$
- Then the conditional probability of an event $A$ given that $B$ has occurred is

$$
P(A | B) = \frac{P(A \cap B)}{P(B)}
$$

- Notice that if $A$ and $B$ are independent (defined later in the lecture), then

$$
P(A | B) = \frac{P(A)P(B)}{P(B)} = P(A)
$$

## Example

- Consider our die roll example
- $B$ = {1, 3, 5}
- $A$ = {1}

$$
\begin{eqnarray*}
P(\mbox{one given that roll is odd}) & = & P(A ~|~ B) \\ \\
    & = & \frac{P(A \cap B)}{P(B)} \\ \\
    & = & \frac{P(A)}{P(B)} \\ \\
    & = & \frac{1/6}{1/3} = \frac{1}{3}
\end{eqnarray*}
$$



### The Bayesian Solution

Let's use Bayes' theorem to prove that switching is the better strategy.

Let $C_1, C_2, C_3$ be the events that the car is behind Door #1, Door #2, or Door #3, respectively. Each of these events is equally likely a priori:
$P(C_1) = P(C_2) = P(C_3) = \frac{1}{3}$

You choose Door #1. Let $H_3$ be the event that the host opens Door #3 to reveal a goat. We want to find the conditional probability of the car being behind Door #1 or Door #2, given that the host opened Door #3.

**Case 1: The car is behind Door #1 ($C_1$)**
* If the car is behind Door #1, the host can open either Door #2 or Door #3. Assuming he chooses randomly, the probability of him opening Door #3 is:
    $P(H_3 | C_1) = \frac{1}{2}$

**Case 2: The car is behind Door #2 ($C_2$)**
* If the car is behind Door #2, the host *must* open Door #3 to reveal a goat. He cannot open your chosen door (Door #1) or the door with the car.
    $P(H_3 | C_2) = 1$

**Case 3: The car is behind Door #3 ($C_3$)**
* If the car is behind Door #3, the host cannot open this door. The probability of him opening Door #3 is 0.
    $P(H_3 | C_3) = 0$

Now, let's find the **total probability** of the host opening Door #3. This is the denominator in Bayes' theorem:
$P(H_3) = P(H_3 | C_1)P(C_1) + P(H_3 | C_2)P(C_2) + P(H_3 | C_3)P(C_3)$
$P(H_3) = \left(\frac{1}{2}\right)\left(\frac{1}{3}\right) + (1)\left(\frac{1}{3}\right) + (0)\left(\frac{1}{3}\right) = \frac{1}{6} + \frac{1}{3} = \frac{1}{2}$

Finally, we apply Bayes' theorem to find the probabilities of the car being behind Door #1 or Door #2 **after** the host opens Door #3.

**Probability of the car being behind your chosen door (Door #1):**
$P(C_1 | H_3) = \frac{P(H_3 | C_1)P(C_1)}{P(H_3)} = \frac{(1/2)(1/3)}{1/2} = \frac{1}{3}$

**Probability of the car being behind the other unopened door (Door #2):**
$P(C_2 | H_3) = \frac{P(H_3 | C_2)P(C_2)}{P(H_3)} = \frac{(1)(1/3)}{1/2} = \frac{2}{3}$

**Conclusion:** The probability of winning if you **stick** is $1/3$, while the probability of winning if you **switch** is $2/3$. You should **always switch**.

The intuition often fails because people forget that Monty's action of opening a door provides new information. He is not opening a door at random; his choice is constrained by your initial choice and the location of the car. This asymmetry is what shifts the probability.

## The card color problem

Most people's intuition is that the probability is 1/2, reasoning that the card must be either the red-red or the red-black card, and those two are equally likely. But let's use Bayes' theorem to prove this intuition wrong.

***

### The Bayesian Solution

Let's define the events:
* $R_{up}$: The event that the side facing up is red. This is our observed evidence.
* $RR$: The event that you picked the red-red card.
* $BB$: The event that you picked the black-black card.
* $RB$: The event that you picked the red-black card.

Initially, before you've seen the card, the probability of picking any of the three cards is equal:
* $P(RR) = 1/3$
* $P(BB) = 1/3$
* $P(RB) = 1/3$

Now, let's consider the conditional probabilities of observing a red side facing up, given which card you picked:
* If you picked the red-red card ($RR$), the probability of a red side being up is certain.
    $P(R_{up} | RR) = 1$
* If you picked the black-black card ($BB$), it's impossible to have a red side up.
    $P(R_{up} | BB) = 0$
* If you picked the red-black card ($RB$), there is a 50% chance the red side is up.
    $P(R_{up} | RB) = 1/2$

We want to find the probability that the card is the red-red card, given that we see a red side up, which is $P(RR | R_{up})$.

Using **Bayes' theorem**:
$P(RR | R_{up}) = \frac{P(R_{up} | RR)P(RR)}{P(R_{up})}$

First, we need the denominator, $P(R_{up})$, which is the total probability of seeing a red side up. We calculate this using the **law of total probability**:
$P(R_{up}) = P(R_{up} | RR)P(RR) + P(R_{up} | BB)P(BB) + P(R_{up} | RB)P(RB)$
$P(R_{up}) = (1)(1/3) + (0)(1/3) + (1/2)(1/3) = 1/3 + 0 + 1/6 = 3/6 = 1/2$

Now we can plug this back into the Bayes' theorem formula:
$P(RR | R_{up}) = \frac{(1)(1/3)}{1/2} = \frac{1/3}{1/2} = 2/3$

***

### Conclusion

The probability that the other side of the card is also red is **2/3**, not 1/2.

The key to understanding this is that there are **three equally likely red sides** that could be facing up (two on the red-red card, and one on the red-black card). Your observation of a red side gives you more evidence for having picked the red-red card, as it has two red faces, doubling its chance of being the observed card. 

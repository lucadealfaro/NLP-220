## Problems

### Coins

Using a normal quarter coin, you threw T, T, T, T.  Which is true after this? 

1. It is more likely to throw a T.
2. It is more likely to throw an H.
3. It is equally likely to throw an H or a T.

### Variance

Prove that $Var(a + X) = Var(X)$.

### The bus problem

#### One version

You arrive at a bus stop at a random time.  Buses arrive every 10 minutes.  What is the expected time you will wait for the next bus?

#### Another version

You are in Dustland, a remote country where, every now and then, a bus comes.  You walk to a bus stop in the middle of nowhere.  You have no idea of the bus schedule, or even if a bus passes by every day.  But, there is another person there, looking bored.  You ask how long they have been waiting, and they tell you, oh, $x$ hours.  

What is the expected time to the next bus?  Why?  

Hint: The solution is simple.  If you think something complicated, you are likely following a wrong path.


### The Italian soccer lottery (Totocalcio). 

In Italy, every weekend they play $N$ soccer matches. 
Each match $i \in 1, \ldots, N$ can have three outcomes: 1, if the home team wins; X, if the match is a draw; 2, if the away team wins.
We denote by $p_i(\alpha)$ the probability that outcome $\alpha \in \{1, X, 2\}$ occurs in match $i$; we assume that the probabilities are independent for different $i$. 

An outcome for the $N$ matches is a vector $X$ of length $N$, where each element is one of $\{1, X, 2\}$, meaning respectively that the home team wins, the match is a draw, or the away team wins.

Let $\cal F$ be the set of all possible outcomes for the $N$ matches.  The total number of possible outcomes is $3^N$.
For an outcome $X \in \cal F$, let $K(X)$ be the number of bets on outcome $X$, and let $K = \sum_{X \in \cal F} K(X)$ be the total number of bets.

A bet on outcome $X$ pays $K(X)/K$ if outcome $X$ occurs, and 0 otherwise.

1. What is the expected payout of a bet on outcome $X$?
2. What is the optimal way to place a bet? 
3. Should you bet on the most likely outcome, that is, on the $(X_1, \ldots, X_N)$, where $X_i$ is the most likely outcome for match $i$? 
4. What strategy would you play?  Explain.  It's not so simple...


## Problem set 1

In the solutions, don't just give the answer, explain how you got it. 

### Coins

Using a normal quarter coin, you threw T, T, T, T.  Which is true after this? 

1. It is more likely to throw a T.
2. It is more likely to throw an H.
3. It is equally likely to throw an H or a T.

### The bus problem

Warning, this is a difficult problem.
The solution is simple, but it may be hard to find. It's ok if you don't solve it. Consider it food for thought. 

#### One version

You arrive at a bus stop at a random time.  Buses arrive every 10 minutes.  What is the expected time you will wait for the next bus?

#### Another version

You are in Dustland, a remote country where, every now and then, a bus comes.  You walk to a bus stop in the middle of nowhere.  You have no idea of the bus schedule, or even if a bus passes by every day.  But, there is another person there, looking bored.  You ask how long they have been waiting, and they tell you, oh, $x$ hours.  

What is the expected time to the next bus?  Why?  

Hint: The solution is simple.  If you think something complicated, you are likely following a wrong path.

### The Blood Test

Suppose that there's a very rare disease, that affects only 1 person in 10,000,000 people.  That is very rare indeed! 

To test for the disease, there is a blood test that is 99% accurate.  

1. How many tests are needed to be 90% confident that a person has the disease? 

2. If a person does 5 tests, and 4 come out positive and one negative, what is the probability that the person has the disease? 

Asssume that the tests are independent, of course.

### Determining the bias of a coin

You need to determine the bias of a coin.  The bias is $x$ when the coin has probability $x$ of coming up heads.

As a reminder of what is done in class, if you toss the coin and get $k$ heads and $m$ tails, the posterior distribution of the bias $x$ is given by $$P(x|k,m) \propto x^k (1-x)^m$$
and in particular, the Beta distribution Beta $(\alpha, \beta)$ with $\alpha = k+1$ and $\beta = m+1$.

The variance of the Beta $(\alpha, \beta)$ distribution is 
$$\frac{\alpha \beta}{(\alpha + \beta)^2 (\alpha + \beta + 1)}$$

Suppose you want to know the bias within a standard deviation of 0.1.  How many tosses do you need to do?  Find a number of tosses that guarantees that the standard deviation is at most 0.1, no matter what the actual toss outcomes are.



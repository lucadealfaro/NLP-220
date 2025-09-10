### Mutual Information

#### Paints

A wall can be painted in a total of 12 paints: 6 basic shades (red, green, blue, yellow, orange, purple), and each shade can be painted either glossy or matte.  A painter is going to use one of these paints at random, with equal probability.

Let $X$ be the random variable representing the paint, $Y \in \{\text{glossy}, \text{matte}\}$ be the finish type, and $Z \in \{\text{red}, \text{green}, \text{blue}, \text{yellow}, \text{orange}, \text{purple}\}$ be the color shade.

1. What is the entropy $H(X)$ of the paint choice?

2. What is the mutual information $I(Y, Z)$?

Now, define the *happy colors* as $\{\text{red}, \text{yellow}, \text{orange}, \text{green}\}$, and the *sad colors* as $\{\text{green}, \text{blue}, \text{purple}\}$. 

Let $C_H$ be the event of choosing a happy color, and $C_S$ be the event of choosing a sad color.  You can consider such events as bits, with value 1 if they occur and 0 otherwise; each value has its own probability. 

What is the mutual correlation between the events $C_H$ and $C_S$?  Explain.

#### Dice

You roll a dice; let $X$ be the outcome; as usual, $X \in \{1, 2, 3, 4, 5, 6\}$.
Of the roll of the dice, you can ask a question $Y$, which asks: is the roll greater than or equal to $k$? 

How do you choose $k$ to maximize the mutual information $I(X; Y)$?  

#### Stock Tips

You have an insider in Wall Street, who wants to tell you, at the beginning of each day, whether to buy or sell a certain stock.  Let $X$ be the random variable with values Buy, Sell, that your friend wants to communicate to you. 

Your friend can communicate to you by placing vases on their balcony.  They have one vase on each balcony of course; the only thing they can decide is where to place it: on the left side of the balcony, or on the right side, or anywhere in the middle.  Let $Y$ be the random variable representing the position of the vase; you are free to adopt any vase-position scheme you like. 

1.  The one-balcony case.  The friend has only one balcony.  Can he adopt a scheme so that you get the value of $X$ with certainty, but a neighbor observing the balcony cannot?  Explain. 

2. The two-balcony case.  The friend has two balconies, one on each side of his corner house.  Can he adopt a scheme so that you get the value of $X$ with certainty, but neighbors that can observe only one balcony at a time cannot?  Explain.  In this case, if $Y_1$ and $Y_2$ are the positions of the vases on the two balconies, what is $I(X; Y_1)$, $I(X; Y_2)$, and $I(X; Y_1, Y_2)$?


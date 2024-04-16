# Decision Trees

Tree-based algorithms are widely used in the data science world.
Decision trees, a supervised learning approach, are the fundamental building blocks of any tree-based model.
Just like any ML algorithm, a decision tree helps predict the outcome given the values of input variables.

Given any ML problem, you are going to start by asking what are the input variables (`Features` or `Predictors`) that you are going to use. For example:
1. In `Regression`, you may want to ask which input variable is going to help you predict the output in the best way.
2. If you want to `classify` an email as spam, what features of the email really help you to classify it as spam email.

Start by asking:
1. Factors that affect the outcome
2. Order of importance of each factor, as some of these predictors are more important than others.

Think of a flowchart with a yes or no outcome at each step. This is a decision tree.

## White Box

If you want to classify articles as tech articles or something, you could use `Support Vector Machines` (SVM). SVMs provide you a plane (in like a 3-D space, n-D space), and based on which side of the plane the article falls, you'll decide the type of article. SVM is like a `black box`. It is hard to understand or visualize what's happening inside.

A decision tree is like a `white box`. An intuitive and rule-like way to explain the classification algorithm. It's like you have a comprehensive set of rules and just by following the rules you arrive at the outcome.

## Types of Variables

Input variables represent `nodes` in a decision trees, where you will decide which way to go. A `leaf` would be the end goal/outcome in this case.

> Note: These types apply to input variables as well as output variables.

### Categorical variables

Variables that take value from a specific set of values. Example: gender, color, spam email.
Here, since decision trees are used for categorical outcome, they can be used for `Classification`, while building a classification tree. In a classification problem, outcomes / leaf nodes are called `Class Labels`.

### Continuous/Numeric variables

One that can take in a range of values. Example: temperature, sale price of a house.
Here, since decision trees are used for range of outcome, they can be used for `Regression`, while building a regression tree.

## Outcome

Your `Feature Vector` would be a list of values, one for each of the Features. You'll precompute all possible vectors, and when your input matches one particular form of feature vector, it is going to result in a known outcome. Example: (1, X, X, X), (0, 1, X X), etc.

Decision tree also gives us the `Conditional Probability` of the outcome, given the values of the input variables. Hence in general, the outcomes are `Non Deterministic`, also called most likely outcome. At each leaf node, we'll know the `probability` of the outcome.

> TODO: Find out how these probabilities are calculated.

## Building the tree

`Recursive partitioning` is the most common strategy, to take some training data and arrive at a decision tree. You:
1. Take the entire training data as a single set
2. Then recursively keep dividing it into subsets, based on the values of the input variables.
3. Each time you divide the data into subsets, a node of the decision tree is created.

Some of the recursive partitioning algorithms are: `ID3`, `C4.5`, `CART`, `CHAID`. These algorithms use a different metrics for arriving at the best attribute.

Training data needs to be represented in the form of tuples, a feature vector, that represents that particular data point and it's label/outcome.

## Recursive Partitioning

The basic idea is to continuously split the data into subsets, based on input variables. With each split, one attribute is chosen to be the basis of the split.

Greedy algorithm for learning a decision tree. We build histograms to find patterns and probabilities.

There is a `stopping condition` when building decision trees, that is:
1. when all our subsets are mostly homogeneous
2. we run out of attributes
3. the tree is too big

Finding the `best split` for the continuous input variable, is done by building histogram and finding a shift in data.

There are more algorithms based on this strategy to solve for decision trees.

## Cons of Decision Trees

One serious problem with them - they are prone to `Overfitting`.
There are bunch of techniques to avoid the overfitting, including `Cross Validation`, `Regularization`, and `Ensemble learning`.

## Random Forest

This is one particular tree-based model that avoids overfitting in decision trees using Ensemble learning.

### Information Gain

The idea of `Information Gain` is to reduce `entropy` and maximize `information`. Information is a measure of the amount of information a statement contains. The lower the probability, the more information you get. Example: guess the card game. `Entropy` is the measure of uncertainty in an answer when you're trying to measure something. Entropy decreases with certainty in the process of figuring out the answer. `ID3` and `C4.5` uses information gain.


## References

* [Kaggle Titanic](https://www.kaggle.com/competitions/titanic) challenge
    * Get the data
    * Train a classifier on the training set
    * Compute predictions on the test set
    * Submit the predictions made, to obtain a score of how good the classifier was

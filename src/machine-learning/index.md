# Machine Learning (Simplified)

Machine learning is like teaching a robot to learn by itself. It's about teaching computers to learn from examples and experiences, just like how you learn new things!

Imagine that you want a robot to learn to sort your toys into different boxes. At first, the robot doesn't know which toy goes into which box. But, if you show the robot many times that the teddy bear goes into the teddy bear box, and the car goes into the car box, the robot will start to learn. After a while, the robot can sort the toys by itself without your help.

## Ways of teaching the robot

### Supervised Learning

These algorithms learn a function that maps inputs to an output from a set of labeled training data.

This is like when parents help the kid with their homework. They already know the correct answers (because they're the "teacher") and they guide them to learn the right answers. In the same way, in supervised learning, we have a robot that is `learning from examples where we already know the right answer`. 

### Unsupervised Learning

These algorithms learn fundamental patterns of the data from unlabeled data samples, without specific goal in mind. This is a NP-hard problem, and does not scale well with data. This issue has made it hard for the research to further much in this area, as compared to supervised learning.

This is like when kids play with their Lego blocks. Nobody tells them what to build, but they start grouping blocks by color or size, and maybe they start building something on their own. In unsupervised learning, the robot doesn't have any right answers to learn from. Instead, it `tries to find patterns or groups in the data` all by itself.

### Reinforcement Learning

These algorithms try to mimic typically how human's learn, through taking an action and waiting for feedback or reward, for them to decide on the next step.

Watch documentary of [Google Deepmind Go challenge](https://www.youtube.com/watch?v=1aMt7ulL6EI&ab_channel=GoogleDeepMind) match. In game 2, step 32 or 37, the step that the algorithm made was ingenious. Find commentaries on that move or read literature around it. It's amazing what these algorithms can learn when they're given so much data.

This is like when you play a video game. You try different things, and sometimes you win points, and sometimes you lose points. Over time, you learn what actions help you win more points. In reinforcement learning, a robot `learns by trying different actions and getting rewards or penalties`. It learns to do the things that get it the most rewards. 

### Other areas in research

* Active learning - early in adoption. Also in a place where it allows to sparingly have a human in the loop.
* Self-supervised learning - Meta's chief scientist is a big proponent of learning from unlabeled data.
* Transfer learning

## Common Algorithms

* **Regression** - predicting a value
* **Classification** - predicting a class or category
* **Clustering** - grouping ungrouped data
* **Association Mining Rule** - finding associations between two or more classes

### Deep Learning

When you're applying machine learning techniques, one of the key aspect is `Feature engineering`, where you're trying to create some sort of features or variables that'll allow the system to learn the task better. Feature engineering is limited by your intuition and understanding of the problem itself. These are mostly driven by domain knowledge, the context of the problem space and your creativity in what you think is important to the problem.

`Deep learning` is a class of ML algorithms that uses multiple layers to progressively extract higher-level features/abstractions from raw inputs. 

Deep learning became a big deal in ML space, because it takes away the feature engineering aspect away from you. It starts to abstract the useful information from the data itself, and is not limited like human brain.

On the contrary, deep learning has also made machine learning a black box, meaning it is harder to figure out what the model is trying to do.

## Trends over time

* <1950s - Statistical methods
* 1950s  - Simple ML algorithms
* 1960s  - Bayesian methods in ML
* 1970s  - AI winters
* 1980s  - Back propagation
* 1990s  - SVMs & RNNs
* 2000s  - Kernel methods
* 2010s  - Deep learning
* 2020s  - LLMs

> Note: When you're solving SVMs, you're actually solving quadratic optimization problem, that does not scale with the number of samples itself. In simple terms, if you had to train with a large amount of data, training of SVMs becomes a problem.

> Note: Yoshua Bengio is the one who brought breakthrough in Deep learning space.

> Note: Models in 1950s were trained on 2 parameters. GPT3 is trained on 175 billion parameters. ML space has evolved a lot in 70 years.

### Reason for progress

1. Computational power
2. Big data + Map-Reduce
3. Breakthrough in Deep learning

All these things came in between 2006 to 2010. For example, you can have an EC2 instance with 12 TB of RAM, democratization of AI

## References

* Applied Machine Learning, Columbia University
* [Machine Learning Course - CS 156](https://www.youtube.com/playlist?list=PLD63A284B7615313A) | CatTech | YouTube playlist
    * [Website](https://work.caltech.edu/telecourse)
* Book: [Fundamentals of Data Visualization](https://learning.oreilly.com/library/view/fundamentals-of-data/9781492031079/), Claus O. Wilke, 2019
    * [Online book](https://clauswilke.com/dataviz/)
    * [GitHub code](https://github.com/clauswilke/dataviz)

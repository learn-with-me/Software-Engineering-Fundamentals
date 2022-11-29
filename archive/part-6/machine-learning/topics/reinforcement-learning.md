# Reinforcement Learning

\(Reward maximization and strengthen the response\)

Supervised learning - function approximation. Goal is to find the function that will map new x to value y

Unsupervised learning - clustering description. Find the function from a bunch of x that will tell you something about Xs

Reinforcement learning - Goal is to find the function that will map new x to value y, based on z

Markov

1. only present matters
2. things are stationary

**Markov Decision Process**

States    : S

Model    : T\(s, a, s'\)  ~  Pr\(s' \| s, a\)

Actions  : A\(s\), A

Reward  : R\(s\), R\(s, a\), R\(s, a, s'\)

Policy    : Pie\(s\) -&gt; a  
                Pie\* - maximizes long term expected result  
                y = f\(x\) based on z is read here as a = Pie\(s\) based on r  
                Can be defined by **Bellman Equation**. Other related terms are** Value Iteration and Policy Iteration**.

If utility of a sequence is more than the other sequence, then adding more states to each of those sequence will have the same preference. This is known as Sequence of Rewards.

```
(Sum of pow(r, t)) . Rmax
x = (r0 + r1 + r2 + .....)
x = 1/(1-r)
Final answer is Rmax/(1-r)
```

Reward -&gt; Immediate feedback

Utility -&gt; Long term feedback -&gt; Delayed reward

![](/assets/learning.png)

![](/assets/learning_types.png)

![](/assets/three_approaches_to_RL.png)

**Policy Iteration \(Evaluating and Improving Policy\)**

Convert non-linear equations to linear equations


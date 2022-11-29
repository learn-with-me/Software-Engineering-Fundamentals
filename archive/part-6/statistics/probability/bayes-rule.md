### Bayes Rule

\(Rev Thomas Bayes\)

```
Prior Probability . Test evidence = Posterior Probability
```

```
Example: p(C) = 0.01

Test: 90% it is positive if you have C           -- Sensitivity
      90% it is negative if you don't have C     -- Specitivity

Prior: p(C) = 0.01
       p(P | C) = 0.9
       p(7P | 7C) = 0.9

Joint/Combined probability of two events
Posterior: p(C , P) = p(C) . p(P | C)
           p(7C , P) = p(7C) . p(P | 7C)

Normalizer: p(P) = p(C , P) + p(7C , P)

Posterior: p(A | B) = Joint probability of two events / Normalizer
           p(C | P) = p(C , P) / p(P)
           p(7C | P) = p(7C , P) / p(P)
```

![](/assets/bayes_rule.png)

![](/assets/bayes_rule_flowchart.png)

0.5 0.5

0.8 0.2

0.4


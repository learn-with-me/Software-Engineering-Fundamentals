# Learning

```
A checkers learning problem

Task                   T : playing checkers
Performance Measure    P : percent of games won in the world tournament
Training Experience    E : games played against itself

In order to complete the design of the learning system, we must now choose
  1. the exact type of knowledge to be learned
  2. a representation for this target knowledge
  3. a learning mechanism
```

Learning can be broken down into three components

1. **Choosing the training experience**  
   Training experience is where our system learns from. Type of training experience can have significant impact on success or failure of the learner. A training experience has following key attributes:

   1. Whether the system can provide direct feedback or indirect feedback :- To note, a game can be lost even with initial optimal moves due to poor moves later on. Hence direct feedback typically is easier than indirect feedback.

   2. Degree to which the learner controls the sequence of training

      1. Learner relies on the teacher to select informative board states and to provide correct moves for each.

      2. Learner itself proposes board states and ask the teacher for correct moves.

      3. Learner has complete control. Learns by playing against itself with no teacher present.

      4. Settings in which training experience is provided by a random process outside of learner's control

      5. Settings in which learner may pose various type of queries to an expert teacher

      6. Settings in which learner collects training examples by autonomously exploring its environment

   3. How well it represents the distribution of examples over which the final system performance P must be measured

      1. In general, learning is most reliable when the training examples follow a distribution similar to that of future test examples

      2. Performance metric **P** is the percent of games the system wins in the world tournament. If its training experience **E** consists only of games played against itself, there is an obvious danger that this training experience might not be fully representative of the distribution of situations over which it will later be tested. Despite our need to make this assumption in order to obtain theoretical results, it is important to keep in mind that this assumption must often be violated in practice.

2. **Choosing the target function**  
   Determine exactly what type of knowledge will be learned and how this will be used by the performance program. The program only needs to learn how to choose the best move from among the legal moves.

3. Choosing a representation for the target function

4. Choosing a function approximation algorithm

5. The final design




# Dynamic Programming in Reinforcement Learning

## Principles of Dynamic Programming

Dynamic Programming (DP) is a method for solving complex problems by breaking them down into simpler subproblems. It is applicable to problems exhibiting the properties of overlapping subproblems and optimal substructure. In the context of reinforcement learning, DP can be used to solve the Markov Decision Process (MDP).

### Key Principles:
- **Optimal Substructure**: The optimal solution of the problem can be constructed from the optimal solutions of its subproblems.
- **Overlapping Subproblems**: The problem can be broken down into subproblems which are reused several times.

DP methods rely on the recursive decomposition of the value functions, and they use Bellman equations to update the value functions.

## Bellman Equations

The Bellman equations are fundamental to dynamic programming in reinforcement learning. They provide a recursive decomposition for the value functions.

### Bellman Optimality Equation

The Bellman optimality equation is nonlinear with a unique solution that is independent of the policy. There is no closed-form solution (in general). Instead, there are several iterative methods to solve for $V$.

### Dynamic Programming Methods:
- **Value Iteration**
- **Policy Iteration**

Other methods include:
- **Monte Carlo Methods**
- **Temporal Difference Learning**

To use dynamic programming, the MDP must be known and well-defined in terms of its components (states, actions, rewards, etc.). DP is used for planning in an MDP and is applied in two cases:
1. **Prediction**: Given a policy $\pi$, find the state-value function and the action-value function.
2. **Control**: Estimate the optimal value functions and the optimal policy $\pi^*$.

### Strategies:

|                  | Evaluate Policy $\pi$     | Find Optimal Policy $\pi^*$  |
|------------------|-------------------------------|----------------------------------|
| **Known MDP**    | Policy Evaluation             | Policy Iteration, Value Iteration|
| **Unknown MDP**  | Monte Carlo, Temporal Difference | Q-learning                     |

### Basic Algorithms:

- **Policy Evaluation**: Given a policy $\pi$, what is the associated value function?
- **Policy Iteration**: Given a policy $\pi$, how to find the optimal policy $\pi^*$?
- **Value Iteration**: How to find an optimal policy $\pi^*$ from scratch?

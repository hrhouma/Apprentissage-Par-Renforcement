# Policy in Reinforcement Learning

## Definition of Policy

In reinforcement learning, a policy defines the agent's way of behaving at a given time. It is a mapping from states of the environment to actions to be taken when in those states. The policy is often denoted by $\pi$.

Mathematically, a policy $\pi$ is defined as:

- **Deterministic Policy**: A deterministic policy maps each state to a specific action. Formally, $\pi(s) = a$, where $s$ is a state and $a$ is an action.
- **Stochastic Policy**: A stochastic policy gives a probability distribution over actions for each state. Formally, $\pi(a|s) = P[A_t = a | S_t = s]$, which is the probability that action $a$ is taken in state $s$.

## Deterministic and Stochastic Policies

### Deterministic Policy

In a deterministic policy, the action is determined with certainty given a state. This can be represented as:
$\pi(s) = a$

### Stochastic Policy

In a stochastic policy, the action is determined based on a probability distribution given a state. This can be represented as:

---


>$$\pi(a|s) = P[A_t = a | S_t = s]$$

Where:
- $\pi(a|s)$ is the probability of taking action $a$ in state $s$.
- $A_t$ is the action at time step t.
- $S_t$ is the state at time step t.


---

## Example of a Policy

Consider a 3x3 grid where an agent can move in four directions: right, down, left, and up. The following matrix represents the policy for the agent, where each element corresponds to an action to be taken in a specific state (grid cell):

```
[ [right, down, down],
[right, right, down],
[right, right, up] ]
```

### Grid Representation

- Each cell in the matrix represents a state.
- The action to be taken in each state is represented by the direction the agent should move.

### Explanation of Actions

- **Row 1**: 
  - From the top-left corner (state (0,0)), the agent should move `right` to (0,1).
  - From state (0,1), the agent should move `down` to (1,1).
  - From state (0,2), the agent should move `down` to (1,2).

- **Row 2**:
  - From state (1,0), the agent should move `right` to (1,1).
  - From state (1,1), the agent should move `right` to (1,2).
  - From state (1,2), the agent should move `down` to (2,2).

- **Row 3**:
  - From state (2,0), the agent should move `right` to (2,1).
  - From state (2,1), the agent should move `right` to (2,2).
  - From state (2,2), the agent should move `up` to (1,2).

This policy directs the agent through the grid in a way that each state has a specific action associated with it, which is a characteristic of a deterministic policy.

## State-Value Function

The state-value function $V(s)$ gives the expected return (cumulative reward) starting from a state $s$ and following a specific policy $\pi$. 

For our example grid, the state-value function matrix $V(s)$ can be represented as:

```
[ [4, 3, 3],
[3, 2, 1],
[3, 1, 0] ]
```

### Explanation of State-Value Function Matrix

- Each cell in the matrix represents the value of that state under the given policy.
- The values indicate the expected return starting from that state and following the policy until reaching the goal.

### Interpretation of Values

- **Row 1**:
  - $V(0,0) = 4$: Starting from state (0,0) and following the policy, the expected return is 4.
  - $V(0,1) = 3$: Starting from state (0,1) and following the policy, the expected return is 3.
  - $V(0,2) = 3$: Starting from state (0,2) and following the policy, the expected return is 3.

- **Row 2**:
  - $V(1,0) = 3$: Starting from state (1,0) and following the policy, the expected return is 3.
  - $V(1,1) = 2$: Starting from state (1,1) and following the policy, the expected return is 2.
  - $V(1,2) = 1$: Starting from state (1,2) and following the policy, the expected return is 1.

- **Row 3**:
  - $V(2,0) = 3$: Starting from state (2,0) and following the policy, the expected return is 3.
  - $V(2,1) = 1$: Starting from state (2,1) and following the policy, the expected return is 1.
  - $V(2,2) = 0$: Starting from state (2,2) and following the policy, the expected return is 0.

This state-value function helps in evaluating how good the given policy is in terms of the expected returns from each state.

## Evaluation of Policy

Evaluating a policy involves determining how good a policy is in achieving the goal of maximizing the cumulative reward. This is typically done using two main functions:

- **State-Value Function (V)**: This function gives the expected return (cumulative reward) starting from a state $s$ and following policy $\pi$. It is defined as:
---


>$$V^{\pi}(s) = \mathbb{E}_{\pi} [R_t | S_t = s]$$


---
- **Action-Value Function (Q)**: This function gives the expected return starting from a state s, taking an action a, and then following policy π. It is defined as:
---


>$$Q^{\pi}(s, a) = \mathbb{E}_{\pi} [R_t | S_t = s, A_t = a]$$

Where:
- $R_t$ is the reward at time step t.
- $S_t$ is the state at time step t.
- $A_t$ is the action at time step t.


---

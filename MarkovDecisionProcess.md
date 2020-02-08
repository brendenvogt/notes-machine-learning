# Markov Decision Process
A framework for mathematically calculating the probability of a certain decision process, and also for evaluating the cost and reward of a certain decision or decision processes.
### The Marcovian Property
- Our transition function only depends on the present state `s`. If your transition function also depended on where you were at a prior state, your transition function would have to include more `s` as input. But this violates The Marcovian Property. 
- You can bend the rules around the Marcovian Process by requiring state `s` to include all the past history of prior states. `s = s(s-1)` for example.
- Another important requirement is that the world doesn't change, or in other words the transition function doesn't change.
## States 
- States are distinct locations, circumstance, variables, that identify and describe something at a given point in time or condition of being. 
  - In the world of a grid. Different grid squares you can reach represents the reachable states, or for our discussion just simply states.
- represented as `s`


## Model (transition model/ transition function)
- Is a combination of a state
- represented as T(s, a, s') ~ Pr(s' | s, a)
  - Given the Transition Function `T`, based on the current state `s`, and action `a`, and desired state `s'` we can calculate the probability `Pr` you will end up in state `s'` given you were in the state `s` and took action `a`.
- For example:
  - In a deterministic world, being in a start state, the probability of arriving in the square right above the start state by taking action up is probability 1. Similarly the probability of arriving at the square to the right when currently at the start state taking action up is probability 0.
  - 

## Action
- Actions are the things you can do in a particular state.
  - e.g. [up, down, left, right]
- represented as: `A(s)` for actions dependent on state, and `A` for actions not dependent on state.
- Some people usually think of actions as a function of state, like some actions are only possible in a certain state, but here we can still represent actions for all states, but the actions that aren't possible at a given state have no effect.


## Reward
- a scalar value for being in a state.
  - for example the reward for arriving at a `good` state is `+1`
  - and the reward for arriving at a `bad` state is `-3`
- Can be represented as `R(s)` the reward for entering a state.
  - Alternatively can be represented as `R(s, a)` which is the reward for being in a certain state and taking in action,
  - And alternatively `R(s,a,s')` which is the reward for being in a certain state, and taking a given action and then ending up in another state `s'`.

## Policy
- A Marcov Decision Process is the problem.
- A Policy is the solution. 
- refered to as pi(s) -> a 
  - or the action that is taken given a certain state.
- Pi* is the optimal solution to a MDP to maximize the Reward as a result.


## More about Rewards

### Problem: The Map
|   |   |   |   |
|---|---|---|---|
| o | o | o | + |
| o | x | o | - |
| o | o | o | o |

- `R(s) = -0.04`
- `+` and `-` are terminating states which means the simulation ends.
- `+` represents a reward of `R(+) = +1.0` 
- `-` represents a reward of `R(+) = -1.0` 
- `x` represents a state that cannot be acted on. (if an action with this as `s'` doesn't have any effect)
- This is like you are at the beach and everywhere you go is hot sand. You live forever so you will either

### Answer: The Policy

|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| A | > | > | > | + |
| B | ^ | x | ^ | - |
| C | ^ | < | < | < |

- Ive put reference letters and numbers to make it easier to reference a particular spot.
- Because this is a stochastic simulation, actions taken will not always result in a definite consistent state. 
  - which means when we are at `C3` we want to go the safest route (the long way around). If we went up from `C3` to `B3` even though it is shorter, it actually increases our probability that we would incur a `-1` and end the simulation.

## Quiz 1
- Given `R(s) = +2`, fill in the following states with one of the following `u`, `d`, `r`, `l`
- There is a slight probability that when you try to go in a particular direction, that you will actually go right or left from that direction. (for example if you want to go left, there is a slight probability that you will actually go up or down)

|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| A |   |   |   | + |
| B |   | x |   | - |
| C |   |   |   |   |

##### Answer
- NOTES - states marked with a `*` means it doesn't matter where you go.

|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| A | * | * | l | + |
| B | * | x | l | - |
| C | * | * | * | d |

##### Explanation
- The reason for `A3` are obvious, going right would end the simulation, thus ending your opportunity for infinite positive reward. `C4` is pretty intuitive because you don't want to go into the `-` so you would originally think to go left. But as it is stated in the rules, there is some chance for you to go right or left from the direction you intended. If you go left from `C4` there is a slight chance you actually go up to the `-` state. So going down is the safest opportunity because there is no probability of going to the `-`.

## Quiz 2
- Given `R(s) = -2`, fill in the following states with one of the following `u`, `d`, `r`, `l`
- There is a slight probability that when you try to go in a particular direction, that you will actually go right or left from that direction. (for example if you want to go left, there is a slight probability that you will actually go up or down)
  
|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| A |   |   |   | + |
| B |   | x |   | - |
| C |   |   |   |   |

##### Answer
  
|   | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| A | r | r | r | + |
| B | u | x | r | - |
| C | r | r | r | u |

##### Explanation

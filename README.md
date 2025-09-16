# VALUE ITERATION ALGORITHM

## AIM
Implement value iteration algorithm to find optimal policy for the altered frozen lake environment.

## PROBLEM STATEMENT
Given an altered Frozen Lake environment with a set of states, actions, transition probabilities, and rewards, the goal is to compute the optimal policy that maximizes the expected cumulative reward. Value iteration is used to iteratively compute the value function and derive the optimal policy from it.

## VALUE ITERATION ALGORITHM
### STEP 1:
Import required libraries for the program.
### STEP 2:
Load the frozen lake environment and make changes.
### STEP 3:
Start by assigning an initial value (usually zero) to all states in the environment.
### STEP 4:
Repeat the process of updating the value of each state based on the expected rewards from all possible actions until the values stop changing significantly.
### STEP 5:
Once the values converge (changes are very small), determine the optimal action for each state.
### STEP 6:
Construct the optimal policy by choosing, for each state, the action that gives the highest expected reward according to the final value function.
### STEP 7:
Run the function and display the results.
## VALUE ITERATION FUNCTION
### Name: Krithick Vivekananda 
### Register Number: 212223240075
```python
def value_iteration(P, gamma=1.0, theta=1e-10):
    V = np.zeros(len(P), dtype=np.float64)
    while True:
      Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
      for s in range(len(P)):
        for a in range(len(P[s])):
          for prob, next_state, reward, done in P[s][a]:
            Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      if np.max(np.abs(V-np.max(Q,axis=1)))<theta:
        break
      V=np.max(Q,axis=1)
    pi=lambda s: {s:a for s,a in enumerate(np.argmax(Q,axis=1))}[s]
    return V, pi
```
## OUTPUT:

### Optimal Policy
<img width="560" height="192" alt="image" src="https://github.com/user-attachments/assets/2f26042e-16e9-4130-bf65-c24ec6901336" />

### Success Rate for the Optimal Policy
<img width="740" height="53" alt="image" src="https://github.com/user-attachments/assets/512a2676-c1d1-4d47-bed2-63929cf21176" />

### Optimal value function
<img width="542" height="129" alt="image" src="https://github.com/user-attachments/assets/07f74409-6fc1-430c-9f4b-e4aa5835c000" />

## RESULT:
Therefore, value iteration algorithm to find optimal policy for the altered frozen lake environment is successfully implemented.

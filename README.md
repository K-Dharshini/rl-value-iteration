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
### Name: DHARSHINI K
### Register Number: 212223230047
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

## OUTPUT
### Optimal policy
<img width="481" height="191" alt="image" src="https://github.com/user-attachments/assets/1779964c-fb20-4d02-83e2-a99938e535f5" />

### Optimal value function
<img width="503" height="193" alt="image" src="https://github.com/user-attachments/assets/69e82015-5238-48dd-93bd-36fb4904f87e" />

### Success rate for the optimal policy
<img width="692" height="30" alt="image" src="https://github.com/user-attachments/assets/c8bcacda-02a7-4428-9a86-c5dd376290fd" />

## RESULT
Therefore, value iteration algorithm to find optimal policy for the altered frozen lake environment is successfully implemented.

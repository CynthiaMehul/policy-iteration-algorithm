# POLICY ITERATION ALGORITHM
## AIM
Implement policy iteration algorithm to find optimal policy by iteratively maximizing the value function. 

## PROBLEM STATEMENT
Finding the optimal policy to start from start state and reach goal state in the frozen lake environment using policy iteration.

## POLICY ITERATION ALGORITHM
# Step 1:
Import required libraries.
# Step 2:
Load the frozen lake environment.
# Step 3:
Define the value evaluation, value improvement and value iteration functions.
# Step 4: 
Run the functions and display the results.

## POLICY IMPROVEMENT FUNCTION
### Name: Cynthia Mehul J
### Register Number: 212223240020
```python
def policy_improvement(V,P,gamma=1.0):
  Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
  for s in range(len(P)):
    for a in range(len(P[s])):
      for prob, next_state, reward, done in P[s][a]:
        Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
      new_pi=lambda s: {s:a for s,a in enumerate(np.argmax(Q, axis=1))}[s]
  return new_pi
```
## POLICY ITERATION FUNCTION
### Name: Cynthia Mehul J
### Register Number: 212223240020
```python
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi
```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy

<img width="523" height="167" alt="image" src="https://github.com/user-attachments/assets/fb4c2735-8c43-41d1-aa05-a42498852cc8" />

<img width="507" height="171" alt="image" src="https://github.com/user-attachments/assets/3e40017c-1bd8-4c8e-8a0d-41b7d6fe5a0a" />

### 2. Policy, Value function and success rate for the Improved Policy

<img width="538" height="156" alt="image" src="https://github.com/user-attachments/assets/81d1e9e6-a458-4ab5-8683-890aa9cefcb1" />

<img width="502" height="160" alt="image" src="https://github.com/user-attachments/assets/fe1894ed-dc22-44fa-a99a-7cb8cc96cfb3" />

### 3. Policy, Value function and success rate after policy iteration

<img width="564" height="150" alt="image" src="https://github.com/user-attachments/assets/2eb34781-7d94-41a8-a2d6-9820249f5d1b" />

<img width="503" height="181" alt="image" src="https://github.com/user-attachments/assets/39cd3b21-68ab-43be-bc0d-94dc7abb1182" />

## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.

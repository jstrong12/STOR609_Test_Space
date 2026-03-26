# Value Iteration Algorithm Package

## The Problem


## The Value Iteration Algorithm

### Input

S = Set of States \
A = Set of Actions \
P = State Transition Function P(s'|s,a) \
R = Reward Function R(s,a)/R(s'|s,a) \
$\gamma$ = \
$\epsilon$ = \
Mode = 1 if R is of the form R(s,a), 2 if R is of the form R(s'|s,a) 

### Output

V\[S\] = Value Function \
$\pi$\[S\] = Optimal Policy

### Pseudocode

```text
Value_iteration(S,A,P,R,γ,ε,mode):
    n1 = Length of S
    n2 = Length of A 
    V = List of n1 zeros
    π = List of n2 zeros
    Diff = 1 
    k = 0

    if mode = 1:
        while Diff > ε:
            k = k + 1
            Vold = V
            for each state s:
                V[s] = max_a [R(s,a) + γ * sum_{s'} (P(s'|s,a) * Vold[s'])]
            Diff = max_s (|V[s] - Vold[s]|)

        for each state s:
            π[s] = max_a [R(s,a) + γ * sum_{s'} (P(s'|s,a) * Vold[s'])]
        return π, V

    if mode = 2:
        while Diff > ε:
            k = k + 1
            Vold = V
            for each state s:
                V[s] = max_a [sum_{s'} (P(s'|s,a) * (Vold[s'] * γ + R(s'|s,a)))]
            Diff = max_s (|V[s] - Vold[s]|)

        for each state s:
            π[s] = max_a [sum_{s'} (P(s'|s,a) * (Vold[s'] * γ + R(s'|s,a)))]
        return π, V
```

## How This Code Compares to Figure 9.16

Figure 9.16 provides pseudocode for the value iteration algorithm, though it is not too specific on some aspects. For example, it says to run a repeat loop until termination, but does not really mention what this actually means. 

$$
\text{Mode 1:} \quad V[s] = max_a [sum_{s'} (P(s'|s,a) * (Vold[s'] * γ + R(s'|s,a)))]

\text{Mode 1:} \quad V[s] = max_a [sum_{s'} (P(s'|s,a) * (Vold[s'] * γ + R(s'|s,a)))]
$$

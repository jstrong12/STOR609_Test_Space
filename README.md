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
Value_iteration(S, A, P, R, γ, ε, mode):

    n1 = |S|
    n2 = |A|
    V = [0, 0, ..., 0]  (length n1)
    π = [0, 0, ..., 0]  (length n1)
    Diff = 1
    k = 0

    if mode == 1:
        while Diff > ε:
            k = k + 1
            Vold = V

            for each state s:
                V[s] = max_a ( R(s,a) + γ * Σ_{s'} ( P(s'|s,a) * Vold[s'] ) )

            Diff = max_s ( |V[s] - Vold[s]| )

        for each state s:
            π[s] = argmax_a ( R(s,a) + γ * Σ_{s'} ( P(s'|s,a) * Vold[s'] ) )

        return π, V


    if mode == 2:
        while Diff > ε:
            k = k + 1
            Vold = V

            for each state s:
                V[s] = max_a ( Σ_{s'} ( P(s'|s,a) * (γ * Vold[s'] + R(s',a)) ) )

            Diff = max_s ( |V[s] - Vold[s]| )

        for each state s:
            π[s] = argmax_a ( Σ_{s'} ( P(s'|s,a) * (γ * Vold[s'] + R(s',a)) ) )

        return π, V
```

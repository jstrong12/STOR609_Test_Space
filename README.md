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

Value_iteration(S,A,P,R,$\gamma$,$\epsilon$,mode){ \
    n1 = Length of S\
    n2 = Length of A \
    V = List of n1 zeros\
    Pi = List of n2 zeros\
    Diff = 1 \
    k = 0\
    **if** mode = 1:\
        **while** Diff > $\epsilon$:\
            k = k + 1\
            Vold = V\
            **for each** state s:\
                V\[s\] = $\max_a \text{R(s,a)} + $
}                

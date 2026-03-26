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

<pre>
Value_iteration(S,A,P,R,$\gamma$,$\epsilon$,mode):
    n1 = Length of S
    n2 = Length of A 
    V = List of n1 zeros
    $\pi$ = List of n2 zeros
    Diff = 1 
    k = 0

    <b>if</b> mode = 1:
        <b>while</b> Diff > $\epsilon$:
            k = k + 1
            Vold = V
            <b>for each</b> state s:
                V[s] = $\max_a \text{R(s,a)} + \gamma \Sigma_{s'} (\text{P(s'|s,a) * Vold[s']})$
            Diff = $\max_s (|\text{V[s] - Vold[s]}|)$

        <b>for each</b> state s:
            $\pi$[s] = $\max_a \text{R(s,a)} + \gamma \Sigma_{s'} (\text{P(s'|s,a) * Vold[s']})$
        <b>return</b> $\pi$, V

    <b>if</b> mode = 2:
        <b>while</b> Diff > $\epsilon$:
            k = k + 1
            Vold = V
            <b>for each</b> state s:
                V[s] = $\max_a \Sigma_{s'} (\text{P(s'|s,a) * (Vold[s'] * \gamma + \text{R(s'|s,a)}))}$
            Diff = $\max_s (|\text{V[s] - Vold[s]}|)$

        <b>for each</b> state s:
            $\pi$[s] = $\max_a \Sigma_{s'} (\text{P(s'|s,a) * (Vold[s'] * \gamma + \text{R(s'|s,a)}))}$
        <b>return</b> $\pi$, V
</pre>
    - $\pi$[s] = $\max_a \Sigma_{s'} (\text{P(s'|s,a) * (Vold[s'] * \gamma + \text{R(s'|s,a)}))}$
  - **return** $\pi$, V 

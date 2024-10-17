

### 1. Bellman Equation

$$
Q(S_1, \text{right})_{\text{observed}} = R(S_2) + \gamma \max_{a} Q(S_2, a)
$$

### 2. TD Error

$$
\text{TD Error} = Q(S_1, \text{right})_{\text{observed}} - Q(S_1, \text{right})_{\text{expected}}
$$



### 3. Update Rule

$$
Q(S_1, \text{right}) = Q(S_1, \text{right}) + \alpha \times \text{TD Error}
$$


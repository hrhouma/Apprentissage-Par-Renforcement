
$$
Q(S_1, \text{right})_{\text{observed}} = R(S_2) + \gamma \max_{a} Q(S_2, a)
$$

$$
\text{TD Error} = Q(S_1, \text{right})_{\text{observed}} - Q(S_1, \text{right})_{\text{expected}}
$$

$$
Q(S_1, \text{right}) = Q(S_1, \text{right}) + \alpha \cdot \text{TD Error}
$$

Ces équations sont maintenant correctement formatées pour un fichier Markdown (.md) utilisant LaTeX avec des doubles dollars ($$). Chaque équation est sur sa propre ligne, entourée de doubles dollars, sans espaces supplémentaires avant ou après les symboles $$. Cela devrait fonctionner correctement dans la plupart des renderers Markdown qui supportent LaTeX.


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


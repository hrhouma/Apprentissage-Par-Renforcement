### TD(0) — Mise à jour immédiate après chaque étape

$$
V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) \right]
$$

### TD(1) — Utilisation d'une récompense après une étape supplémentaire

$$
V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 V(S_{t+2}) \right]
$$

### TD(2) — Utilisation de deux étapes supplémentaires

$$
V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 V(S_{t+3}) \right]
$$

### TD(n) — Généralisation pour \(n\) étapes

$$
V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha \left[ \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} + \gamma^n V(S_{t+n}) \right]
$$

---

### Q-Learning — Apprentissage des paires état-action

$$
Q(S_t, A_t) \leftarrow (1 - \alpha) Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) \right]
$$

---

Ces équations reformulées en utilisant \(1 - \alpha\) permettent de souligner le rôle du taux d'apprentissage \(\alpha\) dans l'actualisation des valeurs tout en conservant une partie de la valeur précédente.

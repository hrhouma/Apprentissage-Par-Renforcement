
## TD(2)

$$V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha [ R_{t+1} + \gamma R_{t+2} + \gamma^2 V(S_{t+2}) ]$$

## TD(3)

$$V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha [ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 V(S_{t+3}) ]$$

## TD(4)

$$V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha [ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 R_{t+4} + \gamma^4 V(S_{t+4}) ]$$

## TD(n) - Généralisation

$$V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha [ \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} + \gamma^n V(S_{t+n}) ]$$

Dans ces équations :

- $V(S_t)$ est la valeur estimée de l'état actuel
- $\alpha$ est le taux d'apprentissage
- $R_{t+k}$ est la récompense reçue k pas dans le futur
- $\gamma$ est le facteur d'actualisation
- $V(S_{t+n})$ est la valeur estimée de l'état n pas dans le futur

La méthode TD(n) utilise les n prochaines récompenses et la valeur estimée de l'état n pas plus loin pour mettre à jour la valeur de l'état actuel. Plus n est grand, plus la méthode prend en compte d'informations futures, ce qui peut améliorer la précision mais augmente aussi la variance des estimations.


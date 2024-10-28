Le **Q-Learning** utilise la stratégie **Off-policy**.

### Pourquoi Q-Learning est Off-policy ?

En Q-Learning, l’agent peut **apprendre une stratégie optimale** en observant toutes les actions possibles dans un état donné, sans se limiter à celles qu'il suit actuellement. Même si l’agent suit une stratégie spécifique pendant son apprentissage, il utilise les **meilleures actions théoriques (actions optimales)** pour mettre à jour ses valeurs Q, indépendamment de sa politique actuelle.

### Expliqué simplement :

Imagine qu’au lieu de jouer toujours de la même façon, tu regardes **toutes les meilleures actions possibles** à chaque tour pour choisir la meilleure stratégie à long terme. Par exemple, même si tu décides parfois de ne pas avancer de trois cases, tu **considères cette action parmi toutes les autres** pour voir si elle t'apporterait plus de succès globalement.

Ainsi, Q-Learning :
- **Observe et apprend des actions optimales possibles** (pas seulement celles suivies en ce moment).
- **Permet d’améliorer la stratégie finale** en se basant sur ce qui pourrait être la meilleure option pour chaque état, même si l’agent ne l’utilise pas tout de suite.

C’est pour cette raison que **Q-Learning est une méthode Off-policy**.

# Partie 2

- Il est à noter que les termes **stochastique** et **non-déterministe** ne sont pas exactement des synonymes, bien qu'ils puissent parfois se chevaucher.
- Voici un tableau qui clarifie les **équivalences** et les **différences** entre ces quatre termes.

# Table des équivalences et différences :

| **Terme**          | **Équivaut à**                                   | **Diffère de**                         | **Explication**                                                                                   |
|--------------------|-------------------------------------------------|---------------------------------------|---------------------------------------------------------------------------------------------------|
| **Stochastique**    | **Non-déterministe** (parfois, selon le contexte) | **Déterministe**                      | En **stochastique**, il y a une part de **hasard** ou de **probabilité** dans les résultats d'une action. Un résultat n'est pas certain à l'avance. |
| **Déterministe**    | Aucun équivalent direct                        | **Stochastique**, **Non-déterministe** | Dans un environnement **déterministe**, chaque action produit un **résultat prévisible et fixe**. Il n'y a pas d'incertitude. |
| **Dynamique**       | Aucun équivalent direct                        | **Statique**                          | Un environnement **dynamique** change ou évolue avec le temps, tandis que le **statique** reste inchangé. La dynamique n'implique pas nécessairement une incertitude. |
| **Non-déterministe**| **Stochastique** (dans certains cas)            | **Déterministe**                      | Le **non-déterminisme** implique que le résultat n'est **pas prévisible** ou que plusieurs résultats sont possibles, mais cela peut être dû à des facteurs non aléatoires (comme une complexité non résolue). Cela peut inclure le **stochastique**, mais pas toujours. |

# Explications en détail :

1. **Stochastique** = **Non-déterministe** ?
   - Ils peuvent être équivalents dans certains contextes, mais ce n'est pas toujours le cas.
   - Un **environnement stochastique** implique que les résultats d'une action sont influencés par des **probabilités** ou du **hasard**. Par exemple, lancer un dé.
   - Un **environnement non-déterministe**, en revanche, signifie simplement que l'issue d'une action **n'est pas certaine** ou qu'il y a plusieurs résultats possibles, mais cela ne signifie pas nécessairement que le hasard est en jeu. Par exemple, dans un algorithme non-déterministe, plusieurs chemins peuvent mener à différents résultats sans qu'il y ait du hasard.

2. **Déterministe** ≠ **Stochastique** ou **Non-déterministe** :
   - Un environnement **déterministe** est celui où chaque action a un **résultat certain et prévisible**. Il n'y a **aucune incertitude**.
   - En revanche, dans un environnement **non-déterministe** ou **stochastique**, les résultats peuvent varier d'une fois à l'autre, soit à cause de l'aléatoire (stochastique), soit à cause de l'**ambiguïté** ou de la **complexité** (non-déterministe).

3. **Dynamique** et **Statique** ne sont pas directement liés à la notion de stochastique ou déterministe :
   - Un **environnement dynamique** change au fil du temps, alors qu'un **environnement statique** ne change pas.
   - Ces deux termes sont **orthogonaux** (indépendants) des termes stochastique et déterministe. Par exemple, un environnement dynamique peut être **stochastique** (il change et les résultats sont aléatoires) ou **déterministe** (il change, mais les résultats sont toujours prévisibles).

# Pour résumer les relations :
- **Stochastique** est un type de **non-déterminisme**, car il introduit de l'aléatoire, mais **non-déterministe** peut aussi inclure des environnements où le résultat est imprévisible sans être aléatoire (comme un problème très complexe).
- **Déterministe** est le contraire de **stochastique** et **non-déterministe**, car il implique un **résultat prévisible** à chaque fois.
- **Dynamique** décrit un environnement en changement, qui peut être **stochastique** (changement imprévisible) ou **déterministe** (changement régulier mais prévisible).

En bref, **stochastique** et **non-déterministe** ne sont pas toujours synonymes, mais ils se recoupent dans certains contextes. Les environnements **déterministes** sont toujours opposés aux deux, et la dimension **dynamique** est indépendante des notions de déterminisme et de hasard.


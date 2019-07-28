# Ensembles de Mandelbrot et Julia
`Difficulté : Moyenne à difficile`  
`Prérequis : les listes`

Nous allons présenter sur cette page les ensembles de Mandelbrot et Julia. 

Cette activité peut faire suite à l'étude de la suite logistique qu'on peut trouver [ici](https://tech.io/playgrounds/17176/recueil-dexercices-pour-apprendre-python-au-lycee/suite-logistique-et-chaos). En effet, nous allons présenter les ensembles de Mandelbrot et Julia en partant de la fonction logistique $`f(x)=\mu x(1-x)`$ (ce qui n'est pas la définition classique).

## Introduction des complexes pour l'activité :

Pour étudier ces ensembles, nous avons besoin des nombres complexes. Comme ils ne sont plus dans les programmes de lycées que pour dans une option et que nous ne les manipulons finalement que peu ici, je vais en faire une très brève présentation pour pouvoir quand même tout faire sans les connaitre avant :

Dans le plan, chaque point peut être repéré par ses coordonées (x,y). A ces coordonnées, on peut associer un nombre qu'on appellera complexe (pas parce qu'il est compliqué mais parce qu'il est composé de deux nombres réels) et qu'on notera $`x + yi`$. Tous les calculs se font comme d'habitude avec une lettre à un détail près : $`i^2 = -1`$.

> Exemple : (2 + 3i) + (4-i) = 6 + 2i  
(2+3i)*(4-i) = 8 + 12i -2i -3i² = 8 +10i -3*(-1) = 11 + 10i

Cela nous permet de définir dans un certain sens, l'addition et la multiplication de points du plan.

En python, pour obtenir le nombre complexe associé à un point, il suffit d'ecrire `complex(x,y)`.  
Inversement, si on a un nombre complexe z, l'abscisse du point associé s'obtient en écrivant `z.real` et son ordonnée `z.imag`.  
Autre fonction qui va nous servir : pour obtenir la distance entre notre point et l'origine O du repère quand on connait son nombre complexe associé z, il suffit de taper `abs(z)`. Cela nous permettra de savoir quand un point s'eloigne trop.


## La suite logistique version complexe
`Difficulté : Moyenne`

Comme pour la suite logistique, nous allons nous intéressé à la suite $`u_{n+1} = \mu u_n(1-u_n)`$ et $`u_0=0.5`$ mais cette fois-ci, au lieu de se restreindre au cas où $`\mu\in [2;4]`$, nous allons prendre pour $`\mu`$ des valeurs complexes.

Nous allons observer graphiquement l'évolution de cette suite en fonction de $`\mu`$.

Dans un premier temps, créer une fonction `u(mu,n)` qui donne la liste des termes de la suite de $`u_0`$ jusqu'à $`u_n`$.

Dans un deuxième temps, compléter la fonction `dessiner(mu,n)` qui place les points associés aux nombres complexes $`u_0`$ jusqu'à $`u_n`$ (on pourra les relier pour voir l'évolution).

> Remarque : Seules les valeurs de la suite seront vérifiées.

@[Visualisation de la suite]({"stubs": ["TP/logistique_complexe_graphique.py"], "command": "python3 TP/logistique_complexe_graphique_Test.py"})

---

## Ensemble de Mandelbrot

Comme on peut le voir sur les graphiques précédents et comme dans le cas de la suite logistique classique, selon la valeur de $`\mu`$, la suite va converger ou osciller ou bien s'éloigner vers l'infini (comme on commence à le voir sur le quatrième graphique).

On va maintenant s'intéresser aux suites qui s'éloignent vers l'infini. Pour pouvoir déterminer si une suite tend vers l'infini ou pas, on va calculer ses termes jusqu'à $`u_{200}`$ et on va estimer que si la distance à l'origine d'un des termes dépasse 1000, alors la suite tend vers l'infini.

Créer une fonction `Mandelbrot(mu)` qui renvoie le rang du premier terme de la suite dont la distance à l'origine est supérieure à 1000. Si quand on a calculé $`u_{200}`$, la distance à l'origine n'a jamais dépassé 1000 alors on renvoie 200. 

> Indication : Il vaut mieux s'inspirer de la fonction `u(mu,n)` pour créer la fonction `Mandelbrot(mu)` que chercher à l'utiliser (pour éviter trop de calculs inutiles car il va falloir calculer vite pour afficher l'image prévue)

> Remarque : Si tous les tests sont validés, vous verrez apparaitre l'ensemble de Mandelbrot où on a simplement pour chaque point (qui représente $`\mu`$) associé une couleur au nombre renvoyé par la fonction `Mandelbrot(mu)`. En noir ce sont les points tels que la suite ne semble pas s'eloigner à l'infini. C'est un exemple de courbe dite fractale car elle est formée de partie qui sont une réplique exacte du tout (Comme la vache qui rit qui a une boucle d'oreille dans laquelle on revoit la vache qui rit qui a une boucle d'oreille ...).

@[Ensemble de Mandelbrot]({"stubs": ["TP/mandelbrot.py"], "command": "python3 TP/mandelbrot_Test.py"})

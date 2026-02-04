On a ici une épreuve de Bernoulli qui s'intéresse à la probabilité de drop une clé antique à la fin du donjon de Frigoria. Cette épreuve a 2 issues :
- Le succès S "la clé est drop" de probabilité p = 0.005
- L'échec S barre (de probabilité 1 - S)
L'épreuve est répétée n fois de manière identique et indépendante (précision importante)
On a donc une variable aléatoire X qui compte le nombre de succès et qui suit la loi binomiale de paramètre n et p = 0.005

On cherche P(X ≥ 1), soit la probabilité qu'au moins une clé antique soit obtenue, en fonction de n (le nombre d'essais)

P(X ≥ 1) = 1 - P(X = 0) # Autrement dit, la probabilité qu'on ne trouve pas aucune clé antique
		=  $1 - \binom{n}{0} * 0.005^0 * (1 - 0.005)^n$  # la formule exacte de p parmi n est n!/(p!(n - p!)), mais 0 parmi n'importe quel nombre vaut 1
		= $1 - 1 * 1 * 0.995^n$
		= $1 - 0.995^n$

On va donc chercher P(X ≥ 1) ≥ 0.9 (le nombre minimal d'essais pour que la probabilité de drop soit au moins égale à 90%)
On peut écrire un programme en python qui va nous donner le résultat en utilisant la formule trouvée plus haut :
```py
n = 1 # n est le nombre d'essais
while 1 - 0.995**n < 0.9: # la formule trouvée plus haut écrite en python (1 - 0.995^n) ≥ 0.9
	n+=1 # on ajoute 1 à n
print(n) # on affiche le résultat
```

Le programme nous donne comme résultat 460 essais minimum pour avoir plus de 90% de chances de drop la clé antique

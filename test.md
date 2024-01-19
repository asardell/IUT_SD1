# TD1

## Exerice 1 -  Fonctions usuelles

### Mémo
| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `c()` | Concatène des vecteurs ou des valeurs pour créer un nouveau vecteur. |  | `nouveaux_vecteur <- c(vecteur1, vecteur2)` |
| `seq()` | Génère une séquence de nombres. | `from`, `to`, `by` spécifiant le début, la fin et l'incrément. | `sequence <- seq(1, 10, by = 2)` |
| `rep()` | Répète les éléments d'un vecteur plusieurs fois. | `times` spécifiant le nombre de répétitions. | `replication <- rep(5, times = 5)` |
| `length()` | Retourne la longueur d'un vecteur. |  | `longueur <- length(vecteur)` |
| `unique()` | Retourne les valeurs uniques d'un vecteur. |  | `valeurs_uniques <- unique(vecteur)` |
| `mean()` | Calcule la moyenne des éléments d'un vecteur. || `moyenne <- mean(vecteur)` |
| `class()` | Retourne le type de classe d'un objet. |  | `type_classe <- class(objet)` |
| `rm()` | Supprime des objets (variables ou fonctions) de l'environnement. | | `rm(objet1, objet2)` |
| `sum()` | Calcule la somme des éléments d'un vecteur. | | `somme <- sum(vecteur)` |


### Exerice sur les Fonctions en R

#### `c()`, `seq()`, `rep()`, `length()`, `unique()`

1. Créez un nouveau vecteur en utilisant la fonction `c()` avec deux vecteurs existants.
<details>
<summary>Correction</summary>

```r
nouveau_vecteur <- c(vecteur1, vecteur2)
```
</details>

2. Générez une séquence de nombres de 1 à 20 avec un incrément de 3 en utilisant la fonction `seq()`.
<details>
<summary>Correction</summary>

```r
sequence <- seq(1, 20, by = 3)
```
</details>

3. Répétez les éléments du vecteur [2, 4, 6] cinq fois en utilisant la fonction `rep()`.
<details>
<summary>Correction</summary>

```r
replication <- rep(c(2, 4, 6), times = 5)
```
</details>

4. Trouvez la longueur du vecteur [10, 20, 30, 40] en utilisant la fonction `length()`.
<details>
<summary>Correction</summary>

```r
longueur <- length(c(10, 20, 30, 40))
```
</details>

5. Créez un vecteur contenant les valeurs uniques du vecteur [1, 2, 2, 3, 3, 3] en utilisant la fonction `unique()`.
<details>
<summary>Correction</summary>

```r
valeurs_uniques <- unique(c(1, 2, 2, 3, 3, 3))
```
</details>

#### `mean()`, `class()`, `rm()`, `sum()`

6. Calculez la moyenne du vecteur [5, 10, 15, 20] en utilisant la fonction `mean()`.
<details>
<summary>Correction</summary>

```r
moyenne <- mean(c(5, 10, 15, 20))
```
</details>

7. Obtenez le type de classe de l'objet "data_frame" en utilisant la fonction `class()`.
<details>
<summary>Correction</summary>

```r
type_classe <- class(data_frame)
```
</details>

8. Supprimez les objets "variable1" et "variable2" de l'environnement en utilisant la fonction `rm()`.
<details>
<summary>Correction</summary>

```r
rm(variable1, variable2)
```
</details>

9. Calculez la somme des éléments du vecteur [2, 4, 6, 8] en utilisant la fonction `sum()`.
<details>
<summary>Correction</summary>

```r
somme <- sum(c(2, 4, 6, 8))
```
</details>

#### Combinaison des fonctions

10. Créez un nouveau vecteur en concaténant les vecteurs [1, 2] et [3, 4] avec la fonction `c()`.
<details>
<summary>Correction</summary>

```r
nouveau_vecteur <- c(1, 2, 3, 4)
```
</details>

11. Générez une séquence de nombres de 5 à 50 avec un incrément de 5, puis répétez-la trois fois.
<details>
<summary>Correction</summary>

```r
sequence <- seq(5, 50, by = 5)
repetition <- rep(sequence, times = 3)
```
</details>

12. Créez un vecteur contenant uniquement les valeurs uniques du vecteur [1, 2, 3, 2, 4, 5] en utilisant `c()` et `unique()`.
<details>
<summary>Correction</summary>

```r
valeurs_uniques <- unique(c(1, 2, 3, 2, 4, 5))
```
</details>

13. Supprimez tous les objets de l'environnement qui ont le type de classe "character".
<details>
<summary>Correction</summary>

```r
objets_a_supprimer <- ls(pattern = "character")
rm(list = objets_a_supprimer)
```
</details>

14. Calculez la moyenne et la somme des éléments du vecteur [10, 20, 30, 40, 50].
<details>
<summary>Correction</summary>

```r
moyenne <- mean(c(10, 20, 30, 40, 50))
somme <- sum(c(10, 20, 30, 40, 50))
```
</details>

#### Utilisation avancée

15. Créez une séquence décroissante de -10 à -1 avec un incrément de 1.
<details>
<summary>Correction</summary>

```r
sequence_decroissante <- seq(-10, -1, by = 1)
```
</details>

16. Générez une séquence de nombres de 0 à 1 avec un incrément de 0.1.
<details>
<summary>Correction</summary>

```r
sequence <- seq(0, 1, by = 0.1)
```
</details>

17. Répétez les éléments du vecteur [1, 2, 3] deux fois, puis créez une séquence de 1 à 6.
<details>
<summary>Correction</summary>

```r
repetition <- rep(c(1, 2, 3), times = 2)
sequence <- seq(1, 6, by = 1)
```
</details>

18. Calculez la longueur d'une séquence de nombres de 5 à 100 avec un incrément de 10.
<details>
<summary>Correction</summary>

```r
longueur <- length(seq(5, 100, by = 10))
```
</details>

19. Créez un vecteur contenant les valeurs uniques du vecteur [3, 3, 2, 1, 1, 4, 4].
<details>
<summary>Correction</summary>

```r
valeurs_uniques <- unique(c(3, 3, 2, 1, 1, 4, 4))
```
</details>

## Exerice 2 -  Fonctions statistique et simulation

### Mémo

| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `mean()` | Calcule la moyenne des éléments d'un vecteur. || `moyenne <- mean(vecteur)` |
| `median()` | Calcule la médiane d'un vecteur. | | `mediane <- median(vecteur)` |
| `min()` | Retourne la valeur minimale d'un vecteur. |  | `minimum <- min(vecteur)` |
| `max()` | Retourne la valeur maximale d'un vecteur. |  | `maximum <- max(vecteur)` |
| `sd()` | Calcule l'écart type d'un vecteur. |  | `ecart_type <- sd(vecteur)` |
| `var()` | Calcule la variance d'un vecteur. |  | `variance <- var(vecteur)` |
| `quantile()` | Calcule les quantiles d'un vecteur. | `x` : le vecteur pour lequel calculer les quantiles. `probs` : les quantiles à calculer (par exemple, c(0.25, 0.5, 0.75)). | `quantiles <- quantile(vecteur, probs = c(0.25, 0.5, 0.75))` |
| `cor()` | Calcule le coefficient de corrélation entre deux vecteurs. | `x`, `y` : les deux vecteurs pour lesquels calculer la corrélation. `method` : méthode de calcul de la corrélation (par défaut "pearson"). | `correlation <- cor(vecteur1, vecteur2, method = "pearson")` |

### Exerice sur les Fonctions en R

#### `mean()`, `median()`, `min()`, `max()`

1. Calculez la moyenne des éléments du vecteur [12, 18, 25, 30] en utilisant la fonction `mean()`.
<details>
<summary>Correction</summary>

```r
moyenne <- mean(c(12, 18, 25, 30))
```
</details>

2. Calculez la médiane du vecteur [5, 10, 15, 20, 25] en utilisant la fonction `median()`.
<details>
<summary>Correction</summary>

```r
mediane <- median(c(5, 10, 15, 20, 25))
```
</details>

3. Trouvez la valeur minimale du vecteur [8, 15, 7, 21] en utilisant la fonction `min()`.
<details>
<summary>Correction</summary>

```r
minimum <- min(c(8, 15, 7, 21))
```
</details>

4. Obtenez la valeur maximale du vecteur [3, 9, 14, 12] en utilisant la fonction `max()`.
<details>
<summary>Correction</summary>

```r
maximum <- max(c(3, 9, 14, 12))
```
</details>

#### `sd()`, `var()`

5. Calculez l'écart type des éléments du vecteur [18, 22, 15, 28] en utilisant la fonction `sd()`.
<details>
<summary>Correction</summary>

```r
ecart_type <- sd(c(18, 22, 15, 28))
```
</details>

6. Calculez la variance du vecteur [7, 14, 21, 28] en utilisant la fonction `var()`.
<details>
<summary>Correction</summary>

```r
variance <- var(c(7, 14, 21, 28))
```
</details>

#### `quantile()`

7. Calculez les quantiles à 10%, 30%, et 60% du vecteur [5, 10, 15, 20, 25] en utilisant la fonction `quantile()`.
<details>
<summary>Correction</summary>

```r
quantiles <- quantile(c(5, 10, 15, 20, 25), probs = c(0.1, 0.3, 0.6))
```
</details>

## Fonction `cor()`

8. Calculez le coefficient de corrélation entre deux vecteurs [2, 4, 6, 8] et [1, 3, 5, 7] en utilisant la fonction `cor()`.
<details>
<summary>Correction</summary>

```r
correlation <- cor(c(2, 4, 6, 8), c(1, 3, 5, 7))
```
</details>

#### Exercices Combinés

9. Créez un nouveau vecteur en concaténant les vecteurs [1, 2, 3] et [4, 5, 6], puis calculez la moyenne.
<details>
<summary>Correction</summary>

```r
nouveau_vecteur <- c(1, 2, 3, 4, 5, 6)
moyenne_combinee <- mean(nouveau_vecteur)
```
</details>

10. Générez une séquence de nombres de 5 à 50 avec un incrément de 5, puis trouvez la médiane.
<details>
<summary>Correction</summary>

```r
sequence <- seq(5, 50, by = 5)
mediane_combinee <- median(sequence)
```
</details>

11. Répétez les éléments du vecteur [2, 4, 6] trois fois, puis calculez la somme.
<details>
<summary>Correction</summary>

```r
repetition <- rep(c(2, 4, 6), times = 3)
somme_combinee <- sum(repetition)
```
</details>

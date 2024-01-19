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


### Questions

Consignes :
Créez et manipulez des vecteurs en utilisant les fonctions de base en R. Utilisez les fonctions `c()`, `length()`, `unique()`, `mean()`, et d'autres fonctions de statistiques univariées.

1. Créez un vecteur nommé 'nombres' contenant les nombres 3, 7, 11, 15, 19.

<details>
<summary>Correction</summary>

```r 
nombres <- c(3, 7, 11, 15, 19)
```
</details>

2. Créez un vecteur nommé 'lettres' contenant les lettres 'a', 'c', 'e', 'g', 'i'.
<details>
<summary>Correction</summary>

```r
lettres <- c('a', 'c', 'e', 'g', 'i')
```
</details>

3. Concaténez les vecteurs 'nombres' et 'lettres' pour créer un vecteur 'mixte'.
<details>
<summary>Correction</summary>

```r
mixte <- c(nombres, lettres)
```
</details>

4. Trouvez la longueur du vecteur 'mixte' en utilisant la fonction `length()`.
<details>
<summary>Correction</summary>

```r
longueur_mixte <- length(mixte)
```
</details>

5. Créez un vecteur 'pairs' contenant les nombres pairs de 2 à 10.
<details>
<summary>Correction</summary>

```r
pairs <- seq(2, 10, by = 2)
```
</details>

6. Créez un vecteur 'replication' contenant la répétition du nombre 5 cinq fois.
<details>
<summary>Correction</summary>

```r
replication <- rep(5, times = 5)
```
</details>

7. Créez un vecteur 'sequence' contenant une séquence de 1 à 10 avec un pas de 2.
<details>
<summary>Correction</summary>

```r
sequence <- seq(1, 10, by = 2)
```
</details>

8. Trouvez les valeurs uniques dans le vecteur 'sequence' en utilisant la fonction `unique()`.
<details>
<summary>Correction</summary>

```r
valeurs_uniques <- unique(sequence)
```
</details>

9.  Calculez la moyenne des éléments du vecteur 'nombres' en utilisant la fonction `mean()`.
<details>
<summary>Correction</summary>

```r
moyenne_nombres <- mean(nombres)
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
| `sample()` | Sélectionne un échantillon aléatoire à partir d'un vecteur. | `x` : vecteur à partir duquel échantillonner. `size` : taille de l'échantillon. | `echantillon <- sample(vecteur, size = 3)` |
| `rnorm()` | Génère des échantillons aléatoires suivant une distribution normale. | `n` : nombre d'échantillons à générer. `mean` : moyenne de la distribution. `sd` : écart-type de la distribution. | `echantillon <- rnorm(100, mean = 10, sd = 2)` |
| `runif()` | Génère des échantillons aléatoires suivant une distribution uniforme. | `n` : nombre d'échantillons à générer. `min` : valeur minimale de la distribution. `max` : valeur maximale de la distribution. | `echantillon <- runif(50, min = 0, max = 1)` |
| `cor()` | Calcule le coefficient de corrélation entre deux vecteurs. | `x`, `y` : les deux vecteurs pour lesquels calculer la corrélation. `method` : méthode de calcul de la corrélation (par défaut "pearson"). | `correlation <- cor(vecteur1, vecteur2, method = "pearson")` |


# Exercices sur les Fonctions en R

## `c()`, `seq()`, `rep()`, `length()`, `unique()`

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

## `mean()`, `class()`, `rm()`, `sum()`

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

## Combinaison des fonctions

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

## Utilisation avancée

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

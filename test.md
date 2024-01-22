# TD1

1. [TD1](#td1)
   1. [Exerice 1 -  Fonctions usuelles](#exerice-1----fonctions-usuelles)
      1. [Mémo](#mémo)
      2. [Exerice sur les Fonctions en R](#exerice-sur-les-fonctions-en-r)
         1. [`c()`](#c)
         2. [`c()`, `seq()`, `length()`](#c-seq-length)
         3. [`c()`, `rep()`](#c-rep)
         4. [`rm()`](#rm)
   2. [Exerice 2 -  Fonctions statistique univariées et simulation](#exerice-2----fonctions-statistique-univariées-et-simulation)
      1. [Mémo](#mémo-1)
      2. [Exerice sur les Fonctions en R](#exerice-sur-les-fonctions-en-r-1)
         1. [`mean()`, `median()`, `min()`, `max()`](#mean-median-min-max)
         2. [`sd()`, `var()`](#sd-var)
         3. [`quantile()`](#quantile)
         4. [`cor()`](#cor)
         5. [Exercices Combinés](#exercices-combinés)
2. [type de vecteur](#type-de-vecteur)
3. [indexation](#indexation)


## Exerice 1 -  Fonctions usuelles

### Mémo
| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `c()` | Concatène des vecteurs ou des valeurs pour créer un nouveau vecteur. |  | `nouveaux_vecteur <- c(vecteur1, vecteur2)` |
| `seq()` | Génère une séquence de nombres. | `from`, `to`, `by` spécifiant le début, la fin et l'incrément. | `sequence <- seq(1, 10, by = 2)` |
| `rep()` | Répète les éléments d'un vecteur plusieurs fois. | `times` spécifiant le nombre de répétitions. | `replication <- rep(5, times = 5)` |
| `length()` | Retourne la longueur d'un vecteur. |  | `longueur <- length(vecteur)` |
| `class()` | Retourne le type de classe d'un objet. |  | `type_classe <- class(objet)` |
| `rm()` | Supprime des objets (variables ou fonctions) de l'environnement. | | `rm(objet1, objet2)` |


### Exerice sur les Fonctions en R


#### `c()`

1. Créer un vecteur numérique de nombres de 1 à 5 et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1, 2, 3, 4, 5)
class_vecteur <- class(vecteur)
```
</details>


1. Créer un vecteur `v1` avec les nombres de 1 à 5.
<details>
<summary>Correction</summary>

```r
v1 <- 1:5

2. Ensuite, créer un vecteur `v2` en ajoutant 3 à chaque élément de `v1`.
<details>
<summary>Correction</summary>

```r
v2 <- v1 + 3
```
</details>

3. Créer un vecteur `v3` avec les nombres de 1 à 6.
<details>
<summary>Correction</summary>

```r
v3 <- 1:6
```
</details>

4. Ensuite, créer un vecteur `v4` avec les carrés de chaque élément de `v3`.
<details>
<summary>Correction</summary>

```r
v4 <- v3^2
```
</details>

5. Ensuite, créer un vecteur `v5` en divisant chaque élément de `v4` par 2.
<details>
<summary>Correction</summary>

```r
v5 <- v4 / 2
```
</details>

2. Créer un vecteur caractère avec les jours de la semaine et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche")
class_vecteur <- class(vecteur)
```
</details>

3. Créer un vecteur avec des valeurs booléennesafficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(TRUE, FALSE, TRUE, FALSE, TRUE)
class_vecteur <- class(vecteur)
```
</details>

4. Créer un vecteur numérique contenant des nombres décimaux et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1.2, 2.5, 3.8, 4.1, 5.6)
class_vecteur <- class(vecteur)
```
</details>

5. Créer un vecteur caractère avec le nom des mois et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Janvier", "Février", "Mars", "Avril", "Mai", "Juin", "Juillet", "Août", "Septembre", "Octobre", "Novembre", "Décembre")
class_vecteur <- class(vecteur)
```
</details>


7. Créer un vecteur numérique avec des nombres négatifs et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(-1, -2, -3, -4, -5)
class_vecteur <- class(vecteur)
```
</details>

8. Créer un vecteur caractère contenant des noms de fruits et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Pomme", "Banane", "Orange", "Fraise", "Ananas")
class_vecteur <- class(vecteur)
```
</details>


10. Créer un vecteur numérique avec des valeurs manquantes (NA) et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1, 2, NA, 4, 5)
class_vecteur <- class(vecteur)
```
</details>


#### `c()`, `seq()`, `length()`


1. Créer une séquence de nombres de 1 à 10 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 1, to = 10)
lenght(seq)
```
</details>

2. Générer une séquence de nombres pairs de 2 à 20 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 2, to = 20, by = 2)
lenght(seq)
```
</details>

1. Créer une séquence décroissante de 0 à -5 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 0, to = -5)
lenght(seq)
```
</details>

1. Générer une séquence de nombres de 5 à 50 avec un pas de 5 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 5, to = 50, by = 5)
lenght(seq)
```
</details>

1. Créer une séquence de 10 à 1 en ordre décroissant puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 10, to = 1, by = -1)
lenght(seq)
```
</details>

1. Générer une séquence de nombres de 0 à 1 avec un pas de 0.1 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 0, to = 1, by = 0.1)
lenght(seq)
```
</details>

1. Générer une séquence de 5 à -5 avec un pas de -1 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 5, to = -5, by = -1)
lenght(seq)
```
</details>

1.  Générer une séquence de 1 à 10 avec seulement les nombres impairs puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 1, to = 10, by = 2)
lenght(seq)
```
</details>


#### `c()`, `rep()`

1. Répéter le nombre 3 cinq fois et stocker le résultat dans un vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(3, times = 5)
```
</details>

1. Créer un vecteur répétant les lettres 'A', 'B', 'C' trois fois chacune.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(c('A', 'B', 'C'), times = 3)
```
</details>

1. Répéter la séquence de nombres de 1 à 3 trois fois et stocker le résultat dans un vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(1:3, times = 3)
```
</details>

1. Créer un vecteur répétant les valeurs TRUE et FALSE quatre fois chacune.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(c(TRUE, FALSE), times = 4)
```
</details>

#### `rm()`

1. Utiliser la fonction rm pour supprimer les objets des questions précédentes.
<details>
<summary>Correction</summary>

```r
rm(vecteur)
```
</details>


## Exerice 2 -  Fonctions statistique univariées et simulation

### Mémo

| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `sum()` | Calcule la somme des éléments d'un vecteur. | | `somme <- sum(vecteur)` |
| `mean()` | Calcule la moyenne des éléments d'un vecteur. || `moyenne <- mean(vecteur)` |
| `median()` | Calcule la médiane d'un vecteur. | | `mediane <- median(vecteur)` |
| `min()` | Retourne la valeur minimale d'un vecteur. |  | `minimum <- min(vecteur)` |
| `max()` | Retourne la valeur maximale d'un vecteur. |  | `maximum <- max(vecteur)` |
| `sd()` | Calcule l'écart type d'un vecteur. |  | `ecart_type <- sd(vecteur)` |
| `var()` | Calcule la variance d'un vecteur. |  | `variance <- var(vecteur)` |
| `quantile()` | Calcule les quantiles d'un vecteur. | `x` : le vecteur pour lequel calculer les quantiles. `probs` : les quantiles à calculer (par exemple, c(0.25, 0.5, 0.75)). | `quantiles <- quantile(vecteur, probs = c(0.25, 0.5, 0.75))` |
| `sort()` | Trie les éléments d'un vecteur ou d'une matrice. | `x` : le vecteur ou la matrice à trier. `decreasing` : un booléen indiquant si le tri doit être effectué par ordre décroissant (par défaut, `FALSE`). | `vecteur_tri <- sort(vecteur)` |
| `unique()` | Retourne les valeurs uniques d'un vecteur. |  | `valeurs_uniques <- unique(vecteur)` |
| `round()` | Arrondit les nombres d'un vecteur à un nombre spécifié de décimales. | `x` : le vecteur à arrondir. `digits` : nombre de décimales (par défaut 0). | `arrondi <- round(3.14159, digits = 2)` |
| `abs()` | Calcule la valeur absolue des éléments d'un vecteur. | | `valeurs_absolues <- abs(vecteur)` |
| `table()` | Construit une table de fréquences pour un vecteur ou une combinaison de vecteurs. | `x` : vecteur ou combinaison de vecteurs pour lesquels construire la table. | `table_frequences <- table(vecteur)` |
| `prop.table()` | Convertit les fréquences d'une table en proportions. | `x` : la table de fréquences à convertir. `margin` : indique les marges à utiliser lors du calcul des proportions (par défaut, `NULL` signifie utiliser toutes les marges). | `proportions <- prop.table(table_frequences)` |
| `rnorm()` | Génère des échantillons aléatoires suivant une distribution normale. | `n` : nombre d'échantillons à générer. `mean` : moyenne de la distribution. `sd` : écart-type de la distribution. | `echantillon_norm <- rnorm(100, mean = 10, sd = 2)` |
| `runif()` | Génère des échantillons aléatoires suivant une distribution uniforme. | `n` : nombre d'échantillons à générer. `min` : valeur minimale de la distribution. `max` : valeur maximale de la distribution. | `echantillon_unif <- runif(50, min = 0, max = 1)` |
| `sample()` | Sélectionne un échantillon aléatoire à partir d'un vecteur. | `x` : vecteur à partir duquel échantillonner. `size` : taille de l'échantillon. | `echantillon_aleatoire <- sample(vecteur, size = 3)` |

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

#### `cor()`

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



# type de vecteur
# indexation
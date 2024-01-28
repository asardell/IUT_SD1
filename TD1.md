# TD1

## Objectifs
Voici les objectifs de ce TD :
- [ ] prendre en main le logiciel RStudio
- [ ] se familiariser avec les commandes de base de R
- [ ] utiliser des scripts et mettre des commentaires
- [ ] manipuler des vecteurs
- [ ] calculer des statistiques descriptives

1. [TD1](#td1)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Les objets et les vecteurs](#exercice-1---les-objets-et-les-vecteurs)
      1. [Mémo](#mémo)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r)
         1. [Les fonctions `c()`,  `rm()`, `print()`](#les-fonctions-c--rm-print)
   3. [Exercice 2 -  Fonctions usuelles](#exercice-2----fonctions-usuelles)
      1. [Mémo](#mémo-1)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-1)
         1. [Les fonctions `c()`,  `class`](#les-fonctions-c--class)
         2. [Les fonctions `c()`, `seq()`, `length()`](#les-fonctions-c-seq-length)
         3. [Les fonctions `c()`, `rep()`](#les-fonctions-c-rep)
         4. [La fonction `rm()`](#la-fonction-rm)
   4. [Exercice 3 -  Fonctions statistique univariées et simulation](#exercice-3----fonctions-statistique-univariées-et-simulation)
      1. [Mémo](#mémo-2)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-2)
         1. [Les fonctions `runif()`, `mean()`, `median()`, `min()`, `max()`](#les-fonctions-runif-mean-median-min-max)
         2. [Les fonctions `rnorm()`, `mean()`, `sd()`,  `hist()`, `quantile()`](#les-fonctions-rnorm-mean-sd--hist-quantile)
         3. [Les fonctions `sum()` , `round()`](#les-fonctions-sum--round)
         4. [Les fonctions `sample()`, `table()`, `prop.table()` , `unique()`, `sort()`](#les-fonctions-sample-table-proptable--unique-sort)
   5. [Comment rendre son travail ?](#comment-rendre-son-travail-)



:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_td1`

## Exercice 1 - Les objets et les vecteurs

### Mémo
| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `c()` | Concatène des vecteurs ou des valeurs pour créer un nouveau vecteur. |  | `nouveaux_vecteur <- c(vecteur1, vecteur2)` |
| `rm()` | Supprime des objets (variables ou fonctions) de l'environnement. | | `rm(objet1, objet2)` |
| `print()` | Affiche dans la console. | | `print(objet1)` |

### Exercice sur les Fonctions en R

#### Les fonctions `c()`,  `rm()`, `print()`

1. Créer un objet `a` avec la valeur `10` et un objet `b` avec la valeur `5`. 
<details>
<summary>Correction</summary>

```r
a <- 10
b <- 5
```

2. Multiplier les deux objets et stocker le résultat dans un objet `resultat`. Afficher cet objet avec la fonction  `print() `.
<details>
<summary>Correction</summary>

```r
resultat <- a * b
print(resultat)
```

3. Créer un objet `A` avec la valeur `7.2` et un objet `B` avec la valeur `10.1`. Que remarquons-nous avec les deux premiers objets ?
<details>
<summary>Correction</summary>

```r
A <- 7.2
b <- 10.1
print("Le langage R est sensible à la casse (majuscule/minuscule) car nous avons 4 objets a,b,A et B")
```

4. Additionner les deux objets `A` et  `B` puis stocker le résultat dans un objet `resultat`. Que remarquons-nous avec le précédent objet `resultat` ?
<details>
<summary>Correction</summary>

```r
resultat <- A + B
print(resultat)
print("La précédente valeur de l'object resultat a été supprimée et remplacée par la somme de A et B.")
```

5. Supprimer l'ensemble des objets des questions précédentes avec la fonction `rm()`.
<details>
<summary>Correction</summary>

```r
rm(a,A,b,B,resultat)
```

## Exercice 2 -  Fonctions usuelles

### Mémo
| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `seq()` | Génère une séquence de nombres. | `from`, `to`, `by` spécifiant le début, la fin et l'incrément. | `sequence <- seq(1, 10, by = 2)` |
| `rep()` | Répète les éléments d'un vecteur plusieurs fois. | `times` spécifiant le nombre de répétitions. | `replication <- rep(5, times = 5)` |
| `length()` | Retourne la longueur d'un vecteur. |  | `longueur <- length(vecteur)` |
| `class()` | Retourne le type de classe d'un objet. |  | `type_classe <- class(objet)` |

### Exercice sur les Fonctions en R


#### Les fonctions `c()`,  `class`

1. Créer un vecteur numérique de nombres de 1 à 5 et afficher sa classe. Afficher le troisième élément du vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1, 2, 3, 4, 5)
class(vecteur)
vecteur[3]
```
</details>


1. Créer un vecteur `v1` avec les nombres de 1 à 5.
<details>
<summary>Correction</summary>

```r
v1 <- 1:5
```
</details>

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

6. Créer un vecteur caractère avec les jours de la semaine et afficher sa classe. Afficher le 2ème et 7ème éléments du vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche")
class(vecteur)
vecteur[c(2,7)]
```
</details>

7. Créer un vecteur avec des valeurs booléennes et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(TRUE, FALSE, TRUE, FALSE, TRUE)
class(vecteur)
```
</details>

8. Créer un vecteur numérique contenant des nombres décimaux et afficher sa classe. Afficher tous les éléments sauf le 3ème.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1.2, 2.5, 3.8, 4.1, 5.6)
class(vecteur)
vecteur[-3]
```
</details>

9. Créer un vecteur caractère avec le nom des mois et afficher sa classe. Afficher les mois du premier trimestre.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Janvier", "Février", "Mars", "Avril", "Mai", "Juin", "Juillet", "Août", "Septembre", "Octobre", "Novembre", "Décembre")
class(vecteur)
vecteur[c(1,2,3)]
```
</details>


10. Créer un vecteur numérique avec des nombres négatifs et afficher sa classe. Afficher le dernier et premier éléments du vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- c(-1, -2, -3, -4, -5)
class(vecteur)
vecteur[c(5,1)]
```
</details>

11. Créer un vecteur caractère contenant des noms de fruits et afficher sa classe. Afficher tous les éléments sauf les deux premiers.
<details>
<summary>Correction</summary>

```r
vecteur <- c("Pomme", "Banane", "Orange", "Fraise", "Ananas")
class(vecteur)
vecteur[-c(1,2)]
```
</details>


12. Créer un vecteur numérique avec des valeurs manquantes (NA) et afficher sa classe.
<details>
<summary>Correction</summary>

```r
vecteur <- c(1, 2, NA, 4, 5)
class_vecteur <- class(vecteur)
```
</details>


#### Les fonctions `c()`, `seq()`, `length()`


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

3. Créer une séquence décroissante de 0 à -5 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 0, to = -5)
lenght(seq)
```
</details>

4. Générer une séquence de nombres de 5 à 50 avec un pas de 5 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 5, to = 50, by = 5)
lenght(seq)
```
</details>

5. Créer une séquence de 10 à 1 en ordre décroissant puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 10, to = 1, by = -1)
lenght(seq)
```
</details>

6. Générer une séquence de nombres de 0 à 1 avec un pas de 0.1 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 0, to = 1, by = 0.1)
lenght(seq)
```
</details>

7. Générer une séquence de 5 à -5 avec un pas de -1 puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 5, to = -5, by = -1)
lenght(seq)
```
</details>

8.  Générer une séquence de 1 à 10 avec seulement les nombres impairs puis calculer la longueur du vecteur.
<details>
<summary>Correction</summary>

```r
seq <- seq(from = 1, to = 10, by = 2)
lenght(seq)
```
</details>


#### Les fonctions `c()`, `rep()`

1. Répéter le nombre 3 cinq fois et stocker le résultat dans un vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(3, times = 5)
```
</details>

2. Créer un vecteur répétant les lettres 'A', 'B', 'C' trois fois chacune.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(c('A', 'B', 'C'), times = 3)
```
</details>

3. Répéter la séquence de nombres de 1 à 3 trois fois et stocker le résultat dans un vecteur.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(1:3, times = 3)
```
</details>

4. Créer un vecteur répétant les valeurs TRUE et FALSE quatre fois chacune.
<details>
<summary>Correction</summary>

```r
vecteur <- rep(c(TRUE, FALSE), times = 4)
```
</details>

#### La fonction `rm()`

5. Utiliser la fonction rm pour supprimer les objets des questions précédentes.
<details>
<summary>Correction</summary>

```r
rm(vecteur)
```
</details>

## Exercice 3 -  Fonctions statistique univariées et simulation

### Mémo

| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `sum()` | Calcule la somme des éléments d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `somme <- sum(vecteur)` |
| `mean()` | Calcule la moyenne des éléments d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `moyenne <- mean(vecteur)` |
| `median()` | Calcule la médiane d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `mediane <- median(vecteur)` |
| `min()` | Retourne la valeur minimale d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `minimum <- min(vecteur)` |
| `max()` | Retourne la valeur maximale d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `maximum <- max(vecteur)` |
| `sd()` | Calcule l'écart type d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `ecart_type <- sd(vecteur)` |
| `var()` | Calcule la variance d'un vecteur. | `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE).  | `variance <- var(vecteur)` |
| `quantile()` | Calcule les quantiles d'un vecteur. | `x` : le vecteur pour lequel calculer les quantiles. `probs` : les quantiles à calculer (par exemple, c(0.25, 0.5, 0.75)). `na.rm` : spécifie si les valeurs NA doivent être retirées (par défaut FALSE). | `quantiles <- quantile(vecteur, probs = c(0.25, 0.5, 0.75))` |
| `sort()` | Trie les éléments d'un vecteur ou d'une matrice. | `x` : le vecteur ou la matrice à trier. `decreasing` : un booléen indiquant si le tri doit être effectué par ordre décroissant (par défaut, `FALSE`). | `vecteur_tri <- sort(vecteur)` |
| `unique()` | Retourne les valeurs uniques d'un vecteur. |  | `valeurs_uniques <- unique(vecteur)` |
| `round()` | Arrondit les nombres d'un vecteur à un nombre spécifié de décimales. | `x` : le vecteur à arrondir. `digits` : nombre de décimales (par défaut 0). | `arrondi <- round(3.14159, digits = 2)` |
| `abs()` | Calcule la valeur absolue des éléments d'un vecteur. | | `valeurs_absolues <- abs(vecteur)` |
| `table()` | Construit une table de fréquences pour un vecteur ou une combinaison de vecteurs. | `x` : vecteur ou combinaison de vecteurs pour lesquels construire la table. | `table_frequences <- table(vecteur)` |
| `prop.table()` | Convertit les fréquences d'une table en proportions. | `x` : la table de fréquences à convertir. `margin` : indique les marges à utiliser lors du calcul des proportions (par défaut, `NULL` signifie utiliser toutes les marges). | `proportions <- prop.table(table_frequences)` |
| `rnorm()` | Génère des échantillons aléatoires suivant une distribution normale. | `n` : nombre d'échantillons à générer. `mean` : moyenne de la distribution. `sd` : écart-type de la distribution. | `echantillon_norm <- rnorm(100, mean = 10, sd = 2)` |
| `runif()` | Génère des échantillons aléatoires suivant une distribution uniforme. | `n` : nombre d'échantillons à générer. `min` : valeur minimale de la distribution. `max` : valeur maximale de la distribution. | `echantillon_unif <- runif(50, min = 0, max = 1)` |
| `sample()` | Sélectionne un échantillon aléatoire à partir d'un vecteur. | `x` : vecteur à partir duquel échantillonner. `size` : taille de l'échantillon. `replace` : avec ou sans remise.| `echantillon_aleatoire <- sample(vecteur, size = 3, replace = TRUE)` |
| `hist()` | Crée un histogramme à partir d'un vecteur de données. | `x` : le vecteur de données à utiliser. `breaks` : le nombre de bâtons (barres) dans l'histogramme. | `histogramme <- hist(data_vector, breaks = 10)` |
| `boxplot()` | Crée une boîte à moustaches à partir d'un ou plusieurs vecteurs de données. | `x` : un ou plusieurs vecteurs de données à utiliser. | `boite_moustaches <- boxplot(data_vector1, data_vector2)` |

### Exercice sur les Fonctions en R

#### Les fonctions `runif()`, `mean()`, `median()`, `min()`, `max()`

Pour chaque question, afficher le vecteur simulé et calculer les statistiques univariées à l'aide des fonctions ci-dessus.

1. Générez un vecteur de 5 nombres aléatoires compris entre 0 et 1 en utilisant la fonction `runif()`.
<details>
<summary>Correction</summary>

```r
vecteur <- runif(n = 5, min = 0, max = 1)
vecteur
mean(vecteur)
median(vecteur)
min(vecteur)
max(vecteur)
```
</details>

2. Créez une séquence de 10 nombres aléatoires compris entre -5 et 5 à l'aide de la fonction `runif()`.
<details>
<summary>Correction</summary>

```r
vecteur <- runif(n = 10, min = -5, max = 5)
vecteur
mean(vecteur)
median(vecteur)
min(vecteur)
max(vecteur)
```
</details>

3. Générez un échantillon de 100 nombres aléatoires suivant une distribution uniforme entre 10 et 20 avec `runif()`.
<details>
<summary>Correction</summary>

```r
vecteur <- runif(n = 100, min = 10, max = 20)
vecteur
mean(vecteur)
median(vecteur)
min(vecteur)
max(vecteur)
```
</details>

4. Créez une séquence de 15 nombres aléatoires compris entre 50 et 100 en utilisant `runif()`.
<details>
<summary>Correction</summary>

```r
vecteur <- runif(n= 15, min = 50, max = 100)
vecteur
mean(vecteur)
median(vecteur)
min(vecteur)
max(vecteur)
```
</details>


#### Les fonctions `rnorm()`, `mean()`, `sd()`,  `hist()`, `quantile()`

Pour chaque question, représenter graphique l'échantillon aléatoire avec un histogramme.

1. Générez un échantillon de 20 nombres aléatoires suivant une distribution normale avec une moyenne de -2 et un écart-type de 3. Calculez la moyenne et l'écart-type de cet échantillon.
<details>
<summary>Correction</summary>

```r
echantillon <- rnorm(n = 200, mean = -2, sd = 3)
moyenne <- mean(echantillon)
ecart_type <- sd(echantillon)
print(paste("Moyenne : ", moyenne))
print(paste("Écart-type : ", ecart_type))
hist(echantillon)
```
</details>

2. Générez un échantillon de 2000 nombres aléatoires suivant une distribution normale avec une moyenne de -2 et un écart-type de 3. Calculez la moyenne et l'écart-type de cet échantillon.
<details>
<summary>Correction</summary>

```r
echantillon <- rnorm(n = 2000, mean = -2, sd = 3)
moyenne <- mean(echantillon)
ecart_type <- sd(echantillon)
print(paste("Moyenne : ", moyenne))
print(paste("Écart-type : ", ecart_type))
hist(echantillon)
```
</details>

3. Générez un échantillon de 2000 nombres aléatoires suivant une distribution normale avec une moyenne de 0 et un écart-type de 1. Calculez la moyenne et l'écart-type de cet échantillon.
<details>
<summary>Correction</summary>

```r
echantillon <- rnorm(n = 2000, mean = 0, sd = 1)
moyenne <- mean(echantillon)
ecart_type <- sd(echantillon)
print(paste("Moyenne : ", moyenne))
print(paste("Écart-type : ", ecart_type))
hist(echantillon)
```
</details>

4. Calculez les quantiles à 25%, 50%, puis 75% de cet échantillon précédent.
<details>
<summary>Correction</summary>

```r
quantile(echantillon, probs = c(0.25))
quantile(echantillon, probs = c(0.50))
quantile(echantillon, probs = c(0.75))
```
</details>

5. Calculez les déciles de cet échantillon précédent.
<details>
<summary>Correction</summary>

```r
quantile(echantillon, probs = seq(0,1,0.1))
```
</details>

6. Calculez les centiles de cet échantillon précédent.
<details>
<summary>Correction</summary>

```r
quantile(echantillon, probs = seq(0,1,0.01))
```
</details>


#### Les fonctions `sum()` , `round()`

1. Générez un échantillon de 3000 salaires aléatoires suivant une distribution normale avec une moyenne de 2400€ et un écart-type de 300€. Calculez la moyenne et l'écart-type de cet échantillon.
<details>
<summary>Correction</summary>

```r
echantillon <- rnorm(n = 3000, mean = 2400, sd = 300)
moyenne <- mean(echantillon)
ecart_type <- sd(echantillon)
print(paste("Moyenne : ", moyenne))
print(paste("Écart-type : ", ecart_type))
```
</details>


2. Arrondir les salaires avec deux décimales.
<details>
<summary>Correction</summary>

```r
echantillon <- round(echantillon, 2)
```
</details>


3. Calculer la masse salariale.
<details>
<summary>Correction</summary>

```r
masse_salariale <- sum(echantillon)
print(paste("Masse salariale : ", masse_salariale))
```
</details>

4. Quel est le salaire médian ?
<details>
<summary>Correction</summary>

```r
salaire_median <- median(echantillon)
print(paste("Salaire médian : ", salaire_median))
```
</details>

5. Interpréter le quantile 99%
<details>
<summary>Correction</summary>

```r
quantile(echantillon, probs = 0.99)
```
</details>

6. Interpréter le quantile 20%
<details>
<summary>Correction</summary>

```r
quantile(echantillon, probs = 0.2)
```
</details>



#### Les fonctions `sample()`, `table()`, `prop.table()` , `unique()`, `sort()`

1. Simuler un lancé de dé avec la fonction `sample()`.
<details>
<summary>Correction</summary>

```r
sample(x = c(1,2,3,4,5,6), size = 1)
```
</details>

1. Simuler un lancé de dé 12 fois et stocker la simulation dans un vecteur appelé `simulation`.
<details>
<summary>Correction</summary>

```r
simulation <- sample(x = c(1,2,3,4,5,6), size = 12, replace = TRUE)
print(simulation)
```
</details>

3. Afficher les différentes valeurs qui sont apparues avec la fonction `unique()` .
<details>
<summary>Correction</summary>

```r
unique(simulation)
```
</details>

4. Compter le nombre d'apparition de chaque face avec la fonction `table()`. Afficher le résultat par ordre décroissant d'apparition avec la fonction `sort()`.
<details>
<summary>Correction</summary>

```r
table(simulation)
```
</details>

5. Compter le nombre d'apparition de chaque face en pourcentage avec la fonction  `prop.table()`. Théoriquement, nous devrions avoir /frac{1}{6} d'obtenir chaque face. Est-ce le cas ?
<details>
<summary>Correction</summary>

```r
prop.table( table(simulation) )
print("Non, ce n'est pas le cas")
```
</details>

6. Cette fois-ci, simuler un lancé de dé 100 000 fois et stocker la simulation dans un vecteur appelé `simulation`.
<details>
<summary>Correction</summary>

```r
simulation <- sample(x = c(1,2,3,4,5,6), size = 100000, replace = TRUE)
print(simulation)
```
</details>

7. Calculer la répartition du nombre d'apparition de chaque face en pourcentage. Afficher le résultat par ordre décroissant d'apparition avec la fonction `sort()`. La taille de cet échantillon permet-il de se rapprocher des probabilités théoriques d'obtenir chacune des faces ? 
<details>
<summary>Correction</summary>

```r
simulation <- sample(x = c(1,2,3,4,5,6), size = 100000, replace = TRUE)
frequence <- prop.table( table(simulation) )
sort(frequence, decreasing = TRUE)
print("Oui, d'après la loi des grands nombres, les probabilités d'obtenir chacune des faces se rapprochent des probabilités théoriques.")
```
</details>

## Comment rendre son travail ? 

1. Créer un compte sur GitHub.com
2. Créer un repository **public** intitulé `iut_sd1_programmation_r` en **cochant** l'ajout d'un fichier *README.md* par défaut.
3. Uploader son script dans son repository

:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_td1`
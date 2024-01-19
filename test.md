# TD1

# Les fonctions du jour

| Nom de Fonction | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `c()` | Concatène des vecteurs ou des valeurs pour créer un nouveau vecteur. | Vecteurs ou valeurs à concaténer. | `nouveaux_vecteur <- c(vecteur1, vecteur2)` |
| `seq()` | Génère une séquence de nombres. | `from`, `to`, `by` spécifiant le début, la fin et l'incrément. | `sequence <- seq(1, 10, by = 2)` |
| `rep()` | Répète les éléments d'un vecteur plusieurs fois. | `times` spécifiant le nombre de répétitions. | `replication <- rep(5, times = 5)` |
| `length()` | Retourne la longueur d'un vecteur. | Vecteur dont vous voulez connaître la longueur. | `longueur <- length(vecteur)` |
| `unique()` | Retourne les valeurs uniques d'un vecteur. | Vecteur dont vous voulez obtenir les valeurs uniques. | `valeurs_uniques <- unique(vecteur)` |
| `mean()` | Calcule la moyenne des éléments d'un vecteur. | Vecteur dont vous voulez calculer la moyenne. | `moyenne <- mean(vecteur)` |
| `min()` | Retourne la valeur minimale d'un vecteur. | Vecteur dont vous voulez trouver la valeur minimale. | `minimum <- min(vecteur)` |
| `max()` | Retourne la valeur maximale d'un vecteur. | Vecteur dont vous voulez trouver la valeur maximale. | `maximum <- max(vecteur)` |
| `sd()` | Calcule l'écart type d'un vecteur. | Vecteur dont vous voulez calculer l'écart type. | `ecart_type <- sd(vecteur)` |
| `var()` | Calcule la variance d'un vecteur. | Vecteur dont vous voulez calculer la variance. | `variance <- var(vecteur)` |
| `sample()` | Sélectionne un échantillon aléatoire à partir d'un vecteur. | `x` vecteur à partir duquel échantillonner. `size` taille de l'échantillon. | `echantillon <- sample(vecteur, size = 3)` |



# Exercice : Création de Vecteurs et Fonctions de Base en R

## Consignes :
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

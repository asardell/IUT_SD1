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

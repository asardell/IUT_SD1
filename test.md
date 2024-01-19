# Exercice : Création de Vecteurs et Fonctions de Base en R

## Consignes :
Créez et manipulez des vecteurs en utilisant les fonctions de base en R. Utilisez les fonctions `c()`, `length()`, `unique()`, `mean()`, et d'autres fonctions de statistiques univariées.

1. Créez un vecteur nommé 'nombres' contenant les nombres 3, 7, 11, 15, 19.
2. Créez un vecteur nommé 'lettres' contenant les lettres 'a', 'c', 'e', 'g', 'i'.
3. Concaténez les vecteurs 'nombres' et 'lettres' pour créer un vecteur 'mixte'.
4. Trouvez la longueur du vecteur 'mixte' en utilisant la fonction `length()`.
5. Créez un vecteur 'pairs' contenant les nombres pairs de 2 à 10.
6. Créez un vecteur 'replication' contenant la répétition du nombre 5 cinq fois.
7. Créez un vecteur 'sequence' contenant une séquence de 1 à 10 avec un pas de 2.
8. Trouvez les valeurs uniques dans le vecteur 'sequence' en utilisant la fonction `unique()`.
9. Calculez la moyenne des éléments du vecteur 'nombres' en utilisant la fonction `mean()`.

<details>
<summary>Correction</summary>

```r
# Correction

# 1.
nombres <- c(3, 7, 11, 15, 19)

# 2.
lettres <- c('a', 'c', 'e', 'g', 'i')

# 3.
mixte <- c(nombres, lettres)

# 4.
longueur_mixte <- length(mixte)

# 5.
pairs <- seq(2, 10, by = 2)

# 6.
replication <- rep(5, times = 5)

# 7.
sequence <- seq(1, 10, by = 2)

# 8.
valeurs_uniques <- unique(sequence)

# 9.
moyenne_nombres <- mean(nombres)

# TD2

<img src="./img/img1.jpg" alt="" style="height: 200px;">

## Objectifs
Voici les objectifs de ce TD :
- [ ] Importer un dataframe
- [ ] Sélection et filtre sur un dataframe
- [ ] Trier un dataframe 

La compétition de sur Mario Kart est un sport où chaque détail compte. La performance d'un kart dépend non seulement de la capacité de conduite du pilote, mais aussi de la configuration et de la composition du kart lui-même. Dans ce TD, nous allons explorer comment les données statistiques peuvent être utilisées pour optimiser la composition d'un kart, en se basant sur des [données réelles disponible ici](https://www.mariowiki.com/Mario_Kart_8_Deluxe_in-game_statistics).

:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_td2`

## Exercice 1 - Importer des données

### Mémo
| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `read.csv()` | Lit un fichier CSV et retourne un dataframe. | `file` : le chemin ou l'URL du fichier CSV à lire, `header` : spécifie si la première ligne contient les noms des variables (par défaut TRUE), `dec` : le caractère utilisé pour indiquer le point décimal (par défaut "."), `sep` : le séparateur de champ (par défaut ",", pour les tabulations `\t`). | `donnees <- read.csv("fichier.csv", header = TRUE, dec = ",", sep = ";")` |
| `getwd()` | Retourne le répertoire de travail actuel. | | `current_dir <- getwd()` |
| `setwd()` | Change le répertoire de travail actuel. | `dir` : le chemin du nouveau répertoire de travail | `setwd("/chemin/vers/le/nouveau/repertoire")` |


### Exercice sur les Fonctions en R

#### Les fonctions `getwd()`,`setwd()` et `read.csv()`.

"bodies_karts.csv", header = TRUE, sep = ";", dec = ",")
tires = read.csv(file = "tires.csv", header = TRUE, sep = "\t", dec = ",")
gliders = read.csv(file = "gliders.csv", header = TRUE, sep = "|", dec = ",")
drivers = read.csv(file = "drivers.csv",

1. Télécharger les jeux de données (`bodies_karts.csv`, `tires.csv`, `gliders.csv` et `drivers.csv`) disponible [ici](./dataset) puis les mettre dans un même dossier appelé `dataset`.


2. Afficher le répertoire courant par défaut de votre session RStudio avec la fonction `getwd()`.
<details>
<summary>Correction</summary>

```r
getwd()
```
</details>

3. Changer le répertoire courant par défaut de votre session RStudio avec la fonction `setwd()` pour pointer sur le dossier avec vos datasets. Puis vérifier le bon changement du répertoire avec la fonction `getwd()`.
<details>
<summary>Correction</summary>

```r
setwd(dir = "C:/Users/Anthony/Documents/asardell/IUT_SD1/dataset")
getwd()
```
</details>

:warning: Il est possible de faire exactement la même chose avec le raccourci clavier `CTRL` + `SHIFT` + `H`.

4. L'intérêt de changer de répertoire est de ne pas être obliger de renseigner tout le chemin d'un fichier à importer. Uniquement le nom du fichier est ainsi suffisant. Importer les datasets avec la fonction `read.csv()`.

:warning: Pensez à ouvrir le fichier avec un bloc note pour prendre connaissance de sa configuration et ainsi bien paramétrer les arguments de la fonction `read.csv()`.

<details>
<summary>Correction</summary>

```r
bodies_karts = read.csv(file = "bodies_karts.csv", header = TRUE, sep = ";", dec = ",")
tires = read.csv(file = "tires.csv", header = TRUE, sep = "\t", dec = ",")
gliders = read.csv(file = "gliders.csv", header = TRUE, sep = "|", dec = ",")
drivers = read.csv(file = "drivers.csv", header = TRUE, sep = ";", dec = ",")
```
</details>


...


## Exercice 2 - Statistique



### Exercice sur les Fonctions en R

1. xxxxx

<details>
<summary>Correction</summary>

```r
```
</details>

## Exercice 3 - Manipulation de data frame

### Mémo
| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `order()` | Trie les éléments d'un vecteur et retourne les indices dans l'ordre croissant ou décroissant. | `x` : le vecteur à trier, `decreasing` : spécifie si le tri doit être effectué dans l'ordre décroissant (par défaut FALSE). | `indices_tri <- order(vecteur, decreasing = FALSE)` |
| `[ , ]` | Indexe un dataframe au niveau des lignes et des colonnes. | `row_index` : index ou condition pour sélectionner les lignes, `col_index` : index ou noms de colonnes pour sélectionner les colonnes. | `donnees_subset <- donnees[1:10, c("colonne1", "colonne2")]` |
| `[ - , ]` | Indexation inverse, exclut les lignes ou colonnes spécifiées. | `row_index` : index ou condition pour exclure les lignes, `col_index` : index ou noms de colonnes pour exclure les colonnes. | `donnees_sans_colonne3 <- donnees[, -3]` |

### Exercice sur les Fonctions en R

1. xxxxx

<details>
<summary>Correction</summary>

```r
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




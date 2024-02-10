# TP1

![]("./img/img1.jpg")

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

1. Afficher le répertoire courant par défaut de votre session RStudio avec la fonction `getwd()`.
<details>
<summary>Correction</summary>

```r
getwd()
```
</details>

2. Changer le répertoire courant par défaut de votre session RStudio avec la fonction `setwd()` pour pointer sur le dossier avec vos datasets. Puis vérifier le bon changement du répertoire avec la fonction `getwd()`.
<details>
<summary>Correction</summary>

```r
setwd(dir = "C:/Users/Anthony/Documents/asardell/IUT_SD1/dataset")
getwd()
```
</details>

:warning: Il est possible de faire exactement la même chose avec le raccourci clavier `CTRL` + `SHIFT` + `H`.

3. L'intérêt de changer de répertoire est de ne pas être obliger de renseigner tout le chemin d'un fichier à importer. Uniquement le nom du fichier est ainsi suffisant. Importer les datasets avec la fonction `read.csv()`.

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




## Exercice 2 - xxx

### Mémo


### Exercice sur les Fonctions en R

## Exercice 3 - xxxx

### Mémo


### Exercice sur les Fonctions en R

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




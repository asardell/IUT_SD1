# TD2

<img src="./img/img1.jpg" alt="" style="height: 200px;">

## Objectifs
Voici les objectifs de ce TD :
- [ ] Importer un dataframe
- [ ] Sélection et filtre sur un dataframe
- [ ] Trier un dataframe 

1. [TD2](#td2)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Importer des données](#exercice-1---importer-des-données)
      1. [Mémo](#mémo)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r)
         1. [Les fonctions `getwd()`,`setwd()` et `read.csv()`.](#les-fonctions-getwdsetwd-et-readcsv)
   3. [Exercice 2 - Statistique](#exercice-2---statistique)
      1. [Mémo](#mémo-1)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-1)
   4. [Exercice 3 - Manipulation de data frame](#exercice-3---manipulation-de-data-frame)
      1. [Mémo](#mémo-2)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-2)
   5. [Exercice 4 - GOAT](#exercice-4---goat)
   6. [Liens utiles](#liens-utiles)

La compétition de sur Mario Kart est un sport où chaque détail compte. La performance d'un kart dépend non seulement de la capacité de conduite du pilote, mais aussi de la configuration et de la composition du kart lui-même. Dans ce TD, nous allons explorer comment les données statistiques peuvent être utilisées pour optimiser la composition d'un kart, en se basant sur des [données réelles](https://www.mariowiki.com/Mario_Kart_8_Deluxe_in-game_statistics).

:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_td2`

## Exercice 1 - Importer des données

### Mémo
| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `read.csv()` | Lit un fichier CSV et retourne un dataframe. | `file` : le chemin ou l'URL du fichier CSV à lire, `header` : spécifie si la première ligne contient les noms des variables (par défaut TRUE), `dec` : le caractère utilisé pour indiquer le point décimal (par défaut `"."`), `sep` : le séparateur de champ (par défaut `","`, pour les tabulations `"\t"`). | `donnees <- read.csv("fichier.csv", header = TRUE, dec = ",", sep = ";")` |
| `getwd()` | Retourne le répertoire de travail actuel. | | `current_dir <- getwd()` |
| `setwd()` | Change le répertoire de travail actuel. | `dir` : le chemin du nouveau répertoire de travail | `setwd("/chemin/vers/le/nouveau/repertoire")` |


### Exercice sur les Fonctions en R

#### Les fonctions `getwd()`,`setwd()` et `read.csv()`.

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
gliders = read.csv(file = "gliders.csv", header = TRUE, sep = "|", dec = ".")
drivers = read.csv(file = "drivers.csv", header = TRUE, sep = ";", dec = ",")
```
</details>

5. Pour chaque dataset, afficher la dimension (ligne/colonne) du dataframe.

<details>
<summary>Correction</summary>

```r
dim(bodies_karts)
dim(tires)
dim(gliders)
dim(drivers)
```
</details>


## Exercice 2 - Statistique

### Mémo

| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `cor()` | Calcule la corrélation entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur, `method` : la méthode de calcul de la corrélation (par défaut "pearson"). | `correlation <- cor(x = vecteur1, y = vecteur2, method = "spearman")` |
| `plot()` | Trace un nuage de points entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur, `xlab` : étiquette de l'axe des abscisses, `ylab` : étiquette de l'axe des ordonnées, `main` : titre du graphique. | `plot(vecteur1, vecteur2, xlab = "Variable X", ylab = "Variable Y", main = "Nuage de points")` |
| `cov()` | Calcule la covariance entre deux vecteurs. | `x` : le premier vecteur, `y` : le deuxième vecteur. | `covariance <- cov(x = vecteur1, y = vecteur2)` |
| `install.packages()` | Installe un package R depuis un dépôt CRAN ou local. | `pkgs` : le nom du package à installer, `repos` : l'URL du dépôt, `dependencies` : spécifie si les dépendances doivent également être installées (par défaut TRUE). | `install.packages("nom_du_package")` |
| `library()` | Charge un package R déjà installé en mémoire pour être utilisé dans la session R courante. | `package` : le nom du package à charger. | `library(nom_du_package)` |

### Exercice sur les Fonctions en R

#### Les fonctions `cor()`, `corrplot()`, `install.packages()` et `plot()`.

1. Pour chaque dataset, effectuer un résumé des données avec la fonction adaptée.

<details>
<summary>Correction</summary>

```r
summary(bodies_karts)
summary(tires)
summary(gliders)
summary(drivers)
```
</details>

2. Représenter graphiquement dans un nuage de points le lien entre les statistiques des drivers sur `Weight` et `Acceleration`. Commenter le lien entre ces deux variables ? Pourquoi il n'y a pas autant de points que de drivers ?


<details>
<summary>Correction</summary>

```r
plot(x = drivers$Weight,
     y = drivers$Acceleration, 
     main = "Drivers : Weight / Acceleration")
#Il semble que les deux variables soient corrélées négativement
#Il y a autant de points mais ils sont superposés car certains drivers ont les mêmes statistiques
```
</details>

3. Calculer le coefficient de corrélation de cette relation avec la fonction `cor()`.

<details>
<summary>Correction</summary>

```r
cor(x = drivers$Weight,
    y = drivers$Acceleration)
```
</details>

4. Vérifier ce résultat en calculant vous même le coéfficient de corrélation. Retrouver la [formule ici](https://fr.wikipedia.org/wiki/Corr%C3%A9lation_(statistiques)#Coefficient_de_corr%C3%A9lation_lin%C3%A9aire_de_Bravais-Pearson).

<details>
<summary>Correction</summary>

```r
covXY = cov(x = drivers$Weight,
    y = drivers$Acceleration)
sX = sd(drivers$Weight)
sY = sd(drivers$Acceleration)
print(covXY / (sX*sY))
```
</details>

5. Calculer le coefficient de détermination de cette même relation.

<details>
<summary>Correction</summary>

```r
coefCorr = cor(x = drivers$Weight,
    y = drivers$Acceleration)
coefDeter = coefCorr^2
print(coefDeter)
```
</details>


6. Construire la matrice des corrélations des *variables quantitatives* de statistiques des `drivers` avec la fonction `cor()`. Afficher cette matrice dans une vue et arrondisser les valeurs avec deux décimales uniquements. Qu'observez vous ? 

<details>
<summary>Correction</summary>

```r
matriceCor = cor(drivers[ , - 1])
matriceCor = round(matriceCor , 2)
View(matriceCor)
#Toutes les variables semblent fortement corrélées entre elles.
```
</details>


7. Pour mieux visualiser ces corrélations, nous allons utiliser un package qui ne fait pas parti des packages par défaut. Installer le package `corrplot` avec la fonction `install.packages()`

<details>
<summary>Correction</summary>

```r
#commande à executer qu'une seule fois
install.packages("corrplot")
```
</details>

8. Construire une Corrélogramme avec la fonction `corrplot()` ([plus d'info ici](http://www.sthda.com/french/wiki/visualiser-une-matrice-de-correlation-par-un-correlogramme#correlogramme-visualisation-de-la-matrice-de-correlation)).

:warning: La fonction à utiliser a le même nom que le package.

<details>
<summary>Correction</summary>

```r
library(corrplot) #je charge mon package pour pouvoir utiliser ses fonctionalités
corrplot(matriceCor, method="circle")
```
</details>

9. Construire une Corrélogramme pour les 3 autres datasets. Pour chaque dataset, quelle est la relation avec le lien le plus fort ? le lien le moins fort ?[Plus d'info ici](http://www.sthda.com/french/wiki/visualiser-une-matrice-de-correlation-par-un-correlogramme#personnaliser-le-correlogramme).

:warning: La fonction `cor()` ne fonctionne que sur des variables quantitatives.

<details>
<summary>Correction</summary>

Pour `tires` dataset :

```r
matriceCor = round(cor(tires[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
         )
```

Pour `bodies_karts` dataset :

```r
matriceCor = round(cor(bodies_karts[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
         )
```

Pour `gliders` dataset :

```r
matriceCor = round(cor(gliders[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
         )
```

:warning: On remarque une erreur liée à la variable `Ground.Handling` car tous les gliders ont la même valeur. Il n'est donc pas possible de calculer le coefficient de corrélation car l'écart-type de cette variable est nul.


</details>


## Exercice 3 - Manipulation de data frame

### Mémo

| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `order()` | Trie les éléments d'un vecteur et retourne les indices dans l'ordre croissant ou décroissant. | `x` : le vecteur à trier, `decreasing` : spécifie si le tri doit être effectué dans l'ordre décroissant (par défaut FALSE). | `indices_tri <- order(vecteur, decreasing = FALSE)` |
| `[ , ]` | Indexe un dataframe au niveau des lignes et des colonnes. | `row_index` : index ou condition pour sélectionner les lignes, `col_index` : index ou noms de colonnes pour sélectionner les colonnes. | `donnees_subset <- donnees[1:10, c("colonne1", "colonne2")]` |
| `[ - , ]` | Indexation inverse, exclut les lignes ou colonnes spécifiées. | `row_index` : index ou condition pour exclure les lignes, `col_index` : index ou noms de colonnes pour exclure les colonnes. | `donnees_sans_colonne3 <- donnees[, -3]` |

### Exercice sur les Fonctions en R

#### La fonction `order()`.

1. Créer un object `resultat` avec uniquement le nom du `Driver` et son `Weight`.

<details>
<summary>Correction</summary>

```r
resultat = drivers[ , c("Driver" , "Weight")]
View(resultat)
```
</details>

2. Créer un object `resultat` avec uniquement le nom du `Driver` et son `Acceleration` sur les 10 premières lignes.

<details>
<summary>Correction</summary>

```r
resultat = drivers[ 1:10 , c("Driver" , "Acceleration")]
View(resultat)
```
</details>

3. Créer un object `resultat`sans les colonnes 5, 7 et 9.

<details>
<summary>Correction</summary>

```r
resultat = drivers[ , -c(5,7,9)]
View(resultat)
```
</details>

4. Créer un object `resultat`sans les colonnes `Weight` et `Acceleration`.

<details>
<summary>Correction</summary>

```r
resultat = drivers[ , -c("Weight","Acceleration")] #cela fonctionne uniquement sur des index numériques.
resultat = drivers[ , -c(2,3)]
```
</details>

:warning: Malheureusement, il n'est pas possible d'utiliser les `-` sur des index non numérique. Nous verrons comment contourner cela dans un prochain cours.

5. Créer un object `resultat` avec uniquement les colonnes `Driver`, `Acceleration` et `Weight` dans cet ordre. Que remarquez-vous ?

<details>
<summary>Correction</summary>

```r
resultat = drivers[ , c("Driver", "Acceleration", "Weight")]
View(resultat)
#Les colonnes sont dans l'ordre défini par le vecteur.
```
</details>

6. Créer un object `resultat` avec uniquement les `Driver` 3 , 12 et 32 dans cet ordre.

<details>
<summary>Correction</summary>

```r
resultat = drivers[ c(3,12,32) , ]
View(resultat)
```
</details>

7. Créer un object `resultat` avec uniquement les `Driver` 32 , 3 , 12 dans cet ordre. Que remarquez-vous ?

<details>
<summary>Correction</summary>

```r
resultat = drivers[ c(32,3,12) , ]
View(resultat)
#Les lignes sont dans l'ordre défini par le vecteur.
```
</details>

8. Créer un object `resultat` avec uniquement les colonnes `Driver` et `Weight` en triant les conducteurs du plus léger au plus lourd avec la fonction `order()`.

<details>
<summary>Correction</summary>

```r
rang = order(drivers$Weight)
resultat = drivers[ rang  , c("Driver", "Weight") ]
View(resultat)
```
</details>

9. Créer un object `resultat` avec uniquement les colonnes `Driver` et `Acceleration` en triant les conducteurs du plus rapide au moins rapide.

<details>
<summary>Correction</summary>

```r
rang = order(drivers$Acceleration, decreasing = TRUE)
resultat = drivers[ rang  , c("Driver", "Acceleration") ]
View(resultat)
```
</details>

10. Créer un object `resultat` avec les colonnes `Driver`, `Weight` et `Acceleration` en triant les conducteurs du plus rapide au moins rapide **puis** du plus léger au plus lourd.

<details>
<summary>Correction</summary>

```r
rang = order(drivers$Acceleration, drivers$Weight, decreasing = c(TRUE,FALSE))
resultat = drivers[ rang  , c("Driver", "Acceleration","Weight") ]
View(resultat)
```
</details>

## Exercice 4 - GOAT

Nous voulons déterminer la combinaison de `bodies_karts`, `tires`, `gliders` et `drivers` qui permet d'obtenir le plus d'`Acceleration`.

1. Créer un object `topDriver` avec les colonnes `Driver` et `Acceleration` avec le ou les conducteurs avec la plus grande `Acceleration`.

<details>
<summary>Correction</summary>

```r
help(subset)
topDriver = subset(x = drivers,
                   subset = Acceleration == max(Acceleration), 
                   select = c("Driver","Acceleration"))
```
:warning: Dans la fonction `subset()` il n'est pas nécessaire de mentionner `drivers$...` car le dataframe utilisé est déjà mentionné dans l'argument `x`.

</details>


2. Créer un object `topGlider`, `topTires` et `topBody` avec la même logique de conserver uniquement les meilleurs statistiques d'`Acceleration`.

<details>
<summary>Correction</summary>

```r
topGlider = subset(x = gliders,
                   subset = Acceleration == max(Acceleration), 
                   select = c("Glider","Acceleration"))
```
```r
topTires = subset(x = tires,
                   subset = Acceleration == max(Acceleration), 
                   select = c("Tire","Acceleration"))
```
```r
topBody = subset(x = bodies_karts,
                   subset = Acceleration == max(Acceleration), 
                   select = c("Body","Acceleration"))
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




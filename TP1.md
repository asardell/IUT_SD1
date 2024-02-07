# TP1

## Objectifs
Voici les objectifs de ce TD :
- [ ] Construire un dataframe
- [ ] Créer des colonnes dans un dataframe
- [ ] Sélection et filtre sur un dataframe 
- [ ] Importer et exporter un dataframe

1. [TP1](#tp1)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Utilisation d'un dataframe existant un dataframe](#exercice-1---utilisation-dun-dataframe-existant-un-dataframe)
      1. [Mémo](#mémo)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r)
   3. [Exercice 2 - Import/Exporter un dataframe](#exercice-2---importexporter-un-dataframe)
      1. [Mémo](#mémo-1)
      2. [Exercice sur les Fonctions en R](#exercice-sur-les-fonctions-en-r-1)
         1. [La fonction `read.csv()`](#la-fonction-readcsv)
         2. [Les fonctions `subset()`,  `table()` et `prop.table()`](#les-fonctions-subset--table-et-proptable)
            1. [Filtre sur les Animes](#filtre-sur-les-animes)
            2. [Filtre sur les Animes](#filtre-sur-les-animes-1)
         3. [Les fonctions `rbind()` et `write.table()`](#les-fonctions-rbind-et-writetable)

    

:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_tp1`

## Exercice 1 - Utilisation d'un dataframe existant un dataframe

R propose un ensemble de jeux de données intégrés qui sont souvent utilisés à des fins d'apprentissage, de démonstration et d'analyse exploratoire. Ces jeux de données couvrent une variété de domaines, de la biologie à l'économie en passant par la sociologie. Pour les lister, vous pouvez utiliser la fonction `data()` qui renvoie une liste des noms des jeux de données disponibles dans l'environnement R. Ensuite, pour accéder à un jeu de données spécifique, vous pouvez utiliser son nom comme argument pour la fonction data(), ou simplement utiliser le nom directement s'il est chargé dans votre session R.

### Mémo
| Nom de la commande | Description | Argument Pertinent | Exemple |
|------------------|-------------|--------------------|---------|
| `data()` | Retourne la liste des noms des jeux de données chargés par défaut. |  | `data()` |
| `ncol()` | Retourne le nombre de colonnes dans un objet (par exemple, un dataframe ou une matrice). |  | `nombre_colonnes <- ncol(objet)` |
| `nrow()` | Retourne le nombre de lignes dans un objet (par exemple, un dataframe ou une matrice). |  | `nombre_lignes <- nrow(objet)` |
| `dim()` | Retourne les dimensions (nombre de lignes et de colonnes) d'un objet (par exemple, un dataframe ou une matrice). |  | `dimensions <- dim(objet)` |
| `colnames()` | Retourne ou définie les noms des colonnes dans un dataframe ou une matrice. | Aucun ou nouveaux noms de colonnes | `noms_colonnes <- colnames(dataframe)` ou `colnames(dataframe) <- c("Nom1", "Nom2", ...)` |
| `summary()` | Produit un résumé statistique des données dans un objet (par exemple, un vecteur, un dataframe, etc.). |  | `res <- summary(objet)` |
| `View()` | Ouvre une visionneuse de données pour explorer un dataframe ou une matrice dans une fenêtre séparée. | Aucun | `View(dataframe)` |
| `head()` | Affiche les premières lignes d'un dataframe ou d'une matrice. | `n` : nombre de lignes à afficher (par défaut 6) | `premieres_lignes <- head(dataframe, n = 10)` |
| `$` | Accéder à une colonne d'un dataframe | | `df$colonneA` |
| `[ , ]` | Accéder à certaines lignes et/ou colonnes d'un datarame. | | `dfExtraction <- df[ c(5,6), c("colonneB", "colonneD")]` |

### Exercice sur les Fonctions en R

1. Afficher le jeu de données `iris` puis afficher la classe de l'objet `iris`.
<details>
<summary>Correction</summary>

```r
iris
class(iris)
```
</details>

2. Afficher le jeu de données `iris` dans une vue avec la fonction `View()`
<details>
<summary>Correction</summary>

```r
View(iris)
```
</details>

3. Afficher le nombre de lignes avec la fonction `nrow()`
<details>
<summary>Correction</summary>

```r
nrow(iris)
```
</details>

4. Afficher le nombre de colonne avec la fonction `ncol()`
<details>
<summary>Correction</summary>

```r
ncol(iris)
```
</details>

5. Afficher le nom des colonnes avec la fonction `colnames()`
<details>
<summary>Correction</summary>

```r
colnames(iris)
```
</details>

6. Afficher un résumé du dataframe avec la fonction `summary()`
<details>
<summary>Correction</summary>

```r
summary(iris)
```
</details>

7. Afficher uniquement les colonnes `Sepal.Length` et `Species`.
<details>
<summary>Correction</summary>

```r
iris[ , c("Sepal.Length","Species")]
```
</details>

9. Afficher uniquement la ligne 100,103 et 105.
<details>
<summary>Correction</summary>

```r
iris[ c(100,103,105) , ]
```
</details

10. Afficher uniquement les lignes 50 à 100.
<details>
<summary>Correction</summary>

```r
iris[ 50:100 , ]
```
</details>

11.  Calculer la moyenne de la variable `Sepal.Length`.
<details>
<summary>Correction</summary>

```r
mean(iris$Sepal.Length)
```
</details>

12.  Calculer la médiane de la variable `Sepal.Width`.
<details>
<summary>Correction</summary>

```r
median(iris$Sepal.Length)
```
</details>

13.   Calculer l'écart-type de la variable `Petal.Length`.
<details>
<summary>Correction</summary>

```r
sd(iris$Petal.Length)
```
</details>

14.   Calculer les déciles de la variable `Petal.Width`.
<details>
<summary>Correction</summary>

```r
quantile(iris$Petal.Width, probs = seq(from = 0.1, to = 0.9, by =0.1))
```
</details>

## Exercice 2 - Import/Exporter un dataframe

### Mémo
| Nom de la commande | Description | Argument Pertinent | Exemple |
|-------------------|-------------|--------------------|---------|
| `read.csv()` | Lit un fichier CSV et retourne un dataframe. | `file` : le chemin ou l'URL du fichier CSV à lire, `header` : spécifie si la première ligne contient les noms des variables (par défaut TRUE), `dec` : le caractère utilisé pour indiquer le point décimal (par défaut "."), `sep` : le séparateur de champ (par défaut ","). | `donnees <- read.csv("fichier.csv", header = TRUE, dec = ",", sep = ";")` |
| `subset()` | Retourne un sous-ensemble d'un objet (par exemple, un dataframe) en fonction de certaines conditions. | `x` : l'objet à sous-ensemble, `subset` : la condition de sous-ensemble. | `sous_ensemble <- subset(dataframe, condition)` |
| `write.table()` | Écrit un objet (par exemple, un dataframe) dans un fichier texte ou CSV. | `x` : l'objet à écrire, `file` : le nom du fichier de sortie, `sep` : le séparateur de champ (par défaut " "), `row.names` : spécifie si les noms de lignes doivent être inclus (par défaut TRUE). | `write.table(dataframe, file = "output.csv", sep = ",", row.names = FALSE)` |
| `rbind()` | Ajoute des lignes à un dataframe existant en les liant par les colonnes. | `nouveau_dataframe <- rbind(dataframe1, dataframe2)` |

| Opérateur logique | Description | Exemple avec la fonction `subset()` |
|-------------------|-------------|----------------------------------------|
| `>` | Vérifie si une valeur est strictement supérieure à une autre. | `subset(dataframe, colonne1 > 10)` |
| `>=` | Vérifie si une valeur est supérieure ou égale à une autre. | `subset(dataframe, colonne2 >= 0)` |
| `<` | Vérifie si une valeur est strictement inférieure à une autre. | `subset(dataframe, colonne3 < 5)` |
| `<=` | Vérifie si une valeur est inférieure ou égale à une autre. | `subset(dataframe, colonne4 <= 100)` |
| `&` | Opérateur logique ET, renvoie TRUE si les deux conditions sont remplies. | `subset(dataframe, colonne1 > 10 & colonne2 < 5)` |
| `\|` | Opérateur logique OU, renvoie TRUE si au moins l'une des conditions est remplie. | `subset(dataframe, colonne3 == "oui" | colonne4 != "non")` |
| `!=` | Vérifie si deux valeurs sont différentes. | `subset(dataframe, colonne5 != "invalide")` |
| `==` | Vérifie si deux valeurs sont égales. | `subset(dataframe, colonne6 == "valide")` |
| `%in%` | Vérifie si une valeur est présente dans un vecteur ou une liste. | `subset(dataframe, colonne7 %in% c("valeur1", "valeur2", "valeur3"))` |
| `!` | Opérateur logique NON, renvoie l'inverse d'une condition. | `subset(dataframe, !colonne8 %in% c("B","C"))` |


### Exercice sur les Fonctions en R

Ces jeux de données comprennent des informations sur les animes et les mangas les mieux notés provenant du site Web populaire MyAnimeList.
Les deux fichiers sont disponibles ce repository git dans le dossier `dataset`. Pour avoir plus d'information sur les données, vous pouvez consulter la source sur [Kaggle](https://www.kaggle.com/datasets/duongtruongbinh/manga-and-anime-dataset/data).

Fichiers :

- anime.csv : Contient des informations sur les séries d'anime les mieux notées.
- manga.csv : Contient des informations sur les séries de manga les mieux notées.

#### La fonction `read.csv()`

1. Importer le jeu de données `manga.csv` dans un objet appelé `dfManga` et le jeu de données `anime.csv` dans un objet appelé `dfAnime`. Puis afficher la classe des deux objets pour vérifier que la classe est *data.frame*.
<details>
<summary>Correction</summary>

```r
dfManga <- read.csv(".../.../.../manga.csv", header = TRUE, sep = ",", dec = ".")
dfAnime <- read.csv(".../.../.../anime.csv", header = TRUE, sep = ",", dec = ".")
class(dfManga)
class(dfAnime)
```
</details>

2. Afficher les jeux de données dans des vues pour les visualiser
<details>
<summary>Correction</summary>

```r
View(dfManga)
#puis
View(dfAnime)
```
</details>

3. Afficher le nombre de lignes et colonnes avec la fonction `dim()`
<details>
<summary>Correction</summary>

```r
dim(dfManga)
dim(dfAnime)
```
</details>

4. Calculer la moyenne de la variable `Score` pour les deux dataframe. Quelle est la moyenne la plus élevée ?
<details>
<summary>Correction</summary>

```r
mean(dfManga$Score)
mean(dfAnime$Score)
```
</details>

5. Calculer le nombre total de votes de la variable `Vote` pour les deux dataframe. Ou y a t-il le plus de votes ?
<details>
<summary>Correction</summary>

```r
sum(dfManga$Vote)
sum(dfAnime$Vote)
```
</details>

6. Calculer l'écart-type des notes de la variable `Score` pour les deux dataframe. Ou est l'échantillon le plus homogènes au niveau des `Score` ?
<details>
<summary>Correction</summary>

```r
sd(dfManga$Score)
sd(dfAnime$Score)
```
</details>

7. Calculer les déciles des notes de la variable `Score` pour les deux dataframe. Quelle dataframe a le décile 1 le plus petit ?
<details>
<summary>Correction</summary>

```r
quantile(dfManga$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
quantile(dfAnime$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
```
</details>

#### Les fonctions `subset()`,  `table()` et `prop.table()`

Pour chaque extraction, créer un nouvel objet et calculer le nombre de ligne filtrées.

##### Filtre sur les Animes

1. Combien de Manga ont une note strictement supérieure à 9/10 ?
<details>
<summary>Correction</summary>

```r
extraction1 <- subset(dfManga, Score > 9)
nrow(extraction1)
```
</details>

2. Combien de Manga ont 200000 votes ou plus ?
<details>
<summary>Correction</summary>

```r
extraction2 <- subset(dfManga, Vote >= 200000)
nrow(extraction2)
```
</details>

3. Combien de Manga ont strictement plus de 200000 votes et plus de 8/10 ?
<details>
<summary>Correction</summary>

```r
extraction3 <- subset(dfManga, Vote >= 200000 & Score >= 8)
nrow(extraction3)
```
</details>

4. Combien de Manga ont une note comprise entre 7/10 et 8/10 ?
<details>
<summary>Correction</summary>

```r
extraction4 <- subset(dfManga, Vote >= 7 & Vote <= 8)
nrow(extraction4)
```
</details>

##### Filtre sur les Animes

1. Calculer les effectifs de la variable  `Rating()`. Combien de modalité de la variable existe-t-il ? Calculer ensuite les effectifs en pourcentage.
<details>
<summary>Correction</summary>

```r
effectifRating <- table(dfAnime$Rating)
print(effectifRating)
length(effectifRating)
prop.table(effectifRating)
```
</details>

2. Combien d'Anime sont concernés par le Rating : *R - 17+ (violence & profanity)* ?
<details>
<summary>Correction</summary>

```r
extraction2 <- subset(dfAnime, Rating == "R - 17+ (violence & profanity)")
nrow(extraction2)
```
</details>

3. Combien d'Anime sont concernés par le Rating : *R - 17+ (violence & profanity)*  et ont une note supérieur à 8/10 ?
<details>
<summary>Correction</summary>

```r
extraction3 <- subset(dfAnime, Rating == "R - 17+ (violence & profanity)" &
                                 Score >= 8)
nrow(extraction3)
```
</details>

4. Combien d'Anime ne correspondent pas au Rating : *R - 17+ (violence & profanity)* ?
<details>
<summary>Correction</summary>

```r
extraction4 <- subset(dfAnime, Rating != "R - 17+ (violence & profanity)")
nrow(extraction4)
```
</details>

5. Combien d'Anime correspondent au Rating : *PG - Children* et *G - All Ages* ?
<details>
<summary>Correction</summary>

```r
extraction5 <- subset(dfAnime, Rating %in% c("PG - Children","G - All Ages"))
nrow(extraction5)
```
</details>

6. Combien d'Anime **ne** correspondent **pas** au Rating : *PG - Children* et *G - All Ages* ?
<details>
<summary>Correction</summary>

```r
extraction6 <- subset(dfAnime, !Rating %in% c("PG - Children","G - All Ages"))
nrow(extraction6)
```
</details>

7. Combien d'Anime ont une note supérieure à 9/10 ou ont plus de 400000 votes ?
<details>
<summary>Correction</summary>

```r
extraction7 <- subset(dfAnime, Score >= 9 | Vote > 400000)
nrow(extraction7)
```
</details>

#### Les fonctions `rbind()` et `write.table()`

Dans ces questions, nous allons conserver uniquement certaines colonnes pour pouvoir fusionner les deux dataframe ensemble. Puis nous exporterons le résultat.

1. Modifier les deux dataframe en ne conservant que les variables : `Title`,`Score`,`Vote`,`Ranked`.
<details>
<summary>Correction</summary>

```r
dfAnime <- dfAnime[ , c("Title","Score","Vote","Ranked")]
dfManga <- dfManga[ , c("Title","Score","Vote","Ranked")]
```
</details>

2. Pour chaque dataframe créer une colonne  `Type` avec pour valeur *Anime* ou *Manga* selon l'objet.
<details>
<summary>Correction</summary>

```r
dfAnime$Type <- "Anime"
dfManga$Type <- "Manga
```
</details>

3. Compiler les deux dataframe avec la fonction `rbind()` dans un objet appelé `dfConcat`. Vérifier le résultat avec dans une vue.
<details>
<summary>Correction</summary>

```r
dfConcat <- rbind(dfManga,dfAnime)
View(dfConcat)
```
</details>

4. Exporter le dataframe dans un fichier csv nommée *ExportTp1.csv* avec la fonction `write.table`.
<details>
<summary>Correction</summary>

```r
write.table(x = dfConcat, file = ".../.../.../ExportTp1.csv",
            sep = ";",row.names = FALSE)
```
</details>







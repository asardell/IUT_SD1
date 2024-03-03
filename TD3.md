# TD3

## Objectifs
Voici les objectifs de ce chapitre :
- [ ] Importer un fichier excel
- [ ] Notion du type factor
- [ ] Opération d'agrégation sur une dataframe
- [ ] Découper un vecteur en tranche

Ce TD utilise le fichier `pokemon.xlsx` qui décrit les statistiques des pokemon des deux premières générations. Le fichier est issu du site [Kaggle](https://www.kaggle.com/rounakbanik/pokemon). Il a été adapté pour ce TD. Pour réaliser ce TD, télécharger le fichier depuis le dossier `/dataset`.

:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_td3`

## Exercice 1 - Importer les données

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|-------------------|-------------|----------------------|---------|
| `read_excel()` | Lit un fichier Excel dans R. | `path` : le chemin vers le fichier Excel, `sheet` : le nom ou l'index de la feuille à lire | `readxl::read_excel(path = "/chemin/vers/votre/fichier.xlsx", sheet = "Nom_de_la_feuille")` |
| `as.factor()` | Convertit un vecteur en facteur. | `x` : le vecteur à convertir | `as.factor(x = c("A", "B", "A", "C"))` |

### Exercice sur les Fonctions en R

#### Les fonctions `read_excel()` et `as.factor()`.

1. Importer le jeu de données *pokemon.xlsx* à l’aide du package `readxl`.

<details>
<summary>Correction</summary>

```r
library(readxl)
pokemon <- read_excel(path = "pokemon.xlsx",sheet = "pokemon")
```
</details>

2. Combien de lignes, colonnes sont présentes dans ce dataset (utilisez les fonctions adaptées) ?

<details>
<summary>Correction</summary>

```r
dim(pokemon)
ncol(pokemon)
nrow(pokemon)
```
</details>

3. Affichez un résumé des données avec la fonction adaptée. On remarque peut-être que les variables qualitatives n'ont pas de statistique. En R, il est important que les variables qualitatives soit de type `factor`.

<details>
<summary>Correction</summary>

```r
summary(pokemon)
```
</details>

4. On souhaite analyser les variables `generation`, `is_legendary`, et `type` en tant que variables qualitatives. Modifier le type de ces variables pour les transformer en type `factor` (plus d'infos sur le type `factor` [ici](https://asardell.github.io/programmation-r/presentation.html#type-de-vecteur))

<details>
<summary>Correction</summary>

```r
pokemon$is_legendary <-as.factor(pokemon$is_legendary)
pokemon$generation <-as.factor(pokemon$generation)
pokemon$type <-as.factor(pokemon$type)
```
</details>

5. Affichez un nouveau résumé des données avec la fonction adaptée.
<details>
<summary>Correction</summary>

```r
summary(pokemon)
```
</details>


## Exercice 2 - Création de colonne

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|-------------------|-------------|----------------------|---------|
| `ifelse()` | Retourne des valeurs en fonction d'une condition. | `test` : la condition logique à évaluer, `yes` : la valeur à retourner si la condition est vraie, `no` : la valeur à retourner si la condition est fausse | `ifelse(test = x > 0, yes = "Positif", no = "Négatif")` |
| `cut()` | Divise les valeurs numériques en intervalles. | `x` : le vecteur de valeurs numériques à découper, `breaks` : les points de rupture pour diviser les valeurs, `labels` : les étiquettes à attribuer aux intervalles | `cut(x = c(1, 2, 3, 4, 5), breaks = 3, labels = c("Faible", "Moyen", "Fort"))` |
| `is.na()` | Vérifie si les valeurs sont manquantes (NA). | `x` : le vecteur à tester | `is.na(x)` |

### Exercice sur les Fonctions en R

Dans cet exercice, nous allons créer des colonnes supplémentaires.

#### La fonction `ifelse()`.

1. Créer une colonne `attack_group` avec la valeur *attack+* si la valeur d'`attack` est supérieure ou égale à la médiane, sinon *attack-*. Convertir cette variable en `factor` puis effectuer un résumé de cette colonne avec la fonction `summary()`.
<details>
<summary>Correction</summary>

```r
med = median(pokemon$attack)
pokemon$attack_group = ifelse(pokemon$attack >= med, "attack+","attack-")
pokemon$attack_group <-as.factor(pokemon$attack_group)
summary(pokemon$attack_group)
```
</details>

2. Créer une colonne `water_fire` avec la valeur *yes* si le `type` est *water* ou *fire*, sinon  renseigner la valeur *no*. Convertir cette variable en `factor` puis effectuer un résumé de cette colonne avec la fonction `summary()`.
<details>
<summary>Correction</summary>

```r
pokemon$water_fire = ifelse(pokemon$type %in% c("water","fire"), "yes","no")
pokemon$water_fire <-as.factor(pokemon$water_fire)
summary(pokemon$water_fire)
```
</details>

3. Créer une colonne `best` avec la valeur *yes* si la valeur d'`attack` fait parti du troisième quartile *et* si la valeur de `defense` fait parti du troisième quartile *et*  si la valeur de `speed` fait parti du troisième quartile, sinon renseigner la valeur *no*. Convertir cette variable en `factor` puis effectuer un résumé de cette colonne avec la fonction `summary()`.
<details>
<summary>Correction</summary>

```r
q3_attack = quantile(pokemon$attack, probs = 0.75)
q3_defense = quantile(pokemon$defense, probs = 0.75)
q3_speed = quantile(pokemon$speed, probs = 0.75)
pokemon$best = ifelse(pokemon$attack > q3_attack &
                      pokemon$defense > q3_defense &
                      pokemon$speed > q3_speed , "yes","no")
pokemon$best <-as.factor(pokemon$best)
summary(pokemon$best)
```
</details>

#### La fonction `is.na()`.

1. Filtrer les données dans un objet nommé `requete` avec les pokemons ayant des valeurs manquantes sur la colonne `weight_kg`.
<details>
<summary>Correction</summary>

```r
requete = subset(pokemon, is.na(weight_kg))
View(requete)
```
</details>

1. Filtrer les données dans un objet nommé `requete` avec les pokemons n'ayant pas des valeurs manquantes sur la colonne `weight_kg`.
<details>
<summary>Correction</summary>

```r
requete = subset(pokemon, !is.na(weight_kg))
View(requete)
```
</details>

2. Créer des nouvelles variables nommées  `weight_kgNa` et `height_mNA` avec les mêmes valeurs pour les valeurs déjà renseignées **mais** en remplaçant les valeurs manquantes `NA` par leur valeurs médianne.
<details>
<summary>Correction</summary>

```r
med_weight_kg = median(pokemon$weight_kg, na.rm = TRUE)
pokemon$weight_kgNa = ifelse(is.na(pokemon$weight_kg) , 
                                 med_weight_kg ,
                                 pokemon$weight_kg)

med_height_m = median(pokemon$height_m, na.rm = TRUE)
pokemon$height_mNA = ifelse(is.na(pokemon$height_m) , 
                                 med_height_m ,
                                 pokemon$height_m)
```
</details>

#### La fonctions `cut()`.

1. Créer une nouvelle variable nommée  `weight_group` en regroupant en 3 tranches avec les labels *léger* / *moyen* / *lourd*.
<details>
<summary>Correction</summary>

```r
pokemon$weight_group = cut(pokemon$weight_kg,
                           breaks = 3,
                           labels = c("léger","moyen","lourd"))
```
</details>

2. Créer une nouvelle variable nommée  `height_m_group` en regroupant en 4 tranches  telles que :  *]0,1]* / *]1,2]* / *]2,3]* / *]3,max]*
<details>
<summary>Correction</summary>

```r
pokemon$height_m_group = cut(pokemon$height_m,
                             breaks = c(0,1,2,3,
                                        max(pokemon$height_m,
                                            na.rm = TRUE)))
```
</details>

3. Créer une nouvelle variable nommée  `defense_group` en regroupant en 5 tranches avec les min, max et quartiles telle que : *[min,Q1]* / *(Q1,Q2]* / *(Q2,Q3]* / *(Q3,max]*. Calculer un résumé de la nouvelle colonne.
<details>
<summary>Correction</summary>

```r
pokemon$defense_group = cut(pokemon$defense,
                             breaks = quantile(pokemon$defense,
                                               na.rm = TRUE),
                            include.lowest = TRUE)
summary(pokemon$defense_group)
```
</details>

## Exercice 3 - Agregation

### Mémo
| Nom de la commande | Description | Arguments Pertinents | Exemple |
|--------------------|-------------|----------------------|---------|
| `aggregate()` | Effectue une opération d'agrégation sur les données groupées. | `x` : formule spécifiant les variables à agréger et les variables de groupe, `data` : le jeu de données, `FUN` :  la ou les fonctions d'agrégation souhaitées | `aggregate(x = y ~ a + b, data = dataframe, FUN = function(x) mean(x))` |

### Exercice sur les Fonctions en R

#### La fonction `aggregate()`.

1. Calculer la moyenne d'`attack` par `type`.
<details>
<summary>Correction</summary>

```r
aggregate(x = attack ~ type, 
          data = pokemon,
          FUN = function(x) mean(x))
```
</details>

2. Calculer la mediane d'`attack` par `generation` et `type`.
<details>
<summary>Correction</summary>

```r
aggregate(x = attack ~ generation + type,
          data = pokemon, 
          FUN = function(x) median(x))
```
</details>

3. Calculer l'effectif par `type`.
<details>
<summary>Correction</summary>

```r
aggregate(x = pokedex_number ~ type,
          data = pokemon,
          FUN = function(x) length(x))
```
</details>

4. Calculer la moyenne et la mediane de la statistique `speed` pour chaque  `generation` et `type`. Afficher également les effectifs de chaque paire. 
<details>
<summary>Correction</summary>

```r
aggregate(speed ~ generation + type,
          data = pokemon, 
          FUN = function(x) c(moy = mean(x),
                              med = median(x),
                              eff = length(x) ) )
```
</details>


## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




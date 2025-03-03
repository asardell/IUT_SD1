# TP2 - Rappel et cas pratique

## Objectifs
Voici les objectifs de ce TD :
- [ ] Importer un dataframe
- [ ] Sélection et filtre sur un dataframe
- [ ] Trier un dataframe

1. [TP2 - Rappel et cas pratique](#tp2---rappel-et-cas-pratique)
   1. [Objectifs](#objectifs)
   2. [Exercice 1 - Importer les données](#exercice-1---importer-les-données)
   3. [Exercice 2 - Statistiques descriptives](#exercice-2---statistiques-descriptives)
   4. [Exercice 3 -  Tris et filtres](#exercice-3----tris-et-filtres)
   5. [Exercice 4 -  Modifier le dataframe](#exercice-4----modifier-le-dataframe)
   6. [Exercice 5 -  Corrélation](#exercice-5----corrélation)
   7. [Liens utiles](#liens-utiles)


:warning: L'ensemble des exercices sont à réaliser dans un seul script nommé `iut_sd1_r_tp2`.

Pour ce TP, on utilise le fichier `fao.csv` qui présente la production, l’importation et l’exportation des ressources alimentaires des pays du monde en 2020. les données sont issues du site de la [FAO](https://www.fao.org/faostat/fr/#data/FBS).
Voici une description des données :

- `Nom` : Nom du pays
- `Dispo_alim` : Disponibilité alimentaire moyenne (en Kcal/personne/jour) en 2020
- `Prod_viande` : Production de viande en milliers de tonnes en 2020
- `Import_viande` : Importations de viande en milliers de tonnes en 2020
- `Export_viande` : Exportations de viande en milliers de tonnes en 2020
- `Population` : Nombre estimé d’habitant en 2018

## Exercice 1 - Importer les données

1. Importer le jeu de données fao.csv avec la fonction `read.csv()` uniquement dans un objet appelé `df`. Vérifier le type des colonnes pour vérifier que les colonnes aient le bon type.
<details>
<summary>Correction</summary>

```r
df<-read.csv("fao.csv", sep=";", dec=",", header = TRUE)
```
</details>



2. Combien de pays sont présents dans ce dataset ?
<details>
<summary>Correction</summary>

```r
nrow(df)
```
</details>

3. Affichez un résumé des données avec la fonction adaptée. Il semble que ce jeu de données présente quelques valeurs manquantes.
<details>
<summary>Correction</summary>

```r
summary(df)
```
</details>

## Exercice 2 - Statistiques descriptives

1. Quelle est la disponibilité alimentaire moyenne mondiale en Kcal/personne/jour ?
<details>
<summary>Correction</summary>

```r
mean(df$Dispo_alim, na.rm=TRUE)
```
</details>

2. Quel est le nombre d’habitant dans le monde ?
<details>
<summary>Correction</summary>

```r
sum(df$Population, na.rm=TRUE)
```
</details>

3. Quel est l’écart-type du volume des exportations de viande ? Et des importations de viande ?
<details>
<summary>Correction</summary>

```r
sd(df$Export_viande, na.rm=TRUE)
sd(df$Import_viande, na.rm=TRUE)
```
</details>

4. Quelle est la médiane du volume de production de viande ?
<details>
<summary>Correction</summary>

```r
median(df$Prod_viande, na.rm=TRUE)
```
</details>

5. Calculez les quartiles du nombre de Kcal de disponibilité alimentaire.
<details>
<summary>Correction</summary>

```r
quantile(df$Dispo_alim)
```
</details>

6. Calculez les centiles du volume d’importation de viande.
<details>
<summary>Correction</summary>

```r
quantile(df$Import_viande, seq(0,1,0.01))
```
</details>

## Exercice 3 -  Tris et filtres

Pour chaque question, il est recommandé de sauvegarder le résultat de la requête dans un objet puis de le visualiser dans une vue pour vérifier.

1. Construire une requête pour extraire les lignes du dataset avec les 5 pays les moins peuplés.
<details>
<summary>Correction</summary>

```r
rang = order(df$Population)
resultat = head(df[ rang , ], n = 5)
View(resultat)
```
</details>

2. Construire une requête pour extraire les lignes du dataset avec les 5 pays les plus peuplés.
<details>
<summary>Correction</summary>

```r
rang = order(df$Population, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
```
</details>

3. Construire une requête pour extraire les lignes du dataset avec les 5 pays qui produisent le plus de viande.
<details>
<summary>Correction</summary>

```r
rang = order(df$Prod_viande, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
```
</details>

4. Construire une requête pour extraire les lignes du dataset avec les 5 pays qui importent le plus de viande.
<details>
<summary>Correction</summary>

```r
rang = order(df$Import_viande, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
```
</details>

5. En moyenne, le besoin énergétique moyen d’une adulte est de 2300 kcal par jour. Construire une requête pour extraire les lignes du dataset avec les pays qui ont une disponibilité alimentaire supérieure ou égale à 2300 kcal. Combien de pays sont concernés ?
<details>
<summary>Correction</summary>

```r
resultat = subset(df, Dispo_alim>=2300)
View(resultat)
```
</details>

6. Construire une requête pour extraire les lignes du dataset avec les pays qui ont une disponibilité alimentaire strictement supérieure à 3500 kcal et qui importe un volume de viande supérieure ou égale à 1 000 000 tonnes par an. Combien de pays sont concernés ?
<details>
<summary>Correction</summary>

```r
resultat = subset(df, Dispo_alim > 3500  & Import_viande > 1000)
View(resultat)
```
</details>

7. Construire une requête pour extraire les lignes du dataset avec la France et la Belgique.
<details>
<summary>Correction</summary>

```r
resultat = subset(df, Nom %in% c("France","Belgique"))
View(resultat)
```
</details>

## Exercice 4 -  Modifier le dataframe

1. Ajouter une colonne nommée `part_export` qui correspond à la part des exportations de viande par rapport à la production de viande.
<details>
<summary>Correction</summary>

```r
df$Part_export<-df$Export_viande/df$Prod_viande
```
</details>

2. La colonne `Dispo_alim` présente la disponibilité alimentaire par personne. Ajouter une colonne nommée `dispo_alim_pays` qui correspond à la disponibilité total du pays en Kcal/jour.
<details>
<summary>Correction</summary>

```r
df$Dispo_alim_pays<-df$Dispo_alim*df$Population
```
</details>

3. Exporter le nouveau dataframe dans un fichier csv nommé *ExportTp2.csv* avec la fonction `write.table()`.
<details>
<summary>Correction</summary>

```r
write.table(x = df, file = "ExportTp2.csv")
```
</details>

4. Calculer la somme de la disponibilité alimentaire mondiale.
<details>
<summary>Correction</summary>

```r
dispo_alim_mondiale = sum(df$Dispo_alim_pays, na.rm=TRUE)
dispo_alim_mondiale
```
</details>

5. Sachant qu’en moyenne, le besoin énergétique moyen d’une adulte est de 2300 kcal par jour. Combien d’adulte pourrait-on nourrir avec la disponibilité alimentaire mondiale ?
<details>
<summary>Correction</summary>

```r
dispo_alim_mondiale/2300
```
</details>

## Exercice 5 -  Corrélation

:warning: ne pas confondre corrélation et lien de cause à effet. [La preuve en chiffre !](https://www.tylervigen.com/spurious-correlations) 

1. Représenter graphiquement dans un nuage de points le lien entre `Prod_viande` et `Export_viande`. Commenter le lien entre ces deux variables ? 
<details>
<summary>Correction</summary>

```r
plot(x = df$Prod_viande,
     y = df$Export_viande, 
     main = "Pays : Prod_viande / Export_viande")
```
</details>

2. Calculer le coefficient de corrélation de cette relation avec la fonction `cor()`.
<details>
<summary>Correction</summary>

```r
cor(x = df$Prod_viande,
    y = df$Export_viande)
```
</details>

3. Construire la matrice des corrélations des *variables quantitatives* avec la fonction `cor()`. Afficher cette matrice dans une vue et arrondisser les valeurs avec deux décimales uniquements. Commenter la relation la plus forte, la plus faible. 

:warning: Il y a des `N/A` dans le dataset, essayer de trouver la solution en vous aidant de la rubrique *Help*.

<details>
<summary>Correction</summary>

```r
matriceCor = cor(df[ , - 1] , use = "complete.obs")
matriceCor = round(matriceCor , 2)
View(matriceCor)
```
</details>

4. Pour mieux visualiser ces corrélations, nous allons utiliser un package qui ne fait pas parti des packages par défaut. Installer le package `corrplot` avec la fonction `install.packages()` **sauf** s'il est déjà installé.

<details>
<summary>Correction</summary>

```r
#commande à executer qu'une seule fois
install.packages("corrplot")
```
</details>

5. Construire une Corrélogramme avec la fonction `corrplot()` ([plus d'info ici](http://www.sthda.com/french/wiki/visualiser-une-matrice-de-correlation-par-un-correlogramme#correlogramme-visualisation-de-la-matrice-de-correlation)).

:warning: La fonction à utiliser a le même nom que le package.

<details>
<summary>Correction</summary>

```r
library(corrplot) #je charge mon package pour pouvoir utiliser ses fonctionalités
corrplot(matriceCor, method="circle")
```
</details>


## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




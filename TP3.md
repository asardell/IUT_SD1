# TP3

## Objectifs
Voici les objectifs de ce chapitre :
- [ ] Rappel des modules précédents

Pour cet TP, on utilise  le fichier `quiz.csv`. Ce fichier présente les statistiques des quiz d'étudiants brillants. Nous souhaitons faire une analyse statistique des résultats.

## Exercice A : Importer les données

1. Modifier votre dossier de travail avec la fonction adaptée

<details>
<summary>Correction</summary>

```r
setwd("C:/Users/Anthony/Documents/asardell/TP3")
```
</details>


2. Importer le jeu de données dans un objet appelé `df`. La réponse à cette question vous sera donné à 14h dans le même dossier que le jeu de données.

<details>
<summary>Correction</summary>

```r
df = read.csv(file = "quiz.csv", sep = "\t", dec = ",")
```
</details>

3. Combien y a t-il d'étudiants ?

<details>
<summary>Correction</summary>

```r
nrow(df)
```
</details>

4. Combien y a t-il de colonnes ?

<details>
<summary>Correction</summary>

```r
ncol(df)
```
</details>

5. Calculer un résumé des données afin de vérifier si les variables ont le bon type. On remarque des valeurs manquantes dans le jeu de données.

<details>
<summary>Correction</summary>

```r
summary(df)
```
</details>

6. On veut analyser les variables qualitatives en classe `factor`. Convertir les variables `Identifiant` , `TD` et `TP` en type `factor`. Vérifier ensuite si les variables ont la bonne classe.

<details>
<summary>Correction</summary>

```r
df$Identifiant <- as.factor(df$Identifiant)
df$TD <- as.factor(df$TD)
df$TP <- as.factor(df$TP)
class(df$Identifiant)
class(df$TD)
class(df$TP)
```
</details>

## Exercice B : Statistiques descriptives

7. Calculer la moyenne de chaque quiz. Quel est le quiz avec la moyenne la plus haute ?

<details>
<summary>Correction</summary>

```r
mean(df$Quiz1, na.rm = TRUE)
mean(df$Quiz2, na.rm = TRUE)
mean(df$Quiz3, na.rm = TRUE)
#meilleur moyenne sur le quiz1
```
</details>

8. Calculer la note maximale du `Quiz3`.

<details>
<summary>Correction</summary>

```r
max(df$Quiz3, na.rm = TRUE)
```
</details>

9. Calculer la médiane du `Quiz2`. Que signifie cette valeur médiane par rapport à la moyenne ?

<details>
<summary>Correction</summary>

```r
median(df$Quiz2, na.rm = TRUE)
#50% ont plus de 11.05/20
```
</details>

10. Calculer les déciles du `Quiz3`. Quel pourcentage d'étudiant a eu 11 ou plus ?

<details>
<summary>Correction</summary>

```r
quantile(df$Quiz3, probs = seq(from = 0.1,
                               to = 0.9, 
                               by =0.1), 
         na.rm = TRUE)
#40% ont eu 11 ou plus.
```
</details>

11. Calculez l'écart-type pour chaque quiz. Qu'est ce qu'on peut dire sur les résultats ?

<details>
<summary>Correction</summary>

```r
sd(df$Quiz1, na.rm = TRUE)
sd(df$Quiz2, na.rm = TRUE)
sd(df$Quiz3, na.rm = TRUE)
#notes plus homogènes sur le quiz1 et le plus hétérogènes sur le quiz2
```
</details>

12. Calculer la réparition en effectif du nombre d'étudiant par groupe de TP. Dans quel groupe y a t-il le moins d'étudiant ?

<details>
<summary>Correction</summary>

```r
table(df$TP)
#le groupe de TP 22
```
</details>

13. Calculer cette répartition en pourcentage en arrondissant avec deux décimales

<details>
<summary>Correction</summary>

```r
round(prop.table(table(df$TP)), digits = 2)
```
</details>

## Exercice C : Extraction

Pour chaque question, pensez à afficher le résultat dans vue pour vérifier le résultat.

Pour chaque question, afficher le résultat de l'extraction dans un objet appelé `resultat` **avec uniquement la colonne `Identifiant` et les colonnes utilisées pour les filtres**.

14. Extraire les lignes avec les étudiants ayant une note strictement supérieur à 10/20 au quiz3. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, Quiz3 > 10)
resultat = resultat[ , c("Identifiant","Quiz3")]
nrow(resultat)
View(resultat)
```
</details>


15. Extraire les lignes avec les étudiants du groupe de TD 1. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, TD == 1)
resultat = resultat[ , c("Identifiant","TD")]
nrow(resultat)
View(resultat)
```
</details>

16. Extraire les lignes avec les étudiants différent du groupe de TP 21. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, TP != 21)
resultat = resultat[ , c("Identifiant","TP")]
nrow(resultat)
View(resultat)
```
</details>

17. Extraire les lignes avec les étudiants ayant une note égale ou comprise entre 5 et 10 au quiz 3. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, Quiz3 >= 5 & Quiz3 <= 10)
resultat = resultat[ , c("Identifiant","Quiz3")]
nrow(resultat)
View(resultat)
```
</details>

18. Extraire les lignes avec les étudiants qui ont les identifiants suivant : *92655100, 85947666, 75752354, 172596215, 111505723, 42690322, 20972010,43177455*.

<details>
<summary>Correction</summary>

```r
resultat = subset(df, Identifiant %in% c(92655100,
                                         85947666,
                                         75752354,
                                         172596215,
                                         111505723,
                                         42690322,
                                         20972010,
                                         43177455))
nrow(resultat)
```
</details>

19. Extraire les lignes avec tous les étudiants sauf ceux mentionnés dans la question précédente.

<details>
<summary>Correction</summary>

```r
resultat = subset(df, !Identifiant %in% c(92655100,
                                         85947666,
                                         75752354,
                                         172596215,
                                         111505723,
                                         42690322,
                                         20972010,
                                         43177455))
nrow(resultat)
```
</details>

20. Extraire les lignes avec les étudiants ayant une note supérieure ou égale à 15/20 à au moins un des 3 quiz. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, Quiz1 >= 15 | Quiz2 >= 15 | Quiz3 >= 15)
resultat = resultat[ , c("Identifiant","Quiz1","Quiz2","Quiz3")]
nrow(resultat)
View(resultat)
```
</details>

21. Extraire les lignes avec les étudiants absents au quiz1. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, is.na(Quiz1))
resultat = resultat[ , c("Identifiant","Quiz1")]
nrow(resultat)
View(resultat)
```
</details>

22. Extraire les lignes avec les étudiants qui n'ont jamais été absent. Combien d'étudiants sont dans l'extraction ?

<details>
<summary>Correction</summary>

```r
resultat = subset(df, !is.na(Quiz1) & !is.na(Quiz2) & !is.na(Quiz3))
resultat = resultat[ , c("Identifiant","Quiz1","Quiz2","Quiz3")]
nrow(resultat)
View(resultat)
```
</details>

## Exercice D : Top et Flop

Pour chaque question, afficher le résultat de l'extraction dans un objet appelé `resultat` **avec uniquement les colonnes pertinentes**.

23. Créer une nouvelle colonne appelée `Moyenne` qui correspond à la moyenne des 3 quiz ? Arrondir avec une décimale. Il y a des valeurs manquantes en cas d'absence mais ce n'est pas grave.

<details>
<summary>Correction</summary>

```r
df$Moyenne = round((df$Quiz1 + df$Quiz2 + df$Quiz3) / 3, digits = 1)
head(df)
```
</details>

24. Extraire les lignes avec les étudiants qui ont les 3 moyennes les plus basses.

<details>
<summary>Correction</summary>

```r
rang = order(df$Moyenne, decreasing = FALSE)
resultat = df[ rang, c("Identifiant","Moyenne")]
head(resultat, n = 3)
```
</details>

25. Extraire les lignes avec les étudiants qui ont les 3 moyennes les plus hautes

<details>
<summary>Correction</summary>

```r
rang = order(df$Moyenne, decreasing = TRUE)
resultat = df[ rang, c("Identifiant","Moyenne")]
head(resultat, n = 3)
```
</details>

26. Trier le tableau selon le groupe de TP **puis** par la moyenne du quiz de la plus haute à la plus basse les lignes avec les étudiants qui ont les 3 moyennes les plus hautes

<details>
<summary>Correction</summary>

```r
rang = order(df$TP, df$Moyenne, decreasing = c(FALSE,TRUE))
resultat = df[ rang, c("Identifiant","TP", "Moyenne")]
head(resultat, n = 5)
```
</details>

27. Agréger les données dans un tableau avec la moyenne de chaque groupe de TP.

<details>
<summary>Correction</summary>

```r
aggregate(Moyenne ~ TP,
          data = df, 
          FUN = function(x) c(moy = mean(x) ) )
```
</details>

28. Agréger les données dans un tableau avec le minimum, la moyenne, le maximum et les effectifs de chaque groupe de TD/TP.

<details>
<summary>Correction</summary>

```r
resultat = aggregate(Moyenne ~ TD + TP,
          data = df, 
          FUN = function(x) c(min = min(x),
                              moy = mean(x),
                              max = max(x),
                              eff = length(x) ) )
```
</details>

## Exercice E : Traitement de données

29. Avec la fonction adaptée, remplacer les valeurs manquantes de chaque quiz par la moyenne du quiz concerné. Recalculer la colonne `Moyenne` de la question `Exercice 4-a`.


<details>
<summary>Correction</summary>

```r
df$Quiz1 = ifelse(test = is.na(df$Quiz1), 
                  yes = mean(df$Quiz1, na.rm = TRUE),
                  no = df$Quiz1)

df$Quiz2 = ifelse(test = is.na(df$Quiz2), 
                  yes = mean(df$Quiz2, na.rm = TRUE),
                  no = df$Quiz2)

df$Quiz3 = ifelse(test = is.na(df$Quiz3), 
                  yes = mean(df$Quiz3, na.rm = TRUE),
                  no = df$Quiz3)

df$Moyenne = round((df$Quiz1 + df$Quiz2 + df$Quiz3) / 3, digits = 1)
```
</details>

30. Créer une nouvelle variable nommée `Moyenne_Classe` en regroupant en 5 tranches avec le minimum, maximum et les quartiles tels que : *[min,Q1] / (Q1,Q2] / (Q2,Q3] / (Q3,max]*. Calculer un résumé de la nouvelle colonne.

<details>
<summary>Correction</summary>

```r
df$Moyenne_Classe = cut(df$Moyenne,
                        breaks = quantile(df$Moyenne),
                        include.lowest = TRUE)
summary(df$Moyenne_Classe)
```
</details>

31. Quelle commande permet d'exporter ce nouveau dataframe dans un fichier `csv` appelé `exam_export` : 

- avec un `;` comme séparateur de colonnes
- avec une `,`  pour la décimale. 
- sans afficher les index de lignes

<details>
<summary>Correction</summary>

```r
write.table(x = df, file = "exam_export.csv", sep = ";", dec = ",", row.names = FALSE)
```
</details>

## Liens utiles

Voici quelques liens utiles :

- [Cours sur la programmation R](https://asardell.github.io/programmation-r/)




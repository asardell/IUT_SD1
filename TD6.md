# TD6

## Objectifs
Voici les objectifs de ce chapitre :
- [ ] Corriger des erreurs

Dans ce TP, vous incarnez un data analyst travaillant dans le service statistique de la NBA. Un de vos collègues est parti en vacances vendredi dernier et a envoyé à votre manager quelques statistiques sur les tirs effectués au cours de la saison 2014-2015. <br>
Le problème c'est que le script est bourré de fautes ! Rien ne fonctionne, à tous les coups, votre collègue était pressé de partir en vacance. Votre manager fait donc appel à vous pour corriger les erreurs de ce script. 

:warning: Votre manager aimerait également comprendre ce que vous programmez dans votre script alors n'oubliez pas de commenter chaque ligne de code pour qu'il la comprenne. 

Le fichier de données `NBA2014_2015.csv` est disponible dans le dossier `dataset`.
<br>

Votre manager a déjà passé beaucoup de temps pour comprendre ce script et aimerait que votre correction garde la même philosophie que le script de votre collègue, cela signifie qu'il ne faut pas écrire d'autres commandes R et simplement faire en sorte que celles déjà présentes fonctionnent.


:warning: L'ensemble des scripts à corriger sont à réaliser dans un seul script nommé `iut_sd1_r_td6`

## Exercice 1 - Importer les données

<details>
<summary>Script</summary>

```r
df <- read.csv(file = "nba2014_2015.csv", sep = ";",
               header = FALSE, dec = ";")
> nrow(nba)
> ncol(nba)
> colname(df)
> srt(df)
> df$Period <- as.factor(df$Period)
> df$PTSTYPE -> as.factor(df$PTSTYPE)
> df$SHOOTER = as.factor(df$shooter)
```
</details>

## Exercice 2 - Statistiques descriptives

<details>
<summary>Script</summary>

```r
> lenght(level(df$Period))
> lenght(df$PTSTYPE)
> lenght(df$SHOTER)
> summary(ddf)
> sd(DF$SHOT_DIST
> sd[df$SHOT_CLOCK]

#combien de tirs manqués/réussis
table(df[ "SHOT_RESULTS" , ])
#les quartiles
quantile(df$SHOT_CLOCK, probs = 4)
#les déciles
quantiles(df$CLOSE_DIST, probs = 10)
#nombre de matches différents
liste_game <- unique(df$GAME_ID))
length(listegame)
#nombre de joueurs différents
df$SHOOTER <- as_factor(df$SHOOTER)
nlevel(df$SHOOTER
#conversion de la variable SHOT_DIST en mètre pour que les européens comprennent nos chiffres
nba$SHOT_DIST_METRE == SHOT_DIST * 0.30
#nombre de points qu'a rapporté la tentative (0,2 ou 3)  
df$PTS_MARQUES <- ifelse(df$SHOT_RESULT = "made", yes = df$PTS_TYPE, 0)
#On supprime la variable GAME_RESULT car elle n'est pas utile
df$GAME_RESULT <- NUL
   
#création d'un objet sans la première colonne GAME_ID
df2 <- df[ -1  ,  ]
```
</details>

## Exercice 3 - Extractions

<details>
<summary>Script</summary>

```r
#Les 100 tirs réussis ou manqués les plus loin
rang <- order(df$SHOT_DIST, decreasing = FALSE)
df3 <- df[, rang]
df3 <- df[ 1 : 100 ; ]

#Les 100 tirs réussis les plus loin
df4 = subset(df3, SHOT_RESULT = made)
df4 <- df[ 1 : 100 ; ]

#Combien de tirs à 3 points a réussi Kobe Bryant ?
df_kobe = subset(df,SHOT_RESULT = made &
                 PTS_TYPE = 3 & 
                 SHOOTER = "Kobe BRYANT")

dim(df_kobe)

#Le TOP5 des joueurs qui ont marqués le plus de points dans la saison
df_total <- aggregate(PTS_MARQUES ~ SHOOTER, data = df, FUN = sum)
df_total_tri <- df_total[-order(df_total$PTS_MARQUES)]
df_top5 <-  df_total_tri[  5  ,  ]
```
</details>

## Exercice 4 - Automatisation

<details>
<summary>Script</summary>

```r
#Des graphiques adaptés selon le type de variable

#construction de la fonction
build_graph <- function(une_colonne, nom_colonne) {
  if(is.numeric(une_colonne)) {
    print(boxplot(une_colonne, main = nom_colonne))
  }
  else if (as.factor(une_colonne)) {
    tri <- table(une_colonne)
    print(barplot(tri, main = nom_colonne))
  }

#on déroule la fonction sur chaque colonne du data frame.

for (colonne in colnames(df) {
  build_graph(une_colonne = df[colonne , ] , nom_colonne = colone)
}
}
```
</details>
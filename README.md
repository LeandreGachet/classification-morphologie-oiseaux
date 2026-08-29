# Classification morphologique d'oiseaux sans étiquettes

Des mesures morphologiques d'oiseaux — longueurs, largeurs, masses. Peut-on retrouver des groupes d'espèces à partir de la seule forme des individus, sans jamais montrer à l'algorithme à quelle espèce ils appartiennent ?

Projet de Master en apprentissage non supervisé, en trinôme.

## Démarche

**Trois familles de méthodes**, choisies parce qu'elles ne font pas les mêmes hypothèses sur ce qu'est un groupe.

**K-means** — groupes sphériques de taille comparable. Nombre de classes choisi sur la courbe d'inertie intra-classe, avec 25 initialisations aléatoires pour ne pas rester coincé dans un optimum local.

**Classification ascendante hiérarchique**, critère de Ward. Pas de nombre de classes fixé d'avance : le dendrogramme montre à quelle hauteur les regroupements deviennent coûteux, et la coupure se discute.

**Mélange gaussien estimé par EM** (`Mclust`), testé de 1 à 15 composantes. Contrairement aux deux précédentes, cette méthode autorise des groupes de formes, d'orientations et de tailles différentes, et **choisit lui-même le nombre de composantes par critère d'information** — le nombre de classes devient un résultat, plus un réglage.

**Comparaison aux vraies espèces.** Les étiquettes existent, mais elles ne servent qu'après coup : à mesurer si les groupes trouvés correspondent à quelque chose de réel. C'est ce qui distingue une partition arbitraire d'une structure.

**Interprétation morphologique** des groupes obtenus — dire ce qui, dans les mesures, sépare les groupes.

## Ce que ça produit

Une comparaison argumentée de trois façons de définir un groupe, sur un cas où la réponse est vérifiable. La compétence exercée est celle du choix : savoir quelle méthode de classification correspond à la structure qu'on suppose dans les données, et savoir reconnaître qu'on s'est trompé.

## Contenu

| | |
|---|---|
| `code/notebook.Rmd` | l'analyse complète |

## Reproduire

```r
install.packages(c("tidyverse", "cluster", "factoextra", "mclust"))
rmarkdown::render("code/notebook.Rmd")
```

Les données de mesures morphologiques sont chargées en tête de notebook ; le chemin est à adapter.

## Co-auteurs

Projet réalisé avec Tangi Meyer et Théo Guérinel. Publié avec leur accord.

---

**Léandre Gachet** — Master Mathématiques appliquées, statistique, Université de Rennes

# SPÉCIFICATIONS APPLICATION TOURNOI DE PICKLEBALL À LA RONDE

---

## But de l’application

Gérer un tournoi de Pickleball comprenant 2 phases distinctes, soit :

**Rondes préliminaires** : Les joueurs sont jumelés au hasard avec d’autres joueurs dans la ronde préliminaire et accumulent des victoires et des points, sur une base individuelle (i.e. round robin individuel), en vue d’accéder aux séries

**Séries** : Les joueurs ayant accumulés le plus de victoires et la plus petite somme des différentiels dans les rondes préliminaires sont regroupés en équipe de 2 avec qui ils joueront jusqu’à la fin du tournoi. Les séries sont de type élimination directe.

---

## Enregistrements des joueurs

La liste des joueurs peut être importés en format CSV ou saisie directement dans l’application. Les informations suivantes sont requises :

- Nom  
- Prénom  
- Sexe : Homme, Femme  
- Age : XX ans  
- Niveau : 3,0, 3,5, 4,0,4,5, 5,0, novice, intermédiaire, avancé  
- Numéro de membre : (facultatif)

---

## Rondes préliminaires

Le but de la ronde préliminaire et permettre aux joueurs d’accumuler des victoires et points différentiels pour se qualifier pour les séries. Le système doit générer les parties de façon aléatoire fonction des critères suivants :

La constitution des catégories est effectuée selon les critères identifiés dans la grille suivantes :

1er critère : Sexe  
2ième critère : Age  
3ième critère : Niveau  

Dans l’éventualité ou il s’agit d’un tournoi ouvert, le critère d’âge n’est pas considéré

Le nombre de catégorie varie en fonction du nombre de participant dans chacune des catégories (ex : Homme et Femmes de niveau 3,0,3,5 et 4,0 sans considération d’âge donne 6 catégories).

Le nom des catégories est formé à partir des caractéristiques de la catégorie (ex : Homme, 20-45 ans, niveau 3,0)

Les joueurs sont jumelés de façon aléatoire à des joueurs de la même catégorie.

Chaque joueur doit jouer le même nombre de partie, tel que définie dans les paramètres globaux

Chaque joueur ne peut être jumelé qu’une fois avec le même partenaire et, autant que possible mais pas obligatoire, éviter de jouer contre les mêmes joueurs. L'algorithme doit privilégier la rotation des adversaires avant la rotation des partenaires pour maximiser l'aspect social du tournoi.

Si le nombre de joueurs dans une catégorie est impaire, le système doit gérer un ou des "Byes" (joueurs en attente ou de remplacement). Dans l’éventualité ou il y aurait des absences ou des blessures au moment du tournoi, des joueurs substituts pourraient agir à titre de remplaçant. L’administrateur devra renommer le joueur absent par substitut 1, substitut 2, etc. et ces joueurs ne pourront pas accumuler de points.

Les parties sont planifiées à un intervalle de XX minutes (voir paramètres globaux) et réparties en fonction du nombre de terrain (voir paramètres globaux)

Un joueur ne peut être dans 2 parties en même temps

Chaque joueur cumule des victoires et des points qui peuvent lui permettre d’attendre les séries, seuls les joueurs ayant le plus de victoires et des plus petits différentiels de points vont se rendre en série. Le calcul des points est effectué comme ceci :

Les deux joueurs d’une équipe ayant le plus haut score d’une partie ont chacun une victoire.

Pour les 2 joueurs de l’équipe perdante, on calcul l’écart entre le score de l’équipe gagnante et celui de l’équipe perdante que le nomme différentiel (ex : 11 à 8 = un différentiel de 3). Le but étant d’avoir le plus petit différentiel.

Le premier critère pour qualifier les joueurs pour les séries est :

Le nombre de victoire

La plus petite somme des différentiels des parties perdues. Par un joueur ayant cumulé 2 victoires et 2 défaites de 11-6 et 8-5 aurait un différentiel cumulé de 5+3=8.

Finalement, dans l’éventualité où il aurait toujours une égalité après l’application des 2 premiers critères, le joueur ayant accumulé le plus de points dans l’ensemble de ses parties servirait à départager l’égalité.

En cas d’égalité, le joueur ayant cumulé le plus grand nombre de points totaux marqués est priorisé.

Le système doit séquencer les joueurs de façon croissante et fournir la liste de joueurs qui feront partis des séries.

Le système doit générer automatiquement la cédule des parties et assigner un numéro de partie pour chaque partie dans un but de référence ultérieure. La cédule doit tenir compte des éléments suivants (voir paramètres globaux) :

- Nombre de joueurs par catégories  
- Nombre de terrains (avec les numéros ou les noms de terrain)  
- Temps alloué pour chaque partie  
- Période de latence  
- Heure de début du tournoi  
- Heure de début des séries  

Dans l’éventualité ou il y aurait moins de 8 joueurs pour former une catégorie, le système doit pouvoir aviser l’administrateur qui devra effectuer des changement (ex : changer des joueurs de catégorie). Le système devra refaire la cédule après ces changements.

Dans l’éventualité ou il n’y a que 8 joueurs dans une catégorie, les rondes préliminaires serviront à déterminer les équipes pour les séries puisque tous les joueurs feront partie des séries.

Le système doit pouvoir générer, en format PDF, un tableau permettant aux joueurs de visualiser leurs parties à venir (voir diagramme suivant).


| Heures | 10h15 | # | 10h30 | # | 10h45 | # | 11h | # |
|-------|-------|---|-------|---|-------|---|-----|---|
| **Terrain 1** | | | | | | | | |
| Équipe 1 | Boucher Daniel | 13 | L’Hérault Daniel | 13 | Brunet Alain | 12 | Dionne Christian | 7 |
|  | Lavoie Stéphane | 32 | Ruel Gilles | 14 | Langlais Stéphane | 10 | Boucher Daniel | 1 |
| Équipe 2 | Carrier François | 21 | Bourret Sylvain | 9 | L’Hérault Daniel | 13 | Lemay Richer | 16 |
|  | Lavigne Simon | 28 | Lamothe Sylvain | 26 | Audet Pierre | 29 | St-Onge Mario | 15 |
| **Terrain 2** | | | | | | | | |
| Équipe 1 | Bovet J. François | 3 | Godin Richard | 2 | Godin Richard | 2 | Rompré Stéphane | 8 |
|  | Boucher Jean-Marc | 23 | Franche Charles | 5 | Di Lalla Gino | 18 | Lacelle Robert | 24 |
| Équipe 2 | Lacelle Robert | 24 | Lemay Richer | 16 | Ruel Gilles | 14 | Faucher Bernard | 20 |
|  | Bérubé Luc | 25 | Bérubé Luc | 25 | Boucher Jean-Marc | 23 | Alarie Stéphane | 27 |
| **Terrain 3** | | | | | | | | |
| Équipe 1 | Franche Charles | 5 | Pelletier Sylvain | 17 | Bovet J. François | 3 | Bourret Sylvain | 9 |
|  | Ruel Gilles | 14 | Bourque Pierre | 6 | Longpré Robert | 11 | Boucher Jean-Marc | 23 |
| Équipe 2 | Bourque Pierre | 6 | Di Lalla Gino | 18 | Lavoie Stéphane | 32 | Carrier François | 21 |
|  | Audet Pierre | 29 | St-Onge Mario | 15 | Lévesque Marco | 31 | Lamothe Sylvain | 26 |
| **Terrain 4** | | | | | | | | |
| Équipe 1 | Dionne Christian | 7 | Garant Frédéric | 19 | Cartier Daniel | 4 | Langlais Stéphane | 10 |
|  | Di Lalla Gino | 18 | Cyr Michel | 30 | Bourret Sylvain | 9 | Bourque Pierre | 6 |
| Équipe 2 | Rompré Stéphane | 8 | Faucher Bernard | 20 | Garant Frédéric | 19 | Beauregard Daniel | 22 |
|  | Godin Richard | 2 | Audet Pierre | 29 | Lavigne Simon | 28 | Bérubé Luc | 25 |
| **Terrain 5** | | | | | | | | |
| Équipe 1 | Bourret Sylvain | 9 | Cartier Daniel | 4 | Franche Charles | 5 | Longpré Robert | 11 |
|  | Lévesque Marco | 31 | Brunet Alain | 12 | Alarie Stéphane | 27 | Lavigne Simon | 28 |
| Équipe 2 | Langlais Stéphane | 10 | Beauregard Daniel | 22 | Pelletier Sylvain | 17 | Bovet J. François | 3 |
|  | Pelletier Sylvain | 17 | Alarie Stéphane | 27 | Lacelle Robert | 24 | Franche Charles | 5 |



---

## Les séries

Les séries sont de type éliminatoire directe, l’équipe gagnante d’une partie se rend à la ronde suivante, l’autre est éliminée. Les joueurs ayant accumulés le plus de victoires et les plus petites sommes des différentiels lors de la ronde préliminaire participent aux séries dont le nombre varie en fonction du nombre de joueurs inscrit dans une catégorie.

Entre 8 et 19 joueurs inscrits dans une catégorie : les séries sont composées de 8 joueurs (demi et finale). Dans l’éventualité où il n’y aurait que 8 joueurs dans une catégorie, les rondes préliminaires serviraient à déterminer les équipes pour les séries puisque tous les joueurs feraient partie des séries.

Entre 20 et 75 joueurs inscrits dans une catégorie : les séries sont composées de 16 joueurs (quart de final, demi final et finale). Dans l’éventualité où il n’y aurait 16 joueurs dans une catégorie, les rondes préliminaires serviraient à déterminer les équipes pour les séries puisque tous les joueurs feraient partie des séries.

---

## Série à 8 joueurs

### Équipe / Joueurs

| Équipe | Joueurs |
|------|--------|
| Équipe 1 | Rang 1 + Rang 5 |
| Équipe 2 | Rang 3 + Rang 7 |
| Équipe 3 | Rang 2 + Rang 6 |
| Équipe 4 | Rang 4 + Rang 8 |

### Bracket

**DEMI-FINALES**  
DF1 : Équipe 1 (1+5) vs Équipe 3 (2+6) Score : ____ / ____  
DF2 : Équipe 2 (3+7) vs Équipe 4 (4+8) Score : ____ / ____

**FINALE**  
Championnat : Vainqueur DF1 vs Vainqueur DF2 Score : ____ / ____

---

## Série à 16 joueurs

### Équipe / Joueurs

| Équipe | Joueurs |
|------|--------|
| Équipe 1 | Rang 1 + Rang 9 |
| Équipe 2 | Rang 2 + Rang 10 |
| Équipe 3 | Rang 3 + Rang 11 |
| Équipe 4 | Rang 4 + Rang 12 |
| Équipe 5 | Rang 5 + Rang 13 |
| Équipe 6 | Rang 6 + Rang 14 |
| Équipe 7 | Rang 7 + Rang 15 |
| Équipe 8 | Rang 8 + Rang 16 |

**QUARTS DE FINALE**  
Q1 : Équipe 1 (1+9) vs Équipe 3 (3+11) Score : ____ / ____  
Q2 : Équipe 2 (2+10) vs Équipe 4 (4+12) Score : ____ / ____  
Q3 : Équipe 5 (5+13) vs Équipe 7 (7+15) Score : ____ / ____  
Q4 : Équipe 6 (6+14) vs Équipe 8 (8+16) Score : ____ / ____

**DEMI-FINALES**  
DF1 : Vainqueur Q1 vs Vainqueur Q2 Score : ____ / ____  
DF2 : Vainqueur Q3 vs Vainqueur Q4 Score : ____ / ____

**FINALE**  
Championnat : Vainqueur DF1 vs Vainqueur DF2 Score : ____ / ____

**MATCH POUR LA 3e PLACE**  
Perdant DF1 vs Perdant DF2 Score : ____ / ____

---

## Paramètres globaux

Nom du tournoi : Défini par l’administrateur (ex : Meli-Melo Terrebonne 2026)  
Durée de la ronde préliminaire : HH:MM (ex : 03:30)  
Heure de début du tournoi : HH:MM (ex : 09:00)  
Heure de début des séries : HH:MM (13:30)  
Période de latence fixe (ex : diner) : prévoir la possibilité d’avoir jusqu’à 3 périodes de latence fixe en respectant le format suivant : entre HH:MM et HH:MM (entre 12:00 et 13:00)  
Nombre de terrain : Nombre de terrain disponible pour le tournoi et possibilité de les nommer  
Nombre de partie par joueur de la ronde préliminaire : Numérique (ex : 4)  
Nombre de minutes d’une partie des rondes préliminaires : XX minutes  
Identification des parties : Les parties doivent être identifiées (ID)

---

## Parcours de l’utilisateur

- Créer le tournoi  
- Configurer paramètres globaux  
- Importer ou saisir les joueurs  
- Générer rondes préliminaires  
- Générer et imprimer tableau des rondes préliminaires (PDF)  
- Saisir scores rondes préliminaires  
- Générer séries  
- Valider et confirmer participants aux séries  
- Générer et imprimer tableau des séries (PDF)  
- Saisir scores des séries  
- Imprimer résultats finaux

---

## Rôles

**Administrateur**

- Peut modifier les paramètres globaux  
- Peut modifier, supprimer des parties et les résultats  
- Peut modifier la catégorie des joueurs  
- Peut modifier l’ordre des participants aux séries  

**Superviseur**

- Peut modifier, supprimer et créer des joueurs  
- Peut ajouter et modifier les résultats des parties

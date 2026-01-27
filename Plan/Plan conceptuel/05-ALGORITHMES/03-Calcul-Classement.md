# Algorithme: Calcul du Classement

## Objectif
Calculer le classement des joueurs d'une catégorie en temps réel, basé sur les résultats des matchs des rondes préliminaires.

---

## Entrées Requises

1. **Liste des matchs terminés** pour une catégorie
2. **Liste des joueurs** de cette catégorie
3. **Scores de chaque match** (score équipe A, score équipe B)

---

## Sortie

Liste ordonnée des joueurs avec:
- Rang (position au classement)
- Nombre de victoires
- Différentiel (points marqués - points encaissés)
- Total de points marqués
- Nombre de matchs joués

---

## Critères de Classement (Ordre de Priorité)

### 1. Nombre de Victoires (Décroissant)
Le joueur avec le plus de victoires est classé premier.

### 2. Différentiel de Points (Décroissant)
À victoires égales, celui avec le meilleur différentiel (points marqués - points encaissés) est devant.

### 3. Points Marqués (Décroissant)
À victoires et différentiel égaux, celui qui a marqué le plus de points est devant.

### 4. Ex-Æquo
Si deux joueurs sont égaux sur les 3 critères, ils partagent le même rang.

---

## Logique de l'Algorithme

### Phase 1: Calcul des Statistiques par Joueur

Pour chaque joueur, initialiser:
- victoires = 0
- defaites = 0
- points_marques = 0
- points_encaisses = 0
- matchs_joues = 0

Pour chaque match terminé:

**1. Identifier les joueurs**
- Équipe A: Joueur 1 + Joueur 2
- Équipe B: Joueur 3 + Joueur 4

**2. Déterminer le gagnant**
- Si score_A > score_B → Équipe A gagne
- Si score_B > score_A → Équipe B gagne

**3. Mettre à jour les statistiques**

Pour les joueurs de l'équipe gagnante:
- victoires += 1
- points_marques += score_gagnant
- points_encaisses += score_perdant
- matchs_joues += 1

Pour les joueurs de l'équipe perdante:
- defaites += 1
- points_marques += score_perdant
- points_encaisses += score_gagnant
- matchs_joues += 1

**4. Calculer le différentiel**
- differentiel = points_marques - points_encaisses

### Phase 2: Tri des Joueurs

Trier la liste des joueurs avec les critères suivants (dans l'ordre):

1. **Victoires** en ordre décroissant
2. Si égalité: **Différentiel** en ordre décroissant
3. Si encore égalité: **Points marqués** en ordre décroissant
4. Si toujours égalité: **Même rang** (ex-æquo)

### Phase 3: Attribution des Rangs

Parcourir la liste triée et attribuer les rangs:

```
rang_actuel = 1
joueurs_meme_rang = 0

Pour chaque joueur dans la liste triée:
    Si joueur a les mêmes stats que le précédent:
        joueur.rang = rang_actuel
        joueurs_meme_rang += 1
    Sinon:
        rang_actuel += joueurs_meme_rang + 1
        joueur.rang = rang_actuel
        joueurs_meme_rang = 0
```

---

## Gestion des Cas Spéciaux

### Joueur Substitut

Les joueurs marqués comme substituts:
- Leurs statistiques sont calculées normalement
- Ils n'apparaissent PAS dans le classement principal
- Ils peuvent être affichés dans une section séparée "Substituts"

### Match Annulé

Un match annulé:
- N'est pas compté dans les statistiques
- Les joueurs concernés n'ont pas de victoire/défaite pour ce match
- Leur nombre de matchs joués n'est pas incrémenté

### Joueur qui a Manqué un Match

Si un joueur a été remplacé par un substitut:
- Le joueur original n'a pas les stats du match
- Le substitut a les stats mais pas au classement
- Indiquer dans le classement: "2/3 matchs joués"

---

## Exemple Concret

**4 joueurs: A, B, C, D - 3 rondes jouées**

| Match | Score | Gagnant |
|-------|-------|---------|
| R1: A+B vs C+D | 11-7 | A+B |
| R2: A+C vs B+D | 9-11 | B+D |
| R3: A+D vs B+C | 11-8 | A+D |

**Statistiques calculées:**

| Joueur | V | D | PM | PE | Diff |
|--------|---|---|----|----|------|
| A | 2 | 1 | 31 | 26 | +5 |
| B | 2 | 1 | 29 | 27 | +2 |
| C | 1 | 2 | 24 | 31 | -7 |
| D | 1 | 2 | 26 | 30 | -4 |

**Classement:**

1. **A** — 2V, +5, 31 pts
2. **B** — 2V, +2, 29 pts
3. **D** — 1V, -4, 26 pts
4. **C** — 1V, -7, 24 pts

---

## Mise à Jour en Temps Réel

### Déclencheur

Le classement est recalculé:
- Après chaque saisie de score
- Après chaque modification de score
- Après annulation d'un match

### Optimisation

Au lieu de tout recalculer:
- Recalculer uniquement les stats des 4 joueurs du match modifié
- Re-trier la liste complète (rapide si déjà presque triée)

---

## Diagramme de Flux

```
┌─────────────────────────────────┐
│ Entrée: Liste des matchs       │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour chaque joueur:            │
│ Initialiser stats à 0          │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour chaque match terminé:     │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Identifier gagnants/perdants   │
│ Mettre à jour V, D, PM, PE     │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Calculer différentiel          │
│ (PM - PE) pour chaque joueur   │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Trier par:                     │
│ 1. Victoires (desc)            │
│ 2. Différentiel (desc)         │
│ 3. Points marqués (desc)       │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Attribuer les rangs            │
│ (gérer les ex-æquo)            │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Sortie: Classement ordonné     │
└─────────────────────────────────┘
```

---

## Cas des Ex-Æquo

### Attribution des Rangs avec Ex-Æquo

Si 2 joueurs sont ex-æquo au 3e rang:

| Rang | Joueur | V | Diff | Pts |
|------|--------|---|------|-----|
| 1 | A | 3 | +10 | 33 |
| 2 | B | 2 | +5 | 28 |
| 3 | C | 1 | -3 | 22 |
| 3 | D | 1 | -3 | 22 |
| 5 | E | 0 | -9 | 18 |

Note: Pas de 4e rang, on passe directement au 5e.

---

## Affichage Final

Le classement doit montrer:

| Rang | Joueur | V/D | Diff | Pts | Matchs |
|------|--------|-----|------|-----|--------|
| 🥇 | Tremblay, Jean | 3/0 | +10 | 33 | 3/3 |
| 🥈 | Lavoie, Pierre | 2/1 | +5 | 28 | 3/3 |
| 🥉 | Martin, Luc | 1/2 | -3 | 22 | 3/3 |
| 4 | Roy, Marc | 0/3 | -12 | 15 | 3/3 |

Médailles pour le top 3.
Indication du nombre de matchs joués sur le total.

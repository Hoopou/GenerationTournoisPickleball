# Algorithme: Jumelage et Génération des Rondes

## Objectif
Générer la cédule des rondes préliminaires en respectant les contraintes du Méli-Mélo:
- Chaque joueur change de partenaire à chaque ronde
- Un même duo de partenaires ne peut se répéter
- Maximiser la rotation des adversaires

---

## Entrées Requises

1. **Liste des joueurs d'une catégorie** (tous actifs)
2. **Nombre de terrains disponibles** pour cette catégorie
3. **Nombre de rondes souhaitées**
4. **Heure de début** du tournoi
5. **Durée estimée par match**
6. **Pauses planifiées** (optionnel)

---

## Sortie

Liste ordonnée de rondes, chaque ronde contenant:
- Liste des matchs (4 joueurs par match)
- Assignation des terrains
- Horaire de chaque match

---

## Contraintes Fondamentales

### Contrainte 1: Unicité des Partenaires
> Deux joueurs ne peuvent être partenaires qu'UNE SEULE FOIS dans tout le tournoi.

### Contrainte 2: Rotation des Adversaires
> Avant de réaffronter un adversaire, on doit avoir affronté le maximum d'autres joueurs.

### Contrainte 3: Équilibre des Matchs
> Chaque joueur doit jouer le même nombre de matchs (autant que possible).

### Contrainte 4: Pas de Repos Consécutifs
> Si un joueur ne joue pas une ronde (nombre impair), il doit jouer la suivante.

---

## Logique de l'Algorithme

### Phase 1: Préparation

**1.1. Calculer les Paramètres**

Soit N = nombre de joueurs dans la catégorie:
- Matchs par ronde = N ÷ 4 (arrondi inférieur)
- Joueurs en repos par ronde = N mod 4
- Maximum théorique de rondes = N - 1 (chaque joueur a été partenaire avec tous les autres une fois)

**1.2. Créer la Matrice des Partenariats**

Une matrice N × N où:
- matrice[i][j] = 0 si les joueurs i et j n'ont jamais été partenaires
- matrice[i][j] = 1 si les joueurs i et j ont déjà été partenaires

Initialement: toute la matrice est à 0.

**1.3. Créer la Matrice des Affrontements**

Une matrice N × N où:
- matrice[i][j] = nombre de fois que i et j se sont affrontés

Initialement: toute la matrice est à 0.

### Phase 2: Génération des Rondes

Pour chaque ronde R de 1 à nombre_rondes:

**2.1. Sélection des Joueurs Disponibles**

- Si N mod 4 ≠ 0: Certains joueurs seront en repos
- Priorité de repos aux joueurs qui ont joué la ronde précédente
- Ne jamais mettre le même joueur en repos deux fois de suite

**2.2. Formation des Équipes pour la Ronde**

Répéter jusqu'à ce que tous les joueurs disponibles soient assignés:

a) **Sélectionner le premier joueur non-assigné** (Joueur A)

b) **Trouver le meilleur partenaire** (Joueur B):
   - DOIT être un joueur non-assigné
   - DOIT ne jamais avoir été partenaire avec A (matrice_partenaires[A][B] = 0)
   - PRÉFÉRER un joueur avec qui A a été le moins souvent adversaire

c) **Trouver les adversaires** (Joueurs C et D):
   - DOIVENT être des joueurs non-assignés
   - DOIVENT ne jamais avoir été partenaires entre eux
   - PRÉFÉRER des joueurs que A et B ont le moins affronté

d) **Créer le match**: (A + B) vs (C + D)

e) **Mettre à jour les matrices**:
   - matrice_partenaires[A][B] = 1
   - matrice_partenaires[C][D] = 1
   - matrice_affrontements[A][C] += 1
   - matrice_affrontements[A][D] += 1
   - matrice_affrontements[B][C] += 1
   - matrice_affrontements[B][D] += 1

**2.3. Assignation des Terrains**

- Assigner les matchs aux terrains disponibles
- Si plus de matchs que de terrains: Certains matchs attendront la prochaine vague

**2.4. Calcul des Horaires**

- Match 1: Heure de début
- Matchs suivants: + durée_match (ou nouvelle vague si terrains saturés)
- Insérer les pauses selon la configuration

### Phase 3: Validation

Vérifier que:
- Aucun duo de partenaires n'est répété
- Chaque joueur a joué le nombre de matchs prévu
- Les horaires sont cohérents

---

## Gestion des Cas Spéciaux

### Nombre de Joueurs Non Multiple de 4

| Joueurs | Comportement |
|---------|--------------|
| 4 | 1 match par ronde, tout le monde joue |
| 5 | 1 match par ronde, 1 joueur en repos tournant |
| 6 | 1 match par ronde, 2 joueurs en repos OU 1 match + 1 trio? |
| 7 | 1 match par ronde, 3 joueurs en repos |
| 8 | 2 matchs par ronde, tout le monde joue |

**Stratégie pour les repos:**
- Faire tourner équitablement
- Prioriser les joueurs qui ont joué plusieurs rondes consécutives

### Impossibilité de Trouver un Partenaire Valide

Si aucun partenaire valide n'existe (tous les autres ont déjà été partenaires):
- **Option A**: Terminer la génération (nombre de rondes limité)
- **Option B**: Autoriser une exception avec avertissement

### Trop de Rondes Demandées

Pour N joueurs, le maximum théorique est N-1 rondes.
- Si l'utilisateur demande plus: Afficher un avertissement
- Proposer le maximum possible

---

## Optimisation de la Rotation des Adversaires

### Critère de Sélection des Adversaires

Score de préférence = Σ (affrontements avec A et B)

Plus le score est BAS, meilleurs sont les adversaires (moins de répétitions).

### Exemple

Joueurs A et B forment une équipe.
Candidats adversaires: C+D ou E+F

| Adversaires | Affrontements A | Affrontements B | Score |
|-------------|-----------------|-----------------|-------|
| C+D | A-C: 1, A-D: 0 | B-C: 0, B-D: 1 | 2 |
| E+F | A-E: 0, A-F: 0 | B-E: 0, B-F: 0 | 0 |

→ Choisir E+F (score 0)

---

## Diagramme de Flux Simplifié

```
┌─────────────────────────────────┐
│ Entrée: N joueurs, R rondes    │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Initialiser matrices           │
│ (partenaires = 0, affront. = 0)│
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour ronde = 1 à R:            │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Déterminer joueurs en repos    │
│ (si N mod 4 ≠ 0)               │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Tant que joueurs non-assignés: │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ 1. Prendre joueur A            │
│ 2. Trouver partenaire B        │
│    (jamais partenaires avant)  │
│ 3. Trouver adversaires C+D     │
│    (C,D jamais partenaires)    │
│ 4. Créer match                 │
│ 5. Mettre à jour matrices      │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Assigner terrains et horaires  │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Ronde suivante...              │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Valider et retourner cédule    │
└─────────────────────────────────┘
```

---

## Exemple Concret

**8 joueurs (A, B, C, D, E, F, G, H), 4 rondes, 2 terrains**

**Ronde 1:**
- Terrain 1: A+B vs C+D
- Terrain 2: E+F vs G+H

**Ronde 2:** (A ne peut plus être avec B, E ne peut plus être avec F, etc.)
- Terrain 1: A+C vs B+E
- Terrain 2: D+F vs G+H? Non! G+H déjà partenaires!
- Terrain 2: D+G vs F+H

**Ronde 3:**
- Terrain 1: A+D vs B+F
- Terrain 2: C+E vs G+H? Non encore!
- Terrain 2: C+G vs E+H

**Ronde 4:**
- Terrains 1 & 2: Continuer avec les combinaisons restantes

---

## Messages d'Erreur

| Situation | Message |
|-----------|---------|
| Moins de 4 joueurs | "Minimum 4 joueurs requis pour générer une cédule." |
| Aucun partenaire disponible | "Impossible de générer plus de X rondes avec ces joueurs." |
| Conflit de partenaires | "Erreur interne: tentative de re-partenariat de X et Y." |

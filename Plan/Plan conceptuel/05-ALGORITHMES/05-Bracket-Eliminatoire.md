# Algorithme: Génération du Bracket Éliminatoire

## Objectif
Générer l'arbre d'élimination (bracket) pour les séries, en positionnant les équipes de manière à éviter que les mieux classées s'affrontent trop tôt.

---

## Entrées Requises

1. **Liste des équipes** formées (avec leur "seed" basé sur le meilleur joueur)
2. **Format d'élimination**: Simple ou Double
3. **Nombre de terrains** disponibles pour les séries

---

## Sortie

Structure du bracket avec:
- Tous les matchs définis (qui affronte qui à chaque tour)
- Progression des gagnants
- (Double élimination) Bracket des perdants

---

## Concept du Seeding

### Qu'est-ce que le Seed?

Le "seed" d'une équipe est déterminé par le classement de son meilleur joueur:
- Équipe avec joueur #1 → Seed 1
- Équipe avec joueur #2 → Seed 2
- etc.

### Pourquoi le Seeding?

Éviter que les 2 meilleures équipes s'affrontent au premier tour.
Idéalement, elles se rencontrent seulement en finale.

---

## Bracket Élimination Simple

### Structure pour 4 Équipes

```
       DEMI-FINALES              FINALE
       
       Seed 1 ─────┐
                   ├───── Gagnant DF1 ─────┐
       Seed 4 ─────┘                       │
                                           ├───── CHAMPION
       Seed 2 ─────┐                       │
                   ├───── Gagnant DF2 ─────┘
       Seed 3 ─────┘
```

**Placement:**
- DF1: Seed 1 vs Seed 4
- DF2: Seed 2 vs Seed 3
- Finale: Gagnant DF1 vs Gagnant DF2

### Structure pour 8 Équipes

```
      QUARTS             DEMI               FINALE

      Seed 1 ─┐
              ├─ G1 ─┐
      Seed 8 ─┘      │
                     ├─ GDF1 ─┐
      Seed 4 ─┐      │        │
              ├─ G2 ─┘        │
      Seed 5 ─┘               │
                              ├─── CHAMPION
      Seed 2 ─┐               │
              ├─ G3 ─┐        │
      Seed 7 ─┘      │        │
                     ├─ GDF2 ─┘
      Seed 3 ─┐      │
              ├─ G4 ─┘
      Seed 6 ─┘
```

**Placement Quarts:**
- Q1: Seed 1 vs Seed 8
- Q2: Seed 4 vs Seed 5
- Q3: Seed 2 vs Seed 7
- Q4: Seed 3 vs Seed 6

---

## Logique de Placement (Puissance de 2)

### Formule Standard

Pour un bracket de taille N (N = puissance de 2):

Le seed 1 affronte le seed N au premier tour.
Le seed 2 affronte le seed N-1.
etc.

Position dans le bracket selon la formule:
```
Position(seed) détermine où placer l'équipe pour que:
- Seed 1 et 2 ne se rencontrent qu'en finale
- Seed 1, 2, 3, 4 ne se rencontrent qu'en demi ou finale
```

### Table de Placement pour 8 Équipes

| Seed | Position Bracket | Adversaire 1er tour |
|------|------------------|---------------------|
| 1 | Haut du bracket haut | 8 |
| 2 | Haut du bracket bas | 7 |
| 3 | Bas du bracket bas | 6 |
| 4 | Bas du bracket haut | 5 |
| 5 | Bas du bracket haut | 4 |
| 6 | Bas du bracket bas | 3 |
| 7 | Haut du bracket bas | 2 |
| 8 | Haut du bracket haut | 1 |

---

## Gestion du Nombre Non-Puissance de 2

### Cas: 6 Équipes

Problème: 6 n'est pas une puissance de 2 (4 ou 8).

**Solution: Byes (exemptions)**

Les 2 meilleures équipes passent directement en demi-finale:

```
      PREMIER TOUR          DEMI               FINALE

      Seed 1 ────────────── (Bye) ─────┐
                                       ├─ GDF1 ─┐
      Seed 4 ─┐                        │        │
              ├─ Gagnant ──────────────┘        │
      Seed 5 ─┘                                 │
                                                ├─── CHAMPION
      Seed 2 ────────────── (Bye) ─────┐        │
                                       ├─ GDF2 ─┘
      Seed 3 ─┐                        │
              ├─ Gagnant ──────────────┘
      Seed 6 ─┘
```

**Règle des Byes:**
- Nombre de byes = Prochaine puissance de 2 - Nombre d'équipes
- Pour 6 équipes: 8 - 6 = 2 byes
- Les byes vont aux meilleurs seeds (1 et 2)

### Cas: 5 Équipes

3 byes (8 - 5 = 3):
- Seeds 1, 2, 3 ont un bye
- Seuls seeds 4 et 5 jouent au premier tour

### Cas: 7 Équipes

1 bye (8 - 7 = 1):
- Seed 1 a un bye
- Les autres jouent au premier tour

---

## Algorithme de Génération

### Étape 1: Déterminer la Taille du Bracket

```
N = nombre d'équipes
taille_bracket = plus petite puissance de 2 >= N
byes = taille_bracket - N
```

### Étape 2: Attribuer les Byes

```
Pour i de 1 à byes:
    equipe[seed i] reçoit un bye
```

### Étape 3: Créer les Matchs du Premier Tour

```
matchs_premier_tour = (N - byes) / 2

Pour chaque match:
    Placer selon la formule de seeding
    Équipe haute seed vs Équipe basse seed complémentaire
```

### Étape 4: Créer les Tours Suivants

```
Pour chaque tour suivant:
    matchs_tour = matchs_tour_precedent / 2
    Chaque match reçoit les gagnants des 2 matchs précédents
```

### Étape 5: Définir la Finale

```
finale = {
    equipe_A: gagnant_demi_1,
    equipe_B: gagnant_demi_2
}
```

---

## Bracket Élimination Double (Optionnel)

### Principe

- Un joueur éliminé passe dans le "Loser's Bracket"
- Il faut perdre 2 fois pour être définitivement éliminé
- Le gagnant du Winner's Bracket affronte le gagnant du Loser's Bracket en finale

### Structure Simplifiée (4 équipes)

```
WINNER'S BRACKET               LOSER'S BRACKET

W1: S1 vs S4 ─┐
              ├─ W_Final ──┐     L1: Perdant W1 ─┐
W2: S2 vs S3 ─┘            │                     ├─ L_Final
                           │     L2: Perdant W2 ─┘     │
                           │                           │
                           └─── GRANDE FINALE ─────────┘
```

### Gestion de la Grande Finale

- Si le gagnant du Winner's Bracket gagne → Champion
- Si le gagnant du Loser's Bracket gagne → Match décisif (car le Winner n'a perdu qu'une fois)

---

## Horaires et Terrains

### Assignation des Horaires

```
heure_courante = heure_debut_series

Pour chaque tour (du premier au dernier):
    Pour chaque match du tour:
        Si terrain_disponible:
            match.heure = heure_courante
            match.terrain = terrain_libre
        Sinon:
            heure_courante += duree_match
            (réassigner les terrains)
```

### Contrainte de Progression

Un match ne peut pas commencer avant que les matchs qui le précèdent soient terminés.

---

## Diagramme de Flux

```
┌─────────────────────────────────┐
│ Entrée: N équipes avec seeds   │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Calculer taille bracket        │
│ (prochaine puissance de 2)     │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Calculer byes = taille - N     │
│ Attribuer aux meilleurs seeds  │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Créer matchs premier tour      │
│ selon formule de seeding       │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Créer structure tours suivants │
│ (gagnants progressent)         │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Assigner terrains et horaires  │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Sortie: Bracket complet        │
└─────────────────────────────────┘
```

---

## Exemple Complet: 6 Équipes

**Équipes:**
- Seed 1: Tremblay + Côté
- Seed 2: Lavoie + Morin
- Seed 3: Martin + Dubois
- Seed 4: Roy + Gagnon
- Seed 5: Pelletier + Fortin
- Seed 6: Girard + Boucher

**Calculs:**
- Taille bracket: 8 (prochaine puissance de 2)
- Byes: 8 - 6 = 2
- Byes pour: Seed 1 et Seed 2

**Bracket Généré:**

```
Premier Tour (11:00):
  - Match 1: Seed 3 (Martin+Dubois) vs Seed 6 (Girard+Boucher) → Terrain 1
  - Match 2: Seed 4 (Roy+Gagnon) vs Seed 5 (Pelletier+Fortin) → Terrain 2

Demi-finales (11:15):
  - DF1: Seed 1 (Tremblay+Côté) vs Gagnant Match 2 → Terrain 1
  - DF2: Seed 2 (Lavoie+Morin) vs Gagnant Match 1 → Terrain 2

Finale (11:30):
  - Gagnant DF1 vs Gagnant DF2 → Terrain 1
```

---

## Mise à Jour du Bracket

### Après Chaque Match

1. Enregistrer le score
2. Déterminer le gagnant
3. Placer le gagnant dans le match suivant
4. Si finale → Déterminer le champion

### Affichage Dynamique

- Matchs à venir: Montrer "Gagnant Match X"
- Matchs connus: Montrer les noms des équipes
- Matchs terminés: Montrer score et indicateur gagnant

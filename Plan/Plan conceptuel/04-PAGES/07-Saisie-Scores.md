# Page: Saisie des Scores

## Objectif
Permettre la saisie rapide et efficace des scores de chaque match, avec validation en temps réel et mise à jour automatique du classement.

---

## Accès
- **Rôles**: Administrateur (tout), Superviseur (saisie et modification)
- **Accès**: Modale depuis la cédule ou page dédiée

---

## Modes d'Accès à la Saisie

### 1. Depuis la Cédule (Recommandé)
- Clic sur un match "À jouer" → Modale de saisie
- Clic sur "Saisir score" → Modale de saisie

### 2. Page Dédiée "Saisie Rapide"
- Menu: Tournoi > Saisie des scores
- Vue optimisée pour saisie en masse

---

## Modale de Saisie de Score

### Affichage Standard

```
┌─────────────────────────────────────────────────────────────────┐
│  SAISIR LE SCORE                                                │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Match #12 - Ronde 2, Terrain 1                                │
│  Catégorie: Homme - 35-50 - 3.5                                │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │    ÉQUIPE A                      ÉQUIPE B               │   │
│  │    ─────────                     ─────────              │   │
│  │    Tremblay, Jean                Martin, Luc            │   │
│  │    Lavoie, Pierre                Roy, Marc              │   │
│  │                                                         │   │
│  │         ┌───────┐                   ┌───────┐           │   │
│  │         │       │       VS          │       │           │   │
│  │         │  11   │                   │   8   │           │   │
│  │         │       │                   │       │           │   │
│  │         └───────┘                   └───────┘           │   │
│  │                                                         │   │
│  │    ✅ Victoire                      Défaite             │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ⚠️ Le score de 11 points est requis pour gagner              │
│                                                                 │
│              [Annuler]  [Enregistrer]  [→ Match suivant]       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Champs de Score

| Élément | Description |
|---------|-------------|
| Score Équipe A | Champ numérique, 0-99 |
| Score Équipe B | Champ numérique, 0-99 |
| Indicateur victoire | Affiché automatiquement selon les scores |

---

## Règles de Validation des Scores

### Score Valide

1. **Un gagnant doit avoir au moins 11 points**
   - Score gagnant: minimum 11
   - Exception: prolongation (pas de limite max)

2. **Écart minimum de 2 points**
   - 11-9 ✅ Valide
   - 11-10 ❌ Invalide (écart de 1)
   - 12-10 ✅ Valide (prolongation)
   - 15-13 ✅ Valide (prolongation)

3. **Les deux scores ne peuvent pas être identiques**
   - 11-11 ❌ Invalide
   - 0-0 ❌ Invalide (sauf annulation)

### Messages de Validation

| Situation | Message |
|-----------|---------|
| Score < 11 pour gagnant | "Le score gagnant doit être d'au moins 11." |
| Écart < 2 | "L'écart doit être d'au moins 2 points." |
| Scores égaux | "Les scores ne peuvent pas être égaux." |
| Score négatif | "Le score ne peut pas être négatif." |

### Indicateurs Visuels

```
Score valide:     ✅ 11 - 8
Score prolongation: ℹ️ 15 - 13 (prolongation)
Score invalide:   ❌ 11 - 10 "Écart insuffisant"
```

---

## Comportements de la Saisie

### Saisie au Clavier

- **Tab**: Passer au champ suivant
- **Enter**: Enregistrer et fermer (si valide)
- **Shift+Enter**: Enregistrer et passer au match suivant
- **Escape**: Annuler et fermer

### Auto-complétion

- Si un score de 11+ est saisi et l'autre est vide, focus sur l'autre champ
- Validation en temps réel pendant la saisie

### Navigation Rapide

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│  [← Match précédent]                        [Match suivant →]  │
│                                                                 │
│  Match 12 sur 24 (Ronde 2)                                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Page Saisie Rapide

### Affichage

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  SAISIE RAPIDE DES SCORES                                                   │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Catégorie: [Homme - 35-50 - 3.5     ▼]   Ronde: [Ronde 2 (en cours)   ▼] │
│                                                                             │
│  Matchs de la Ronde 2 - 3 sur 6 terminés                                   │
│  ───────────────────────────────────────                                    │
│                                                                             │
│  ┌────────┬───────────────────────────────────────────┬────────┬────────┐  │
│  │ Terr.  │ Match                                     │ Score  │ Statut │  │
│  ├────────┼───────────────────────────────────────────┼────────┼────────┤  │
│  │   1    │ Tremblay+Lavoie vs Martin+Roy            │ [  ]-[ ]│ 🕐     │  │
│  │   2    │ Gagnon+Dubois vs Morin+Côté              │ [11]-[8]│ ✅     │  │
│  │   3    │ Pelletier+Fortin vs Girard+Boucher       │ [  ]-[ ]│ 🕐     │  │
│  │   4    │ Lemieux+Nadeau vs Poirier+Simard         │ [11]-[5]│ ✅     │  │
│  │   5    │ Bergeron+Ouellet vs Gagné+Caron          │ [  ]-[ ]│ 🕐     │  │
│  │   6    │ Bélanger+Lévesque vs Beaulieu+Carrier    │ [9]-[11]│ ✅     │  │
│  └────────┴───────────────────────────────────────────┴────────┴────────┘  │
│                                                                             │
│  [Tout valider]                                                             │
│                                                                             │
│  Progression de la ronde: ████████░░░░ 50%                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Fonctionnalités

1. **Saisie directe**: Taper les scores directement dans la grille
2. **Tab pour naviguer**: Entre les champs de score
3. **Validation en masse**: Bouton "Tout valider" pour enregistrer tous les scores modifiés
4. **Auto-save optionnel**: Enregistrement automatique après quelques secondes

---

## Modification d'un Score

### Accès

- Clic sur un match déjà terminé
- Bouton "Modifier score" dans le détail du match

### Modale de Modification

```
┌─────────────────────────────────────────────────────────────────┐
│  MODIFIER LE SCORE                                              │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Match #12 - Ronde 2, Terrain 1                                │
│                                                                 │
│  Score actuel: 11 - 8                                          │
│                                                                 │
│  Nouveau score:                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │    Équipe A                      Équipe B               │   │
│  │    ┌───────┐                     ┌───────┐              │   │
│  │    │  11   │       VS            │   9   │              │   │
│  │    └───────┘                     └───────┘              │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Raison de la modification:                                     │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Erreur de saisie initiale                               │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ⚠️ La modification sera journalisée                          │
│                                                                 │
│              [Annuler]  [Enregistrer la modification]          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Journalisation

Toute modification de score est enregistrée:
- Date/heure de la modification
- Utilisateur qui a modifié
- Score avant / Score après
- Raison donnée

---

## Saisie pour Substitut

### Comportement Spécial

Quand un joueur substitut participe au match:

```
┌─────────────────────────────────────────────────────────────────┐
│  SAISIR LE SCORE                                                │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  ℹ️ Ce match inclut un substitut                               │
│     Le score compte pour les adversaires mais pas pour         │
│     le classement du substitut.                                │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │    ÉQUIPE A                      ÉQUIPE B               │   │
│  │    ─────────                     ─────────              │   │
│  │    Tremblay, Jean                Martin, Luc            │   │
│  │    [Substitut 1] 🔄              Roy, Marc              │   │
│  │                                                         │   │
│  │         ┌───────┐                   ┌───────┐           │   │
│  │         │  11   │       VS          │   7   │           │   │
│  │         └───────┘                   └───────┘           │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Impact:                                                        │
│  • Tremblay: +1 victoire, +4 diff, +11 pts                     │
│  • [Substitut 1]: Pas de points (substitut)                    │
│  • Martin: +1 défaite, -4 diff, +7 pts                         │
│  • Roy: +1 défaite, -4 diff, +7 pts                            │
│                                                                 │
│              [Annuler]  [Enregistrer]                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Saisie Multiple (Optionnel)

### Pour Catégories Multiples

Si plusieurs catégories jouent en même temps:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  SAISIE RAPIDE - TOUTES CATÉGORIES                                         │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  HOMME - 35-50 - 3.5 (Ronde 2)                                             │
│  ─────────────────────────────                                              │
│  │ T1 │ Tremblay+Lavoie vs Martin+Roy    │ [11]-[ 8] │ ✅ │                │
│  │ T2 │ Gagnon+Dubois vs Morin+Côté      │ [  ]-[  ] │ 🕐 │                │
│                                                                             │
│  FEMME - 35-50 - 3.5 (Ronde 2)                                             │
│  ─────────────────────────────                                              │
│  │ T3 │ Roy+Gagnon vs Lavoie+Bouchard    │ [  ]-[  ] │ 🕐 │                │
│  │ T4 │ Tremblay+Martin vs Côté+Dubois   │ [ 9]-[11] │ ✅ │                │
│                                                                             │
│  [Tout valider]                                                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Écran Tactile / Mobile

### Interface Optimisée

Pour une saisie sur tablette au bord du terrain:

```
┌───────────────────────────────────────┐
│  TERRAIN 2 - RONDE 2                  │
│  ─────────────────────                │
│                                       │
│  ┌─────────────────────────────────┐  │
│  │     TREMBLAY + LAVOIE           │  │
│  │                                 │  │
│  │         ┌─────────┐             │  │
│  │         │         │             │  │
│  │         │   11    │             │  │
│  │         │         │             │  │
│  │         └─────────┘             │  │
│  │    [ - ]          [ + ]         │  │
│  └─────────────────────────────────┘  │
│                                       │
│              VS                       │
│                                       │
│  ┌─────────────────────────────────┐  │
│  │     MARTIN + ROY                │  │
│  │                                 │  │
│  │         ┌─────────┐             │  │
│  │         │         │             │  │
│  │         │    8    │             │  │
│  │         │         │             │  │
│  │         └─────────┘             │  │
│  │    [ - ]          [ + ]         │  │
│  └─────────────────────────────────┘  │
│                                       │
│  ┌─────────────────────────────────┐  │
│  │      ✅ ENREGISTRER             │  │
│  └─────────────────────────────────┘  │
│                                       │
└───────────────────────────────────────┘
```

### Boutons +/-

- Grands boutons pour saisie tactile
- Incrémentation/décrémentation par 1
- Appui long pour incrémentation rapide

---

## Feedback et Confirmations

### Après Enregistrement

```
┌─────────────────────────────────────────┐
│  ✅ Score enregistré                    │
│                                         │
│  Résultat: Victoire Équipe A (11-8)     │
│                                         │
│  Classement mis à jour automatiquement  │
│                                         │
│  [Voir classement]  [Match suivant]     │
└─────────────────────────────────────────┘
```

### Indicateur de Progression

Sur la page de cédule, après chaque score:
- Mise à jour du compteur "X/Y matchs terminés"
- Barre de progression de la ronde
- Notification si la ronde est complète

---

## Annulation vs Score Zéro

### Différence

| Action | Résultat |
|--------|----------|
| Score 11-0 | Match valide, défaite complète pour l'équipe B |
| Annuler match | Match ne compte pas, comme s'il n'avait pas eu lieu |

### Quand Annuler?

- Blessure pendant le match
- Forfait avant le match
- Problème technique empêchant le match

Le bouton "Annuler" est distinct de la saisie de score.

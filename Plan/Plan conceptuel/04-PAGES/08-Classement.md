# Page: Classement

## Objectif
Afficher le classement en temps réel des joueurs par catégorie, calculé selon les règles officielles (Victoires → Différentiel → Points marqués). Permettre la visualisation détaillée des statistiques.

---

## Accès
- **Rôles**: Tous (lecture seule pour Superviseur)
- **Menu**: Tournoi > Classement

---

## Règles de Classement (Rappel)

### Critères de Tri (Ordre de Priorité)

1. **Nombre de victoires** (décroissant)
2. **Différentiel de points** (points marqués - points encaissés)
3. **Points marqués** (total des points marqués)

### Cas d'Égalité

Si deux joueurs sont à égalité sur les 3 critères:
- Même rang affiché (ex: deux joueurs 3e ex-æquo)
- Le suivant est décalé (ex: pas de 4e, directement 5e)

---

## Affichage Principal

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  CLASSEMENT                                            [📊 Statistiques]   │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Catégorie: [Homme - 35-50 - 3.5     ▼]                                    │
│                                                                             │
│  Rondes jouées: 3 sur 4 (75%)                    Dernière MAJ: 10:32:15    │
│                                                                             │
│  ┌────┬─────┬──────────────────────┬──────┬──────┬───────┬────────────────┐│
│  │Rang│ #PJ │ Joueur               │ Vic. │ Diff │ Pts   │ Détail         ││
│  ├────┼─────┼──────────────────────┼──────┼──────┼───────┼────────────────┤│
│  │ 🥇 │ 3/3 │ Tremblay, Jean       │  3   │ +12  │  33   │ [Voir]         ││
│  │ 🥈 │ 3/3 │ Lavoie, Pierre       │  3   │ +8   │  31   │ [Voir]         ││
│  │ 🥉 │ 3/3 │ Martin, Luc          │  2   │ +5   │  28   │ [Voir]         ││
│  │ 4  │ 3/3 │ Roy, Marc            │  2   │ +3   │  27   │ [Voir]         ││
│  │ 5  │ 3/3 │ Gagnon, Pierre       │  2   │ +3   │  25   │ [Voir]         ││
│  │ 6  │ 3/3 │ Dubois, André        │  1   │ -2   │  24   │ [Voir]         ││
│  │ 7  │ 3/3 │ Morin, François      │  1   │ -4   │  22   │ [Voir]         ││
│  │ 8  │ 3/3 │ Côté, Michel         │  1   │ -6   │  20   │ [Voir]         ││
│  │ 9  │ 2/3 │ Pelletier, Robert    │  1   │ -3   │  15   │ [Voir] ⚠️     ││
│  │ 10 │ 3/3 │ Fortin, Daniel       │  0   │ -8   │  18   │ [Voir]         ││
│  │ 11 │ 3/3 │ Girard, Paul         │  0   │ -10  │  16   │ [Voir]         ││
│  │ 12 │ 3/3 │ Boucher, René        │  0   │ -12  │  14   │ [Voir]         ││
│  └────┴─────┴──────────────────────┴──────┴──────┴───────┴────────────────┘│
│                                                                             │
│  ⚠️ = Match manqué                                                         │
│                                                                             │
│  [📄 Exporter PDF]  [📊 Exporter Excel]  [🖨️ Imprimer]                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Colonnes du Classement

| Colonne | Abréviation | Description |
|---------|-------------|-------------|
| Rang | - | Position au classement (médailles pour top 3) |
| #PJ | Parties Jouées | X/Y où Y = nombre total de rondes |
| Joueur | - | Nom complet du joueur |
| Vic. | Victoires | Nombre de victoires |
| Diff | Différentiel | Points marqués - Points encaissés |
| Pts | Points | Total des points marqués |
| Détail | - | Lien vers les statistiques détaillées |

### Indicateurs Spéciaux

| Icône | Signification |
|-------|---------------|
| 🥇 🥈 🥉 | Podium (top 3) |
| ⚠️ | A manqué un ou plusieurs matchs |
| 🔄 | Joueur substitut (pas au classement principal) |
| ▲ / ▼ | Progression depuis la dernière ronde (optionnel) |

---

## Mise à Jour en Temps Réel

### Comportement

- Après chaque saisie de score, le classement se recalcule automatiquement
- Animation visuelle des changements de position
- Horodatage de la dernière mise à jour affiché

### Animation de Changement

```
Avant le match:
│ 3  │ Martin, Luc   │  1   │ +2   │  19  │

Après victoire de Martin:
│ 🔼 2│ Martin, Luc  │  2   │ +5   │  30  │  ← Surbrillance verte

Après défaite de Roy (qui descend):
│ 🔽 5│ Roy, Marc    │  1   │ -2   │  18  │  ← Surbrillance rouge
```

---

## Détail d'un Joueur

### Modale Statistiques

```
┌─────────────────────────────────────────────────────────────────┐
│  STATISTIQUES - TREMBLAY, JEAN                                  │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Classement actuel: 1er / 12                                   │
│  Catégorie: Homme - 35-50 - 3.5                                │
│                                                                 │
│  ┌───────────────────────────────────────────────────────────┐ │
│  │  RÉSUMÉ                                                   │ │
│  │  ───────                                                  │ │
│  │  Parties jouées:  3                                       │ │
│  │  Victoires:       3 (100%)                                │ │
│  │  Défaites:        0 (0%)                                  │ │
│  │  Points marqués:  33                                      │ │
│  │  Points encaissés: 21                                     │ │
│  │  Différentiel:    +12                                     │ │
│  │  Moyenne pts/match: 11.0                                  │ │
│  └───────────────────────────────────────────────────────────┘ │
│                                                                 │
│  HISTORIQUE DES MATCHS                                         │
│  ─────────────────────                                         │
│  ┌────────┬──────────────┬─────────────────┬──────┬──────────┐ │
│  │ Ronde  │ Partenaire   │ Adversaires     │Score │ Résultat │ │
│  ├────────┼──────────────┼─────────────────┼──────┼──────────┤ │
│  │ R1     │ Lavoie, P.   │ Martin + Roy    │ 11-7 │ ✅ Vic.  │ │
│  │ R2     │ Gagnon, P.   │ Dubois + Morin  │ 11-9 │ ✅ Vic.  │ │
│  │ R3     │ Martin, L.   │ Côté + Pelletier│ 11-5 │ ✅ Vic.  │ │
│  │ R4     │ À venir      │ À venir         │  -   │ -        │ │
│  └────────┴──────────────┴─────────────────┴──────┴──────────┘ │
│                                                                 │
│  PARTENAIRES                          ADVERSAIRES              │
│  ───────────                          ───────────              │
│  • Lavoie (1x)                        • Martin (2x)            │
│  • Gagnon (1x)                        • Roy (1x)               │
│  • Martin (1x)                        • Dubois (1x)            │
│                                       • Morin (1x)             │
│                                       • Côté (1x)              │
│                                       • Pelletier (1x)         │
│                                                                 │
│                              [Fermer]                           │
└─────────────────────────────────────────────────────────────────┘
```

---

## Filtres et Options

### Filtres

| Filtre | Options |
|--------|---------|
| Catégorie | Liste des catégories du tournoi |
| Afficher substituts | Oui / Non (par défaut: Non) |

### Options d'Affichage

- **Complet**: Toutes les colonnes
- **Simplifié**: Rang, Nom, Victoires, Diff
- **Détaillé**: Avec historique visible inline

---

## Classement Multi-Catégories

### Vue Globale

Optionnel: voir le classement de toutes les catégories:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  CLASSEMENT - VUE GLOBALE                                                   │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  ┌──────────────────────────────────┐  ┌──────────────────────────────────┐│
│  │ HOMME - 35-50 - 3.5              │  │ FEMME - 35-50 - 3.5              ││
│  │ ─────────────────────            │  │ ─────────────────────            ││
│  │ 🥇 Tremblay, Jean (3V, +12)     │  │ 🥇 Gagnon, Marie (3V, +10)       ││
│  │ 🥈 Lavoie, Pierre (3V, +8)      │  │ 🥈 Roy, Sophie (2V, +6)          ││
│  │ 🥉 Martin, Luc (2V, +5)         │  │ 🥉 Dubois, Anne (2V, +4)         ││
│  │ [Voir classement complet]        │  │ [Voir classement complet]        ││
│  └──────────────────────────────────┘  └──────────────────────────────────┘│
│                                                                             │
│  ┌──────────────────────────────────┐  ┌──────────────────────────────────┐│
│  │ HOMME - 50+ - 3.5                │  │ FEMME - 20-35 - 3.5              ││
│  │ ...                              │  │ ...                              ││
│  └──────────────────────────────────┘  └──────────────────────────────────┘│
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Cas Spéciaux

### Joueur avec Match Manqué

Un joueur qui a manqué un match (substitut à sa place, ou match annulé):

```
│ 9  │ 2/3 │ Pelletier, Robert │  1   │ -3   │  15  │ [Voir] ⚠️ │

Explication: "Ce joueur n'a joué que 2 matchs sur 3.
              Ronde 2: Remplacé par un substitut."
```

### Ex-Æquo

```
│ 3  │ 3/3 │ Martin, Luc       │  2   │ +5   │  28  │ [Voir] │
│ 3  │ 3/3 │ Roy, Marc         │  2   │ +5   │  28  │ [Voir] │
│ 5  │ 3/3 │ Gagnon, Pierre    │  2   │ +3   │  25  │ [Voir] │
                               ↑
                    Pas de 4e, saut au 5e
```

### Substituts

Les substituts apparaissent séparément ou sont masqués:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  ☐ Afficher les substituts                                                 │
│                                                                             │
│  SUBSTITUTS (Non classés)                                                   │
│  ─────────────────────────                                                  │
│  │ -  │ 2/4 │ [Substitut 1]   │  1   │ +2   │  18  │ [Voir] 🔄 │          │
│  │ -  │ 1/4 │ [Substitut 2]   │  0   │ -3   │   8  │ [Voir] 🔄 │          │
│                                                                             │
│  ℹ️ Les substituts ne sont pas classés mais leurs stats sont suivies.     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Progression vers les Séries

### Indicateur de Qualification

Quand les rondes préliminaires sont terminées:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  ✅ RONDES PRÉLIMINAIRES TERMINÉES                                         │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Classement final:                                                          │
│                                                                             │
│  ┌────┬──────────────────────┬──────┬──────┬───────┬──────────────────────┐│
│  │Rang│ Joueur               │ Vic. │ Diff │ Pts   │ Équipe Séries        ││
│  ├────┼──────────────────────┼──────┼──────┼───────┼──────────────────────┤│
│  │ 1  │ Tremblay, Jean       │  4   │ +15  │  44   │ Équipe avec #5       ││
│  │ 2  │ Lavoie, Pierre       │  4   │ +12  │  42   │ Équipe avec #6       ││
│  │ 3  │ Martin, Luc          │  3   │ +8   │  38   │ Équipe avec #7       ││
│  │ 4  │ Roy, Marc            │  3   │ +5   │  35   │ Équipe avec #8       ││
│  │ 5  │ Gagnon, Pierre       │  2   │ +2   │  30   │ Équipe avec #1       ││
│  │ 6  │ Dubois, André        │  2   │ -1   │  28   │ Équipe avec #2       ││
│  │ 7  │ Morin, François      │  1   │ -5   │  24   │ Équipe avec #3       ││
│  │ 8  │ Côté, Michel         │  1   │ -8   │  22   │ Équipe avec #4       ││
│  │ -- │ ─────────────────────│──────│──────│───────│ NON QUALIFIÉS ────── ││
│  │ 9  │ Pelletier, Robert    │  0   │ -10  │  18   │ -                    ││
│  │ 10 │ Fortin, Daniel       │  0   │ -12  │  16   │ -                    ││
│  └────┴──────────────────────┴──────┴──────┴───────┴──────────────────────┘│
│                                                                             │
│  Formation d'équipes: 1+5, 2+6, 3+7, 4+8                                   │
│                                                                             │
│  [Générer les séries éliminatoires]                                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Export et Impression

### Options d'Export

| Format | Contenu |
|--------|---------|
| PDF | Classement formaté pour impression |
| Excel | Données brutes avec toutes les colonnes |
| CSV | Format simple pour import externe |

### Aperçu PDF

```
┌─────────────────────────────────────────┐
│  CLASSEMENT - Homme 35-50 3.5           │
│  Tournoi: Méli-Mélo Janvier 2026        │
│  Date: 15 janvier 2026                  │
│  ─────────────────────────────────────  │
│                                         │
│  Rang  Joueur           V  Diff  Pts    │
│  ────  ───────────────  ─  ────  ───    │
│   1    Tremblay, Jean   4   +15   44    │
│   2    Lavoie, Pierre   4   +12   42    │
│   ...                                   │
│                                         │
│  Généré le 15/01/2026 à 12:30          │
└─────────────────────────────────────────┘
```

---

## Messages et États

| Situation | Affichage |
|-----------|-----------|
| Aucune ronde jouée | "Aucune partie jouée. Le classement sera disponible après la première ronde." |
| Rondes en cours | "Classement en cours - X rondes sur Y complétées" |
| Rondes terminées | "Rondes préliminaires terminées. Classement final." |
| Catégorie sans joueur | "Aucun joueur dans cette catégorie." |

# Page: Séries Éliminatoires

## Objectif
Gérer la deuxième phase du tournoi: formation des équipes fixes basées sur le classement, génération du bracket d'élimination, saisie des scores et progression vers la finale.

---

## Accès
- **Rôles**: Administrateur (génération, modification), Superviseur (saisie scores)
- **Menu**: Tournoi > Séries éliminatoires
- **Prérequis**: Rondes préliminaires terminées pour cette catégorie

---

## Concept des Séries

### Différence avec les Rondes

| Rondes Préliminaires | Séries Éliminatoires |
|----------------------|----------------------|
| Partenaires aléatoires | Équipes fixes |
| Points individuels | Équipe gagne ou perd |
| Tout le monde joue toutes les rondes | Élimination après défaite(s) |
| Classement individuel | Bracket d'élimination |

### Formation des Équipes

**Principe**: Équilibrer les équipes en jumelant les meilleurs avec les moins bien classés.

Pour 8 joueurs qualifiés:
- Équipe A: Joueur #1 + Joueur #5
- Équipe B: Joueur #2 + Joueur #6
- Équipe C: Joueur #3 + Joueur #7
- Équipe D: Joueur #4 + Joueur #8

Pour 6 joueurs:
- Équipe A: #1 + #4
- Équipe B: #2 + #5
- Équipe C: #3 + #6

---

## Affichage Principal - Avant Génération

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  SÉRIES ÉLIMINATOIRES                                                       │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Catégorie: [Homme - 35-50 - 3.5     ▼]                                    │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ ✅ Rondes préliminaires terminées                                   │   │
│  │                                                                     │   │
│  │ Joueurs qualifiés: 8                                                │   │
│  │                                                                     │   │
│  │ FORMATION DES ÉQUIPES (Proposition)                                 │   │
│  │ ──────────────────────────────────                                  │   │
│  │                                                                     │   │
│  │ Équipe 1: Tremblay (#1) + Gagnon (#5)                              │   │
│  │ Équipe 2: Lavoie (#2) + Dubois (#6)                                │   │
│  │ Équipe 3: Martin (#3) + Morin (#7)                                 │   │
│  │ Équipe 4: Roy (#4) + Côté (#8)                                     │   │
│  │                                                                     │   │
│  │ [✏️ Modifier les équipes]  [🎲 Générer le bracket]                 │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  OU si non terminées:                                                       │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ ⏳ Rondes préliminaires en cours (3/4)                              │   │
│  │                                                                     │   │
│  │ Les séries éliminatoires seront disponibles après la 4e ronde.     │   │
│  │                                                                     │   │
│  │ [Voir le classement actuel]                                        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Modification des Équipes

### Modale de Modification

```
┌─────────────────────────────────────────────────────────────────┐
│  MODIFIER LA FORMATION DES ÉQUIPES                              │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Méthode de formation:                                          │
│  ○ Automatique (1+5, 2+6, 3+7, 4+8)  ← Recommandé              │
│  ○ Manuelle                                                     │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  ÉQUIPES                                                        │
│  ───────                                                        │
│                                                                 │
│  Équipe 1: [Tremblay, Jean (#1)  ▼] + [Gagnon, Pierre (#5) ▼]  │
│  Équipe 2: [Lavoie, Pierre (#2)  ▼] + [Dubois, André (#6)  ▼]  │
│  Équipe 3: [Martin, Luc (#3)     ▼] + [Morin, François (#7)▼]  │
│  Équipe 4: [Roy, Marc (#4)       ▼] + [Côté, Michel (#8)   ▼]  │
│                                                                 │
│  ⚠️ Un joueur ne peut être que dans une seule équipe           │
│                                                                 │
│  Nommage des équipes (optionnel):                               │
│  Équipe 1: [Les Champions          ]                            │
│  Équipe 2: [                       ]                            │
│  Équipe 3: [                       ]                            │
│  Équipe 4: [                       ]                            │
│                                                                 │
│              [Annuler]  [Confirmer]                             │
└─────────────────────────────────────────────────────────────────┘
```

### Règles de Modification

- Chaque joueur doit être dans exactement une équipe
- Les joueurs non-qualifiés ne peuvent pas participer
- Les substituts ne peuvent pas être dans les équipes des séries

---

## Bracket d'Élimination

### Bracket 4 Équipes (Demi-finales + Finale)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  BRACKET - SÉRIES ÉLIMINATOIRES                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  DEMI-FINALES                              FINALE                           │
│  ────────────                              ──────                           │
│                                                                             │
│  ┌────────────────────────┐                                                 │
│  │ Équipe 1               │                                                 │
│  │ Tremblay + Gagnon      │───┐                                             │
│  │                        │   │                                             │
│  └────────────────────────┘   │                                             │
│        vs                     │        ┌────────────────────────┐           │
│  ┌────────────────────────┐   ├───────►│ Gagnant DF1            │           │
│  │ Équipe 4               │   │        │ ?                      │───┐       │
│  │ Roy + Côté             │───┘        │                        │   │       │
│  │                        │            └────────────────────────┘   │       │
│  └────────────────────────┘                   vs                    │       │
│                                        ┌────────────────────────┐   │       │
│  ┌────────────────────────┐   ┌───────►│ Gagnant DF2            │   │       │
│  │ Équipe 2               │   │        │ ?                      │───┤       │
│  │ Lavoie + Dubois        │───┤        │                        │   │       │
│  │                        │   │        └────────────────────────┘   │       │
│  └────────────────────────┘   │                                     │       │
│        vs                     │                                     │       │
│  ┌────────────────────────┐   │                               ┌─────┴─────┐ │
│  │ Équipe 3               │───┘                               │ 🏆        │ │
│  │ Martin + Morin         │                                   │ CHAMPION  │ │
│  │                        │                                   │           │ │
│  └────────────────────────┘                                   └───────────┘ │
│                                                                             │
│  DF1: Terrain 1, 11:00                  Finale: Terrain 1, 11:30           │
│  DF2: Terrain 2, 11:00                                                      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Bracket 8 Équipes (Quarts + Demi + Finale)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  QUARTS DE FINALE           DEMI-FINALES              FINALE               │
│  ────────────────           ────────────              ──────               │
│                                                                             │
│  ┌──────────────┐                                                           │
│  │ Équipe 1     │──┐                                                        │
│  └──────────────┘  │        ┌──────────────┐                               │
│        vs          ├───────►│ Gagnant QF1  │──┐                             │
│  ┌──────────────┐  │        └──────────────┘  │                             │
│  │ Équipe 8     │──┘              vs          │        ┌──────────────┐     │
│  └──────────────┘           ┌──────────────┐  ├───────►│ Gagnant DF1  │     │
│                    ┌───────►│ Gagnant QF2  │──┘        └──────────────┘     │
│  ┌──────────────┐  │        └──────────────┘                 vs             │
│  │ Équipe 4     │──┤                                   ┌──────────────┐     │
│  └──────────────┘  │                          ┌───────►│ Gagnant DF2  │     │
│        vs          │                          │        └──────────────┘     │
│  ┌──────────────┐  │                          │              │              │
│  │ Équipe 5     │──┘                          │              ▼              │
│  └──────────────┘                             │        ┌──────────────┐     │
│                                               │        │ 🏆 CHAMPION  │     │
│  ┌──────────────┐                             │        └──────────────┘     │
│  │ Équipe 2     │──┐        ┌──────────────┐  │                             │
│  └──────────────┘  │        │ Gagnant QF3  │──┤                             │
│        vs          ├───────►└──────────────┘  │                             │
│  ┌──────────────┐  │              vs          │                             │
│  │ Équipe 7     │──┘        ┌──────────────┐  │                             │
│  └──────────────┘  ┌───────►│ Gagnant QF4  │──┘                             │
│                    │        └──────────────┘                                │
│  ┌──────────────┐  │                                                        │
│  │ Équipe 3     │──┤                                                        │
│  └──────────────┘  │                                                        │
│        vs          │                                                        │
│  ┌──────────────┐  │                                                        │
│  │ Équipe 6     │──┘                                                        │
│  └──────────────┘                                                           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Détail d'un Match de Série

### Clic sur un Match

```
┌─────────────────────────────────────────────────────────────────┐
│  DEMI-FINALE 1                                                  │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Terrain: 1                    Heure: 11:00                    │
│  Statut: 🕐 À jouer                                            │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │    ÉQUIPE 1                      ÉQUIPE 4               │   │
│  │    ─────────                     ─────────              │   │
│  │    Tremblay, Jean (#1)           Roy, Marc (#4)         │   │
│  │    Gagnon, Pierre (#5)           Côté, Michel (#8)      │   │
│  │                                                         │   │
│  │         ┌───────┐                   ┌───────┐           │   │
│  │         │       │       VS          │       │           │   │
│  │         │       │                   │       │           │   │
│  │         │       │                   │       │           │   │
│  │         └───────┘                   └───────┘           │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Le gagnant affrontera le gagnant de DF2 en finale.            │
│                                                                 │
│  [✏️ Saisir le score]                                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Après Saisie du Score

```
┌─────────────────────────────────────────────────────────────────┐
│  DEMI-FINALE 1 - TERMINÉE                                       │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │    ÉQUIPE 1 🏆                   ÉQUIPE 4               │   │
│  │    ─────────                     ─────────              │   │
│  │    Tremblay + Gagnon             Roy + Côté             │   │
│  │                                                         │   │
│  │         ┌───────┐                   ┌───────┐           │   │
│  │         │       │                   │       │           │   │
│  │         │  11   │       VS          │   7   │           │   │
│  │         │       │                   │       │           │   │
│  │         └───────┘                   └───────┘           │   │
│  │                                                         │   │
│  │      ✅ VAINQUEUR                   ❌ ÉLIMINÉ          │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  L'Équipe 1 avance en finale!                                  │
│                                                                 │
│  [Modifier le score]                                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Progression du Bracket

### Mise à Jour Automatique

Quand un match est terminé:
1. Le gagnant s'affiche dans le match suivant du bracket
2. Le bracket se met à jour visuellement
3. Le prochain match devient "À jouer"

### Affichage des Matchs Futurs

```
┌────────────────────────┐
│ 🕐 FINALE              │
│ ─────────              │
│ Équipe 1               │  ← Gagnant DF1 connu
│ Tremblay + Gagnon      │
│                        │
│         vs             │
│                        │
│ ?                      │  ← En attente DF2
│ (Gagnant DF2)          │
│                        │
│ À jouer: 11:30         │
└────────────────────────┘
```

---

## Finale et Résultat

### Match de Finale

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  🏆 FINALE                                                                  │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Catégorie: Homme - 35-50 - 3.5                                            │
│  Terrain: Central                  Heure: 11:30                            │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                                                                     │   │
│  │         ÉQUIPE 1                           ÉQUIPE 2                 │   │
│  │    Tremblay + Gagnon                  Lavoie + Dubois              │   │
│  │                                                                     │   │
│  │    ┌───────────────┐                  ┌───────────────┐            │   │
│  │    │               │                  │               │            │   │
│  │    │      11       │       VS         │       9       │            │   │
│  │    │               │                  │               │            │   │
│  │    └───────────────┘                  └───────────────┘            │   │
│  │                                                                     │   │
│  │         🏆 CHAMPION                       2e PLACE                 │   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  🎉 FÉLICITATIONS AUX CHAMPIONS!                                           │
│                                                                             │
│  [📄 Imprimer les résultats]  [🏆 Voir le podium]                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Écran du Podium

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│              🏆 RÉSULTATS - HOMME 35-50 3.5 🏆                 │
│              ───────────────────────────────                   │
│                                                                 │
│                      ┌───────────────┐                         │
│                      │   🥇 1ER      │                         │
│                      │               │                         │
│                      │   ÉQUIPE 1    │                         │
│                      │  Tremblay     │                         │
│                      │  + Gagnon     │                         │
│                      │               │                         │
│       ┌──────────────┴───────────────┴──────────────┐          │
│       │           🥈 2E                             │          │
│       │                                             │          │
│       │           ÉQUIPE 2                          │          │
│       │          Lavoie + Dubois                    │          │
│       │                                             │          │
│       ├─────────────────────────────────────────────┤          │
│       │           🥉 3E                             │          │
│       │                                             │          │
│       │        ÉQUIPE 3 & ÉQUIPE 4                  │          │
│       │   (Martin+Morin) & (Roy+Côté)               │          │
│       │      (Demi-finalistes)                      │          │
│       └─────────────────────────────────────────────┘          │
│                                                                 │
│  [Imprimer]  [Partager]  [Retour au tournoi]                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Options de Format

### Élimination Simple vs Double

**Élimination Simple** (Par défaut):
- Une défaite = éliminé
- Plus rapide

**Élimination Double** (Optionnel):
- Deux défaites pour être éliminé
- Bracket "Loser's bracket"
- Plus long mais plus équitable

### Configuration au Moment de la Génération

```
┌─────────────────────────────────────────────────────────────────┐
│  GÉNÉRER LE BRACKET                                             │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Format:                                                        │
│  ○ Élimination simple (1 défaite = éliminé)                    │
│  ○ Élimination double (2 défaites = éliminé)                   │
│                                                                 │
│  Équipes qualifiées: 4                                          │
│                                                                 │
│  Matchs prévus:                                                 │
│  - Simple: 3 matchs (2 demi + 1 finale)                        │
│  - Double: 6-7 matchs                                          │
│                                                                 │
│              [Annuler]  [Générer]                               │
└─────────────────────────────────────────────────────────────────┘
```

---

## Gestion des Cas Spéciaux

### Nombre Impair d'Équipes

Si 6 équipes: Certaines équipes ont un "bye" (passe au tour suivant sans jouer)

```
  QUARTS                    DEMI                    FINALE
  ──────                    ────                    ──────

  Équipe 1 ─────────────────┬── Équipe 1 ──┐
  (Bye)                     │              │
                            │              ├── Gagnant → Champion
  Équipe 3 ──┬── Gagnant ───┘              │
     vs      │                             │
  Équipe 6 ──┘                             │
                                           │
  Équipe 2 ─────────────────┬── Équipe 2 ──┘
  (Bye)                     │
                            │
  Équipe 4 ──┬── Gagnant ───┘
     vs      │
  Équipe 5 ──┘
```

### Forfait en Série

Si une équipe déclare forfait:
- L'adversaire avance automatiquement
- Le match est marqué "Forfait"
- Pas de score enregistré

---

## Messages et États

| Situation | Message |
|-----------|---------|
| Rondes non terminées | "Terminez les rondes préliminaires avant de générer les séries." |
| Bracket généré | "Bracket généré avec X équipes. Les demi-finales peuvent commencer!" |
| Match terminé | "L'Équipe X avance au tour suivant!" |
| Finale terminée | "🏆 Félicitations aux champions: [Noms]!" |
| Équipes modifiées | "Formation des équipes modifiée. Le bracket sera régénéré." |

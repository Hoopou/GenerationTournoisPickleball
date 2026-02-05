# Page: Rondes Préliminaires (Cédule)

## Objectif
Afficher et gérer la cédule des rondes préliminaires: visualisation des matchs, filtrage par catégorie/terrain/ronde, génération automatique, et modifications manuelles.

---

## Accès
- **Rôles**: Administrateur (génération, modification), Superviseur (lecture seule)
- **Menu**: Tournoi > Rondes préliminaires

---

## Concept des Rondes

### Déroulement
1. L'admin génère automatiquement la cédule via l'algorithme de jumelage
2. Chaque ronde contient plusieurs matchs simultanés
3. Les partenaires changent à chaque ronde (Méli-Mélo)
4. On ne peut pas avoir le même partenaire deux fois
5. Maximiser la rotation des adversaires avant de répéter

### Structure d'un Match
- **Équipe A**: Joueur 1 + Joueur 2 (partenaires aléatoires)
- **Équipe B**: Joueur 3 + Joueur 4 (partenaires aléatoires)
- **Terrain**: Numéro du terrain assigné
- **Heure**: Créneau horaire

---

## Affichage Principal

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  RONDES PRÉLIMINAIRES                                                       │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Catégorie: [Homme - 35-50 - 3.5     ▼]                                    │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ ℹ️ Cédule non générée pour cette catégorie                          │   │
│  │                                                                     │   │
│  │     [🎲 Générer la cédule]                                         │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  OU si déjà générée:                                                        │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ ✅ Cédule générée - 4 rondes, 24 matchs                             │   │
│  │                                            [🔄 Régénérer] [📥 PDF]  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  Filtres: [Ronde: Toutes ▼] [Terrain: Tous ▼] [Statut: Tous ▼]             │
│                                                                             │
│  Vue: [📋 Liste] [📊 Grille] [📅 Timeline]                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Vues de la Cédule

### Vue Liste (Défaut)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  RONDE 1 - 09:00                                                            │
│  ────────────────                                                           │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Terrain 1 │ Tremblay + Lavoie  VS  Martin + Roy    │ 🕐 À jouer    │   │
│  │           │ [Saisir score]                          │               │   │
│  ├───────────┼─────────────────────────────────────────┼───────────────┤   │
│  │ Terrain 2 │ Gagnon + Dubois    VS  Morin + Côté    │ 🕐 À jouer    │   │
│  │           │ [Saisir score]                          │               │   │
│  ├───────────┼─────────────────────────────────────────┼───────────────┤   │
│  │ Terrain 3 │ Pelletier + Fortin VS  Girard + Boucher│ ✅ 11-7       │   │
│  │           │ [Modifier score]                        │               │   │
│  └───────────┴─────────────────────────────────────────┴───────────────┘   │
│                                                                             │
│  RONDE 2 - 09:15                                                            │
│  ────────────────                                                           │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Terrain 1 │ Tremblay + Gagnon  VS  Dubois + Lavoie │ 🕐 À jouer    │   │
│  │           │ [Saisir score]                          │               │   │
│  └───────────┴─────────────────────────────────────────┴───────────────┘   │
│  ...                                                                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Vue Grille (par Terrain)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│           │  Terrain 1       │  Terrain 2       │  Terrain 3       │       │
│  ─────────┼──────────────────┼──────────────────┼──────────────────┼────── │
│  Ronde 1  │ Tremblay+Lavoie  │ Gagnon+Dubois    │ Pelletier+Fortin │       │
│  09:00    │ vs Martin+Roy    │ vs Morin+Côté    │ vs Girard+Bouch. │       │
│           │ [À jouer]        │ [À jouer]        │ [11-7 ✅]        │       │
│  ─────────┼──────────────────┼──────────────────┼──────────────────┼────── │
│  Ronde 2  │ Tremblay+Gagnon  │ Lavoie+Martin    │ Roy+Dubois       │       │
│  09:15    │ vs Dubois+Lavoie │ vs Fortin+Morin  │ vs Côté+Pell.    │       │
│           │ [À jouer]        │ [À jouer]        │ [À jouer]        │       │
│  ─────────┼──────────────────┼──────────────────┼──────────────────┼────── │
│  ⏸️ PAUSE │      PAUSE DE 15 MINUTES (09:30 - 09:45)              │       │
│  ─────────┼──────────────────┼──────────────────┼──────────────────┼────── │
│  Ronde 3  │ ...              │ ...              │ ...              │       │
│  09:45    │                  │                  │                  │       │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Vue Timeline

Affichage chronologique avec barre de temps:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  09:00        09:15       09:30       09:45       10:00       10:15        │
│  │────────────│───────────│───────────│───────────│───────────│            │
│  │            │           │           │           │           │            │
│  │ RONDE 1    │ RONDE 2   │▓▓PAUSE▓▓│ RONDE 3   │ RONDE 4   │            │
│  │ 6 matchs   │ 6 matchs  │           │ 6 matchs  │ 6 matchs  │            │
│  │ [3 faits]  │ [0 faits] │           │           │           │            │
│  │            │           │           │           │           │            │
│  │▼ Actuelle  │           │           │           │           │            │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Génération de la Cédule

### Modale de Génération

```
┌─────────────────────────────────────────────────────────────────┐
│  GÉNÉRER LA CÉDULE                                              │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Catégorie: Homme - 35-50 - 3.5                                │
│  Joueurs: 12                                                    │
│  Terrains disponibles: 3                                        │
│                                                                 │
│  Nombre de rondes souhaitées:                                   │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ [    4    ]                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ℹ️ Avec 12 joueurs et 3 terrains:                             │
│     - Maximum théorique: 11 rondes (chaque partenaire unique)  │
│     - Recommandé: 4-6 rondes                                    │
│     - Chaque joueur jouera 4 matchs                            │
│                                                                 │
│  Options avancées:                                              │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ☐ Éviter que les mêmes joueurs se rencontrent          │   │
│  │   plus de 2 fois comme adversaires                      │   │
│  │                                                         │   │
│  │ ☐ Équilibrer l'utilisation des terrains                │   │
│  │                                                         │   │
│  │ ☐ Forcer le même nombre de matchs par joueur           │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│              [Annuler]  [🎲 Générer]                            │
└─────────────────────────────────────────────────────────────────┘
```

### Processus de Génération

1. **Clic sur Générer**
2. **Indicateur de chargement** avec message: "Génération en cours..."
3. **Algorithme**:
   - Créer tous les jumelages possibles (partenaires)
   - Organiser en rondes respectant les contraintes
   - Assigner les terrains et horaires
4. **Résultat**:
   - Afficher la cédule générée
   - Message: "Cédule générée: X rondes, Y matchs"

### Échec de Génération

Si l'algorithme ne peut pas générer une cédule valide:

```
┌─────────────────────────────────────────────────────────────────┐
│  ❌ IMPOSSIBLE DE GÉNÉRER LA CÉDULE                            │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Raison: Pas assez de joueurs pour le nombre de rondes demandé │
│                                                                 │
│  Suggestions:                                                   │
│  • Réduire le nombre de rondes à 3 maximum                     │
│  • Fusionner cette catégorie avec une autre                    │
│  • Ajouter des joueurs à cette catégorie                       │
│                                                                 │
│                              [OK]                               │
└─────────────────────────────────────────────────────────────────┘
```

---

## Régénération

### Confirmation

```
┌─────────────────────────────────────────────────────────────────┐
│  ⚠️ RÉGÉNÉRER LA CÉDULE?                                       │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Attention: Des scores ont déjà été saisis.                    │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  • 8 matchs avec score seront supprimés                 │   │
│  │  • Le classement actuel sera remis à zéro               │   │
│  │  • Cette action est irréversible                        │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ☐ Je comprends et je veux régénérer                           │
│                                                                 │
│              [Annuler]  [Régénérer]                             │
└─────────────────────────────────────────────────────────────────┘
```

---

## Détail d'un Match

### Clic sur un Match

```
┌─────────────────────────────────────────────────────────────────┐
│  MATCH #12 - Ronde 2, Terrain 1                                │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Heure prévue: 09:15                                           │
│  Catégorie: Homme - 35-50 - 3.5                                │
│                                                                 │
│  ┌───────────────────────┐    ┌───────────────────────┐        │
│  │  ÉQUIPE A             │    │  ÉQUIPE B             │        │
│  │  ─────────            │    │  ─────────            │        │
│  │  Tremblay, Jean       │    │  Martin, Luc          │        │
│  │  Lavoie, Pierre       │    │  Roy, Marc            │        │
│  │                       │ VS │                       │        │
│  │  Score: [   ]         │    │  Score: [   ]         │        │
│  └───────────────────────┘    └───────────────────────┘        │
│                                                                 │
│  Statut: 🕐 À jouer                                            │
│                                                                 │
│  Actions:                                                       │
│  [✏️ Saisir le score]  [🔄 Échanger joueurs]  [❌ Annuler match]│
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Modifications Manuelles

### Échanger des Joueurs

L'admin peut échanger des joueurs entre équipes d'un même match ou entre matchs de la même ronde.

```
┌─────────────────────────────────────────────────────────────────┐
│  ÉCHANGER DES JOUEURS                                          │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Match actuel (Ronde 2, Terrain 1):                            │
│  Tremblay + Lavoie  VS  Martin + Roy                           │
│                                                                 │
│  Sélectionnez le joueur à échanger:                            │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  ○ Tremblay, Jean                                       │   │
│  │  ○ Lavoie, Pierre                                       │   │
│  │  ○ Martin, Luc                                          │   │
│  │  ○ Roy, Marc                                            │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Échanger avec:                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  Matchs de la Ronde 2                                   │   │
│  │  ────────────────────                                   │   │
│  │  ○ Gagnon (Terrain 2 - Gagnon+Dubois vs Morin+Côté)    │   │
│  │  ○ Dubois (Terrain 2)                                   │   │
│  │  ○ Morin (Terrain 2)                                    │   │
│  │  ○ Côté (Terrain 2)                                     │   │
│  │  ...                                                    │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ⚠️ Attention: L'échange peut créer un doublon de partenaire  │
│                                                                 │
│              [Annuler]  [Valider l'échange]                    │
└─────────────────────────────────────────────────────────────────┘
```

### Validation des Échanges

Avant de valider un échange, vérifier:
- Les joueurs échangés n'ont pas déjà été partenaires ensemble
- Alerte si cette contrainte est violée: "Attention: Tremblay et Morin ont déjà été partenaires à la Ronde 1. Continuer quand même?"

---

## Annuler un Match

### Raisons d'Annulation

- Joueur blessé
- Abandon
- Problème de terrain

```
┌─────────────────────────────────────────────────────────────────┐
│  ANNULER LE MATCH                                              │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Match: Tremblay+Lavoie vs Martin+Roy (Ronde 2, Terrain 1)     │
│                                                                 │
│  Raison de l'annulation:                                        │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ○ Blessure d'un joueur                                  │   │
│  │ ○ Abandon                                               │   │
│  │ ○ Forfait d'équipe                                      │   │
│  │ ○ Problème technique/terrain                            │   │
│  │ ○ Autre (préciser)                                      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ⚠️ Ce match ne comptera pas dans les statistiques            │
│                                                                 │
│              [Retour]  [Confirmer l'annulation]                │
└─────────────────────────────────────────────────────────────────┘
```

---

## Filtres et Recherche

### Filtres Disponibles

| Filtre | Options |
|--------|---------|
| Ronde | Toutes, Ronde 1, Ronde 2, ... |
| Terrain | Tous, Terrain 1, Terrain 2, ... |
| Statut | Tous, À jouer, Terminé, Annulé |
| Joueur | Recherche par nom |

### Recherche par Joueur

```
┌─────────────────────────────────────────────────────────────────┐
│  Recherche: [Tremblay                      ] [🔍]              │
│                                                                 │
│  Résultats: 4 matchs pour "Tremblay"                           │
│                                                                 │
│  Ronde 1, Terrain 1: Tremblay + Lavoie vs Martin + Roy         │
│  Ronde 2, Terrain 1: Tremblay + Gagnon vs Dubois + Fortin      │
│  Ronde 3, Terrain 2: Tremblay + Martin vs Lavoie + Côté        │
│  Ronde 4, Terrain 3: Tremblay + Côté vs Gagnon + Martin        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Statuts des Matchs

| Statut | Icône | Description |
|--------|-------|-------------|
| À jouer | 🕐 | Match programmé, pas encore joué |
| En cours | ⏳ | Match commencé (optionnel) |
| Terminé | ✅ | Score saisi et validé |
| Annulé | ❌ | Match annulé, ne compte pas |

---

## Messages et Alertes

| Situation | Message |
|-----------|---------|
| Cédule générée | "Cédule générée avec succès: X rondes, Y matchs." |
| Cédule régénérée | "Cédule régénérée. X scores ont été supprimés." |
| Échange effectué | "Joueurs échangés avec succès." |
| Échange refusé | "Impossible: ces joueurs ont déjà été partenaires." |
| Match annulé | "Match annulé. Il n'affectera pas le classement." |
| Pas assez de joueurs | "Minimum 4 joueurs requis pour générer une cédule." |
| Pas assez de temps | "Le temps prévue pour les rondes prélimnaires ne permet de réaliser tous les match." | 

---

## Interactions avec Autres Pages

| Action | Impact |
|--------|--------|
| Saisie de score | Met à jour le classement en temps réel |
| Modification de catégorie | Peut invalider la cédule |
| Ajout de joueur | Nécessite régénération |
| Suppression de joueur | Nécessite régénération ou annulation des matchs |

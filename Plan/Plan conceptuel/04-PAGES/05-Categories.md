# Page: Gestion des Catégories

## Objectif
Générer automatiquement et gérer les catégories basées sur les critères (sexe, âge, niveau). Permettre les ajustements manuels et la fusion/séparation de catégories.

---

## Accès
- **Rôles**: Administrateur (génération, fusion, suppression), Superviseur (lecture seule)
- **Menu**: Joueurs > Catégories

---

## Principe de la Catégorisation

### Critères de Catégorie
Une catégorie regroupe des joueurs selon:
1. **Sexe**: Homme ou Femme
2. **Tranche d'âge**: Définies par l'admin (ex: 20-35, 35-50, 50+)
3. **Niveau**: DUPR (3.0-5.0) ou textuel (Novice, Intermédiaire, Avancé)

### Exemple
Un joueur homme de 38 ans niveau 3.5 → Catégorie "Homme - 35-50 - 3.5"

---

## Affichage Principal

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  CATÉGORIES                                              [⚙️ Configuration] │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ ⚠️ ATTENTION: 3 joueurs sans catégorie                              │   │
│  │    Cliquez ici pour les voir et les assigner                        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  [🔄 Régénérer les catégories]                                             │
│                                                                             │
│  CATÉGORIES GÉNÉRÉES (8)                                                    │
│  ────────────────────────                                                   │
│                                                                             │
│  ┌────────────────────────┐  ┌────────────────────────┐                    │
│  │ HOMME - 20-35 - 3.5    │  │ FEMME - 20-35 - 3.5    │                    │
│  │ ──────────────────     │  │ ──────────────────     │                    │
│  │ 8 joueurs              │  │ 6 joueurs              │                    │
│  │ ✅ Nb pair             │  │ ⚠️ Nb impair!         │                    │
│  │                        │  │                        │                    │
│  │ [Voir] [Fusionner]     │  │ [Voir] [Fusionner]     │                    │
│  └────────────────────────┘  └────────────────────────┘                    │
│                                                                             │
│  ┌────────────────────────┐  ┌────────────────────────┐                    │
│  │ HOMME - 35-50 - 3.5    │  │ FEMME - 35-50 - 3.5    │                    │
│  │ ──────────────────     │  │ ──────────────────     │                    │
│  │ 12 joueurs             │  │ 10 joueurs             │                    │
│  │ ✅ Nb pair             │  │ ✅ Nb pair             │                    │
│  │                        │  │                        │                    │
│  │ [Voir] [Fusionner]     │  │ [Voir] [Fusionner]     │                    │
│  └────────────────────────┘  └────────────────────────┘                    │
│                                                                             │
│  ┌────────────────────────┐  ┌────────────────────────┐                    │
│  │ HOMME - 35-50 - 4.0    │  │ FEMME - 50+ - 3.5      │                    │
│  │ ──────────────────     │  │ ──────────────────     │                    │
│  │ 4 joueurs              │  │ 2 joueurs              │                    │
│  │ ✅ Nb pair             │  │ ⚠️ Moins de 4 joueurs │                    │
│  │                        │  │                        │                    │
│  │ [Voir] [Fusionner]     │  │ [Voir] [Fusionner]     │                    │
│  └────────────────────────┘  └────────────────────────┘                    │
│                                                                             │
│  ┌────────────────────────┐  ┌────────────────────────┐                    │
│  │ HOMME - 50+ - 3.5      │  │ NON-ASSIGNÉS           │                    │
│  │ ──────────────────     │  │ ──────────────────     │                    │
│  │ 6 joueurs              │  │ 3 joueurs              │                    │
│  │ ✅ Nb pair             │  │ ❌ À traiter           │                    │
│  │                        │  │                        │                    │
│  │ [Voir] [Fusionner]     │  │ [Voir les joueurs]     │                    │
│  └────────────────────────┘  └────────────────────────┘                    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Carte de Catégorie

### Indicateurs Visuels

| Icône | Signification |
|-------|---------------|
| ✅ | Nombre pair de joueurs (idéal) |
| ⚠️ Nb impair | Nombre impair de joueurs - recommander fusion |
| ⚠️ < 4 joueurs | Moins de 4 joueurs - recommander fusion |
| ❌ | Problème critique à corriger |

### Actions par Carte

| Bouton | Action |
|--------|--------|
| Voir | Ouvre la liste des joueurs de cette catégorie |
| Fusionner | Ouvre la modale de fusion avec une autre catégorie |
| Séparer | (Si catégorie fusionnée) Défaire la fusion |

---

## Configuration des Catégories

### Modale Configuration

```
┌─────────────────────────────────────────────────────────────────┐
│  CONFIGURATION DES CATÉGORIES                                   │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  TRANCHES D'ÂGE                                                 │
│  ───────────────                                                │
│  Définissez les tranches d'âge pour la catégorisation:         │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  1. De [ 0  ] à [ 20 ] ans    [🗑️]                      │   │
│  │  2. De [ 20 ] à [ 35 ] ans    [🗑️]                      │   │
│  │  3. De [ 35 ] à [ 50 ] ans    [🗑️]                      │   │
│  │  4. De [ 50 ] à [ 99 ] ans    [🗑️]                      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  [+ Ajouter une tranche]                                        │
│                                                                 │
│  SYSTÈME DE NIVEAU                                              │
│  ─────────────────                                              │
│  ○ DUPR (3.0, 3.5, 4.0, 4.5, 5.0)                              │
│  ○ Textuel (Novice, Intermédiaire, Avancé)                     │
│                                                                 │
│  CATÉGORISATION PAR SEXE                                        │
│  ────────────────────────                                       │
│  ☑️ Séparer hommes et femmes                                   │
│                                                                 │
│              [Annuler]  [Sauvegarder et régénérer]              │
└─────────────────────────────────────────────────────────────────┘
```

### Règles de Configuration

**Tranches d'âge**:
- Les tranches ne peuvent pas se chevaucher
- Les tranches doivent couvrir tous les âges possibles (5-100)
- Minimum 1 tranche, maximum 10 tranches

**Validation**:
- Si une tranche est modifiée, avertissement: "Les catégories seront régénérées. Les assignations manuelles seront perdues."

---

## Génération des Catégories

### Bouton "Régénérer les catégories"

1. **Confirmation**: "Régénérer les catégories réassignera tous les joueurs selon leurs caractéristiques. Continuer?"
2. **Traitement**:
   - Pour chaque joueur actif
   - Calculer la catégorie selon: Sexe + Tranche d'âge + Niveau
   - Créer la catégorie si elle n'existe pas
   - Assigner le joueur
3. **Résultat**:
   - Afficher le nombre de catégories créées
   - Signaler les joueurs non-assignables (données incomplètes)

### Catégories Résultantes

Les catégories sont nommées automatiquement:
- Format: `[Sexe] - [Tranche âge] - [Niveau]`
- Exemples:
  - "Homme - 35-50 - 3.5"
  - "Femme - 20-35 - Intermédiaire"
  - "Homme - 50+ - 4.0"

---

## Fusion de Catégories

### Pourquoi Fusionner?

- Nombre impair de joueurs dans une catégorie
- Trop peu de joueurs (< 4)
- Équilibrer les catégories

### Modale de Fusion

```
┌─────────────────────────────────────────────────────────────────┐
│  FUSIONNER CATÉGORIES                                           │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Catégorie sélectionnée:                                        │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  FEMME - 50+ - 3.5 (2 joueurs)                          │   │
│  │  - Roy, Sophie                                          │   │
│  │  - Gagnon, Louise                                       │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Fusionner avec:                                                │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  ○ Femme - 35-50 - 3.5 (10 joueurs) ← Recommandé       │   │
│  │  ○ Femme - 50+ - 4.0 (4 joueurs)                        │   │
│  │  ○ Femme - 35-50 - 4.0 (6 joueurs)                      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Nom de la nouvelle catégorie:                                  │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Femme - 35+ - 3.5                                       │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Résultat: 12 joueurs (✅ pair)                                 │
│                                                                 │
│              [Annuler]  [Fusionner]                             │
└─────────────────────────────────────────────────────────────────┘
```

### Règles de Fusion

- **Recommandation**: Suggérer la catégorie la plus proche:
  1. Même sexe (obligatoire)
  2. Même niveau (priorité)
  3. Tranche d'âge adjacente
- **Résultat pair**: Indiquer si la fusion donne un nombre pair
- **Nom automatique**: Proposer un nom logique basé sur les caractéristiques combinées

---

## Détail d'une Catégorie

### Vue Liste des Joueurs

```
┌─────────────────────────────────────────────────────────────────┐
│  ← Retour aux catégories                                        │
│                                                                 │
│  HOMME - 35-50 - 3.5                                            │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  12 joueurs                           [Ajouter un joueur]       │
│                                                                 │
│  ┌────┬──────────────────────┬─────┬────────┬─────────────────┐ │
│  │ #  │ Nom                  │ Âge │ Niveau │ Actions         │ │
│  ├────┼──────────────────────┼─────┼────────┼─────────────────┤ │
│  │ 1  │ Tremblay, Jean       │ 38  │ 3.5    │ [Déplacer] [❌] │ │
│  │ 2  │ Lavoie, Pierre       │ 42  │ 3.5    │ [Déplacer] [❌] │ │
│  │ 3  │ Martin, Luc          │ 45  │ 3.5    │ [Déplacer] [❌] │ │
│  │ .. │ ...                  │ ... │ ...    │                 │ │
│  └────┴──────────────────────┴─────┴────────┴─────────────────┘ │
│                                                                 │
│  Actions:                                                       │
│  [Fusionner cette catégorie]  [Supprimer catégorie vide]       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Actions sur un Joueur dans la Catégorie

| Action | Description |
|--------|-------------|
| Déplacer | Ouvre une modale pour choisir une autre catégorie |
| ❌ | Retire le joueur de la catégorie (devient non-assigné) |

---

## Joueurs Non-Assignés

### Alerte Visible

Quand des joueurs n'ont pas de catégorie, une alerte apparaît:

```
┌─────────────────────────────────────────────────────────────────┐
│ ⚠️ JOUEURS SANS CATÉGORIE (3)                                   │
│ ───────────────────────────────────────────────────────────────│
│                                                                 │
│  Ces joueurs n'ont pas pu être catégorisés:                     │
│                                                                 │
│  ┌────────────────────┬─────────────────────────────────────┐  │
│  │ Martin, Luc        │ Raison: Niveau non renseigné        │  │
│  │                    │ [Modifier joueur] [Assigner manuellement]│
│  ├────────────────────┼─────────────────────────────────────┤  │
│  │ Dubois, Anne       │ Raison: Âge 120 hors limite         │  │
│  │                    │ [Modifier joueur] [Assigner manuellement]│
│  ├────────────────────┼─────────────────────────────────────┤  │
│  │ Roy, Marc          │ Raison: Catégorie supprimée         │  │
│  │                    │ [Modifier joueur] [Assigner manuellement]│
│  └────────────────────┴─────────────────────────────────────┘  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Assigner Manuellement

```
┌─────────────────────────────────────────┐
│  ASSIGNER UN JOUEUR                     │
│  ──────────────────                     │
│                                         │
│  Joueur: Martin, Luc (H, 38 ans, ?)     │
│                                         │
│  Choisir une catégorie:                 │
│  ┌─────────────────────────────────┐    │
│  │ ○ Homme - 35-50 - 3.5  (12 j.) │    │
│  │ ○ Homme - 35-50 - 4.0  (8 j.)  │    │
│  │ ○ Homme - 20-35 - 3.5  (6 j.)  │    │
│  └─────────────────────────────────┘    │
│                                         │
│           [Annuler]  [Assigner]         │
└─────────────────────────────────────────┘
```

---

## Alertes et Validations

### Avertissements Automatiques

| Situation | Message | Suggestion |
|-----------|---------|------------|
| Nombre impair | "Cette catégorie a un nombre impair de joueurs." | "Fusionner avec une autre catégorie" |
| < 4 joueurs | "Cette catégorie a moins de 4 joueurs." | "Fusionner pour un meilleur tournoi" |
| Joueurs non-assignés | "X joueurs n'ont pas de catégorie." | "Assigner ou modifier les joueurs" |
| Catégorie vide | "Cette catégorie n'a plus de joueurs." | "Supprimer cette catégorie" |

### Blocages

| Situation | Comportement |
|-----------|--------------|
| Régénérer avec rondes déjà générées | Confirmation: "Les rondes devront être régénérées." |
| Fusionner avec rondes générées | Confirmation: "La cédule de ces catégories sera invalidée." |
| Supprimer catégorie avec joueurs | Interdit - message d'erreur |

---

## Interactions avec Autres Pages

| Action | Impact |
|--------|--------|
| Catégories générées | Permet de passer à l'étape Rondes |
| Fusion effectuée | Invalide la cédule si déjà générée |
| Joueur ajouté | Assigné automatiquement si catégorie existe |
| Joueur modifié (âge/niveau) | Peut changer de catégorie automatiquement |

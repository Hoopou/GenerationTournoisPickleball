# Page: Gestion des Tournois

## Objectif
Créer, configurer et gérer les tournois. Cette page regroupe la création d'un nouveau tournoi et la modification de ses paramètres.

---

## Accès
- **Rôles**: Administrateur (modification), Superviseur (lecture seule)
- **Menu**: Tournoi > Paramètres

---

## Sous-pages

1. **Liste des Tournois** — Vue de tous les tournois
2. **Création de Tournoi** — Formulaire de création
3. **Paramètres du Tournoi** — Configuration détaillée
4. **Gestion des Terrains** — Configuration des terrains
5. **Périodes de Pause** — Configuration des pauses

---

## 1. Liste des Tournois

### Affichage

```
┌─────────────────────────────────────────────────────────────────┐
│  MES TOURNOIS                              [+ Nouveau tournoi]  │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ 📋 Méli-Mélo Terrebonne 2026                            │   │
│  │    Statut: En cours │ 45 joueurs │ 6 catégories         │   │
│  │    Créé le: 15 janvier 2026                              │   │
│  │    [Sélectionner] [Paramètres] [Supprimer]              │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ 📋 Tournoi Été 2025 (Archivé)                           │   │
│  │    Statut: Terminé │ 32 joueurs │ 4 catégories          │   │
│  │    Créé le: 10 juillet 2025                              │   │
│  │    [Consulter] [Dupliquer] [Supprimer]                  │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Actions sur chaque Tournoi

| Bouton | Condition | Action |
|--------|-----------|--------|
| Sélectionner | Tournoi non terminé | Définir comme tournoi actif |
| Paramètres | Tournoi actif | Aller à la page Paramètres |
| Consulter | Tournoi terminé | Voir les résultats (lecture seule) |
| Dupliquer | Toujours | Créer une copie avec nouveaux joueurs |
| Supprimer | Admin + Tournoi pas "En cours" | Supprimer après confirmation |

---

## 2. Création de Tournoi

### Formulaire de Création

```
┌─────────────────────────────────────────────────────────────────┐
│  NOUVEAU TOURNOI                                                │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Informations générales                                         │
│  ─────────────────────                                          │
│  Nom du tournoi *                                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Méli-Mélo Terrebonne 2026                               │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Date du tournoi                                                │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ 📅 25 janvier 2026                                      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ☐ Tournoi ouvert (pas de critère d'âge)                       │
│                                                                 │
│  ──────────────────────────────────────────────────────────    │
│                                                                 │
│  Horaires                                                       │
│  ────────                                                       │
│  Heure de début des rondes        Heure de début des séries     │
│  ┌───────────────────┐            ┌───────────────────┐         │
│  │ 09:00             │            │ 13:30             │         │
│  └───────────────────┘            └───────────────────┘         │
│                                                                 │
│  ──────────────────────────────────────────────────────────    │
│                                                                 │
│  Paramètres des parties                                         │
│  ──────────────────────                                         │
│  Nombre de parties par joueur     Durée par partie (minutes)    │
│  ┌───────────────────┐            ┌───────────────────┐         │
│  │ 4                 │            │ 15                │         │
│  └───────────────────┘            └───────────────────┘         │
│  (rondes préliminaires)           (incluant battement)          │
│                                                                 │
│  ──────────────────────────────────────────────────────────    │
│                                                                 │
│                          [Annuler]  [Créer le tournoi]          │
└─────────────────────────────────────────────────────────────────┘
```

### Champs du Formulaire

| Champ | Type | Obligatoire | Valeur par défaut | Validation |
|-------|------|-------------|-------------------|------------|
| Nom du tournoi | Texte | Oui | - | 3-200 caractères |
| Date du tournoi | Date | Non | Aujourd'hui | Date future ou aujourd'hui |
| Tournoi ouvert | Checkbox | Non | Non coché | - |
| Heure début rondes | Heure | Oui | 09:00 | Format HH:MM |
| Heure début séries | Oui | Oui | 13:30 | Après heure rondes |
| Nb parties/joueur | Nombre | Oui | 4 | Entre 2 et 10 |
| Durée partie | Nombre | Oui | 15 | Entre 10 et 30 minutes |

### Comportement "Créer le tournoi"

**Clic →**
1. Valider tous les champs
2. Si erreur: afficher les messages sous les champs concernés
3. Si valide: créer le tournoi
4. Rediriger vers la page Paramètres du nouveau tournoi
5. Afficher message: "Tournoi créé avec succès"

---

## 3. Paramètres du Tournoi

### Structure de la Page

```
┌─────────────────────────────────────────────────────────────────┐
│  PARAMÈTRES: Méli-Mélo Terrebonne 2026      [Statut: Brouillon] │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  [Onglet: Général] [Onglet: Terrains] [Onglet: Pauses]         │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    CONTENU DE L'ONGLET                  │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│                          [Annuler]  [Enregistrer]               │
└─────────────────────────────────────────────────────────────────┘
```

### Onglet "Général"

Mêmes champs que la création, mais modifiables.

**Restrictions selon le statut**:

| Statut | Champs modifiables |
|--------|-------------------|
| Brouillon | Tous |
| Joueurs inscrits | Tous |
| Rondes générées | Nom, Date, Heure séries |
| Rondes en cours | Nom, Date uniquement |
| Séries en cours | Nom uniquement |
| Terminé | Aucun (lecture seule) |

**Avertissement si modification pendant rondes**:
- Message: "Modifier ces paramètres pendant le tournoi peut affecter la cédule."
- Demander confirmation avant d'enregistrer

---

## 4. Gestion des Terrains (Onglet)

### Affichage

```
┌─────────────────────────────────────────────────────────────────┐
│  TERRAINS                                    [+ Ajouter terrain] │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  │ # │ Nom du terrain          │ Actif │ Actions            │  │
│  ├───┼─────────────────────────┼───────┼────────────────────┤  │
│  │ 1 │ Central Gym 1           │  ✅   │ [Modifier] [🗑️]   │  │
│  │ 2 │ Central Gym 2           │  ✅   │ [Modifier] [🗑️]   │  │
│  │ 3 │ Terrain Annexe          │  ❌   │ [Modifier] [🗑️]   │  │
│  │ 4 │ Terrain Extérieur       │  ✅   │ [Modifier] [🗑️]   │  │
│                                                                 │
│  ℹ️ Les terrains inactifs ne seront pas utilisés pour la       │
│     génération de la cédule.                                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Ajouter/Modifier un Terrain

**Modale**:
```
┌─────────────────────────────────────┐
│  Ajouter un terrain                 │
│  ───────────────────                │
│                                     │
│  Numéro *        Nom                │
│  ┌─────────┐     ┌───────────────┐  │
│  │ 5       │     │               │  │
│  └─────────┘     └───────────────┘  │
│                                     │
│  ☑️ Terrain actif                   │
│                                     │
│       [Annuler]  [Enregistrer]      │
└─────────────────────────────────────┘
```

| Champ | Obligatoire | Validation |
|-------|-------------|------------|
| Numéro | Oui | Entier > 0, unique |
| Nom | Non | Max 100 caractères |
| Actif | Non | Par défaut: oui |

### Suppression d'un Terrain

- **Si aucune partie assignée**: Suppression directe avec confirmation
- **Si parties assignées**: Message "Ce terrain a des parties assignées. Désactivez-le plutôt."

---

## 5. Périodes de Pause (Onglet)

### Affichage

```
┌─────────────────────────────────────────────────────────────────┐
│  PÉRIODES DE PAUSE                            [+ Ajouter pause]  │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  │ Description       │ Début  │ Fin    │ Actions            │  │
│  ├───────────────────┼────────┼────────┼────────────────────┤  │
│  │ Dîner             │ 12:00  │ 13:00  │ [Modifier] [🗑️]   │  │
│  │ Pause collation   │ 10:30  │ 10:45  │ [Modifier] [🗑️]   │  │
│                                                                 │
│  ℹ️ Aucune partie ne sera planifiée pendant ces périodes.      │
│     Maximum 3 périodes de pause.                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Ajouter/Modifier une Pause

**Modale**:
```
┌─────────────────────────────────────┐
│  Ajouter une période de pause       │
│  ────────────────────────────       │
│                                     │
│  Description                        │
│  ┌───────────────────────────────┐  │
│  │ Dîner                         │  │
│  └───────────────────────────────┘  │
│                                     │
│  Heure début *     Heure fin *      │
│  ┌─────────────┐   ┌─────────────┐  │
│  │ 12:00       │   │ 13:00       │  │
│  └─────────────┘   └─────────────┘  │
│                                     │
│       [Annuler]  [Enregistrer]      │
└─────────────────────────────────────┘
```

**Validation**:
- Heure fin > Heure début
- Pas de chevauchement avec autres pauses
- Maximum 3 périodes
- Périodes entre heure début rondes et heure début séries

---

## Actions Globales

### Bouton "Enregistrer" (bas de page)

- Sauvegarde tous les changements de l'onglet actif
- Message de confirmation: "Paramètres enregistrés"
- Reste sur la même page

### Bouton "Annuler"

- Annule les changements non enregistrés
- Demande confirmation si modifications en cours
- Retour au Dashboard

### Supprimer le Tournoi (Admin seulement)

- Bouton dans l'onglet Général ou menu d'actions
- **Condition**: Tournoi pas "En cours" ni "Terminé"
- Confirmation requise: "Cette action est irréversible. Supprimer le tournoi ?"
- Si confirmé: Suppression et retour à la liste des tournois

---

## Messages d'Erreur

| Situation | Message |
|-----------|---------|
| Nom vide | "Le nom du tournoi est obligatoire." |
| Nom trop court | "Le nom doit contenir au moins 3 caractères." |
| Heure séries avant rondes | "L'heure des séries doit être après l'heure des rondes." |
| Nb parties invalide | "Le nombre de parties doit être entre 2 et 10." |
| Pas de terrain actif | "Au moins un terrain actif est requis." |
| Modification impossible | "Ce paramètre ne peut plus être modifié une fois le tournoi en cours." |

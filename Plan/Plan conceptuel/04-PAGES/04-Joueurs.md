# Page: Gestion des Joueurs

## Objectif
Gérer la liste des joueurs du tournoi: ajout manuel, import CSV, modification, suppression, et gestion des statuts (actif, substitut).

---

## Accès
- **Rôles**: Administrateur (tout), Superviseur (ajout/modification seulement)
- **Menu**: Joueurs > Liste des joueurs

---

## Sous-pages

1. **Liste des Joueurs** — Vue tableau de tous les joueurs
2. **Fiche Joueur** — Détail et modification d'un joueur
3. **Import CSV** — Import en masse

---

## 1. Liste des Joueurs

### Affichage Principal

```
┌─────────────────────────────────────────────────────────────────────────┐
│  JOUEURS (45)                        [🔍 Rechercher]  [+ Ajouter joueur] │
│  ───────────────────────────────────────────────────────────────────── │
│                                                                         │
│  Filtres: [Catégorie ▼] [Sexe ▼] [Niveau ▼] [Statut ▼]  [Réinitialiser] │
│                                                                         │
│  ┌────┬──────────────────┬───────┬─────┬─────────┬────────────┬───────┐ │
│  │ #  │ Nom              │ Sexe  │ Âge │ Niveau  │ Catégorie  │ Stat. │ │
│  ├────┼──────────────────┼───────┼─────┼─────────┼────────────┼───────┤ │
│  │ 1  │ Tremblay, Jean   │ H     │ 35  │ 3.5     │ H-35-3.5   │ ✅    │ │
│  │ 2  │ Gagnon, Marie    │ F     │ 28  │ 4.0     │ F-28-4.0   │ ✅    │ │
│  │ 3  │ Lavoie, Pierre   │ H     │ 42  │ 3.5     │ H-35-3.5   │ ✅    │ │
│  │ 4  │ Roy, Sophie      │ F     │ 55  │ Nov.    │ F-50-Nov   │ ✅    │ │
│  │ 5  │ [Substitut 1]    │ H     │ 30  │ 3.5     │ H-35-3.5   │ 🔄    │ │
│  │ 6  │ Martin, Luc      │ H     │ 38  │ 4.0     │ -          │ ⚠️    │ │
│  └────┴──────────────────┴───────┴─────┴─────────┴────────────┴───────┘ │
│                                                                         │
│  Légende: ✅ Actif  🔄 Substitut  ⚠️ Sans catégorie  ❌ Inactif        │
│                                                                         │
│  Affichage: 1-20 sur 45        [◀ Précédent] [Page 1 ▼] [Suivant ▶]   │
│                                                                         │
│  Actions groupées: [☐ Tout sélectionner]  [Supprimer sélection]        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Colonnes du Tableau

| Colonne | Description | Triable | Action au clic |
|---------|-------------|---------|----------------|
| # | Numéro de ligne | Non | - |
| Nom | Nom, Prénom | Oui | Ouvrir fiche joueur |
| Sexe | H ou F | Oui | - |
| Âge | Âge en années | Oui | - |
| Niveau | 3.0-5.0 ou texte | Oui | - |
| Catégorie | Nom de la catégorie | Oui | Lien vers catégorie |
| Statut | Icône de statut | Oui | - |

### Filtres

| Filtre | Options |
|--------|---------|
| Catégorie | Toutes, [liste des catégories], Sans catégorie |
| Sexe | Tous, Homme, Femme |
| Niveau | Tous, 3.0, 3.5, 4.0, 4.5, 5.0, Novice, Intermédiaire, Avancé |
| Statut | Tous, Actifs, Inactifs, Substituts |

### Recherche

- Champ de recherche textuelle
- Recherche sur: Nom, Prénom, Numéro de membre
- Recherche instantanée (au fur et à mesure de la frappe)

### Actions sur la Liste

| Bouton | Rôle requis | Action |
|--------|-------------|--------|
| + Ajouter joueur | Admin/Superviseur | Ouvrir modale d'ajout |
| Import CSV | Admin/Superviseur | Aller à la page Import |
| Supprimer sélection | Admin | Supprimer les joueurs cochés |
| Exporter | Admin/Superviseur | Télécharger CSV de la liste |

---

## 2. Modale/Page Ajout de Joueur

### Formulaire

```
┌─────────────────────────────────────────────────────┐
│  AJOUTER UN JOUEUR                                  │
│  ──────────────────                                 │
│                                                     │
│  Nom *                        Prénom *              │
│  ┌─────────────────────┐      ┌─────────────────┐   │
│  │ Tremblay            │      │ Jean            │   │
│  └─────────────────────┘      └─────────────────┘   │
│                                                     │
│  Sexe *                       Âge *                 │
│  ┌─────────────────────┐      ┌─────────────────┐   │
│  │ ○ Homme  ○ Femme    │      │ 35              │   │
│  └─────────────────────┘      └─────────────────┘   │
│                                                     │
│  Niveau *                                           │
│  ┌─────────────────────────────────────────────┐   │
│  │ 3.5                                     ▼   │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  Numéro de membre (facultatif)                      │
│  ┌─────────────────────────────────────────────┐   │
│  │ 12345                                       │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  ☐ Marquer comme substitut                          │
│    (Ne cumulera pas de points)                      │
│                                                     │
│              [Annuler]  [Ajouter]                   │
│                                                     │
│  [Ajouter et continuer] ← Pour ajout multiple      │
└─────────────────────────────────────────────────────┘
```

### Champs

| Champ | Type | Obligatoire | Validation |
|-------|------|-------------|------------|
| Nom | Texte | Oui | 2-100 caractères |
| Prénom | Texte | Oui | 2-100 caractères |
| Sexe | Radio | Oui | Homme ou Femme |
| Âge | Nombre | Oui | Entre 5 et 100 |
| Niveau | Dropdown | Oui | Liste prédéfinie |
| Numéro membre | Texte | Non | Max 50 caractères |
| Substitut | Checkbox | Non | Par défaut: non |

### Comportements

**Bouton "Ajouter"**:
1. Valider les champs
2. Vérifier doublon (même nom + prénom dans ce tournoi)
3. Si doublon: "Un joueur avec ce nom existe déjà."
4. Sinon: Ajouter et fermer la modale
5. Message: "Joueur ajouté avec succès"
6. Rafraîchir la liste

**Bouton "Ajouter et continuer"**:
- Même comportement mais garde la modale ouverte
- Réinitialise le formulaire pour ajout suivant

---

## 3. Fiche Joueur (Détail)

### Affichage

```
┌─────────────────────────────────────────────────────────────────┐
│  ← Retour à la liste                                            │
│                                                                 │
│  JEAN TREMBLAY                          [Modifier] [Supprimer]  │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  ┌─────────────────────────┐  ┌─────────────────────────────┐  │
│  │  INFORMATIONS           │  │  STATISTIQUES               │  │
│  │  ────────────           │  │  ───────────                │  │
│  │  Sexe: Homme            │  │  Parties jouées: 3/4        │  │
│  │  Âge: 35 ans            │  │  Victoires: 2               │  │
│  │  Niveau: 3.5            │  │  Différentiel: 5            │  │
│  │  N° membre: 12345       │  │  Points marqués: 28         │  │
│  │                         │  │  Classement: 3e / 12        │  │
│  │  Catégorie:             │  │                             │  │
│  │  Homme - 35-50 - 3.5    │  │                             │  │
│  │  [Changer catégorie]    │  │                             │  │
│  │                         │  │                             │  │
│  │  Statut: ✅ Actif       │  │                             │  │
│  │  [Désactiver]           │  │                             │  │
│  └─────────────────────────┘  └─────────────────────────────┘  │
│                                                                 │
│  HISTORIQUE DES PARTIES                                         │
│  ──────────────────────                                         │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Partie #12 │ Avec: Marie L. │ Vs: Pierre G. + Sophie R. │   │
│  │ Résultat: Victoire 11-8 │ Terrain 2 │ 09:15             │   │
│  ├─────────────────────────────────────────────────────────┤   │
│  │ Partie #18 │ Avec: Luc M.   │ Vs: Anne B. + Marc D.     │   │
│  │ Résultat: Défaite 7-11  │ Terrain 1 │ 09:30             │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Actions sur la Fiche

| Bouton | Rôle | Condition | Action |
|--------|------|-----------|--------|
| Modifier | Admin/Superviseur | Toujours | Ouvrir formulaire modification |
| Supprimer | Admin | Pas de parties jouées | Supprimer avec confirmation |
| Changer catégorie | Admin | Catégories générées | Modale de sélection |
| Désactiver/Activer | Admin/Superviseur | Toujours | Changer le statut |
| Marquer substitut | Admin | Toujours | Transformer en substitut |

### Modale "Changer de Catégorie"

```
┌─────────────────────────────────────────┐
│  CHANGER LA CATÉGORIE                   │
│  ─────────────────────                  │
│                                         │
│  Catégorie actuelle: Homme - 35-50 - 3.5│
│                                         │
│  Nouvelle catégorie:                    │
│  ┌─────────────────────────────────┐    │
│  │ ○ Homme - 20-35 - 3.5  (8 j.)  │    │
│  │ ○ Homme - 35-50 - 3.5  (12 j.) │    │
│  │ ○ Homme - 35-50 - 4.0  (10 j.) │    │
│  │ ○ Homme - 50+ - 3.5    (6 j.)  │    │
│  └─────────────────────────────────┘    │
│                                         │
│  ⚠️ Si les rondes sont générées, la    │
│  cédule devra être régénérée.          │
│                                         │
│           [Annuler]  [Confirmer]        │
└─────────────────────────────────────────┘
```

---

## 4. Import CSV

### Page d'Import

```
┌─────────────────────────────────────────────────────────────────┐
│  IMPORTER DES JOUEURS (CSV)                                     │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Étape 1: Télécharger le modèle                                 │
│  ─────────────────────────────                                  │
│  [📥 Télécharger le modèle CSV]                                 │
│                                                                 │
│  ──────────────────────────────────────────────────────────    │
│                                                                 │
│  Étape 2: Sélectionner votre fichier                           │
│  ───────────────────────────────────                            │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │     📁 Glissez votre fichier ici                       │   │
│  │        ou cliquez pour sélectionner                     │   │
│  │                                                         │   │
│  │     Formats acceptés: .csv                              │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ──────────────────────────────────────────────────────────    │
│                                                                 │
│  Étape 3: Vérifier et importer                                  │
│  ─────────────────────────────                                  │
│  (Apparaît après sélection du fichier)                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Format CSV Attendu

```csv
Nom;Prenom;Sexe;Age;Niveau;NumeroMembre
Tremblay;Jean;H;35;3.5;12345
Gagnon;Marie;F;28;4.0;
Lavoie;Pierre;Homme;42;Intermédiaire;67890
```

**Règles**:
- Séparateur: point-virgule (;) ou virgule (,)
- Première ligne = en-têtes (obligatoire)
- Sexe accepté: H, F, Homme, Femme
- Niveau accepté: 3.0, 3.5, 4.0, 4.5, 5.0, Novice, Intermédiaire, Avancé
- NumeroMembre: facultatif (peut être vide)

### Aperçu Avant Import

```
┌─────────────────────────────────────────────────────────────────┐
│  APERÇU DE L'IMPORT                                             │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Fichier: joueurs_tournoi.csv                                   │
│  Lignes détectées: 45                                           │
│                                                                 │
│  ✅ 42 joueurs valides                                          │
│  ⚠️ 2 joueurs avec avertissements                              │
│  ❌ 1 joueur en erreur                                          │
│                                                                 │
│  ┌────┬────────────────┬────────────────────────────────────┐  │
│  │ #  │ Joueur         │ Statut                             │  │
│  ├────┼────────────────┼────────────────────────────────────┤  │
│  │ 1  │ Tremblay, Jean │ ✅ Valide                          │  │
│  │ 2  │ Gagnon, Marie  │ ✅ Valide                          │  │
│  │ 3  │ Lavoie, Pierre │ ⚠️ Doublon possible (Pierre L.)   │  │
│  │ 4  │ Roy, Sophie    │ ❌ Âge invalide: "abc"             │  │
│  │ .. │ ...            │                                    │  │
│  └────┴────────────────┴────────────────────────────────────┘  │
│                                                                 │
│  ☐ Ignorer les lignes en erreur et importer le reste           │
│                                                                 │
│              [Annuler]  [Importer 42 joueurs]                   │
└─────────────────────────────────────────────────────────────────┘
```

### Résultat de l'Import

```
┌─────────────────────────────────────────┐
│  IMPORT TERMINÉ                         │
│  ───────────────                        │
│                                         │
│  ✅ 42 joueurs importés avec succès     │
│  ⚠️ 2 joueurs ignorés (avertissements) │
│  ❌ 1 joueur ignoré (erreur)            │
│                                         │
│  [Voir le détail des erreurs]           │
│                                         │
│  [Retour à la liste des joueurs]        │
└─────────────────────────────────────────┘
```

---

## Gestion des Substituts

### Qu'est-ce qu'un Substitut?

Un substitut est un joueur de remplacement qui:
- Peut jouer à la place d'un joueur absent
- **Ne cumule PAS de points** pour le classement
- Ses adversaires et partenaires comptent normalement

### Transformer en Substitut

1. Ouvrir la fiche du joueur
2. Cliquer "Marquer comme substitut"
3. Le nom change pour "[Substitut X]" ou on garde le nom avec un indicateur
4. Confirmation: "Ce joueur ne cumulera plus de points. Continuer?"

### Nommage des Substituts

Deux options possibles:
- **Option A**: Renommer en "Substitut 1", "Substitut 2", etc.
- **Option B**: Garder le nom mais avec badge "Substitut"

L'admin choisit selon la spécification originale (renommage préféré).

---

## Messages d'Erreur

| Situation | Message |
|-----------|---------|
| Nom vide | "Le nom est obligatoire." |
| Prénom vide | "Le prénom est obligatoire." |
| Âge invalide | "L'âge doit être un nombre entre 5 et 100." |
| Doublon | "Un joueur nommé X Y existe déjà dans ce tournoi." |
| Suppression impossible | "Ce joueur a des parties assignées. Désactivez-le plutôt." |
| CSV invalide | "Le fichier n'est pas un CSV valide." |
| CSV colonnes manquantes | "Colonnes manquantes: Nom, Age" |

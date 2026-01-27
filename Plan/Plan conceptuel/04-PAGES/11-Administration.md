# Page: Administration

## Objectif
Gérer les utilisateurs du système, les paramètres globaux de l'application, et les configurations par défaut. Accessible uniquement aux administrateurs.

---

## Accès
- **Rôles**: Administrateur uniquement
- **Menu**: ⚙️ Administration

---

## Sections de l'Administration

1. **Gestion des Utilisateurs** — Créer, modifier, supprimer des comptes
2. **Paramètres Globaux** — Configuration de l'application
3. **Paramètres par Défaut** — Valeurs par défaut pour nouveaux tournois
4. **Sauvegarde et Restauration** — Backup des données

---

## 1. Gestion des Utilisateurs

### Liste des Utilisateurs

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  GESTION DES UTILISATEURS                               [+ Nouvel utilisateur]│
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  ┌──────────────────────┬──────────────┬─────────────────┬─────────────────┐│
│  │ Utilisateur          │ Rôle         │ Dernière connex.│ Actions         ││
│  ├──────────────────────┼──────────────┼─────────────────┼─────────────────┤│
│  │ admin@club.com       │ Admin        │ Aujourd'hui     │ [✏️] [🔑]       ││
│  │ jean.tremblay@...    │ Admin        │ 14 jan 2026     │ [✏️] [🔑] [🗑️] ││
│  │ marie.superviseur@...│ Superviseur  │ 14 jan 2026     │ [✏️] [🔑] [🗑️] ││
│  │ pierre.score@...     │ Superviseur  │ 13 jan 2026     │ [✏️] [🔑] [🗑️] ││
│  └──────────────────────┴──────────────┴─────────────────┴─────────────────┘│
│                                                                             │
│  Légende: [✏️] Modifier  [🔑] Réinitialiser mot de passe  [🗑️] Supprimer  │
│                                                                             │
│  ℹ️ Vous ne pouvez pas supprimer votre propre compte.                      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Créer un Utilisateur

```
┌─────────────────────────────────────────────────────────────────┐
│  NOUVEL UTILISATEUR                                             │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Nom complet *                                                  │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Jean Tremblay                                           │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Adresse courriel *                                             │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ jean.tremblay@email.com                                 │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Rôle *                                                         │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ○ Administrateur                                        │   │
│  │   - Accès complet à toutes les fonctionnalités         │   │
│  │   - Peut créer/modifier des tournois                    │   │
│  │   - Peut gérer les utilisateurs                         │   │
│  │                                                         │   │
│  │ ○ Superviseur                                           │   │
│  │   - Peut saisir et modifier des scores                  │   │
│  │   - Peut ajouter des joueurs                            │   │
│  │   - Ne peut pas modifier la structure du tournoi        │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Mot de passe temporaire *                                      │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ••••••••••                                              │   │
│  └─────────────────────────────────────────────────────────┘   │
│  [🔄 Générer automatiquement]                                  │
│                                                                 │
│  ☑️ Forcer le changement de mot de passe à la première connexion│
│                                                                 │
│              [Annuler]  [Créer l'utilisateur]                  │
└─────────────────────────────────────────────────────────────────┘
```

### Modifier un Utilisateur

```
┌─────────────────────────────────────────────────────────────────┐
│  MODIFIER L'UTILISATEUR                                         │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Nom complet                                                    │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Jean Tremblay                                           │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Adresse courriel (non modifiable)                              │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ jean.tremblay@email.com                          🔒     │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Rôle                                                           │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Administrateur                                      ▼   │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Statut du compte:                                              │
│  ○ Actif                                                        │
│  ○ Désactivé (ne peut plus se connecter)                       │
│                                                                 │
│              [Annuler]  [Sauvegarder]                          │
└─────────────────────────────────────────────────────────────────┘
```

### Réinitialiser un Mot de Passe

```
┌─────────────────────────────────────────────────────────────────┐
│  RÉINITIALISER LE MOT DE PASSE                                 │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Utilisateur: jean.tremblay@email.com                          │
│                                                                 │
│  Nouveau mot de passe:                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ••••••••                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│  [🔄 Générer automatiquement]                                  │
│                                                                 │
│  ☑️ Forcer le changement à la prochaine connexion              │
│                                                                 │
│  ⚠️ Envoyez ce mot de passe à l'utilisateur de façon sécurisée │
│                                                                 │
│              [Annuler]  [Réinitialiser]                        │
└─────────────────────────────────────────────────────────────────┘
```

---

## 2. Paramètres Globaux

### Page des Paramètres

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  PARAMÈTRES GLOBAUX                                                         │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  IDENTITÉ DE L'APPLICATION                                                  │
│  ─────────────────────────                                                  │
│                                                                             │
│  Nom du club / organisation:                                                │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Club de Pickleball de Montréal                                      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  Logo:                                                                      │
│  ┌───────────────┐                                                          │
│  │     [Logo]    │  [📤 Changer le logo]                                   │
│  │               │  Formats: PNG, JPG (max 2MB)                            │
│  └───────────────┘                                                          │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  AFFICHAGE                                                                  │
│  ─────────                                                                  │
│                                                                             │
│  Format de date:                                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ JJ/MM/AAAA (ex: 15/01/2026)                                     ▼   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  Format d'heure:                                                            │
│  ○ 12 heures (ex: 9:30 AM)                                                 │
│  ○ 24 heures (ex: 09:30)                                                   │
│                                                                             │
│  Langue:                                                                    │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Français                                                        ▼   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  SESSION                                                                    │
│  ───────                                                                    │
│                                                                             │
│  Durée d'inactivité avant déconnexion:                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 60 minutes                                                      ▼   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│                                            [Sauvegarder les paramètres]    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Paramètres par Défaut des Tournois

### Configuration des Valeurs par Défaut

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  PARAMÈTRES PAR DÉFAUT DES TOURNOIS                                         │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Ces valeurs seront pré-remplies lors de la création d'un nouveau tournoi. │
│                                                                             │
│  CATÉGORISATION                                                             │
│  ──────────────                                                             │
│                                                                             │
│  Système de niveau par défaut:                                              │
│  ○ DUPR (3.0, 3.5, 4.0, 4.5, 5.0)                                          │
│  ○ Textuel (Novice, Intermédiaire, Avancé)                                 │
│                                                                             │
│  Tranches d'âge par défaut:                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 1. De 0 à 20 ans                                               [🗑️] │   │
│  │ 2. De 20 à 35 ans                                              [🗑️] │   │
│  │ 3. De 35 à 50 ans                                              [🗑️] │   │
│  │ 4. De 50 à 99 ans                                              [🗑️] │   │
│  │ [+ Ajouter une tranche]                                             │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  RONDES                                                                     │
│  ──────                                                                     │
│                                                                             │
│  Durée estimée par match:                                                   │
│  ┌───────────────┐                                                          │
│  │ 15    minutes │                                                          │
│  └───────────────┘                                                          │
│                                                                             │
│  Nombre de rondes par défaut:                                               │
│  ┌───────────────┐                                                          │
│  │ 4             │                                                          │
│  └───────────────┘                                                          │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  SCORES                                                                     │
│  ──────                                                                     │
│                                                                             │
│  Score minimum pour gagner:                                                 │
│  ┌───────────────┐                                                          │
│  │ 11    points  │                                                          │
│  └───────────────┘                                                          │
│                                                                             │
│  Écart minimum requis:                                                      │
│  ┌───────────────┐                                                          │
│  │ 2     points  │                                                          │
│  └───────────────┘                                                          │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  SÉRIES ÉLIMINATOIRES                                                       │
│  ────────────────────                                                       │
│                                                                             │
│  Format par défaut:                                                         │
│  ○ Élimination simple                                                       │
│  ○ Élimination double                                                       │
│                                                                             │
│  Nombre de qualifiés par défaut:                                            │
│  ┌───────────────┐                                                          │
│  │ 8     joueurs │                                                          │
│  └───────────────┘                                                          │
│                                                                             │
│                                            [Sauvegarder les paramètres]    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Sauvegarde et Restauration

### Page de Sauvegarde

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  SAUVEGARDE ET RESTAURATION                                                 │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  CRÉER UNE SAUVEGARDE                                                       │
│  ────────────────────                                                       │
│                                                                             │
│  Contenu à sauvegarder:                                                     │
│  ☑️ Tous les tournois et leurs données                                     │
│  ☑️ Liste des joueurs                                                      │
│  ☑️ Utilisateurs et rôles                                                  │
│  ☑️ Paramètres de l'application                                            │
│                                                                             │
│  [💾 Créer une sauvegarde maintenant]                                      │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  SAUVEGARDES EXISTANTES                                                     │
│  ──────────────────────                                                     │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Date                 │ Taille   │ Contenu              │ Actions    │   │
│  ├──────────────────────┼──────────┼──────────────────────┼────────────┤   │
│  │ 15/01/2026 - 08:00   │ 2.4 MB   │ Complet              │ [📥] [🗑️]  │   │
│  │ 14/01/2026 - 18:00   │ 2.3 MB   │ Complet              │ [📥] [🗑️]  │   │
│  │ 10/01/2026 - 10:30   │ 1.8 MB   │ Tournois seulement   │ [📥] [🗑️]  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  RESTAURER UNE SAUVEGARDE                                                   │
│  ────────────────────────                                                   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                                                                     │   │
│  │     📁 Glissez un fichier de sauvegarde ici                        │   │
│  │        ou cliquez pour sélectionner                                 │   │
│  │                                                                     │   │
│  │     Format: .backup                                                 │   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ⚠️ La restauration remplacera TOUTES les données actuelles.              │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Confirmation de Restauration

```
┌─────────────────────────────────────────────────────────────────┐
│  ⚠️ CONFIRMER LA RESTAURATION                                  │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Fichier: backup_15012026_080000.backup                        │
│  Date de la sauvegarde: 15/01/2026 08:00                       │
│                                                                 │
│  ATTENTION:                                                     │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Cette action va:                                        │   │
│  │ • Supprimer TOUTES les données actuelles               │   │
│  │ • Restaurer les données de la sauvegarde               │   │
│  │ • Cette action est IRRÉVERSIBLE                        │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Pour confirmer, tapez "RESTAURER":                            │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│              [Annuler]  [Confirmer la restauration]            │
└─────────────────────────────────────────────────────────────────┘
```

---

## 5. Mon Profil (Accessible à tous)

### Page Profil

Accessible depuis l'avatar en haut à droite:

```
┌─────────────────────────────────────────────────────────────────┐
│  MON PROFIL                                                     │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  INFORMATIONS                                                   │
│  ────────────                                                   │
│                                                                 │
│  Nom: Jean Tremblay                                            │
│  Courriel: jean.tremblay@email.com                             │
│  Rôle: Administrateur                                          │
│                                                                 │
│  [✏️ Modifier mon nom]                                         │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  CHANGER MON MOT DE PASSE                                       │
│  ────────────────────────                                       │
│                                                                 │
│  Mot de passe actuel:                                           │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ••••••••                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Nouveau mot de passe:                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ••••••••                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Confirmer le nouveau mot de passe:                            │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ ••••••••                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  [Changer le mot de passe]                                     │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  SESSIONS ACTIVES                                               │
│  ────────────────                                               │
│                                                                 │
│  • Chrome sur Windows (Actuelle)                               │
│  • Safari sur iPad - Dernière activité: il y a 2 heures       │
│    [Déconnecter cette session]                                 │
│                                                                 │
│  [Déconnecter toutes les autres sessions]                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Règles de Sécurité des Mots de Passe

### Exigences

- Minimum 8 caractères
- Au moins une lettre majuscule
- Au moins une lettre minuscule
- Au moins un chiffre
- (Optionnel) Au moins un caractère spécial

### Indicateur de Force

```
Mot de passe: [••••••••          ]

Force: ████████░░ Fort
       ✅ 8+ caractères
       ✅ Majuscule
       ✅ Minuscule
       ✅ Chiffre
       ⚠️ Caractère spécial (recommandé)
```

---

## Messages et Alertes

| Action | Message |
|--------|---------|
| Utilisateur créé | "Utilisateur créé avec succès. Un courriel a été envoyé." |
| Utilisateur modifié | "Modifications enregistrées." |
| Utilisateur supprimé | "L'utilisateur a été supprimé." |
| Mot de passe réinitialisé | "Mot de passe réinitialisé. Communiquez-le à l'utilisateur." |
| Paramètres sauvegardés | "Paramètres enregistrés." |
| Sauvegarde créée | "Sauvegarde créée avec succès (2.4 MB)." |
| Restauration réussie | "Restauration terminée. Reconnectez-vous." |
| Mot de passe changé | "Votre mot de passe a été modifié." |

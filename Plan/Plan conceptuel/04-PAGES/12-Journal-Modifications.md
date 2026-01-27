# Page: Journal des Modifications

## Objectif
Tracer toutes les modifications importantes effectuées dans l'application pour permettre l'audit, le dépannage et la transparence des actions.

---

## Accès
- **Rôles**: Administrateur (complet), Superviseur (ses propres actions seulement)
- **Menu**: ⚙️ Administration > Journal des modifications

---

## Pourquoi un Journal?

### Cas d'Usage

1. **Audit**: Qui a modifié quoi et quand?
2. **Dépannage**: Comprendre pourquoi une donnée a changé
3. **Responsabilité**: Savoir qui a fait une action contestée
4. **Transparence**: Les superviseurs voient leurs propres actions

### Actions Journalisées

| Catégorie | Actions tracées |
|-----------|-----------------|
| Tournoi | Création, modification, suppression |
| Joueurs | Ajout, modification, suppression, changement de catégorie |
| Catégories | Génération, fusion, modification manuelle |
| Cédule | Génération, régénération, modification de match |
| Scores | Saisie initiale, modification, annulation |
| Séries | Génération bracket, modification équipes, scores |
| Utilisateurs | Création, modification, suppression, connexion |
| Système | Sauvegarde, restauration, modification paramètres |

---

## Affichage Principal

### Vue par Défaut (Récent)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  JOURNAL DES MODIFICATIONS                                                  │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Filtres:                                                                   │
│  [Date: Aujourd'hui ▼] [Utilisateur: Tous ▼] [Type: Tous ▼] [🔍 Rechercher] │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 10:45:32                                              │   │
│  │ 👤 jean.tremblay@email.com (Admin)                                  │   │
│  │ 📝 SCORE MODIFIÉ                                                    │   │
│  │    Match #12 (Ronde 2, Terrain 1)                                   │   │
│  │    Avant: 11-8 → Après: 11-9                                        │   │
│  │    Raison: "Erreur de saisie initiale"                              │   │
│  │    [Voir les détails]                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 10:32:15                                              │   │
│  │ 👤 marie.superviseur@email.com (Superviseur)                        │   │
│  │ ✅ SCORE SAISI                                                      │   │
│  │    Match #12 (Ronde 2, Terrain 1)                                   │   │
│  │    Score: 11-8 (Victoire Équipe A)                                  │   │
│  │    [Voir les détails]                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 09:15:00                                              │   │
│  │ 👤 jean.tremblay@email.com (Admin)                                  │   │
│  │ 🎲 CÉDULE GÉNÉRÉE                                                   │   │
│  │    Catégorie: Homme - 35-50 - 3.5                                   │   │
│  │    4 rondes, 24 matchs créés                                        │   │
│  │    [Voir les détails]                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 09:00:05                                              │   │
│  │ 👤 jean.tremblay@email.com (Admin)                                  │   │
│  │ 👥 JOUEUR AJOUTÉ                                                    │   │
│  │    Tremblay, Jean (H, 38 ans, 3.5)                                  │   │
│  │    Catégorie: Homme - 35-50 - 3.5                                   │   │
│  │    [Voir les détails]                                               │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 08:30:00                                              │   │
│  │ 👤 jean.tremblay@email.com (Admin)                                  │   │
│  │ 🔐 CONNEXION                                                        │   │
│  │    Depuis: Chrome sur Windows                                       │   │
│  │    IP: 192.168.1.100                                                │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  Affichage: 1-20 sur 156         [◀ Précédent] [Page 1 ▼] [Suivant ▶]     │
│                                                                             │
│  [📥 Exporter le journal (CSV)]                                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Types d'Entrées de Journal

### Icônes et Couleurs

| Icône | Type | Couleur |
|-------|------|---------|
| ✅ | Action de création/ajout | Vert |
| 📝 | Modification | Orange |
| 🗑️ | Suppression | Rouge |
| 🎲 | Génération (cédule, catégories) | Bleu |
| 🔐 | Connexion/Déconnexion | Gris |
| ⚠️ | Alerte/Erreur | Rouge |
| 💾 | Sauvegarde/Restauration | Violet |
| 👥 | Action sur joueur | Vert |
| 🏆 | Action sur séries | Or |

---

## Filtres

### Options de Filtrage

```
┌─────────────────────────────────────────────────────────────────┐
│  FILTRES AVANCÉS                                                │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Période:                                                       │
│  ○ Aujourd'hui                                                  │
│  ○ Cette semaine                                                │
│  ○ Ce mois                                                      │
│  ○ Personnalisée:                                               │
│    Du [15/01/2026] au [15/01/2026]                             │
│                                                                 │
│  Utilisateur:                                                   │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Tous les utilisateurs                               ▼   │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Type d'action:                                                 │
│  ☑️ Scores (saisie, modification)                              │
│  ☑️ Joueurs (ajout, modification, suppression)                 │
│  ☑️ Cédules (génération, modification)                         │
│  ☑️ Catégories (génération, fusion)                            │
│  ☑️ Séries (génération, scores)                                │
│  ☑️ Tournois (création, modification)                          │
│  ☑️ Utilisateurs (création, modification)                      │
│  ☐ Connexions (masquer par défaut)                             │
│  ☑️ Système (sauvegarde, restauration)                         │
│                                                                 │
│  Tournoi:                                                       │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Tous les tournois                                   ▼   │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Recherche textuelle:                                           │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Tremblay                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│              [Réinitialiser]  [Appliquer les filtres]          │
└─────────────────────────────────────────────────────────────────┘
```

---

## Détail d'une Entrée

### Modale de Détail

```
┌─────────────────────────────────────────────────────────────────┐
│  DÉTAIL DE L'ACTION                                             │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  📝 SCORE MODIFIÉ                                               │
│                                                                 │
│  Date: 15 janvier 2026 à 10:45:32                              │
│  Utilisateur: jean.tremblay@email.com (Administrateur)         │
│  Adresse IP: 192.168.1.100                                     │
│  Navigateur: Chrome 120 sur Windows 11                         │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  CONTEXTE                                                       │
│  ────────                                                       │
│  Tournoi: Méli-Mélo Janvier 2026                               │
│  Catégorie: Homme - 35-50 - 3.5                                │
│  Match #12: Ronde 2, Terrain 1                                 │
│  Équipe A: Tremblay + Lavoie                                   │
│  Équipe B: Martin + Roy                                        │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  MODIFICATIONS                                                  │
│  ─────────────                                                  │
│  ┌────────────────────┬──────────────┬──────────────┐          │
│  │ Champ              │ Avant        │ Après        │          │
│  ├────────────────────┼──────────────┼──────────────┤          │
│  │ Score Équipe A     │ 11           │ 11           │          │
│  │ Score Équipe B     │ 8            │ 9            │          │
│  │ Différentiel       │ +3           │ +2           │          │
│  └────────────────────┴──────────────┴──────────────┘          │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  RAISON FOURNIE                                                 │
│  ──────────────                                                 │
│  "Erreur de saisie initiale - Le score correct était 11-9"    │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  IMPACT                                                         │
│  ──────                                                         │
│  • Classement recalculé                                        │
│  • Différentiel de Martin: +5 → +6                             │
│  • Différentiel de Roy: +5 → +6                                │
│  • Différentiel de Tremblay: +12 → +11                         │
│  • Différentiel de Lavoie: +8 → +7                             │
│                                                                 │
│                              [Fermer]                           │
└─────────────────────────────────────────────────────────────────┘
```

---

## Types d'Entrées Détaillées

### Score Saisi

```
✅ SCORE SAISI
   Match #12 (Ronde 2, Terrain 1)
   Équipes: Tremblay+Lavoie vs Martin+Roy
   Score: 11-8 (Victoire Équipe A)
```

### Score Modifié

```
📝 SCORE MODIFIÉ
   Match #12 (Ronde 2, Terrain 1)
   Avant: 11-8 → Après: 11-9
   Raison: "Erreur de saisie initiale"
```

### Joueur Ajouté

```
✅ JOUEUR AJOUTÉ
   Nom: Tremblay, Jean
   Sexe: Homme, Âge: 38, Niveau: 3.5
   Catégorie assignée: Homme - 35-50 - 3.5
   Méthode: Ajout manuel
```

### Joueur Importé (CSV)

```
✅ IMPORT CSV
   45 joueurs importés
   2 ignorés (données invalides)
   Fichier: joueurs_tournoi.csv
```

### Cédule Générée

```
🎲 CÉDULE GÉNÉRÉE
   Catégorie: Homme - 35-50 - 3.5
   4 rondes créées
   24 matchs générés
   Options: Rotation maximale activée
```

### Cédule Régénérée

```
📝 CÉDULE RÉGÉNÉRÉE
   Catégorie: Homme - 35-50 - 3.5
   Ancienne cédule supprimée (8 scores perdus)
   Nouvelle cédule: 4 rondes, 24 matchs
   Raison: "Ajout de 2 nouveaux joueurs"
```

### Catégories Fusionnées

```
📝 CATÉGORIES FUSIONNÉES
   Catégorie 1: Femme - 50+ - 3.5 (2 joueurs)
   Catégorie 2: Femme - 35-50 - 3.5 (10 joueurs)
   Nouvelle catégorie: Femme - 35+ - 3.5 (12 joueurs)
```

### Séries Générées

```
🏆 SÉRIES GÉNÉRÉES
   Catégorie: Homme - 35-50 - 3.5
   Format: Élimination simple
   Équipes formées: 4
   Bracket créé: 3 matchs (2 demi + 1 finale)
```

### Match de Série Terminé

```
🏆 MATCH DE SÉRIE TERMINÉ
   Demi-finale 1
   Équipe 1 (Tremblay+Gagnon) bat Équipe 4 (Roy+Côté)
   Score: 11-7
   → Équipe 1 qualifiée pour la finale
```

### Connexion

```
🔐 CONNEXION
   Utilisateur: jean.tremblay@email.com
   Appareil: Chrome sur Windows 11
   IP: 192.168.1.100
   Localisation: Montréal, QC (si disponible)
```

### Déconnexion

```
🔐 DÉCONNEXION
   Utilisateur: jean.tremblay@email.com
   Durée de session: 2h 30min
   Type: Manuelle / Expiration
```

### Sauvegarde Créée

```
💾 SAUVEGARDE CRÉÉE
   Taille: 2.4 MB
   Contenu: Complet (tournois, joueurs, utilisateurs)
   Fichier: backup_15012026_080000.backup
```

### Restauration

```
💾 RESTAURATION EFFECTUÉE
   Fichier: backup_14012026_180000.backup
   Données restaurées: Tous les tournois et utilisateurs
   ⚠️ Données précédentes écrasées
```

---

## Export du Journal

### Format CSV

```
Date,Heure,Utilisateur,Type,Action,Détails,IP
2026-01-15,10:45:32,jean.tremblay@email.com,Score,Modification,"Match #12: 11-8 → 11-9",192.168.1.100
2026-01-15,10:32:15,marie.superviseur@email.com,Score,Saisie,"Match #12: 11-8",192.168.1.101
2026-01-15,09:15:00,jean.tremblay@email.com,Cédule,Génération,"Homme-35-50-3.5: 4 rondes",192.168.1.100
```

### Options d'Export

```
┌─────────────────────────────────────────────────────────────────┐
│  EXPORTER LE JOURNAL                                            │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Période à exporter:                                            │
│  ○ Données actuellement filtrées                               │
│  ○ Tout le journal                                             │
│  ○ Période personnalisée:                                       │
│    Du [01/01/2026] au [31/12/2026]                             │
│                                                                 │
│  Format:                                                        │
│  ○ CSV (Excel compatible)                                      │
│  ○ PDF (rapport formaté)                                       │
│                                                                 │
│              [Annuler]  [Exporter]                              │
└─────────────────────────────────────────────────────────────────┘
```

---

## Rétention des Données

### Politique de Conservation

- Les entrées de journal sont conservées pendant 1 an
- Après 1 an, les entrées sont automatiquement archivées
- L'admin peut purger les anciennes entrées manuellement

### Avertissement de Purge

```
┌─────────────────────────────────────────────────────────────────┐
│  ⚠️ PURGER LES ANCIENNES ENTRÉES                               │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Supprimer les entrées plus anciennes que:                     │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ 6 mois                                              ▼   │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Entrées qui seront supprimées: 1,234                          │
│                                                                 │
│  ⚠️ Cette action est irréversible.                             │
│  ℹ️ Recommandation: Exportez le journal avant de purger.       │
│                                                                 │
│              [Annuler]  [Purger]                                │
└─────────────────────────────────────────────────────────────────┘
```

---

## Vue Superviseur

Les superviseurs ne voient que leurs propres actions:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  MES ACTIONS RÉCENTES                                                       │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 10:32:15                                              │   │
│  │ ✅ SCORE SAISI                                                      │   │
│  │    Match #12 (Ronde 2, Terrain 1)                                   │   │
│  │    Score: 11-8 (Victoire Équipe A)                                  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 15 jan 2026 - 10:15:00                                              │   │
│  │ ✅ SCORE SAISI                                                      │   │
│  │    Match #8 (Ronde 1, Terrain 2)                                    │   │
│  │    Score: 11-5 (Victoire Équipe B)                                  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ℹ️ Seules vos propres actions sont affichées.                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

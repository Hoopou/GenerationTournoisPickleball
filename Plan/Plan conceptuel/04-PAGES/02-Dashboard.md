# Page: Dashboard

## Objectif
Vue d'ensemble du tournoi actif avec accès rapide aux actions principales et indicateurs clés.

---

## Accès
- **URL**: Page d'accueil après connexion
- **Condition d'accès**: Connecté
- **Rôles**: Administrateur, Superviseur

---

## Contenu de la Page

### Structure Générale

```
┌─────────────────────────────────────────────────────────────────┐
│ [En-tête avec sélection de tournoi]                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TOURNOI: Méli-Mélo Terrebonne 2026          [Statut: En cours] │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌────────┐  │
│  │  👥 45       │ │  🏷️ 6        │ │  🎯 120/180  │ │ 🏆 0/6 │  │
│  │  Joueurs    │ │  Catégories  │ │  Parties     │ │ Séries │  │
│  └──────────────┘ └──────────────┘ └──────────────┘ └────────┘  │
│                                                                 │
│  ┌─────────────────────────────────┐ ┌────────────────────────┐ │
│  │  PROCHAINES PARTIES             │ │  ACTIONS RAPIDES       │ │
│  │  ───────────────────────        │ │  ──────────────        │ │
│  │  09:15 - Terrain 1              │ │  [📝 Saisir scores]    │ │
│  │  Jean+Marie vs Pierre+Sophie    │ │  [👥 Gérer joueurs]    │ │
│  │  Catégorie: Homme 3.5           │ │  [📊 Voir classement]  │ │
│  │                                 │ │  [🖨️ Imprimer]        │ │
│  │  09:15 - Terrain 2              │ │                        │ │
│  │  Luc+Anne vs Marc+Julie         │ └────────────────────────┘ │
│  │  Catégorie: Femme 4.0           │                            │
│  │                                 │ ┌────────────────────────┐ │
│  │  [Voir toutes les parties →]    │ │  ALERTES               │ │
│  └─────────────────────────────────┘ │  ──────                 │ │
│                                      │  ⚠️ Catégorie "H-3.0"  │ │
│  ┌─────────────────────────────────┐ │  n'a que 6 joueurs     │ │
│  │  CLASSEMENT (Top 5 par cat.)    │ │                        │ │
│  │  ───────────────────────        │ │  ⚠️ 3 parties sans    │ │
│  │  [Sélecteur catégorie ▼]        │ │  score depuis 30min    │ │
│  │                                 │ └────────────────────────┘ │
│  │  1. Jean Tremblay    3V - D:2   │                            │
│  │  2. Pierre Gagnon    3V - D:5   │                            │
│  │  3. Marie Lavoie     2V - D:1   │                            │
│  │  4. ...                         │                            │
│  │                                 │                            │
│  │  [Voir classement complet →]    │                            │
│  └─────────────────────────────────┘                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Widgets du Dashboard

### 1. Cartes de Statistiques (En haut)

Quatre cartes affichant les métriques clés:

| Carte | Icône | Valeur | Clic → Destination |
|-------|-------|--------|-------------------|
| Joueurs | 👥 | Nombre de joueurs actifs | Page Liste Joueurs |
| Catégories | 🏷️ | Nombre de catégories | Page Catégories |
| Parties | 🎯 | Jouées / Total | Page Cédule Rondes |
| Séries | 🏆 | Matchs joués / Total | Page Bracket Séries |

**Comportement des cartes**:
- Survol: effet visuel (ombre, légère élévation)
- Clic: navigation vers la page détaillée
- Couleur: varie selon progression (vert si avancé, orange si en retard)

### 2. Widget "Prochaines Parties"

**Contenu**:
- Liste des 5 prochaines parties non jouées
- Pour chaque partie:
  - Heure prévue
  - Numéro/nom du terrain
  - Équipe A vs Équipe B (noms des 4 joueurs)
  - Nom de la catégorie
- Lien "Voir toutes les parties"

**Comportement**:
- Clic sur une partie → Ouvre la modale de saisie de score
- Lien "Voir toutes" → Page Cédule des Rondes

**Mise à jour**: Automatique toutes les 30 secondes ou après saisie de score

### 3. Widget "Actions Rapides"

**Boutons disponibles** (selon le statut du tournoi):

| Statut Tournoi | Actions affichées |
|----------------|-------------------|
| Brouillon | Paramètres, Gérer joueurs, Générer catégories |
| Joueurs inscrits | Gérer joueurs, Générer catégories, Vérifier catégories |
| Catégories générées | Générer rondes, Modifier catégories |
| Rondes générées | Saisir scores, Imprimer tableau |
| Rondes en cours | Saisir scores, Voir classement, Imprimer |
| Rondes terminées | Générer séries, Voir classement |
| Séries en cours | Saisir scores séries, Voir bracket |
| Terminé | Voir résultats, Imprimer résultats |

### 4. Widget "Classement" (Aperçu)

**Contenu**:
- Sélecteur de catégorie (dropdown)
- Top 5 joueurs de la catégorie sélectionnée
- Pour chaque joueur:
  - Rang
  - Nom complet
  - Nombre de victoires
  - Différentiel cumulé
- Lien "Voir classement complet"

**Comportement**:
- Changement de catégorie → Mise à jour du top 5
- Clic sur un joueur → Page détail joueur
- Lien "Voir complet" → Page Classement

### 5. Widget "Alertes" (Si applicable)

**Types d'alertes**:

| Situation | Message | Action proposée |
|-----------|---------|-----------------|
| Catégorie < 8 joueurs | "Catégorie X n'a que Y joueurs" | Lien vers Catégories |
| Parties en retard | "X parties sans score depuis Y min" | Lien vers Saisie Scores |
| Joueur sans catégorie | "X joueurs non catégorisés" | Lien vers Joueurs |
| Conflit d'horaire | "Joueur X a 2 parties à la même heure" | Lien vers Cédule |

**Comportement**:
- Clic sur une alerte → Navigation vers la page concernée
- Icône ⚠️ visible si alertes actives
- Disparaît quand le problème est résolu

---

## Sélection du Tournoi

### Si Plusieurs Tournois Existent

**En-tête affiche**:
- Nom du tournoi actuel
- Icône de changement (dropdown)

**Clic sur le sélecteur**:
- Liste déroulante avec tous les tournois
- Indication du statut de chaque tournoi
- Option "Créer nouveau tournoi" (admin seulement)

### Si Aucun Tournoi

Afficher:
```
┌─────────────────────────────────────────┐
│                                         │
│   Aucun tournoi configuré               │
│                                         │
│   [Créer mon premier tournoi]           │
│                                         │
└─────────────────────────────────────────┘
```

---

## Comportements par Rôle

### Administrateur
- Voit toutes les actions rapides
- Peut créer/supprimer des tournois
- Voit les alertes de configuration

### Superviseur
- Actions limitées (pas de génération, pas de suppression)
- Focus sur saisie de scores
- Voit les alertes de parties en attente

---

## Responsive

### Mobile
- Cartes de stats sur 2 colonnes (2x2)
- Widgets empilés verticalement
- Boutons actions rapides en pleine largeur
- Parties prochaines en format carte

### Tablette
- Cartes de stats sur une ligne
- Widgets sur 2 colonnes
- Actions rapides dans un panneau latéral

### Desktop
- Layout complet comme illustré
- Widgets côte à côte
- Plus d'informations visibles

---

## Rafraîchissement

- **Automatique**: Toutes les 30 secondes pour les parties et classement
- **Manuel**: Bouton de rafraîchissement dans l'en-tête
- **Événementiel**: Après chaque action (saisie score, modification)

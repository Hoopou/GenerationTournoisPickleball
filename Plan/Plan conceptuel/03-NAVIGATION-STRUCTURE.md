# Navigation et Structure des Pages

## Structure Globale de l'Interface

L'application est composée de:
- **En-tête fixe**: Logo, nom du tournoi actif, utilisateur connecté, déconnexion
- **Menu latéral**: Navigation principale (peut être réduit sur mobile)
- **Zone de contenu**: Page active
- **Pied de page** (optionnel): Version, date/heure

---

## Menu de Navigation Principal

### Organisation du Menu

```
📊 Dashboard
    
📋 Tournoi
   ├── Paramètres
   ├── Terrains
   └── Périodes de pause

👥 Joueurs
   ├── Liste des joueurs
   └── Import CSV

🏷️ Catégories

🎯 Rondes Préliminaires
   ├── Cédule
   ├── Saisie des scores
   └── Classement

🏆 Séries Éliminatoires
   ├── Bracket
   └── Saisie des scores

🖨️ Impression
   ├── Tableau des rondes
   ├── Bracket des séries
   └── Résultats finaux

⚙️ Administration (Admin seulement)
   ├── Utilisateurs
   └── Journal des modifications
```

---

## Flux de Navigation Typique

### Parcours de Création de Tournoi

```
[Dashboard] 
    → Clic "Nouveau tournoi"
    → [Page Création Tournoi]
    → Remplir le formulaire
    → Clic "Créer"
    → [Dashboard du nouveau tournoi]
```

### Parcours Avant le Tournoi

```
[Dashboard]
    → Clic "Gérer les joueurs"
    → [Liste Joueurs]
    → Clic "Importer CSV" ou ajout manuel
    → Retour [Dashboard]
    → Clic "Générer catégories"
    → [Page Catégories] - Vérification
    → Retour [Dashboard]
    → Clic "Générer rondes"
    → [Cédule Rondes] - Vérification
    → Clic "Imprimer"
    → [Page Impression] - PDF
```

### Parcours Pendant les Rondes

```
[Dashboard]
    → Clic "Saisir scores" (ou depuis menu)
    → [Page Saisie Scores]
    → Sélectionner la partie
    → Entrer les scores
    → Clic "Enregistrer"
    → Partie suivante ou
    → Clic "Voir classement"
    → [Page Classement]
```

### Parcours Transition vers Séries

```
[Classement]
    → Vérifier classement final
    → Clic "Générer les séries"
    → [Page Confirmation] - Liste des qualifiés
    → Clic "Confirmer"
    → [Page Bracket Séries]
```

### Parcours Pendant les Séries

```
[Bracket Séries]
    → Clic sur un match
    → Entrer le score
    → Le bracket se met à jour automatiquement
    → Continuer jusqu'à la finale
```

---

## Détail des Zones de l'Interface

### En-tête (Header)

| Élément | Position | Description |
|---------|----------|-------------|
| Logo | Gauche | Logo de l'application, clic = retour Dashboard |
| Nom du tournoi | Centre | Nom du tournoi actuellement sélectionné |
| Badge statut | Centre | Indicateur: "Brouillon", "En cours", "Terminé" |
| Nom utilisateur | Droite | Prénom + Nom de l'utilisateur connecté |
| Icône rôle | Droite | Icône indiquant Admin ou Superviseur |
| Bouton déconnexion | Droite | Icône de déconnexion |

### Menu Latéral

| Comportement | Description |
|--------------|-------------|
| Desktop | Menu toujours visible, largeur fixe |
| Tablette | Menu rétractable, icône hamburger |
| Mobile | Menu caché par défaut, overlay au clic |
| Section active | Mise en évidence visuelle |
| Sous-menus | Dépliables au clic |
| Compteurs | Badges sur certains items (ex: parties en attente) |

### Zone de Contenu

| Élément | Description |
|---------|-------------|
| Fil d'Ariane | Chemin de navigation (Dashboard > Joueurs > Jean Tremblay) |
| Titre de page | Titre principal avec actions contextuelles |
| Contenu | Zone scrollable, adaptatif |
| Actions flottantes | Boutons d'action rapide (mobile) |

---

## États de Navigation

### Indicateurs Visuels

L'application doit indiquer clairement:

1. **Où l'utilisateur se trouve**
   - Item de menu surligné
   - Fil d'Ariane visible

2. **Ce qui est possible**
   - Boutons actifs vs désactivés
   - Liens cliquables identifiables

3. **Ce qui s'est passé**
   - Messages de succès/erreur
   - Confirmations d'action

4. **Ce qui est en cours**
   - Indicateurs de chargement
   - Progress bars pour les opérations longues

### Gestion des Erreurs de Navigation

| Situation | Comportement |
|-----------|--------------|
| Page non trouvée | Afficher page 404 avec lien vers Dashboard |
| Accès non autorisé | Afficher message + redirection Dashboard |
| Session expirée | Redirection page connexion + message |
| Tournoi inexistant | Message + proposition de créer |

---

## Comportement Responsive

### Desktop (> 1024px)
- Menu latéral fixe visible
- Tableaux complets
- Actions en ligne

### Tablette (768px - 1024px)
- Menu rétractable
- Tableaux avec scroll horizontal si nécessaire
- Actions dans menu contextuel

### Mobile (< 768px)
- Menu hamburger
- Cartes au lieu de tableaux
- Actions en boutons flottants
- Navigation par swipe possible

---

## Navigation Contextuelle

### Liens Rapides depuis le Dashboard

| Widget | Destination au clic |
|--------|---------------------|
| Compteur joueurs | Page Liste Joueurs |
| Compteur parties | Page Saisie Scores |
| Classement résumé | Page Classement complète |
| Prochaines parties | Page Cédule filtrée |

### Actions Contextuelles

Sur chaque page, des actions pertinentes au contexte:

| Page | Actions disponibles |
|------|---------------------|
| Liste Joueurs | Ajouter, Importer, Filtrer, Exporter |
| Détail Joueur | Modifier, Supprimer, Changer catégorie, Voir parties |
| Cédule | Filtrer par catégorie, Filtrer par terrain, Imprimer |
| Partie | Saisir score, Voir détails, Annuler (admin) |
| Classement | Changer catégorie, Exporter, Actualiser |

---

## Modales et Dialogues

### Types de Modales

1. **Confirmation** — Demande de confirmation avant action destructive
   - "Êtes-vous sûr de vouloir supprimer ce joueur?"
   - Boutons: Annuler / Confirmer

2. **Formulaire rapide** — Saisie sans quitter la page
   - Saisie de score
   - Ajout rapide de joueur
   - Boutons: Annuler / Enregistrer

3. **Information** — Message important
   - "Le classement a été mis à jour"
   - Bouton: OK

4. **Sélection** — Choix parmi plusieurs options
   - Sélectionner une catégorie
   - Sélectionner un joueur substitut

### Comportement des Modales

- Fond assombri (overlay)
- Fermeture au clic sur l'overlay (sauf formulaires)
- Fermeture avec touche Échap
- Focus automatique sur le premier champ
- Validation avant fermeture si formulaire

---

## Raccourcis et Navigation Rapide

### Raccourcis Clavier (Desktop)

| Raccourci | Action |
|-----------|--------|
| Ctrl + H | Retour au Dashboard |
| Ctrl + J | Page Joueurs |
| Ctrl + S | Page Scores (si contexte pertinent) |
| Ctrl + P | Imprimer la page actuelle |
| Échap | Fermer modale / Annuler |

### Navigation par Recherche

- Barre de recherche globale dans l'en-tête
- Recherche de joueurs par nom
- Recherche de parties par numéro
- Résultats en dropdown avec accès direct

---

## Gestion du Tournoi Actif

### Sélection du Tournoi

- Si un seul tournoi existe: sélectionné automatiquement
- Si plusieurs tournois: liste de sélection au démarrage
- Le tournoi actif est affiché dans l'en-tête
- Possibilité de changer de tournoi depuis l'en-tête

### Persistance

- Le dernier tournoi consulté est mémorisé
- À la reconnexion, retour au même tournoi
- Si le tournoi n'existe plus: redirection vers liste

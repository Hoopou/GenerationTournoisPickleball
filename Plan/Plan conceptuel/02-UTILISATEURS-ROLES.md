# Utilisateurs et Rôles

## Vue d'Ensemble

L'application gère deux types d'utilisateurs avec des permissions différentes. Un utilisateur se connecte avec email et mot de passe.

---

## Rôle: Administrateur

### Description
L'administrateur a le contrôle total sur le tournoi. C'est généralement l'organisateur principal du tournoi.

### Permissions Complètes

| Action | Autorisé |
|--------|----------|
| Créer un tournoi | ✅ Oui |
| Modifier les paramètres globaux | ✅ Oui |
| Supprimer un tournoi | ✅ Oui |
| Ajouter/Modifier/Supprimer des joueurs | ✅ Oui |
| Importer des joueurs (CSV) | ✅ Oui |
| Changer la catégorie d'un joueur | ✅ Oui |
| Marquer un joueur comme substitut | ✅ Oui |
| Générer les catégories | ✅ Oui |
| Générer les rondes préliminaires | ✅ Oui |
| Régénérer la cédule | ✅ Oui |
| Saisir les scores | ✅ Oui |
| Corriger un score validé | ✅ Oui |
| Supprimer une partie | ✅ Oui |
| Générer les séries | ✅ Oui |
| Modifier l'ordre des joueurs en séries | ✅ Oui |
| Voir le journal des modifications | ✅ Oui |
| Gérer les autres utilisateurs | ✅ Oui |
| Imprimer/Exporter PDF | ✅ Oui |

### Cas d'Utilisation Typiques
- Créer et configurer un nouveau tournoi
- Ajuster une catégorie qui a trop peu de joueurs
- Corriger une erreur de score après validation
- Modifier le classement si contestation justifiée
- Régénérer la cédule après un changement majeur

---

## Rôle: Superviseur

### Description
Le superviseur aide à la gestion du tournoi le jour même. Il peut saisir les scores et gérer les joueurs, mais ne peut pas modifier les règles ou supprimer des données importantes.

### Permissions Limitées

| Action | Autorisé |
|--------|----------|
| Créer un tournoi | ❌ Non |
| Modifier les paramètres globaux | ❌ Non |
| Supprimer un tournoi | ❌ Non |
| Ajouter/Modifier des joueurs | ✅ Oui |
| Supprimer un joueur (sans parties) | ✅ Oui |
| Importer des joueurs (CSV) | ✅ Oui |
| Changer la catégorie d'un joueur | ❌ Non |
| Marquer un joueur comme substitut | ❌ Non |
| Générer les catégories | ❌ Non |
| Générer les rondes préliminaires | ❌ Non |
| Régénérer la cédule | ❌ Non |
| Saisir les scores | ✅ Oui |
| Corriger un score validé | ❌ Non (doit demander à l'admin) |
| Supprimer une partie | ❌ Non |
| Générer les séries | ❌ Non |
| Modifier l'ordre des joueurs en séries | ❌ Non |
| Voir le journal des modifications | ✅ Oui (lecture seule) |
| Gérer les autres utilisateurs | ❌ Non |
| Imprimer/Exporter PDF | ✅ Oui |

### Cas d'Utilisation Typiques
- Saisir les scores pendant le tournoi
- Ajouter un joueur de dernière minute
- Désactiver un joueur qui se blesse
- Consulter la cédule pour informer les joueurs

---

## Matrice des Permissions par Écran

| Page | Administrateur | Superviseur |
|------|----------------|-------------|
| Connexion | Accès | Accès |
| Dashboard | Accès complet | Lecture + actions limitées |
| Gestion Tournois | CRUD complet | Lecture seule |
| Paramètres Tournoi | Modification | Lecture seule |
| Liste Joueurs | CRUD complet | Ajouter/Modifier |
| Import CSV | Accès | Accès |
| Catégories | Générer + Modifier | Lecture seule |
| Rondes Préliminaires | Générer + Modifier | Lecture + Saisie scores |
| Saisie Scores | Tous scores | Scores non validés |
| Classement | Lecture + Ajustement | Lecture seule |
| Séries | Générer + Modifier | Lecture + Saisie scores |
| Impression PDF | Accès | Accès |
| Administration | Accès complet | ❌ Aucun accès |
| Journal Modifications | Accès complet | Lecture seule |

---

## Comportement de l'Interface selon le Rôle

### Éléments Cachés vs Désactivés

Pour les actions non autorisées, l'interface doit:
- **Cacher** les boutons d'action si le superviseur n'a jamais besoin de les voir
- **Désactiver (grisé)** les boutons si le superviseur doit savoir que l'action existe mais nécessite un admin

### Exemples

**Bouton "Supprimer tournoi"**: Caché pour superviseur
- Le superviseur n'a pas besoin de savoir que cette action existe

**Bouton "Régénérer cédule"**: Visible mais grisé pour superviseur
- Le superviseur peut voir que c'est possible et demander à l'admin de le faire

**Champ de score d'une partie validée**: Lecture seule pour superviseur
- Le superviseur voit le score mais ne peut pas le modifier
- Un indicateur visuel (cadenas) montre que c'est verrouillé

---

## Création des Utilisateurs

### Premier Administrateur
- Créé à l'installation de l'application
- Ou via une page d'inscription initiale si aucun utilisateur n'existe

### Ajout d'Utilisateurs
- Seul l'administrateur peut créer de nouveaux comptes
- L'admin choisit le rôle lors de la création
- L'admin peut changer le rôle d'un utilisateur existant

### Informations Utilisateur
- Email (identifiant de connexion)
- Mot de passe (avec règles de sécurité minimales)
- Prénom et Nom (pour affichage)
- Rôle (Administrateur ou Superviseur)
- Statut (Actif ou Inactif)

---

## Scénarios Multi-Utilisateurs

### Tournoi avec 1 Admin + 3 Superviseurs

**Configuration typique**:
- 1 Administrateur: Gère les problèmes, prend les décisions
- 3 Superviseurs: Chacun responsable de quelques terrains pour saisir les scores

**Flux de travail**:
1. Les parties se terminent
2. Le superviseur du terrain saisit le score
3. Si erreur détectée après validation → appeler l'admin
4. L'admin corrige si nécessaire

### Gestion des Conflits

Si deux personnes modifient la même donnée:
- Le dernier à enregistrer "gagne"
- Un message informe l'autre que les données ont changé
- Le journal des modifications permet de voir qui a fait quoi

---

## Session et Déconnexion

### Durée de Session
- Session active pendant 8 heures (durée d'un tournoi)
- Pas de déconnexion automatique pendant cette période
- Option "Se souvenir de moi" pour connexion persistante

### Déconnexion
- Bouton de déconnexion toujours visible dans l'en-tête
- Déconnexion redirige vers la page de connexion
- Les données non sauvegardées sont perdues (avec avertissement)

### Sécurité
- Mot de passe minimum 8 caractères
- Après 5 tentatives échouées: compte bloqué 15 minutes
- L'admin peut débloquer un compte manuellement

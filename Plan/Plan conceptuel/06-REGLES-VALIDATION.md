# Règles de Validation

## Objectif
Centraliser toutes les règles métier et validations de l'application pour assurer la cohérence des données et le bon déroulement du tournoi.

---

## 1. Validation des Joueurs

### Champs Obligatoires

| Champ | Règle | Message d'erreur |
|-------|-------|------------------|
| Nom | 2-100 caractères | "Le nom doit contenir entre 2 et 100 caractères." |
| Prénom | 2-100 caractères | "Le prénom doit contenir entre 2 et 100 caractères." |
| Sexe | Homme ou Femme | "Veuillez sélectionner un sexe." |
| Âge | Entier entre 5 et 100 | "L'âge doit être entre 5 et 100 ans." |
| Niveau | Valeur de la liste | "Veuillez sélectionner un niveau valide." |

### Validation de Doublon

```
Règle: Pas deux joueurs avec le même nom ET prénom dans un tournoi
Vérification: Insensible à la casse
Message: "Un joueur nommé [Prénom Nom] existe déjà dans ce tournoi."
```

### Import CSV

| Validation | Règle | Message |
|------------|-------|---------|
| Format | .csv avec séparateur ; ou , | "Le fichier doit être au format CSV." |
| En-têtes | Colonnes obligatoires présentes | "Colonnes manquantes: [liste]" |
| Sexe | H, F, Homme, Femme | "Ligne X: Sexe invalide '[valeur]'" |
| Âge | Nombre entier | "Ligne X: Âge invalide '[valeur]'" |
| Niveau | Valeur connue | "Ligne X: Niveau inconnu '[valeur]'" |

---

## 2. Validation des Catégories

### Tranches d'Âge

| Règle | Message |
|-------|---------|
| Minimum 1 tranche | "Au moins une tranche d'âge est requise." |
| Pas de chevauchement | "Les tranches d'âge [X-Y] et [Y-Z] se chevauchent." |
| Couverture complète | "L'âge [X] n'est couvert par aucune tranche." |
| Âge min < Âge max | "La tranche [X-Y] a un minimum supérieur au maximum." |

### Catégories Générées

| Règle | Avertissement |
|-------|---------------|
| Moins de 4 joueurs | "⚠️ Catégorie [Nom]: seulement [X] joueurs. Fusionner recommandé." |
| Nombre impair | "⚠️ Catégorie [Nom]: [X] joueurs (impair). Un joueur sera en repos." |
| Joueurs non assignés | "❌ [X] joueurs n'ont pas de catégorie. Données incomplètes." |

### Fusion de Catégories

| Règle | Message |
|-------|---------|
| Même sexe obligatoire | "Impossible de fusionner: les catégories n'ont pas le même sexe." |
| Au moins 1 joueur chacune | "Impossible de fusionner une catégorie vide." |

---

## 3. Validation des Scores

### Score de Match

| Règle | Condition | Message |
|-------|-----------|---------|
| Score minimum gagnant | >= 11 | "Le score gagnant doit être d'au moins 11 points." |
| Écart minimum | >= 2 | "L'écart doit être d'au moins 2 points (ex: 11-9, pas 11-10)." |
| Pas d'égalité | Score A ≠ Score B | "Les scores ne peuvent pas être égaux." |
| Score non négatif | >= 0 | "Le score ne peut pas être négatif." |
| Score raisonnable | <= 99 | "Le score semble anormalement élevé." |

### Exemples de Validation

| Score | Valide? | Raison |
|-------|---------|--------|
| 11-8 | ✅ | Correct |
| 11-9 | ✅ | Correct (écart = 2) |
| 11-10 | ❌ | Écart insuffisant |
| 15-13 | ✅ | Prolongation valide |
| 10-8 | ❌ | Gagnant < 11 |
| 11-11 | ❌ | Égalité impossible |
| -1-5 | ❌ | Score négatif |

### Modification de Score

| Règle | Message |
|-------|---------|
| Raison obligatoire | "Veuillez indiquer la raison de la modification." |
| Score différent | "Le nouveau score est identique à l'ancien." |

---

## 4. Validation de la Cédule

### Génération

| Règle | Message |
|-------|---------|
| Minimum 4 joueurs | "Il faut au moins 4 joueurs pour générer une cédule." |
| Terrains disponibles | "Au moins 1 terrain doit être configuré." |
| Rondes > 0 | "Le nombre de rondes doit être supérieur à 0." |
| Rondes <= maximum | "Maximum [X] rondes possibles avec [Y] joueurs." |

### Contraintes de Jumelage

| Contrainte | Message si Violation |
|------------|----------------------|
| Partenaire unique | "Impossible: [A] et [B] ont déjà été partenaires (Ronde X)." |
| Joueur dispo | "Le joueur [A] a déjà un match assigné à cette heure." |

### Régénération

| Règle | Message |
|-------|---------|
| Scores existants | "⚠️ [X] scores seront perdus. Confirmer?" |
| Séries en cours | "Impossible: les séries éliminatoires ont déjà commencé." |

---

## 5. Validation des Séries Éliminatoires

### Prérequis

| Règle | Message |
|-------|---------|
| Rondes terminées | "Terminez toutes les rondes préliminaires avant de générer les séries." |
| Assez de joueurs | "Minimum 4 joueurs qualifiés pour les séries." |
| Nombre pair | "Le nombre de qualifiés doit être pair. Actuellement: [X]." |

### Formation d'Équipes

| Règle | Message |
|-------|---------|
| 1 équipe par joueur | "Le joueur [A] est déjà dans l'équipe [X]." |
| 2 joueurs par équipe | "Chaque équipe doit avoir exactement 2 joueurs." |
| Qualifiés seulement | "Le joueur [A] n'est pas qualifié pour les séries." |

### Progression du Bracket

| Règle | Message |
|-------|---------|
| Match précédent terminé | "Le match [X] ne peut pas commencer: [match précédent] non terminé." |
| Gagnant déterminé | "Un gagnant est requis pour progresser." |

---

## 6. Validation des Utilisateurs

### Création de Compte

| Champ | Règle | Message |
|-------|-------|---------|
| Email | Format valide | "L'adresse courriel n'est pas valide." |
| Email | Unique | "Cette adresse courriel est déjà utilisée." |
| Mot de passe | Min 8 caractères | "Le mot de passe doit contenir au moins 8 caractères." |
| Mot de passe | 1 majuscule | "Le mot de passe doit contenir au moins une majuscule." |
| Mot de passe | 1 minuscule | "Le mot de passe doit contenir au moins une minuscule." |
| Mot de passe | 1 chiffre | "Le mot de passe doit contenir au moins un chiffre." |
| Nom | Non vide | "Le nom est obligatoire." |

### Connexion

| Règle | Message |
|-------|---------|
| Email requis | "Veuillez entrer votre adresse courriel." |
| Mot de passe requis | "Veuillez entrer votre mot de passe." |
| Identifiants valides | "Courriel ou mot de passe incorrect." |
| Compte actif | "Ce compte a été désactivé. Contactez un administrateur." |

### Sécurité

| Règle | Comportement |
|-------|--------------|
| 5 tentatives échouées | Bloquer 15 minutes |
| Session expirée | Rediriger vers connexion |
| Token invalide | "Session expirée. Veuillez vous reconnecter." |

---

## 7. Validation des Tournois

### Création

| Champ | Règle | Message |
|-------|-------|---------|
| Nom | 3-100 caractères | "Le nom du tournoi doit contenir entre 3 et 100 caractères." |
| Date | Format valide | "La date n'est pas valide." |
| Date | Future ou aujourd'hui | "La date du tournoi doit être aujourd'hui ou dans le futur." |
| Heure début | Format valide | "L'heure de début n'est pas valide." |

### Terrains

| Règle | Message |
|-------|---------|
| Au moins 1 terrain | "Au moins un terrain est requis." |
| Nom unique | "Le nom de terrain '[X]' est déjà utilisé." |
| Capacité > 0 | "La capacité doit être supérieure à 0." |

### Pauses

| Règle | Message |
|-------|---------|
| Durée > 0 | "La durée de la pause doit être supérieure à 0." |
| Heure cohérente | "L'heure de pause doit être après le début du tournoi." |
| Pas de chevauchement | "Les pauses ne peuvent pas se chevaucher." |

---

## 8. Validation des Suppressions

### Avec Confirmation

| Élément | Condition | Message de confirmation |
|---------|-----------|------------------------|
| Joueur | A des matchs | "Ce joueur a [X] matchs. Voulez-vous vraiment le supprimer?" |
| Catégorie | A des joueurs | "Cette catégorie contient [X] joueurs. Ils seront non-assignés." |
| Tournoi | A des données | "Ce tournoi contient des données. Suppression irréversible?" |
| Utilisateur | Pas soi-même | "Voulez-vous vraiment supprimer cet utilisateur?" |

### Interdictions

| Élément | Condition | Message |
|---------|-----------|---------|
| Joueur | Parties jouées | "Impossible: ce joueur a des parties avec scores." |
| Utilisateur | Soi-même | "Vous ne pouvez pas supprimer votre propre compte." |
| Catégorie | Cédule générée | "Impossible: une cédule existe pour cette catégorie." |

---

## 9. Validations en Temps Réel

### Formulaires

- Validation au fur et à mesure de la saisie (après perte de focus)
- Indicateur visuel immédiat (bordure rouge, icône ❌)
- Message d'erreur sous le champ
- Bouton de soumission désactivé si erreurs

### Grilles de Saisie Rapide

- Validation à chaque cellule
- Surbrillance des cellules invalides
- Tooltip avec le message d'erreur

---

## 10. Messages d'Erreur Standards

### Format des Messages

- **Clairs**: Expliquer le problème simplement
- **Actionnables**: Indiquer comment corriger
- **Polis**: Pas de ton accusateur

### Exemples

❌ Mauvais: "Erreur 400: Bad Request"
✅ Bon: "L'âge doit être un nombre entre 5 et 100."

❌ Mauvais: "Données invalides"
✅ Bon: "Le prénom est obligatoire."

❌ Mauvais: "Impossible"
✅ Bon: "Le score gagnant doit être d'au moins 11 points."

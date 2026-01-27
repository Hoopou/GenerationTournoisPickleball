# Instructions pour l'IA — Plan de Développement

**Lire ce fichier EN PREMIER avant tout travail.**

---

## Objectif de ce Plan

Ce dossier contient le plan de développement **conceptuel** complet pour l'application de gestion de tournoi Pickleball Méli-Mélo. Ce plan décrit:

- Les pages et écrans de l'application
- Les interactions utilisateur
- Les flux de navigation
- La logique métier et les algorithmes
- Les règles de validation
- Les comportements attendus

Ce plan **ne contient PAS** de code, de structures de fichiers, ou de choix technologiques. L'IA qui implémentera le projet devra faire ces choix techniques en fonction de ce plan conceptuel.

---

## Structure du Plan

```
00-INSTRUCTIONS-IA.md      ← Ce fichier (lire en premier)
01-RESUME-APPLICATION.md   ← Vue d'ensemble et objectifs
02-UTILISATEURS-ROLES.md   ← Rôles et permissions
03-NAVIGATION-STRUCTURE.md ← Structure des pages et menus
04-PAGES/                  ← Détail de chaque page
   01-Connexion.md
   02-Dashboard.md
   03-Tournois.md
   04-Joueurs.md
   05-Categories.md
   06-Rondes-Preliminaires.md
   07-Saisie-Scores.md
   08-Classement.md
   09-Series.md
   10-Impression-PDF.md
   11-Administration.md
   12-Journal-Modifications.md
05-ALGORITHMES/            ← Logique métier détaillée
   01-Categorisation.md
   02-Jumelage-Rondes.md
   03-Generation-Cedule.md
   04-Calcul-Classement.md
   05-Formation-Equipes-Series.md
   06-Bracket-Eliminatoire.md
06-REGLES-VALIDATION.md    ← Toutes les règles métier
07-PROGRESSION.md          ← État d'avancement pour passation IA
```

---

## Comment Utiliser ce Plan

### Pour l'IA qui Implémente

1. **Lire** `01-RESUME-APPLICATION.md` pour comprendre le contexte
2. **Lire** `02-UTILISATEURS-ROLES.md` pour comprendre les permissions
3. **Lire** `03-NAVIGATION-STRUCTURE.md` pour la structure globale
4. **Consulter** chaque fichier dans `04-PAGES/` lors de l'implémentation de chaque écran
5. **Consulter** les fichiers `05-ALGORITHMES/` pour la logique métier
6. **Valider** avec `06-REGLES-VALIDATION.md` que toutes les règles sont respectées
7. **Mettre à jour** `07-PROGRESSION.md` après chaque étape

### Délégation Obligatoire

Chaque section majeure (groupe de pages ou algorithme) doit être déléguée à un sous-agent:

```
runSubagent("Implémenter [section] selon le plan dans Idea Plan/[fichier]. Retourner: éléments créés, tests effectués, problèmes rencontrés.")
```

### Passation entre Sessions IA

Le fichier `07-PROGRESSION.md` sert de point de reprise. Il contient:
- L'état actuel de chaque section
- Les décisions prises
- Les problèmes en cours
- La prochaine étape à effectuer

---

## Principes de Conception

### Simplicité d'Utilisation
- L'application sera utilisée pendant un tournoi en temps réel
- Les actions fréquentes (saisie de score) doivent être rapides
- Interface claire même sous pression

### Fiabilité
- Aucune donnée ne doit être perdue
- Possibilité d'annuler/corriger les erreurs
- Journalisation de toutes les modifications

### Flexibilité
- L'administrateur peut ajuster pendant le tournoi
- Gestion des imprévus (joueur absent, erreur de score)
- Possibilité de regénérer les cédules si nécessaire

---

## Règles pour l'IA

1. **Ne pas improviser** — Suivre le plan tel que décrit
2. **Poser des questions** — Si un cas n'est pas couvert, demander clarification
3. **Tester chaque partie** — Valider avant de passer à la suite
4. **Documenter les décisions** — Noter dans PROGRESSION.md les choix faits
5. **Respecter les rôles** — Vérifier les permissions pour chaque action

# Algorithme: Catégorisation des Joueurs

## Objectif
Assigner automatiquement chaque joueur à une catégorie basée sur ses caractéristiques (sexe, âge, niveau).

---

## Entrées Requises

1. **Liste des joueurs** avec pour chacun:
   - Sexe (Homme/Femme)
   - Âge (en années)
   - Niveau (DUPR 3.0-5.0 ou Novice/Intermédiaire/Avancé)

2. **Configuration des tranches d'âge**:
   - Liste ordonnée des tranches (ex: 0-20, 20-35, 35-50, 50+)
   - Chaque tranche définie par un âge minimum et maximum

3. **Configuration du système de niveau**:
   - DUPR (valeurs numériques)
   - OU Textuel (Novice, Intermédiaire, Avancé)

---

## Sortie

Pour chaque joueur:
- Catégorie assignée (ou "Non-assigné" si données incomplètes)
- Nom de la catégorie au format: `[Sexe] - [Tranche âge] - [Niveau]`

Liste des catégories créées avec leur nombre de joueurs.

---

## Logique de l'Algorithme

### Étape 1: Validation des Données du Joueur

Pour chaque joueur, vérifier:
- Le sexe est renseigné (Homme ou Femme)
- L'âge est un nombre valide (entre 5 et 100)
- Le niveau est renseigné et valide

Si une donnée manque ou est invalide → Joueur marqué "Non-assigné" avec la raison.

### Étape 2: Détermination de la Tranche d'Âge

Parcourir les tranches d'âge configurées:
- Si l'âge du joueur est >= minimum ET < maximum de la tranche → Tranche trouvée
- Cas spécial: La dernière tranche (ex: 50+) n'a pas de maximum strict

**Exemple:**
- Tranches: [0-20], [20-35], [35-50], [50-99]
- Joueur de 38 ans → Tranche "35-50"
- Joueur de 52 ans → Tranche "50+"

### Étape 3: Construction du Nom de Catégorie

Combiner les trois critères:
```
Nom = [Sexe] + " - " + [Tranche] + " - " + [Niveau]
```

**Exemples:**
- Homme, 38 ans, 3.5 → "Homme - 35-50 - 3.5"
- Femme, 28 ans, Intermédiaire → "Femme - 20-35 - Intermédiaire"

### Étape 4: Création ou Association à la Catégorie

- Si la catégorie existe déjà → Ajouter le joueur à cette catégorie
- Si la catégorie n'existe pas → Créer la catégorie puis ajouter le joueur

### Étape 5: Rapport de Catégorisation

Produire un résumé:
- Nombre total de joueurs traités
- Nombre de catégories créées
- Liste des catégories avec leur nombre de joueurs
- Liste des joueurs non-assignés avec les raisons

---

## Cas Spéciaux

### Joueur à la Limite d'une Tranche

Un joueur dont l'âge est exactement à la limite:
- **Règle**: L'âge minimum est INCLUSIF, l'âge maximum est EXCLUSIF
- Joueur de 35 ans avec tranches [20-35] et [35-50] → Va dans "35-50"

### Données Manquantes

| Donnée manquante | Comportement |
|------------------|--------------|
| Sexe | Non-assigné - "Sexe non renseigné" |
| Âge | Non-assigné - "Âge non renseigné" |
| Niveau | Non-assigné - "Niveau non renseigné" |
| Âge hors limites | Non-assigné - "Âge invalide: X" |

### Régénération

Si l'algorithme est relancé (régénération):
1. Supprimer toutes les catégories existantes
2. Recréer les catégories depuis zéro
3. Réassigner tous les joueurs
4. Les assignations manuelles précédentes sont perdues

---

## Optimisations

### Performance

- Créer un dictionnaire des catégories par nom pour éviter les recherches répétées
- Traiter les joueurs en lot plutôt qu'un par un

### Pré-validation

Avant de lancer l'algorithme, vérifier:
- Au moins 1 joueur actif existe
- Les tranches d'âge sont configurées et cohérentes
- Le système de niveau est défini

---

## Alertes Post-Catégorisation

Après l'exécution, signaler:

| Situation | Alerte |
|-----------|--------|
| Catégorie avec moins de 4 joueurs | ⚠️ "Catégorie X: seulement Y joueurs" |
| Catégorie avec nombre impair | ⚠️ "Catégorie X: nombre impair (Y joueurs)" |
| Joueurs non-assignés | ❌ "X joueurs non catégorisés" |
| Catégorie vide créée | Impossible (catégorie créée seulement si un joueur y va) |

---

## Diagramme de Flux

```
┌─────────────────────────────┐
│ Début: Liste de joueurs    │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│ Pour chaque joueur:        │
└─────────────┬───────────────┘
              ▼
      ┌───────────────┐
      │ Données       │──NON──► "Non-assigné"
      │ complètes?    │         + raison
      └───────┬───────┘
              │ OUI
              ▼
┌─────────────────────────────┐
│ Déterminer tranche d'âge   │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│ Construire nom catégorie   │
│ [Sexe]-[Tranche]-[Niveau]  │
└─────────────┬───────────────┘
              ▼
      ┌───────────────┐
      │ Catégorie     │──NON──► Créer catégorie
      │ existe?       │
      └───────┬───────┘
              │ OUI
              ▼
┌─────────────────────────────┐
│ Ajouter joueur à catégorie │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│ Joueur suivant...          │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│ Fin: Rapport généré        │
└─────────────────────────────┘
```

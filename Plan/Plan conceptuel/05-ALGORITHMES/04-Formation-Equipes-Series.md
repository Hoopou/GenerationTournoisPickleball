# Algorithme: Formation des Équipes pour les Séries

## Objectif
Former des équipes fixes et équilibrées pour les séries éliminatoires, en jumelant les joueurs les mieux classés avec ceux moins bien classés.

---

## Entrées Requises

1. **Classement final** des rondes préliminaires
2. **Nombre de joueurs qualifiés** (configurable, défaut: 8 ou tous si moins)
3. **Mode de formation** (automatique ou manuel)

---

## Sortie

Liste des équipes formées avec:
- Numéro d'équipe
- Joueur 1 (mieux classé)
- Joueur 2 (moins bien classé)
- Nom d'équipe (optionnel)

---

## Principe Fondamental

> **Équilibrer les forces** en associant un joueur du haut du classement avec un joueur du bas.

Cela évite d'avoir une équipe avec les 2 meilleurs joueurs qui dominerait le bracket.

---

## Formule de Jumelage

### Pour N Joueurs Qualifiés

L'équipe formée associe:
- Joueur classé **rang R** avec Joueur classé **rang (N - R + 1)**

### Exemples

**8 joueurs qualifiés:**
| Équipe | Joueur 1 (rang) | Joueur 2 (rang) |
|--------|-----------------|-----------------|
| A | #1 | #8 |
| B | #2 | #7 |
| C | #3 | #6 |
| D | #4 | #5 |

**6 joueurs qualifiés:**
| Équipe | Joueur 1 (rang) | Joueur 2 (rang) |
|--------|-----------------|-----------------|
| A | #1 | #6 |
| B | #2 | #5 |
| C | #3 | #4 |

**4 joueurs qualifiés:**
| Équipe | Joueur 1 (rang) | Joueur 2 (rang) |
|--------|-----------------|-----------------|
| A | #1 | #4 |
| B | #2 | #3 |

---

## Logique de l'Algorithme

### Étape 1: Déterminer les Qualifiés

```
Si nombre_joueurs_catégorie <= joueurs_qualifiés_config:
    qualifiés = tous les joueurs
Sinon:
    qualifiés = les N premiers du classement

N = nombre_qualifiés (doit être pair)
```

### Étape 2: Vérifier la Parité

```
Si N est impair:
    Option A: Exclure le dernier (N = N - 1)
    Option B: Demander à l'admin de choisir qui exclure
```

### Étape 3: Former les Équipes

```
nombre_equipes = N / 2

Pour i de 1 à nombre_equipes:
    joueur_haut = classement[i]           // rang i
    joueur_bas = classement[N - i + 1]    // rang N-i+1
    
    equipe[i] = {joueur_haut, joueur_bas}
```

### Étape 4: Nommer les Équipes

Par défaut:
- Équipe 1, Équipe 2, Équipe 3, Équipe 4...

Optionnel:
- Permettre des noms personnalisés ("Les Champions", etc.)

---

## Cas Spéciaux

### Nombre Impair de Qualifiés

Si le nombre de joueurs qualifiés est impair:

**Option 1: Exclure le Dernier**
- Le joueur de rang N (le moins bien classé des qualifiés) ne participe pas aux séries
- Notification: "9 joueurs qualifiés - 1 exclu (nombre impair)"

**Option 2: Bye pour une Équipe**
- Une équipe est formée avec un seul joueur
- Cette équipe a un "bye" au premier tour
- Non recommandé car déséquilibré

### Ex-Æquo au Classement

Si deux joueurs sont ex-æquo à la limite de qualification:

```
Situation: 8 places, joueurs 7 et 8 ex-æquo au rang 7

Options:
- Qualifier les deux (total 9 → revient au cas impair)
- Départager par un critère supplémentaire (confrontation directe?)
- Demander à l'admin de choisir
```

### Pas Assez de Joueurs

```
Si N < 4:
    Erreur: "Minimum 4 joueurs pour les séries"
    
Si N = 4:
    Seulement 2 équipes → Finale directe (pas de demi)
```

---

## Validation des Équipes

### Vérifications Automatiques

1. Chaque joueur n'apparaît que dans une seule équipe
2. Toutes les équipes ont exactement 2 joueurs
3. Les rangs sont corrects (pas de #1 avec #2)

### Modifications Manuelles

L'admin peut modifier les équipes avant de générer le bracket:
- Échanger des joueurs entre équipes
- Avertissement si l'échange déséquilibre les forces

---

## Diagramme de Flux

```
┌─────────────────────────────────┐
│ Entrée: Classement final       │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Déterminer N qualifiés         │
│ (config ou tous si moins)      │
└─────────────┬───────────────────┘
              ▼
      ┌───────────────┐
      │ N est pair?   │───NON──► Exclure dernier
      └───────┬───────┘          ou demander
              │ OUI
              ▼
┌─────────────────────────────────┐
│ Nombre d'équipes = N / 2       │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour i = 1 à N/2:              │
│   Équipe[i] = rang[i] + rang[N-i+1]│
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Afficher proposition           │
│ à l'admin                      │
└─────────────┬───────────────────┘
              ▼
      ┌───────────────┐
      │ Modifications?│───OUI──► Appliquer
      └───────┬───────┘          modifications
              │ NON
              ▼
┌─────────────────────────────────┐
│ Sortie: Équipes formées        │
└─────────────────────────────────┘
```

---

## Exemple Complet

**Classement final - 10 joueurs, 8 qualifiés:**

| Rang | Joueur |
|------|--------|
| 1 | Tremblay |
| 2 | Lavoie |
| 3 | Martin |
| 4 | Roy |
| 5 | Gagnon |
| 6 | Dubois |
| 7 | Morin |
| 8 | Côté |
| 9 | Pelletier | ← Non qualifié
| 10 | Fortin | ← Non qualifié

**Équipes formées:**

| Équipe | Joueurs | Somme rangs |
|--------|---------|-------------|
| Équipe 1 | Tremblay (#1) + Côté (#8) | 9 |
| Équipe 2 | Lavoie (#2) + Morin (#7) | 9 |
| Équipe 3 | Martin (#3) + Dubois (#6) | 9 |
| Équipe 4 | Roy (#4) + Gagnon (#5) | 9 |

→ Toutes les équipes ont la même "force théorique" (somme des rangs = 9)

---

## Affichage à l'Utilisateur

### Avant Confirmation

```
FORMATION DES ÉQUIPES PROPOSÉE
──────────────────────────────

Équipe 1: Tremblay (1er) + Côté (8e)
Équipe 2: Lavoie (2e) + Morin (7e)
Équipe 3: Martin (3e) + Dubois (6e)
Équipe 4: Roy (4e) + Gagnon (5e)

Joueurs non qualifiés: Pelletier (9e), Fortin (10e)

[Modifier les équipes] [Confirmer et générer le bracket]
```

### Après Modification (si échange)

```
⚠️ Modification détectée

Équipe 1: Tremblay (1er) + Morin (7e)  ← Modifié
Équipe 2: Lavoie (2e) + Côté (8e)      ← Modifié

Note: L'équilibre des équipes a été modifié.
Somme rangs Équipe 1: 8 (était 9)
Somme rangs Équipe 2: 10 (était 9)

[Annuler les modifications] [Confirmer quand même]
```

---

## Transition vers le Bracket

Une fois les équipes confirmées:
1. Les équipes sont verrouillées
2. L'algorithme de génération du bracket peut commencer
3. Les équipes ne peuvent plus être modifiées sans régénérer tout

→ Voir [04-Bracket-Eliminatoire.md]

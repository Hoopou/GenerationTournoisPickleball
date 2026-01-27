# Algorithme: Génération des Horaires

## Objectif
Créer un horaire cohérent pour tous les matchs du tournoi en tenant compte des terrains disponibles, des pauses, et de la durée estimée des matchs.

---

## Entrées Requises

1. **Cédule des matchs** (générée par l'algorithme de jumelage)
2. **Nombre de terrains** disponibles
3. **Heure de début** du tournoi
4. **Durée estimée par match** (en minutes)
5. **Pauses planifiées** (heure début, durée)
6. **Catégories multiples?** (si oui, leur gestion)

---

## Sortie

Pour chaque match:
- Heure de début prévue
- Terrain assigné
- Numéro de ronde

Pour chaque pause:
- Position dans la cédule

---

## Principe de Base

### Vagues de Matchs

Une "vague" = ensemble de matchs qui peuvent se jouer simultanément.

```
Nombre de matchs par vague = Nombre de terrains disponibles
```

Si 3 terrains et 6 matchs par ronde:
- Vague 1: Matchs 1, 2, 3 (terrains 1, 2, 3)
- Vague 2: Matchs 4, 5, 6 (terrains 1, 2, 3)

### Calcul de l'Heure

```
heure_match = heure_debut + (numero_vague - 1) × duree_match
```

---

## Logique de l'Algorithme

### Étape 1: Initialisation

```
heure_courante = heure_debut
terrain_index = 0
vague_courante = 1
```

### Étape 2: Pour Chaque Ronde

```
Pour chaque ronde R:
    
    matchs_ronde = liste des matchs de cette ronde
    
    Pour chaque match M dans matchs_ronde:
        
        // Vérifier si on doit insérer une pause
        Si pause_planifiee_à(heure_courante):
            Insérer pause
            heure_courante += duree_pause
        
        // Assigner terrain
        M.terrain = (terrain_index % nombre_terrains) + 1
        terrain_index += 1
        
        // Assigner heure
        M.heure = heure_courante
        
        // Si tous les terrains utilisés, passer à la vague suivante
        Si terrain_index % nombre_terrains == 0:
            heure_courante += duree_match
            vague_courante += 1
```

### Étape 3: Gérer les Pauses

```
Pour chaque pause P configurée:
    Si P.type == "après_ronde_X":
        Insérer P après la ronde X
    Si P.type == "à_heure_fixe":
        Insérer P à l'heure spécifiée
```

---

## Gestion des Pauses

### Types de Pauses

| Type | Description |
|------|-------------|
| Après ronde X | Pause après une ronde spécifique |
| À heure fixe | Pause à une heure précise (ex: 10:30) |
| Intervalle | Pause toutes les X rondes |

### Insertion d'une Pause

```
Si pause après ronde R:
    Dernier match de R se termine à: heure_fin_R
    Premier match de R+1 commence à: heure_fin_R + duree_pause
```

### Exemple

```
Ronde 1: 09:00 - 09:15
Ronde 2: 09:15 - 09:30
--- PAUSE 15 min ---
Ronde 3: 09:45 - 10:00
Ronde 4: 10:00 - 10:15
```

---

## Gestion Multi-Catégories

### Scénario

Plusieurs catégories jouent en même temps (terrains partagés).

### Stratégies

**Stratégie A: Terrains Dédiés**
- Catégorie 1: Terrains 1, 2
- Catégorie 2: Terrains 3, 4

Chaque catégorie a sa propre cédule indépendante.

**Stratégie B: Rotation**
- Toutes les catégories partagent tous les terrains
- Les rondes alternent entre catégories

**Stratégie C: Séquentiel**
- Catégorie 1 joue toutes ses rondes d'abord
- Puis Catégorie 2

### Exemple Stratégie A (Terrains Dédiés)

```
09:00:
  Terrain 1: Cat A - Ronde 1 Match 1
  Terrain 2: Cat A - Ronde 1 Match 2
  Terrain 3: Cat B - Ronde 1 Match 1
  Terrain 4: Cat B - Ronde 1 Match 2

09:15:
  Terrain 1: Cat A - Ronde 2 Match 1
  ...
```

---

## Validation des Horaires

### Vérifications

1. **Pas de conflit de terrain**
   - Un terrain ne peut avoir qu'un match à la fois
   
2. **Joueur ne joue pas deux matchs simultanément**
   - Important en multi-catégories ou si un joueur est dans plusieurs

3. **Pauses respectées**
   - Aucun match pendant une pause

4. **Heure de fin raisonnable**
   - Vérifier que le tournoi ne finit pas trop tard

### Messages de Validation

| Problème | Message |
|----------|---------|
| Conflit terrain | "Terrain X a 2 matchs à 09:15" |
| Joueur occupé | "Joueur Y a 2 matchs à 09:15" |
| Dépassement horaire | "Le tournoi finirait à 18:30 (après limite)" |

---

## Diagramme de Flux

```
┌─────────────────────────────────┐
│ Entrée: Matchs, Terrains, Cfg  │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Initialiser:                   │
│ heure = debut, terrain = 1     │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour chaque ronde:             │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Pour chaque match:             │
└─────────────┬───────────────────┘
              ▼
      ┌───────────────┐
      │ Pause prévue? │───OUI──► Insérer pause
      └───────┬───────┘          heure += pause
              │ NON
              ▼
┌─────────────────────────────────┐
│ Assigner terrain               │
│ match.terrain = terrain_index  │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Assigner heure                 │
│ match.heure = heure_courante   │
└─────────────┬───────────────────┘
              ▼
      ┌───────────────┐
      │ Terrains tous │───OUI──► heure += duree_match
      │ utilisés?     │
      └───────┬───────┘
              │ NON
              ▼
┌─────────────────────────────────┐
│ Match suivant...               │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Valider (pas de conflits)      │
└─────────────┬───────────────────┘
              ▼
┌─────────────────────────────────┐
│ Sortie: Cédule avec horaires   │
└─────────────────────────────────┘
```

---

## Exemple Complet

### Configuration

- Heure début: 09:00
- 3 terrains
- 15 minutes par match
- 12 joueurs (6 matchs par ronde)
- 4 rondes
- Pause de 15 min après ronde 2

### Résultat

```
RONDE 1 - 09:00
  Terrain 1: A+B vs C+D
  Terrain 2: E+F vs G+H
  Terrain 3: I+J vs K+L

RONDE 1 (suite) - 09:15
  (Pas de suite, 3 matchs = 3 terrains, tout tient en une vague)

RONDE 2 - 09:15
  Terrain 1: A+C vs B+E
  Terrain 2: D+F vs G+I
  Terrain 3: H+J vs K+L? (ajustement selon jumelage)

--- PAUSE 15 MINUTES (09:30 - 09:45) ---

RONDE 3 - 09:45
  Terrain 1: ...
  Terrain 2: ...
  Terrain 3: ...

RONDE 4 - 10:00
  Terrain 1: ...
  Terrain 2: ...
  Terrain 3: ...

FIN ESTIMÉE: 10:15
```

---

## Ajustements en Temps Réel

### Si un Match Prend du Retard

Option 1: **Décaler les suivants**
- Simple mais peut créer effet domino

Option 2: **Absorber avec pauses**
- Réduire les pauses pour rattraper

Option 3: **Ne pas modifier**
- L'horaire est indicatif, les matchs commencent quand le terrain est libre

### Recommandation

Afficher l'horaire comme "prévu" et non comme absolu:
- "Ronde 2 - 09:15 (prévu)"
- "Ronde 2 - Terrain libre"

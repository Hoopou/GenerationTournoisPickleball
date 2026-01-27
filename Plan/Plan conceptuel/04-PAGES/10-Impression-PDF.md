# Page: Impression et Génération PDF

## Objectif
Permettre l'impression et l'export de tous les documents nécessaires au bon déroulement du tournoi: listes, cédules, classements, brackets, et feuilles de match.

---

## Accès
- **Rôles**: Administrateur et Superviseur (lecture/export)
- **Menu**: Tournoi > Impressions
- **Aussi accessible**: Boutons "PDF" et "Imprimer" sur chaque page concernée

---

## Centre d'Impression

### Page Principale

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  CENTRE D'IMPRESSION                                                        │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  Tournoi: Méli-Mélo Janvier 2026                                           │
│  Catégorie: [Toutes les catégories      ▼]                                 │
│                                                                             │
│  DOCUMENTS DISPONIBLES                                                      │
│  ─────────────────────                                                      │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 📄 LISTES DE JOUEURS                                                │   │
│  │ ────────────────────                                                │   │
│  │ ☐ Liste complète de tous les joueurs                               │   │
│  │ ☐ Liste par catégorie                                              │   │
│  │ ☐ Liste des substituts                                             │   │
│  │                                      [👁️ Aperçu]  [📥 Télécharger] │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 📅 CÉDULES DE MATCHS                                                │   │
│  │ ────────────────────                                                │   │
│  │ ☐ Cédule complète (toutes rondes)                                  │   │
│  │ ☐ Cédule par ronde                                                 │   │
│  │ ☐ Cédule par terrain                                               │   │
│  │ ☐ Horaire récapitulatif                                            │   │
│  │                                      [👁️ Aperçu]  [📥 Télécharger] │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 📊 CLASSEMENTS                                                      │   │
│  │ ─────────────                                                       │   │
│  │ ☐ Classement par catégorie                                         │   │
│  │ ☐ Classement global avec statistiques                              │   │
│  │                                      [👁️ Aperçu]  [📥 Télécharger] │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 🏆 SÉRIES ÉLIMINATOIRES                                             │   │
│  │ ───────────────────────                                             │   │
│  │ ☐ Bracket d'élimination                                            │   │
│  │ ☐ Formation des équipes                                            │   │
│  │ ☐ Résultats finaux / Podium                                        │   │
│  │                                      [👁️ Aperçu]  [📥 Télécharger] │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ 📝 FEUILLES DE MATCH                                                │   │
│  │ ────────────────────                                                │   │
│  │ ☐ Feuilles vierges pour saisie manuelle                            │   │
│  │ ☐ Feuilles pré-remplies avec noms                                  │   │
│  │                                      [👁️ Aperçu]  [📥 Télécharger] │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  [📦 Télécharger tout (ZIP)]  [🖨️ Imprimer sélection]                      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Types de Documents

### 1. Liste des Joueurs

**Contenu:**
- Nom complet
- Sexe, Âge, Niveau
- Catégorie assignée
- Numéro de membre (si présent)

**Format:**
```
┌─────────────────────────────────────────────────────────────────┐
│  LISTE DES JOUEURS - HOMME 35-50 3.5                           │
│  Tournoi: Méli-Mélo Janvier 2026                               │
│  Date: 15 janvier 2026                                          │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  #   Nom                  Sexe   Âge   Niveau   N° Membre       │
│  ─── ──────────────────── ────── ───── ──────── ─────────       │
│  1   Tremblay, Jean       H      38    3.5      12345           │
│  2   Lavoie, Pierre       H      42    3.5      12346           │
│  3   Martin, Luc          H      45    3.5      -               │
│  4   Roy, Marc            H      40    3.5      12348           │
│  ...                                                            │
│                                                                 │
│  Total: 12 joueurs                                              │
│                                                                 │
│  Généré le 15/01/2026 à 08:30                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

### 2. Cédule des Matchs

**Format Complet:**
```
┌─────────────────────────────────────────────────────────────────┐
│  CÉDULE DES MATCHS - HOMME 35-50 3.5                           │
│  Tournoi: Méli-Mélo Janvier 2026                               │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  RONDE 1 - 09:00                                                │
│  ─────────────────                                              │
│  Terrain 1: Tremblay + Lavoie  VS  Martin + Roy                │
│  Terrain 2: Gagnon + Dubois    VS  Morin + Côté                │
│  Terrain 3: Pelletier + Fortin VS  Girard + Boucher            │
│                                                                 │
│  RONDE 2 - 09:15                                                │
│  ─────────────────                                              │
│  Terrain 1: Tremblay + Gagnon  VS  Dubois + Lavoie             │
│  Terrain 2: Martin + Morin     VS  Roy + Pelletier             │
│  Terrain 3: Côté + Girard      VS  Fortin + Boucher            │
│                                                                 │
│  ⏸️ PAUSE 09:30 - 09:45                                        │
│                                                                 │
│  RONDE 3 - 09:45                                                │
│  ...                                                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Format par Terrain:**
```
┌─────────────────────────────────────────────────────────────────┐
│  CÉDULE - TERRAIN 1                                            │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Heure     Équipe A                  VS    Équipe B             │
│  ─────     ────────────────────────        ─────────────────    │
│  09:00     Tremblay + Lavoie               Martin + Roy         │
│  09:15     Tremblay + Gagnon               Dubois + Lavoie      │
│  09:45     Martin + Côté                   Gagnon + Fortin      │
│  10:00     Roy + Dubois                    Lavoie + Girard      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 3. Classement

**Format Standard:**
```
┌─────────────────────────────────────────────────────────────────┐
│                     CLASSEMENT OFFICIEL                         │
│             Tournoi Méli-Mélo - Janvier 2026                   │
│                  Homme - 35-50 - 3.5                           │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Rang   Joueur               Victoires   Diff    Points        │
│  ────   ──────────────────   ─────────   ────    ──────        │
│   🥇    Tremblay, Jean          4        +15       44           │
│   🥈    Lavoie, Pierre          4        +12       42           │
│   🥉    Martin, Luc             3         +8       38           │
│    4    Roy, Marc               3         +5       35           │
│    5    Gagnon, Pierre          2         +2       30           │
│    6    Dubois, André           2         -1       28           │
│    7    Morin, François         1         -5       24           │
│    8    Côté, Michel            1         -8       22           │
│    9    Pelletier, Robert       0        -10       18           │
│   10    Fortin, Daniel          0        -12       16           │
│                                                                 │
│  Critères: Victoires > Différentiel > Points marqués           │
│                                                                 │
│  Classement au: 15/01/2026 - 12:00                             │
└─────────────────────────────────────────────────────────────────┘
```

---

### 4. Bracket Séries

**Format Imprimable:**
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        SÉRIES ÉLIMINATOIRES                                 │
│                    Homme - 35-50 - 3.5                                      │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│     DEMI-FINALES                                FINALE                      │
│     (11:00)                                     (11:30)                     │
│                                                                             │
│     ┌───────────────────────┐                                               │
│     │ Équipe 1              │                                               │
│     │ Tremblay + Gagnon     │────┐                                          │
│     └───────────────────────┘    │                                          │
│              vs                  │         ┌───────────────────────┐        │
│     ┌───────────────────────┐    ├────────►│                       │        │
│     │ Équipe 4              │    │         │                       │        │
│     │ Roy + Côté            │────┘         │                       │        │
│     └───────────────────────┘              │         🏆            │        │
│                                            │       CHAMPION        │        │
│     ┌───────────────────────┐              │                       │        │
│     │ Équipe 2              │    ┌────────►│                       │        │
│     │ Lavoie + Dubois       │────┤         └───────────────────────┘        │
│     └───────────────────────┘    │                                          │
│              vs                  │                                          │
│     ┌───────────────────────┐    │                                          │
│     │ Équipe 3              │────┘                                          │
│     │ Martin + Morin        │                                               │
│     └───────────────────────┘                                               │
│                                                                             │
│  Formation: #1+#5, #2+#6, #3+#7, #4+#8                                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 5. Feuilles de Match

**Feuille Pré-remplie:**
```
┌─────────────────────────────────────────────────────────────────┐
│  FEUILLE DE MATCH                                               │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Ronde: 1        Terrain: 1        Heure: 09:00                │
│  Catégorie: Homme - 35-50 - 3.5                                │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │  ÉQUIPE A                         ÉQUIPE B              │   │
│  │  ─────────                        ─────────             │   │
│  │                                                         │   │
│  │  Tremblay, Jean                   Martin, Luc           │   │
│  │  Lavoie, Pierre                   Roy, Marc             │   │
│  │                                                         │   │
│  │                                                         │   │
│  │  SCORE:  ┌─────────┐              ┌─────────┐           │   │
│  │          │         │     VS       │         │           │   │
│  │          │         │              │         │           │   │
│  │          └─────────┘              └─────────┘           │   │
│  │                                                         │   │
│  │                                                         │   │
│  │  Vainqueur: ☐ Équipe A    ☐ Équipe B                   │   │
│  │                                                         │   │
│  │  Signature arbitre: ____________________                │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Feuille Vierge:**
```
┌─────────────────────────────────────────────────────────────────┐
│  FEUILLE DE MATCH                                               │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Ronde: ___     Terrain: ___     Heure: ___:___                │
│  Catégorie: _________________________________                   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                                                         │   │
│  │  ÉQUIPE A                         ÉQUIPE B              │   │
│  │  ─────────                        ─────────             │   │
│  │                                                         │   │
│  │  1. ____________________          1. ____________________│   │
│  │  2. ____________________          2. ____________________│   │
│  │                                                         │   │
│  │                                                         │   │
│  │  SCORE:  ┌─────────┐              ┌─────────┐           │   │
│  │          │         │     VS       │         │           │   │
│  │          │         │              │         │           │   │
│  │          └─────────┘              └─────────┘           │   │
│  │                                                         │   │
│  │                                                         │   │
│  │  Vainqueur: ☐ Équipe A    ☐ Équipe B                   │   │
│  │                                                         │   │
│  │  Signature: ____________________                        │   │
│  │                                                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 6. Résultats Finaux / Podium

**Certificat Champion:**
```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                           🏆                                    │
│                                                                 │
│                       CHAMPION                                  │
│              Tournoi Méli-Mélo Pickleball                      │
│                   Janvier 2026                                  │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│                    Catégorie:                                   │
│                 Homme - 35-50 - 3.5                            │
│                                                                 │
│                    ÉQUIPE GAGNANTE                              │
│                                                                 │
│                  Jean TREMBLAY                                  │
│                        &                                        │
│                  Pierre GAGNON                                  │
│                                                                 │
│  ─────────────────────────────────────────────────────────────  │
│                                                                 │
│  Score finale: 11 - 9                                          │
│                                                                 │
│  Date: 15 janvier 2026                                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Options d'Impression

### Paramètres Généraux

```
┌─────────────────────────────────────────────────────────────────┐
│  OPTIONS D'IMPRESSION                                           │
│  ───────────────────────────────────────────────────────────── │
│                                                                 │
│  Format du papier:                                              │
│  ○ Lettre (8.5 x 11 po)                                        │
│  ○ A4 (210 x 297 mm)                                           │
│  ○ Légal (8.5 x 14 po)                                         │
│                                                                 │
│  Orientation:                                                   │
│  ○ Portrait                                                     │
│  ○ Paysage                                                      │
│                                                                 │
│  Qualité:                                                       │
│  ○ Brouillon (rapide)                                          │
│  ○ Normal                                                       │
│  ○ Haute qualité                                                │
│                                                                 │
│  Options:                                                       │
│  ☑️ Inclure le logo du tournoi                                 │
│  ☑️ Inclure la date de génération                              │
│  ☐ Imprimer en noir et blanc                                   │
│  ☐ Ajouter des numéros de page                                 │
│                                                                 │
│              [Annuler]  [Générer PDF]  [Imprimer]              │
└─────────────────────────────────────────────────────────────────┘
```

---

## Aperçu Avant Impression

### Fenêtre d'Aperçu

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  APERÇU - Classement Homme 35-50 3.5                    [×]                │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                                                                     │   │
│  │  ┌─────────────────────────────────────────────────────────────┐   │   │
│  │  │                                                             │   │   │
│  │  │              CLASSEMENT OFFICIEL                            │   │   │
│  │  │         Tournoi Méli-Mélo - Janvier 2026                   │   │   │
│  │  │              Homme - 35-50 - 3.5                           │   │   │
│  │  │                                                             │   │   │
│  │  │  Rang   Joueur             Vic   Diff   Pts                │   │   │
│  │  │  ────   ────────────────   ───   ────   ───                │   │   │
│  │  │   🥇    Tremblay, Jean      4    +15    44                 │   │   │
│  │  │   🥈    Lavoie, Pierre      4    +12    42                 │   │   │
│  │  │   ...                                                      │   │   │
│  │  │                                                             │   │   │
│  │  └─────────────────────────────────────────────────────────────┘   │   │
│  │                                                                     │   │
│  │                         Page 1 / 1                                 │   │
│  │                                                                     │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  [◀ Page précédente]  [Page suivante ▶]     [🖨️ Imprimer]  [📥 PDF]       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Export en Lot

### Télécharger Tout

Le bouton "Télécharger tout (ZIP)" génère une archive contenant:

```
Tournoi_MeliMelo_Janvier2026.zip
├── Listes/
│   ├── Liste_Complete.pdf
│   ├── Liste_Homme_35-50_35.pdf
│   ├── Liste_Femme_35-50_35.pdf
│   └── Liste_Substituts.pdf
├── Cedules/
│   ├── Cedule_Complete_Homme_35-50_35.pdf
│   ├── Cedule_Complete_Femme_35-50_35.pdf
│   ├── Cedule_Terrain1.pdf
│   └── ...
├── Classements/
│   ├── Classement_Homme_35-50_35.pdf
│   └── Classement_Femme_35-50_35.pdf
├── Series/
│   ├── Bracket_Homme_35-50_35.pdf
│   └── Resultats_Finaux_Homme_35-50_35.pdf
└── Feuilles_Match/
    ├── Feuilles_Preremplies_Ronde1.pdf
    └── ...
```

---

## Accès Rapide depuis Autres Pages

### Boutons Contextuels

Sur chaque page concernée, un bouton d'impression rapide:

| Page | Boutons Disponibles |
|------|---------------------|
| Liste Joueurs | [📄 PDF] [🖨️ Imprimer] |
| Catégories | [📄 PDF par catégorie] |
| Rondes Préliminaires | [📄 Cédule PDF] [📝 Feuilles de match] |
| Classement | [📄 PDF] [📊 Excel] |
| Séries | [📄 Bracket PDF] [🏆 Podium] |

# Résumé de l'Application — Tournoi Pickleball Méli-Mélo

## Qu'est-ce qu'un Tournoi Méli-Mélo?

Un tournoi "Méli-Mélo" est un format de tournoi de Pickleball où:

1. **Phase 1 — Rondes Préliminaires**: Les joueurs sont jumelés **aléatoirement** avec différents partenaires à chaque partie. Chaque joueur accumule des points **individuellement** même s'il joue en équipe de 2.

2. **Phase 2 — Séries Éliminatoires**: Les meilleurs joueurs de chaque catégorie forment des **équipes fixes** basées sur leur classement, puis s'affrontent en format élimination directe.

L'aspect "social" est central: maximiser les rencontres entre joueurs différents.

---

## Objectif de l'Application

Gérer l'ensemble du tournoi de A à Z:

1. **Avant le tournoi**
   - Créer et configurer le tournoi
   - Inscrire les joueurs (manuellement ou par import)
   - Générer les catégories selon les critères
   - Planifier les rondes préliminaires

2. **Pendant les rondes préliminaires**
   - Afficher la cédule aux joueurs
   - Saisir les scores en temps réel
   - Calculer le classement automatiquement
   - Gérer les imprévus (absences, substituts)

3. **Entre rondes et séries**
   - Afficher le classement final des rondes
   - Former les équipes pour les séries
   - Permettre ajustements si nécessaire

4. **Pendant les séries**
   - Afficher le bracket éliminatoire
   - Saisir les scores des matchs
   - Progression automatique des vainqueurs

5. **Après le tournoi**
   - Afficher les résultats finaux
   - Imprimer les tableaux et résultats

---

## Les Deux Phases Expliquées

### Phase 1: Rondes Préliminaires

**But**: Permettre aux joueurs de jouer avec et contre différentes personnes tout en accumulant des points individuels.

**Fonctionnement**:
- Chaque joueur joue un nombre fixe de parties (ex: 4 parties)
- À chaque partie, il est jumelé avec un partenaire différent
- Il affronte également des adversaires différents autant que possible
- Les points accumulés sont **individuels** (pas par équipe)

**Exemple**: 
- Partie 1: Jean + Marie vs Pierre + Sophie
- Partie 2: Jean + Pierre vs Marie + Luc
- Partie 3: Jean + Sophie vs Pierre + Marie
- etc.

Jean accumule ses propres victoires et différentiels, indépendamment de ses partenaires.

### Phase 2: Séries Éliminatoires

**But**: Couronner les meilleures équipes de chaque catégorie.

**Fonctionnement**:
- Les 8 ou 16 meilleurs joueurs de chaque catégorie participent
- Ils sont regroupés en équipes de 2 **fixes** pour toute la durée des séries
- Format élimination directe: perdre = être éliminé
- Le jumelage équilibre les forces (meilleur avec moins bon)

**Exemple avec 8 joueurs**:
- Équipe 1: Joueur rang 1 + Joueur rang 5
- Équipe 2: Joueur rang 3 + Joueur rang 7
- Équipe 3: Joueur rang 2 + Joueur rang 6
- Équipe 4: Joueur rang 4 + Joueur rang 8

---

## Catégories de Joueurs

Les joueurs sont regroupés en catégories selon 3 critères (dans l'ordre):

1. **Sexe**: Homme ou Femme
2. **Âge**: Tranches d'âge (si le tournoi n'est pas "ouvert")
3. **Niveau**: 3.0, 3.5, 4.0, 4.5, 5.0, Novice, Intermédiaire, Avancé

**Exemple de catégories**:
- Homme - 20-45 ans - Niveau 3.5
- Femme - 50+ ans - Niveau Intermédiaire
- Homme - Tous âges - Niveau 4.0 (tournoi ouvert)

Chaque catégorie a sa propre cédule de rondes et ses propres séries.

---

## Calcul du Classement (Rondes Préliminaires)

Chaque joueur est classé selon 3 critères (dans l'ordre de priorité):

1. **Nombre de victoires** (plus = mieux)
   - Une victoire = faire partie de l'équipe gagnante d'une partie

2. **Différentiel cumulé des défaites** (moins = mieux)
   - Pour chaque défaite: différentiel = score adverse - score équipe
   - On additionne tous les différentiels des défaites
   - Exemple: Perdre 11-8 et 11-6 = différentiel de 3 + 5 = 8

3. **Total des points marqués** (plus = mieux)
   - En cas d'égalité parfaite sur les 2 premiers critères

---

## Utilisateurs de l'Application

### Administrateur
- Configure le tournoi
- Gère les paramètres globaux
- Peut modifier/supprimer n'importe quoi
- Peut changer les catégories des joueurs
- Peut modifier l'ordre des participants aux séries

### Superviseur  
- Ajoute/modifie les joueurs
- Saisit les scores des parties
- Ne peut pas modifier les paramètres globaux
- Ne peut pas supprimer de parties

---

## Déroulement Type d'un Tournoi

1. **Semaines avant**: L'admin crée le tournoi, configure les paramètres
2. **Jours avant**: Import des joueurs inscrits (CSV ou manuel)
3. **Jour J matin**: 
   - Vérification des présences
   - Ajustement des joueurs si absences
   - Génération des catégories
   - Génération de la cédule des rondes
   - Impression des tableaux
4. **Jour J rondes**: 
   - Les parties se jouent selon la cédule
   - Les scores sont saisis après chaque partie
   - Le classement se met à jour en temps réel
5. **Jour J midi**: 
   - Fin des rondes préliminaires
   - Affichage du classement final
   - Génération des équipes de séries
   - Validation par l'admin
6. **Jour J après-midi**:
   - Les séries se jouent
   - Les scores sont saisis
   - Le bracket se remplit progressivement
7. **Jour J fin**:
   - Finale jouée
   - Résultats finaux affichés
   - Impression des résultats

---

## Contraintes Importantes

### Rondes Préliminaires
- Un joueur ne peut être jumelé qu'**une seule fois** avec le même partenaire
- Maximiser la rotation des **adversaires** (priorité) puis des partenaires
- Un joueur ne peut pas jouer 2 parties en même temps
- Tous les joueurs doivent jouer le **même nombre** de parties
- Les substituts ne cumulent **pas** de points

### Séries
- Les équipes sont **fixes** pour toute la durée des séries
- 8 joueurs = 4 équipes (demi-finales + finale)
- 16 joueurs = 8 équipes (quarts + demi + finale + match 3e place)

### Terrains et Horaires
- Respecter le nombre de terrains disponibles
- Respecter les périodes de pause (ex: dîner)
- Respecter l'heure de début des séries

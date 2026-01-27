# Page: Connexion

## Objectif
Permettre aux utilisateurs de s'authentifier pour accéder à l'application.

---

## Accès
- **URL**: Page d'entrée de l'application
- **Condition d'accès**: Non connecté
- **Redirection si connecté**: Dashboard

---

## Contenu de la Page

### Éléments Visuels

```
┌─────────────────────────────────────────────┐
│                                             │
│              [LOGO APPLICATION]             │
│                                             │
│         Tournoi Pickleball Méli-Mélo        │
│                                             │
│  ┌───────────────────────────────────────┐  │
│  │  📧 Email                             │  │
│  │  ┌─────────────────────────────────┐  │  │
│  │  │                                 │  │  │
│  │  └─────────────────────────────────┘  │  │
│  │                                       │  │
│  │  🔒 Mot de passe                      │  │
│  │  ┌─────────────────────────────────┐  │  │
│  │  │                                 │  │  │
│  │  └─────────────────────────────────┘  │  │
│  │                                       │  │
│  │  ☐ Se souvenir de moi                 │  │
│  │                                       │  │
│  │  ┌─────────────────────────────────┐  │  │
│  │  │        SE CONNECTER             │  │  │
│  │  └─────────────────────────────────┘  │  │
│  │                                       │  │
│  │  Mot de passe oublié?                 │  │
│  └───────────────────────────────────────┘  │
│                                             │
│              Version 1.0.0                  │
└─────────────────────────────────────────────┘
```

### Champs du Formulaire

| Champ | Type | Obligatoire | Validation |
|-------|------|-------------|------------|
| Email | Email | Oui | Format email valide |
| Mot de passe | Mot de passe | Oui | Non vide |
| Se souvenir | Checkbox | Non | - |

---

## Comportements

### Bouton "Se Connecter"

**Clic →**
1. Valider les champs (afficher erreurs si invalide)
2. Afficher indicateur de chargement
3. Envoyer la demande de connexion
4. **Si succès**: Rediriger vers Dashboard
5. **Si échec**: Afficher message d'erreur

### Messages d'Erreur Possibles

| Code | Message affiché |
|------|-----------------|
| Champs vides | "Veuillez remplir tous les champs." |
| Email invalide | "Format d'email invalide." |
| Identifiants incorrects | "Email ou mot de passe incorrect." |
| Compte bloqué | "Compte bloqué. Réessayez dans X minutes." |
| Compte inactif | "Ce compte a été désactivé. Contactez l'administrateur." |

### Lien "Mot de passe oublié?"

**Clic →**
- Afficher modale de récupération de mot de passe
- OU Rediriger vers page dédiée

**Modale de récupération**:
- Champ: Email
- Bouton: "Envoyer le lien de réinitialisation"
- Message succès: "Si ce compte existe, un email a été envoyé."

### Case "Se souvenir de moi"

- **Cochée**: Session persistante (30 jours)
- **Non cochée**: Session limitée (8 heures)

---

## Cas Particuliers

### Premier Lancement (Aucun Utilisateur)

Si aucun utilisateur n'existe dans le système:
- Afficher le formulaire de connexion normalement
- OU Rediriger vers une page de création du premier admin

### Tentatives Échouées

- Après 5 tentatives échouées en 15 minutes:
  - Bloquer le compte pendant 15 minutes
  - Afficher: "Trop de tentatives. Compte bloqué pour 15 minutes."
- Compteur réinitialisé après connexion réussie

### Redirection Post-Connexion

- Par défaut: Dashboard
- Si l'utilisateur tentait d'accéder à une page protégée: retour à cette page
- Si le tournoi précédemment consulté existe: rester sur ce tournoi

---

## Responsive

### Mobile
- Logo plus petit
- Formulaire pleine largeur avec marges
- Clavier adapté pour champ email

### Tablette / Desktop
- Formulaire centré, largeur maximale de 400px
- Ombre portée pour effet de carte

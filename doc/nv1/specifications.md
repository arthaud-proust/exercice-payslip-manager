# [nv.1] Cahier des charges

## Comptes utilisateurs

### Besoin

Les administrateurs ont besoin de se créer un compte pour gérer les salariés et pour gérer les présences.
Les salariés peuvent se créer un compte pour gérer leurs présences.  
Chaque compte, qu'importe le rôle, a un tarif journalier.

### Rôles et permissions

Deux rôles :

- administrateur
- salarié

Un administrateur doit pouvoir:

- accéder aux rapports
- générer un rapport
- gérer les présences de n'importe quel salarié
- voir la liste des salariés
- modifier un rôle de salarié

Un salarié doit pouvoir gérer ses présences.

### Inscription et connexion

Un utilisateur peut se créer un compte.

Le rôle attribué à l'inscription est "salarié".

Une authentification par email et mot de passe est suffisante.

Une réinitialisation de mot de passe en cas d'oubli est nécessaire.

Pas besoin de validation d'email.

### Compte par défaut

Un compte Administrateur par défaut doit être présent.  
Email: `admin@email.com`  
Mot de pase: `196$Sih-RD4`

## Jours travaillés

Pour chaque jour ouvré (lundi au vendredi) et qu'importe son rôle, un utilisateur peut définir s'il travaille, ou s'il ne travaille pas.
Par défaut, les jours ne sont pas marqués comme travaillés.

## Rapports mensuels

Le dernier jour de chaque mois à 23h59 (fuseau Paris) un rapport JSON est généré.  
Le rapport contient pour chaque employé ses jours travaillés du mois et son salaire.

Il y a une page affichant la liste des rapports. Il peuvent être téléchargés.

Un rapport du mois actuel peut être généré et téléchargé à la demande.

### Calcul du salaire

Le salaire est calculé via la formule suivante :

```
salary = dailyPrice * nbWorkedDays
```

### Format du rapport

```json
{
  "employees": [
    {
      "id": 1,
      "firstName": "...",
      "lastName": "...",
      "dailyPrice": 500,
      "salary": 1500,
      "workedDays": ["2023-01-01", "2023-01-02", "2023-01-08"]
    }
  ]
}
```

## Robustesse

Comme la société est de grande taille, le site doit pouvoir gérer 10 000 salariés.

Cela ne doit pas impacter les performances, les rapports doivent se générer en quelques secondes.

## Hébergement

Le site doit être totalement fonctionnel.
Il doit donc être en ligne et les requêtes sécurisées par TLS.
Il faut pouvoir envoyer des emails.

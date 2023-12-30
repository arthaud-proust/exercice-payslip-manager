# [nv.1] Cahier des charges

## Comptes utilisateurs

### Besoin

Les administrateurs ont besoin de se créer un compte pour gérer les salariés et pour gérer les présences.
Les salariés peuvent se créer un compte pour gérer leurs présences.  
Chaque compte, qu'importe le rôle, a un tarif journalier.

### Rôles

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

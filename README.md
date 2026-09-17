# Mon projet

## Projet web minimal utilisant HTML, Docker et PostgreSQL.

📁 Structure du projet

```
mon-projet/
├── .env
├── .gitignore
├── docker-compose.yml
├── index.html
└── README.md
```

## ⚙️ Prérequis

Installer les outils suivants :

````
Git
Docker Desktop
````

## Vérifier les installations :

```
git --version
docker --version
docker compose version
```

## 🚀 Initialisation du projet

### 1. Ouvrir le terminal dans le projet

Se placer dans le dossier du projet :

```
cd chemin/vers/mon-projet
```

### 2. Initialiser Git

Initialiser le repository Git :

```
Créer un nouveau repo git sur GitHub
Sur VS Code, mettre "Cloner un repository" et mettre le lien du nouveau repo
```


### 3. Vérifier le .gitignore

Le fichier .gitignore doit contenir :

```
.env
```

Le fichier .env contient des informations sensibles et ne doit jamais être envoyé sur GitHub.

### 4. Configurer les variables d'environnement

Le fichier .env contient la configuration PostgreSQL :

```
POSTGRES_DB=mon_projet
POSTGRES_USER=admin
POSTGRES_PASSWORD=change-moi
POSTGRES_PORT=5432
```

⚠️ Ne jamais publier le fichier .env sur GitHub.

## 🐳 Docker

### 5. Lancer PostgreSQL

Le fichier docker-compose.yml contient déjà la configuration de PostgreSQL.

Depuis la racine du projet :

```
docker compose up -d
```

Docker va :

Télécharger PostgreSQL si nécessaire.
Créer le conteneur PostgreSQL.
Créer le volume postgres_data.
Démarrer PostgreSQL en arrière-plan.

### 6. Vérifier PostgreSQL

Vérifier que le conteneur fonctionne :

```
docker compose ps
```

Le service db doit être actif.

Pour voir les logs :

```
docker compose logs db
```

Pour suivre les logs en temps réel :

```
docker compose logs -f db
```

### 7. Configuration PostgreSQL

La base de données utilise les valeurs du fichier .env :

```
Paramètre	Valeur
Base de données	mon_projet
Utilisateur	admin
Mot de passe	change-moi
Port	5432
```

Les données sont conservées dans le volume Docker :

```
postgres_data
```

## 🗄️ Accéder à la base de données PostgreSQL

### 8. Se connecter à PostgreSQL

Une fois le conteneur PostgreSQL démarré, il est possible d'accéder directement à PostgreSQL depuis le terminal.

Utiliser :

```
docker compose exec db psql -U admin -d mon_projet
```

Si la connexion fonctionne, le terminal affiche quelque chose comme :

```
psql (16.x)
Type "help" for help.
mon_projet=#
```

Le symbole :

```
mon_projet=#
```

signifie que vous êtes maintenant connecté à la base de données PostgreSQL.

Vous pouvez alors exécuter des requêtes SQL.

### 9. Commandes PostgreSQL utiles

Voir les bases de données

```
\l
```

Voir les tables

```
\dt
```

Voir la structure d'une table

```
\d contacts
```

Quitter PostgreSQL

```
\q
```

## 📋 Manipuler une table avec SQL

Les exemples suivants utilisent une table appelée contacts.

### 10. Créer une table

Créer une table contacts :

```
CREATE TABLE contacts (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100),
    email VARCHAR(255),
    telephone VARCHAR(20)
);
```

Vérifier que la table existe :

```
\dt
```

### 11. Ajouter des données — INSERT

Ajouter un contact :

```
INSERT INTO contacts (nom, email, telephone)
VALUES ('Jean Dupont', 'jean@email.com', '0612345678');
```

Ajouter plusieurs contacts :

```
INSERT INTO contacts (nom, email, telephone)
VALUES
    ('Jean Dupont', 'jean@email.com', '0612345678'),
    ('Marie Martin', 'marie@email.com', '0698765432'),
    ('Paul Durand', 'paul@email.com', '0611223344');
```

### 12. Lire les données — SELECT

Afficher tous les contacts :

```
SELECT * FROM contacts;
```

Afficher uniquement les noms et les emails :

```
SELECT nom, email
FROM contacts;
```

Afficher un contact précis :

```
SELECT *
FROM contacts
WHERE id = 1;
```

### 13. Mettre à jour des données — UPDATE

Modifier le numéro de téléphone du contact ayant l'identifiant 1 :

```
UPDATE contacts
SET telephone = '0600000000'
WHERE id = 1;
```

Modifier plusieurs informations :

```
UPDATE contacts
SET
    nom = 'Jean Martin',
    email = 'jean.martin@email.com'
WHERE id = 1;
```

⚠️ Toujours faire attention à la clause WHERE.

Par exemple :

```
UPDATE contacts
SET telephone = '0600000000';
```

modifierait le numéro de téléphone de tous les contacts.

### 14. Supprimer des données — DELETE

Supprimer le contact ayant l'identifiant 1 :

```
DELETE FROM contacts
WHERE id = 1;
```

⚠️ Attention à la clause WHERE.

Cette requête :

```
DELETE FROM contacts;
```

supprime tous les contacts de la table.

La table elle-même reste cependant présente.

## 🗑️ Supprimer une table

### 15. Supprimer la table contacts

Pour supprimer complètement la table :

```
DROP TABLE contacts;
```

Cela supprime :

La table.
Toutes les données qu'elle contient.
Sa structure.

Pour éviter une erreur si la table n'existe pas :

```
DROP TABLE IF EXISTS contacts;
```

Vérifier ensuite :

```
\dt
```

La table contacts ne doit plus apparaître.

⚠️ DROP TABLE est différent de DELETE.

```
DELETE FROM contacts;
```

➡️ Supprime les données mais conserve la table.

```
DROP TABLE contacts;
```

➡️ Supprime la table et ses données.


## 📌 État actuel

Le projet dispose actuellement de :

✅ Git
✅ GitHub
✅ Docker
✅ PostgreSQL
✅ Variables d'environnement .env
✅ index.html
✅ Volume Docker pour PostgreSQL

La communication entre le site et PostgreSQL sera ajoutée ultérieurement avec une technologie serveur adaptée.
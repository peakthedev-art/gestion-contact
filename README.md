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
git init
```

Définir main comme branche principale :

```
git branch -M main
```

Vérifier l'état du projet :

```
git status
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

Depuis la machine locale, PostgreSQL est accessible via :

```
localhost:5432
```

Les données sont conservées dans le volume Docker :

```
postgres_data
```

## 🐙 GitHub

### 8. Créer le repository GitHub

Créer un nouveau repository sur GitHub.

Exemple :

```
mon-projet
```

Le repository doit être créé vide :

❌ Pas de README
❌ Pas de .gitignore
❌ Pas de licence

Le README et le .gitignore existent déjà dans le projet local.

### 9. Connecter le projet à GitHub

Ajouter le repository GitHub comme remote :

```
git remote add origin https://github.com/USERNAME/mon-projet.git
```

Remplacer USERNAME par son nom d'utilisateur GitHub.

Vérifier la connexion :

```
git remote -v
```

### 10. Faire le premier commit

Ajouter les fichiers :

```
git add .
```

Créer le premier commit :

```
git commit -m "Initial project setup"
```

Envoyer le projet sur GitHub :

```
git push -u origin main
```

Le projet est maintenant disponible sur GitHub.

🔒 Le fichier .env ne sera pas envoyé grâce au .gitignore.

## 🌐 Site web

### 11. index.html

Le fichier index.html contient actuellement une page HTML minimale :

```
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mon projet</title>
</head>
<body>

    <h1>Mon projet</h1>

</body>
</html>
```

Le fichier peut être ouvert directement dans un navigateur.

## 🔄 Utilisation quotidienne

Démarrer PostgreSQL

```
docker compose up -d
```

Vérifier Docker

```
docker compose ps
```

Arrêter PostgreSQL

```
docker compose down
```

Les données PostgreSQL sont conservées.

Voir les modifications Git

```
git status
```

Envoyer des modifications sur GitHub

```
git add .
git commit -m "Description des modifications"
git push
```

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
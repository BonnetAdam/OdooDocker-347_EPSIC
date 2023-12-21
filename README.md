

---

# 🚀 Documentation du Projet Docker avec Odoo pour le Labo 347-08

## 🌟 Introduction
Ce projet a pour but de développer et déployer une application Odoo en utilisant Docker, en établissant des environnements de développement et de production distincts et adaptés.

## 📋 Charte de l'Équipe
- **Membres et Rôles :**
  - **👨‍💻 [Ruben](https://github.com/ruben4reall) :** Rédaction du README et préparation de la présentation.
  - **👨‍🔧 [Adam](https://github.com/CrazyOutOff) :** Implémentation et gestion de Docker.

- **📆 Planning de Travail :**
  - Travail pendant les heures de cours et, au besoin, pendant les weekends.

- **🛠️ Outils de Planification :**
  - Trello pour la gestion des tâches et GitHub pour le suivi du code.

- **📢 Communication :**
  - Mises à jour quotidiennes pour coordination.

- **📁 Gestion des Documents :**
  - Adam gère la finalisation et le rendu. Tous les fichiers seront sur GitHub.

## 🌐 Environnements de Développement et de Production
- **🔧 Base commune :** Les deux environnements partagent la même image Docker.
- **💻 Environnement de Développement :**
  - Addons pour le développement.
  - `odoo-dev.conf` pour la configuration.
  - Base de données distincte.
- **🚀 Environnement de Production :**
  - Addons pour le déploiement.
  - `odoo.conf` pour la configuration.

## 📂 Arborescence des Fichiers
Utilisation de la commande `git ls-tree -r --name-only HEAD | tree --fromfile` pour générer l'arborescence. Les commentaires sont ajoutés manuellement.

```
.
├── 🚫 .gitignore                # Exclusion de fichiers
├── 🔗 .gitmodules               # Sous-modules
├── 📖 README.md                 # Documentation principale
├── 🧩 addons                    # Addons communs
│   └── 🔄 crm                   # Addon CRM
├── ⚙️ config                    # Configurations Odoo
│   ├── 🛠️ odoo-dev.conf         # Config dev
│   └── 🚀 odoo.conf             # Config prod
├── 🖥️ dev-addons                # Addons pour le dev
│   └── 🌐 web                   # Addon web
├── 🐳 docker-compose.dev.yml    # Docker Compose dev
└── 🐳 docker-compose.prod.yml   # Docker Compose prod
```

## 🏗️ Architecture Docker
- **📦 2 Containers :**
  - 🌐 Odoo (Back-end + Front-end, port 8069).
  - 💾 PostgreSQL (Base de données, port 5432).

## 📘 Guide d'Utilisation

### 📥 Clonage du Repository
1. **🔑 Avec clé SSH :**
   ```bash
   git clone --recursive git@github.com:CrazyOutOff/347-08.git
   ```
   Cette commande clone le repository en utilisant SSH, ce qui nécessite une clé SSH configurée sur GitHub. L'option `--recursive` assure que tous les sous-modules sont également clonés.

2. **🔗 Sans clé SSH :**
   ```bash
   git clone --recursive https://github.com/CrazyOutOff/347-08.git
   ```
   Utilisez cette commande si vous n'avez pas configuré de clé SSH. Elle clone le repository via HTTPS.

### ▶️ Lancement des Environnements
1. **💻 Développement :**
   ```bash
   docker-compose -f docker-compose.dev.yml up
   ```
   Cette commande lance l'environnement de développement en utilisant le fichier `docker-compose.dev.yml`. Elle démarre tous les services définis dans ce fichier Docker Compose.

2. **🚀 Production :**
   ```bash
   docker-compose -f docker-compose.prod.yml up
   ```
   Utilisez cette commande pour lancer l'environnement de production. Elle se base sur le fichier `docker-compose.prod.yml`, qui contient la configuration pour la production.

### ⏹️

 Arrêt des Environnements
1. **🛑 Arrêt standard :**
   ```bash
   docker-compose -f <fichier> down
   ```
   Remplacez `<fichier>` par le nom du fichier Docker Compose correspondant à l'environnement que vous souhaitez arrêter.

2. **🧹 Arrêt avec suppression des volumes :**
   ```bash
   docker-compose -f <fichier> down -v
   ```
   Cette commande arrête l'environnement et supprime également les volumes associés, ce qui est utile pour un nettoyage complet.

---


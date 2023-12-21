

# 🚀 Documentation du Projet Docker avec Odoo pour le Labo 347-08

## 🌟 Introduction
Ce projet a pour but de développer et déployer une application Odoo en utilisant Docker, en créant des environnements de développement et de production distincts et adaptés.

## 📋 Charte de l'Équipe
- **Membres et Rôles :**
  - **👨‍💻 Ruben :** Rédaction du README et préparation de la présentation.
  - **👨‍🔧 Adam :** Implémentation et gestion de Docker.

- **📆 Planning de Travail :**
  - Travail pendant les heures de cours et, au besoin, les weekends.

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
- **🔑 Avec clé SSH :**
  ```bash
  git clone --recursive git@github.com:CrazyOutOff/347-08.git
  ```
- **🔗 Sans clé SSH :**
  ```bash
  git clone --recursive https://github.com/CrazyOutOff/347-08.git
  ```

### ▶️ Lancement des Environnements
- **💻 Développement :**
  ```bash
  docker-compose -f docker-compose.dev.yml up
  ```
- **🚀 Production :**
  ```bash
  docker-compose -f docker-compose.prod.yml up
  ```

### ⏹️ Arrêt des Environnements
- **🛑 Arrêt standard :**
  ```bash
  docker-compose -f <fichier> down
  ```
- **🧹 Arrêt avec suppression des volumes :**
  ```bash
  docker-compose -f <fichier> down -v
  ```


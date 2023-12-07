# 347-08 Labo Docker
Pour ce project nous avons desider de partir sur du Odoo. Nous avons donc créer un environnement de développement et un environnement de production. Dans l'environnement de développement nous avons ajouter des addons qui nous permet de développer plus rapidement. Dans l'environnement de production nous avons ajouter des addons qui nous permet de déployer plus rapidement.

## Charte du groupe
1. Qui fait quoi?
   - Ruben : ReadMe + Présentation
   - Adam  : Implimentation Docker
3. Quand est-ce qu’on va travailler ?
   - Pendant les heures de cours + si nécessaire en WeekEnd
5. Détails du travail à faire
    1. Outils de planification
       - Trello + Githubs
6. Comment/Quand (fréquence) on va communiquer ?
   - Tous les jours pour se donner des news et pouvoir s'organiser
7. Comment rent ont les documents ?
   - C'est Adam qui s'occupera du Rendu, tout sera sur le github et pourra être télécharger n'importe ou et a n'importe quelle moment

## Caractéristiques des environnements
Les environnements sont basé sur la même image. Cependant il y a des différences entre les deux. Dans l'env dev j'ai mis `Chargement de code` et `Variables d'environnement` ansi que des changements tels que pas la même base de données. 

## Arborescence
J'ai utiliser `git ls-tree -r --name-only HEAD | tree --fromfile` pour créer l'arborescence ci dessous. Les commentaire sont fait a la main en revanche.
```bash
.
├── .gitignore # Permet d'évite de commit les mauvais fichier
├── .gitmodules # Permet de ressencer les submodules
├── README.md # Le fichier que vous lisez actuellement
├── addons # Les addons qui sont présent dans les deux environnement
│   └── crm # un addon utile en prod sur Odoo
├── config # Les fichiers de configuration
│   ├── odoo-dev.conf # La configuration de l'environnement de dev
│   └── odoo.conf # La configuration de l'environnement de prod
├── dev-addons # Les addons qui sont présent uniquement dans l'environnement de dev
│   └── web # Un addon utile en dev sur Odoo
├── docker-compose.dev.yml # Le fichier de configuration de l'environnement de dev
└── docker-compose.prod.yml # Le fichier de configuration de l'environnement de prod
```

## Architecture
Dans ce projet docker nous avons 2 containers, un contenant mon Back + mon Front, Odoo à malheuresement été développer comme ceci. Et un autre contenant qui contient la base de donnée. Nous avons donc 2 containers qui communique entre eux. Le container Odoo est accessible via le port 8069 et le container Postgres est accessible via le port 5432. 

## How To
/!\ Attention. Si le terminal vous met une erreur pour `docker-compose`, il faut faire `docker compose`. Cela est du suite a l'installation que vous avait choisi  /!\
### Comment Cloner ?
Dans notre repos j'ai utiliser des submodules externe. Donc pour clone notre repos il faut le faire d'une façon particulière. Les commandes ci dessous change si vous avais une clefs ssh relier a github ou non. 
##### Avec clefs SSH
```bash
git clone --recursive git@github.com:CrazyOutOff/347-08.git
```
##### Sans clefs SSH
```bash
git clone --recursive https://github.com/CrazyOutOff/347-08.git
```
#### Comment lancer l'environnement de développement
L'environnement de développement a des modules supplémentaire qui ne sont pas présent dans l'environnement de production. Dans ce dossier nous pouvons mettre des Addons qui permet de nous aider a developer et debugger plus rapidement.
```bash
docker-compose -f docker-compose.dev.yml up
```
#### Comment lancer l'environnement de production
L'environment de production na pas les modules qui sont present dans dev-addons.
```bash
docker-compose -f docker-compose.prod.yml up
```

#### Comment stoper un environnement
Dans le script suivant vous devais remplacer \<file> par le fichier que vous voulez stoper. Les noms des fichiers sont indiquer dans les commandes ci dessus.
```bash
docker-compose -f <file> down
```
Et si vous souhaiter vraiment tout supprimer il vous faut ajouter `-v` à la fin de la commande. Comme sa vous supprimer les volumes.

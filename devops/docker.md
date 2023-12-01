# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la création d'une image docker ✔️ <br/>
  Pour créer une image Docker, dans mon dossier concerné, je créé un fichier Dockerfile. A l'intérieur de celui-ci je défini mon environnement de départ avec "FROM", puis j'execute la commande de créer /app avec RUN mkdir /app. Je défini quel est répertoir de travail avec WORKDIR /app. Je copy mon index.js, dans le fichier index.js de mon image. Je lance la commande pour démarer sur mon terminal CMD node index.js<br/>

- l'éxécution d'un container ✔️ <br/>
  Pour démarrer un container à partir d'une image : <br/>
  --> docker run nomDeMonApp <br />
  Pour démarre un container de façon détachée et consulter les logs : <br />
  --> docker run -d nomDeMonApp <br/>
  Pour consulter les logs : <br/>
  --> docker logs -f idDeMonConteneur

- l'orchestration de containers avec docker-compose ✔️ <br/>
  Par exemple mon projet comprends plusieurs images/containes. Au lieu de devoir toutes les lancer une à une, je peux créer à la racine de mon projet un fichier docker-compose.yml <br />
  Celui-ci va reprendre les information de chacun des Dockerfile présents dans mon dossier et par exemple aussi reprendre celui d'un SGBDR (mongoDb par ex) <br/>
  Je vais pouvoir y ajouter des volumes par service pour obtenir un hot reload sur ma machine, le reload ne se faisant que sur le serveur docker apr défaut.

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

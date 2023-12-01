# Docker

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

Pour utiliser Docker, je dois tout d'abord l'installer sur mon environnement de travail, ce qui me permet de créer mon propre compte sur DockerHub (pour, entre autre, partager des images de conteneur Docker, collaborer en équipe) et Docker Desktop sur ma machine.

- la création d'une image docker ✔️ <br/>
  Pour créer une image Docker, dans mon dossier concerné, je créé un fichier nommé Dockerfile.<br/>
  Dockerfile d'un dossier backend (ex) : <br/>

  ```
  FROM node:20.9.0-alpine3.17 // définition de mon environnement de départ

  WORKDIR /app //Je défini quel est répertoire de travail

  COPY package*.json ./  // Je copie mes fichier commencant par package et ayant l'extension .json

  RUN npm install  // J'installe les dépendances

  COPY ./tsconfig.json ./tsconfig.json  // je copie le fichier tsconfig.json de mon app en local, vers le même emplacement dans mon image
  COPY ./src ./src // je copie mon dossier src de mon app en local, vers le même emplacement dans mon image

  CMD npm start // je démarre mon app
  ```

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
  Je vais pouvoir y ajouter des volumes par service pour obtenir un hot reload sur ma machine, le reload ne se faisant que sur le serveur docker apr défaut. <br/>
  Pour finir on va pouvoir lancer la commande : <br/>
  --> docker compose up <br/>
  --> docker compose -f docker-compose.dev.yml up --build // avec cette commande légèrement différente, cela nous permet de spécifier quel fichier docker-compose on veux lancer. Si on utilise la première commande, cela sera d'office le "docker-compose.yml" --build indique que l'on sohaite recompiler l'image

- Entrer en mode shell pour avoir accès à un premier set de données en runnant notre fichier resetDb.ts : <br/>

```

docker exec -it containerId sh
/app # ls
/app # npm run resetDB // si le script est bien écrit dans ce sens dans le package.json

```

## 💻 J'utilise

### Un exemple personnel commenté ✔️

Dockerfile du front : <br/>

```

FROM node:20.9.0-alpine3.17

WORKDIR /app

COPY package\*.json ./

RUN npm install

COPY ./tsconfig.json ./tsconfig.json
COPY ./next-env.d.ts ./next-env.d.ts
COPY ./next.config.js ./next.config.js
COPY ./tailwind.config.js ./tailwind.config.js
COPY ./postcss.config.js ./postcss.config.js

COPY ./src ./src

CMD npm run dev

```

Dockerfile d'un MongoDb ajouté dans un projet<br/>

docker-compose.yml (ex) : <br/>

```
services:
  db:
    image: postgres:15-alpine
    environment:
      - POSTGRES_PASSWORD=postgres
    healthcheck: // pour vérifier que la db est bien connectée avant de lancer les autres images pour ne pas faire planter le projet
      test: ["CMD-SHELL", "pg_isready -d postgres -U postgres"]
      interval: 10s
      timeout: 5s
      retries: 5

  backend:
    depends_on:
      db:
        condition: service_healthy
    build: backend
    ports:
      - 4001:4001
    volumes:
      - ./backend/src:/app/src

  frontend:
    build: frontend
    ports:
      - 3000:3000
    volumes:
      - ./frontend/src:/app/src
```

### Utilisation dans un projet ❌ / ✔️

[lien github](git@github.com:caudrel/the-good-corner.git)

Description : branches docker et dockerProd. C'est le projet fil rouge codé en cours pour apprendre les différentes stacks. C'est un site de publication d'annonces entre particuliers.

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

- repliquer dans un autre projet que le projet fil rouge de notre cours ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

```

```

```

```

```

```

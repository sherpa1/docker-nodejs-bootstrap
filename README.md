# Docker + Node.js Bootstrap

## Variables d'environnement

Renommer et adapter le fichier ./api/.env.example :

```
- ./api/.env
```

## Test de l'API

### Requête HTTP GET

Après avoir démarré les services Docker, la commande :

`curl localhost:3000`

doit fournir la réponse suivante :

`{"message":"Welcome !"}`

### Requête HTTP POST

`curl localhost:3000 -H "Content-Type: application/json" -X POST -d '{"message":"Hello World!"}'`

doit fournir la réponse suivante :

`{"message":"Hello World!"}`

## Commandes utiles

### Node.js

#### Environnement de Dévelopement

Dans le fichier ./api/.env, indiquer la valeur :

`NODE_ENV=dev`

#### Environnement de Production

Dans le fichier ./api/.env, indiquer la valeur :

`NODE_ENV=production`

### Docker

#### Lancer les services Docker

```
docker-compose up
```

#### Lancer les services Docker et reprendre la main dans Bash

```
docker-compose up -d
```

#### Arrêter les services Docker

```
docker-compose stop
```

### Docker + Node.js

#### Installer les dépendances NPM dans le dossier node_modules du container

Les modules NPM doivent être installés directement dans le container de destination (et pas simplement synchroniser avec le volume source).

Plusieurs solutions sont possibles :

1 - Via une commande docker-compose :

`docker-compose run api npm install`

2 - Via bash, au sein du container :

`docker-compose run api bash`

puis

`npm install`

3 - Via l'attribut "command" du service dans le fichier docker-compose.yml :

`command: bash -c 'npm i && npm start'`

Démarrer les services après avoir activé cette commande.
Une fois les modules NPM installés (en particulier Nodemon), pour activer le Hot Reloading, possibilité d'utiliser la commande :

`command: bash -c 'npm run dev'`

---

**Alexandre Leroux**

- _Mail_ : alex@sherpa.one
- _Github_ : sherpa1
- _Twitter_ : @_sherpa_
- _Discord_ : sherpa#3890

_Enseignant vacataire à l'Université de Lorraine_

- IUT Nancy-Charlemagne (LP Ciasie)

- Institut des Sciences du Digital (Masters Sciences Cognitives)

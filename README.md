# Docker + Node.js Bootstrap

## Variables d'environnement

Renommer et adapter le fichier ./api/.env.example :

```
- ./api/.env
```

<br>
<br>

## Test de l'API

### Requête HTTP GET

Après avoir démarré les services Docker, la commande :

`curl localhost:3000`

doit fournir la réponse suivante :

`{"message":"Welcome !"}`

<br>
<br>

### Requête HTTP POST

`curl localhost:3000 -H "Content-Type: application/json" -X POST -d '{"message":"Hello World!"}'`

doit fournir la réponse suivante :

`{"message":"Hello World!"}`

<br>
<br>

## Commandes utiles

### Node.js

#### Environnement de Dévelopement

Dans le fichier ./api/.env, indiquer la valeur :

`NODE_ENV=development`

#### Environnement de Production

Dans le fichier ./api/.env, indiquer la valeur :

`NODE_ENV=production`

<br>
<br>

### Docker

#### Lancer les services Docker

```
docker-compose up
```

<br>

#### Lancer les services Docker et reprendre la main dans Bash

```
docker-compose up -d
```

<br>

#### Arrêter les services Docker

```
docker-compose stop
```

<br>
<br>

### Docker + Node.js

#### Installer les dépendances NPM dans le dossier node_modules du container

Les modules NPM doivent être installés directement dans le container de destination (et pas simplement synchroniser avec le volume source).

Plusieurs solutions sont possibles :

1 - Via une commande docker-compose :

`docker-compose run api npm install`

<br>
<br>

2 - Via bash, au sein du container :

`docker-compose run api bash`

puis

`npm install`

<br>
<br>

3 - Via l'attribut "command" du service dans le fichier docker-compose.yml :

`command: bash -c 'npm i && npm start'`

_Répeter l'une des 3 méthodes d'installation à chaque fois qu'une nouvelle dépendance NPM est ajoutée au fichier ./api/package.json_

<br>
<br>

#### Hot Reloading

- Ajouter nodemon aux dépendances du fichier `./api/package.json`

- Installer Nodemon dans le container (via l'une des 3 méthodes ci-avant)

- Activer la commande suivante dans `docker-compose.yml`

`command: bash -c 'npm run dev'`

<br>
<br>

---

**Alexandre Leroux**

- _Mail_ : alex@sherpa.one
- _Github_ : sherpa1
- _Twitter_ : @_sherpa_
- _Discord_ : sherpa#3890

_Enseignant vacataire à l'Université de Lorraine_

- IUT Nancy-Charlemagne (LP Ciasie)

- Institut des Sciences du Digital (Masters Sciences Cognitives)


# Plusieurs aspects à évoquer

## des méthodes non conventionnels de jouer avec une API

- étrange d'un point de vue hackathon de dump la data de l'api en local : explique le "pseudo" ETL
  - Pendant le hackathon nous étions invités a *fetch* la data de l'API pour utiliser comme bon nous semble. La [documentation](https://github.com/EcrituresNumeriques/2022-Hackathon-Navigations/blob/main/DOC/README.md) nous invitait clairement a faire un dump local des epigrams (passages). Cela semble un peu contre intuitif sur la manière d'utiliser une API. Une contrainte qui aurait pu nous etre imposer aurait été de seulement d'accéder aux datas par requête. Mais apparement les organisateurs connaissaient les limitation de leur data et la flexibilité de leur API, nous proposant une alternative si l'on souhaitait faire de l'IA ou bien l'analytique et pas seulement de l'exposition ou bien forwarding.
  
### Possibilités

- Margot review plz -> Nous avons envisagé de faire seulement un frontend pour render les different plots comme le montre ce [notebook observable HQ](https://observablehq.com/d/7de89004c95e1067?collection=@lenamk/hackathon-navigations); cependant le mixte technologique de notre groupe nous a fait partir sur une extraction et une tranformation en python. Nous condamnent a devoir faire des updates de cette sources of truth (mais qui ne devrait pas posé de problème sachant que lanthologie est un corpus fini).

## Un retour sur l'API

- discours sur le formatage de l'Api qui ne permet pas de plugger directement dessus : retour critique sur la structuration technique du projet // le travail collaboratif et la réunion d'expertises diverses et externes sur le projet permet de souligner ses faiblesses, de renouer avec des choix d'implémentations fait au début de la conception technique et ainsi de davantage délimiter le projet en tant qu'objet technique = le projet 4 alimente/enrichie/actualise le projet AG / donc le hackathon n'est pas juste un moment ludique d'extension d'un projet global, c'est une occasion de dialogue critique avec un objet culturel
  - RESTfullness ???
  - interoperabilité de AG
  - suitable data format
  - travailler *en local* vs appeler une API
- détermination du projet par les profils techniques : choix des outils et des visualisations produites
  - on a décidé d'aller avec les spécialités de chacun
    - pourquoi?
      - ça simplifiait la productivité pour le temps donnée
      - permetait de se focaliser sur différent aspect de livrables a la fois paralllélisation
      - tout le monde mettait la main a la patte en même temps et demandait de l'aide poctuelle a la personne la plus concerné (doc, product, front, backend)

## Un travail à plusieurs endroits

- traçage dans les différents lieux d'intervention : commit, message, whats app, "t'as pusché chou", en incluant le troll volontaire et quelles traces on a conservé dans la doc (par besoin, urgence, contexte)

## La dynamique synergique de l'équipe 4

- la dynamique synergique qui s'est concrètement mise en place autour de la table de travail (photos à l'appui) qui a placé chacun dans un environnement technique choisi qu'il maîtrise tout en permettant les dialogues entre les différents lieux d'intervention et en gardant le fil rouge des visualisations prévues et visées pour conserver une cohérence de travail. (margot : je vais refaire un schéma de la table) - en parvenant à faire communiquer, à s'articuler en un commun

---

# Draft: Choix technologique(s)

## Séparation des expertises et des langages de programation

### pseudo-ETL ~~pipeline~~

*Extraction Transform Load* car

- API peut-être pas assez rapide
- pas dans le format qu'on souhaitait
- Too much overhead to do fast JS
- Too complex data struture to render
  - Maybe the API doesn't represent the data

Data wanted : <!--Lena pour Enzo: me semble que je t'avais noté le format dont j'avais besoin pour chaque viz, mais je ne sais plus si c'était sur papier ou dans un contexte numérique, ce qui me fait penser: on avait un chat? -->

- graph 1
    -

- visualisation 2

  -

#### Extract: API data dump au lieu connected frontend

#### Transform: Ingestable data for our use case

#### Load: A simple a sharable ~~end~~share-point (github)

## Frontend with D3

### Start from scratch --> Nope

### What and how do we represent ?

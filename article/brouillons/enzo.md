
# Plusieurs aspects à évoquer

## des méthodes non conventionnels de jouer avec une API ✅

- étrange d'un point de vue hackathon de dump la data de l'api en local : explique le "pseudo" ETL
  - Pendant le hackathon nous étions invités a *fetch* la data de l'API pour utiliser comme bon nous semble. La [documentation](https://github.com/EcrituresNumeriques/2022-Hackathon-Navigations/blob/main/DOC/README.md) nous invitait clairement a faire un dump local des epigrams (passages). Cela semble un peu contre intuitif sur la manière d'utiliser une API. Une contrainte qui aurait pu nous etre imposer aurait été de seulement d'accéder aux datas par requête. Mais apparement les organisateurs connaissaient les limitation de leur data et la flexibilité de leur API, nous proposant une alternative si l'on souhaitait faire de l'IA ou bien l'analytique et pas seulement de l'exposition ou bien forwarding.
  
### Possibilités 👀 Margot

Nous avions envisagé dans un premier temps procéder uniquement à un frontend pour render visibles les different plots (comme montré dans ce [notebook observable HQ](https://observablehq.com/d/7de89004c95e1067?collection=@lenamk/hackathon-navigations)); cependant la diversité technologique de notre groupe nous a réorienté vers une extraction et une tranformation en python.
Obligés à faire des updates de cette sources of truth (mais qui ne devrait pas posé de problème sachant que lanthologie est un corpus fini).
Cependant il reste possible de réaliser ce nous avons fait en full python ou javascript (dans un observable notebook with d3 ou jupyter notebook avec d3graph ou self encapsuled sans un site).
Les décisions prises par le groupe se justifient pour correspondre aux différents profils techniques du groupe, afin que chacun des membres puisse être plus à l'aise et efficace dans chacune de leurs tâches (tout en s'amusant).

## Un retour sur l'API

> - discours sur le formatage de l'Api qui ne permet pas de plugger directement dessus : retour critique sur la structuration technique du projet // le travail collaboratif et la réunion d'expertises diverses et externes sur le projet permet de souligner ses faiblesses, de renouer avec des choix d'implémentations fait au début de la conception technique et ainsi de davantage délimiter le projet en tant qu'objet technique = le projet 4 alimente/enrichie/actualise le projet AG / donc le hackathon n'est pas juste un moment ludique d'extension d'un projet global, c'est une occasion de dialogue critique avec un objet culturel
> - RESTfullness ???
> - interoperabilité de AG
> - suitable data format

Par la clarté de sa structure, l'API est simple de navigation à partir de son endpoint `/api`.
En revanche, l'accès à certaines données de l'API peuvent être obtenues directement par `/api/passages/` sans passer par les endpoints proposés et qui s'avèrent ainsi redondants.

1. Par exemple, le endpoint `/api/book` n'a en tant que tel pas été utilisé dans le cadre du projet du groupe pour accèder aux épigrammes d'un livre. Il s'est avéré, dans le travail de restructuration de l'API, que cet endpoint relevait davantage d'un filtre pour trier les épigrammes : `api/passages/?book_number=1` donne les épigrammes du livre 1.

1. Si la navigation dans les données de l'API s'en trouve accrue, il demeure une redondance de par le fonctionnement des URL retournées et attribuées dans chaque objet. Mais il n'est peut-être pas necessaire de dupliquer un sous-resources à l'intérieur d'un resource.
1. Certes on va miniser les calls à l'API drastiquement mais l'un des buts d'une API restfull est de concevoir l'API de manière à permettre aux clients de spécifier les données qu'ils souhaitent récupérer, afin d'éviter le transfert d'informations inutiles. On pourrez envisager de fournir une option pour récupérer toutes les sous-ressources de maniére optionnel mais si on envoit leut id c'est ptet pas necessaire.
1. Accessibilité aux sous-ressources doit êter rapide mais l'objectif est de permettre aux clients d'accéder rapidement aux données dont ils ont besoin sans avoir à récupérer des informations supplémentaires non pertinentes.

### dupliquer un sous-resources à l'intérieur d'un resource

```txt
GET /api/keywords/116/
```

```json
{
    "id": 116,
    "url": "https://anthologiagraeca.org/api/keywords/116/",
    "category": {
        "url": "https://anthologiagraeca.org/api/keyword_categories/4/",
        "names": [
            {
                "name": "Époques",
                "language": "fra"
            },
            {
                "name": "Periods",
                "language": "eng"
            },
            {
                "name": "Tempora",
                "language": "lat"
            },
            {
                "name": "Periodi",
                "language": "ita"
            },
            {
                "name": "Épocas",
                "language": "por"
            }
        ]
    },
    "names": [
        {
            "name": "époque byzantine",
            "language": "fra"
        },
        {
            "name": "epoca bizzantina",
            "language": "ita"
        }
    ],
...
}

```

```txt
GET /api/keyword_categories/4/
```

```json
{
    "url": "https://anthologiagraeca.org/api/keyword_categories/4/",
    "names": [
        {
            "name": "Époques",
            "language": "fra"
        },
        {
            "name": "Periods",
            "language": "eng"
        },
        {
            "name": "Tempora",
            "language": "lat"
        },
        {
            "name": "Periodi",
            "language": "ita"
        },
        {
            "name": "Épocas",
            "language": "por"
        }
    ]
}
```

### Proposition

```txt
GET /api/passages/{epigram_id}?include=texts,authors,comments
```

Utilisez le paramètre include pour spécifier les sous-ressources que vous souhaitez inclure dans la réponse, ici les sous-ressources "texts", "authors" et "comments" de l'épigramme.

Et bien sur:

```txt
GET /api/passages/{epigram_id}?include=all
```

serait equivalent a:

```txt
GET /api/passages/{epigram_id}
```

## détermination du projet par les profils techniques

- détermination du projet par les profils techniques : choix des outils et des visualisations produites
  - on a décidé d'aller avec les spécialités de chacun
    - pourquoi?
      - ça simplifiait la productivité pour le temps donnée
      - permetait de se focaliser sur différent aspect de livrables a la fois paralllélisation
      - tout le monde mettait la main a la patte en même temps et demandait de l'aide poctuelle a la personne la plus concerné (doc, product, front, backend)

## Un travail à plusieurs endroits

- traçage dans les différents lieux d'intervention : commit, message, whats app, "t'as pusché chou", en incluant le troll volontaire et quelles traces on a conservé dans la doc (par besoin, urgence, contexte)

## La dynamique synergique de l'équipe 4

Une dynamique synergique s'est concrètement mise en place autour de la table de travail (photos à l'appui), et a permis de placer chacun dans un environnement technique choisi  et maîtrisé. Cette disposition a engendré des dialogues entre les différents lieux d'intervention, tout en suivant le fil rouge des visualisations envisagées pour conserver une cohérence de travail [margot : je vais refaire un schéma de la table] — en parvenant à faire communiquer chaque personne et à faire dialogue chaque initiative, et ainsi former un commun.
Une fois attablée, la collaboration et les échanges se sont 'équipe s'est divisée en quatre sous-groupes, ouvrant  qui ont collaboré et changé pendant que les heures défilaient.
Dés le début, le premier sous-groupe, des pythonnistes, apparut !
Aprés avoir lu la documentation, notamment pour réaliser les tâches d'extraction des données comme cela était recommandé, ce sous-groupe composé de Marianne et d'Enzo se décrit alors comme le _backend_.
En effet leur tâche est principalement d'extraire et de transformer les données (voir ce jeu de données [dumpall](https://github.com/EPgg92/2022-Hackathon-Navigations/blob/Team4/Team4/dumpall.py)).
Une notion importante a émergé au moment de cette opération : le fait qu'une forme de contrat est nécessaire, ce contrat se traduisant par un traitement puis un affichage de ces données, notamment par une autre opération : une sémantique commune à définir.
Après le _backend_, c'est donc un _frontend_ qu'il faut mettre en place, il s'agit concrètement de réaliser des visualisations pour pouvoir observer des dynamiques.
Ce sous-groupe, ainsi nommé _frontend_, est initié par Lena sur la génération de visualisations, rejointe par Margot sur la manipulation des données dans des _notebooks_ — sorte de bacs à sable pour prototyper.
Alors que l'effervescence bat son plein, l'inquiétude concernant un livrable réalisé dans un temps aussi cours se fait ressentir.
Il est alors temps que le troisième sous-groupe apparaisse : le produit.
Margot, Lena et Antoine, délaissés par les _pythoneux_ concentrés sur des problèmes de restructuration des données (avec des Jupyter Notebooks, des inscriptions de shebang et des scripts [à préciser par @enzo]), se posent des questions de _timeline_ pour représenter les données, revoyant à la baisse les objectifs initialement formulés.
"AI pas le temps trop compliqué et notre backend a déjà du mal a démarré" laisse sous-entendre notre cerbère inquiet.
L'enjeu de montrer des relations entre des épigrammes n'est envisageable qu'en faisant usage de fonctionnalités déjà existantes dans la structuration des données dans l'Anthologie Grecque !
Simple pensai(en)t-il(s), le découpage par livre peut donner une première dimension a notre représentation.
Mais quel alors le lien avec les épigrammes, ce qui permet de les lier _entre_ les livres ?
Les mots-clés (_keywords_) contenus dans les epigrammes.
"Comment représenterons-nous ces données n'est pas la question pour l'instant" soupire le molosse qui se sépare déjà du groupe en quête de papier ! [précisions de @enzo nécessaires]
L'important est de répondre au contrat quand à l'intransigeance du _backend_ qui cherche d'abord dans l'API les premières brides d'information.
Désormais ils savent quoi chercher et demande alors la paix.
Chaque livre devrait être ainsi représenté par le backend [@antoine : ça y est je suis largué…]

```py
{
  "nb_epi": 0, # nombre d'épigrame par livre
  "list_id_epi": [], # la liste des ids des épigrams
  "nb_kw": 0, # nombre de keyword l'intérieur des épigrame du dit livre livre
  "list_id_kw": [], # la liste des keywords (qui s'avera etre la liste des URL des KW)
  "name": 'undefined', # Le nom du livre 
  "number": 0, # le numéro du livre
  "url": '', # l'url du livre
}
```

Maintenant que le sous-groupe _backend_ est occupé, la tâche des autres personnes est de trouver un accord entre les différents cerveaux, et le dessin de visualisations à trois stylos sur du papier est un bon moyen d'avancer sur ce point.
Les ronds et arcs apparaissent quasi directement !
Mais comment identifier les différents éléments de ces schémas de ces esquisses ?
Pour Margot, chaque nœud est un livre
Antoine (ou quelqu'un d'autre) rétorque que l'on ne peut pas ajouter des arcs pour chacun des mots-clés, cela serait trop fourni et incompréhensible.
Les ardeurs d'illisibilité de Margot raisonnées, nous nous demandons donc comment représenter les mots-clés part des arcs.
Lena ajoute que les capacités du _frontend_ choisit permettent de faire plus qu'un simple graphique de nœuds et d'arcs.
En effet elle indique que non seulement elle a accès à de une colorimétrie variée mais aussi que les arcs et les nœuds eux-mêmes peuvent porter des attributs visibles.
L'épaisseur des arcs et la largeur des nœuds représente alors le nombre de _keywords_.
Si la couleur est indéterminée pour le moment, elle sera certainement utile pour différencier les livres.
Les enfants de méduse sont en accord avec le plan, tous le monde se rassoit, et nous nous lançons dans l'implémentation des différentes idées.
Des _notes hérissons_ émergent (des _pads_) ainsi que des _chaînes_ diverses (Whatsapp, Discord, GitHub) afin de faciliter le partage des idées, et de leur formalisation sous forme de fichiers.
Les deux premières heures filent, des propositions d'utilisation de d3 only sont proposées, mais les enfants de méduses sont déjà emportés par le projet, et promettent une data beaucoup plus simple a loader au lieu de ddos l'api á chaque fois que l'on fait un graph ...
L'heure des victuailles sonne que la pression se fait déjà sentir dans le groupe.
Les serpents sensibles au vibrations laissent le brouhaha des cerveaux de tout les groupes descendre se rassasier !
Ils descendent aussi pour continuer leur quatre mains mais de la même manière se répétant de pizza froide et de calme.

dans le procahain épisode

- Succeed to share data
- Cerberes crée view2 pendant absence
- new contract
<https://github.com/EPgg92/2022-Hackathon-Navigations/commit/8250a783cbf0fa4ae3ff171c609191daf689d48e>

```json
{
    "view1": {
        "node_book": [
            {
                "name": "1",
                "nb_epi": 0,
                "list_id_epi": [
                    123
                ],
                "nb_kw": 0,
                "list_id_kw": []
            }
        ],
        "edge_keyword": {}
    },
    "view2": {
        "books": [
            {
                "name": "12",
                "map_kw": [
                    {
                        "name": "",
                        "caterory": "",
                        "list_epi": [
                            {
                                "name": "",
                                "id": "",
                                "url": ""
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
```

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

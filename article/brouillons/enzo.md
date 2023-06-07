
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

La dynamique synergique qui s'est concrètement mise en place autour de la table de travail (photos à l'appui) qui a placé chacun dans un environnement technique choisi qu'il maîtrise tout en permettant les dialogues entre les différents lieux d'intervention et en gardant le fil rouge des visualisations prévues et visées pour conserver une cohérence de travail. (margot : je vais refaire un schéma de la table) - en parvenant à faire communiquer, à s'articuler en un commun.
Une fois atablé, on peut décrire 4 sous-groupes principaux qui ont collaboré et changé pendant que les heures défilaient.
Trés vite dés le début, le premier sous-groupes, des pythonnistes, apparut!
Aprés avoir lu la doc afin d'extraire le data comme cela était recommendé.
Ce sous-groupe de 2 (Marianne et Enzo) se décrivit alors comme le backend car principalement souhaitant extraire et transformer la donnée. [dumpall](https://github.com/EPgg92/2022-Hackathon-Navigations/blob/Team4/Team4/dumpall.py)
La notion de contrat émergeait alors et l'idée d'une équipe frontend devenait évidente!
En effet, s'il y avait de la donnée a traité il fallait un format a définir et une sémantique commune à établir.
Et s'il y avait un backend c'était pour communiqué de l'information a un frontend.
Lena pris donc en charge une premiére exploration des visuialization possible et dynamiques de observable.
Créant ainsi le sous-groupe qui sera appelé frontend pour le reste du hackathon.
Margot la rejoindra pour faire des tests sur les notebook de noeud et d'arc qui formeront plus tard notre première visualisation.
Mais alors que l'effervesence battait son plein l'inquiétude du délivrable dans un temps aussi cours se fut resentir
Il était temps que le troisiéme sous groupe apparaisse: le produit.
Margot, Lena et Antoine, délaissé par les pythoneux en train de faire un 4 mains pour entre jupyter et des inscryption de shebang dans les scripts, se posait alors des questions de timeline revoyant à la baisse les expectations juste discuté avant que tout le mond s'assoient!
"AI pas le temps trop compliqué et notre backend a déjà du mal a démarré" laisse sous-entendre notre cerbère inquiet.
Des relations entre épigrames "oui" mais seulement si l'on utilise sur des features déjà existantes!
Simple pensai(en)t-il(s), le découpage par livre allait donné une premiére dimension a notre représentation.
Mais quel serait l'articulation ?
Les keywords contenus dans les epigrames.
"Comment on les représenteras ce n'est pas la question pour l'instant" soupira le molosse qui se séparait déjà en quête de papier de !
L'important était de répondre un contrat a l'intrensigeance du backend qui cherchait dans l'API les premières brides d'information.
Maintenant ils savaient quoi chercher et demandaient alors la paix.
Chaque livre devrait être ainsi représenté par le backend

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

Maintenant le backend est occupé, la tâche consitait a trouver un entendement entre les différents cerveau composant le canidé se regroupant sur une feuille de papier avec 3 stylos.
Les ronds et arcs apparurent quasi directement!
Cependant qui étaient quoi ? Margot habitué à GTR proposat de symboliser les noeuds par les livres.
Antoine (ou quelqu'un d'autre) retorquait que l'on ne pouvait pas ajouter des un arc par mots clés ca serait trop fourni et incompréhensible.
Les ardeurs d'illisibilité de Margot calmer; on revenait a se demander comment representer les keywords part des arcs.
Lena ajouta que les capacités du frontend choisit permettait de faire plus qu'un simple graph de noeud et d'arc.
En effet elle indiqua que non seulement elle avait accès à de la colorimétrie varié mais aussi que les arcs et les noeuds eux-mêmes pouvait porter des attributs visibles.
L´épaisseurs des arcs et la largeurs des noeud serait alors le nombre de keyword.
La couleur pas sûr pour le moment mais certainement utile pour différencier les livres.
Les enfants de méduse en accord avec le plan tout le monde se re-assis et on se lança dans l'implémentation des différentes idées.
Des notes hérissons émergérent et des channels divers (whatsapp, discord, github) s'ouvraient pour faciliter le partage de idée et des fichiers.
Les deux premiéres heures filaient des propositions de'utilisation de d3 only fur proposé mais les enfants de méduses déjà emporter par le projet prometait une data beaucoup plus simple a loader au lieu de ddos l'api á chaque fois que l'on fait un graph ...
L'heure des victuailles sonnait que la pression se faisait déjà sentir dans le groupes.
Les serpents sensibles au vibrations laissaient le brouhaha des cerveaux de tout les groupes descendre se rasasier!
Mais l'appel du ventre se faisant resentir ils descendairent aussi pour continuer leur 4 mains mais de la même maniére se repétant de pizza froide et de calme.

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

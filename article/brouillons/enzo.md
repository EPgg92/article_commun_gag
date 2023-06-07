
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
Parcontre certain endpoints semblent redondant voir inutiles car on pourrait seulement utilisé `/api/passages/` pour accéder.

1. Par exemple le endpoint `/api/book` ne semble pas avoir d'intérêt, on pourrait penser il nous permettrait d'accéder aux épigrams d'un livre. Mais au final on s'apercoit que les livres ne sont que un parametres de filtres pour les epigrams `api/passages/?book__number=1`.

1. La navigabilité est certes accrue mais souvent cela donne beaucoup de redondance grace au URL retourné dans chaque objet et attribué. Mais il n'est peut-être pas necessaire de dupliquer un sous-resources à l'intérieur d'un resource
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

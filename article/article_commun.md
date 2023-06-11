# Le projet Graph ton Anthologie Grecque (GAG) : restitution d’une expérience de Hackathon

Cet article procède pour une grande part d’un travail de restitution d’un projet collaboratif mené lors du Hackathon du colloque *Navigations anthologiques* (CRCEN 2022). Par oubli d’étapes, égarements d’archives, ou nostalgies d’un collectif, cette restitution comporte une dimension de romantisation qui ne demeure pas moins fidèle à l’expérience passée.

## Chauffe intellectuelle (Partie Margot + Antoine)
<!-- ~9h -->
À l’origine du travail effectué par le groupe 4 se trouve une recherche de complémentarité entre les différentes expertises et intérêts des membres le composant (voir *Présentation des membres* ci-dessus). La réalisation finale, intitulée "Graph ton Anthologie Grecque" (GAG), témoigne, dans les différents éléments qui la structurent (extraction et restructuraton des données, visualisations versionnées, documentation produite et publiée en parallèle) mais également dans la dynamique de production qui lui a permi de voir le jour, de chacun des profils présents et surtout de leur synergie commune.

<!-- ~9h15 -->
Une image dessinée (cf. Figure 1) au tout début de la période de brassage de cerveaux du groupe a permit à juste titre d’illustrer l’idéal de collaboration synergique visé non seulement par l’équipe mais plus largement par la communauté du colloque :

![Figure 1. La Marmite de la collaboration](https://s3.hedgedoc.org/demo/uploads/855005e5-a806-4aa9-845c-7b69a72baca6.jpg)

Légende de la figure 1. : dans une marmite mise à chauffer, différents éléments aux diverses aspérités et caractéristiques sont réunis. Ils forment, sur une vue en coupe, des strates de connaissances.

Ce que l’image ne montre pas directement est ce qui advient des différentes strates de connaissances une fois que l’espace qui les contient est rendu brûlant. Le travail de « chauffe intellectuelle » permet à ce qui était distinct de se mêler. Ce qui était auparavant un ensemble de composants ne partageant pas ou très peu de points communs dans leurs cultures se modifie pour faire émerger une complémentarité complice qui ne permet (presque) plus de distinguer les ingrédients à l’origine. Si le dernier stade de cette métamorphose, l’idée d’une complémentarité effaçant les oppositions disciplinaires pour fonder un collectif en action, s’est retrouvé notamment énoncé dans le cadre des échanges du colloque *Navigations anthologiques*, et évoque une dynamique plus générale des Humanités numériques, elle est à l’amorce du projet du groupe 4 (sans lui être exclusive puisque d’autres groupes du Hackathon ont pu l’adresser ou la performer indirectement).

Dans le cadre d’un projet délimité dans le temps comme dans l’espace de ses développements (le Hackathon se déroulait au sein de l’Université de Montréal sur une durée de 8 heures), le groupe 4 avait pour objectif commun de faire s’articuler ses différents profils pour permettre un alliage d’idées (ou un maillage de connaissances) et une interopérabilité des pratiques. Si les deux perspectives sont classiquement distinguées dans les Humanités numériques tout en déterminant la particularité d’un champs disciplinaire, il était important que dans l’articulation la théorie et la technique ne soient pas cloisonnées et que chaque membre puisse contribuer, selon ses compétences, aux deux perspectives. L’un des premiers défis qui s’est alors exprimé était moins le fait de s’accorder sur un théorie du projet (que veut-on réaliser ?) que sur un modèle technique (comment va-t-on réaliser ?) suffisamment souple et ouvert pour permettre à chacun des participant·e·s de contribuer avec ses pratiques numériques.

C’est en gardant en veille ces objectifs de complémentarité et interopérabilité qu’a été discuté le sujet de la réalisation. Parmi les différentes propositions de réalisation discutées, deux projets potentiels ont été identifiés et formulés lors du brainstorming :

- la fabrique d’un livre épigrammatique à la volée : selon des critères spécifiques et avec des parcours de lecture adaptatifs ;
- la visualisation ou le *graph* du corpus : sous la forme de graphiques, visualiser et structurer des liens anthologiques selon des critères thématiques, littéraires et/ou philologiques. <!-- Enzo: Beaucoup d’ambition ont été abandonné premièrement avec Marianne on voulait représenter les liens sémantiques des différent épigrames en créant leurs *embeddings*. J’avoue avoir rejoint cette équipe car on avait cette prétention (et les autres projets ne me tentait pas trop😅). --><!--écris-le alors (le truc des embeddings, pas que tu n’étais pas tenté par les autres projets)-->

Le premier projet des livres épigrammatiques évoquait dans sa structure et sa visée didactique le projet POP ([Plateforme Ouverte des Parcours d’imaginaires](http://pop.anthologiegrecque.org/#/)), projet initié par la CRCEN en 2018 qui propose des parcours de lecture thématiques de l’Anthologie grecque. Parce qu’il impliquait une lecture plus affinée du corpus, le projet POP était orienté vers des objectifs de diffusion et de personnalisation. Cette première perspective n’a pas été retenue justement parce qu’elle aurait nécessité un travail plus approfondi de la structure de l’Anthologie. Pour nous permettre de fournir un livrable à l’issue de l’Hackathon, nous avons conservé le deuxième sujet, se destinant à explorer les données anthologique, objectif qui représentait également davantage l’ensemble des profils et les intérêts du groupe. L’horizon du hackathon pour le groupe 4 se dessinait donc comme la lecture de l’Anthologie Grecque au travers des relations entre les épigrammes et au fil des livres qui la constituent.

## Dialogues entre idéation et réalisation

### L’anthologie comme corpus

Si le livrable final a été réalisé de manière concrète par plusieurs mains techniques, sa modélisation en amont repose sur une considération précise du corpus de travail et s’inscrit ainsi dans la lignée des recherches déjà produites autour du projet d’édition de l’Anthologie grecque par la CRCEN. Les différentes recherches qui ont été produites autour du projet d’édition de l’Anthologie Grecque, pour documenter un avancement ou expliciter une démarche, mettent chacune en perspective une même caractéristique de l’Anthologie qui est autant à l’origine de sa richesse qu’elle est en cause de sa complexité : l’Anthologie grecque est en réalité moins une oeuvre littéraire qu’un corpus regroupant plus de 4 000 épigrammes (soit des fragments généralement courts) [Mathilde & Margot, « Passés et présents anthologiques. Modèles de valorisation et d’appropriation de patrimoines anciens dans le projet d’édition numérique collaborative de l’Anthologie grecque », à paraître]. Par son histoire (la multiplication des manuscrits et compilations changeant sans cesse l’ordre, la nature et la succession des épigrammes) mais également par son principe de rassemblements de fragments distinct (par l’époque, l’auteur, le thème, le style ou même le modèle épigrammatique), l’Anthologie défie une notion d’oeuvre en tant qu’objet délimitable et échappe ainsi à des principes d’édition savante (mue par la recherche d’une *vérité* du texte et l’établissement d’une unique version) [@vitali-rosati_lepopee_2021]. Cette perspective sur un objet littéraire est au fondement d’un projet dont la composante éditoriale souhaite retranscrire l’hétérogénéité et la multitude d’un ensemble culturel.

La notion de corpus à la différence du principe d’oeuvre permet d’embrasser autant de phénomène de disparités, de pluralité que de contradiction au sein d’un collectif de textes sans lui enlever toute possibilité d’édition ou de structuration définies. Ce que cette approche implique cependant est de développer des outils de lecture, d’analyse et plus largement d’édition qui prennent la mesure du collectif sans l’unifier ou lui imposer une cohérence mais en valorisant les dynamiques dialogiques entre les fragments (l’édition des mots-clefs thématiques est un exemple). La logique anthologique dans cette perspective se fait donc par entités (terme utilisé dans l’API du projet) qui demeurent en écho sans être inter-dépendants. 

## La couronne graphique

Fondé sur cette idée de l’Anthologie comme corpus et donc comme ensemble dialogique, le projet du groupe 4 souhaitait refaire le lien avec un imaginaire justement à l’origine de l’objet de travail : l’imaginaire de la couronne (ἀνθολογία ou florilège en latin) qui réunit et tisse collectivement une série d’éléments comme des fleurs représentatifs d’une culture (celle de la littérature grecque pour le cas de l’Anthologie grecque) [@vitali-rosati_editorializing_2020]. Pouvoir montrer les liens au sein du corpus, et surtout les dynamiques d’inclusion et d’exclusion (est-ce que dans un livre où est représenté le thème de l’amour, le thème de la mort est également représenté ? le thème de l’argent y-est-il exclu ? est-ce que ce lien se fait au sein des mêmes épigrammes ou dans une vision plus diffuse au sein du livre ?) qui parcours le corpus et participent sans doute à établir une cohésion anthologique tout en démarquant cette anthologie d’autres structures narratives anthologiques. Ces visualisations (dont une qui correspond à un graphe et qui a donné le titre au livrable) devaient permettre, telles que décrites au cours du brainstorming de l’équipe, de structer des liens entre les données de l’Anthologie qui n’étaient ni directement visibles sur les plateformes du projet déjà existantes ni directement perceptibles par la lecture individuelle.

---

#### [encadré] la visualisation de données

La visualisation de données propose une représentation graphique de données. Pour créer une visualisation de données, il faut typiquement travailler avec des données sérielles, des éléments d’un jeu de données à étudier/comparer/analyser et choisir un critère qu’on va associer à une caractéristique graphique.
Exemples:

- Histogramme ou diagramme en barre: montrer graphiquement le nombre d’épigramme (quantité, à associer à la longueur d’une barre) pour chaque livre (on crée une barre par livre).

- *Scatterplot* ou diagramme de dispersion: inscrire les mot-clefs des épigrammes d’un livre sur dans un système de coordonnées cartésiennes. Dans l’axe x, on a le déroulement "chronologique" des épigrammes d’un livre, et en y la liste de mot-clefs. Pour chaque épigramme, on un point à son emplacement (x) de l’épigramme et à la hauteur du mot-clef en question. On peut ainsi visualiser les passages où les même mot-clefs sont employés (dans l’espace), le nombre d’occurences de chacun des mot-clefs (lecture horizontale sur la hauteur en y d’un mot-clef), ainsi que les mots-clef associés à un passage (lecture verticale à partir de l’emplacement en x du passage).

Les visualisations ou graphes en réseau (*graph network*) sont produites à partir de données structurées en nœuds et arrêtes. Les nœuds sont les points sur le réseau, et les arrêtes les liens entre les points. À la différence d’un digramme de dispersion par exemple, le placement des nœuds dans l’espace graphique n’est pas porteur de sens. On peut réorganiser un réseau sans changer sa signification intrinsèque, toutefois son organisation spatiale influence la lecture et l’interprétation du graphique.

---

Les données avec lesquelles nous avons souhaité travailler sont les suivantes :

- l’**Anthologie Grecque** en tant qu’un ensemble de livres ;
- les **livres** qui sont des ensembles d’épigrammes organisés de façon linéaire ;
- les **épigrammes** qui sont des entités textuelles — disponibles en plusieurs traductions — et auxquelles sont attribuées des mots-clefs ;
- les **mots-clefs** qui sont associés aux épigrammes selon une catégorisation (ensemble cohérent et thématique de mots-clés).

Il faut noter que les textes présents dans l’Anthologie Grecque sont nombreux : plus de 4 000 épigrammes avec parfois cinq traductions pour chacune. L’enjeu pour nous était donc de proposer une nouvelle façon de découvrir et de prendre la mesure de cette Anthologie. Le projet a été une première fois présenté à l’ensemble des participants du colloque avec pour objectif d’établir une lecture graphique *et* anthologique.

Deux approches complémentaires ont été proposées :

1. appréhender les livres qui composent l’Anthologie : **quels peuvent être les liens entre ces livres qui se composent chacun d’un nombre variable d’épigrammes ?** L’objectif est de visualiser les connexions entre les différents livres de l’Anthologie grâce aux mots-clefs qui sont associés à chaque épigramme (épigrammes qui composent les livres). En partant du nombre de mots-clefs que peuvent partager plusieurs livres, nous proposons de donner une visualisation graphique des relations entre ces livres de l’Anthologie Grecque, à travers la qualification des épigrammes.
2. saisir l’évolution du sens des épigrammes entre elles : **comment visualiser l’évolution du contenu des différentes épigrammes ?** Ces textes étant très nombreux, il est difficle de percevoir facilement et visuellement ce foisennement sémantique. Nous utilisons les mots-clefs associés aux épigrammes, et nous analysons plus particulièrement la variation de ceux-ci à l’intérieur d’un même livre. Les mots-clefs étant catégorisés (regroupement des termes selon des ensembles lexicaux organisés), les éditeurs et les éditrices ont une pratique relativement uniformisée d’attribution de mots-clefs. Il s’agit donc de visualiser les épigrammes d’un même livre selon les mots-clefs qui leur sont attribués.

Le projet a aussi été orienté par la sélection de graphiques dont le code est disponible et ouvert sur la plateforme Observable. Cette plateforme de notebooks a été sélectionnée car Lena s’en sert régulièrement pour la visualisation de données. Elle permet la collaboration en temps réel sur le code. Comme elle est hébergée en ligne <!--ça se dit??-->, les visualisations produites sont accessibles et visibles par tou·te·s, et peuvent être intégrées dans d’autres contenus web (en utilisant des iframes) comme dans cet article.

---

#### [encadré] les notebooks

Un notebook est un environnement de programmation dans lequel le code est structuré en cellules qu’on peut *run* <!--rouler? lance? --> individuellement. Contrairement à la programmation en scripts, le code pensé pour être segmenté, ce qui invite à une organisation différente des contenus. On peut notamment ajouter des cellues de texte pour ajouter des commentaires ou des explications sur le code.<!-- cependant, nous n’avons pas suffisamment fait usage de cette fonctionnalité (si on l’avait fait, on aurait eu plus d’informations sur la production de chaque graphique). Nous avons plutôt noté nos idées sur le papier, puis dans la documentation produite en live (sur hedgedoc).-->  On peut également « appeler » une cellule pour avoir accès à sa valeur, comme on appelerait une variable, et chaîner les actions ainsi. <!--désolée c’est mauvais, si quelque’un se sent de retravailler ça ce serait le bienvenu-->
Les notebooks [Observable](observablehq.com/) sont spécialisés pour la visualisation de données. Ils intègrent de nombreuses fonctionnalités qui facilitent et accompagnent la création de visualisations, notamment l’intégration des librairies Plot et D3.js. Plot, développée *in-house*<!--ou: à l’interne, par l’équipe Observable-->, prédéfinit des formats de visualisation pour lequels on doit simplement préciser la source de données et les paramètres (propriétés concernées, couleurs, ...).

---

En parcourant les exemples dans Observable (probablement avec une recherche par mot-clef dans l’outil de recherche intégré), nous avons identifié plusieurs formes visuelles qui pouvaient convenir aux données de l’API POP: 

- une [visualisation chronologique avec des arcs](https://observablehq.com/@bstaats/arc-diagram) (Stats 2018): chaque point représente un personnage des *Misérables*. Ils sont ordonné par ordre d’apparition. Les arcs représentent les interactions entre les personnages. 
- une [visualisation en graph qui montre le réseau des personnages dans STAR WARS](https://observablehq.com/@pthaden/d3-use-the-force-directed-graph) (Thaden 2018). Chaque point est un personnage et les liens représentent (je crois) leur co-occurences dans une scène. Les couleurs sont utilisées pour mettre en valeur les personnages principaux 
- un [diagramme de points *Scatterplot*](https://observablehq.com/@observablehq/pauls-observable-tips-tricks#cell-183) (Buffa 2022) produite avec la Librairie Plot. Dans cet exemple, les points sont placés en fonction de leur valeur sur l’axe X, et s’empilent les uns sur les autres selon l’affulence sur le point en X. La couleur est associée à une autre variable, et premet d’exprimer, dans le cas de ce graphique sur les œuvres d’art du MoMA, le médium de chaque œuvre de la collection.

### Idéation: dessin et design

Pour chacune de ces formes graphiques, il nous semblait que nous pourrions imaginer remplacer les données utilisées par celles de l’API POP. Nous avons donc commencé par faire un *fork* de ces graphiques pour regarder le code plus en détail, particulièrement le format des données employé pour créer la visualisation, et à effectuer certaines modifications pour observer si et comment pourraient être intégrées nos données. C’est à cette étape qu’a commencé le travail de conception des graphiques, un travail qui exige un certain niveau de connaissances sur les données de l’API ainsi qu’une approche *design* sur les formes visuelles à produire.

Deux modèles graphiques se sont précisés, au fil du travail collaboratif, jusqu’à leurs versions finales.

<img src="https://s3.hedgedoc.org/demo/uploads/dc305da3-5aee-4056-a79c-7ab21390d93c.jpg" alt="Figure 2. Visualisation ronde des livres en fonction des mots-clefs" style="zoom: 33%;" />

Dans ce premier dessin, nous avons utilisé une visualisation en réseau, fondée sur des nœuds et des arcs. Les nœuds sont des livres et les liens des passages qui ont le même mot-clef. Ainsi, des livres qui auraient des mot-clefs en commun se trouvent reliés, et l'épaisseur du trait peut indiquer l'intensité de ces thématiques communes.

<img src="https://s3.hedgedoc.org/demo/uploads/a1b6f71a-5632-4716-82e4-d3843d4e5ee6.jpg" alt="Figure 3. Visualisation en ligne des mots-clefs des épigrammes d’un même livre" style="zoom: 50%;" />

Ce second modèle graphique présente un livre comme une série de passage ordonnée. Chaque passage occupe une coordonnée en x, et l'axe y est faceté par mot-clef (une coordonnée en y par mot-clef). Ce modèle visualise, comme une lecture dirstante, les thématiques d'un livre par la présence et la fréquence des mot-clefs qui sont associés à chaque passage. Une lecture plus rapprochée invite à faire des corrélations entre les cooccurrences ou utilisations récurrentes de mot-clefs. L'association d'une couleur à chaque mot-clef, en plus de son emplacement sur l'axe y, facilite leur distinction visuelle.

## Les données

Pour visualiser des données, il faut commencer par parcourir les données et s'assurer de les 

- préparation des données
  - illusion que les données "sont prêtes" puisque l’API est là, documentée et avec pl
- "placer les données dans le fork du code existant"



### Restructuration des données
Lors du hackathon, chaque groupe était invité à récupérer (ou *fetch*) les données de l'API de la plateforme principale du projet et ce, dans l'idée de pouvoir les restructurer et travailler diverses visualisations. La [documentation](https://github.com/EcrituresNumeriques/2022-Hackathon-Navigations/blob/main/DOC/README.md) fournie dans le cadre de cette rencontre conseillait de procéder à la création d'un dépôt (ou *dump*) en local, soit sur les machines des utilisateurs, de toutes les épigrammes de l'Anthologie (décrites dans l'API comme des *passages*). Ce fonctionnement, qui pourrait sembler peu intuitif dans le cadre d'hackathons classiques dans les milieux des sciences informatiques, s'explique pour des questions d'accessibilité et de littéracie des participant·e·s de l'activités et au contexte interdisciplinaire de l'évènement. Connaissant la flexibilité de leur API mais également les possibles limites issues de la structuration des données, les organisateurs ont préféré, à la solution plus commune de donner accès au corpus aux participants au travers de requêtes, l'alternative du *dump* de l'API qui permettait davantage de liberté, d'autonomie mais également qui correspondait davantage à l'esprit d'exploration des données qui était à l'origine de la rencontre.
<!-- include article/brouillons -->

[…]

Le travail effectué à partir d’un miroir de l’API récupérée du projet a été l’occasion d’une connaissance approfondie mais également critique du projet. L’API incarne, dans la dimension technique du projet, une facette importante voir primordiale. Ainsi, la parcourir et l’explorer dans le cadre d’une réalisation éphémère a permis de découvrir le projet comme objet technique : d’observer comment l’idée de corpus, essentielle à la perspective de recherche, avait été techniquement implémentée au sein d’une structuration des données. En revanche, cette même exploration a amené le développement d’un regard critique sur les choix de structuration des données qui avait été fait. La réunion d’expertises et cultures diverses autour de cet objet qui concentre pour une majeure partie le travail d’édition numérique de l’Anthologie grecque a permit de souligner des failles ou tensions dans le projet (qui pour certaines avaient déjà été identifiées par les chercheurs du projet) et de questionner plus généralement les choix d’implémentation techniques. Cette perspective du travail collaboratif fait du hackathon non seulement un moment ludique et une occasion d’extension d’un projet déjà mature, mais également un espace-temps pour établir un dialogue critique avec un objet culturel.

--

#### [encadré] l’API

> [encadré]
> proposer une description et/ou exemple des données de l’API
> cliquer sur les ▶ pour voir le contenu

[À la racine de l’API](https://anthologiagraeca.org/api/)

<iframe width="100%" height="462" frameborder="0"
  src="https://observablehq.com/embed/7de89004c95e1067@80?cells=anthologyData"></iframe>

<!--Lena: ouin ok je pense que toute ma description de l’API doit aller plus loin dans le texte, après "la couronne graphique", mais du coup je ne sais pas quoi dire pour cette section -->
On peut voir que l’API est structurée par une arborescence, et qu’elle contient beaucoup de liens (URL) qui pointent vers une section de l’API. Cette organisation est logique au niveau informatique, puisqu’une machine peut aisément parcourir les liens et ainsi naviguer les contenus. Toutefois, en tant qu’utilisateur·rice·s de l’API lors du hackathon, cette structuration signifiait un travail plus long pour récupérer les données. <!-- une API orientée "utilisation" pourrait être moins stricte, elle contiendrait des informations redondantes (remettre le contenu au lieu de mettre un lien vers le contenu) mais offrirait un accès plus direct au contenu-->

On peut voir dans l’exemple de passage ci-dessous, premier élément du résultat retourné par la requête `https://anthologiagraeca.org/api/passages`, qu’il contient en valeurs <!--dure?--> son identifiant (`id`), le texte en plusieurs langues (`texts[n].text)`), mais les mots-clefs (`keywords`) continent uniquement l’URL.

[Exemple de passage](https://anthologiagraeca.org/api/passages)

<iframe width="100%" height="441" frameborder="0"
  src="https://observablehq.com/embed/7de89004c95e1067@81?cells=exemplePassage"></iframe>
<!--truc bizarre avec le book number, mathilde confirme que c’est normal mais c’est pas intelligible (trace de l’ancienne plateforme, à voir si on veut creuser cette piste ou non)-->

---

Nous étions intéressé·e·s par les mot-clefs, pour voir s’il y a des thématiques qui regroupent des passages par exemple. <!--pas très sûre, @Margot par exemple tu penses à autre chose pour ça? --> Quand on va sur l’URL du premier mot-clef de cet exemple (`https://anthologiagraeca.org/api/keywords/116/`), on comprend cette décision car les mot-clefs sont renseignés (`names`) et catégorisés (`categories`) en plusieurs langues. Toutefois, on y trouve également la liste des passages qui sont associés à ce mot-clef. On aurait donc pu inverser la logique et utiliser `https://anthologiagraeca.org/api/keywords/` pour parcourir les mot-clefs et les associer au fur et à mesure à des passages, mais nous n’avons pas considéré cette avenue. Cela vient probablement du fait que nous avions décidé de centrer le travail sur les passages, ceux-ci étant les éléments constitutifs de l’anthologie <!--l’anthologie est une collection de passages? -->

Pour obtenir les mots-clefs liés à un passage, il faut donc faire autant de requêtes qu’il y a de mots-clefs. Pour les obtenir pour l’ensemble des passages, il faut donc coder un algorithme qui parcourt la liste des passages et requête les valeurs sélectionnées pour chaque mot-clef. Toutefois, coder ce type de requêtes peut être chronophage, il faut notamment s’assurer qu’il n’y a pas d’erreurs ni d’oublis dans le code.



## Organisation du labeur pour l’après-midi

<!-- là c’est la partie où moi (Lena) j’ai dit que jếtais pas à l’aise de faire ça en javascript et depuis un notebook particulièrement, du coup quitte à sortir de l’environnement Observable on s’est dit (à mon souvenir) qu’on allait diviser le travail et qu’Enzo et Marianne seraient plus à l’aise de le faire en python, pendant que je me concentrais sur la préparation des viz, à commencer par identifier quel est le format de données dont on va avoir besoin en sortie-->



### Equipe données: Enzo et Marianne

<!--Cette partie est peut-être déjà dans ##Données-->

### Equipe dataviz: Lena et Margot

Nous avons renoncé au graphique en arcs car nous n'étions pas sûr·e·s de ce que nous pourrions représenter par les arcs. 



 #### graph des livres

- enjeux des données: comprendre comment créer les nœuds et les liens

#### livre 5

format de données en exemple (drôles d'exemples)

```json
keywords = [
  {name: "chat", ordre:"5.0", cat:"domestique", url: "https://anthologiagraeca.org/passages/urn:cts:greekLit:tlg7000.tlg001.ag:5.3/"},
  {name: "chien", ordre:"5.23", cat:"domestique", url: "https://anthologiagraeca.org/passages/urn:cts:greekLit:tlg7000.tlg001.ag:5.3/"},  
  {name: "baleine", ordre:"5.117", cat:"océan", url: "https://anthologiagraeca.org/passages/urn:cts:greekLit:tlg7000.tlg001.ag:5.3/"},
  {name: "cheval", ordre:"5.250", cat:"loisir", url: "https://anthologiagraeca.org/passages/urn:cts:greekLit:tlg7000.tlg001.ag:5.3/"},
]
```



#### Erreurs, hésitations et complexté







### Equipe documentation: Margot et Antoine



## Fin?

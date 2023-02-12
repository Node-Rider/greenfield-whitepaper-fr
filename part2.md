## Partie 2 : Les Showcases des labs

## Table des matières

- [9 Showcases : Stockage décentralisé](#9-Showcases--stockage-décentralisé)
  - [9.1 Hébergement web et disque cloud personnel](#91-hébergement-web-et-personal-cloud-drive)
  - [9.2 Couche de disponibilité des données pour la blockchain publique](#92-couche-de-disponibilité-des-données-pour-la-blockchain-publique)
    - [9.2.1 Couche 1 de la Blockchain pour l'échange de données](#921-échange-de-données-de-blockchain-de-couche-1)
    - [9.2.2 Couche de disponibilité des données pour les rollups de la couche 2](#922-couche-de-disponibilité-des-données-pour-les-rollups-de-couche-2)
    - [9.2.3 Instantanés et sauvegardes de données par blocs](#923-instantanés-et-sauvegardes-de-données-en-bloc)
- [10 Showcases : Nouvelles méthodes de publication numérique](#10-Showcases--les-nouveaux-modes-dédition-numérique)
  - [10.1 Grass-Root Digital Publishing](#101-lédition-numérique-de-base)
  - [10.2 Marché des données](#102-marché-des-données)
  - [10.3 Risque : Anti-piratage](#103-risque--anti-piratage)
- [11 Showcases : Contenu généré par l'utilisateur](#11-Showcases--contenu-généré-par-lutilisateur)
  - [11.1 Anti-monopole et anti-censure](#111-anti-monopole-et-anti-censure)
  - [11.2 Token Curated Registries](#112-registres-créés-par-les-jetons)
- [12 Showcases : marché des données personnelles](#12-Showcases--marché-des-données-personnelles)
- [13 Des Showcases à la production réelle](#13-des-Showcases-à-la-production-réelle)

L'objectif de la plateforme BNB Greenfield est de libérer la puissance de la blockchain décentralisée et de la technologie de stockage en matière de propriété des données et d'économie des données.

Cette partie du livre blanc n'est ni précise en tant que dessins industriels ni sérieuse en tant que recherche universitaire. Elle énumère simplement
quelques présentations potentielles qui peuvent être modelées sur BNB Greenfield dans un "environnement de laboratoire". Ces exemples sont utilisées pour
inspirer de nouvelles expérimentations et une conception solide pour créer la prochaine génération d'applications décentralisées.

## 9 Showcases : Stockage décentralisé

BNB Greenfield devrait tout d'abord être une infrastructure de stockage décentralisé pratique avec une qualité de service décente.

### 9.1 Hébergement Web et Personal Cloud Drive

Étant donné que GreenField fournit des API et des concepts très similaires à AWS S3, il n'est pas difficile pour les utilisateurs d'y déployer facilement leurs sites Web et de gérer la facturation via le BNB.

Grâce à une application client sophistiquée, les utilisateurs peuvent également créer leur propre disque réseau avec leur adresse. Ils peuvent charger et télécharger des fichiers, des photos et des vidéos via leur ordinateur de bureau et leurs appareils mobiles, classer ces données dans différents dossiers. Les données peuvent être cryptées avec leurs clés privées et l'accès peut être limité à eux-mêmes.

Une bonne caractéristique de Greenfield en tant que stockage dans le cloud est qu'il permet le stockage de données sponsorisé par la communauté. Le propriétaire des données peut rendre un objet public, tandis que d'autres utilisateurs peuvent parrainer le stockage et télécharger via la bande passante
comme ils le souhaitent. Ce n'est pas quelque chose qui peut être fait facilement avec les fournisseurs de clouds centralisés actuels. Des miroirs de logiciels libres peuvent être mis en place sur Greenfield. Les sites Web à vocation sociale peuvent être gérés plus facilement.

### 9.2 Couche de disponibilité des données pour la blockchain publique

La couche de disponibilité des données est un sujet brûlant en 2022 pour plusieurs raisons :

1. Les données de la couche 1, à la fois les données des blocs et les données d'état, se sont trop accumulées;

2. Les solutions de rollup de la couche 2 nécessitent un stockage à faible coût, sans confiance ou presque, pour les données de rollup;

3. les blockchains modulaires espèrent qu'une couche de données autonome peut augmenter la capacité totale.

#### 9.2.1 Échange de données de blockchain de couche 1

L'écosystème de la chaîne BNB, notamment la BSC elle-même, s'intéresse particulièrement aux couches 1 et 2. Parmi toutes les blockchains publiques générales, la BSC est la plus grande blockchain informatique en termes de données d'état, d'adresses uniques, de contrats intelligents, de transactions totales et d'utilisateurs actifs quotidiens. Le total des données historiques de la BSC dépassaient déjà plusieurs dizaines de téraoctets en 2022. Parmi toutes ces données, certaines sont périmées, mortes ou dormantes. Elles ne seront jamais utilisées ou ne le seront que dans de rares cas. Elles ne devraient pas toujours occuper de l'espace avec d'autres données actives ou exercer une pression sur les performances.

À l'instar des systèmes d'exploitation des PC modernes, ces données périmées doivent être transférées vers un stockage à long terme moins coûteux, tel que Greenfield. Des transactions spéciales, des codes d'opération EVM et l'économie correspondante peuvent être introduits pour obtenir un consensus sur l'échange des données. Lorsqu'un utilisateur ou un contrat intelligent veut opérer sur ces données échangées, une erreur de "défaut de page" sera déclenchée et les utilisateurs devront explicitement échanger les données de Greenfield vers la BSC. Ces idées sont déjà prises en compte par la BSC Core Dev.

#### 9.2.2 Couche de disponibilité des données pour les rollups de couche 2

Tout comme Ethereum, la BSC accueille également les rollups de couche 2 comme la solution pour faire évoluer la puissance de calcul totale et la taille du ledger. Le stockage des données sur la BSC est moins cher que sur Ethereum, mais cela peut être beaucoup plus efficace s'il existe une infrastructure de stockage commune fiable et vérifiable. Une telle infrastructure et la gestion correspondante de la couche de disponibilité des données peuvent
réduire considérablement le coût des rollups.

#### 9.2.3 Instantanés et sauvegardes de données en bloc

Le stockage des données à long terme n'était pas un sujet sérieusement envisagé lors de l'invention de la blockchain. Cependant, c'est devenu un
problème aujourd'hui. La plupart des développeurs préfèrent exécuter un nœud de blockchain à partir d'un instantané, plutôt que de l'exécuter à partir de sa genèse. De nombreux réseaux, dont Ethereum, ont fait des recherches pour que les blocs et les données historiques qui existent depuis plus d'un certain temps devraient être autorisés à tomber. La communauté a besoin d'une source de données publiquement accessible et crédible pour lire ces données très anciennes et ces instantanés récents. BNB Greenfield peut être une bonne option. Sa fonction de parrainage est naturelle pour ces données de
bien social.

## 10 Showcases : Les nouveaux modes d'édition numérique

L'édition numérique est aujourd'hui une industrie mature. Les e-books, les jeux, la musique, les longues vidéo en streaming, et les clips courts sont tous très courants et largement acceptés par les auteurs et les consommateurs grand public.

Les deux exemples ci-dessous montrent comment l'écosystème Greenfield de BNB peut aider ce secteur.

### 10.1 L'édition numérique de base

Sans parler de l'édition professionnelle, même l'édition amateur peuvent être très formelles et lourdes. Pour certains créateurs ou auteurs de base, leurs œuvres ne sont que des insuccès aux yeux des éditeurs traditionnels ou même sur Internet et ne valent pas la peine d'être couvertes.

Avec Greenfield et la BSC, tout auteur amateur peut stocker ses œuvres sur Greenfield et les mettre en miroir sur la BSC. Ils peuvent vendre leurs œuvres sur un marché de la BSC, et le marché peut automatiquement accorder les permissions de lecture aux adresses des acheteurs après qu'ils aient payé. Les auteurs n'ont pas besoin d’intermédiaires tels les éditeurs, ils n'ont qu'à effectuer quelques clics sur une dApp et à gérer leur (petite) communauté.

### 10.2 Marché des données

Ce marché est très similaire à celui de l'édition numérique. Mais il s'étend à tout type de données en dehors des arts numériques, comme les statistiques historiques pour certains domaines, les données d'expériences scientifiques, etc.

Avec Greenfield, certains marchés basés sur les NFT sur la BSC peuvent devenir un "Ebay" des données.

### 10.3 Risque : Anti-piratage

La conception actuelle de Greenfield n'a aucune protection anti-piratage. Une fois que l'adresse a obtenu l'autorisation de lecture, elle peut télécharger les données et les distribuer à quiconque, que ce soit à des fins lucratives ou non. Certains des mécanismes de DRM peuvent encore fonctionner, mais beaucoup ne fonctionneront pas.

Cependant, en tant qu'infrastructure publique et décentralisée, elle fournit naturellement un historique vérifiable des données, avec contenu, signature,
les horodatages et les sommes de contrôle. Cela aide beaucoup à fournir des preuves pour le litige sur le droit d'auteur.

Les auteurs, les éditeurs et les dApps doivent être conscients de ces limites et choisir de les utiliser à leurs propres risques pour le moment. D'autres fonctionnalités liées au droit d'auteur pourraient être introduites dans Greenfield avec l'aide de la communauté.

## 11 Showcases : Contenu généré par l'utilisateur

### 11.1 Anti-monopole et anti-censure

Il y a un métier qui bénéficie le plus du développement des médias sociaux : Les leaders d'opinion, alias KOLs. Ils publient des opinions, des articles,
des vidéos et des œuvres musicales qui plaisent, influencent et inspirent les gens. Les KOLs créent leur propre fandom et peuvent faire fortune en utilisant l'attention et le trafic de leurs fans.

Cependant, il y a un talon d'Achille pour ces KoL : ils ne peuvent pas être propriétaires de leurs données et de leurs relations avec les fans si les plates-formes ne sont pas en mesure de leur fournir les informations nécessaires. Nous savons tous que vous ne pouvez rien y changer, même si vous êtes le président du pays le plus puissant du monde.

BNB Greenfield fournit une infrastructure pratique pour faire en sorte que les données soient entièrement la propriété des créateurs. Pendant ce temps, les dApps peuvent toujours utiliser ces données, les publier à l'intention du public et entretenir le réseau social. De plus, même la relation de fandom ou le graphique du réseau social peut être sauvegardé sur Greenfield comme un type données appartenant aux utilisateurs. Il n'y a pas d'entreprise unique qui peut bloquer l'accès aux données. Les dApps fournissent simplement des interfaces et des outils pratiques pour faciliter la création et la propagation.

Un autre grand avantage de Greenfield est qu'il permet de créer facilement des fandoms privés en utilisant les fonctions de groupe. Par exemple, un KOL peut créer un groupe spécial pour un fandom particulier. Ce groupe peut être uniquement géré par un contrat intelligent sur la BSC et n'autoriser que les adresses à rejoindre sur la base d'informations spéciales, comme la détention d'un certain jeton ou le paiement d'un abonnement. Tous ces éléments sont faciles à mettre en œuvre avec Greenfield.

### 11.2 Registre de listes décentralisées

[Registre de listes dites décentralisées] (https://hackernoon.com/what-are-token-curated-registries-and-decentralized-lists-d33fa42ba167) ont été largement discutés et étudiés en 2018. Mais ils n'ont pas acquis une grande reconnaissance dans les cas d'utilisation réels. L'une des raisons peut être qu'il est difficile et coûteux de sauvegarder les différentes listes et de les présenter de manière crédible.

BNB Greenfield offre une solution parfaite pour les listes établies à l'aide de jetons. Un contrat intelligent sur la BSC peut supporter toute la gouvernance et la logique d'incitation de l'enregistrement, et possède en même temps les droits de créer des objets de chaque liste sous le bucket désigné pour l'entreprise. La liste d'objets et l'historique complet des changements sont des fonctions inestimables pour de telles idées de vote et de gouvernance décentralisés.

## 12 Showcases : Marché des données personnelles

Il s'agit peut-être du problème le plus compliqué à résoudre de nos jours : comment s'approprier vos données, telles que les pages vues, les inscriptions, les clics, les données comportementales, etc. et bien plus encore. La propriété garantit qu'aucune plateforme (généralement les
monopole) ne puisse en abuser. De nombreuses lois sont définies pour punir l'utilisation abusive, mais il existe peu de solutions proactives.

BNB Greenfield propose de nouveaux angles d'attaque pour résoudre ce problème : et si vous pouviez demander aux applications de stocker toutes vos données cryptées sur Greenfield sous votre compte, et de ne permettre le traitement de vos données que via un code lisible par le public ?

Examinons un scénario spécifique. Un marché de données stocke vos ordres d'achat et de vente passés sur Greenfield, cryptés par la clé publique de votre compte. Seul votre clé privée peut le décrypter et le lire. Cependant, l'application du marché de données aimerait lire vos données pour recommander d'autres articles, pendant ce temps, une autre agence de données aimerait utiliser ces données pour effectuer des recherches commerciales. Les deux sont prêts à vous payer pour le traitement de vos données. Vous avez tendance à leur accorder l'autorisation de lire
les données, mais vous craignez qu'elles ne fassent autre chose avec vos données. Comment BNB Greenfield peut-elle résoudre ce problème ?

Il ne s'agit peut-être pas d'une mise en œuvre au jour le jour, mais BNB Greenfield vise à résoudre ce problème de confiance informatique en fournissant un runtime informatique vérifiable ("do not trust, verify").

Dans le scénario ci-dessus, l'application de marché de données et l'agence de données peuvent placer les programmes qui ont besoin de lire les données des utilisateurs sur Greenfield et les partager avec vous ou même avec le grand public. Vous pouvez vérifier si vous êtes à l'aise avec ce que font les programmes. Ensuite, vous accordez la permission de lecture de ce nouvel objet avec un "[orienté groupe](https://onlinelibrary.wiley.com/doi/epdf/10.1002/sec.1593)" à ces programmes. Le marché des données et l'agence de données peuvent vous payer et exécuteront alors ces programmes pour obtenir le résultat sur un sandbox vérifiable du runtime de Greenfield.

Une fois ce modèle compris, de nombreuses améliorations peuvent être apportées par le biais de la cryptographie moderne pour améliorer l'expérience de l'utilisateur.

Par exemple, l'accord peut être négocié à l'avance entre vous et le marché des données. Ainsi, l'octroi de l'autorisation et l'échange des avantages économiques correspondants peuvent se faire dans le cadre d'un contrat intelligent afin de réduire la confiance nécessaire. Une fois l'accord conclu, les données seront sauvegardées via un cryptage basé sur BLS à partir du moment où elles sont générées. Soit le propriétaire des données ou les programmes du marché des données approuvés par le propriétaire des données (pas le propriétaire du marché des données) peuvent, et seulement, accéder aux données.

De nombreuses autres infrastructures liées au scénario ci-dessus ne sont pas encore prises en compte dans ce document, mais elles peuvent être
progressivement conçues et mises en œuvre sur BNB Greenfield.

## 13 Des Showcases à la production réelle

Différents exemples, ont été abordées dans la partie 2 de ce document. Certains d'entre eux peuvent valoir la peine d'être mises en œuvre dans une application réelle, mais d'autres sont censées inspirer de nouveaux modèles à inventer, pour libérer la puissance de BNB Greenfield. Cette partie du document devrait bientôt être remplacée par des applications réelles en production.

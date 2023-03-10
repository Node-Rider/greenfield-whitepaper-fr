# Partie 1 Conception de GreenField et de l'économie de stockage décentralisée

## Table des matières

- [1 Principes de conception](#1-principes-de-conception)
- [2 Hypothèses](#2-hypothèses)
- [3 L'architecture en général](#3-larchitecture-en-général)
  - [3.1 Noyau GreenField](#31-noyau-greenfield)
  - [3.2 Applications Greenfield de BNB](#32-les-dapps-de-bnb-greenfield)
  - [3.3 La chaîne croisée avec BSC](#33-la-chaîne-croisée-avec-bsc)
  - [3.4 La trinité](#34-la-trinité)
- [4 Noyau Greenfield BNB](#4-noyau-de-bnb-greenfield)
  - [4.1 La blockchain Greenfield de BNB](#41-la-blockchain-bnb-greenfield)
  - [4.2 Les fournisseurs de stockage](#42-les-fournisseurs-de-stockage-sp)
  - [4.3 La synergie des paires](#34-la-trinité)
- [5 Le stockage des données Greenfield](#5-le-stockage-des-données-de-greenfield)
  - [5.1 Données avec consensus](#51-données-avec-consensus)
    - [5.1.1 Comptes et solde](#511-comptes-et-solde)
    - [5.1.2 Métadonnées du validateur et de la FS](#512-métadonnées-du-validateur-et-du-ps)
    - [5.1.3 Métadonnées de stockage](#513-métadonnées-de-stockage)
    - [5.1.4 Métadonnées de permission](#514-métadonnées-dautorisation)
    - [5.1.5 Métadonnées de facturation](#515-métadonnées-de-facturation)
  - [5.2 Stockage des données des objets de données utiles hors chaîne](#52-stockage-des-données-utiles-de-lobjet-hors-chaîne)
    - [5.2.1 FS primaires et secondaires](#521-fournisseurs-de-stockage-primaires-et-secondaires)
    - [5.2.2 Redondance des données](#522-redondance-des-données)
- [6 Économie du stockage et ses primitives](#6-économie-du-stockage-et-ses-primitives)
  - [6.1 Création de compte](#61-création-de-compte)
  - [6.2 Création d'objets de données](#62-création-dobjets-de-données)
  - [6.3 Stockage des données](#63-stockage-des-données)
  - [6.4 Lecture et téléchargement des données](#64-lecture-et-téléchargement-de-données)
  - [6.5 Permissions et Groupe](#65-permissions-et-groupes)
  - [6.6 Frais et paiements](#66-fees-and-payments)
  - [6.7 Défi d'intégrité et de disponibilité des données](#67-défi-de-lintégrité-et-de-la-disponibilité-des-données)
  - [6.8 Suppression des données](#68-suppression-de-données)
- [7 Économie des actifs de données](#7-économie-des-actifs-de-données)
  - [7.1 Cross chains avec BSC](#71-cross-chains-avec-bsc)
  - [7.2 Framework](#72-framework)
  - [7.3 Couche de communication](#73-couche-de-communicationla-couche-de-communication-est-composée-dun-ensemble-de-relais-greenfield)
  - [7.4 Couche miroir de ressources](#74-couche-miroir-de-ressources)
    - [7.4.1 Miroir d'entité de ressource](#741-miroir-dentité-de-ressource)
    - [7.4.2 Primitives de fonctionnement inter-chaînes](#742-primitives-dexploitation-inter-chaînes)
- [8 "Pas" de fin pour la conception](#8-pas-de-fin-pour-la-conception)
  - [8.1 Remerciements](#81-Remerciements)

La partie 1 décrit les principes généraux et les considérations relatives à la conception BNB Greenfield. Elle couvre l'architecture
et l'analyse des fonctionnalités. Bien que la véritable innovation du modèle se situe au niveau de l'inter-chaîne avec la BSC, il est également important de souligner les principes fondamentaux du stockage unique.

## 1 Principes de conception

1. **Simplicité** - La conception privilégie ce premier principe par rapport aux autres considérations. Les solutions simples sont non seulement
   faciles à mettre en œuvre, à exécuter, à maintenir et à étendre, mais aussi favorables aux performances logiciels, qui est un objectif principal de        la conception. Par exemple, une preuve à forte intensité de calcul, comme celle adoptée par [Filecoin] (https://filecoin.io/filecoin.pdf),
   est exclue selon ce principe.

2. **Améliorable et en constante évolution** - Un système parfait en une seule fois n'est pas l'objectif de la conception. Nous nous attendons à ce que      l'ensemble de l'architecture, les différents composants, et même ce livre blanc, évoluent et soient améliorés en fonction des réactions de la              communauté et du marché ainsi que des futurs développements technologiques. L'infrastructure devrait avoir une constitution "suffisante" pour
   se développer et se mettre à niveau au fil du temps.

3. **Plate-forme ouverte** - La plus grande leçon tirée de l'industrie de la cryptographie et de l'écosystème BNB est que la communauté a le plus de          talent et de pouvoir pour construire plus d'applications et d'infrastructures de différentes manières en autonomie. La conception devrait se concentrer    sur la plateforme de base et les fondations techniques qui fournissent suffisamment d'interface, d'outils et d'autres facilités à la communauté des        développeurs pour qu'ils puissent créer des applications et des infrastructures.

4. **Adoption massive** - L'économie vise non seulement les clients actuels de la chaîne BNB chaîne, mais aussi les utilisateurs et les développeurs          traditionnels du Web2. La conception du système doit essayer d'être aussi compatible que possible avec les normes populaires du Web2 et du Web3.

5. **La décentralisation est un voyage** - Prenons l'exemple du système de stockage, il y a deux extrémités au spectre de la décentralisation. D'un côté,    les utilisateurs doivent créer et stocker toutes leurs données auprès d'un seul fournisseur de services. Et de l'autre extrémité, les utilisateurs        peuvent créer et stocker leurs données sur le terminal informatique de n'importe quel foyer (il ne doit même pas s'agir d'un bureau). La conception ne    s'imposera pas dès le départ sur ce dernier point. Elle choisit la solution la plus simple qui fait avancer l'aiguille vers une plus grande                décentralisation et qui s'améliorera au fil du temps. En ce sens, la première étape de Greenfield consiste à offrir la liberté de choisir parmi une        multitude de fournisseurs de services à tout moment, avec des coûts insignifiants car ils possèdent les données.

<div align="center"><img src="./assets/1%20Decentralization%20Spectrum.png" height="80%" width="80%"></div>
<div align="center"><i>Figure 1.1: Decentralization Spectrum</i></div>

## 2 Hypothèses

La plus grande hypothèse pour la conception est :

***Greenfield est un écosystème économiquement durable, orienté vers les services.***

Par "autonome", on entend que les fournisseurs et les consommateurs de services de Greenfield sont rationnels ; ils se
se complètent mutuellement. Les fournisseurs et les validateurs de la blockchain seront payés équitablement pour le service qu'ils fournissent, tandis que les utilisateurs sont prêts à payer pour le service qu'ils utilisent.

Par "orienté service", cela signifie que la valeur a été créée au sein de Greenfield en fournissant un service aux utilisateurs de l'écosystème. Il n'y a pas de valeur intrinsèque en soi.

L'hypothèse implicite qui sous-tend ces deux traits est que la majorité des fournisseurs et des validateurs de blockchain sont des entités et des individus raisonnables. Ils ne feront pas le mal étant donné que le profit qu'ils gagnent est plus grand que la fortune qu'ils peuvent piller.

Il s'agit d'une confiance auto-justifiable pour que l'ensemble de l'écosystème existe : si un pourcentage substantiel de fournisseurs et de validateurs de blockchain font le mal et que l'écosystème ne peut pas se guérir en éliminant ces acteurs malveillants, l'ensemble de l'écosystème ne sera pas en mesure d'exister. Si cela se produit, personne ne gagne, même pour une courte période.

Avec cette confiance implicite intégrée, de nombreuses conceptions sont simplifiées.
comme décrit dans les sections suivantes.

Une autre hypothèse est que tant le fournisseur de services que le consommateur s'attendraient à ce que les "contrats de service" réels entre les deux permettent une responsabilité limitée et offrent des options de sortie, même si les contrats sont essentiellement exécutés par du code. Dans l'intérêt des consommateurs, ils ne veulent pas payer d'emblée une somme importante et souhaiteraient pouvoir choisir un meilleur fournisseur au sein des écosystèmes ou même en dehors quand ils le souhaitent. De l'autre côté, dans l'intérêt des fournisseurs de services, ils ne veulent pas devenir une poubelle de données ou aider à faire circuler du contenu contre leurs propres principes.

Le paiement, la vérification de la disponibilité des données et quelques autres fonctions clés sont conçus sur la base de cette hypothèse.

La dernière grande hypothèse est que les données ont une valeur et que les utilisateurs voudront extraire cette valeur grâce à l'automatisation des contrats intelligents, à la confidentialité et à la transparence. Cela se traduit par une conception considérable de l'inter-chaîne entre BNB Greenfield et BNB Smart Chain (BSC). Cela devrait être l'hypothèse la plus importante et, espérons-le, proche de la vérité.

## 3 L'architecture en général

<div align="center"><img src="./assets/3%20Greenfield%20Economy%20General%20Architecture.png"></div>
<div align="center"><i>Figure 3.1: Architecture générale de l'économie Greenfield</i></div>

L'écosystème de Greenfield est une "trinité" comme le montre la figure ci-dessus.

### 3.1 Noyau GreenField

Le noyau GreenField est la nouvelle infrastructure du système décrite en profondeur
dans ce document. Il est le centre du nouvel écosystème de données. Il comporte deux
couches.

1. Une nouvelle blockchain orientée stockage, et

2. Un réseau composé de "fournisseurs de stockage".

La blockchain BNB Greenfield maintient le registre pour les utilisateurs et les métadonnées de stockage comme données d'état communes de la blockchain. Elle dispose du BNB, transféré de la BNB Smart Chain, comme son jeton natif pour le gaz et la gouvernance. La blockchain BNB Greenfield blockchain a aussi sa propre logique de staking pour la gouvernance.

Les fournisseurs de stockage (FS) sont des infrastructures de services de stockage que les organisations ou individus fournissent et les rôles correspondants qu'ils jouent. Ils utilisent Greenfield comme grand livre de comptes et comme source unique de vérité. Chaque fournisseur de services de stockage peut répondre et répondra aux demandes des utilisateurs pour écrire (Envoyer) et lire (télécharger) des données, en servant de gardien des droits et authentifications des utilisateurs.

Dans un premier temps, un certain nombre de validateurs, gérés soit par la communauté BNB, soit par des FS, se lancent dans la genèse de BNB Greenfield,  tandis que quelques prestataires de services lanceront également l'infrastructure de stockage correspondante et s'inscriront sur la blockchain Greenfield. Les FS forment un autre réseau P2P pour fournir un ensemble complet de fonctionnalités aux applications et aux utilisateurs afin de créer,
stocker, lire et échanger des données tout en utilisant la blockchain Greenfield comme la couche de métadonnées et du registre.

<div align="center"><img src="./assets/3.2%20BNB%20Greenfield%20Core.jpg"></div>
<div align="center"><i>Figure 3.2: Noyau GreenField</i></div>

La blockchain BNB Greenfield et les Fournisseurs de Stockage constituent ensemble le centre de cette nouvelle économie, qui est en fait un système de stockage d'objets décentralisés (avec une connectivité EVM comme expliqué plus loin).

Contrairement à l'alternative centralisée, ce système de stockage d'objets gère ses données en deux parties collaboratives, on-chain et off-chain.

La blockchain Greenfield contient deux catégories d'états "on-chain" :

1. Les comptes et leur registres de solde BNB

2. Les métadonnées du système de stockage d'objets et des FS, les métadonnées des objets stockés sur ce système de stockage, et les informations de          permission et de facturation associées à ce système de stockage.

Les transactions de la blockchain Greenfield peuvent modifier les états ci-dessus. Ces états et les transactions constituent les principales données économiques de BNB Greenfield.

Alors que les métadonnées sont stockées sur la chaîne (on-chain), le système de stockage d'objets stocke toutes les données relatives au contenu de l'objet (la charge utile) en dehors de la chaîne (off-chain), plus précisément sur les systèmes off-chain des prestataires de services , de manière décentralisée et redondante.

Lorsque les utilisateurs veulent créer et utiliser les données sur Greenfield, ils peuvent interagir avec l'Infrastructure Centrale de BNB Greenfield par l'intermédiaire des dApps de BNB Greenfield (applications décentralisées).

### 3.2 Les dApps de BNB Greenfield

Les dApps de BNB Greenfield sont de nouveaux types d'applications décentralisées. Elles peuvent être les outils clients qui facilitent l'interaction des utilisateurs avec le système de stockage décentralisé, le Noyau GreenField Infra; ou des applications qui apportent de la valeur à la vie réelle des utilisateurs en utilisant les systèmes Greenfield comme leur infrastructure. Ces applications utiliseront les adresses blockchain comme identifiants d'utilisateur et interagiront avec les fonctionnalités et les contrats intelligents sur la blockchain Greenfield, les FS Greenfield et la BSC.

Il existe des terminaux de données, des interfaces de transaction, des réseaux P2P et des kits de développement logiciel (SDK) correspondants pour aider les développeurs à créer des dApps sur BNB Greenfield.

Les dApps BNB Greenfield devraient faire partie de la création de l'infrastructure de la BNB Chain construite principalement par la communauté et les partenaires de l'écosystème. Elles peuvent être décentralisées ou centralisées, selon leurs préférences.

La partie 2 présente les considérations à travers une liste de dApps BNB Greenfield.

### 3.3 L'Inter-chaîne avec la BSC

Il existe un pont natif inter-chaînes entre la BSC et la blockchain BNB Greenfield. Alors que les données peuvent être créées et lues de manière plus économique sur le Noyau GreenField Infra, l'opération concernée des données peut être transférée à la BSC et être intégrées aux systèmes de contrats intelligents, tels que la DeFi, pour créer de nouveaux modèles commerciaux.

### 3.4 La trinité

Du point de vue des dApps de BNB Greenfield, ces applications peuvent aider les utilisateurs à créer, lire et exécuter des données sur la BNB Greenfield,
les Fournisseurs de Stockage, la BSC, et répondre aux besoins des utilisateurs.

Du point de vue de l'Infrastructure Centrale de BNB Greenfield, elles acceptent les demandes et les observations des dApps Greenfield au nom des utilisateurs, ainsi que les instructions de la BSC pour qu'ils fonctionnent ensemble au travers de différents scénarios commerciaux.

Du point de vue de la BSC, elles peuvent accepter les actifs de données transférés de la BNB Greenfield, et fournir davantage de services commerciaux via des contrats intelligents, et ce, à de nouveaux types de dApps Greenfield.

Les utilisateurs peuvent interagir avec toutes les parties de la trinité à différentes fins, directement ou indirectement.

## 4 Noyau de BNB Greenfield

### 4.1 La blockchain BNB Greenfield

La blockchain BNB Greenfield utilise le Proof-of-Stake basée sur le consensus Tendermint-consensus pour la sécurité de son propre réseau. Les blocs sont créés toutes les 2 secondes sur la chaîne Greenfield par un groupe de validateurs.

Le BNB sera le jeton de gaz et de gouvernance sur cette blockchain. Il existe un pont inter-chaîne natif entre la blockchain Greenfield et la BSC. Le BNB initial sera verrouillé sur la BSC et ré-imprimé (re-mint) sur Greenfield. Le BNB et les opération primitives de données peuvent circuler entre Greenfield et la BSC.

La quantité totale de BNB en circulation restera inchangée, mais circulera entre la BNB Beacon Chain, la BSC et Greenfield.

L'élection et la gouvernance du validateur sont basées sur un mécanisme de proposition et de vote, qui est révisé sur la base du module de gouvernance de Cosmos SDK :
Tout le monde peut créer et proposer de devenir un validateur, et l'élection dans l'ensemble des actifs sera basée sur le classement de staking (initialement les nouveaux validateurs peuvent demander les votes de l'ensemble des validateurs existants pour être qualifiés pour l'élection). Comme les validateurs hébergeront toutes les métadonnées critiques et répondront à toutes les transactions d'opérations de données, ils doivent fonctionner de manière professionnels en termes de performances et de stabilité.

Pour faciliter les opérations inter-chaînes et la gestion des actifs, le format d'adresse de la blockchain Greenfield sera entièrement compatible avec la
avec la BSC (et Ethereum). Il accepte également la signature et la vérification des transactions EIP712. Ces éléments permettent à l'infrastructure des portefeuilles existants d'interagir avec Greenfield dès le début et naturellement.

### 4.2 Les fournisseurs de stockage (FS)

Les fournisseurs de stockage jouent un rôle différent de celui des validateurs Greenfield, bien que les mêmes organisations ou individus puissent gérer les deux s'ils suivent toutes les règles et procédures pour être élus.

Les FS stockent les données réelles des objets, c'est-à-dire les données utiles. Chaque FS gère son propre système de stockage d'objets. Semblable à Amazon S3 et d'autres systèmes de stockage d'objets, les objets stockés sur les FS sont immuables. Les utilisateurs peuvent supprimer et recréer l'objet (sous un autre identifiant ou une autre forme, ou sous le même identifiant après certains réglages déclarés publiquement), mais ils ne peuvent pas le modifier.

Les prestataires de services doivent d'abord s'enregistrer en déposant sur la blockchain Greenfield comme leur "Service Stake". Les validateurs Greenfield passeront par une procédure de gouvernance dédiée pour voter pour les FS de leur élection. Les prestataires de services sont encouragés à faire de la publicité pour leurs informations et à prouver à la communauté leurs capacités, car ils doivent fournir un  système de stockage professionnel avec un SLA de haute qualité.

Les prestataires de services fournissent des API accessibles au public pour que les utilisateurs puissent charger, télécharger et gérer les données. Ces API sont très similaires aux API d'Amazon S3, de sorte que les développeurs existants peuvent se sentir suffisamment familiers pour coder des applications de stockage. En attendant, ils se fournissent mutuellement des API REST et constituent un autre réseau P2P en liste blanche pour communiquer entre eux et garantir la disponibilité et la redondance des données. Il y aura également un réseau P2P entre les FS et le logiciel client de l'utilisateur pour faciliter les connexions et les téléchargements rapides.

## 5 Le stockage des données de Greenfield

Les données stockées sur Greenfield ont deux catégories principales :

1. les données avec consensus blockchain - Ce sont les données blockchain Greenfield.
   Tous les validateurs Greenfield disposent de ces données actives dans leur intégralité (au moins le dernier état).
   Tout le monde peut rejoindre la blockchain en tant que nœuds complets pour synchroniser ces données gratuitement.

2. les données utiles des objets - en abrégé, les données des objets. Il s'agit des données que les utilisateurs stockent sur Greenfield.
   Ces données sont soumises à un contrôle d'accès et leur stockage est payant.
   Elles ne sont pas stockées sur la blockchain mais sur un nombre suffisant d'instances de Fournisseurs de Stockage hors-chaîne.

### 5.1 Données avec consensus

Ces données sont sur la blockchain et ne peuvent être modifiées que par des transactions sur la blockchain Greenfield. Elles sont de plusieurs types, comme décrit ci-dessous.

#### 5.1.1 Comptes et solde

Chaque utilisateur a son "adresse de propriétaire" comme identifiant de compte de propriétaire pour "posséder" les ressources de données. Il existe un autre type de "compte de paiement" dédié à la facturation et au paiement, détenu par les adresses des propriétaires.

Tant les comptes propriétaires que les comptes de paiement peuvent détenir le solde de BNB sur Greenfield. Les utilisateurs peuvent déposer des BNB à partir de la BSC, accepter des transferts d'autres utilisateurs et les dépenser pour des transactions de gaz et de stockage.

#### 5.1.2 Métadonnées du validateur et du FS

Il s'agit des informations de base sur les validateurs et les FS Greenfield. Les FS peuvent avoir plus d'informations, car ils doivent publier
leurs informations de service pour les opérations de données des utilisateurs. Il devrait y avoir un mécanisme de réputation pour les FS.

#### 5.1.3 Métadonnées de stockage

Les "métadonnées de stockage" comprennent la taille, la propriété, les hachages de somme de contrôle et l'emplacement de la distribution parmi les FS. Comme pour AWS S3, l'unité de base du stockage est un "*objet*", qui peut être un morceau de données binaires, des fichiers texte, des photos, des vidéos ou tout autre format. Les utilisateurs peuvent créer leurs objets sous leur "*bucket*". Un bucket est unique au monde. L'objet peut être référencé via le nom du bucket et l'ID de l'objet. Il peut également être localisé par le nom du bucket, le préfixe et l'identifiant de l'objet des simplifications hors chaîne.

#### 5.1.4 Métadonnées d'autorisation

Les ressources de données sur Greenfield, telles que les objets de données et les buckets, ont toutes un contrôle d'accès, tel que l'adresse qui peut créer, lire, lister, ou même exécuter les ressources, et quelle adresse peut accorder/révoquer ces permissions.

Deux autres ressources de données ont également un contrôle d'accès. L'une est le "Groupe". Un groupe représente un ensemble d'adresses d'utilisateurs qui ont les mêmes permissions pour les mêmes ressources. Il peut être utilisé de la même manière qu'une adresse dans le contrôle d'accès. Cependant, il faut également une autorisation pour changer le groupe. L'autre est le "compte de paiement". Ils sont créés par les comptes propriétaires.

Ici, le contrôle d'accès est appliqué par les FS hors chaîne. Les gens peuvent tester et défier les FS s'ils ne respectent pas le contrôle. Des réductions et des récompenses seront de mise pour que les prestataires de services respectent les principes.

#### 5.1.5 Métadonnées de facturation

Les utilisateurs doivent payer des frais pour stocker des objets de données sur Greenfield. Alors que chaque objet bénéficie d'un quota gratuit à télécharger par les utilisateurs qui y sont autorisés, le téléchargement excessif nécessitera le paiement de paquets de données supplémentaires pour
la bande passante. Outre l'adresse du propriétaire, les utilisateurs peuvent dériver plusieurs "adresses de paiement" pour payer ces frais. Les objets sont stockés dans des buckets, tandis que chaque bucket peut être associé à ces adresses de paiement, et le système facturera ces comptes pour le stockage et/ou le téléchargement. De nombreux buckets peuvent partager la même adresse de paiement. Ces informations d'association sont également stockées sur des chaînes avec consensus.

Le paiement de Greenfield est basé sur un modèle de paiement par flux, ce qui réduit considérablement la complexité de la mise en œuvre de la facturation. - plus décrite dans la Partie 3.

### 5.2 Stockage des données utiles de l'objet hors chaîne

Les données utiles de l'objet, c'est-à-dire les octets qui composent les fichiers de données, les photos et les vidéos, sont stockées hors chaîne dans plusieurs FS avec un système de gestion des données. Chaque FS peut avoir son édition d'un système de stockage d'objets avec un bon accord de niveau de service et une interface très performante pour interagir avec les utilisateurs et les autres fournisseurs de services.

#### 5.2.1 Fournisseurs de Stockage primaires et secondaires

Parmi les multiples FS sur lesquels un objet est stocké, un FS sera le "FS primaire", tandis que les autres seront les "FS secondaires".

Lorsque les utilisateurs veulent écrire un objet dans Greenfield, eux-mêmes ou le logiciel client qu'ils utilisent doivent spécifier le FS primaire. Le FS primaire doit être utilisé comme le seul FS pour télécharger les données. Les utilisateurs peuvent changer le FS primaire pour leurs objets par la suite s'ils ne sont pas satisfaits de ce service.

#### 5.2.2 Redondance des données

Après que les utilisateurs aient émis une demande d'"écriture", le FS primaire doit répondre à la demande de téléchargement du client pour accepter le téléchargement de l'utilisateur, découper les données de l'objet en segments et vérifier l'intégrité des données. Ensuite, le Primary FS calcule une solution de redondance des données pour ces segments basée sur le codage par effacement (EC). Ensuite, le FS primaire ou les utilisateurs sélectionneront
quelques serveurs secondaires pour stocker ces répliques de segments et leurs pièces de parité EC. Cette communication de distribution de données se fera via le réseau p2p et les API REST entre les FS.

La configuration de la redondance des données vise à garantir que, même si le FS primaire et quelques FS secondaires deviennent indisponibles à un moment donné, les données ne seront pas perdues.
quelques FS secondaires deviennent indisponibles, Greenfield peut toujours récupérer l'ensemble des données.

## 6 Économie du stockage et ses primitives

Dans cette section, l'économie sous-jacente et les primitives d'exploitation sont examinées en fonction du cycle de vie d'un objet de données. Les primitives ci-dessous peuvent être exécutées après la genèse de la blockchain Greenfield et qu'un nombre suffisant de FS se soient enregistrés et aient commencé à travailler correctement.

### 6.1 Création de compte

Pour écrire un objet de données dans Greenfield, les utilisateurs doivent avoir un compte, ou plus précisément, une adresse sur la blockchain BNB Greenfield. Cela peut être fait en transférant des BNB depuis d'autres adresses sur Greenfield ou depuis la BSC.

Il se peut que les utilisateurs puissent sauter cette étape et émettre la demande de "transfert et d'écriture" directement à partir de la BSC. Comme Greenfield et BSC partagent le même protocole d'adresse, cette action crée de facto un compte sur Greenfield avec la même adresse sur BSC.

### 6.2 Création d'objets de données

Les utilisateurs doivent créer des "Buckets" avant de créer des objets. Similaire aux concepts de "Bucket" dans AWS S3, les "buckets" ici sont une ressource de données pour regrouper les objets de données d'un utilisateur. Tous les objets sous le même bucket seront stockés sur le même FS primaire et téléchargeables depuis ce FS. Les utilisateurs peuvent créer de nombreux buckets et stocker leurs objets de données dans différents buckets.

Chaque bucket est associé à un FS primaire, ce qui signifie que tous les objets de ce bucket utiliseront ce FS primaire. Si le FS primaire choisi ne peut pas bien répondre aux demandes, l'utilisateur peut choisir de migrer le bucket vers un autre FS complètement via une transaction on-chain.

La création d'objets de données s'effectue en deux phases.

1. Phase de demande :

a. Les utilisateurs établissent la connexion avec le FS primaire et envoient un message "get approval" pour demander s'il est prêt à stocker l'objet.
   La FS primaire accuse réception de la demande en signant un message sur l'opération et le renvoie au client.

b. Une fois que la FS primaire a décidé d'accepter la demande de stockage des données en tant que FS primaire, le client construit un message de              transaction "write" avec la signature du FS primaire et les métadonnées initiales de l'objet, telles que le nom de l'objet, le nom du bucket, la          taille, la somme de contrôle, et éventuellement le type de contenu et la préférence de stockage, etc. L'utilisateur signe la transaction et la soumet à    la chaîne Greenfield ;

c. Les utilisateurs obtiennent le résultat de la transaction et le hash de la transaction;

d. Greenfield accepte la demande de "création" et verrouille les droits des utilisateurs.

2. Phase de scellement :

a. Les utilisateurs se connectent à la FS primaire et envoient le hachage de la transaction. Le FS primaire utilise le hachage de la transaction pour        vérifier si les métadonnées de l'objet sont déjà créées sur la chaîne Greenfield;

b. Les utilisateurs commencent à télécharger les données utiles de l'objet vers le FS primaire si les métadonnées de l'objet sont déjà créées; le FS          primaire vérifie si les données utiles correspondent aux métadonnées de l'objet en comparant la somme de contrôle de l'objet sur la chaîne Greenfield      et la somme de contrôle des données utiles. Si c'est identique, Le FS primaire signe la confirmation "téléchargé" aux utilisateurs;

c. Le FS primaire se synchronise avec les FS secondaires pour mettre en place la redondance des données, puis il signe une transaction "Seal" avec les        métadonnées finalisées pour le stockage. Si le FS primaire détermine qu'il ne veut pas stocker le fichier pour une raison quelconque, il peut aussi        "SealRejecter" la demande.

d. Greenfield traite la transaction "Seal" ou "SealReject" pour lancer le cycle de vie du stockage de l'objet. Les utilisateurs peuvent toujours              "CancelRequest" pour renoncer à la demande de création et être partiellement remboursé.

Il existe des scénarios dans lesquels le FS primaire ne coopère pas bien avec l'utilisateur : 
1. Le FS primaire accuse réception de la demande de téléchargement, mais n'accepte pas le téléchargement à temps; 
2. le FS primaire signe la confirmation du "téléchargement" mais ne scelle pas la transaction à temps. 
Greenfield s'attend à ce que le FS primaire termine la création de l'objet par une transaction "Seal" ou "SealReject" dans les délais impartis.
Soit par une transaction "SealReject" dans une fenêtre de temps prédéfinie; sinon, le FS primaire ne peut pas terminer la création de l'objet.

### 6.3 Stockage des données

Une fois qu'un objet de données est "scellé", le propriétaire de l'objet a de facto conclu un contrat avec les FS pour le stockage. Dans ce cas, les propriétaires doivent payer des frais pour ce stockage et les FS doivent garantir la disponibilité des données.

Les propriétaires d'objets de données ont toujours le droit de changer de FS principal pour le stockage de leurs données, après avoir réglé les frais de stockage.

Les prestataires de services, en particulier les prestataires de services primaires, peuvent également informer les gens qu'ils doivent cesser de stocker les données, que ce soit en raison de leurs propres opinions ou décisions. Les prestataires de services et les propriétaires peuvent observer les notifications correspondantes. Les Fournisseurs de Stockage peuvent volontairement se proposer comme successeurs pour stocker les
objets de données sur Greenfield si les propriétaires ne réagissent pas à la notification dans un délai prédéfini, afin de prendre le relais et de récupérer l'affaire.

### 6.4 Lecture et téléchargement de données

Par conception, les octets qui sont stockés et téléchargés ultérieurement pour l'objet sont exactement les mêmes octets que ceux qui ont été envoyés à l'origine. Les FS peuvent utiliser leur logique de cryptage comme ils le souhaitent, mais lorsque les données sont téléchargées, elles affichent les mêmes octets que lors de l'envoie. Les utilisateurs peuvent choisir leur propre schéma de cryptage ou utiliser celui par défaut fourni par le logiciel client s'ils veulent que les données soient méconnaissables par les FS ou toute autre personne, même si les FS ont l'obligation de ne pas faire circuler ces données hors de l'instruction des utilisateurs.

Les objets de données ne peuvent être lus et téléchargés que par les adresses disposant des autorisations de lecture appropriées. Le FS primaire des objets est la principale source de téléchargement. Si le Primary FS n'est pas disponible, le propriétaire et les validateurs de la blockchain Greenfield peuvent le contester (voir partie 3) et changer le FS primaire de l'objet pour récupérer le téléchargement.

Chaque objet a un quota de bande passante de trafic basé sur le temps, qui est fourni gratuitement, c'est-à-dire que personne n'a besoin de payer pour télécharger une certaine quantité dans une période donnée. On s'attend à ce que ce quota puisse satisfaire la plupart des besoins de téléchargement individuels dans le cadre des conditions normales d'utilisation.

Pour disposer d'une bande passante supplémentaire pour télécharger l'objet, il faut payer un forfait de données, qui est abordé dans la section sur le paiement.

### 6.5 Permissions et groupes

La permission est la principale logique introduite dans Greenfield pour permettre des modèles commerciaux potentiels.

Les ressources de données, y compris les objets, les buckets, les comptes de paiement, et les groupes, ont toutes des permissions liées. Ces permissions définissent si chaque compte peut effectuer des actions particulières.

Un groupe est une liste de comptes qui peuvent être traités de la même manière qu'un compte unique.

Des exemples de permissions sont :

- Mettre, Lister, Obtenir, Supprimer, Copier et Exécuter des objets de données ;

- Créer, Supprimer, et Lister des buckets

- Créer, Supprimer, ListMembersOf, Quitter des groupes

- Créer, associer des comptes de paiement

- Accorder, révoquer les permissions ci-dessus

Ces permissions sont associées aux ressources de données et aux comptes/groupes, et les définitions des groupes sont stockées publiquement sur la blockchain Greenfield. Pour l'instant, elles sont en texte clair. Plus tard, un mode de confidentialité sera introduit sur la base de la technologie Zero Knowledge Proof.

Une chose qui rend l'opération de permission plus intéressante est qu'elles peuvent être exploitées depuis la BSC directement, soit par des smart contracts soit par une EOA.

### 6.6 Frais et Paiements

<div align="center"><img src="./assets/6.6%20Payment%20Stream%20Flow.png" height="80%" width="80%"></div>
<div align="center"><i>Figure 6.1: Flux de paiement</i></div>

Les frais de stockage seront facturés sur Greenfield dans un style de flux de paiement comme *[Superfluid](https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/constant-flow-agreement-cfa)*.
Les frais sont payés sur Greenfield dans le style "Stream" des utilisateurs aux comptes récepteurs à un taux constant. Les frais sont "facturés" chaque
seconde au fur et à mesure de leur utilisation.

Il existe deux types de frais pour Greenfield : les frais de stockage d'objets et les frais de paquet de données.

Pour le stockage, chaque objet stocké sur Greenfield est facturé au prix calculé en fonction de la taille, du nombre de répliques, d'un ratio de prix de base et d'autres paramètres. Une fois l'objet stocké, le coût total du stockage sera principalement lié au temps et à la durée du stockage.

Pour le téléchargement de données, il existe un quota gratuit, basé sur le temps, pour chaque bucket des objets des utilisateurs. S'il est dépassé, les utilisateurs peuvent promouvoir leur paquet de données pour obtenir plus de quota. Chaque paquet de données a un prix fixe pour la
période définie. Une fois le paquet de données choisi, le coût total du téléchargement sera uniquement lié au temps et au prix du paquet de données, jusqu'à ce que les paramètres du paquet de données soient à nouveau modifiés.

Dans ce cas, la confiance règne entre les utilisateurs et les FS pour le téléchargement de données. Comme la bande passante supplémentaire pour le téléchargement est payante et que le journal des téléchargements n'est pas entièrement stocké sur la blockchain Greenfield. Les prestataires de services doiven fournir une interface de point de terminaison permettant aux utilisateurs d'interroger le téléchargement avec des journaux détaillés et les signatures des téléchargeurs. Si les utilisateurs et les prestataires de services ne parviennent pas à se mettre d'accord sur la facture, les utilisateurs peuvent simplement choisir un autre prestataire de services primaires.

Par défaut, l'adresse du propriétaire de l'objet sera utilisée pour payer les objets qu'il possède. Mais les utilisateurs peuvent aussi créer plusieurs "comptes de paiement", et associer des objets à des comptes de paiement différents pour payer le stockage et de la bande passante.

Le format de l'adresse du compte de paiement est le même que celui des comptes normaux. Elle est dérivée du hachage de l'adresse de l'utilisateur et de l'index du compte de paiement. Cependant, les comptes de paiement ne sont en fait que logiques et n'existent que dans le module de paiement du stockage. Les utilisateurs peuvent déposer, retirer et consulter le solde des comptes de paiement sur la blockchain Greenfield, mais ils ne peuvent pas utiliser les comptes de paiement pour effectuer des transactions de staking ou d'autres transactions sur la chaîne. Les comptes de paiement peuvent être définis comme
"non-remboursable". Les utilisateurs ne peuvent pas retirer de fonds de ces comptes de paiement.

D'autres utilisateurs peuvent également parrainer le paiement en faisant don d'un flux de "paiement stream" vers les comptes de paiement "non-remboursables" sélectionnés. Ils peuvent faire une pause quand ils le souhaitent.

Tous les frais de stockage et les paquets de données sont tarifés et payés en BNB. Il y a des paramètres système et des oracles de prix provenant des relais Greenfield (décrits ci-dessous) pour ajuster la tarification en fonction de la situation commerciale.

Une fois que les comptes de paiement n'ont plus de BNB, les objets associés à ces comptes de paiement souffriront d'une dégradation du service de
téléchargement, c'est-à-dire que la vitesse de téléchargement et les numéros de connexion seront limités. Une fois les fonds transférés sur les comptes de paiement, la qualité du service peut être rétablie immédiatement. Si le service n'est pas rétabli pendant une longue période, les FS peuvent décider d'effacer les données, de manière similaire à la façon dont les FS prétendent arrêter les services de certains objets. Dans un tel cas, les données peuvent disparaître complètement de Greenfield.

### 6.7 Défi de l'intégrité et de la disponibilité des données

Il existe trois aspects de l'intégrité, de la disponibilité et de la redondance des données.
comme indiqué ci-dessous :

1. Le FS primaire stocke l'objet correct que l'utilisateur a téléchargé.

2. Le FS stocke correctement les segments de données qui lui ont été attribués, soit en tant que rôle de FS primaire, soit en tant que FS secondaire, et      les éléments de données stockés ne doivent pas être manquants, corrompus ou contrefaits.

3. Les éléments de codage d'effacement stockés dans les FS secondaires peuvent récupérer l'objet original stocké dans la FS primaire.

L'intégrité et la redondance des données doivent être assurées en premier lieu par la mise en place de la somme de contrôle et de la redondance des objets. Ils font partie des données, qui doivent être vérifiées par les FS et les utilisateurs lors de la création des objets. Ces métadonnées seront également stockées sur la blockchain Greenfield.

Greenfield et les FS doivent travailler ensemble pour garantir l'intégrité et la disponibilité des données, en particulier pour le point #2 ci-dessus. Contrairement aux autres systèmes de stockage décentralisés, ici une "preuve de défi" est introduite pour renforcer la confiance des utilisateurs dans le fait que les données sont bien stockées comme promis.

Les challengers peuvent provenir de différentes parties prenantes. Premièrement, les utilisateurs peuvent soumettre des transactions de défi; deuxièmement, tout comme les utilisateurs, les Fournisseurs de Stockage peuvent soumettre des transactions de défi à d'autres FS ; et enfin, la blockchain Greenfield émettra également des défis internes de manière aléatoire.

Le défi peut être déclenché par des transactions Greenfield ou des événements internes à la fin du blocage. Lorsque les validateurs Greenfield observent un tel challenge, ils doivent exécuter une vérification hors chaîne standard contre les données des FS contestés. Ces validateurs voteront pour les
résultats de la contestation par le biais d'un multisig agrégé via un réseau P2P et les soumettront à la blockchain Greenfield. L'échec du résultat
d'un défi entraînera la suppression des FS correspondants. L'expéditeur et les validateurs seront récompensés pour de tels défis.

Les données qui ont échoué le défi ne seront pas contestées dans un certain temps afin de donner aux FS le temps de se rétablir.

Une autre section de la partie 3 traitera plus en détail des défis de disponibilité des données.

### 6.8 Suppression de données

Les utilisateurs peuvent demander la suppression de leurs objets de données. Greenfield supprimera les métadonnées de l'état de la blockchain, tandis que le FS primaire devrait répondre à cette demande et supprimer toutes les répliques et les segments redondants. Le flux de paiement sera fermé avec un rabais de récompense pour encourager la suppression à l'avenir.

## 7 Économie des actifs de données

La véritable puissance de l'écosystème Greenfield réside dans le fait que la plateforme n'est pas seulement conçue pour stocker les données, mais aussi pour soutenir la création de valeur basée sur les actifs de données et l'économie qui y est associée.

Les caractéristiques des actifs des données sont d'abord établies en fonction des permissions, par exemple, l'autorisation de lire les données. Lorsque ce droit est déconnecté des données elles-mêmes, ils deviennent des actifs négociables et augmentent la valeur des données. Cela peut être amplifié lorsque les données elles-mêmes peuvent être exécutables (un nouveau type de "code intelligent"), interagir entre elles et générer de nouvelles données. Cela laisse beaucoup de place pour imaginer la construction d'un nouvel environnement informatique sans confiance et à forte intensité de données.

Deuxièmement, les autorisations de données peuvent être transférées d'une chaîne à l'autre sur la BSC, et y devenir des actifs numériques. Cela crée une variété de possibilités et d'intégrer ces actifs avec les protocoles et modèles DeFi existants sur la BSC.

Ceci est encore amélioré par les contrats intelligents sur la BSC, qui bénéficient du même format d'adresse que les comptes sur la blockchain Greenfield
et peuvent être les propriétaires des objets de données et hériter de différentes permissions. Cela va libérer de nombreuses nouvelles opportunités commerciales basées sur les données et leurs opérations.

### 7.1 Inter-chaîne avec la BSC

Le modèle cross-chain vise à atteindre les objectifs suivants :

- Intégration aux systèmes existants : essayer de réutiliser l'infrastructure et les dApps actuelles, telles que les NFT Marketplace, l'indexation des       données et les explorateurs de blockchain.

- Programmable : les dApps peuvent définir comment elles veulent envelopper les actifs de Greenfield.

- Sécurisé et récupérable.

Le pont inter-chaînes natif est maintenu et sécurisé par les validateurs de Greenfield, via un système d'échange de données, basé sur un
schéma multisig agrégé (plus de détails dans les sections suivantes). Les validateurs de Greenfield feront fonctionner les relais pour faciliter les flux via la pont rapidement et à large bande passante.

Le BNB sera transféré de la BSC à Greenfield comme première action inter-chaînes. L'ensemble initial de validateurs de Greenfield à sa genèse bloquera d'abord un certain montant de BNB dans le contrat "Greenfield Token Hub" sur la BSC. Ce contrat sera également utilisé dans le cadre de la passerelle native pour le transfert de BNB après la genèse. Ces BNB verrouillés initialement seront utilisés pour le paiement des validateurs et des frais de gaz des premiers jours.

### 7.2 Framework

<div align="center"><img src="./assets/7.1%20Cross-chain%20Architecture.jpg" height="80%" width="80%"></div>
<div align="center"><i>Figure 7.1: Architecture Inter-chaîne</i></div>

La couche inférieure est une couche de communication inter-chaînes **Communication Layer**, qui se concentre sur la gestion et la vérification des paquets de communication primitifs. La couche intermédiaire met en œuvre le **Miroir de ressources**. Elle est responsable de la gestion des ressources définies sur Greenfield mais reflétées sur la BSC. La couche supérieure est la **couche d'application**, qui sont les contrats intelligents mis en œuvre par les développeurs de la communauté sur la BSC pour exploiter les entités de ressources en miroir avec leurs primitives. Greenfield ne dispose pas d'une telle couche d'application puisqu'il ne fournit pas encore de programmabilité. Les véritables dApps auront une part dans cette couche d'application et interagiront également avec le Noyau GreenField et toutes sortes d'infrastructures de soutien.

En raison de la structure asymétrique, BSC se concentre davantage sur le plan d'application/contrôle, tandis que GreenField se concentre sur le plan des données. Pour éviter la course aux états, les règles suivantes sont introduites :

- Toute ressource dont la création est initiée par la BSC ne peut être contrôlée que par la BSC.

- Toute ressource contrôlée par la BSC ne peut pas transférer les droits de contrôle à Greenfield.

- Toute ressource contrôlée par Greenfield peut transférer des droits de contrôle à la BSC.

### 7.3 La couche de communication est composée d'un ensemble de **Relais Greenfield** :

- Chaque validateur doit faire fonctionner un relais. Chaque relais possède une clé privée BLS avec l'adresse de la clé stockée sur la chaîne comme         faisant partie de l'information obligatoire du validateur.

- Le relais surveille tous les événements inter-chaînes qui se produisent sur la BSC et la blockchain Greenfield indépendamment. Après un nombre suffisant   de blocs de confirmation pour atteindre la finalité, le relayeur signera un message par la clé BLS pour confirmer les événements, et diffuse               l'attestation de signature, qui est appelée "le vote", à travers un réseau p2p aux autres relais.

- Une fois qu'un nombre suffisant de votes a été collecté, le relayeur va assemblera un paquet de transactions inter-chaînes et le soumettra à la BSC ou     au réseau Greenfield.

### 7.4 Couche miroir de ressources

#### 7.4.1 Miroir d'entité de ressource

Les objectifs de presque tous les paquets inter-chaînes sont de changer l'état des entités de ressources sur la blockchain Greenfield. Ainsi, les entités ressources ci-dessous devraient pouvoir être mises en miroir sur la BSC :

1. Compte

2. BNB

3. Bucket

4. Objet

5. Groupe

Le mappage des comptes est naturel : la BSC et Greenfield utilisent le même schéma d'adresses. Les mêmes valeurs d'adresse des deux côtés signifient le même compte. Ils n'ont pas besoin d'un miroir réel.

Le BNB est un jeton nativement ancré depuis la genèse de Greenfield. Le contrat "Token Hub" est un contrat intelligent construit sur la BSC pour garantir que Greenfield ne puisse pas gonfler le BNB et sécuriser la circulation totale de BNB.

Les Bucket, Object et Group sont reflétés sur la BSC en tant que NFT d'un nouveau BEP révisée à partir de la norme ERC-721. Ces NFTs ont des informations de métadonnées correspondantes pour les ressources. Les propriétaires des NFTs sur la BSC correspondent aux propriétaires de ces ressources sur Greenfield. Comme ces propriétaires ne sont pas transférables sur Greenfield, ces NFT ne sont pas transférables sur la BSC.

#### 7.4.2 Primitives d'exploitation inter-chaînes

Quelques séries de primitives inter-chaînes sont définies pour que les dApps les appellent pour opérer sur ces entités de ressources.

Il convient de souligner que les contrats intelligents peuvent appeler ces primitives de la même manière que les EOA.

Comptes

-Créer des comptes de paiement sur la BSC

BNB :

- Transfert bidirectionnel entre les comptes de la BSC et Greenfield (y compris les comptes de paiement)

Bucket :

- Création d'un bucket sur la BSC

- Miroir de Greenfield vers la BSC

Objet :

- Objet miroir de Greenfield à la BSC

- Créer un objet sur la BSC

- Accorder/révoquer les permissions des objets sur la BSC aux comptes/groupes

- Copier des objets sur la BSC

- Lancer l'exécution d'un objet sur la BSC

- Associer des buckets à des comptes de paiement sur la BSC

Groupe :

- Groupe miroir de Greenfield à la BSC

- Créer un groupe sur la BSC

- Changer les membres d'un groupe sur la BSC

- Quitter un groupe sur la BSC

Une fois que ces primitives sont appelées par l'EOA ou les smart contracts, les événements prédéfinis seront émis. Les relais de Greenfield doivent capter
ces événements et les relayer à Greenfield et la BSC. Comme le changement se produira de manière asynchrone, il y aura des paquets spécifiques à travers la chaîne pour les accusés de réception ou les erreurs, qui peuvent déclencher un rappel. L'appelant des primitives devrait payer les frais à l'avance pour les opérations inter-chaînes et aussi pour le rappel potentiel. Plus de détails sont abordés dans la partie 3.

## 8 "Pas" de fin pour la conception

De nombreux détails ne sont pas couverts dans la partie 1. Alors que certains sujets seront ajoutés et développés dans la partie 3, certains sont des éléments très stratégiques qui vont trop loin pour que l'équipe les prenne en compte maintenant.

Par exemple, le trait "execute" d'un objet de données. Ce concept indique que certaines données sont des programmes exécutables. Greenfield peut créer un environnement informatique plus transparent. Les utilisateurs sont à l'aise pour utiliser ou consacrer leurs données à des programmes particuliers stockés sur Greenfield parce qu'ils peuvent vérifier le programme, ils n'ont pas à s'inquiéter que le programme puisse changer après leur confirmation, et ils savent que le programme peut seulement s'exécuter avec leurs données dans un environnement de confiance fourni par Greenfield.

Cette fonction particulière, ainsi que d'autres nouvelles fonctionnalités, seront recherchées et étudiées dans le cadre du développement futur de BNB Greenfield.

### 8.1 Remerciements

Nous tenons à remercier tout particulièrement les efforts et les idées des équipes et des communautés suivantes (sans ordre particulier et certainement pas par ordre d'importance). BNB Greenfield s'appuie sur les épaules de ces géants pour construire.

1. Ethereum

2. Cosmos SDK

3. Superfluid

4. Services Web d'Amazon

5. MinIO, et autres systèmes de stockage open-source

6. Filecoin, Arweave, StorJ, et autres réseaux de stockage décentralisés

7. Bitcoin, et

8. toutes les autres personnes et projets qui luttent pour la nouvelle économie du Web3.

## Partie 3 : Spécifications techniques simplifiées

## Table des matières

- [14 Acteurs de l'écosystème](#14-acteurs-de-lécosystème)
  - [14.1 Greenfield Validators](#141-validateurs-greenfield)
  - [14.2 Fournisseurs de stockage (FS)](#142-prestataires-de-services-de-stockage-ps)
  - [14.3 Greenfield dApps](#143-les-dapps-greenfield)
- [15 Identifiant de l'utilisateur](#15-identifiant-de-lutilisateur)
  - [15.1 Solde utilisateur](#151-solde-de-lutilisateur)
- [16 Greenfield Blockchain](#16-blockchain-greenfield)
  - [16.1 Économie des jetons](#161-économie-des-jetons)
  - [16.2 Consensus et élection du validateur](#162-consensus-et-élection-du-validateur)
  - [16.3 Transactions de gouvernance](#163-transactions-de-gouvernance)
    - [16.3.1 Créer et modifier le validateur](#1631-créer-et-modifier-un-validateur)
    - [16.3.2 Distribution des récompenses de jalonnement](#1632-distribution-des-récompenses-de-jalonnement)
    - [16.3.3 Créer un fournisseur de stockage](#1633-create-storage-provider)
    - [16.3.4 Supprimer le fournisseur de stockage](#1634-supprimer-un-fournisseur-de-stockage)
- [17 Storage MetaData Models](#17-modèles-de-métadonnées-de-stockage)
  - [17.1 Bucket](#171-bucket)
  - [17.2 Objet](#172-objet)
  - [17.3 Groupe](#173-groupe)
  - [17.4 Permission](#174-permission)
    - [17.4.1 Propriété](#1741-propriétaire)
    - [17.4.2 Définitions de la permission](#1742-définitions-des-permissions)
    - [17.4.3 Suppression de la permission](#1743-suppression-de-permissions)
    - [17.4.4 Exemples](#1744-exemples)
- [18 Gestion du stockage des charges utiles](#18-gestion-du-stockage-des-charges-utiles)
  - [18.1 Segments](#181-segments)
  - [18.2 Code d'effacement et redondance des données](#182-code-deffacement-et-redondance-des-données)
    - [18.2.1 Conception de la redondance des données](#1821-conception-de-la-redondance-des-données)
    - [18.2.2 Code d'effacement](#1822-code-deffacement)
      - [18.2.2.1 Codage](#18221-encodage)
      - [18.2.2.2 Décodage : Récupération des données](#18222-décodage--récupération-des-données)
- [19 Défi de la disponibilité des données](#19-le-défi-de-la-disponibilité-des-données)
  - [19.1 Les métadonnées initiales d'intégrité et de redondance des données](#191-the-initial-data-integrity-and-redundancy-metadata)
  - [19.2 Processus de contestation de la disponibilité des données](#192-data-availability-challenge-process)
- [20 Storage Transactions](#20-transactions-de-stockage)
- [21 Facturation et paiement](#21-facturation-et-paiement)
  - [21.1 Concepts et formules](#211-concepts-et-formules)
    - [21.1.1 Terminologie](#2111-terminologie)
    - [21.1.2 Formule](#2112-formule)
    - [21.1.3 Types et interfaces](#2113-types-et-interfaces)
  - [21.2 Flux de travail sur les clés](#212-flux-de-travail-clé)
    - [21.2.1 Dépôt et retrait](#2121-dépôt-et-retrait)
    - [21.2.2 Flux de paiement](#2122-flux-de-paiement)
    - [21.2.3 Règlement forcé](#2123-règlement-forcé)
    - [21.2.4 Compte de paiement](#2124-compte-de-paiement)
    - [21.2.5 Gel et reprise du compte](#2125-gel-et-reprise-de-compte)
    - [21.2.6 Prix et ajustement de la redevance de stockage](#2126-prix-et-ajustement-des-frais-de-stockage)
- [22 Modèles inter-chaînes](#22-modèles-inter-chaînes)
  - [22.1 Canaux de communication et paquets](#221-canaux-et-paquets-de-communication)
    - [22.1.1 Vote par sondage](#2211-vote-par-sondage)
    - [22.1.2 Canal et séquence](#2212-canal-et-séquence)
    - [22.1.3 Protocole de fiabilité](#2213-protocole-de-fiabilité)
    - [22.1.4 Mise à jour du validateur](#2214-mise-à-jour-du-validateur)
  - [22.2 Economique](#222-économique)
    - [22.2.1 Frais et récompense des paquets inter-chaînes](#2221-frais-et-récompense-des-paquets-inter-chaînes)
    - [22.2.2 Course à la livraison de paquets inter-chaînes](#2222-course-pour-la-livraison-de-paquets-inter-chaînes)
    - [22.2.3 Rappels et gaz limité](#2223-callbacks-et-gaz-limité)
    - [22.2.4 Contrats d'infrastructure inter-chaînes sur BSC](#2224-contrats-dinfrastructure-inter-chaînes-sur-bsc)
  - [22.3 Gestion des erreurs et des défaillances](#223-traitement-des-erreurs-et-des-défaillances)
- [23 API de la FS](#23-api-de-sp)
  - [23.1 Point de terminaison universel](#231-point-daccès-universel)
    - [23.1.1 URI standard](#2311-norme-uri)
    - [23.1.2 API REST HTTFS](#2312-https-rest-api)
    - [23.1.3 P2P RPC](#2313-p2p-rpc)
  - [23.2 Opérations de liste](#232-opérations-de-liste)

Cette partie du livre blanc est la plus détaillée et est donc sujette à de fréquentes modifications. Il convient de souligner ici et de bien
largement compris que le contenu de cette partie sera continuellement mis à jour, beaucoup plus fréquemment que les autres parties,
avec l'ajout de nouvelles sections ou la révision des sections existantes.

## 14 Acteurs de l'écosystème

Il existe plusieurs rôles d'acteurs pour l'ensemble de l'écosystème Greenfield.

<div align="center"><img src="./assets/14.1%20All%20Players%20of%20Greenfield.jpg"  height="80%" width="80%"></div>
<div align="center"><i>Figure 14.1: All Players of Greenfield</i></div>

### 14.1 Validateurs Greenfield

En tant que blockchain PoS, la blockchain Greenfield a ses propres validateurs.
Ces validateurs sont élus sur la base de la logique de preuve d'acceptation.

Ces validateurs sont responsables de la sécurité de la blockchain Greenfield.
blockchain. Ils sont impliqués dans la gouvernance et le jalonnement de la
blockchain. Ils forment un réseau P2P qui est similaire à d'autres réseaux PoS
blockchain.

En même temps, ils acceptent et traitent les transactions pour permettre aux utilisateurs de
d'exploiter leurs objets stockés sur Greenfield. Ils maintiennent les métadonnées
de Greenfield comme l'état de la blockchain, qui est le panneau de contrôle pour les
fournisseurs de stockage (FS) et des utilisateurs. Ces deux parties utilisent et mettent à jour
ces états pour faire fonctionner le stockage d'objets.

Les validateurs de Greenfield sont également tenus d'exploiter le système de relais
pour la communication inter-chaînes avec le BSC.

La topologie du réseau des validateurs Greenfield est similaire à la configuration existante des validateurs sécurisés de la blockchain PoS.
validateurs sécurisés existants des blockchains PoS. Les "Sentry Nodes" sont utilisés pour
défendre contre les DDoS et fournir un réseau privé sécurisé, comme le montre le schéma ci-dessous.
le schéma ci-dessous.

<div align="center"><img src="./assets/14.2%20Greenfield%20Blockchain%20Network.jpg"  height="80%" width="80%"></div>
<div align="center"><i>Figure 14.2: Greenfield Blockchain Network</i></div>

### 14.2 Prestataires de services de stockage (FS)

Les fournisseurs de stockage sont des personnes et des organisations professionnelles qui gèrent
une série de services pour fournir des services de données basés sur la blockchain Greenfield.
blockchain.

Chaque FS doit avoir une bonne connexion avec le réseau Greenfield en
maintenant son propre nœud complet local afin qu'il puisse regarder l'état
directement l'évolution de l'état, indexer les données correctement et envoyer des demandes de transaction
en temps voulu.

Les différents FS sont également interconnectés via des API REST et un réseau P2P.
tout en fournissant des services aux utilisateurs en répondant à leurs demandes dans les API REST ou le réseau P2P.
demandes dans les API REST ou les RPC P2P.

La topologie typique d'un réseau de FS connectés est présentée dans la figure ci-dessous.

<div align="center"><img src="./assets/14.3%20Greenfield%20Storage%20Provider%20Network.jpg" height="80%" width="80%"></div>
<div align="center"><i>Figure 14.3: Greenfield Storage Provider Network</i></div>

Les FS peuvent fournir de nombreux services pratiques pour que les utilisateurs et les dApps obtiennent
données sur Greenfield.

### 14.3 Les dApps Greenfield

Les dApps Greenfield sont des applications qui fournissent des fonctions basées sur le stockage Greenfield et ses caractéristiques économiques.
fonctions basées sur le stockage Greenfield et les caractéristiques économiques qui y sont liées pour résoudre certains
problèmes de leurs utilisateurs.

Ces dApps peuvent interagir avec Greenfield ou interagir à la fois avec la blockchain Greenfield et les FS.
Greenfield blockchain et les Fournisseurs de Stockage, ou le plus souvent, interagir avec
la blockchain Greenfield, les FS et la BSC.

Les dApps peuvent lire les données provenant de toutes ces sources de données pour faciliter
l'interaction des utilisateurs avec les contrats intelligents et les faire naviguer à travers
les différents types de scénarios d'utilisation.

Dans Greenfield, comme dans d'autres environnements décentralisés, les dApps n'ont pas besoin de demander un enregistrement, mais communiquent avec les utilisateurs.
n'ont pas besoin de demander une inscription, mais communiquent avec les portefeuilles des utilisateurs pour obtenir des instructions et d'autres informations.
les instructions et autres informations des utilisateurs.

## 15 Identifiant de l'utilisateur

Chaque utilisateur a sa propre adresse comme identifiant pour son compte.
Les adresses peuvent créer des objets à stocker sur Greenfield, supporter et gérer les
les permissions, et payer des frais.

Greenfield définit son compte dans le même format que BSC et Ethereum.
Il commence avec la courbe ECDSA secp256k1 pour les clés et est conforme à
[EIP84] (https://github.com/ethereum/EIPs/issues/84) pour les clés.
complet
[BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)
chemins. Le chemin du disque dur racine pour les comptes basés sur Greenfield est le suivant
m/44'/60'/0'/0. Dans la présentation lisible, l'adresse Greenfield est la suivante
une chaîne hexadécimale de 42 caractères, dérivée des 20 derniers octets de la clé publique
clé publique du compte de contrôle avec 0x comme préfixe.

Avec ce schéma d'adresse compatible, les utilisateurs peuvent réutiliser les comptes et l'infrastructure existants de BSC sur Greenfield.
comptes et l'infrastructure existants de BSC sur Greenfield. Par exemple, ils
peuvent utiliser TrustWallet et Metamask (ou d'autres portefeuilles compatibles) pour
déposer leur BNB de BSC à Greenfield et interagir avec les dApps sur Greenfield.
Greenfield. Il est également facile d'identifier le même propriétaire en se référant aux
les mêmes adresses sur BSC et Greenfield.

La blockchain Greenfield est une chaîne spécifique à une application sans EVM.
structure des données de transaction et l'API sont différentes de celles de la BSC. Greenfield
ne supportera pas toutes les fonctions des portefeuilles existants, par exemple le transfert, l'envoi de transactions, etc.
Transactions, etc. Mais elle permettra aux portefeuilles existants de signer des
transactions avec le
Mais il permettra aux portefeuilles existants de signer des transactions avec la norme [EIP712] (https://eips.ethereum.org/EIFS/eip-712).
Cette norme permet aux portefeuilles d'afficher les données dans les invites de signature dans un format structuré et lisible.
format structuré et lisible. Il s'agit d'un
[exemple](https://medium.com/metamask/eip712-is-coming-what-to-expect-and-how-to-use-it-bb92fd1a7a26)
de comment l'utiliser dans Metamask. À terme, les portefeuilles commenceront à prendre en charge
Greenfield directement.

### 15.1 Solde de l'utilisateur

L'identifiant de l'utilisateur est associé à un compte dans le grand livre de Greenfield.
Le compte peut contenir un solde de BNB. Ces BNB peuvent être utilisés pour
participer au jalonnement, payer les frais de gaz des transactions de Greenfield, et
payer les services de Greenfield.

Ce solde peut être ajouté via un transfert de BNB natif sur Greenfield, ou
transfert cross-chain entre Greenfield et BSC.

## 16 Blockchain Greenfield

En tant que blockchain indépendante, la blockchain Greenfield est construite sur Cosmos
SDK et la bibliothèque Tendermint. Elle fonctionne de la même manière que les autres
Elle fonctionne de la même manière que les autres blockchains PoS qui sont basées sur le même cadre.

### 16.1 Économie des jetons

BNB reste le principal jeton de service sur Greenfield.

BNB peut être transféré de la BSC à la blockchain Greenfield, et vice versa.
versa. Il sera utilisé pour :

1. s'auto-déléguer et déléguer en tant que mise, ce qui permet de gagner des récompenses en gaz et
   peuvent subir des coupures pour des comportements inappropriés.

2. payer le gaz pour soumettre des transactions sur la blockchain Greenfield,
   qui comprend les transactions locales de Greenfield ou les transactions inter-chaînes
   entre Greenfield et BSC. Cette somme est facturée au
   au moment de la soumission de la transaction et envoyé aux validateurs de Greenfield
   validateurs Greenfield, et potentiellement aux fournisseurs de stockage Greenfield pour certaines
   transactions.

3. payer les frais pour le stockage des objets et le paquet de données de la bande passante de téléchargement.
   Ces frais sont facturés au fur et à mesure et envoyés aux fournisseurs de stockage Greenfield.

### 16.2 Consensus et élection du validateur

Comme la méthode Proof-of-Stake est adoptée dans Greenfield, il y aura un ensemble de validateurs fondateurs dans l'état genesis.
validateur fondateur dans l'état de genèse. Ces validateurs déposent leurs BNBs
sur un contrat intelligent BSC, qui seront verrouillés comme leurs enjeux. Le nouveau
validateur peut être élu par la majorité des validateurs actuels pour les rejoindre.
et est élu comme validateur actif en fonction de la taille de sa délégation.
taille. Voici les étapes à suivre pour devenir un nouveau validateur :

1. L'autodélégataire accorde une autorisation au délégué pour le compte du module gov. L'autorisation du délégué
   permet au bénéficiaire d'exécuter MsgDelegate pour le compte du délégant.

2. Initier une proposition pour devenir un valideur.

3. Attendre que les validateurs actuels votent sur cette proposition.

4. Une fois la proposition adoptée, le nouveau validateur sera créé automatiquement.

Un validateur peut ne pas toujours être membre de l'ensemble des validateurs actifs,
qui proposera et produira des blocs. Seuls ceux qui sont élus par le rang
de la taille de la délégation seront les validateurs actifs. L'élection a lieu
à chaque bloc. Le nombre maximum de validateurs actifs est fixé et régi par
les validateurs existants.

Il convient de souligner que les validateurs de Greenfield sont séparés
des fournisseurs de stockage Greenfield. 
Les validateurs Greenfield sont responsables de la génération de blocs Greenfield
la sécurité de la blockchain Greenfield, de vérifier la disponibilité des données et de maintenir la communication entre les chaînes.
la disponibilité des données et de la communication entre les chaînes.
de stocker les objets de données et de répondre aux demandes de téléchargement.
Il n'y a pas de lien fort entre eux, bien que la même organisation puisse jouer deux rôles en même temps.
même organisation peut jouer deux rôles en même temps.

### 16.3 Transactions de gouvernance

#### 16.3.1 Créer et modifier un validateur

Pour devenir un validateur, le runner doit accorder au délégué une autorisation sur le compte du module
compte du module gov avec suffisamment BNB, puis une proposition doit être
soumise pour obtenir les votes des validateurs existants. Après l'adoption de la proposition,
l'auto-délégation sera faite par le module gov, et le validateur
sera créé automatiquement. L'autodélégation est obligatoire,
et la délégation ouverte d'autres délégataires sera également prise en charge ultérieurement.

La logique de création du validateur devrait être modifiée ultérieurement pour réduire le problème des cartels.
préoccupation des cartels.

Message MsgCreateValidator:

```go
type MsgCreateValidator struct {
    Description       Description
    Commission        CommissionRates
    MinSelfDelegation github_com_cosmos_cosmos_sdk_types.Int
    DelegatorAddress  string
    ValidatorAddress  string
    Pubkey            *types.Any
    Value             types.Coin
    From              string
    RelayerAddress    string
    RelayerBlsKey     string
}
```

Un validateur peut modifier sa description et sa commission en soumettant une transaction de type "Edit Validator".
transaction "Edit Validator". Le taux de commission sera vérifié comme étant un
nombre approprié.

Message MsgEditValidator:

```go
type MsgEditValidator struct {
    Description       Description
    ValidatorAddress  string
    CommissionRate    *github_com_cosmos_cosmos_sdk_types.Dec
    MinSelfDelegation *github_com_cosmos_cosmos_sdk_types.Int
    RelayerAddress    string
    RelayerBlsKey     string
}
```

#### 16.3.2 Distribution des récompenses de jalonnement

Les validateurs recevront des frais de transaction comme récompense pour le jalonnement. Les récompenses de
récompenses seront distribuées de manière passive. Ceci est différent de la chaîne de balises BNB
Chain, où le système distribue les récompenses automatiquement.
Les validateurs peuvent soumettre des demandes de retrait pour obtenir toutes les récompenses de transaction mises à jour.
à jour, et lorsque les validateurs changent de taux de commission ou démissionnent
ou démissionnent, toutes les récompenses de transaction qui n'ont pas été retirées seront également
distribuées.

#### 16.3.3 Create Storage Provider

Pour devenir un fournisseur de stockage, le coureur doit soumettre une proposition, et les validateurs actifs actuels peuvent voter sur cette proposition.
validateurs actifs peuvent voter sur cette proposition. Une fois la proposition adoptée, le
nouveau fournisseur de stockage sera créé automatiquement.

Greenfield sépare les rôles de validateur et de fournisseur de stockage.
Bien qu'il soit naturel pour les validateurs de maintenir un nombre significatif et sain de fournisseurs de stockage, il devrait y avoir un équilibre entre les deux.
nombre significatif et sain de fournisseurs de stockage, il devrait toujours y avoir des incitations
pour les validateurs de gérer un nombre raisonnable de FS. Les validateurs
Les validateurs obtiendront plus de récompenses pour les défis de données s'il y a plus de fournisseurs de stockage.
fournisseurs de stockage. Le flux de paiement qui est utilisé pour les récompenses de défi de données
serait le suivant :

Réserves pour les défis de données = (1 - \frac{1}{Nombre de FS + 1}) * Pourcentage maximum $$$

Le défi de la disponibilité des données sera abordé dans la section suivante.

#### 16.3.4 Supprimer un fournisseur de stockage

Toute personne peut soumettre une proposition de retrait d'un fournisseur de stockage pour les raisons suivantes
le fournisseur de stockage ne fournit pas un bon service ou préfère arrêter
service. Les validateurs actifs actuels peuvent voter sur cette proposition. Une fois que cette
proposition est adoptée, le fournisseur de stockage ne pourra plus accepter de nouvelles
d'accepter de nouvelles demandes de stockage d'objets, mais aura toujours l'obligation de répondre aux demandes de requêtes. Autre
Fournisseurs de Stockage ou les propriétaires de données devraient commencer à demander de déplacer les données de
données de ce PE "à supprimer". Le FS "à supprimer" doit faciliter le déplacement des données
données afin qu'il puisse récupérer l'intégralité de son dépôt et éviter de nouvelles coupures.
En fait, même s'il choisit de ne pas coopérer, les données peuvent être récupérées auprès des
les autres FS. Une fois que toutes les données ont été migrées, ce FS "à supprimer" peut retirer tout son dépôt et ce FS "à supprimer" peut retirer tout son dépôt.
peut retirer tout son dépôt, et ce FS sera supprimé.

## 17 Modèles de métadonnées de stockage

Les modèles de données de base pour le stockage Greenfield sont :

- bucket (ou bucket)

- objet

- groupe

- permission

Ces métadonnées sont stockées en tant qu'état de la blockchain dans le stockage persistant de la blockchain Greenfield.
de la blockchain Greenfield.

### 17.1 Bucket

Bucket est l'unité de regroupement des "objets" de stockage. Le BucketName doit être
unique au monde. Chaque compte utilisateur peut créer un Bucket. Le compte
deviendra le "propriétaire" du bucket.

Chaque bucket doit être associé à son propre FS primaire, et aux paiements
de paiement pour Read et Store. L'adresse du propriétaire sera le compte de paiement
compte de paiement par défaut.

### 17.2 Objet

L'objet est l'unité de base pour stocker des données sur Greenfield. Les métadonnées de l'objet
l'objet seront stockées sur la blockchain de Greenfield :

- nom et ID

- propriétaire

- bucket qui l'héberge

- taille et horodatage

- type de contenu

- somme de contrôle pour les éléments de stockage

- état du stockage

- informations sur le FS associé

Les métadonnées d'objet sont stockées avec le nom du bucket comme préfixe de la clé.
Il est possible d'itérer à travers tous les objets sous le même bucket, mais
il est possible d'itérer à travers tous les objets sous le même godet, mais cela peut être un travail lourd pour un grand godet avec beaucoup d'objets.

### 17.3 Groupe

Un groupe est un ensemble de comptes ayant les mêmes permissions. Le nom du groupe
n'est pas autorisé à être dupliqué sous le même utilisateur. Cependant, un
groupe **ne peut pas créer ou posséder** une ressource. Un groupe **ne peut pas être
membre** d'un autre groupe non plus.

Une ressource ne peut avoir qu'un nombre limité de groupes associés à elle
pour les permissions. Cela garantit que la vérification des permissions sur la chaîne peut être
peut être terminée dans un temps constant.

### 17.4 Permission

Le bucket, l'objet, le groupe sont tous des ressources (le compte de paiement est un autre type de ressource mais il est traité dans le paiement).
de ressource, mais il sera traité plus tard dans la section sur les paiements). Chaque ressource
Chaque ressource a un ID unique et le module de permission utilise ces ID pour contrôler comment
les ressources sont accessibles.

#### 17.4.1 Propriétaire

Le propriétaire des ressources fait référence au compte qui crée la ressource. Par
Par défaut, seul le propriétaire de la ressource a le droit d'accéder à ses ressources.

- Le créateur de la ressource est propriétaire de la ressource.

- Chaque ressource n'a qu'un seul propriétaire et la propriété ne peut pas être transférée une fois que la ressource est créée.

- Certaines fonctions permettent à une adresse d'"approuver" une autre adresse.
  Il existe des fonctionnalités qui permettent à une adresse d'"approuver" une autre adresse pour créer et télécharger des objets qui seront la propriété de l'adresse de l'approbateur, tant que cela reste dans les limites.

- Le propriétaire ou le compte de paiement du propriétaire paie la ressource.

#### 17.4.2 Définitions des permissions

- Permission de propriété : Par défaut, le propriétaire a toutes les permissions sur la ressource.

- Permission publique ou privée : Par défaut, la ressource est
  ***private***, seul le propriétaire peut accéder à la ressource.
  Si une ressource est ***public***, tout le monde peut y accéder.

- Permission partagée : Ces permissions sont gérées par le module
  d'autorisation. Il gère généralement qui a la permission pour quelles ressources.

Il existe deux types de permissions : **La permission d'utilisateur unique** et **La permission d'utilisateur de groupe**, qui
sont stockées dans des formats différents dans l'état de la blockchain.

##### Permission d'utilisateur unique

- Bucket: `0x10 | ResouceID(Bucket) | Address(Grantee) ➝ Protobuf(PermissionInfo)`
- Object: `0x11 | ResouceID(Object) | Address(Grantee) ➝ Protobuf(PermissionInfo)`
- Group: `0x12 | ResouceID(Group) | Address(Grantee) ➝ Protobuf(PermissionInfo)`

```go
type permissionInfo struct {
  ActionList     []Action  // [GetObject,PutObject...]
  resourceList   []string  // optional，For prefix resource.
  Allow          Effect    // optional, For some scenarios where some permissions need to be prohibited
}
```

##### Permission d'un groupe d'utilisateurs

- Bucket: `0x20 | ResouceID(Bucket)  ➝ Protobuf(GroupPermissionInfo)`
- Object: `0x21 | ResouceID(Object)  ➝ Protobuf(GroupPermissionInfo)`
- Group: `0x22 | ResouceID(Group)  ➝ Protobuf(GroupPermissionInfo)`

```go
type GroupPermissionInfo map[uint32]permissionInfo // groupID ➝ permissionInfo mapping, mapsize limit to 20?
```

#### 17.4.3 Suppression de permissions

Les utilisateurs peuvent supprimer activement une ou plusieurs permissions. Cependant, lorsqu'une
ressource est supprimée, les permissions qui lui sont associées doivent également être supprimées,
peut-être pas par l'utilisateur qui prend l'initiative de la supprimer, mais par d'autres
mécanismes de nettoyage. Car si trop de comptes ont des permissions sur l'objet
objet à supprimer, cela prend trop de temps à traiter dans le cadre d'une
traitement de la transaction.

#### 17.4.4 Exemples

Les permissions typiques pour les ressources sont listées ci-dessous.

| Permission Type | Bucket                                     | Object                                | Group                                        |
| --------------- | ------------------------------------------ | ------------------------------------- | -------------------------------------------- |
| Write           | ✅ Allow PutObject                          | ❌                                     | ✅ Allow AddMember                            |
| Read            | ✅ Allow ListObject                         | ✅ Allow GetObject                     | ✅ Allow ListMember As a member of this group |
| Full Control    | ✅ Allow Put/ListObject, Allow DeleteBucket | ✅ Allow GetObject, Allow DeleteObject | ✅ Allow DeleteMember, Allow ListMember       |
| Execute         | ❌                                          | ✅ Allow Execute                       | ❌                                            |
Disons que Greenfield possède deux comptes, Bob(0x1110) et Alice(0x1111). A
scénario de base serait le suivant :

- Bob a téléchargé une photo nommée avatar.jpg dans un bucket nommé "profil" ;

- Bob accorde à Alice la permission d'action GetObject pour l'objet avatar.jpg,
  il stockera une clé `0x11 | ResourceID(profile_avatar.jpg) | Address(Alice)` dans un arbre d'état de permission.

- Lorsqu'Alice veut lire le fichier avatar.jpg, le FS doit vérifier dans la blockchain Greenfield si la clé est valide.
  blockchain Greenfield que la clé `Prefix(ObjectPermission) | ResourceID(profile_avatar.jpg) | Address(Alice)` existe dans l'arbre d'état des permissions, et si l'action a été exécutée.
  l'arbre d'état des permissions, et si la liste d'actions contient GetObject.
  Passons à des scénarios plus complexes :

- Bob a créé un bucket nommé "profil"

- Bob accorde la permission de l'action PutObject pour le bucket "profil".
  à Alice, la clé `0x10 | ResourceID(profile) | Address(Alice)`
  sera placée dans l'arbre d'état des permissions.

- Quand Alice veut télécharger un objet nommé avatar.jpg dans le bucket "profile", elle crée une action Putject.
  profil, elle crée une transaction PutObject qui sera exécutée sur la chaîne.
  exécutée sur la chaîne.

- La blockchain Greenfield a besoin de confirmer que Alice a la permission
  d'opérer, elle vérifie donc si la clé `0x10 |
  ResourceID(profile) | Address(Alice)` existait dans l'arbre d'état de la permission
  et obtient les informations de permission si elles existent.

- Si les informations de permission montrent qu'Alice a la permission de l'action PutObject
  du profil du bucket, elle peut alors effectuer l'opération PutObject.

Un autre scénario plus complexe qui contient des groupes :

- Bob crée un groupe nommé "Games", et crée un bucket nommé "profile".

- Bob ajoute Alice au groupe "Games", la clé `0x12 | ResourceID(Games)
  | Adresse(Alice)` sera placée dans l'arbre des permissions.

- Bob met une image avatar.jpg dans le bucket profile et accorde la permission de l'action
  CopyObject au groupe Games.

- Quand Alice veut copier l'objet avatar.jpg . Tout d'abord, la blockchain Greenfield
  vérifie si elle a la permission via la clé `0x11 |
  ResourceID(avatar.jpg) | Address(Alice)` ; si c'est un échec,
  Greenfield va itérer tous les groupes que l'objet avatar.jpg
  associe et vérifiera si Alice est membre de l'un de ces groupes en contrôlant
  groupes en vérifiant, par exemple, si la clé `0x21 | ResourceID(groupe, par ex.
  Jeux)` existait, puis itérer la carte `permissionInfo`, et déterminer si Alice est dans
  un groupe qui a la permission d'effectuer l'opération CopyObject par le biais de la clé
  `0x12| ResourceID(Games) | Address(Alice)`

## 18 Gestion du stockage des charges utiles

Même si les métadonnées seront stockées sur la blockchain Greenfield, les
données de contenu qui seront stockées sur Greenfield sont ici appelées "payload" et
elles sont stockées hors chaîne, sur les fournisseurs de stockage.

L'unité de ce stockage est l'"objet", et chaque objet est divisé et stocké de manière intégrale et redondante.
et stocké de manière intégrale et redondante pour garantir la disponibilité.

### 18.1 Segments

Le segment est la structure de stockage de base d'un objet. La charge utile d'un objet
est composée d'un ou plusieurs segments en séquence. La taille du segment par
par défaut est de 16MB. Si la taille de l'objet est inférieure à 16 Mo, il n'a qu'un seul segment et la taille du segment est la même que celle de l'objet.
segment et la taille du segment est la même que celle de l'objet. Pour
objets plus grands, les données utiles seront divisées en segments.

Veuillez noter que les données utiles d'un objet sont divisées en segments de même taille.
segment de même taille, sauf le dernier segment, qui correspond à la taille réelle. Pour
Par exemple, si un objet a une taille de 50 Mo, seule la taille du dernier segment est de 2 Mo.
segment est de 2 Mo et les tailles des autres segments sont toutes de 16 Mo.

<div align="center"><img src="./assets/18.1%20Object%20Segmentation.jpg"  height="50%" width="50%"></div>
<div align="center"><i>Figure 18.1 Object Segmentation</i></div>

### 18.2 Code d'effacement et redondance des données

#### 18.2.1 Conception de la redondance des données

Bien que chaque FS puisse fournir un service plus stable et ne s'arrêtera pas
et ne s'éteindra pas, car suffisamment BNB s'associent pour former un FS.
stratégie de redondance afin de se débarrasser de la dépendance à l'égard d'un seul FS et d'assurer la disponibilité des données dans un système décentralisé.
de soutenir la disponibilité des données de manière décentralisée. Voici l'idée de base de la
idée de base de la conception.

Premièrement, tous les segments de chaque objet sont stockés dans le FS primaire en tant que "morceaux",
qui peuvent être considérés comme une réplique de l'objet. Les utilisateurs peuvent télécharger
ces données directement à partir du FS primaire, car il est censé fournir les
données complètes avec une faible latence.

Ensuite, le code d'effacement (EC) est introduit pour obtenir une redondance efficace des données.
redondance des données. Le segment est la limite pour effectuer le codage d'effacement. En
En codant l'effacement d'un segment à la fois, il est possible d'effectuer le
traitement du téléchargement de l'objet sans attendre la fin de la charge utile
l'ensemble de la charge utile de l'objet. La stratégie EC par défaut est 4+2, 4 morceaux de données et 2 morceaux de parité pour un segment.
chunks de parité pour un segment. La taille des morceaux de données est de ¼ du segment.
Comme un segment typique est de 16M, un morceau de données typique de EC est de 4M.
Une personnalisation spécialisée des paramètres de l'EC pour chaque utilisateur peut être fournie
via des transactions spéciales.

Tous les morceaux EC de chaque objet sont stockés dans certains FS secondaires en tant que morceaux,
qui peuvent être considérés comme plus d'une réplique EC de l'objet. Si un
Si un ou plusieurs segments de l'objet sont perdus dans le FS primaire, n'importe quel 4
chunks de 6 Fournisseurs de Stockage peuvent récupérer les segments.

Toutes ces informations sur les segments et les Fournisseurs de Stockage sont stockées sur la blockchain Greenfield
en tant que métadonnées de l'objet. Les répliques EC de chaque segment du même objet
segments sont stockés dans la même séquence de Fournisseurs de Stockage secondaires.
Cette convention permet d'économiser la taille des métadonnées. Un exemple d'un objet de 50M
stocké avec un FS primaire, FS0, et 6 FS secondaires, FS1-FS6.
dans le diagramme ci-dessous.

<div align="center"><img src="./assets/18.2%20EC%20for%20Segments%20in%20Different%20Secondary%20SPs.jpg"  height="80%" width="80%"></div>
<div align="center"><i>Figure 18.2 EC pour les segments dans différents fournisseurs de Stockage secondaires</i></div>

#### 18.2.2 Code d'effacement

Le module EC est défini comme la structure suivante.

```go
type Erasure struct {
    encoder func () Encoder
    
    dataBlocks, parityBlocks int
    chunkSize                int64
}
```
Le *encodeur* indique le type de fonction de l'algorithme EC. Les *blocs de données*
et *parityBlock* sont les principaux paramètres de l'algorithme EC. L'adresse
*chunkSize* indique la taille de chaque tesson après le codage. En considérant
le scénario d'application de Greenfield, *dataBlocks* est fixé à 4 ;
*parityBlocks* est de 2 ; et le *chunkSize* est configuré à 16MB, ce qui correspond à la taille du morceau.
correspondant à la taille de la pièce. Reed-Solomon est utilisé comme algorithme EC
est utilisé comme algorithme EC. Le module EC possède une fonction Encode pour diviser les données et les coder en 6 blocs (4 blocs de données).
données et les coder en 6 blocs (4 blocs de données et 2 blocs de parité).
pour reconstruire les données à partir des blocs.

Le module EC dispose de deux fonctions supplémentaires：

1. Remplissage automatique. Si la taille du dernier bloc n'est pas divisible par 4,
   le module d'encodage EC ajoutera des données de remplissage dans le segment.
   segment qui n'est pas plus de 3 octets ;

2. Traitement parallèle basé sur la taille des tessons pour une vitesse optimale.

##### 18.2.2.1 Encodage

Voici une configuration détaillée de l'encodage EC.

<div align="center"><img src="./assets/18.3%20EC%20Encoding.jpg" height="80%" width="80%"></div>
<div align="center"><i>Figure 18.3 EC Encoding</i></div>

Comme dans l'exemple présenté dans la figure ci-dessus, la charge utile de 50M de l'objet
sera divisée en segments (16M chacun) et chaque segment sera codé par la fonction
par la fonction Encode du module EC. Tous les segments peuvent être
traités simultanément. Chaque segment est encodé en 4 blocs de données
(indiqués par un rectangle orange)et 2 blocs de parité (indiqués dans le
rectangle vert).

Si la taille du dernier segment est inférieure à 16MB, il sera encodé en tant que
une partie indépendante. Mais si elle est inférieure à 500k, elle sera
considéré comme étant fusionné avec le segment précédent.

Si la taille du dernier bloc n'est pas divisible par 4, il sera ajouté de
1-3 octets par la fonction de remplissage automatique du module EC. Après que tous les
segments ont été codés, nous avons 16 pièces de 16M et 6 pièces de 0,5M.
6 pièces de 0,5M.

Le logiciel client de l'utilisateur et le FS primaire sont tous deux responsables de ce qui suit
l'encodage de l'EC. Le logiciel client peut ne pas télécharger la parité de l'EC mais seulement
mais seulement la somme de contrôle pour que le FS primaire la vérifie.

Du FS primaire aux FS secondaires, chaque fragment d'EC est traité comme un objet pièce et un flux de données est maintenu.
objet et un flux de données est maintenu pour chaque FS secondaire pour un traitement
traitement parallèle. Les morceaux sont stockés dans une structure de données appelée "piece
store" sur les différents Fournisseurs de Stockage. Comme implémentation de référence, la clé de l'objet
pièce est *objId_s+segIndex\_ spIndex+ ECIndex* pour chaque segment.
Le *spIndex* peut indiquer vers quel secondaire le message sera acheminé. L'adresse
*ECIndex* est l'index des mandrins EC, avec lesquels 0-3 sont des blocs de données et
4-5 sont des blocs de parité. Par exemple, le morceau appelé obj0Id_s1_sp1 est
le 2ème segment de l'objet et sera transmis à FS1.

##### 18.2.2.2 Décodage : Récupération des données

Lorsque le FS primaire perd un segment, lui ou d'autres FS peuvent récupérer les
données par l'intermédiaire des chunks EC. Tel qu'il est conçu, l'indice ECIndex avec les valeurs 0-3 sont des blocs de données tandis que 4-5 sont des blocs de parité.
blocs de données tandis que 4-5 sont des blocs de parité. Il existe deux cas de traitement
pour reconstruire la charge utile de l'objet :

1. Tous les blocs de données sont entièrement stockés dans les FS secondaires. L'initiateur de la récupération
   initiateur de la récupération peut juste lire les pièces qui sont des blocs de données
   séquentiellement et les assembler ;

2. Certains blocs de données ont été perdus par les FS secondaires. L'initiateur de la récupération
   initiateur de récupération doit lire tous les blocs de données et les blocs de parité et
   utiliser la fonction Decode du module EC pour récupérer le contenu de tous les segments.
   tous les segments.

## 19 Le défi de la disponibilité des données

La première priorité de tout réseau de stockage décentralisé est toujours de
garantir l'intégrité et la disponibilité des données. La plupart des solutions existantes
solutions existantes reposent sur le calcul intensif pour générer des preuves. Cependant,
Greenfield choisit la voie de la surveillance sociale et des défis.

L'objectif global de Greenfield est de s'assurer que le fournisseur de stockage (FS) stocke les données comme prévu.
stocke les données comme prévu sont les suivants :

a. Le FS primaire divise correctement l'objet original que l'utilisateur télécharge en
segments correctement.

b. La FS primaire code les segments en morceaux redondants de code d'effacement
et les distribue au FS secondaire comme convenu.

c. Le FS stocke les pièces attribuées soit en tant que rôle du FS primaire
ou de FS secondaire, et les données stockées ne doivent pas être corrompues ou falsifiées.
ou falsifiés.

Un utilisateur doit s'assurer que l'objet stocké sur Greenfield est bien le sien sans télécharger l'ensemble de l'objet.
son objet sans télécharger l'objet entier et en comparer le contenu.
contenu. De plus, chaque FS doit stocker le bon élément pour chaque objet.
objet, et cette information doit être vérifiée sur la blockchain de Greenfield.
blockchain Greenfield. Une structure spéciale de métadonnées est introduite pour
chaque objet pour les défis de données comme ci-dessous :

```go
type ObjectInfo struct {
    …
    root         Hash  // primary FS object root, the hash of segments' hashes
    subRootList []hash //secondary FS object root, the hash of local pieces' hashes
    …
}
```
Each storage provider will keep a local manifest for the pieces of each
object that are stored on it. For the primary FS, the local manifest
records each segment's hashes. The "*root*" field of the object's
metadata in the above code stores the hash of the whole local manifest
of the primary FS, e.g., it is the "*PiecesRootHash(FS0)*" in the below
diagram. For the secondary Fournisseurs de Stockage, the local manifest records each piece's
hashes, and the hash of their local manifest files are recorded in the
subRooList field in order, e.g. the 4th element of this list will store
the 4th secondary FS's "*PiecesRootHash(FS4)*" in the below diagram.

<div align="center"><img src="./assets/19.1%20Hashes%20for%20Data%20Integrity.jpg" height="80%" width="80%"></div>
<div align="center"><i>Figure 19.1 Hashes for Data Integrity</i></div>

These root hashes serve as the checksum for the data segments and
redundancy pieces.

### 19.1 The Initial Data Integrity and Redundancy Metadata

The user-side client software will perform some work:

1. Split the object file into segments if necessary;

2. Calculer le hachage racine de tous les segments ;

3. Calculer l'EC et calculer les hachages pour les pièces de parité ;

4. Envoyer des transactions à la blockchain Greenfield pour demander la création de
   l'objet avec les informations ci-dessus.

En plus d'envoyer les informations à la blockchain Greenfield, le logiciel client les envoie également à la FS primaire et télécharge l'objet.
client envoie également les mêmes informations au FS primaire et télécharge les données de
sur celui-ci. Pour que le FS primaire stocke les segments originaux de l'objet, il doit vérifier l'identité de l'objet.
l'objet, le FS doit vérifier le hash racine pour vérifier l'intégrité du segment.
segment. Le FS doit également calculer les pièces EC par lui-même et vérifier le hachage.
le hachage. Tous les hachages seront enregistrés dans un fichier manifeste stocké
manifeste stocké localement chez le FS, et le hash racine du fichier sera soumis à la blockchain
la blockchain Greenfield dans la transaction "Seal". La blockchain Greenfield
vérifiera les hachages de la transaction Seal par rapport à la transaction de demande de création d'objet afin de garantir l'intégrité des données.
transaction de demande de création d'objet afin d'assurer l'intégrité des données, puisqu'elles sont
la valeur convenue entre les FS primaires et les utilisateurs.

Ces hachages et les fichiers manifestes correspondants seront utilisés pour vérifier les données dans le défi de la disponibilité des données, comme le montre le tableau ci-dessous.
les données dans le défi de la disponibilité des données, comme décrit ci-dessous.
### 19.2 Data Availability Challenge Process

<div align="center"><img src="./assets/19.2%20Data%20Availability%20Challenge.jpg"  height="80%" width="80%"></div>
<div align="center"><i>Figure 19.2 Data Availability Challenge</i></div>
Ce problème de disponibilité des données est illustré dans la figure 19.2 ci-dessus.

Les validateurs Greenfield ont la responsabilité de vérifier la disponibilité des données auprès des FS.
Ils forment un comité de vote pour exécuter cette tâche en incitant les FS à payer des frais et des amendes potentielles (barres obliques).

Une logique de multi-signature, par exemple une multi-signature basée sur BLS, est utilisée pour atteindre un autre niveau de consensus hors chaîne entre les FS.
un autre niveau de consensus hors chaîne parmi les validateurs Greenfield.
Lorsque le validateur vote pour le défi de données, il cosigne une attestation et la soumet à la chaîne.
attestation et la soumettent dans la chaîne.

Le mécanisme global de contestation de la disponibilité des données fonctionne comme suit :

1. N'importe qui peut soumettre une transaction pour contester la disponibilité des données. L'information de contestation de
   Les informations de contestation seront écrites dans l'événement on-chain
   déclenché après le traitement de la transaction.

2. La deuxième façon de déclencher la contestation est plus courante : à la fin de la phase de traitement des blocs de chaque bloc, Greenfield utilisera une fonction de contestation de la disponibilité des données.
   à la fin de la phase de traitement de chaque bloc, Greenfield utilisera un
   algorithme aléatoire pour générer certains événements de défi de disponibilité des données.
   de données. Toutes les informations relatives au défi seront conservées sur la chaîne
   jusqu'à ce que le défi soit confirmé ou expiré.

3. Chaque validateur doit exécuter un module de vérification de la disponibilité des données hors chaîne.
   module. Ce programme garde la trace des informations de défi sur la chaîne
   et lance ensuite une vérification de la disponibilité des données hors chaîne.
   de données hors chaîne. Il vérifie si une donnée est disponible dans la FS spécifiée en réponse à l'événement de défi.
   FS spécifiée en réponse à l'événement de défi, peu importe que l'événement soit
   que l'événement soit déclenché par le challenger individuel ou par la
   chaîne Greenfield elle-même. Il y a trois étapes pour effectuer la
   vérification :

   a. Demandez au PE contesté cette donnée et le manifeste local de l'objet.
   de l'objet. Si les données attendues ne peuvent pas être téléchargées, la pièce doit être considérée comme indisponible.
   l'objet doit être considéré comme indisponible.

   b. Calculer le hachage du manifeste local et le comparer avec le hachage de la racine qui est enregistré dans les métadonnées.
   avec le hachage racine correspondant qui est enregistré dans les métadonnées de l'objet.
   l'objet. S'ils sont différents, la pièce doit être considérée comme étant
   indisponible.

   c. Calculer la somme de contrôle de la pièce contestée et la comparer à la somme de contrôle connexe enregistrée dans la base de données locale.
   avec la somme de contrôle correspondante enregistrée dans le manifeste local.
   local. S'ils sont différents, la pièce doit être considérée comme indisponible.
   comme indisponible.

   L'un ou l'autre des cas d'"indisponibilité" ci-dessus marquera le succès de la contestation
   que la donnée est indisponible, et le validateur votera
   "indisponible".

4. Le validateur utilise sa clé privée BLS pour signer un vote de contestation de données en fonction du résultat.
   en fonction du résultat. Les données à voter doivent être les mêmes pour
   tous les validateurs : elles doivent inclure l'en-tête du bloc qui contient le
   bloc qui contient le défi, l'information sur le défi de données, et le résultat du défi.
   le résultat du défi.
   
5. Les votes du défi de la disponibilité des données sont propagés à travers le réseau p2p.

6. Une fois qu'un validateur a recueilli un accord de plus de 2/3 validateurs, une "attestation" est conclue.
   "attestation" est conclue. Le validateur peut agréger les signatures, assembler l'attestation de défi de données et soumettre une attestation.
   l'attestation de défi de données, et soumettre une transaction d'attestation. Afin de
   de résoudre le problème des validateurs qui se contentent de suivre les résultats des autres
   et n'effectuent pas la vérification eux-mêmes, une logique de " commit-and-reveal " sera
   introduite.

7. La transaction d'attestation du défi des données sera exécutée
   sur la chaîne. Le premier validateur qui soumet l'attestation
   peut obtenir une récompense pour la soumission, tandis que la soumission ultérieure sera
   rejetée. Plus le validateur accumule de votes, plus il peut obtenir de récompenses.
   il peut obtenir. Outre les récompenses de soumission, il existe des récompenses d'attestation.
   également des récompenses d'attestation. Seuls les validateurs dont les votes ont été intégrés dans l'attestation seront récompensés.
   l'attestation seront récompensés, il se peut donc que certains validateurs
   aient voté, mais que leurs votes n'aient pas été assemblés par le validateur. Ils
   ne seront pas récompensés pour ces défis de disponibilité des données. De même, pour
   résultats différents, les récompenses seront différentes : le résultat "indisponible" qui
   Le résultat "indisponible" qui réduit les FS obtiendra plus de récompenses pour les validateurs.

8. Au bout d'un certain nombre de blocs, par exemple 100 blocs, le défi de la disponibilité des données expirera même si les soumissions de données sont toujours en cours.
   défi expirera même si les soumissions d'attestations ne sont pas
   arrivées. Dans un tel cas, le défi expirera simplement sans autre action.

9. Une fois qu'un cas de disponibilité des données est contesté avec succès, c'est-à-dire que
   c'est-à-dire qu'il est confirmé que les données ne sont pas disponibles avec un service de qualité, il y aura un délai de réflexion pour que les données soient disponibles.
   service de qualité, les FS disposeront d'un délai de réflexion pour retrouver, récupérer ou
   récupérer ou déplacer cette donnée.

10. Une fois le délai de réflexion expiré, la disponibilité de cette donnée peut être à nouveau remise en cause si cette donnée n'est pas disponible.
   être remise en question si cette donnée est toujours indisponible,
   le PEI sera à nouveau réduit.

## 20 Transactions de stockage

La blockchain Greenfield prend en charge une série de transactions pour créer,
mettre à jour et supprimer les ressources Greenfield.

Les transactions de création de seaux et d'objets doivent interagir avec les FS pour s'assurer qu'ils sont prêts.
Fournisseurs de Stockage pour s'assurer qu'ils sont prêts, tandis que les opérations liées aux groupes et aux
n'ont pas besoin de cela.

Les utilisateurs doivent toujours créer un bucket avant de pouvoir stocker des objets.
objets.

Le nom du bucket Greenfield suit la même spécification de nommage que le nom du bucket AWS S3
bucket name. Il doit être unique au niveau mondial.

La transaction CreateBucket doit comporter les informations suivantes :

- expéditeur, qui peut être dérivé du signataire de la transaction

- nom du bucket

- l'identifiant du FS que le bucket et tous les objets sous ce bucket
  utiliseront comme FS primaire

Il existe une transaction DeleteBucket correspondante. Elle exige que tous
les objets sous le bucket doivent être supprimés en premier. Comme décrit dans la
section précédente, le propriétaire du bucket peut supprimer n'importe quel objet sous son
bucket.

La création d'objets est décrite dans la partie 1. Il existe une transaction correspondante
DeleteObject correspondante. La suppression indique à Greenfield de rembourser
les frais réservés et de réduire le flux de paiement.

Il existe des transactions de création et de suppression de groupes et de gestion des membres.

Il existe des transactions de création et de suppression de permissions, car elles
sont la fonctionnalité de base de l'économie.

Plus digne d'être souligné, toutes ces transactions peuvent être déclenchées
via l'infrastructure cross-chain des contrats intelligents de la BSC et des EOA.

Il y a quelques transactions concernant la modification du FS primaire des utilisateurs.
des utilisateurs. Elles seront asynchrones car l'action peut prendre un certain temps en fonction du nombre et de la taille des objets.
sur le nombre et la taille des objets dans le bucket. Le bucket doit
être "scellé" à nouveau par le nouveau FS primaire.

## 21 Facturation et paiement

Greenfield facturera les utilisateurs en deux parties. Premièrement, chaque
transaction nécessitera des frais de gaz pour payer le validateur Greenfield pour
écrire les métadonnées sur la chaîne. Deuxièmement, les fournisseurs de services facturent aux utilisateurs
leur service de stockage. Ce paiement s'effectue également sur le Greenfield. Cette section
Cette section traite de ce dernier point : comment ces frais de service hors-chaîne sont facturés
et facturés.

Il existe deux types de frais pour le service hors chaîne : les frais de stockage d'objets et les frais de lecture de paquets.
stockage d'objets et les frais de lecture :

1. Chaque objet stocké sur Greenfield est facturé en fonction de sa taille, de son type de contenu et d'autres paramètres.
   taille, du type de contenu et d'autres paramètres.

2. Il existe un quota gratuit pour la lecture des objets des utilisateurs en fonction de leur taille, de leur type de contenu, etc.
   taille, du type de contenu et d'autres paramètres. En cas de dépassement, c'est-à-dire si les données de l'objet
   données de l'objet ont été téléchargées trop de fois, FS limitera la bande passante
   pour d'autres téléchargements. Les utilisateurs peuvent augmenter le niveau de leur forfait de données pour
   pour obtenir plus de quotas de téléchargement. Chaque paquet de données a un prix fixe.

Comme décrit dans la partie 1, les frais sont payés sur Greenfield à la manière de
"flux" des utilisateurs vers les FS à un taux constant. Les frais sont facturés
chaque seconde au fur et à mesure de leur utilisation.

### 21.1 Concepts et formules

Le flux est un mouvement constant, à la seconde près, de fonds d'un compte émetteur vers un compte récepteur.
compte émetteur à un compte récepteur. Au lieu d'envoyer des transactions de paiement
de paiement, Greenfield enregistre le solde statique, la dernière mise à jour, l'horodatage et le débit dans son module de paiement.
de la dernière mise à jour, l'horodatage et le débit dans son module de paiement.
solde dynamique avec une formule utilisant ces données dans les enregistrements. Si le
débit net n'est pas nul, le solde dynamique changera au fil du temps.
s'écoule.

#### 21.1.1 Terminologie

- **Module de paiement:** Il s'agit d'un module spécial et d'un système de grand livre
  gérant la facturation et le paiement sur la blockchain Greenfield.
  Les fonds seront déposés ou facturés à partir du solde ou des comptes de paiement des utilisateurs dans ce module de paiement.
  comptes de paiement des utilisateurs dans ce module de paiement.

- **Compte de flux** : Le module de paiement possède son propre grand livre pour
  gestion de la facturation. Les utilisateurs peuvent déposer et retirer des fonds dans
  leurs "comptes" correspondants sur le grand livre du module de paiement. Ces
  Ces comptes sont appelés "comptes de flux", qui interagissent directement
  avec les fonctions de paiement de flux et facturent aux utilisateurs le service de
  service de stockage et de données.

- Compte de paiement** : Le compte de paiement a déjà été abordé dans d'autres
  sections de la partie 1 et de la partie 3. Il s'agit en fait d'un type de
  compte de flux. Les utilisateurs peuvent créer différents comptes de paiement et
  et l'associer à des buckets différents à des fins différentes.

- **Payment Stream:** Chaque fois que les utilisateurs ajoutent/suppriment/modifient un objet de stockage ou téléchargent un paquet de données, ils ajoutent ou modifient un ou plusieurs comptes de paiement.
  de données, ils ajoutent ou modifient un ou plusieurs "flux de paiement" pour ce service.
  "flux de paiement" pour ce service fourni par les FS.

- **Flow Rate** : Le taux par seconde auquel un expéditeur diminue son flux de sortie net et augmente le flux de réception.
  flux de sortie net et augmente le flux d'entrée net d'un récepteur.
  lors de la création ou de la mise à jour d'un flux de paiement.

- **Taux de flux net** : Le taux par seconde auquel le solde d'un compte change.
  change. Il s'agit de la somme des flux entrants et sortants du compte.
  du compte.

- **Emetteur** : Le compte de flux qui démarre le flux de paiement en
  spécifiant un récepteur et un débit à partir duquel son flux net diminue.
  diminue.

- **Récepteur** : Le compte de flux à l'extrémité de réception d'un ou plusieurs flux de paiement.

- **CRUD Timestamp** : L'horodatage du moment où l'utilisateur crée, met à jour,
  ou supprime un flux de paiement.

- **Solde delta** : Le montant du solde du compte de flux qui a
  changé depuis le dernier horodatage CRUD en raison du flux. Il peut être
  positif ou négatif.

- **Solde statique** : Le solde du compte de flux au dernier
  horodatage CRUD.

- Solde dynamique** : Le solde réel d'un compte de streaming. Il s'agit de
  la somme de la balance statique et de la balance delta.

Lorsque le compte de flux d'un utilisateur est initié dans le module de paiement par
dépôt, plusieurs champs seront enregistrés pour ce compte de flux :

- CRUD Timestamp - sera l'horodatage du moment.

- Static Balance - sera le montant du dépôt.

- Netflow Rate - sera égal à 0.

- Buffer Balance - sera égal à 0.

#### 21.1.2 Formule

*Solde statique = Solde initial au dernier horodatage CRUD*.

*Solde delta = Taux de débit net \* Secondes écoulées depuis le dernier horodatage CRUD*.

*Solde actuel = solde statique + solde delta*.

*Solde du tampon = - débit net *Temps de réserve préconfiguré si le débit net est négatif*.


<div align="center"><img src="./assets/21.1%20How%20a%20User%20Receives%20Inflow%20and%20Outflow%20of%20Funds.jpg"  height="60%" width="60%"></div>
<div align="center"><i>Figure 21.1 How a User Receives Inflow and Outflow of Funds</i></div>

Chaque fois qu'un utilisateur crée, met à jour ou supprime un flux de paiement, de nombreuses variables des formules ci-dessus sont mises à jour.
variables des formules ci-dessus seront mises à jour et les comptes de flux des utilisateurs dans le module de
module de paiement seront réglés.

- Le flux net du compte de flux de l'utilisateur dans le module de paiement
  sera recalculé pour compenser tous ses flux entrants et sortants en ajoutant/supprimant les nouveaux flux.
  d'entrée et de sortie en ajoutant/supprimant le nouveau flux de paiement par rapport au
  débit net actuel. Par exemple, lorsqu'un utilisateur crée un nouvel objet dont le
  dont le prix est de 0,4 $/mois, son débit net sera augmenté de 0,4 $/mois.

- Si le taux de flux net est négatif, la quantité de BNB associée sera
  être réservé dans un solde tampon. Il est utilisé pour éviter que le solde dynamique
  dynamique ne devienne négatif. Lorsque le solde dynamique devient inférieur au seuil
  le seuil, le compte sera réglé de manière forcée.

- L'horodatage CRUD deviendra l'horodatage actuel.

- Le solde statique sera recalculé. Le solde dynamique précédent
  sera réglé. Le nouveau solde statique sera le solde actuel
  Le nouveau solde statique sera le solde actuel plus le changement du solde de la mémoire tampon.

#### 21.1.3 Types et interfaces

```go
type PaymentConfig struct {
    // Time duration which the buffer balance need to be reserved for NetOutFlow e.g. 6 month
    ReserveTime      uint64
    // Time duration threshold of forced settlement.
    // If dynamic balance is less than NetOutFlowRate * forcedSettleTime, the account can be forced settled.
    ForcedSettleTime uint64
}
```

```go
type StreamPayment struct {
    CRUDTimestamp uint64
    NetflowRate   int64
    StaticBalance uint64
    BufferBalance uint64 // reserved balance for a period, e.g. 1 day
}
```

```go
type PaymentKeeperI interface {
    GetStorePrice(replicaNum, size uint64) (uint64, error)
    GetReadPackagePrice(packageType ReadPackageType) (uint64, error)
    UpdatePaymentFlow(from, to Address, rate int64) error
    LiquidateAccount(addr Address) error
}
```
### 21.2 Flux de travail clé

#### 21.2.1 Dépôt et retrait

Tous les utilisateurs (y compris les FS) peuvent déposer et retirer des BNB dans le module de paiement.
module. Le StaticBalance dans la structure de données StreamPayment sera
sera "réglée" en premier : l'horodateur CRUDTimeStamp sera mis à jour et le StaticBalance
sera compensé par le DeltaBalance. Ensuite, les numéros de dépôt et de retrait
essaieront d'ajouter/réduire le StaticBalance dans l'enregistrement. Si le solde statique
est inférieur au montant du retrait, le retrait échouera.

Le dépôt/retrait via cross-chain sera également pris en charge pour permettre aux
aux utilisateurs de déposer ou de retirer directement de la BSC.

Plus précisément, le dépôt de paiement peut être déclenché automatiquement pendant
la création d'objets ou l'ajout de paquets de données. Tant que
les utilisateurs disposent d'actifs dans leurs comptes d'adresse et de paiement, le module de
module de paiement peut facturer directement les utilisateurs en déplaçant les fonds des comptes d'adresses.
comptes d'adresses.

#### 21.2.2 Flux de paiement

Les flux de paiement circulent dans un seul sens. Chaque fois que les utilisateurs déposent
de leurs comptes d'adresses vers les comptes de flux (y compris le compte de paiement par
compte de paiement par défaut des utilisateurs et d'autres comptes de paiement), les fonds vont d'abord
les fonds passent d'abord des comptes d'adresses des utilisateurs à un compte système géré par le module de paiement.
module de paiement, bien que la taille des fonds et les autres paramètres de paiement soient enregistrés sur le compte de flux des utilisateurs.
seront enregistrés sur le compte de flux des utilisateurs, c'est-à-dire l'enregistrement StreamPayment,
dans le grand livre du module de paiement. Lorsque le paiement est réglé, les fonds
passeront du compte système aux comptes d'adresses des FS en fonction de leur
leur calcul du flux entrant.

Chaque fois que les utilisateurs effectuent les actions suivantes, leur enregistrement StreamPayment sera
sera mis à jour :

- La création d'un objet créera un nouveau flux vers le compte système.

- La suppression d'un objet entraîne la suppression d'un flux sur le compte système.

- L'ajustement des paquets de données pour la lecture/téléchargement permettra de
  créer/supprimer/mettre à jour les flux associés.

Le flux du compte système vers les fournisseurs de stockage sera mis à jour
ensemble lorsque les utilisateurs effectuent les actions ci-dessus. Le débit entrant de
FS sera également enregistré avec précision dans le module de paiement, comme par exemple
la taille totale stockée (en tant que FS primaire ou secondaire), etc. Le flux entrant total
Le flux entrant total sera réparti entre les FS en fonction des enregistrements.

#### 21.2.3 Règlement forcé

Si un utilisateur ne dépose pas pendant une longue période, son dépôt précédent peut être utilisé pour les objets stockés.
épuisé pour les objets stockés. Greenfield dispose d'un mécanisme de règlement forcé
pour s'assurer que suffisamment de fonds sont garantis pour les frais de service ultérieurs.

Il existe deux configurations, ReserveTime et ForcedSettleTime. Disons que
7 jours et 1 jour. Si un utilisateur veut stocker un objet au prix de
environ 0,1 $ par mois(0,00000004 $/seconde), il doit réserver des frais
pour 7 jours dans le solde du tampon, qui est de `0,00000004 $ * 7 * 86400 =
$0.024192`. Si l'utilisateur dépose initialement 1$, l'enregistrement du paiement du flux
sera le suivant.

- Horodatage CRUD : 100

- Solde statique : $0.975808

- Taux de flux net : -0,00000004 $/seconde

- Solde du tampon : $0.024192

Après 10000 secondes, le solde dynamique de l'utilisateur est `0.975808 - 10000 * 0.00000

Après 24395200 secondes (environ 282 jours), le solde dynamique de l'utilisateur deviendra négatif.
l'utilisateur deviendra négatif. Les utilisateurs devraient avoir des alarmes pour de tels
alarmes qui leur rappellent de fournir des fonds supplémentaires à temps.

Si aucun fonds supplémentaire n'est fourni et que le solde dynamique plus le solde tampon sont inférieurs au seuil de règlement forcé, le solde dynamique sera négatif.
tampon est inférieur au seuil de règlement forcé, le compte sera réglé de force.
règlement forcé. Tous les flux de paiement du compte seront fermés et le compte sera marqué comme étant hors service.
et le compte sera marqué comme étant déséquilibré. La vitesse de téléchargement pour tous les
objets associés au compte ou au compte de paiement sera
déclassée. Les objets seront supprimés par les FS si aucun financement n'est
fourni dans le cadre du seuil prédéfini.

Le règlement forcé entraînera également des frais, ce qui constitue une autre incitation pour les utilisateurs à réapprovisionner les fonds de manière proactive.
incitant les utilisateurs à réapprovisionner les fonds de manière proactive.

Disons que le ForceSettlementTime est de 1 jour. Après 24913601
secondes (environ 288 jours), le solde dynamique devient `0.975808 -
24913601 *0.00000004 = -0.02073604`, et le solde tampon est de
$0.00345596. Le seuil de règlement forcé est de `86400* 0.00000004 =
0.003456`. Le règlement forcé sera déclenché, et l'enregistrement de l'utilisateur sera le suivant : - 1.
l'enregistrement de l'utilisateur sera le suivant :

- CRUD Timestamp : 24913701

- Balance statique : \$0

- Débit net : \$0/sec

- Solde de la mémoire tampon : \$0

Les validateurs recevront les 0,00345596 $ restants comme récompense. Le compte
compte sera marqué comme "insuffisant" et ses objets seront déclassés
par les FS.

Chaque fois qu'un enregistrement de flux est mis à jour, Greenfield calcule le moment
où le compte sera déséquilibré. Ainsi, Greenfield peut garder une
liste on-chain pour tracer les horodatages du règlement forcé potentiel.
règlement forcé. La liste sera vérifiée à la fin du traitement de chaque bloc.
traitement. Lorsque l'heure du bloc dépasse l'horodatage du règlement forcé,
le règlement des comptes de flux associés sera déclenché
automatiquement.

#### 21.2.4 Compte de paiement

Le compte de paiement est un type spécial de "compte de flux" dans le module de paiement.
de paiement. Les utilisateurs peuvent créer plusieurs comptes de paiement et ont la
l'autorisation de lier des buckets à différents comptes de paiement pour payer le
stockage et le paquet de données.

Les structures de données et l'interface pertinentes sont les suivantes :

```go
// PaymentAccountNum mapping
// key: PaymentAccountNumPrefix | Address
// value: uint64  // counter
// use cases:
// - record the number of payment accounts of a user
// - derive new payment account address from user address
// - PaymentAccountAddress = Hash(OwnerAddress | current_num), increased by 1 when create a new payment account

// key: PaymentAccountPrefix | Address
type PaymentAccount struct {
    Owner        Address
    Withdrawable bool
}

type PaymentKeeperI interface {
    Deposit(from, to Address, amount uint64) error
    Withdraw(from, to Address, amount uint64) error
    CreatePaymentAccount(addr Address) (paymentAccountAddr Address, err error)
    ForbidWithdraw(sender, paymentAccount Address) error
    SetBucketStorePayer(bucket BucketID, sender, payer Address) error
    SetBucketReadDataPayer(bucket BucketID, sender, payer Address) error
}
```

Les comptes de paiement ont les caractéristiques suivantes :

- Chaque utilisateur peut créer plusieurs comptes de paiement. Les comptes
  comptes de paiement créés par l'utilisateur sont enregistrés avec une carte sur la
  blockchain Greenfield.

- Le format de l'adresse du compte de paiement est le même que celui des comptes normaux.
  normaux. Elle est dérivée du hachage de l'adresse de l'utilisateur et de
  l'index du compte de paiement. Le compte de paiement n'existe que dans le
  module de paiement de stockage. Les utilisateurs peuvent effectuer des dépôts, des retraits et
  et consulter le solde des comptes de paiement dans le module de paiement.
  ce qui signifie que les comptes de paiement ne peuvent pas être utilisés pour le transfert ou le jalonnement.

- Les utilisateurs peuvent seulement associer leurs buckets à leurs comptes de paiement
  pour payer le stockage et la bande passante. Les utilisateurs ne peuvent pas associer leurs propres
  Les utilisateurs ne peuvent pas associer leurs propres buckets avec les comptes de paiement des autres, et les utilisateurs ne peuvent pas associer les buckets des autres avec leurs propres comptes de paiement.
  d'autres avec leurs propres comptes de paiement.

- Le propriétaire d'un compte de paiement est l'utilisateur qui l'a créé. Le propriétaire
  peut le rendre non-remboursable. Il s'agit d'un paramètre à sens unique qui ne peut pas être
  révoqué. Ainsi, les utilisateurs peuvent définir certains objets comme des "biens publics" qui
  peuvent recevoir des dons pour le stockage et la bande passante tout en conservant la
  la propriété.

#### 21.2.5 Gel et reprise de compte

Si un compte de paiement est en déséquilibre, il est soldé et un indicateur de déséquilibre lui est attribué.
comme étant en déséquilibre.

Le NetflowRate sera mis à 0, tandis que les paramètres actuels du
stream pay sera sauvegardé dans une autre structure de données. La vitesse de téléchargement
de tous les objets de ce compte sera réduite.

Si quelqu'un dépose sur un compte gelé et que le solde statique est
suffisant pour les frais réservés, le compte sera repris automatiquement. L'adresse
paiement du flux sera récupéré à partir de la sauvegarde.

Pendant la période OutOfBalance, aucun objet ne peut être associé à ce
compte de paiement, ce qui a pour conséquence qu'aucun objet ne peut être créé sous
le bucket associé au compte.

Si l'objet associé est supprimé, les paramètres de paiement du flux de sauvegarde seront modifiés en conséquence pour s'assurer qu'ils reflètent la nouvelle situation.
seront modifiés en conséquence pour s'assurer qu'ils reflètent la dernière version du compte
est repris.

#### 21.2.6 Prix et ajustement des frais de stockage

Les frais de stockage des objets sont calculés en fonction des métadonnées de l'objet
et du temps. L'unité du prix sera le dollar US. Le paiement effectivement
facturé sur Greenfield est le BNB, et le prix du BNB sera soumis par l'oracle.
l'oracle.

Par exemple, si le prix est de 0,03 USD / GB / mois, le prix actuel de BNB
actuel sur la chaîne est de 258 USD, 70% des frais de stockage seront reçus par le
70% des frais de stockage seront perçus par le FS primaire, le reste étant réparti entre les FS secondaires.

Lorsqu'un objet de 123, 456, 789 octets (environ 123 Mo) est scellé,
il y aura 7 flux de paiement mis à jour. Le taux de frais est de `0.03 / 258 *
123456789 / (1024*1024*1024) / (30*24*60*60) = 5.158003812501789e-12`
BNB/seconde.

Let's set the rate as R.

- User -\> Primary FS flow rate: 0.7 \* R

- User -\> Secondary FS 1 flow rate: 0.05 \* R

- User -\> Secondary FS 2 flow rate: 0.05 \* R

- User -\> Secondary FS 3 flow rate: 0.05 \* R

- User -\> Secondary FS 4 flow rate: 0.05 \* R

- User -\> Secondary FS 5 flow rate: 0.05 \* R

- User -\> Secondary FS 6 flow rate: 0.05 \* R

Les enregistrements des flux des comptes de paiement seront ajustés. Si la
temps réservé est de 6 mois, l'utilisateur doit réserver `(R * 6 * 30 * 24 * 60 * 60) = 8,021727529202782e-05` BNB dans le solde tampon.
le solde tampon. Si le solde du compte de paiement n'est pas suffisant, soit l'opération de déclenchement échouera, soit le compte sera clôturé.
échouera ou le compte sera marqué comme "insuffisant".

Le prix du BNB sera soumis par un oracle des relais validateurs Greenfield périodiquement. 
Lorsque le prix est mis à jour, tous les prix des paiements seront calculés avec le dernier prix. 
Mais tous les débits des paiements existants resteront inchangés jusqu'au prochain règlement,
déclenché soit par les nouvelles actions de l'utilisateur comme mettre un nouvel objet ou
le règlement automatique.

La formule de tarification des frais de stockage des objets devrait être stable puisque l'unité de prix est le dollar américain et que le coût des frais de stockage des objets n'est pas le même.
l'unité de prix est l'USD et que le coût du stockage évolue lentement dans le temps. Le site
formule pourrait être suffisamment flexible pour être codée en dur sur la chaîne.

Il se peut que les FS veuillent changer la formule (par exemple pour une mise à jour du modèle commercial).
mise à jour du modèle commercial). Cela sera réalisé par la gouvernance coordonnée des FS et des validateurs.
gouvernance coordonnée des FS et des validateurs.

## 22 Modèles inter-chaînes

Le cadre des Cross chains a été présenté dans la partie 1. Ici, plus de
détails sur la couche de communication et l'économie seront expliqués ici.

### 22.1 Canaux et paquets de communication

#### 22.1.1 Vote par sondage

Une nouvelle communication p2p à travers les relais cross-chain sera introduite.
sera introduite, appelée "Vote Poll". Ce Vote Poll permettra d'échanger des informations sur les
votes signés au sein du réseau. Pour éviter l'inondation de messages, tous les
votes signés expireront après un temps fixe. Les relais Greenfield peuvent
soit mettre des votes, soit récupérer des votes du sondage et les assembler en tant que
transactions de paquets inter-chaînes.

#### 22.1.2 Canal et séquence

Pour permettre le multiplexage et la résistance aux attaques par relecture, les concepts de "canal" et de "séquence" sont introduits pour gérer tout type de communication.
canal" et "séquence" sont introduits pour gérer tout type de communication.
Voici un exemple de définition :

```go
type Package struct {
    PackType     uint8 // SYN, ACK or FAIL_ACK
    SrcChainId   uint16
    DstChainId   uint16
    Sequence     int64
    ChannelId    uint16
    Payload      []byte
    BLSSignature sdk.Sig
    BLSBits      sdk.Bits // indicate the signer of the package
}
```

Les paquets d'un même canal doivent être traités en séquence, tandis que
ils peuvent être traités en parallèle s'ils appartiennent à des canaux différents.

Les messages d'opération sur les différentes ressources Greenfield sont mappés sur des
différents canaux. Par exemple, les buckets et les objets de stockage appartiennent à
différents canaux.

#### 22.1.3 Protocole de fiabilité

Un protocole est défini ici pour garantir la fiabilité de la transmission des données en continu
entre BSC et Greenfield.

Le protocole doit permettre de récupérer les scénarios dans lesquels les données inter-chaînes sont
endommagées, dupliquées ou livrées hors service par les relais. Il
attribue un numéro de séquence à chaque paquet et exige un accusé de réception positif (ACK) de la part des relais.
positif (ACK) de la chaîne cible. Ici, il y a trois types
de paquets :

1. SYN : les paquets initiaux inter-chaînes lancés par les utilisateurs ou les dApps.

2. ACK : l'accusé de réception positif envoyé par la couche ressource de la chaîne cible.
   chaîne cible.

3. FAIL_ACK : l'acquittement négatif envoyé par la couche de communication de la
   de la chaîne cible, généralement causé par des données endommagées ou une
   une incohérence de protocole déclenchée par le cas limite.

Chaque paquet de communication doit commencer par SYN et se terminer par ACK ou
FAIL_ACK. Le code du gestionnaire et les contrats de chaque côté doivent gérer ces
primitives.

#### 22.1.4 Mise à jour du validateur

Avec un schéma multi-signatures agrégeable, par exemple BLS, la chaîne croisée peut être assez légère.
peut être assez légère. Cependant, des données suffisantes doivent être ajoutées
sur le paquet pour indiquer les validateurs qui signent les événements.
Cela peut être réalisé en combinant un bitmap et un ensemble de validateurs sur la chaîne.
Cependant, l'ensemble des validateurs Greenfield est volatile.
doivent synchroniser les informations avec le BSC dès qu'il y a une mise à jour de l'ensemble de
ensemble de validateurs Greenfield. Ceci est mis en œuvre en construisant un client Greenfield
Greenfield sur BSC, qui est similaire au client léger implémenté pour la chaîne de balises BNB sur BSC.
pour BNB Beacon Chain sur BSC.

### 22.2 Économique

Les relais Greenfield jouent un rôle important dans le relais des paquets inter-chaînes.
chaîne. Une incitation adéquate est nécessaire pour que les relais continuent à apporter leur contribution à long terme.
contribution à long terme.

#### 22.2.1 Frais et récompense des paquets inter-chaînes

Les paquets SYN et ACK/FAIL_ACK coûtent tous deux de l'essence pour être relayés, les utilisateurs (ou les
les utilisateurs (ou les smart contracts) devront payer les frais pour couvrir les deux lorsqu'ils
ils lancent les paquets SYN cross-chain.

Pour encourager les relais Greenfield à signer des paquets cross-chain :

1. Le livreur du paquet recevra un ratio fixe des frais de relais comme récompense.

2. Le reste des frais de relais sera distribué de manière égale entre ceux qui signent.

#### 22.2.2 Course pour la livraison de paquets inter-chaînes

Il y a plusieurs relais Greenfield, et ils peuvent se faire concurrence pour soumettre
les paquets multisignés agrégés sur la blockchain Greenfield et la BSC.
BSC. Pour éviter les transactions de course causées par la compétition, qui
concurrence, ce qui entraîne un gaspillage de gaz, les relayeurs effectuent une rotation pour relayer les transactions, par exemple en se relayant toutes les 10 minutes.
toutes les 10 minutes. Chaque paquet cross-chain reçoit un horodatage, si
il n'est pas relayé dans un délai limité lorsque le relayeur désigné
désigné ne remplit pas sa fonction, d'autres relais Greenfield sont autorisés à
relayer un tel paquet.

#### 22.2.3 Callbacks et gaz limité

Les dApps BSC, c'est-à-dire les contrats intelligents sur BSC, sont autorisés à mettre en œuvre leur propre logique pour gérer les ACK ou FA.
propre logique pour traiter les paquets ACK ou FAIL_ACK. Les contrats intelligents peuvent
enregistrer des fonctions de rappel pour traiter les paquets ACK. Comme il est
impossible pour l'infrastructure cross-chain de prévoir la consommation de
consommation de gaz du callback, une estimation de la limitation de gaz doit être définie
par les contrats intelligents qui enregistrent les fonctions de rappel.

Pour tous les paquets cross-chain qui partent du BSC, le contrat intelligent doit spécifier la limitation de gaz pour le BSC.
doit spécifier la limitation de gaz pour le paquet ACK ou FAIL_ACK, les frais du
Les frais de relais sont prépayés en conséquence sur BSC. Les relais peuvent rembourser les
rembourser les frais excessifs plus tard.

#### 22.2.4 Contrats d'infrastructure inter-chaînes sur BSC

La logique inter-chaînes est également mise en œuvre sur Greenfield sous forme de contrats intelligents.
contrats intelligents. Mais ces contrats ne seront plus implémentés sur BSC comme le
Mais ces contrats ne seront plus implémentés sur BSC en tant que contrat de genèse, mais simplement en tant que contrats évolutifs. La mise à niveau
La mise à niveau sera contrôlée par l'accord des validateurs de Greenfield à travers
un processus de gouvernance. La conception peut tirer pleinement parti des contrats normaux
normaux, par exemple en contournant la limite de taille de 24k en déléguant
en déléguant différentes logiques à différents contrats d'implémentation.

### 22.3 Traitement des erreurs et des défaillances

Des erreurs et des défaillances peuvent se produire pendant la communication
chaîne.

Un type d'erreur provient du protocole inter-chaînes lui-même et est marqué par
par "FAIL_ACK". Cela signifie que le protocole lui-même rencontre des erreurs fatales,
et qu'il ne peut pas achever le transport du paquet inter-chaînes avant même qu'il ne soit
avant de toucher la couche supérieure à la couche de communication. Ce problème est généralement causé par
des bogues du système qui entraînent une corruption ou une incohérence des données.

L'autre type est l'erreur au-dessus de la couche de communication, par exemple,
les erreurs déclenchées par une logique incorrecte ou des bogues dans la couche miroir des ressources
ou la couche d'application. Ces cas doivent toujours renvoyer un "ACK" à la couche de
la couche de communication, mais le paquet ACK doit contenir suffisamment d'informations
suffisamment d'informations pour que la couche miroir des ressources ou la couche application
pour revenir à l'état initial.

<div align="center"><img src="./assets/22.3%20Error%20and%20Failure%20Handling.jpg"  height="60%" width="60%"></div>
<div align="center"><i>Figure 22.1 Cross-chain Error and Failure Handling</i></div>

Lorsque Greenfield émet un paquet ACK ou FAIL_ACK, les callbacks enregistrés de
callbacks enregistrés des dApps BSC (c'est-à-dire les contrats intelligents) seront appelés pour traiter le paquet, mais ces fonctions peuvent échouer à traiter le paquet.
traiter le paquet, mais ces fonctions peuvent échouer à traiter les paquets
ACK/FAIL_ACK en raison de bogues ou d'exceptions dans les callbacks,
ces paquets seront placés dans une autre file d'attente qui appartient aux
BSC dApps.

Les dApps BSC correspondants peuvent réessayer le paquet, par exemple avec une limite de gaz plus élevée, ou simplement sauter le paquet.
limite de gaz plus élevée, ou simplement sauter le paquet pour tolérer l'échec, ou même mettre à niveau
son contrat pour gérer les cas particuliers. Les dApps BSC ne peuvent pas démarrer de nouveaux
paquets cross-chain s'il y a des paquets en attente d'échec dans leur file d'attente.
file d'attente. Il demande aux dApps BSC de traiter les paquets défaillants en
séquence.

La couche de communication peut attraper n'importe quelle exception lancée par la couche miroir des ressources ou par la couche d'application, de sorte que la livraison des paquets soit assurée.
ou la couche applicative, de sorte que la livraison des paquets ne soit pas bloquée par des
applications personnalisées.

## 23 API de FS

La FS doit fournir de nombreuses API pour faciliter la recherche d'informations par les utilisateurs, le téléchargement d'objets, la récupération de données, etc.
informations, de télécharger les objets, de récupérer les données, et d'envoyer des
transactions sur la blockchain Greenfield. Cette section sera
étendue au fil du temps.

Tous les prestataires de services devraient fournir les API énumérées dans cette section.

### 23.1 Point d'accès universel

#### 23.1.1 Norme URI

Tous les objets peuvent être identifiés et accessibles via un chemin universel :

*gnfd://\<nom_du_bucket\>\<nom_de_l'objet\>*?\[paramètre\]*

*où:*

- *"gnfd://" est l'identifiant principal fixe, qui est obligatoire*.

- *nom_du_bucket est le nom du bucket de l'objet, obligatoire*.

- *object_name est le nom de l'objet, obligatoire*.

- *parameter est une liste de paires clé-valeur pour les informations supplémentaires pour l'URI, ce qui est facultatif*.

Ce chemin doit être mappé 1:1 à un objet. Il est utile de mentionner ici que si
nous voulons faire référence au même objet même s'il a été supprimé et recréé, nous pouvons
ajouter le paramètre `If-Match-Checksum` à l'URI. Par exemple *gnfd://mybucket/myobject?If-Match-Checksum=qUiQTy8PR5uPgZdpSzAYSw0u0cHNKh7A+4XSmaGSpEc=*.


#### 23.1.2 HTTFS REST API

Chaque FS enregistrera plusieurs points de terminaison pour accéder à ses services, par ex.
"FS1" peut demander à ses utilisateurs de télécharger des objets via
[https://greenfield.sp1.com/download](https://greenfield.sp1.com/download).

Le point d'accès le plus important est celui qui permet aux utilisateurs de télécharger des objets. Pour
Pour télécharger un objet, les utilisateurs n'ont qu'à remplacer le "gnfd://" de l'URI standard par le point d'extrémité FS.
par le point de terminaison FS. Par exemple, pour accéder à
gnfd://mybucket/foo/bar.jpg, les utilisateurs peuvent simplement visiter FS1 à l'adresse suivante
[https://greenfield.sp1.com/download/mybucket/foo/bar.jpg](https://greenfield.sp1.com/download/mybucket/foo/bar.jpg).

Lorsque FS1 reçoit la requête vers ce chemin d'accès, il doit comprendre que les
utilisateurs veulent télécharger l'objet à
gnfd://mybucket/foo/bar/my-cool-object-id. FS1 doit d'abord déterminer quelle FS
est le FS primaire actuel de cet objet, si c'est le FS1 lui-même, le FS1
devrait commencer à envoyer les données à l'utilisateur ; sinon, FS1 enverra un
HTTP 302 pour rediriger la demande vers le point final de téléchargement du FS primaire.

#### 23.1.3 P2P RPC

Veuillez noter que les nœuds complets de la blockchain Greenfield (y compris les validateurs) et les FS fourniront des RPC P2P pour accéder à différentes données.
validateurs) et les FS fourniront des RPC P2P pour accéder à différentes données.

Les RPC des nœuds complets de la blockchain Greenfield seront des points d'accès pour lire et modifier les données de la blockchain.
lire et modifier les données de la blockchain, par exemple, les utilisateurs peuvent vérifier la hauteur actuelle du bloc et les informations sur l'ensemble des validateurs.
les utilisateurs peuvent vérifier la hauteur actuelle des blocs et les informations sur l'ensemble des validateurs, ou envoyer des transactions pour créer un bloc.
bucket.

Les FS P2P RPCs sont sous un protocole P2P différent principalement pour la lecture des données,
qui est conçu sur la base du protocole BitTorrent. Tout logiciel client
qui veut utiliser cette fonctionnalité doit intégrer ce protocole P2P.

Une chose à noter est que Greenfield met en œuvre la permission et le contrôle d'accès afin que les données transférées vers le serveur soient protégées.
d'accès de sorte que les données transmises au réseau P2P doivent être
cryptées avec les clés publiques des utilisateurs.

### 23.2 Opérations de liste

Il existe de nombreuses opérations permettant de "lister" des informations sur Greenfield.
Par exemple, il est possible d'énumérer tous les objets d'un bucket, tous les membres d'un groupe ou tous les utilisateurs d'une base de données.
membres d'un groupe ou tous les objets associés à un compte de paiement.
de paiement. Ces opérations sont généralement trop lourdes pour être prises en charge directement
par le biais d'une blockchain Greenfield full node RPCs. Les prestataires de services doivent donc fournir
fonctions via les API correspondantes afin que les utilisateurs aient une meilleure
expérience pour stocker, vérifier, télécharger et gérer les objets.
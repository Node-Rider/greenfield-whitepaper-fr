Livre blanc # Greenfield

L'objectif de BNB Greenfield est de libérer le pouvoir de la technologie décentralisée de la blockchain et du stockage sur la propriété et l'économie des données.

BNB Greenfield n'est pas seulement une nouvelle blockchain dans BNB, mais aussi une infrastructure et un écosystème visant à faciliter le développement de la blockchain décentralisée.
mais aussi une infrastructure et un écosystème destinés à faciliter l'économie des données
économie de données décentralisée. Elle tente d'y parvenir en facilitant le processus de stockage et de gestion de l'accès aux données et en reliant la propriété des données à l'économie des données.
et de gérer l'accès aux données et en liant la propriété des données au contexte massif de DeFi
dans le contexte de la BSC.

Il se concentre sur 3 parties qui diffèrent des systèmes de stockage centralisés et décentralisés existants : les
systèmes de stockage centralisés et décentralisés existants :

- Il permet aux adresses compatibles avec Ethereum de créer et de gérer à la fois des données et des actifs de jetons.

- Il lie nativement les permissions et la logique de gestion des données au BSC en tant qu'actifs échangeables et programmes de contrats intelligents
  avec tous les autres actifs.

- Il offre aux développeurs des primitives d'API et des performances similaires à celles du stockage dans le cloud Web2 existant.

Greenfield devrait constituer un terrain de jeu et d'essai
pour les nouveaux modèles d'économie des données et de dApp, qui finiront par faire partie des
la base du Web3.

Le livre blanc de ce dépôt décrit la conception et la mise en œuvre principales de la plateforme.
mise en œuvre de la plateforme. De nombreuses idées sont basées sur les grandes
contributions d'autres protocoles et équipes de premier plan. Veuillez vous référer aux
sections de remerciements.

Toutes les opinions constructives, les idées et les commentaires sont les bienvenus.

Nous espérons que vous apprécierez le voyage !

## Table des matières

- [Aperçu](./overview.md)
- [Partie 1 Conception de GreenField et de l'économie de stockage décentralisée](./part1.md)
  - [1 Principes de conception](./part1.md#1-principes-de-conception)
  - [2 Hypothèses](./part1.md#2-hypothèses)
  - [3 L'architecture en général](./part1.md#3-larchitecture-en-général)
    - [3.1 Noyau GreenField](./part1.md#31-noyau-greenfield)
    - [3.2 BNB Greenfield dApps](./part1.md#32-les-dapps-de-bnb-greenfield)
    - [3.3 La chaîne croisée avec BSC](./part1.md#33-la-chaîne-croisée-avec-bsc)
    - [3.4 La trinité](./part1.md#34-la-trinité)
  - [4 Noyau GreenField](./part1.md#4-noyau-de-bnb-greenfield)
    - [4.1 La blockchain BNB GreenField](./part1.md#41-la-blockchain-bnb-greenfield)
    - [4.2 Les fournisseurs de stockage](./part1.md#42-les-fournisseurs-de-stockage-sp)
    - [4.3 La synergie des paires](./part1.md#34-la-trinité)
  - [5 Le stockage des données Greenfield](./part1.md#5-le-stockage-des-données-de-greenfield)
    - [5.1 Données avec consensus](./part1.md#51-données-avec-consensus)
      - [5.1.1 Comptes et solde](./part1.md#511-comptes-et-solde)
      - [5.1.2 Métadonnées du validateur et de la PS](./part1.md#512-métadonnées-du-validateur-et-du-ps)
      - [5.1.3 Métadonnées de stockage](./part1.md#513-métadonnées-de-stockage)
      - [5.1.4 Métadonnées de permission](./part1.md#514-métadonnées-dautorisation)
      - [5.1.5 Métadonnées de facturation](./part1.md#515-métadonnées-de-facturation)
    - [5.2 Stockage des données des objets de données utiles hors chaîne](./part1.md#52-stockage-des-données-utiles-de-lobjet-hors-chaîne)
      - [5.2.1 PS primaires et secondaires](./part1.md#521-fournisseurs-de-stockage-primaires-et-secondaires)
      - [5.2.2 Redondance des données](./part1.md#522-redondance-des-données)
  - [6 Storage Economics and Its Primitives](./part1.md#6-économie-du-stockage-et-ses-primitives)
    - [6.1 Création de compte](./part1.md#61-création-de-compte)
    - [6.2 Création d'objets de données](./part1.md#62-création-dobjets-de-données)
    - [6.3 Stockage des données](./part1.md#63-stockage-des-données)
    - [6.4 Lecture et téléchargement des données](./part1.md#64-lecture-et-téléchargement-de-données)
    - [6.5 Permissions et groupe](./part1.md#65-permissions-et-groupes)
    - [6.6 Frais et paiements](./part1.md#66-fees-and-payments)
    - [6.7 Défi d'intégrité et de disponibilité des données](./part1.md#67-défi-de-lintégrité-et-de-la-disponibilité-des-données)
    - [6.8 Suppression des données](./part1.md#68-suppression-de-données)
  - [7 Économie des actifs de données](./part1.md#7-économie-des-actifs-de-données)
    - [7.1 Chaînes croisées avec BSC](./part1.md#71-chaînes-croisées-avec-bsc)
    - [7.2 Framework](./part1.md#72-framework)
    - [7.3 Couche de communication](./part1.md#73-couche-de-communicationla-couche-de-communication-est-composée-dun-ensemble-de-relais-greenfield)
    - [7.4 Couche miroir de ressources](./part1.md#74-couche-miroir-de-ressources)
      - [7.4.1 Miroir d'entité de ressource](./part1.md#741-miroir-dentité-de-ressource)
      - [7.4.2 Primitives d'exploitation inter-chaînes](./part1.md#742-primitives-dexploitation-inter-chaînes)
  - [8 "Pas" de fin pour la conception](./part1.md#8-pas-de-fin-pour-la-conception)
    - [8.1 Accusé de réception](./part1.md#81-remerciements)
- [Partie 2 Showcases dans les labs](./part2.md)
  - [9 Showcases : Stockage décentralisé](./part2.md#9-Showcases--stockage-décentralisé-)
    - [9.1 Hébergement Web et lecteur de cloud personnel](./part2.md#91-hébergement-web-et-personal-cloud-drive)
    - [9.2 Couche de disponibilité des données pour la blockchain publique](./part2.md#92-couche-de-disponibilité-des-données-pour-la-blockchain-publique)
      - [9.2.1 Couche 1 de la blockchain pour l'échange de données](./part2.md#921-échange-de-données-de-blockchain-de-couche-1)
      - [9.2.2 Couche de disponibilité des données pour les rollups de la couche 2](./part2.md#922-couche-de-disponibilité-des-données-pour-les-rollups-de-couche-2)
      - [9.2.3 Instantanés et sauvegardes de données en bloc](./part2.md#923-instantanés-et-sauvegardes-de-données-en-bloc)
  - [10 Showcases : Nouvelles méthodes de publication numérique](./part2.md#10-Showcases--les-nouveaux-modes-dédition-numérique)
    - [10.1 Grass-Root Digital Publishing](./part2.md#101-lédition-numérique-de-base)
    - [10.2 Marché des données](./part2.md#102-marché-des-données)
    - [10.3 Risque : Anti-Piratage](./part2.md#103-risque--anti-piratage)
  - [11 Showcases : Contenu généré par l'utilisateur](./part2.md#11-Showcases--contenu-généré-par-lutilisateur)

    - [11.1 Anti-monopole et anti-censure](./part2.md#111-anti-monopole-et-anti-censure)
    - [11.2 Token Curated Registries](./part2.md#112-registres-créés-par-les-jetons)
  - [12 Showcases : marché des données personnelles](./part2.md#12-Showcases--marché-des-données-personnelles)
  - [13 Des Showcases à la production réelle](./part2.md#13-des-Showcases-à-la-production-réelle)
- [Partie 3 Spécifications techniques simplifiées](./part3.md)
  - [14 Acteurs de l'écosystème](./part3.md#14-acteurs-de-lécosystème)
    - [14.1 Validateurs Greenfield](./part3.md#141-validateurs-greenfield)
    - [14.2 Fournisseurs de stockage (SP)](./part3.md#142-prestataires-de-services-de-stockage-ps)
    - [14.3 Greenfield dApps](./part3.md#143-les-dapps-greenfield)
  - [15 Identifiant de l'utilisateur](./part3.md#15-identifiant-de-lutilisateur)
    - [15.1 Solde de l'utilisateur](./part3.md#151-solde-de-lutilisateur)
  - [16 Greenfield Blockchain](./part3.md#16-blockchain-greenfield)
    - [16.1 Économie des jetons](./part3.md#161-économie-des-jetons)
    - [16.2 Consensus et élection du validateur](./part3.md#162-consensus-et-élection-du-validateur)
    - [16.3 Transactions de gouvernance](./part3.md#163-transactions-de-gouvernance)
      - [16.3.1 Créer et modifier le validateur](./part3.md#1631-)

      - [16.3.2 Distribution des récompenses de jalonnement](./part3.md#1632-distribution-des-récompenses-de-jalonnement)
      - [16.3.3 Créer un fournisseur de stockage](./part3.md#1633-create-storage-provider)
      - [16.3.4 Supprimer le fournisseur de stockage](./part3.md#1634-supprimer-un-fournisseur-de-stockage)
  - [17 Storage MetaData Models](./part3.md#17-modèles-de-métadonnées-de-stockage)
    - [17.1 Bucket](./part3.md#171-bucket)
    - [17.2 Object](./part3.md#172-objet)
    - [17.3 Groupe](./part3.md#173-groupe)
    - [17.4 Permission](./part3.md#174-permission)
      - [17.4.1 Propriété](./part3.md#1741-propriétaire)
      - [17.4.2 Définitions des permissions](./part3.md#1742-définitions-des-permissions)
      - [17.4.3 Suppression des permissions](./part3.md#1743-suppression-de-permissions)
      - [17.4.4 Exemples](./part3.md#1744-exemples)
  - [18 Gestion du stockage des charges utiles](./part3.md#18-gestion-du-stockage-des-charges-utiles)
    - [18.1 Segments](./part3.md#181-segments)
    - [18.2 Code d'effacement et redondance des données](./part3.md#182-code-deffacement-et-redondance-des-données)
      - [18.2.1 Conception de la redondance des données](./part3.md#1821-conception-de-la-redondance-des-données)
      - [18.2.2 Code d'effacement](./part3.md#1822-code-deffacement)
        - [18.2.2.1 Codage](./part3.md#18221-encodage)
        - [18.2.2.2 Décodage : récupération des données](./part3.md#18222-décodage--récupération-des-données)
  - [19 Défi de la disponibilité des données](./part3.md#19-le-défi-de-la-disponibilité-des-données)
    - [19.1 Les métadonnées initiales d'intégrité et de redondance des données](./part3.md#191-the-initial-data-integrity-and-redundancy-metadata)
    - [19.2 Processus de contestation de la disponibilité des données](./part3.md#192-data-availability-challenge-process)
  - [20 Transactions de stockage](./part3.md#20-transactions-de-stockage)
  - [21 Facturation et paiement](./part3.md#21-facturation-et-paiement)
    - [21.1 Concepts et formules](./part3.md#211-concepts-et-formules)
      - [21.1.1 Terminologie](./part3.md#2111-terminologie)
      - [21.1.2 Formule](./part3.md#2112-formule)
      - [21.1.3 Types et interfaces](./part3.md#2113-types-et-interfaces)
    - [21.2 Flux de travail des clés](./part3.md#212-flux-de-travail-clé)
      - [21.2.1 Dépôt et retrait](./part3.md#2121-dépôt-et-retrait)
      - [21.2.2 Flux de paiement](./part3.md#2122-flux-de-paiement)
      - [21.2.3 Règlement forcé](./part3.md#2123-règlement-forcé)
      - [21.2.4 Compte de paiement](./part3.md#2124-compte-de-paiement)
      - [21.2.5 Gel et reprise du compte](./part3.md#2125-gel-et-reprise-de-compte)
      - [21.2.6 Prix et ajustement des frais de stockage](./part3.md#2126-prix-et-ajustement-des-frais-de-stockage)
  - [22 Modèles inter-chaînes](./part3.md#22-modèles-inter-chaînes)
    - [22.1 Canaux de communication et paquets](./part3.md#221-canaux-et-paquets-de-communication)
      - [22.1.1 Vote par sondage](./part3.md#2211-vote-par-sondage)
      - [22.1.2 Canal et séquence](./part3.md#2212-canal-et-séquence)
      - [22.1.3 Protocole de fiabilité](./part3.md#2213-protocole-de-fiabilité)
      - [22.1.4 Mise à jour du validateur](./part3.md#2214-mise-à-jour-du-validateur)
    - [22.2 Economique](./part3.md#22-modèles-inter-chaînes)
      - [22.2.1 Frais et récompense des paquets inter-chaînes](./part3.md#2221-frais-et-récompense-des-paquets-inter-chaînes)
      - [22.2.2 Course pour livrer les paquets inter-chaînes](./part3.md#2222-course-pour-la-livraison-de-paquets-inter-chaînes)
      - [22.2.3 Rappels et gaz limité](./part3.md#2223-)

      - [22.2.4 Contrats d'infrastructure inter-chaînes sur BSC](./part3.md#2224-contrats-dinfrastructure-inter-chaînes-sur-bsc)
    - [22.3 Gestion des erreurs et des défaillances](./part3.md#223-traitement-des-erreurs-et-des-défaillances)
 - [23 SP APIs](./part3.md#23-api-de-sp)
    - [23.1 Endpoint universel](./part3.md#231-point-daccès-universel)
      - [23.1.1 URI standard](./part3.md#2311-norme-uri)
      - [23.1.2 API REST HTTPS](./part3.md#2312-https-rest-api)
      - [23.1.3 P2P RPC](./part3.md#2313-p2p-rpc)
    - [23.2 Opérations de liste](./part3.md#232-opérations-de-liste)
- [Fin](./ending.md)

## Contribuer

1. Clonez le dépôt et vérifiez une branche.

  ```shell
  git clone https://github.com/bnb-chain/greenfield-whitepaper.git
  git checkout -b <your-branch-name>
  ```
2. Effectuez vos modifications

3. Lint les fichiers avant une pull request

  ```shell
  # install markdownlint-cli from https://github.com/igorshubovych/markdownlint-cli
  markdownlint '**/*.md'  -c .github/workflows/markdownlint.yaml
  ```

4. Soumettre la pull request

## License

Tout le contenu est sous licence [CC BY 4.0] (https://creativecommons.org/licenses/by/4.0/).
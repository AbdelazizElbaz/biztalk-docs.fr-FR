---
title: "Termes et définitions de Common | Documents Microsoft"
description: Glossaire des termes et et leurs significations pour BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac9c7c7d-a97e-425a-9666-02ca6edd8be6
caps.latest.revision: "68"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29af2ae479f1927665ddbb3171a64cd5b6ccfe3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
Les termes et les définitions suivants sont utilisés dans l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name=""></a>.  
  
|Terme|Définition|  
|----------|----------------|  
|fichier .brl|Fichier de définition des règles d'entreprise.|  
|fichier .btm|Fichier de mappage BizTalk Server.|  
|fichier .btp|Un fichier de pipeline BizTalk Server.|  
|.btproj|Un fichier de projet BizTalk.|  
|fichier .btt|Fichier de modèle de suivi|  
|fichier .odx|Fichier d'orchestration BizTalk Server.|  
|fichier .xsd|Fichier de schéma BizTalk Server.|  
|||  
  
## <a name="a"></a>Un  
  
|Terme|Définition|  
|----------|----------------|  
|action|Une ou plusieurs fonctions correspondant à l'élément « THEN » d'une règle et qui déterminent les instructions à exécuter au cas où la condition est réalisée.|  
|Propriété Activer|Propriété de la forme Réception indiquant si l'orchestration est activée ou non lorsqu'un message est reçu. La forme Réception peut être marquée uniquement comme étant activée si elle représente la première forme d'envoi ou de réception activée dans une orchestration.|  
|bloc d'activation|Ensemble d'étapes ou d'actions au sein d'un modèle d'activité.|  
|réception avec activation|Expression abrégée désignant la condition d'une forme Réception pour laquelle la propriété Activer est définie sur True.|  
|modèle d'activité|Suite prédéfinie d'actions pouvant être appelées par les blocs d'activation.|  
|étape du modèle d'activité|Synonyme d'action dans le cadre d'un modèle d'activité. Lorsqu'une action est incluse dans un modèle d'activité, elle est appelée « étape du modèle d'activité ».|  
|nœud d'activité|Nœud qui contient les étapes majeures et les éléments correspondant aux données d'intérêt pour l'analyste d'entreprise. Ce nœud est créé par l'analyste à l'aide des Assistants de Microsoft Excel.|  
|fenêtre d'activité|Définit la période pendant laquelle les données d'instance d'activité sont visibles. Les données évoluent en permanence car le point dans le temps change constamment. Après avoir passé les données via la fenêtre d'activité, vous pouvez les déplacer vers la base de données des archives BAM en exécutant le lot DTS/SSIS de maintenance des données. Une fois déplacées vers la base de données des archives BAM, elles ne sont plus disponibles pour le traitement des requêtes sur le portail BAM.|  
|intervenant|Personne ou processus qui lance une activité ou y participe. Les intervenants peuvent être des initiateurs ou des cibles.|  
|adaptateur|Composant .NET ou COM facilitant l'échange des messages entre les applications (par exemple, un système sectoriel) et BizTalk Server. Chaque adaptateur dispose de composants de conception et d'exécution pour les opérations de réception et d'envoi.|  
|infrastructure d'adaptateurs|Spécifications pour la création d'adaptateurs BizTalk à l'aide de standards ouverts basés sur des services Web.|  
|addenda|Partie d'un accord. Un accord se compose de plusieurs addenda qui définissent le processus d'entreprise utilisé, votre rôle et celui de votre partenaire, de même que les stratégies ou paramètres employés dans cette relation et en stipulent par ailleurs les conditions commerciales et juridiques.|  
|application associée|Entité logique de l'authentification unique de l'entreprise, définie par l'administrateur, qui représente un système ou un sous-système (par exemple, un hôte, un système principal ou une application sectorielle) auquel vous êtes connecté via l'authentification unique. Une application associée peut représenter un système autre que Windows, tel qu'un macroordinateur (grand système) ou un ordinateur fonctionnant sous UNIX. Elle peut également constituer une application SAP ou une sous-classe du système, telle que les sous-systèmes « Avantages » ou « Bulletin de paie ».|  
|agenda|Liste numérotée qui répertorie les actions de la règle devant être exécutées par le moteur de règles.|  
|agrégation|Table ou structure qui contient des données précalculées pour un cube de traitement analytique en ligne (OLAP). Les agrégations prennent en charge l'interrogation rapide et efficace d'une base de données multidimensionnelle.|  
|accord|Il s'agit de l'élément de définition dans la configuration d'une relation. Un accord est basé sur le processus d’entreprise sous-jacent et artefacts de gestion de tiers et est définie entre votre profil personnel et profil de votre partenaire. Il se compose d’un ou plusieurs addenda. Ces addenda définissent le processus d'entreprise utilisé, le rôle de votre organisation, celui de votre partenaire et les paramètres utilisés pour la relation commerciale. Les accords peuvent concerner aussi bien des profils de partenaires individuels que des profils de groupe de partenaires. Cela facilite la gestion des partenaires qui ont des relations commerciales identiques avec votre organisation.|  
|notification d'alerte|Technique utilisée pour avertir un utilisateur ou un groupe d'utilisateurs d'une situation spécifique prédéfinie.|  
|alias|Autre nom donné à un tiers. Chaque tiers reçoit un alias par défaut unique composé d'un nom (organisation), d'un qualificateur (nom de l'organisation) et d'une valeur (nom du tiers). Cet alias est toujours considéré comme étant l'alias par défaut et comprend toujours un nom, un qualificateur et une valeur. Dans la base de données de gestion BizTalk, la paire qualificateur-valeur doit être unique pour chaque tiers.|  
|Tous, PremièreCorrespondance|Modes d'exécution utilisés dans les étapes de pipeline. « Tous » indique une exécution linéaire des composants du pipeline au cours d'une étape. « PremièreCorrespondance » désigne une exécution sûre dans laquelle le premier composant qui reconnaît le format du message l'utilise. Lorsque l'exécution est linéaire, tous les composants d'une étape sont exécutés dans l'ordre avant que le message ne soit transmis à l'étape suivante.|  
|ANSI X.12|Format de message mis au point par l'Institut national américain de normalisation (ANSI, American National Standards Institute). Le format X.12 est principalement utilisé aux États-Unis.|  
|adaptateur d'application|Adaptateur conçu pour fonctionner avec une application ou un protocole spécifique (SQL par exemple).|  
|données archivées|Données traitées par BizTalk Server et enregistrées dans une base de données appropriée.|  
|artefact|Fait le plus souvent référence à une partie d'une application BizTalk, qui est une unité logique d'une solution BizTalk. Les artefacts sont gérés et déployés à l'aide de la console Administration de BizTalk. Il peut s'agir par exemple d'orchestrations, pipelines, schémas de message, certificats de sécurité, stratégies d'entreprise, liaisons, etc. Ils constituent également les parties d'un projet BizTalk, autre unité logique d'une solution BizTalk. Dans ce contexte, les artefacts permettent de générer les assemblys dans Visual Studio qui composent la solution BizTalk.|  
|assembleur|Composant de pipeline qui regroupe des documents individuels en un seul lot. Les composants de pipeline assembleur livrés avec BizTalk Server incluent un Assembleur de fichier plat, un Assembleur BizTalk Framework et un Assembleur XML.|  
|assembly|Fichier .dll pouvant contenir des ressources telles que des orchestrations, des pipelines, des schémas, des mappages, etc. qui ne sont pas propres à BizTalk Server, mais doivent être utilisés dans une application BizTalk.|  
|déploiement d'assembly|Processus consistant à déployer les ressources d'un assembly à partir de Visual Studio dans une application BizTalk.|  
|Assistant Déploiement des assemblys|Dans BizTalk Server 2004, il s'agissait d'un Assistant pour vous guider tout au long des étapes d'insertion, de suppression, d'importation et d'exportation des assemblys, des étapes d'importation et d'exportation des liaisons ainsi que des étapes d'installation et de désinstallation des assemblys dans le Global Assembly Cache (GAC). Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cette fonctionnalité n'est pas disponible dans les Assistants Importation, Installation et Exportation.|  
|version de l'assembly|Identificateur d'un assembly, composé d'une version mineure et d'une version majeure.|  
|orchestration atomique|Transaction de courte durée qui permet d'appliquer la sémantique de validation et de restauration d'une transaction « ACID » (atomicité, cohérence, isolement et durabilité) de la même manière qu'une application COM+ utilisant le service DTC.|  
|attribut|En langage XML, terme utilisé pour décrire une construction destinée à associer des informations supplémentaires à des éléments XML.|  
|Approuvé(e) par authentification|Méthode de marquage des applications permettant d'indiquer si l'application est en mesure d'envoyer ou non des messages à MessageBox avec un ID tiers (PID) différent (c'est-à-dire, dont l'alias est différent) de l'ID de sécurité Windows appartenant au compte de service de l'instance d'application.|  
  
## <a name="b"></a>B  
  
|Terme|Définition|  
|----------|----------------|  
|BAM|Voir Analyse BAM (Business Activity Monitoring).|  
|activité BAM|Liste de l'intégralité des étapes majeures et des données capturées par BAM pour une unité de travail à analyser. Par exemple, une application d'emprunt pourra contenir des étapes majeures telles que « Emprunt approuvé » et des données comme « Nom du candidat » et « Montant de l'emprunt ». Les activités BAM sont souvent directement mappées vers un processus d’entreprise.|  
|alerte BAM|Une alerte est une notification générée par l'infrastructure BAM (très exactement, par SQL Server Notification Services) pour informer le destinataire de l'existence d'un ensemble donné de conditions. Les utilisateurs définissent les conditions qui, lorsqu'elles sont remplies, entraînent la génération d'une alerte par des services automatisés.|  
|point de contrôle BAM|Également appelé « élément » dans le complément BAM pour Excel.|  
|configuration BAM|Fichier XML qui contient, pour les manifestes BAM, des paramètres tels que le nom de la base de données d'importation principale BAM et celui du serveur.|  
|Définition BAM|Représentation XML d'un modèle d'observation BAM.|  
|Infrastructure BAM|Ensemble d'interfaces API gérées qui prennent en charge la concentration des événements et des infrastructures créés de façon dynamique.|  
|infrastructure BAM|L'infrastructure de l'analyse BAM se compose de tables SQL Server, de vues BAM, de procédures stockées et de lots DTS (Data Transformation Services) situés dans les bases de données BAM (bases de données d'importation principale, des archives, de schémas en étoile et d'analyse) tel que cela est configuré et géré par le biais de développements incrémentiels de définitions BAM. Cette infrastructure est l'endroit où, lors de l'exécution, les événements sont corrélés, agrégés, puis rendus disponibles aux requêtes des utilisateurs.|  
|Gestionnaire BAM|Composant interne qui gère l'infrastructure dynamique de l'analyse BAM (Business Activity Monitoring).|  
|modèle d'observation BAM|Définition de niveau élevé des exigences de visibilité pour un processus d'entreprise. Cette définition comprend les étapes majeures et les événements de données à récupérer (activité BAM), une description des agrégations de données et une présentation des informations aux utilisateurs (vue BAM).|  
|vue BAM|Manière de présenter les données constituant une activité BAM propre aux rôles. Elles permettent d'afficher des données filtrées ainsi que des agrégations de ces données et de présenter ces données filtrées de différentes manières (dans un graphique croisé dynamique, par exemple). L'analyse BAM prend en charge la définition d'une ou de plusieurs vues par activité.|  
|élément de données de base|Au sein de l'analyse BAM, élément d'activité servant de base pour une dimension ou une mesure. L'élément de données de base « ID de produit » peut par exemple être utilisé comme base de calcul pour une mesure de type Nombre (nombre d'unités vendues pour un produit donné).|  
|liaison|Processus par lequel des composants logiciels et des couches sont reliés. Les relations de liaison et de dépendance des composants sont établies au moment où un composant réseau est installé. La liaison permet aux composants de communiquer entre eux. Dans BizTalk Server, une liaison est un mappage entre le point de terminaison d'un adaptateur d'orchestration non spécifié (port ou lien de rôle) et les points de terminaison d'un adaptateur physique spécifique (tiers ou ports d'envoi/de réception).|  
|fichier de liaison|Fichier qui comporte la capture instantanée de la liaison. Il ne contient aucune information concernant l'aboutissement de cette liaison par rapport à l'orchestration.|  
|console Administration de BizTalk|Console MMC (Microsoft Management Console) utilisée pour administrer un groupe BizTalk Server.|  
|groupe d'administrateurs BizTalk|Groupe chargé d'administrer BizTalk Server. Les tâches d'administration incluent, entre autres, l'accès à la file d'attente des messages interrompus et la mise à jour de la base de données de configuration.|  
|application BizTalk|Groupe d'artefacts, de ressources et de paramètres associés, exposés ensemble pour une gestion depuis la console Administration de BizTalk. Tout artefact d'une application peut faire référence à un autre artefact de cette même application ou d'une autre application référencée.|  
|BizTalk Application 1|Application créée par défaut pour chaque nouvelle installation de BizTalk Server. Cette application est créée principalement pour des raisons de compatibilité avec les versions antérieures. Ce dossier contient les artefacts déployés sans qu'une application ait été spécifiée. Les nouveaux artefacts déployés sans qu'une application ait été spécifiée sont déployés dans l'application par défaut. Vous pouvez définir toute autre application en tant qu'application par défaut en modifiant un paramètre utilisateur.|  
|groupe Utilisateurs d'applications BizTalk|Groupe d'utilisateurs qui disposent d'un droit d'accès aux bases de données MessageBox pour un groupe BizTalk donné.|  
|vue Application de BizTalk|Une des deux vues (avec la vue Déploiement de BizTalk) qui s'affiche à l'ouverture de la console System Center Operations Manager pour BizTalk Server. Un administrateur BizTalk utilise cette vue pour analyser le fonctionnement des artefacts et des applications BizTalk, tels que des orchestrations, des ports d'envoi et des emplacements de réception.|  
|Assembly BizTalk|Fichier DLL de Microsoft Windows contenant des informations de ressource telles que des orchestrations, des pipelines, des schémas et des mappages à utiliser dans une solution d'entreprise BizTalk Server. L'assembly contient également le numéro de version, la culture et les jetons de clé publique.|  
|vue Déploiement de BizTalk|Une des deux vues (avec la vue Application de BizTalk) qui s'affiche à l'ouverture de la console System Center Operations Manager pour BizTalk Server. Un administrateur informatique de l'entreprise utilise cette vue pour analyser le fonctionnement général du « déploiement physique » d'une installation de BizTalk Server.|  
|Éditeur BizTalk|Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], outil graphique de conception des schémas BizTalk Server permettant de définir la structure des messages de l'instance, qu'ils soient XML ou natifs.|  
|Explorateur BizTalk|Fenêtre de l'outil Visual Studio dans laquelle s'affiche le contenu d'une base de données de configuration BizTalk. Il présente les assemblys, les ports et les tiers sous forme d'arborescence. Vous pouvez vous en servir pour configurer et gérer les projets, les tiers et les orchestrations BizTalk.|  
|Modèle objet de l'Explorateur BizTalk|Interfaces API utilisées pour créer des outils et des scripts permettant d'automatiser les tâches consécutives au déploiement que vous exécutez habituellement dans l'Explorateur BizTalk. Ces tâches incluent notamment la création de ports, la liaison d'orchestrations, la gestion des propriétés de tiers ou toute autre tâche nécessitant l'Explorateur BizTalk. Les modèles objet de l'Explorateur BizTalk se trouvent dans l'espace de noms Microsoft.BizTalk.ExplorerOM.|  
|BizTalk Framework|Désigne une infrastructure de commerce électronique pouvant fonctionner sur n'importe quelle plate-forme. Elle s'appuie sur des normes industrielles et des schémas XML (Extensible Markup Language). En outre, elle permet l'intégration dans les divers secteurs d'activité et entre les différents systèmes d'entreprise et ce, sans tenir compte des plateformes, des systèmes d'exploitation ou des technologies sous-jacentes.|  
|groupe BizTalk|Un groupe BizTalk est composé de bases de données MessageBox, d'hôtes, d'emplacements de réception, de ports d'envoi, de groupes de ports d'envoi, d'orchestrations, de serveurs et d'adaptateurs.|  
|hôte BizTalk|Processus logique et limite de sécurité dans BizTalk Server. Chaque hôte dispose d'un groupe de sécurité et peut contenir plusieurs instances d'hôte, qui, chacune sur un ordinateur différent, effectuent le travail de l'hôte. À l'inverse, chaque instance d'hôte correspond à un seul hôte et le compte de service de l'instance de l'hôte fait partie du groupe de sécurité de l'hôte. Le groupe de sécurité peut être utilisé pour accorder des droits d'accès à des ressources physiques telles que des bases de données pour qu'elles puissent être utilisées par n'importe quelle instance d'un hôte.|  
|alerte du pack d'administration BizTalk|Notification à laquelle les administrateurs peuvent s’abonner dans le pack d’administration de BizTalk Server. Une fois abonnés à une alerte donnée, les administrateurs reçoivent une notification chaque fois que certaines conditions sont remplies. Par exemple, si un certain nombre d'instances de l'hôte sont limitées, une alerte peut être déclenchée.|  
|diagnostics du pack d'administration BizTalk|Fonctionnalité que les administrateurs peuvent utiliser pour afficher la cause et les informations de résolution d'un problème donné. Par exemple, si le fonctionnement d'un port d'envoi s'affiche en rouge, l'onglet Événement de modification d'état de la console Operations Manager affiche la raison du passage de la couleur verte à la couleur rouge.|  
|Mappeur BizTalk|Dans Visual Studio, outil graphique de conception des mappages BizTalk permettant de définir des transformations de données.|  
|Message Queuing BizTalk|Composant de transport Message Queuing dans BizTalk Server. Il est fourni en tant que composant interne principal de BizTalk Server et représente l'un de ses nombreux composants d'adaptateur.|  
|banque de messages BizTalk|Table du serveur Microsoft SQL Server contenant l'ensemble des messages et leurs éléments. Les orchestrations mobilisées utilisent les références des messages stockés dans la banque de messages pour retirer de la file d'attente une copie du message et de ses propriétés.|  
|projet BizTalk|Type de projet Visual Studio utilisé pour créer des applications exécutant BizTalk Server.|  
|fichier de projet BizTalk (.btproj)|Fichier contenant les paramètres spécifiques à un projet BizTalk.|  
|système de projet BizTalk|Système utilisé pour créer tout ou partie d'une application ou d'une solution d'entreprise BizTalk Server. Il permet d'ajouter, de modifier ou de supprimer des éléments BizTalk Server (par exemple, des orchestrations, des mappages, des schémas ou des pipelines) et est doté de fonctions de compilation et de déploiement.|  
|Pack d’administration de BizTalk Server|Amélioration BizTalk qui garantit des capacités complètes d'analyse des applications et de l'infrastructure BizTalk. Elle inclut des fonctionnalités telles que des diagnostics et des alertes pour analyser le fonctionnement d'un déploiement BizTalk.|  
|Administration de BizTalk Server|Interface de la console MMC (Microsoft Management Console) permettant d'administrer le groupe de serveurs BizTalk Server et leurs propriétés, de contrôler les fonctions de réception ainsi que les opérations contenues dans les files d'attente Microsoft SQL Server et susceptibles d'être utilisées par le groupe de serveurs.|  
|fichier de mappage BizTalk Server (.btm)|Format conservé pour un mappage BizTalk, créé à l'aide du Mappeur BizTalk, et compilé pour générer les directives de transformation spécifiées à l'aide du langage XSLT.|  
|Mappeur BizTalk|Fonctionnalité permettant la création visuelle de transformations entre deux schémas dans une application BizTalk. Elle comporte également des améliorations de la convivialité pour gérer des mappages complexes.|  
|moteur de messagerie BizTalk Server|Ensemble de services requis dans un logiciel intermédiaire pour faciliter l'utilisation des solutions des scénarios clients. Ces services d'exécution représentent un élément essentiel de la plate-forme BizTalk Server. Parmi eux, on trouve un service performant de traitement des messages du pipeline. Le traitement de pipeline permet l'extraction des propriétés et la régularisation du format des données.|  
|fichier de pipeline BizTalk Server (.btp)|Fichier permettant de décrire la configuration du pipeline et de ses composants. Ce type de fichier peut être compilé dans un projet BizTalk.|  
|schéma BizTalk Server|Description de la structure des messages de l'instance BizTalk Server basée sur le format XSD (XML Schema Definition language).|  
|fichier de schéma BizTalk Server (.xsd)|Fichier contenant le format conservé pour un schéma BizTalk.|  
|Panneau de configuration de BizTalk|Fonctionnalité BizTalk que les administrateurs BizTalk peuvent utiliser pour gérer et modifier, de manière centralisée, les paramètres du moteur BizTalk. Les administrateurs peuvent exporter er importer des paramètres d'un environnement à l'autre, comme de la phase intermédiaire à la phase de production.|  
|corps|Voir Corps du message.|  
|BTSTask|Outil de ligne de commande vous permettant de gérer des applications et des assemblys. Vous pouvez utiliser BTSTask pour ajouter une application BizTalk à la base de données de gestion BizTalk, ajouter une ressource dans une application, exporter une application vers un fichier MSI, exporter des informations de liaison dans un fichier, importer une application à partir d'un fichier MSI, importer des informations de liaison d'un fichier, afficher la liste de toutes les ressources d'une application et celle de toutes les applications de la base de données de gestion BizTalk, présenter le contenu d'un fichier MSI, supprimer une application dans la base de données de gestion BizTalk et de la console Administration de BizTalk et pour supprimer une ressource à une application.|  
|BAM (Business Activity Monitoring)|Composant BizTalk Server qui offre aux utilisateurs des activités une vue en temps réel de leurs différents processus d'entreprise, leur permettant ainsi de prendre d'importantes décisions commerciales.|  
|vue Activité d'entreprise|Ensemble de vues hiérarchiques faisant apparaître un ou plusieurs processus d'entreprise et permettant aux utilisateurs des activités de catégories spécifiques de définir l'affichage de leur Activité d'entreprise. Des données d'activité d'entreprise identiques (suivi BAM) peuvent être interprétées de plusieurs façons possibles.|  
|analyste d'entreprise|Utilisateur qui possède des compétences en matière de gestion d'entreprise et d'analyse commerciale. La tâche première d'un analyste d'entreprise consiste à utiliser les données d'entreprise et à les analyser pour connaître les tendances de l'activité de l'entreprise.|  
|utilisateur final d'entreprise|Travailleur de l'information en charge du contrôle et du dépannage d'un processus d'entreprise et/ou des échanges de messages à caractère commercial. Cette personne ne possède pas de connaissances techniques particulières.|  
|services de configuration de processus d'entreprise|Outils permettant aux utilisateurs des activités d'entreprise de configurer et de gérer les éléments d'orchestration de niveau inférieur par le biais de stratégies commerciales. Les développeurs ou les éditeurs de logiciels utilisent ces outils pour définir les processus d'entreprise de sorte qu'ils puissent être configurés à l'aide de stratégies d'entreprise et de paramètres.|  
|espace de travail des processus d'entreprise|Dans cette interface, les responsables commerciaux sont en mesure d'effectuer le suivi et la gestion de l'ensemble des processus d'entreprise à partir de SharePoint Team Services.|  
|profil d'entreprise|Visage commercial d'une organisation. Chaque département d'une organisation, qui entretient des relations commerciales avec un autre département d'une autre organisation, est représenté par un profil d'entreprise dans une solution de gestion des partenaires commerciaux (GPC). Toutes les propriétés qui définissent les paramètres de messagerie interentreprises spécifiques au département, à l'unité commerciale ou au système d'entreprise, sont capturées dans son profil d'entreprise.|  
|Outil Éditeur des règles d’entreprise|Outil basé sur l'interface utilisateur graphique permettant d'élaborer des stratégies.|  
|moteur de règles d'entreprise|Moteur d'inférence d'exécution servant à évaluer les règles par rapport aux faits et à mettre en place des actions en fonction des résultats de l'analyse.|  
|langage des règles d'entreprise|Langage de balisage des règles au format XML permettant d'exprimer des déclarations dans les définitions de règles.|  
|interentreprises|Relatif aux ventes se déroulant par le biais de transactions et d'activités associées entre une entreprise et des acheteurs autres que les consommateurs finaux. Ces acheteurs peuvent être des institutions gouvernementales, des entreprises et des revendeurs. Qualifie une entreprise qui communique avec une autre entreprise ou lui vend des produits.|  
  
## <a name="c"></a>C  
  
|Terme|Définition|  
|----------|----------------|  
|durée calculée|Propriété autorisant l'emploi d'une formule personnalisée dans les colonnes calculées.|  
|liste de codes|Ensemble de paires abréviation-explication utilisées pour faciliter la définition des ensembles de valeurs de type Enumeration XSD (XML Schema Definition language) au moment de la conception.|  
|outil de ligne de commande pour le déploiement|Outils utilisés pour ajouter, supprimer, importer et exporter des assemblys, importer et exporter des liaisons et installer ou désinstaller des assemblys dans le Global Assembly Cache (GAC).|  
|requête de modification de validation|Voir le terme : demande de modification du type fin|  
|modèle de communication|Propriété qui définit si la communication du port est unidirectionnelle ou bidirectionnelle (requête-réponse).|  
|compensation|Ensemble d'actions destinées à annuler ou à atténuer l'effet d'une transaction validée.|  
|onglet Compensation|Surface de conception pour l'ajout d'une compensation à une orchestration.|  
|compilation|Dans un environnement BizTalk Server, processus de conversion de la représentation des éléments BizTalk Server, tels que des schémas, des mappages et des orchestrations, au moment de la conception en leurs opérations équivalentes enregistrées dans les assemblys Visual Studio.|  
|service de composition|Composant qui prend en charge l'activation des actions, la fonction d'interruption et l'envoi des réponses de la tâche. Ce service élabore des messages de protocole d'action, puis les envoie aux ports d'écoute HTTP qui les acheminent ensuite vers la base de données MessageBox pour pouvoir les utiliser.|  
|condition|Élément « IF » d'une règle permettant d'indiquer les conditions à évaluer. Il s'agit d'une expression logique unique qui a pour résultat de se réaliser ou non (True ou False). Une condition est susceptible de prendre en charge les conditions définies par l'utilisateur.|  
|intervalle d'actualisation de cache de configuration|Intervalle, en secondes, pendant lequel les modifications apportées aux propriétés générales d'un groupe BizTalk (propriété d'hôte SMTP, par exemple) sont récupérées. Cet intervalle est défini lors de la configuration du groupe. Lorsque vous démarrez BizTalk Server, tous les éléments d'administration de BizTalk Server tels que les bases de données MessageBox, les propriétés de serveur, les adaptateurs et les connexions à la base de données des suivis sont stockés dans le cache d'administration. Par défaut, tous les éléments du cache sont actualisés toutes les 60 secondes, à l'exception des connexions à la base de données du serveur et des propriétés du serveur.|  
|nom du serveur de la base de données de configuration|Élément de l'interface utilisateur. Nom du serveur sur lequel réside la base de données de gestion ou base de données de configuration.|  
|connecteur|Nom donné au service de communication utilisé lors de l'échange de documents avec vos partenaires commerciaux ou vos systèmes internes.|  
|point de connexion|Élément du Concepteur d'orchestration permettant aux utilisateurs de connecter une forme Envoi ou Réception à un port.|  
|contrainte|Propriété destinée à limiter le rôle de l'initiateur de l'action racine et qui a pour cible toute autre action du modèle d'activité.|  
|routage basé sur le contenu|Routage d'un document en fonction des informations extraites de la charge de ce document. Dans BizTalk Server, le routage basé sur le contenu est effectué à l'aide des fonctions de promotion des propriétés d'un document et de filtrage des expressions sur les orchestrations et les ports d'envoi.|  
|continuation|Capacité à contribuer à une activité BAM unique à partir d'applications différentes, à l'aide de deux identificateurs uniques différents, tels qu'ActivityID. Par exemple, dans une partie d'un processus d'entreprise, le numéro de bon de commande d'un client peut servir à suivre une activité. Dans une autre partie du processus, un numéro interne d'exécution de commandes peut être utilisé pour suivre la même activité. Vous pouvez activer la continuation et mettre en relation le numéro de bon de commande et le numéro d'exécution de commandes afin que les deux parties du processus puissent ajouter des informations à la même activité.|  
|jeton de liaison|Élément d'information unique envoyée de l'Application 1.|  
|taux de conversion|Multiplicateur utilisé pour convertir la devise de base du site Web dans la devise de l'acheteur ou du fournisseur. Ce taux de conversion est stocké dans le site Web secondaire de commande du kit de développement, et ce, à titre indicatif uniquement. Son suivi doit être effectué par un système de gestion ou de comptabilité tiers au sein de sites Web en production.|  
|Corrélation|Processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration. Cette mise en correspondance s'effectue par le biais de propriétés du message qui le lient à l'orchestration. Si des messages relatifs au même processus d'entreprise contiennent des propriétés incompatibles, telles qu'un schéma de bon de commande avec un élément POId et un schéma de facture avec un élément OrderID, alors des développeurs obtiennent la corrélation en créant des schémas de propriété contenant des noms de propriété abstraits pour ces éléments.|  
|ID de corrélation|ID généré de façon aléatoire, associé à un message et attribué pour la durée de vie du message donné.|  
|ensemble de corrélations|Instance d'un type de corrélation, à savoir, liste des propriétés d'un message servant à déterminer si elles appartiennent à l'instance donnée d'une orchestration.|  
|type de corrélation|Ensemble des propriétés d'un message utilisées pour identifier de façon unique un processus d'entreprise et établir une corrélation entre les messages et les instances d'orchestrations.|  
|culture|Propriétés des données ou du texte relatives à la langue ou à des éléments localisables.|  
|adaptateur personnalisé|Code personnalisé écrit par un développeur et placé avant un pipeline de réception ou après un pipeline d'envoi pour obtenir une interface avec des adaptateurs et/ou des applications.|  
|numérotation personnalisée|Série de nombres qui, affectés par un compteur, permet d'incrémenter la valeur de chaque numéro d'une unité.|  
|référence cyclique|Modèle d'un schéma XML dans lequel un nœud descendant est déclaré du même type complexe que l'un de ses nœuds de niveau supérieur. Un schéma, doté d'une profondeur quasi illimitée et représentant des messages d'instance, est ainsi créé.|  
  
## <a name="d"></a>D  
  
|Terme|Définition|  
|----------|----------------|  
|langage DDL (Data Description Language)|Langage utilisé pour définir des données et leur relation avec les autres données. Il permet de créer la structure des données dans une base de données. Tous les principaux systèmes de gestion de base de données (SGBD) s'appuient sur le langage de description des données SQL.|  
|dimension Données|Nœud spécifique créé dans la vue Hiérarchique de l'Éditeur de modèle de suivi en tant qu'enfant direct du modèle de suivi concerné afin de décrire un groupe ou une dimension de données logique. Le nom de chaque dimension de données doit être unique et doit être composé d'un ou de plusieurs champs de données.|  
|élément de données|Nœud spécifique créé dans la vue Hiérarchique de l'Éditeur de modèle de suivi en tant qu'enfant direct de la catégorie des données. Le champ des données existe en tant que champ particulier de la charge d'entreprise.|  
|mappage de données|Processus de définition d'un mappage, au moment de la conception, entre les nœuds d'un schéma source et les nœuds d'un schéma de destination.|  
|DDL|Voir Langage DDL (Data Description Language).|  
|hôte par défaut|Objets d'administration facilitant le déploiement et l'inscription de l'orchestration. Ces objets sont signalés par une coche dans la console Administration de BizTalk Server. Durant le processus d'inscription de l'orchestration, l'hôte par défaut est automatiquement utilisé pour héberger l'orchestration, à moins que l'utilisateur n'ait sélectionné un hôte différent.|  
|pipelines par défaut|Désignent les assemblys compilés et déployés de BizTalk Server contenant des pipelines pour lesquels les étapes et les composants sont préconfigurés.|  
|mise en attente|Technique permettant d'enregistrer l'état d'une orchestration en cours d'exécution dans un stockage persistant et de le supprimer de sa mémoire après une certaine période d'inactivité de l'orchestration.|  
|fichier plat délimité|Format de fichier utilisé pour présenter des documents commerciaux dans lesquels les enregistrements et leurs champs associés sont délimités par des caractères ou des séquences de caractères spéciaux.|  
|délimiteur|Un ou plusieurs caractères spéciaux permettant de séparer des caractères semblables dans une structure délimitée et ce, à tous les niveaux (champs, enregistrements, etc.).|  
|rétrogradation|Action d'écrire des données de date et d'heure d'une propriété de contexte dans la charge d'un document.|  
|base de données de destination|Seule destination prise en charge par BizTalk 2004, bien que plusieurs bases de données de destination soient prises en charge par l'infrastructure du service Bus d'événements BAM.|  
|schéma de destination|Schéma utilisé dans un mappage BizTalk Server qui représente la structure des instances de messages sortants.|  
|Environnement DTE (Development Tools Environment)|Ensemble d'interfaces permettant aux développeurs de programmer plusieurs des tâches clés de l'interface IDE (Integrated Development Environment).|  
|hiérarchie de dimension|Structure arborescente logique qui organise les membres d'une dimension de telle sorte que chaque membre possède un membre parent et éventuellement des membres enfants.|  
|niveau de dimension|Élément signalant qu'un groupe d'éléments de données doit être considéré comme étant un niveau d'une hiérarchie de dimension. La définition DataPerspective affiche les résultats dans une hiérarchie de dimension OLAP.|  
|composant de pipeline Désassembleur|Composant de pipeline qui divise les messages en lots dans des documents séparés. Les composants de pipeline désassembleur fournis avec BizTalk Server sont : plate désassembleur de fichier, Désassembleur BizTalk Framework et désassembleur XML.|  
|champ distinctif|Membre de la classe .NET ou champ du schéma XSD (XML Schema Definition language) dans un message qui a été explicitement rendu disponible pour une orchestration afin d'être utilisé dans les expressions et les composants de pipeline personnalisés en tant qu'un champ de propriété écrite. Il ne peut pas être utilisé dans les expressions de filtre.|  
|coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator)|Service, intégré à une application COM+, faisant fonctionner les transactions distribuées.  Avec le coordinateur de transactions distribuées, il est possible de déployer des transactions vers un ou plusieurs ordinateurs sans avoir besoin d'un code spécial.|  
|DMZ|Zone démilitarisée. Voir Réseau de périmètre.|  
|document|Dans le cadre de la norme EDI, ensemble de segments combinés de façon logique. Incluent des types de documents : les factures, les commandes de transport, les déclarations en douane et ainsi de suite.|  
|définition de type de document (DTD, Document Type Definition)|L'une des nombreuses façons de définir la structure d'un document XML. BizTalk Server est en mesure d'ouvrir un schéma décrit à l'aide de la définition DTD, mais doit le convertir en langage XSD durant le processus.|  
|DTC|Voir Coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator).|  
|DTD|Voir Définition de type de document (DTD, Document Type Definition).|  
|DTE|Voir Environnement DTE (Development Tools Environment)|  
|duration|Élément chargé de demander au compilateur BAM de créer une colonne supplémentaire dans la vue pour indiquer la durée écoulée entre deux points de contrôle.|  
|adaptateur dynamique|Se dit d'un adaptateur disposant d'une interface utilisateur personnalisée.|  
|liaison dynamique|Liaison de port qui est appliquée au port au moment de l'exécution, généralement issue d'une propriété de message (par exemple, une adresse de réponse).|  
|mise à jour dynamique de stratégie|Récupération de stratégies au moment de l'exécution via le service de mise à jour du moteur des règles.|  
|port dynamique|Désigne un port d'envoi qui ne comporte pas d'adresse de destination, ni de type d'adaptateur associés. Un port d'envoi dynamique permet d'associer l'adresse de destination et le type d'adaptateur lors de la phase d'exécution, apportant ainsi une certaine souplesse d'utilisation (envoi de messages vers plusieurs destinations par le biais d'un même port et de plusieurs types d'adaptateurs).|  
  
## <a name="e"></a>E  
  
|Terme|Définition|  
|----------|----------------|  
|Routage|Voir Échange de données informatisé (EDI, Electronic Data Interchange)|  
|EDIFACT|Voir Échange de données informatisé pour l'administration, le commerce et le transport (EDIFACT, Electronic Data Interchange for Administrative Commerce and Transport)|  
|syntaxe UNOA EDIFACT|Seuls des caractères de syntaxe EDIFACT qui autorise les éléments suivants : lettres majuscules, chiffres, vide, le point d’exclamation ( !), guillemet («), signe pourcentage (%), esperluette (&), d’ouverture et de parenthèses fermantes (« ( » et «) »), astérisque (*), virgule, tiret (-), transférer les virgule décimale (.), barre oblique (/), point-virgule ( ;), moins-signe (\<) et supérieur-signe > (supérieur).|  
|syntaxe UNOB EDIFACT|Seuls des caractères de syntaxe EDIFACT qui autorise les éléments suivants : lettres majuscules et minuscules, des chiffres tous les vide, le point d’exclamation ( !), guillemet («), signe de pourcentage (%), esperluette (&), guillemet simple ('), parenthèses ((« » et «) »), astérisque (*), signe plus (+), virgule, tiret (-), le point décimal (.), transférer la barre oblique (/), deux-points ( :), point-virgule ( ;), moins-signe (\<), signe égal (=), supérieur-que le signe > (supérieur à) et de point d’interrogation ( ?).|  
|EIF|Voir Fichier d'entrée du moteur (EIF, Engine Input File).|  
|EIP|Voir Plateforme d'intégration d'entreprise (EIP, Enterprise Integration Platform).|  
|échange de données informatisé (EDI, Electronic Data Interchange)|Échange électronique de documents structurés et normalisés entre deux applications logicielles à l'aide d'un ensemble de normes permettant de surveiller le transfert de documents, tels que des bons de commande ou des factures, entre les ordinateurs.|  
|Échange de données informatisé pour l'administration, le commerce et le transport (EDIFACT, Electronic Data Interchange for Administrative Commerce and Transport)|Norme d'échange de données informatisé (EDI) au niveau mondial.|  
|element|Dans le cadre de la norme EDI, plus petite unité d'informations d'un document. Un élément peut être, par exemple, un numéro de facture. Dans le cadre de la norme XML, construction XML utilisée pour organiser des informations par ordre hiérarchique en imbriquant certains éléments dans d'autres avec une profondeur quasi illimitée.|  
|groupes d'éléments|Structure des regroupements d’éléments frères dans un document XML selon différentes contraintes : classés séquence (groupe séquence), séquence non ordonnée (groupe tous) et un-de-plusieurs (groupe choix).|  
|accord sur le codage|Accord entre les profils d'entreprise de deux partenaires commerciaux pour utiliser un protocole de codage spécifique (X12 ou EDIFACT) lors de l'échange de messages.|  
|protocole de codage|Protocole qui régit la structure et le contenu d'un message interentreprises. Les paramètres du protocole de codage pour un profil d'entreprise définissent le protocole de codage utilisé par un département pour envoyer et recevoir des messages interentreprises. X12, EDIFACT, HIPAA et EANCOM sont des exemples de protocoles de codage.|  
|clé de chiffrement|Chaîne utilisée pour chiffrer ou déchiffrer les informations d'identification.|  
|requête de modification de type de fin|Dernière étape du déploiement d'un type d'artefact sur l'ordinateur de destination, pendant l'importation d'un fichier MSI d'une application BizTalk à l'aide de la console Administration ou de l'outil BTSTask. Cette requête est également appelée requête de modification de validation ou encore, importation de validation pour un type d'artefact.|  
|point de terminaison|Représentation logique d'un emplacement, généralement exprimé sous la forme d'une URL, indiquant l'adresse physique des données reçues ou envoyées.|  
|Fichier d'entrée du moteur (EIF, Engine Input File)|Désigne la version compilée d'un schéma de document. Ce fichier permet d'expédier des conversions en vue de les distribuer à d'autres utilisateurs d'un groupe d'utilisateurs fermé. Il est automatiquement compilé dès qu'un schéma de langage XSD (XML Schema Definition language) est généré ou modifié via BizTalk Server.|  
|inscrire|Action d'associer une orchestration à l'environnement physique dans lequel elle va être exécutée. Cette action implique l'indication des adaptateurs nécessaires au transport des messages depuis et vers l'orchestration, l'indication du processus de l'application dans laquelle se trouve l'orchestration et la création des abonnements MessageBox indiqués par le routage.|  
|intégration d'applications d'entreprise (EAI, Enterprise Application Integration)|Processus d'association de données ou de fonctions provenant d'une application d'entreprise avec des données ou des fonctions provenant d'une autre application.|  
|Plateforme d'intégration d'entreprise (EIP, Enterprise Integration Platform)|Environnement dans lequel se produit l'intégration des applications d'entreprise. Ce scénario n'est autre qu'une classe de scénarios regroupés dans un seul scénario.|  
|système de l'authentification unique de l'entreprise|Système regroupant une base de données d'authentification unique, un serveur de secret principal ainsi qu'un ou plusieurs serveurs d'authentification unique de l'entreprise. Ces derniers effectuent le mappage entre les informations d'identification Windows et celles d'autres systèmes, recherchent ces informations d'identification dans la base de données d'authentification unique et sont utilisés pour l'administration du système de l'authentification unique. La base de données de l'authentification unique peut également servir à stocker les données de configuration personnalisées des adaptateurs.|  
|enveloppe|Ensemble structuré d'informations associées à l'instance du message, apportant généralement des informations sur son traitement et son envoi. Il est possible d'imbriquer des enveloppes.|  
|schéma d'enveloppe|Type particulier de schéma qui indique la structure d'une enveloppe par l'intermédiaire de plusieurs propriétés supplémentaires spécifiques aux enveloppes. Celles-ci apportent notamment des informations d'identification du contenu d'une enveloppe dans un flux de données mises sous enveloppe.|  
|cycle d'exécution|Assertion des faits, évaluation des conditions et exécution des actions dans le moteur des règles d'entreprise.|  
|Mode d'exécution|Propriété de l'étape pipeline qui détermine le modèle d'exécution des composants de pipeline dans une étape. Le mode Exécution comporte deux options : « Tous » et « PremièreCorrespondance ». En mode « Tous », tous les composants de l'étape sont exécutés dans la séquence configurée. Ce mode est utilisé lorsque plusieurs composants sont requis pour terminer une certaine tâche logique et qu'ils doivent tous être exécutés. Si une erreur se produit dans un composant lors du traitement d'un message à l'étape de pipeline, une erreur d'exécution est renvoyée.|  
|Assistant Exportation|Assistant que vous démarrez dans la console Administration de BizTalk pour générer un fichier MSI à partir d'une application BizTalk. Vous pouvez ensuite copier ce fichier MSI dans une autre instance de BizTalk Server et utiliser l'Assistant Importation pour importer les ressources du fichier MSI.|  
|remise expresse|Type de remise d'un message qui implique une certaine persistance (stockage dans la base de données SQL) lors du traitement des messages entrants et sortants.|  
|Langage de transformation de feuille de style extensible (XSLT)|Langage développé à partir de la norme XSL (Extensible Stylesheet Language) initiale. Le langage XSL spécifie une définition de langage pour la présentation et la transformation de données XML. La présentation des données correspond à leur affichage dans un certain format et/ou en utilisant un certain support et s'appuie sur les styles. La transformation des données a pour objet l'analyse d'un document XML d'entrée dans une arborescence de nœuds, puis la conversion de l'arborescence source en une arborescence résultat. La transformation s'applique à l'échange des données.|  
|format de message externe|Format d'un message avant ou après avoir été traité par BizTalk Server. Il est également appelé « format câble » lorsqu'il se rapporte au format de message externe.|  
  
## <a name="f"></a>F  
  
|Terme|Définition|  
|----------|----------------|  
|facette|Concept lié au langage XSD destiné à limiter les valeurs possibles des éléments ou des attributs, fournissant ainsi des paramètres de validation aux instances d'un schéma. Par exemple, vous pouvez définir une longueur minimale et maximale pour les données de chaîne. À différents types de données correspondent différents types de facets.|  
|fait|Données utilisateur auxquelles les conditions de règles s'appliquent. Au moment de la conception, un fait est une référence à ces données.|  
|base de faits|Regroupement de faits pour évaluer les conditions de règles.|  
|extracteur de faits (moteur de règles)|Composant plug-in optionnel, défini par l'utilisateur, qui implémente l'interface IFactRetriever de façon à collecter des faits à long terme qui seront utilisés avec des stratégies d'entreprise.|  
|banque de faits|Base de données permettant de stocker des informations sur des intervenants, y compris des rôles et des attributs. En outre, la banque de faits fournit une fonction de navigation par arborescence de sorte que les actions puissent définir la position relative des intervenants au sein d'une organisation.|  
|gestionnaire de la banque de faits|Composant qui permet d'extraire les informations de faits depuis les divers objets Extracteur de faits.|  
|transport de basculement|Transport secondaire.|  
|accord de partenariat commercial de secours|Ensemble de paramètres que BizTalk Server utilise pour la gestion des messages interentreprises en cas d'absence d'accord explicite.|  
|Adaptateur de fichier|Adaptateur capable de lire des messages provenant du système de fichiers et de les transmettre au serveur. Il est également capable d'écrire des messages depuis le serveur dans un fichier du système de fichiers.|  
|propriété Expression de filtre|Propriété de la forme Réception qui détermine les messages qui seront reçus. Sa propriété Activer doit être définie sur True pour obtenir une expression de filtre.|  
|vue Rechercher un message|Affichage des rapports permettant aux utilisateurs de rechercher des messages d'après les propriétés du message suivi.|  
|Adaptateur FTP|Adaptateur qui permet l'échange de fichiers entre BizTalk Server et les serveurs FTP.|  
|function|Abstraction utilisée pour accéder aux membres des classes à la fois dans les actions et les définitions de prédicats. Une fonction est utilisée dans les actions et également en tant que terme d'un prédicat.|  
|fonctoid|Module exécutable qui effectue un calcul ou une manipulation de données spécifique et qui est utilisé de façon graphique lors de la construction de mappages BizTalk Server afin de servir de base à des transformations plus performantes que celles effectuées simplement par XSLT.|  
|Functoid IntelliSense|Fonctionnalité du Mappeur BizTalk dans laquelle des indices visuels sont représentés sur la surface de la grille, en cas d'erreurs dans la configuration du fonctoid.|  
|boîte à outils des fonctoids|Fenêtre ancrable de Visual Studio qui sert de palette de fonctoids lors de la construction d'un mappage. Les fonctoids sont organisés dans différents onglets de la boîte à outils en fonction de leur rôle respectif.|  
  
## <a name="g"></a>G  
  
|Terme|Définition|  
|----------|----------------|  
|GAC|Voir Global Assembly Cache (GAC).|  
|cache d’assembly global (GAC)|Conteneur sur un serveur BizTalk destiné à un groupe comportant des assemblys identiques à ceux déployés vers la base de données de configuration de ce groupe.|  
|port global|Nom convivial utilisé pour associer un port à un profil de partenaire.|  
|en-tête du groupe|Dans le cadre de la norme EDI, partie du message utilisée pour indiquer le début d'un groupe fonctionnel de documents.|  
|paramètre au niveau du groupe|Un des paramètres que les administrateurs BizTalk peuvent modifier dans le Panneau de configuration de BizTalk. Exemples : propriétés, telles que l'intervalle d'actualisation de la configuration, la taille maximale du lot de messages et le suivi au niveau du groupe.|  
|code de fin du groupe|Dans le cadre de la norme EDI, partie du message utilisée pour indiquer la fin d'un groupe fonctionnel de documents.|  
|segment GS|Dans le cadre de la norme EDI, segment de l'en-tête du groupe fonctionnel d'un ensemble de documents ANSI X.12 (ensembles de transactions) appartenant à un même type de document. Ce segment obligatoire contient des informations sur un ensemble de transactions lors d'un échange, notamment le code d'envoi et de réception de l'application, le numéro de contrôle de groupe, l'ID de la version, de la version finale, de l'activité, etc.|  
  
## <a name="h"></a>H  
  
|Terme|Définition|  
|----------|----------------|  
|gestionnaire|Instance d'un hôte BizTalk sur laquelle un adaptateur s'exécute.|  
|hachage|Résultat de taille fixe obtenu par application d'une fonction mathématique unidirectionnelle (parfois appelée algorithme de hachage) à une quantité arbitraire de données. Si les données d'entrée sont modifiées, le hachage est également modifié. Le hachage peut être utilisé dans de nombreuses situations, telles que les opérations d'authentification et de signature numérique. Ce procédé est également appelé synthèse de message.|  
|analyse du fonctionnement|Processus de surveillance des applications, des composants et des serveurs sur lesquels la solution BizTalk Server est implémentée afin d'anticiper les problèmes ou de les résoudre.|  
|cube d'analyse du fonctionnement|Cube de traitement analytique en ligne (OLAP) destiné à fournir des informations sur les messages et les services. Les deux cubes livrés avec BizTalk Server sont : les faits de Message et faits de Service.|  
|vue Hiérarchique|Volet gauche de l'Éditeur de modèle de suivi (TPE, Tracking Profile Editor) et zone dans laquelle les espaces de noms et les activités d'entreprise sont affichés. Son rôle principal consiste à présenter le modèle de suivi.|  
|base de données d'historique|Base de données principale spécifique au scénario de gestion des processus d'entreprise.|  
|hôte|Conteneur logique représentant une ou plusieurs instances d'exécution BizTalk Server. Un hôte représente l'espace de traitement dans lequel se trouvent des informations sur les artefacts. Autrement dit, tous les éléments de type orchestration, schéma, emplacement de réception et adaptateur résident dans un hôte. Il sert aussi de domaine de sécurité dans Windows. En effet, il constitue une limite de processus virtuelle dans laquelle les instances de l'hôte exécutent un ou plusieurs serveurs.|  
|instance de l'hôte|Service Windows NT. Une instance de l'hôte est la représentation physique d'un hôte sur un serveur particulier.|  
|paramètre au niveau de l'instance de l'hôte|Un des paramètres que les administrateurs BizTalk peuvent modifier dans le Panneau de configuration de BizTalk. Exemples : paramètres .NET CLR et propriétés liées à une limitation de mémoire d'une orchestration. Spécifiques à une instance de l'hôte donnée, les paramètres au niveau de l'hôte régissent essentiellement l'utilisation des ressources d'un ordinateur (comme la RAM ou E/S). Un exemple est Max. Threads d’e/s.|  
|paramètre au niveau de l'hôte|Un des paramètres que les administrateurs BizTalk peuvent modifier dans le Panneau de configuration de BizTalk. Exemples : le suivi de l'hôte et des propriétés relatives à la limitation basée sur la ressource, la limitation basée sur la fréquence et la limitation de l'orchestration. Les paramètres au niveau de l'hôte modifient légèrement le comportement de toutes les instances de l'hôte dans un déploiement donné. Par exemple, si pour Host1 le paramètre Max. threads de moteur est passé à 200, toutes les instances de Host1 fonctionneront avec un maximum de 200 threads de moteur.|  
|équilibrage de la charge de l'hôte|Processus d'ajout de plusieurs serveurs exécutant BizTalk Server à un groupe BizTalk, puis de configuration de plusieurs instances d'un hôte In-process pour une exécution sur ces serveurs. Cela répartit l'exécution des services et des artefacts configurés dans cet hôte sur plusieurs instances de l'hôte, ce qui améliore sa disponibilité et son évolutivité.|  
|type d'hôte|Propriété qui définit si l'hôte est contrôlé à l'intérieur ou à l'extérieur du processus BizTalk Server. Un hôte peut être de type In-process ou Isolé.|  
|adaptateur HTTP|Adaptateur qui permet l'échange de messages entre BizTalk Server et n'importe quelle application utilisant le protocole HTTP ou HTTPS.|  
  
## <a name="i"></a>I  
  
|Terme|Définition|  
|----------|----------------|  
|IDE|Voir Environnement de développement intégré (IDE).|  
|Importer/Exporter|Dans le Panneau de configuration de BizTalk, importation/exportation de paramètres et de liaisons. Les paramètres actuels de BizTalk pour le groupe, l'hôte et l'instance de l'hôte, sont exportés et enregistrés dans un fichier XML. Les administrateurs BizTalk importent ces paramètres pour les appliquer à un autre environnement BizTalk.|  
|Assistant Importation|Assistant que vous démarrez dans la console Administration de BizTalk pour importer des ressources d'un fichier MSI dans une application BizTalk. Si l'application spécifiée n'existe pas, l'Assistant Importation la crée automatiquement.|  
|composition indépendante|Suite de deux actions : la seconde action n'attend pas que la première lui envoie un message de synchronisation pour pouvoir commencer à traiter la logique d'entreprise. La seconde action s'exécute sans délai.|  
|info-bulle|Info-bulle utilisée pour donner une description des commandes du bureau, de la fenêtre et du menu Démarrer en mode Web, et dans la colonne Commentaire de l'Explorateur Windows en mode Détails.|  
|héritage|Dans le cadre du service Web de gestion des partenaires commerciaux, un profil de membre hérite de toutes les préférences de son groupe parent. Lorsqu'il s'agit d'un groupe sans héritage, le profil du membre n'hérite d'aucune des préférences du groupe parent. Un tel groupe peut devenir un groupe héritier, mais le contraire n'est pas possible.|  
|orchestration interruptible|Orchestration pouvant être interrompue en cours de traitement, à des points bien définis.|  
|hôte In-process|Type d'hôte s'exécutant dans l'espace de processus BizTalk Server. Une orchestration peut faire l'objet d'une inscription auprès d'un hôte In-process, et un gestionnaire d'envoi peut se trouver sur cet hôte. Les hôtes In-process ne peuvent héberger que les gestionnaires de réception des hôtes In-process (adaptateur FILE).|  
|adaptateur de réception In-process|Adaptateur qui se trouve au sein des processus BizTalk Server. Il est créé, contrôlé et détruit par les processus serveur.|  
|Assistant Installation|Assistant que vous pouvez lancer à la dernière étape de l'Assistant Importation afin d'installer une application BizTalk sur l'ordinateur local.|  
|activité de l'instance|Série d'étapes de traitement consécutives via lesquelles un ou plusieurs messages sont acheminés.|  
|message de l'instance|Unité discrète de données d'exécution acheminées dans BizTalk Server. Elle représente généralement un document commercial particulier (par exemple, un bon de commande) et diffère du schéma BizTalk Server qui définit sa structure.|  
|Environnement de développement intégré (IDE)|Ensemble combiné d'outils utilisant l'interface utilisateur graphique Microsoft Windows pour la construction, la vérification et l'ajustement d'une plate-forme et de ses composants.|  
|intercepteur|Mécanisme servant à extraire des données d'un flux de traitement et à stocker ces données.|  
|échange|Dans le cadre de la norme EDI, combinaison logique de documents. Les échanges ne peuvent contenir qu'un destinataire unique. Dans la messagerie BizTalk, un échange est un ensemble de données traitées au cours de la phase de désassemblage du pipeline de réception ou de la phase d'assemblage du pipeline d'envoi. L'échange peut ne contenir aucun message comme il peut en contenir plusieurs. Dans un pipeline de réception, le composant désassembleur extrait les messages contenus dans l'échange qu'il a reçu et les propage à un niveau inférieur du pipeline de réception.|  
|en-tête de l'échange|Dans le cadre de la norme EDI, partie d'un échange ou groupe de documents associés de façon logique permettant d'indiquer le début de l'échange.|  
|code de fin de l'échange|Dans le cadre de la norme EDI, partie d'un échange ou groupe de documents associés de façon logique permettant d'indiquer la fin de l'échange.|  
|adaptateur intergroupe|Adaptateur de BizTalk Server capable de cibler une communication intranet ou LAN entre deux groupes de serveurs BizTalk sans passer par un stockage intermédiaire.|  
|format de message interne|Le format du message après ou avant qu’il est traité par BizTalk Server. Par exemple, le message reçu par BizTalk Server au début du pipeline de réception correspond à un format externe. Après acheminement du message via le pipeline, le format du message est un format interne.|  
|hôte isolé|Désigne un type d'hôte qui s'exécute en dehors de l'installation BizTalk Server. Un hôte isolé ne peut ni disposer d'orchestrations inscrites, ni héberger un gestionnaire d'envoi, ni utiliser le suivi de l'hôte ou même être utilisé comme hôte par défaut du groupe. Seuls les gestionnaires de réception pour hôtes isolés (HTTP, SOAP) peuvent être hébergés par un hôte isolé.|  
|adaptateur de réception isolé|Adaptateur de réception qui se trouve dans un processus autre qu'un processus BizTalk Server. Il est créé et contrôlé par un processus externe et s'inscrit auprès du serveur BizTalk au moment de l'exécution pour envoyer ses messages.|  
  
## <a name="k"></a>K  
  
|Terme|Définition|  
|----------|----------------|  
|Indicateur de performance clé (KPI)|Métrique d'entreprise personnalisable fournie par le composant Analysis Services. Ces indicateurs sont composés d'attributs et de calculs associés appropriés qui génèrent des objectifs et des tests d'évaluation conformes aux normes industrielles. Une collection d'indicateurs clés de performance comprend une mesure, un objectif, des propriétés d'affichage et des variations. Les sociétés peuvent avoir recours à ces indicateurs pour effectuer le suivi des performances et améliorer leur pouvoir décisionnel.|  
  
## <a name="l"></a>L  
  
|Terme|Définition|  
|----------|----------------|  
|port à liaison tardive|Port spécifié dans l'orchestration et dont la propriété Liaison est définie sur Spécifier plus tard. Un port à liaison tardive est configuré au moment de sa liaison à un port physique. La liaison est effectuée à l'aide de la console Administration de BizTalk.|  
|application sectorielle|Application indispensable à la gestion de l'entreprise : systèmes de salaire, de planification des ressources, de gestion de la chaîne logistique et de comptabilité.|  
|données actives|Données en cours de traitement par BizTalk Server.|  
|identificateur unique local (LUID, Locally Unique Identifier)|Nom donné à un artefact pour l'identifier de manière unique dans le groupe BizTalk. Les éléments composant le LUID peuvent varier selon le type d'artefact. Par exemple, l'identificateur unique local d'un assembly BizTalk inclut le nom de l'assembly, sa version, sa culture et le jeton de clé publique correspondant. Ex. : Microsoft.BizTalk.Hws.HwsPromotedProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35.|  
|transaction longue|Regroupement d'actions traitées en tant qu'unité et utilisé pour maintenir un état approprié de manière sûre et programmée. La transaction peut s'étendre sur une durée indéfinie et comporter plusieurs transactions imbriquées.|  
|enregistrement de boucle|Structure pouvant contenir plus d'une occurrence par message de l'instance.|  
  
## <a name="m"></a>M  
  
|Terme|Définition|  
|----------|----------------|  
|Management database|Base de données Microsoft SQL Server qui enregistre les informations de configuration relatives aux ressources d'une organisation. Il existe une base de données de gestion par organisation. Cette base de données est également appelée base de données de configuration.|  
|carte|Fichier XML qui définit les relations de correspondance entre les enregistrements et les champs de deux spécifications. Il comporte une feuille de style XSL utilisée par BizTalk Server pour effectuer la transformation qu'il décrit.|  
|grille du Mappeur|Zone intermédiaire multicouche de la fenêtre principale du Mappeur BizTalk, située entre les schémas source et de destination, dans laquelle le mappage des données est défini.|  
|page de grille du Mappeur|Couche qui, dans la grille du Mappeur, est unique et permet d'organiser des mappages de données associées indépendamment des mappages d'autres données.|  
|secret principal|Clé générée par le serveur de secret principal sur demande de l'administrateur de l'authentification unique de l'entreprise. Cette clé est stockée dans le registre en tant que secret de l'autorité de sécurité locale sur le serveur de secret principal. Seuls les administrateurs de SSO peuvent accéder à cette clé secrète.|  
|serveur de secret principal|Dans un environnement d'authentification unique de l'entreprise distribué, ordinateur sur lequel se trouve le registre contenant la clé de secret principal. Plusieurs serveurs de l'authentification unique (installés sur différentes machines) peuvent accéder à cette base de données unique. Néanmoins, un seul de ces serveurs peut être désigné comme étant le serveur de secret principal.|  
|message|Instance de données électronique, généralement transmise d'une application ou d'un processus d'entreprise en cours d'exécution vers un autre processus ou une autre application en cours d'exécution.|  
|corps du message|Partie centrale d'un message BizTalk Server, contenant la charge active et, dans la plupart des cas, un objet Blob XML. Tous les messages doivent avoir au plus une partie du corps. En règle générale, les données lues dans le flux correspondant au corps du message BizTalk Server sont utilisées pour promouvoir les propriétés de contexte de ce message. Par conséquent, le routage, la publication ou l'abonnement qui reposent sur les propriétés promues sont souvent effectués en fonction du corps du message.|  
|contexte de message|Conteneur pour diverses propriétés utilisées par BizTalk Server lors du traitement d'un document.|  
|propriétés du contexte de message|Ensemble de propriétés associées au message.|  
|vue Détails sur le message|Dans la page Hub du groupe, vue détaillée de toutes les informations connues concernant un message donné dans la base de données MessageBox. Cet affichage est disponible via le menu contextuel, dans la liste de champs du tableau croisé dynamique de l'une des deux vues Opérations.|  
|synthèse de message|Voir autre terme : hachage|  
|cube de faits d'un message|Cube de traitement analytique en ligne (OLAP) destiné à regrouper des informations sur les messages et les services. Les deux cubes livrés prêtes à l’emploi sont : les faits de Message et faits de Service.|  
|flux de messages|Série d'étapes de traitement consécutives via lesquelles un ou plusieurs messages sont acheminés.|  
|vue Flux message.|Vue dans la page Hub du groupe dans laquelle est affiché un historique des événements de traitement de messages spécifiques.|  
|en-tête du message|Dans le cadre de la norme EDI, partie du message utilisée pour indiquer le début d'un document et constituée d'un lot de segments combinés logiques contenant des informations sur une transaction. Dans le cadre de la norme ANSI X.12, un message équivaut à un ensemble de transactions.|  
|instance de message|Instance d'un message en cours de traitement ou sérialisé par le serveur BizTalk dans la base de données MessageBox pour un traitement ultérieur, ou dans la base de données des suivis pour un suivi. Dans BizTalk Server, il s'agit généralement d'une référence au message, à ses propriétés promues ainsi qu'au corps du message.|  
|vue Message Metrics|Vue de tableau croisé dynamique intégrée au cube de traitement analytique en ligne Message Metrics.|  
|code de fin du message|Dans le cadre de la norme EDI, partie du message utilisée pour indiquer la fin d'un document et constituée d'un lot de segments combinés logiques contenant des informations sur une transaction. Dans le cadre de la norme ANSI X.12, un message équivaut à un ensemble de transactions.|  
|liaison MessageBox|Liaison qui interagit avec MessageBox.|  
|Base de données MessageBox|Groupe de bases de données Microsoft SQL Server contenant des informations sur l'abonnement et le suivi d'un groupe MessageBox.|  
|nœud MessageBox|Dans la console Administration de BizTalk, nœud utilisé pour afficher la liste des bases de données MessageBox en cours d'exécution.|  
|vue Messages|Dans la page Hub du groupe, affichage en temps réel des instances de message utilisées par des services dans une base de données MessageBox. Cet affichage est disponible dans le menu Opérations.|  
|Messagerie|Une des fonctions principales de BizTalk Server. Elle garantit la réception, le routage et la distribution des messages de manière fiable.|  
|Instance de messagerie|Dans la page Hub du groupe, les instances de messagerie incluent les instances de service des ports d'envoi et de réception. Les instances de messagerie font référence aux instances de service de messagerie.|  
|Métadonnées|Informations, telles qu'un emplacement, une heure, une taille de message et/ou des informations sur une exception.|  
|alias d'étape majeure|Dans le composant d'analyse BAM, nom désignant une étape majeure ou un élément de données contenu dans les activités BAM. Chaque étape majeure ou élément de données peut avoir plusieurs alias.|  
|contenu mixte|Désigne le contenu d'un élément XML particulier incluant à la fois des sous-éléments et des données ne faisant pas partie de ces sous-éléments. Est un exemple de code HTML : &lt;P&gt;la pleine lune apparaît &lt;EM&gt;toujours&lt;/EM&gt; rise plus ou moins au coucher du soleil,.&lt; /P&gt;|  
|type de message à parties multiples|Définition de la structure d'un message, incluant le type de données de ses éléments. Un type de message à parties multiples peut contenir une seule ou plusieurs parties.|  
  
## <a name="n"></a>N  
  
|Terme|Définition|  
|----------|----------------|  
|native|Tout format de données autre que XML.|  
|adaptateur natif|Adaptateurs fournis par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment les adaptateurs MQSeries, FILE, FTP, HTTP, SMTP, SOAP et SQL.|  
|composant de pipeline natif|Composant de pipeline fourni par Microsoft et livré avec la solution BizTalk Server.  Exemples : Désassembleur de fichier plat, Désassembleur de fichier XML et Décodeur S/MIME.|  
|node|Chaque entrée de l'arborescence de schéma affichée dans l'Éditeur et le Mappeur BizTalk.|  
  
## <a name="o"></a>O  
  
|Terme|Définition|  
|----------|----------------|  
|OLAP|Voir Traitement analytique en ligne (OLAP, Online Analytical Processing).|  
|traitement analytique en ligne (OLAP, Online Analytical Processing)|Technologie utilisant les structures multidimensionnelles pour fournir un accès rapide aux données à analyser. Les données sources pour OLAP sont couramment stockées dans des entrepôts de données dans une base de données relationnelle.|  
|opération|Requête ou requête-réponse sur un port associée à une action d'envoi ou de réception.|  
|vues Opérations|Dans la page Hub du groupe, affichages qui permettent à l'utilisateur de voir des données actives, sans les suivre.|  
|Opérations/vue Détails sur le message|Affichage détaillé de toutes les informations connues concernant un message donné dans MessageBox.|  
|Opérations/vue Messages|Affichage en temps réel des messages de la base de données MessageBox utilisés par des services.|  
|Opérations/vue Détails sur l'instance de service|Affichage détaillé de toutes les informations connues concernant une instance de service donnée dans MessageBox.|  
|Opérations/vue Instances de service|Affichage en temps réel des services (actifs ou interrompus) dans la base de données MessageBox. Dans BizTalk Server 2002, files de travail/d'attente de messages interrompus.|  
|orchestration|Processus d'entreprise exécutable.|  
|liaison d'orchestration|Port d'orchestration qui ne se connecte pas à un point de terminaison fixe mais directement à MessageBox.|  
|Concepteur d'orchestration|Outil basé sur l'interface utilisateur graphique pour concevoir et implémenter des processus d'entreprise.|  
|instance d'orchestration|Instance en cours d'exécution d'un processus d'entreprise exécutable particulier.|  
  
## <a name="p"></a>P  
  
|Terme|Définition|  
|----------|----------------|  
|PAM|Voir Gestion des accords de partenariat (PAM).|  
|paramètre|Désigne les paramètres par défaut d'un processus d'entreprise, les paramètres d'un processus d'entreprise de chaque partenaire et les paramètres d'un processus d'entreprise de chaque groupe de partenaires.|  
|serveur partenaire|Voir autre terme : partenaire commercial|  
|Gestion des accords de partenariat (PAM)|Interface utilisateur dans le nœud Tiers de la console Administration de BizTalk Server, dans laquelle vous définissez les propriétés du tiers. Vous pouvez définir des propriétés de traitement pour les tiers impliqués dans un échange de document EDI, un traitement par lot EDI, le transport de document AS2, ainsi que des propriétés globales à utiliser en l'absence d'un tiers.|  
|tiers|Entité extérieure à BizTalk Server qui interagit avec une orchestration. L'ensemble des partenaires avec lesquels votre société traite sont considérés comme des tiers. Votre organisation peut compter des centaines de partenaires.|  
|inscription du tiers|Mécanisme qui lie un tiers à un rôle. Vous pouvez inscrire un tiers dans un rôle pour que l'orchestration interagisse avec le tiers.|  
|transfert|Configuration des ports BizTalk Server de sorte qu'un port de réception soit directement connecté à un port d'envoi par l'intermédiaire d'une seule expression de filtre sur un port d'envoi. L'expression de filtre doit se présenter sous la forme BTS.ReceivePortName == "Nom ou port de réception". Dans cette configuration, tous les messages provenant du port de réception sont directement acheminés vers un port d'envoi. La signification de l’exécution directe dans BizTalk 2004 est différente de la signification de l’exécution directe dans BizTalk Server 2000 ou 2002. Dans BizTalk Server 2004, le message de l’exécution directe est toujours traité dans les pipelines et peut-être être transformé dans des ports.|  
|surveillance des performances|Processus de surveillance du taux de réception/traitement des messages, du nombre d'orchestrations en cours d'exécution, du nombre d'accès au cache, de l'utilisation de la mémoire dans le temps, etc.|  
|règles de traitement des performances|Règles qui régissent les performances de traitement ou la capacité des compteurs.|  
|réseau de périmètre|Ensemble de périphériques et de sous-réseaux placés entre un intranet et Internet en vue de protéger l'intranet contre l'intrusion d'utilisateurs Web non autorisés. Également appelé sous-réseau filtré ou zone démilitarisée (DMZ).|  
|liaison physique (anticipée)|Informations contenues dans l'assembly qui sont utilisées par le processus de déploiement pour créer des ports d'envoi et de réception.|  
|pipeline|Infrastructure logicielle qui définit et relie une ou plusieurs étapes, puis les exécute dans l'ordre pour réaliser une tâche spécifique. Les pipelines divisent le traitement en étapes, ou abstractions, qui décrivent une catégorie de travail. Ils déterminent également l'ordre dans lequel chaque catégorie de travail est exécutée.|  
|composant de pipeline|Composant COM ou .NET qui peut être placé dans un pipeline pour exécuter des actions de traitement sur les messages acheminés via ce pipeline.|  
|Concepteur de pipeline|Outil basé sur l'interface utilisateur graphique pour créer et configurer des pipelines dans BizTalk Server.|  
|stratégie|Collection gérée de règles d'entreprise.|  
|ligne de connecteur de port|Ligne indiquant la connexion entre une forme Envoi/Réception et une opération sur une forme Port. Les deux points de terminaison de la ligne de connecteur de port doivent obligatoirement être attachés.|  
|type de port|Propriété qui définit les modèles d'interaction des messages (opérations) autorisés avec ce point de terminaison. Une opération peut être unidirectionnelle (un seul message est envoyé ou reçu) ou de type requête-réponse (un message est envoyé/reçu et une réponse est reçue/envoyée).|  
|fichier plat positionnel|Type de format de fichier employé pour représenter des documents commerciaux dans lesquels les enregistrements et les champs ont une longueur fixe, ce qui évite d'avoir à utiliser des délimiteurs.|  
|file d'attente privée|File d'attente qui n'est pas publiée en tant qu'objet Active Directory. Message Queuing BizTalk prend entièrement en charge l'envoi et la réception de messages dans les files d'attente privées.|  
|surface du processus|Zone intermédiaire de la surface de conception dans le Concepteur d'orchestration utilisée pour concevoir des orchestrations.|  
|Concepteur de projet|Représentation virtuelle des services, des ports et des liaisons qui constituent un projet. Les utilisateurs peuvent retoucher des éléments graphiques dans le Concepteur de projet en ajoutant et supprimant des services, et en créant et supprimant des liaisons entre les ports compatibles des services du concepteur.|  
|promotion des propriétés|Le mécanisme par lequel les propriétés de message spécifique sont écrites dans le contexte du message associé au message en tant que champs de propriété. Les propriétés écrites dans le contexte du message comme champs de propriété sont considérés comme étant des propriétés promues (le **IsPromoted** du champ est définie sur **True**) et nécessitent un schéma de propriété associée.  Champs de propriété sont utilisées par le moteur BizTalk Server de messagerie à des fins de suivi des messages, le routage de document et de l’évaluation dans les orchestrations. Le contexte du message est stocké dans la colonne imgContext, à la ligne correspondant au message, dans la table de mise en attente de la base de données MessageBox.|  
|schéma de propriété|Schéma associé à un schéma de BizTalk Server servant à identifier les champs d'éléments d'un document qui seront promus vers le contexte de message en tant que champs de propriété.|  
|paramètre du protocole|Paramètre qui définit la manière dont les transactions commerciales doivent être prises en charge pour un protocole interentreprises spécifique. Chaque profil d'entreprise définit les divers paramètres de traitement des messages (codage) ou de leur transmission (transport) pour chaque protocole interentreprises via lequel le partenaire peut communiquer. Un paramètre du protocole peut s'appliquer aux protocoles de codage ou à un protocole de transport.|  
|file d'attente publique|File d'attente qui est publiée en tant qu'objet Active Directory.|  
|publication-abonnement|Voir autre terme : publication/abonnement d’architecture|  
|architecture « publication-abonnement »|Combinaison des processus de publication et d'abonnement permettant de faire passer les messages d'un sous-système à l'autre. Par exemple, les ports de réception reçoivent des messages qu'il traitent avant de les publier dans MessageBox. BizTalk Server achemine ensuite ces messages vers des orchestrations d'abonnement ou des ports d'envoi qui les traitent à leur tour pour les publier à nouveau dans MessageBox ou pour les envoyer vers des systèmes externes.|  
|Publication|Action de stocker une instance de message dans la base de données MessageBox de sorte qu'elle corresponde à un abonnement dans une application utilisatrice.|  
  
## <a name="q"></a>Q  
  
|Terme|Définition|  
|----------|----------------|  
|Expression de requête|Groupe de clauses de requête, dans la page Hub du groupe, que vous pouvez utiliser pour créer et exécuter des requêtes sur la base de données des suivis BizTalk.|  
  
## <a name="r"></a>R  
  
|Terme|Définition|  
|----------|----------------|  
|dimension Plage|Dans le composant d'analyse BAM, dimension utilisée pour créer des plages de critères. Vous pouvez par exemple créer des plages numériques rendant compte du nombre d'unités vendues : Faible (0 à 100), Moyen (100 à 500) et Élevé (500 à 1000).|  
|composant Receipt Generator|Composant qui génère un faux accusé de réception afin de rendre possible la suppression d'un message de la file d'attente des nouvelles tentatives de remise.  Ce composant est employé lorsqu'un port de messagerie est configuré pour utiliser un système de messagerie fiable.|  
|gestionnaire de réception|Instance d'un hôte BizTalk sur laquelle un adaptateur de réception s'exécute. Un gestionnaire de réception constitue le conteneur logique d'un composant d'écoute, d'un composant de gestion des points de terminaison et d'un composant MessageAgent.|  
|type de l'hôte du gestionnaire de réception|Propriété qui limite le type d'hôte pouvant héberger un gestionnaire de réception particulier.|  
|emplacement de réception|Notion physique d'un emplacement (par exemple, une URL) et d'un type d'adaptateur, générée durant la phase de conception. Dans le nœud Hôte de la console Administration de BizTalk Server, un emplacement de réception définit la fonctionnalité de réception.|  
|pipeline de réception|Pipeline exécuté sur les messages après leur réception par un adaptateur et avant leur publication dans la base de données MessageBox.|  
|port de réception|Groupe logique d'emplacements de réception similaires.|  
|redéployer|Action de redéployer un assembly qui existe déjà dans l'environnement cible en supprimant les anciens attributs et en déployant les nouveaux.|  
|réalimenter|Fait d'activer une orchestration inactive dans la mémoire depuis un stockage persistant suite à un événement, tel que la réception d'un message.|  
|Vue Pertinence|Vue dans le Mappeur BizTalk dans laquelle les frères non pertinents d'un élément de schéma sont réduits afin d'obtenir une vue plus compacte du schéma, réduisant ainsi le besoin de défilement et mettant l'accent sur les parties utiles du schéma et du mappage.|  
|vue Rapports|Ensemble de vues hiérarchiques présentant un ou plusieurs processus d'entreprise.|  
|référentiel|Conteneur de stockage des métadonnées utilisé par Analysis Services. Les métadonnées sont enregistrées dans les tables d'une base de données relationnelle, puis sont utilisées pour définir les paramètres et les propriétés des objets du serveur d'analyse. Les outils XML utilisent ce référentiel en mode lecture-écriture, tandis que l'Explorateur BizTalk accède aux données en mode lecture uniquement.|  
|adaptateur de requête-réponse|Adaptateur de réception qui reçoit un message de requête de la part du client, l'envoie au serveur, attend une réponse, puis renvoie la réponse au client.|  
|forme Retour|Forme utilisée pour terminer une orchestration un peu avant la fin effective de cette orchestration.  Ceci peut être : si (contrôle de sécurité réussi) continuation, else retour.|  
|rôle|Ensemble de types de port qui utilisent ou implémentent un service et fournissent ainsi aux tiers un moyen d'interagir avec les orchestrations. Par exemple, une orchestration peut revêtir le rôle d'un Expéditeur. Un ou deux tiers sont associés à ce rôle. Lorsque l'orchestration choisit la société de transport à utiliser pour un élément, elle compare le prix des tiers dans le rôle Expéditeur.|  
|lien de rôle|Relation entre les rôles définie par les types de ports et de messages utilisés dans les interactions de façon réciproque.|  
|type de lien de rôle|Propriété qui représente la relation entre deux services ou orchestrations en définissant le rôle tenu par chacun des services de cette relation et en indiquant les types de ports fournis par chacun des rôles.|  
|nœud racine|Nœud d'un schéma BizTalk Server qui représente l'élément XML le plus éloigné dans le document commercial spécifié par le schéma.|  
|fenêtre RTA|Définit la période pendant laquelle les données d'une agrégation RTA sont agrégées. Par exemple, si la période est d'une journée et que le point dans le temps est défini à maintenant, vous accéderez uniquement aux agrégations sur les données des dernières 24 heures. Le point dans le temps changeant en permanence, la période dans la fenêtre RTA change également ; c'est pourquoi elle est également appelée « fenêtre temporelle mobile ».|  
|règle|Association de conditions et d'actions.|  
|ensemble de règles|Groupe logique de règles similaires. Il peut être considéré comme un procédé de groupement/segmentation du moteur de règles.|  
|infrastructure du moteur de règles|Bibliothèque de composant .NET, interfaces API et services utilisés par les développeurs pour développer des applications basées sur des règles.|  
|service de mise à jour du moteur des règles|Service qui effectue des mises à jour de stratégies dynamiques.|  
|magasin de règles|Emplacement des stratégies persistantes. Une base de données SQL Server est le magasin de règles par défaut.|  
  
## <a name="s"></a>S  
  
|Terme|Définition|  
|----------|----------------|  
|schéma|Structure d'un message. Un schéma peut contenir plusieurs sous-schémas.|  
|extension de l'Éditeur de schéma|Procédé par lequel les modules logiciels étendent la fonctionnalité de base XML/XSD prise en charge par l'Éditeur BizTalk. En général, les extensions de l'Éditeur de schéma ajoutent des propriétés supplémentaires à un ou plusieurs nœuds dans les schémas BizTalk pour obtenir leur propre sémantique.|  
|sous-réseau filtré|Voir le terme : réseau de périmètre|  
|protocole SSL|Un protocole qui améliore la sécurité des communications de données à l’aide d’une combinaison de chiffrement des données, de certificats numériques et de chiffrement à clé publique. Le protocole SSL active l'authentification et augmente l'intégrité et la confidentialité des données sur les réseaux. SSL ne fournit pas d'autorisation ou de non-répudiation.|  
|segment|Dans le cadre de la norme EDI, combinaison logique d'éléments. Par exemple, les informations de nom et d'adresse sont regroupées en un seul segment.|  
|balise du segment|Dans le cadre de la norme EDI, identificateur unique d'un segment. Dans la norme EDIFACT, par exemple, les balises de segments correspondent à un code formé de trois lettres majuscules joint aux éléments d'un document comme préfixe. Dans la norme ANSI X.12, elles représentent un code formé de deux ou trois lettres majuscules. Les identificateurs de type d'enregistrement et les balises de segment sont de même nature.|  
|gestionnaire d'envoi|Hôte BizTalk auquel l'adaptateur d'envoi est associé.|  
|pipeline d'envoi|Pipeline exécuté sur les messages avant l'envoi de ces derniers par le serveur BizTalk.|  
|port d'envoi|Emplacement vers lequel les messages sont envoyés ou à partir duquel ces derniers sont reçus. Désigne également la technologie utilisée pour implémenter la communication. Seul le nom du port permet d'identifier l'emplacement.|  
|groupe de ports d'envoi|Regroupement logique de ports d'envoi. Lorsqu'un message est envoyé à un groupe de ports d'envoi, il est acheminé vers tous les ports d'envoi associés. Un tel regroupement est également appelé liste de distribution.|  
|service|Programme, routine ou processus qui exécute une fonction système spécifique afin de prendre en charge d'autres programmes au niveau du système d'exploitation, notamment un service Windows NT. Un service est un service Windows NT ou COM+ qui fonctionne sur un serveur.|  
|instance de service|Généralement, instance d'une orchestration en cours de traitement ou sérialisée par BizTalk Server dans la base de données MessageBox pour un traitement ou un suivi ultérieur. Il s'agit le plus souvent d'une représentation sérialisée de l'état de l'orchestration et des références aux messages en cours d'utilisation dans l'orchestration. Dans le contexte de la messagerie, une instance de service s'applique à une instance d'un port, par exemple à un port de réception où l'entrée est l'emplacement de réception et la sortie est publiée dans la base de données MessageBox, ou à un port d'envoi où l'entrée est la MessageBox et la sortie est généralement un adaptateur d'envoi.|  
|vue Service Metrics|Vue de tableau croisé dynamique intégrée au cube OLAP Service Metrics. Anciennement intégrée à la vue Agrégation.|  
|session|Connexion logique entre deux hôtes pour l'échange de données. D'ordinaire, les sessions envoient les données par ordre chronologique avec accusé de réception.|  
|forme|Représentation graphique d'une action ou d'un groupe d'actions dans une orchestration.|  
|ligne de connexion de formes|Ligne utilisée pour relier des formes entre elles et déterminer leur ordre relatif dans une orchestration.|  
|forme simple|Forme d'une orchestration qui ne peut pas être réduite ni contenir d'autres formes.|  
|authentification unique (SSO, Single Sign-On)|Voir autre terme : Enterprise Single Sign-On système|  
|administration de l'authentification unique|Modèle objet accessible via les utilitaires de ligne de commande d'administration (par exemple, ssomanage et ssoconfig), Windows Management Instrumentation (WMI) et l'Explorateur BizTalk pour les scénarios de stockage de la configuration. Ce composant communique avec la base de données d'authentification unique à l'aide du serveur de l'authentification unique.|  
|groupe des administrateurs de l'authentification unique|Administrateur qui dispose du plus haut niveau d'autorité et définit généralement la clé de chiffrement.|  
|groupe des administrateurs d'applications associées à authentification unique|Administrateurs capables de créer et de gérer des applications associées, de spécifier un compte d'administrateurs d'applications à authentification unique pour chaque application associée et d'accomplir les mêmes tâches d'administration que les administrateurs et les utilisateurs d'applications à authentification unique.|  
|groupe des administrateurs d'applications à authentification unique|Administrateurs affectés individuellement à chaque application associée.|  
|utilitaires clients de l'authentification unique|Disponibles dans le composant Administration, ces utilitaires destinés aux utilisateurs finaux servent à fournir des mappages d'informations d'identification les concernant dans la base de données de l'authentification unique. Ils sont utilisés par le serveur de l'authentification unique pour communiquer avec la base de données d'authentification unique.|  
|base de données de l'authentification unique (SSO)|Base de données dans laquelle sont enregistrées les informations de l'authentification unique de l'entreprise. Plusieurs bases de données stockent les URL et les ports d'envoi, mais une seule dispose d'un sous-service de secret.|  
|serveur de l'authentification unique|Serveur sur lequel le service de l'authentification unique de l'entreprise est installé.|  
|services de l'authentification unique|Services qui permettent d'authentifier les adaptateurs en accédant aux informations d'identification dans la base de données de l'authentification unique. Vous pouvez avoir recours à ces services pour gérer et administrer la base de données de l'authentification unique. En tant que stockage de la configuration, ils permettent d'accéder aux données de configuration des adaptateurs.|  
|Balise active|Avertissement graphique indiquant qu'une forme n'est pas entièrement configurée. Fournit également des indications sur la façon de procéder.|  
|adaptateur SMTP|Adaptateur qui implémente le protocole SMTP (autrement dit, qui envoie les messages électroniques) afin d'interagir avec des applications sectorielles. Il comprend uniquement le gestionnaire d'envoi.|  
|adaptateur SOAP|Adaptateur qui implémente le protocole SOAP afin d'interagir avec des applications sectorielles, qui publie des orchestrations en tant que services Web et qui utilise des services Web externes.|  
|erreur SOAP|Message d'erreur renvoyé par un service Web faisant état d'une exception d'application.|  
|En-tête SOAP|Élément facultatif de l'enveloppe d'un message SOAP capable de contenir des données qui ne sont pas directement liées à la fonctionnalité principale de la méthode de service Web XML.|  
|message SOAP|Document XML correctement formé. Il doit utiliser l'enveloppe et les espaces de noms de codage SOAP. Il doit inclure une déclaration facultative XML, ainsi qu'une enveloppe SOAP (l'élément racine), composée d'un en-tête SOAP facultatif et d'un corps de message SOAP.|  
|suivi de message SOAP|Méthode de définition d'un point d'arrêt dans un service Web publié afin de renvoyer des exceptions détaillées à un client Web.|  
|adaptateur de sollicitation-réponse|Adaptateur d'envoi bidirectionnel. Un adaptateur de réception de type sollicitation-réponse envoie un message de requête de BizTalk Server vers un destinataire, attend la réponse du destinataire, puis renvoie le message de réponse à BizTalk Server.|  
|schéma source|Schéma utilisé dans un mappage BizTalk Server qui représente la structure des messages de l'instance sortants.|  
|Adaptateur SQL|Adaptateur qui échange des informations entre une base de données SQL Server et BizTalk Server.|  
|AUTHENTIFICATION UNIQUE|Voir Système de l'authentification unique de l'entreprise.|  
|étape|Phase d'un pipeline destinée à accomplir une certaine catégorie de travail. Les composants de pipeline de chaque étape se chargent d'effectuer les tâches actives.|  
|base de données intermédiaire|Base de données utilisée par un testeur pour déployer l'assembly et ses liaisons vers la base de données intermédiaire ou de test.|  
|adaptateur statique|Adaptateur reposant sur l'interface utilisateur fournie par l'infrastructure d'adaptateurs.|  
|port statique|Désigne un port d'envoi qui comporte une adresse de destination ainsi qu'un type d'adaptateur associés. À la différence d'un port d'envoi dynamique, la configuration d'un port d'envoi statique ne peut pas être modifiée pendant son exécution. En outre, un port d'envoi statique ne peut envoyer des messages qu'à une seule adresse de destination.|  
|fichier de clé de nom fort|Fichier contenant l'identité d'un assembly : son nom simple au format texte, son numéro de version et des informations de culture, le cas échéant, ainsi qu'une clé publique et une signature numérique. Il est généré à partir d'un fichier d'assembly à l'aide de la clé privée correspondante. (Le fichier d'assembly contient le manifeste d'assembly, qui contient les noms et les hachages de tous les fichiers composant l'assembly.)|  
|envoyer|Action de placer un message et ses propriétés dans les tables appropriées de la base de données MessageBox et d'analyser le répertoire des abonnements à la recherche des abonnements dont le prédicat correspond aux propriétés du message.|  
|subscribe|Procédé de BizTalk permettant d'indiquer à MessageBox d'acheminer vers les processus appropriés les messages dont les propriétés respectent les paramètres spécifiés (abonnements). Par exemple, les filtres de port d'envoi créent des abonnements dans MessageBox. Lorsque des messages correspondant au filtre spécifié sont publiés dans MessageBox, BizTalk Server les achemine vers les ports d'envoi abonnés pour traitement.|  
|abonnement|Procédé d'acheminement des messages correspondant à certains critères de comparaison des propriétés dans une file de travail.|  
|Base de données d'abonnement|Base de données MessageBox dans laquelle tous les abonnements d'un groupe MessageBox sont enregistrés.|  
|instance suspendue|Instance d'un message ou d'une orchestration dont BizTalk Server a arrêté le traitement en raison d'une erreur dans le système ou le message. Les instances dont l'exécution a été interrompue suite à des erreurs système peuvent généralement reprendre une fois le problème résolu. En revanche, les instances dont l'exécution a été suspendue en raison d'un problème de message ne peuvent généralement pas reprendre et le message doit être réparé avant d'être renvoyé au système BizTalk Server.|  
|file d'attente de messages interrompus|File d'attente qui contient des opérations pour lesquelles une erreur ou une défaillance s'est produite lors du traitement. La file d'attente de messages interrompus stocke les messages jusqu'à ce qu'ils soient corrigés et de nouveau traités, ou bien supprimés.|  
  
## <a name="t"></a>T  
  
|Terme|Définition|  
|----------|----------------|  
|base de données/environnement cible|Cette base de données est identifiée pendant le déploiement d'un assembly et de ses liaisons dans un environnement cible.|  
|tâche|Intervention de l'utilisateur dans une action. Chaque action peut comporter aucune ou plusieurs tâches affectées à différentes cibles. La correspondance existante entre les tâches et les cibles est de type un-à-un.|  
|réponse de la tâche|Réponse apportée à la tâche de la part des cibles. Chaque tâche peut comporter aucune ou plusieurs réponses.|  
|TDDS|Voir Service TDDS (Tracking Data Decode Service).|  
|mode Détails techniques|Vue dans la page Hub du groupe dans laquelle sont affichées les étapes du processus technique d'un seul thread d'activité.|  
|terme|Entité atomique comportant une valeur qui peut être utilisée dans les prédicats et les actions. Un terme peut être un membre de classe (par exemple, une propriété, une méthode ou un champ de la classe .NET, un élément XML ou un élément de base de données), une variable de règle ou une constante.|  
|dimension de temps|Élément de l'interface utilisateur indiquant la date et l'heure, telles qu'elles apparaissent pour les agrégations.|  
|message de déclenchement programmé|Message intégré à la file d'attente qui déclenche automatiquement le déplacement du flux dans la file d'attente.|  
|boîte à outils|Fenêtre ancrable contenant divers éléments utiles à la conception de l'orchestration.|  
|info-bulle|Petite info-bulle qui fournit une brève aide contextuelle lorsque vous déplacez le pointeur de la souris sur l'élément.|  
|TPE|Voir Éditeur de modèle de suivi (TPE, Tracking Profile Editor).|  
|suivi|Possibilité de suivre les échanges et les messages traités par BizTalk Server.|  
|base de données Analyse des suivis|Nom donné à la base de données Analyse des suivis (OLAP) pour le groupe MessageBox associé.|  
|service TDDS (Tracking Data Decode Service)|Service permettant de déplacer des données d'événements de la base de données MessageBox dans la base de données d'importation principale BAM. Ce service traite et stocke à la fois des données décisionnelles et des données d'analyse du fonctionnement de BizTalk.|  
|Base de données des suivis|Désigne la base de données Microsoft SQL Server qui enregistre les informations de suivi d'un groupe MessageBox. Chaque groupe MessageBox contient une base de données des suivis.|  
|mode Options de suivi|Vue dans la page Hub du groupe qui définit les options de suivi.|  
|modèle de suivi|Ensemble de caractéristiques qui définissent un processus de type commercial et contiennent le mappage entre une orchestration spécifique et une définition d'activité.  Il s'agit d'un fichier dont le nom est doté de l'extension .btt.|  
|Éditeur de modèle de suivi|Outil basé sur l'interface utilisateur graphique pour définir des éléments importants d'un processus d'entreprise ainsi que des données intéressantes sur la charge d'entreprise.|  
|partenaire commercial|Organisation externe ou interne avec laquelle votre organisation échange des données électroniques. Exemples : un fournisseur, un client ou un service interne à votre entreprise.|  
|accord de partenariat commercial|Accord définitif et ferme entre deux partenaires commerciaux pour le traitement des messages via un protocole interentreprises spécifique. Un accord de partenariat commercial combine les propriétés communes de traitement des messages bidirectionnelles à partir des profils d'entreprise spécifiques des deux partenaires. Il s'agit d'un ensemble complet d'aspects régissant la transaction commerciale entre deux partenaires commerciaux. L’accord de partenariat commercial est généralement dérivé des profils de chaque partenaire, avec la possibilité de personnaliser et de remplacer les paramètres requis.|  
|gestion des partenaires commerciaux|Gestion et stockage d'informations sur les partenaires, leur entreprise et les relations/accords interentreprises. La solution de gestion des partenaires commerciaux (GPC) améliorée reflète, de manière plus intuitive, les entités commerciales et leurs relations car elle permet aux organisations de mieux gérer les partenariats commerciaux avec des partenaires commerciaux.|  
|partie commerciale|Entité qui est à la racine d'une solution de gestion des partenaires commerciaux (GPC). Une partie commerciale est chaque organisation participant à une relation commerciale continue et toute entité commerciale qui exécute BizTalk Server et envoie ou reçoit des messages de ou à un autre tiers.|  
|messagerie transactionnelle|Envoi unique d'un flux de messages par ordre chronologique à l'aide de la synchronisation et de la coordination des diverses instances de l'adaptateur de Message Queuing BizTalk.|  
|Forme Transformer|Forme dans une orchestration qui sert à déplacer les données d'un message à un autre tout en les transformant à l'aide d'un mappage XSLT.|  
|transformation|Procédé de conversion d'un document XML correspondant à un schéma en un document XML correspondant à un autre schéma, entraînant souvent la modification de la structure du document.|  
|traduction|Technique de conversion d'un document XML en un format natif (non-XML), et inversement.|  
|accord sur le transport|Accord entre les profils d'entreprise de deux partenaires commerciaux pour utiliser un protocole de transport spécifique (AS2) lors de l'échange de messages.|  
|Transport Layer Security|Protocole qui assure la confidentialité et la sécurité des communications entre deux applications communiquant via un réseau. TLS chiffre les communications et permet aux clients d'authentifier les serveurs et, éventuellement, aux serveurs d'authentifier les clients. TLS est une version plus sécurisée du protocole SSL (Secure Sockets Layer).|  
|protocole de transport|Protocole qui régit le canal de transport utilisé pour échanger des messages entre deux partenaires. En termes de gestion des partenaires commerciaux (GPC), seul le protocole AS2 est pris en charge.|  
  
## <a name="u"></a>U  
  
|Terme|Définition|  
|----------|----------------|  
|annuler le déploiement|Processus de suppression d'une application BizTalk dans les bases de données de BizTalk Server et dans la console Administration ainsi que sur tous les ordinateurs où elle a été installée.|  
|désinscrire|Annulation de tous les abonnements et de toutes les instances (en cours ou suspendues) associés à un service.|  
|Dictionnaire du Commerce et des échanges électroniques (UNTDED, United Nations Trade Data Elements Dictionary)|Dans le cadre de la norme EDI, dictionnaire regroupant tous les éléments utilisés avec la norme EDIFACT.|  
|UNTDED|Voir Dictionnaire du Commerce et des échanges électroniques (UNTDED, United Nations Trade Data Elements Dictionary).|  
|segment UNZ|Dans le cadre de la norme EDI, segment représentant le code de fin de l'échange d'un document EDIFACT. Il comporte les éléments Référence de l'échange et Numéro du document. Ce segment est utilisé pour indiquer la fin d'un échange, et pour vérifier la référence de l'échange et le nombre de documents dans l'échange.|  
  
## <a name="v"></a>V  
  
|Terme|Définition|  
|----------|----------------|  
|contrôle de version|Mise à jour de l'implémentation d'un artefact et incrémentation de son numéro de version.|  
|nœud virtuel|Dans un schéma, nœud qui ne correspond pas directement à un attribut ou à un élément XML dans les messages de l'instance définis par ce schéma.|  
|vocabulaire|Ensemble d'éléments de vocabulaire utilisés lors de la création d'une règle.|  
|élément de vocabulaire|Nom de fait lisible par l'utilisateur.|  
  
## <a name="w"></a>W  
  
|Terme|Définition|  
|----------|----------------|  
|Services Web|Unité de logique d'application qui fournit des données et des services aux autres applications. Les applications accèdent aux services Web XML via des protocoles Web et des formats de données omniprésents, tels que HTTP, XML et SOAP, sans tenir compte du mode d'implémentation de chaque service Web XML. Les services Web XML associent les aspects les plus performants du développement à base de composants et du Web. Ils constituent l'élément fondamental du modèle de programmation Microsoft .NET.|  
|WSDL (Web Services Description Language)|Langage XML décrivant les services Web en tant que points de terminaison pour l'échange de messages. Ce langage est extensible et permet ainsi la description des points de terminaison et de leurs messages, quels que soient le format de message et le protocole réseau utilisés. Ce langage est utilisé par UDDI (Universal Description, Discovery, and Integration), un annuaire professionnel Web.|  
|Windows Management Instrumentation (WMI)|Composant du système d'exploitation Microsoft Windows et de l'implémentation de Microsoft WBEM (Gestion système par interface Web), utilisé pour automatiser les tâches administratives dans un environnement d'entreprise.|  
|WMI|Voir Windows Management Instrumentation (WMI).|  
|file de travail|File d'attente contenant les messages à traiter par le serveur BizTalk.|  
|WSDL|Voir WSDL (Web Services Description Language).|  
  
## <a name="x"></a>X  
  
|Terme|Définition|  
|----------|----------------|  
|certificat X.509|Format standard des certificats utilisés par les processus à base de certificat de Windows. Un certificat X.509 comprend la clé publique et des informations sur la personne ou l'entité à laquelle le certificat est délivré, des informations relatives au certificat, ainsi que des informations facultatives sur l'Autorité de certification qui délivre le certificat.|  
|XDR|Voir XDR (XML-Data Reduced).|  
|XSD (XML Schema definition language)|Langage de schéma. Un schéma XML définit les types de données, des attributs et des éléments qui se conforment à World Wide Web Consortium (W3C) XML Schema Part 1 : Structures Recommendation pour le langage de définition de schéma XML. W3C XML Schema Part 2 : Datatypes Recommendation est à définir les types de données utilisés dans les schémas XML. Le langage XSD permet de définir la structure et les types de données des messages XML.|  
|XDR (XML-Data Reduced)|L'une des nombreuses façons de définir la structure d'un document XML.  BizTalk Server est en mesure d'ouvrir un schéma décrit à l'aide de la définition XDR, mais doit le convertir en langage de définition du schéma XML durant le processus.|  
|XPath|Langage complet permettant de naviguer dans la hiérarchie d'un document XML. Les expressions XPath peuvent contenir des informations sur des attributs et des éléments XML. Elles permettent de rechercher des données correspondant à des critères spécifiques et de comparer les données qui ont été extraites. XPath est également appelé « chemin d'accès au nœud ».|  
|XSD|Voir XSD (XML Schema Definition language).|  
|XSLT|Voir Langage de transformation par feuilles de styles extensible (XSLT, Extensible Stylesheet Language Transformations).|  
  
## <a name="z"></a>Z  
  
|Terme|Définition|  
|----------|----------------|  
|zombie|Message qui n'a pas été traité par une orchestration. Il ne se trouve pas dans la file d'attente des messages interrompus, ni à un autre emplacement où il pourrait faire l'objet d'une nouvelle tentative.|  
|réactivateur de zombie|Orchestration qui recherche les zombies dans la base de données MessageBox et réactive ceux qui satisfont certains critères.|
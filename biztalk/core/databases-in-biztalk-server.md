---
title: "Bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Archive database [BAM]
- Analysis database [BAM]
- Windows SharePoint Services, content database
- Windows SharePoint Services, configuration database
- TPM database
- BizTalk Server, databases
- Notification Services Instance database [BAM]
- Star Schema database [BAM]
- Primary Import database [BAM]
- Rule Engine database
- databases, BizTalk Server
- SSO database
- Tracking Analysis Server database [BAM]
- Management database
- Tracking database
- MessageBox database
ms.assetid: bb504a26-cae6-4f2a-9b86-3554ef8f6045
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08cd452aa7f56ad7802c1ea458620ed9fcd21047
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="databases-in-biztalk-server"></a>Bases de données dans BizTalk Server
Microsoft BizTalk Server installe plusieurs bases de données sur le serveur SQL Server. Cette rubrique décrit ces bases de données et les groupes de la logique SQL utilisés par ces bases de données.  

## <a name="database-descriptions"></a>Descriptions de la base de données
Le tableau suivant décrit les caractéristiques d’utilisation pour la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
Opérations d’exécution BizTalk Server utilisent généralement les quatre premières bases de données : base de données de gestion BizTalk Server, bases de données MessageBox, base de données de suivi et de la base de données SSO. Selon la fonctionnalité BizTalk Server employée, vous pouvez disposer de tout ou partie des bases de données de ce tableau.  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Analyse BAM|BAMAnalysis|Base de données contenant les cubes OLAP d'analyse BAM pour les analyses en ligne et hors ligne.|  
|Archives BAM|BAMArchive|Base de données dans laquelle sont archivées les anciennes données d'activité d'entreprise. Créez une base de données d'archives de l'analyse BAM pour réduire la quantité de données d'activité d'entreprise accumulées dans la base de données d'importation principale BAM.|  
|Base de données de l'application des services de notification BAM|BAMAlertsApplication|Cette base de données contient des informations d'alerte relatives aux notifications BAM. Par exemple, lorsque vous créez une alerte à partir du portail BAM, des entrées spécifiant les conditions et les événements auxquels l'alerte se rapporte ainsi que des éléments de données relatifs à l'alerte sont insérés dans la base de données.|  
|Base de données de l'instance des services de notification BAM|BAMAlertsNSMain|Cette base de données des informations d'instance précisant la manière dont les services de notification se connectent au système contrôlé par l'analyse BAM.|  
|Base de données d'importation principale BAM|BAMPrimaryImport|C'est dans cette base de données que l'analyse BAM collecte les des données de suivi brutes.|  
|Schémas en étoile BAM|BAMStarSchema|Cette base de données contient le tableau intermédiaire et les tables de mesures et de dimensions.|  
|Base de données de gestion BizTalk|BizTalkMgmtDb|Cette base de données constitue la banque centrale de méta-informations de toutes les instances de BizTalk Server.|  
|Base de données MessageBox de BizTalk|BizTalkMsgBoxDb|Cette base de données est utilisée par le moteur de BizTalk Server pour le routage, la mise en file d'attente, la gestion des instances et de nombreuses autres tâches.|  
|Base de données des suivis BizTalk|BizTalkDTADb|Cette base de données stocke les données d'analyse du fonctionnement traitées par le moteur de suivis BizTalk Server.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Cette base de données constitue un référentiel pour les éléments suivants :<br /><br /> -Les stratégies, qui sont des ensembles de règles associées.<br />-Les vocabulaires, qui sont des collections de noms conviviaux spécifique à un domaine pour référencer des données dans les règles.|  
|Base de données SSO|SSODB|Cette base de données d'authentification unique de l'entreprise stocke en toute sécurité les informations de configuration relatives aux emplacements de réception.|  
|Base de données de configuration de Windows SharePoint Services|*Défini par l’utilisateur*|Cette base de données contient tous les paramètres généraux du serveur.|  
|Base de données de contenu Windows SharePoint Services|*Défini par l’utilisateur*|Cette base de données stocke tout le contenu du site, notamment les éléments de liste et les documents.|  

## <a name="database-login-accounts"></a>Comptes de connexion de base de données

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]crée des groupes de connexion SQL et les mappe vers les rôles SQL Server et les rôles de base de données répertoriées dans le tableau suivant :  
  
|Grouper|Description|Rôles de serveur SQL Server ou rôles de base de données|  
|-----------|-----------------|----------------------------------------|  
|Utilisateurs d'applications BizTalk|Inclut tous les comptes ayant accès aux hôtes BizTalk In-Process (processus hôte dans BizTalk Server, BTSNTSvc.exe).  Utilisez un groupe d'hôtes BizTalk pour chaque hôte In-Process de votre environnement.|Rôle de base de données de serveur SQL Server BTS_HOST_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> Rôle de base de données de serveur SQL Server BAM_EVENT_WRITER dans la base de données BAMPrimaryImport|  
|Utilisateurs d'hôtes BizTalk isolés|Inclut tous les comptes ayant accès aux hôtes BizTalk isolés. Utilisez un groupe d'hôtes BizTalk isolés unique pour chaque hôte isolé de votre environnement.|Rôle de base de données de serveur SQL Server BTS_HOST_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|Administrateurs BizTalk Server|Inclut tous les administrateurs BizTalk Server qui vont déployer des solutions, gérer des applications et résoudre les problèmes liés au traitement des messages.|Rôle de base de données de serveur SQL Server BTS_ADMIN_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> Rôle de base de données de serveur SQL Server db_owner pour les bases de données suivantes :<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de base de données de serveur SQL Server NSAdmin dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> Administrateurs OLAP sur l'ordinateur hébergeant la base de données OLAP BAMAnalysis.|  
|Opérateurs BizTalk Server|Possède un rôle affecté de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.<br /><br /> Ne contient aucun compte de service.|Rôle de base de données de serveur SQL Server BTS_OPERATORS dans les bases de données suivantes :<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|Administrateurs SSO|Administrateurs de niveau supérieur du service d'authentification unique de l'entreprise.<br /><br /> Contient le compte d'utilisateur utilisé pour exécuter la configuration de BizTalk.<br /><br /> Contient le compte de service de l'authentification unique de l'entreprise et tout utilisateur/groupe devant être habilité à configurer et à administrer BizTalk Server et l'authentification unique.|Rôle de la base de données de serveur SQL Server db_owner pour l'authentification unique<br /><br /> Rôle de serveur SQL Server securityadmin pour le serveur SQL Server sur lequel est située l'authentification unique|  

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]crée des comptes de connexion SQL et les mappe aux rôles de base de données SQL Server répertoriées dans le tableau suivant :  
  
|Compte d'utilisateur|Description|Rôles SQL de base de données|  
|------------------|-----------------|------------------------|  
|Service de mise à jour du moteur des règles|Compte d'utilisateur utilisé pour le service de mise à jour du moteur des règles.|Rôle de base de données de serveur SQL Server RE_HOST_USERS dans la base de données BizTalkRuleEngineDb|  
|Utilisateur des services de notification BAM|Compte d'utilisateur utilisé pour les services de notification de l'analyse BAM.|Rôle de base de données du serveur SQL Server NSRunService dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de base de données SQL Server BAM_ManagementNSReader pour la base de données BAMPrimaryImport|  
|Utilisateur de service Web de gestion BAM|Compte d'utilisateur utilisé pour le service Web de gestion BAM.|Rôle de base de donnés du serveur SQL Server NSSubscriberAdmin dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de base de données SQL Server BAM_ManagementWS pour la base de données BAMPrimaryImport|  
  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et la Structure de base de données](../core/database-structure-and-jobs.md)   
 [La base de données MessageBox](../core/the-messagebox-database.md)   
 [Gestion de BizTalk Server](../technical-guides/maintaining-biztalk-server-databases.md)   
 [Mise à l’échelle de vos Solutions](../core/scaling-your-solutions.md)   
 [Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md)
---
title: "Groupes Windows et les comptes d’utilisateur dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, BTS_ADMIN_USERS role [SQL Server database]
- MessageBox database, BTS_HOST_USERS role [SQL Server database]
- Rule Engine database, BTS_HOST_USERS role [SQL Server database]
- Management database, BTS_OPERATORS role [SQL Server database]
- BTS_HOST_USERS role [SQL Server database]
- NSSubscriberAdmin role [SQL Server database]
- Management database, tpm_user role [SQL Server database]
- SSO, securityadmin role [SQL Server database]
- IIS_WPG group
- BAM Notification service account
- EDI_ADMIN_USERS role [SQL Server database]
- Archive database [BAM], db_owner role [SQL Server database]
- Primary Import database [BAM], db_owner role [SQL Server database]
- Primary Import database [BAM], BAM_EVENT_WRITER role [SQL Server database]
- Notification Services Application database [BAM], db_owner role [SQL Server database]
- NSRunService role [SQL Server database]
- RE_HOST_USERS role [SQL Server database]
- MessageBox database, BTS_OPERATORS role [SQL Server database]
- Rule Engine database, RE_HOST_USERS role [SQL Server database]
- Windows groups, creating
- securityadmin role [SQL Server database]
- BizTalk Isolated Host Instance service account
- In-Process BizTalk Host groups
- Primary Import database [BAM], BTS_ADMIN_USERS role [SQL Server database]
- SSO Affiliate Administrators [Windows group]
- Star Schema database [BAM], db_owner role [SQL Server database]
- Notification Services Instance database [BAM], db_owner role [SQL Server database]
- MessageBox database, BTS_ADMIN_USERS role [SQL Server database]
- Rule Engine Update Service account
- Configuration Manager, creating user accounts
- SSO Administrators [Windows group]
- Rule Engine database, BTS_ADMIN_USERS role [SQL Server database]
- Tracking database, BTS_OPERATORS role [SQL Server database]
- Primary Import database [BAM], BAM_ManagementNSReader role [SQL Server database]
- Notification Services Instance database [BAM], role [SQL Server database]
- BizTalk Application Users [Windows group]
- user accounts, creating
- Rule Engine database, BTS_OPERATORS role [SQL Server database]
- STS_WPG group
- BAM_ManagementWS role [SQL Server database]
- BTS_OPERATORS role [SQL Server database]
- Tracking database, BTS_HOST_USERS role [SQL Server database]
- SSO, db_owner role [SQL Server database]
- Notification Services Application database [BAM], role [SQL Server database]
- OLAP Administrators
- BAM_EVENT_WRITER role [SQL Server database]
- Windows groups, group list
- tpm_user role [SQL Server database]
- BizTalk Host Instance service account
- Base DBI database, EDI_ADMIN_USERS role [SQL Server database]
- Primary Import database [BAM], role [SQL Server database]
- BizTalk SharePoint Adapter Enabled Hosts [Windows group]
- BAM Management Web service account
- db_owner role [SQL Server database]
- Management database, BTS_ADMIN_USERS role [SQL Server database]
- Configuration Manager, creating groups
- Management database, BTS_HOST_USERS role [SQL Server database]
- BizTalk Server Operators [Windows group]
- Base DBI database, BTS_OPERATORS role [SQL Server database]
- Enterprise Single Sign-On Service account
- NSAdmin role [SQL Server database]
- BAM_ManagementNSReader role [SQL Server database]
- Notification Services Application database [BAM], NSRunService role [SQL Server database]
- BTS_ADMIN_USERS role [SQL Server database]
- BizTalk Isolated Host Users [Windows group]
- Notification Services Instance database [BAM], NSAdmin role [SQL Server database]
- SQLServer2005NotificationServicesUser
- EDI Subsystem Users [Windows group]
- Primary Import database [BAM], BTS_HOST_USERS role [SQL Server database]
- BizTalk Server Administrators [Windows group]
- BAM Portal Users [Windows group]
- Notification Services Application database [BAM], NSAdmin role [SQL Server database]
ms.assetid: a01603bd-4105-4691-819d-de43b00b40f3
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a04b8e774156acaaa44dc49377bbdd7e3f91b198
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="windows-groups-and-user-accounts-in-biztalk-server"></a>Groupes et comptes d'utilisateur Windows dans BizTalk Server
Informations sur les comptes BizTalk Server local et le domaine utilisateur et de groupe. Le Gestionnaire de configuration crée les comptes de groupe BizTalk nécessaires par défaut si vous installez BizTalk Server et tous les logiciels requis sur un seul ordinateur. Les informations contenues dans cette section s'appliquent à plusieurs topologies informatiques.  
  
> [!IMPORTANT]
>  BizTalk Server prend en charge les comptes d'utilisateur et de groupe locaux uniquement dans des configurations ne comprenant qu'un seul ordinateur. BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs. Si vous utilisez des groupes de domaine pour configurer BizTalk Server, vous devez créer manuellement les groupes avant de configurer BizTalk Server. Le Gestionnaire de configuration ne peut pas créer de groupes de domaine.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-windows-group-and-user-accounts-in-biztalk-server"></a>Pour créer des comptes de groupe et d'utilisateur Windows dans BizTalk Server  
  
1.  À l’aide d’Active Directory, à partir de la **Démarrer** menu, pointez sur **programmes**, pointez sur **outils d’administration**, puis sélectionnez **utilisateurs Active Directory et Ordinateurs**.  
  
2.  Dans la fenêtre Active Directory Users and Computers, cliquez sur en bas du volet de droite, ou cliquez sur le **utilisateurs** dossier dans l’arborescence de navigation dans le volet gauche.  
  
3.  Sélectionnez **nouveau**, puis sélectionnez **groupe** ou **utilisateur**.  
  
4.  Entrez les informations de groupe ou d'utilisateur indiquées dans le tableau suivant.  
  
 Le tableau suivant répertorie le groupe Windows et leur appartenance utilisés par BizTalk Server. Il identifie également les rôles de serveur SQL Server ou les rôles de base de données pour les groupes.  
  
|Grouper|Description du groupe|Adhésion|Rôles de serveur SQL Server ou rôles de base de données|  
|-----------|-----------------------|----------------|----------------------------------------|  
|Administrateurs SSO|Administrateur du service d'authentification unique de l'entreprise|Contient les comptes de service pour le service d'authentification unique de l'entreprise.<br /><br /> Contient les utilisateurs/groupes qui doivent être capables de configurer et d'administrer BizTalk Server et le service d'authentification unique.<br /><br /> Contient les comptes utilisés pour exécuter le Gestionnaire de configuration BizTalk lors de la configuration du serveur de secret principal de l'authentification unique.|Rôle de la base de données de serveur SQL Server db_owner pour l'authentification unique<br /><br /> Rôle de serveur SQL Server securityadmin pour le serveur SQL Server sur lequel est située l'authentification unique|  
|Administrateurs d'applications associées à authentification unique|Administrateurs de certaines applications associées à authentification unique.<br /><br /> Peut créer/supprimer des applications associées SSO, administrer des mappages d’utilisateur et définir les informations d’identification pour associée utilisateurs d’applications|Ne contient aucun compte de service.<br /><br /> Contient le compte utilisé pour les administrateurs BizTalk Server.||  
|Administrateurs BizTalk Server|Dispose des privilèges nécessaires pour effectuer des tâches d’administration<br /><br /> Peut déployer des solutions, gérer des applications et résoudre des problèmes liés au traitement des messages.<br /><br /> Pour effectuer des tâches d'administration pour les adaptateurs, les gestionnaires de réception et d'envoi et les emplacements de réception, les administrateurs BizTalk Server doivent être ajoutés aux administrateurs d'applications associées à authentification unique.<br /><br /> Pour plus d’informations, consultez [sécurité de la gestion de BizTalk Server](../core/managing-biztalk-server-security.md).|Contient les utilisateurs/groupes qui doivent être capables de configurer et d'administrer BizTalk Server.|Rôle de base de données de serveur SQL Server BTS_ADMIN_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> Rôle de base de données de serveur SQL Server db_owner pour les bases de données suivantes :<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de base de données de serveur SQL Server NSAdmin dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Administrateurs OLAP sur l'ordinateur hébergeant la base de données OLAP BAMAnalysis.|  
|Opérateurs BizTalk Server|Possède un rôle affecté de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.<br /><br /> Pour plus d’informations, consultez [sécurité de la gestion de BizTalk Server](../core/managing-biztalk-server-security.md)|Contient des utilisateurs/des groupes chargés de la surveillance des solutions.<br /><br /> Ne contient aucun compte de service.|Rôle de base de données de serveur SQL Server BTS_OPERATORS dans les bases de données suivantes :<br /><br /> BizTalkDTADb<br /><br /> BizTalkEDIDb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|Utilisateurs d'applications BizTalk|Nom par défaut du premier groupe d'hôtes BizTalk In-Process créé par le Gestionnaire de configuration.<br /><br /> Utilisez un groupe d'hôtes BizTalk pour chaque hôte In-Process de votre environnement.<br /><br /> Inclut des comptes ayant accès aux hôtes BizTalk In-Process (processus hôte dans BizTalk Server, BTSNTSvc.exe).|Contient des comptes de service pour l'instance d'hôte BizTalk In-Process dans l'hôte auquel est associé le groupe d'hôtes BizTalk.|Rôle de base de données de serveur SQL Server BTS_HOST_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> Rôle de base de données de serveur SQL Server BAM_EVENT_WRITER dans la base de données BAMPrimaryImport|  
|Utilisateurs d'hôtes BizTalk isolés|Nom par défaut du premier groupe d'hôtes BizTalk isolés créé par le Gestionnaire de configuration. Hôtes BizTalk isolés ne s'exécutant pas sur BizTalk Server, tels que HTTP et SOAP.<br /><br /> Utilisez un groupe d'hôtes BizTalk isolés unique pour chaque hôte isolé de votre environnement.|Contient des comptes de service pour l'instance d'hôte BizTalk isolé dans l'hôte auquel est associé le groupe d'hôtes BizTalk isolés.|Rôle de base de données de serveur SQL Server BTS_HOST_USERS dans les bases de données suivantes :<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|Utilisateurs du portail BAM|Dispose de l'accès au site Web du portail BAM.|Le groupe Tout le monde est utilisé par défaut pour ce rôle.<br /><br /> Ne contient aucun compte de service.||  
|Hôtes avec adaptateur BizTalk SharePoint activé|Dispose de l'accès au service Web de l'adaptateur Windows SharePoint Services.|Contient des comptes de service pour permettre à l'instance de l'hôte BizTalk d'appeler l'adaptateur SharePoint.||  
|Groupe Opérateurs B2B BizTalk|Nouveau rôle BizTalk qui réduit la charge des administrateurs dans la réalisation de toutes les opérations de gestion des tiers. Ce rôle permet aux utilisateurs Windows associés au rôle de réaliser toutes les opérations de gestion des tiers.|Il contient les utilisateurs/groupes qui doivent être en mesure de configurer et de gérer les données GPC BizTalk Server ainsi que de surveiller les solutions.|Rôle de base de données SQL Server BTS_OPERATORS dans les bases de données suivantes : BizTalkDTADb, BizTalkMgmtDb, BizTalkMsgBoxDb, BizTalkRuleEngineDb et BAMPrimaryImport|  
  
 Le tableau suivant répertorie les comptes d'utilisateur ou de service Windows et les affiliations de groupe utilisés par BizTalk Server. Il identifie également les rôles de serveur SQL Server ou les rôles de base de données pour les comptes.  
  
|Utilisateur|Description de l'utilisateur|Affiliation de groupe|Rôles de serveur SQL Server ou rôles de base de données|  
|----------|----------------------|-----------------------|----------------------------------------|  
|Service d'authentification unique de l'entreprise|Compte de service utilisé pour exécuter le service d'authentification unique de l'entreprise qui accède à la base de données d'authentification unique.|Administrateurs SSO||  
|Compte de l'instance de l'hôte BizTalk|Compte de service utilisé pour exécuter l'instance de l'hôte BizTalk de type In-Process qui accède à l'instance d'hôte BizTalk de type In-Process (BTNTSVC).|Utilisateurs d'applications BizTalk<br /><br /> Administrateurs d'applications associées à authentification unique||  
|Compte de l'instance de l'hôte BizTalk isolé|Compte de service utilisé pour exécuter l'instance de l'hôte BizTalk isolé (HTTP/SOAP).|Utilisateurs d'hôtes BizTalk isolés<br /><br /> Administrateurs d'applications associées à authentification unique<br /><br /> IIS_WPG||  
|Service de mise à jour du moteur des règles|Compte de service utilisé pour exécuter le Service de mise à jour du moteur des règles qui reçoit des notifications aux stratégies de déploiement/annulation du déploiement à partir de la base de données du moteur de règles.||Rôle de base de données de serveur SQL Server RE_HOST_USERS dans la base de données BizTalkRuleEngineDb|  
|Utilisateur des services de notification BAM|Compte de service utilisé pour exécuter les services de notification BAM, qui accède aux bases de données BAM.|SQLServer2008NotificationServicesUser$\<**Nom_Ordinateur**\>|Rôle de base de données du serveur SQL Server NSRunService dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de serveur SQL Server BAM_ManagementNSReader pour la base de données BAMPrimaryImport|  
|Utilisateur de service Web de gestion de l'analyse BAM|Compte d'utilisateur pour le service Web de gestion de l'analyse BAM (BAMManagementService) pour l'accès aux diverses ressources BAM. Le portail BAM appelle BAMManagementService avec les informations d’identification de l’utilisateur connectées sur le portail BAM pour gérer les alertes, obtenir des vues BAM et XML de définition BAM|IIS_WPG|Rôle de base de donnés du serveur SQL Server NSSubscriberAdmin dans les bases de données suivantes :<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> Rôle de serveur SQL Server BAM_ManagementWS pour la base de données BAMPrimaryImport|  
|Compte de Pool d’applications BAM|Compte du pool d'applications BAMAppPool qui héberge le site Web du portail BAM.|IIS_WPG||  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Groupes locaux](../core/local-groups.md)  
  
-   [Groupes de domaine](../core/domain-groups.md)
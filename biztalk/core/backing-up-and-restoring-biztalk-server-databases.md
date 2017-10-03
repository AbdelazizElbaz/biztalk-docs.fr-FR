---
title: "Sauvegarde et restauration des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up [BAM]
- databases, backing up
- databases, restoring
- backing up, restoring
- backing up, databases
- restoring, BAM
- backing up, BAM
- backing up, backup jobs
- BAM, restoring
- restoring, databases
- restoring [BAM]
- BAM, backing up
ms.assetid: 82fc1af2-1389-4c79-80dc-f2df5656d201
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dba0e9e7cb5d01bf845eaa4adf3557dc3b6ea34a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-biztalk-server-databases"></a>Sauvegarde et restauration des bases de données BizTalk Server
Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de sauvegarder toutes les bases de données de votre système source [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], à l'exception de certaines d'entre elles qui sont utilisées par l'analyse BAM (Business Activity Monitoring). Un système source est constitué d'un serveur ou groupe de serveurs contenant des données actives. En raison des exigences de sauvegarde et de restauration particulières auxquelles sont soumises les bases de données BAM, celles-ci sont sauvegardées et restaurées à l'aide d'autres méthodes.  
  
 Les opérations de sauvegarde et de restauration des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se déroulent selon les étapes suivantes :  
  
1.  **Configuration du travail de sauvegarde de BizTalk Server**  
  
     Avant que vous ne puissiez sauvegarder les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez configurer le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le système source ; les sauvegardes sont alors écrites automatiquement dans un dossier où elles pourront être utilisées pour restaurer les bases de données sur le système de destination. Un système de destination est constitué d'un serveur ou groupe de serveurs qui est utilisé pour restaurer des sauvegardes de base de données produites par un système source. Pour plus d’informations sur cette étape, consultez [comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md).  
  
2.  **Configuration du système de destination pour l’envoi de journaux**  
  
     Vous devez également configurer le système de destination pour l'envoi de journaux. L'envoi de journaux offre des fonctionnalités de serveur de secours, ce qui réduit le temps mort en cas de défaillance du système. Pour plus d’informations sur cette étape, consultez [comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md).  
  
3.  **Restauration des bases de données**  
  
     En cas de défaillance du système, vous pouvez restaurer vos bases de données à l'aide des sauvegardes et des journaux envoyés au système de destination. Pour plus d’informations sur cette étape, consultez [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).  
  
## <a name="biztalk-server-databases"></a>Bases de données BizTalk Server  
 Le tableau suivant répertorie les bases de données utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et identifie les méthodes de sauvegarde de ces bases de données.  
  
### <a name="databases-backed-up-by-the-backup-biztalk-server-job"></a>Bases de données sauvegardées par le travail de sauvegarde de BizTalk Server  
 Le tableau suivant répertorie les bases de données dont la sauvegarde et la restauration relèvent du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez modifier le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à ce qu'il sauvegarde des bases de données personnalisées en les ajoutant à la table adm_OtherBackupDatabases. Pour plus d’informations, consultez [arrière des personnalisé bases de données](../core/how-to-back-up-custom-databases.md).  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Base de données dans laquelle l'analyse BAM collecte les données de suivi brutes.|  
|Base de données de l'application des services de notification BAM|BAMAlertsApplication|Cette base de données contient des informations d'alerte relatives aux notifications BAM. Par exemple, lorsque vous créez une alerte à partir du portail BAM, des entrées spécifiant les conditions et les événements auxquels l'alerte se rapporte ainsi que des éléments de données relatifs à l'alerte sont insérés dans la base de données.|  
|Base de données de l'instance des services de notification BAM|BAMAlertsNSMain|Cette base de données des informations d'instance précisant la manière dont les services de notification se connectent au système contrôlé par l'analyse BAM.|  
|Base de données des suivis BizTalk|BizTalkDTADb|Cette base de données stocke les données d'analyse du fonctionnement traitées par le moteur de suivis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|Base de données de gestion BizTalk|BizTalkMgmtDb|Cette base de données constitue la banque centrale de méta-informations de toutes les instances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|Base de données MessageBox de BizTalk|BizTalkMsgBoxDb|Cette base de données est utilisée par le moteur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le routage, la mise en file d'attente, la gestion des instances et de nombreuses autres tâches.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Cette base de données constitue un référentiel pour les éléments suivants :<br /><br /> -Les stratégies, qui sont des ensembles de règles associées.<br />-Les vocabulaires, qui sont des collections de noms conviviaux spécifique à un domaine pour référencer des données dans les règles.|  
|Base de données SSO|SSODB|Cette base de données d'authentification unique de l'entreprise stocke en toute sécurité les informations de configuration relatives aux emplacements de réception.|  
  
### <a name="databases-backed-up-by-the-bam-backup-process"></a>Bases de données sauvegardées par le processus de sauvegarde de l'analyse BAM  
 Le tableau suivant répertorie les bases de données sont sauvegardées et restaurées à l’aide des procédures dans [sauvegarde et restauration de BAM](../core/backing-up-and-restoring-bam.md):  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Schémas en étoile BAM|BAMStarSchema|Cette base de données contient le tableau intermédiaire et les tables de mesures et de dimensions.|  
|Analyse BAM|BAMAnalysis|Cette base de données contient les cubes OLAP d'analyse BAM pour les analyses en ligne et hors ligne.|  
|Archives BAM|BAMArchive|Base de données dans laquelle sont archivées les anciennes données d'activité d'entreprise. Créez une base de données d'archives de l'analyse BAM pour réduire la quantité de données d'activité d'entreprise accumulées dans la base de données d'importation principale BAM.|  
|Serveur Analyse des suivis|BizTalkAnalysisDb|Cette base de données contient les cubes OLAP d'analyse de fonctionnement.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration du travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)  
  
-   [Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
-   [Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md)  
  
-   [Comment sauvegarder et restaurer des travaux de l’Agent SQL](../core/how-to-back-up-and-restore-sql-agent-jobs.md)  
  
-   [Comment sauvegarder et restaurer les connexions SQL Server](../core/how-to-back-up-and-restore-sql-server-logins.md)
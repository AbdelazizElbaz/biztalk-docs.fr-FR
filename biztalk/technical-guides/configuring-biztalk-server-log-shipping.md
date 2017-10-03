---
title: Journaux de configuration de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcef31f7-30d1-4ada-b627-2a5c9ec7e43e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3209d96c4516c603510f3cbb7fb48e3b1eb3209
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-biztalk-server-log-shipping"></a>Journaux de configuration de BizTalk Server
Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de sauvegarder toutes les bases de données de votre système source [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], à l'exception de certaines d'entre elles qui sont utilisées par l'analyse BAM (Business Activity Monitoring). Un système source est constitué d'un serveur ou groupe de serveurs contenant des données actives. Étant donné que certaines des bases de données BAM ont autre sauvegarde et restaurer la configuration requise, ces bases de données sont sauvegardées et restaurées à l’aide d’autres méthodes.  
  
 Les opérations de sauvegarde et de restauration des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se déroulent selon les étapes suivantes :  
  
1.  **Configuration du travail de sauvegarde de BizTalk Server**  
  
     Avant que vous ne puissiez sauvegarder les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez configurer le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le système source ; les sauvegardes sont alors écrites automatiquement dans un dossier où elles pourront être utilisées pour restaurer les bases de données sur le système de destination. Un système de destination est constitué d'un serveur ou groupe de serveurs qui est utilisé pour restaurer des sauvegardes de base de données produites par un système source. Pour plus d’informations sur cette étape, consultez [comment configurer un travail de sauvegarde de BizTalk Server](../technical-guides/how-to-configure-a-backup-biztalk-server-job.md).  
  
2.  **Configuration du système de destination pour l’envoi de journaux**  
  
     Vous devez également configurer le système de destination pour l'envoi de journaux. L'envoi de journaux offre des fonctionnalités de serveur de secours, ce qui réduit le temps mort en cas de défaillance du système. Pour plus d’informations sur cette étape, consultez [comment configurer le système de Destination](../technical-guides/how-to-configure-the-destination-system.md).  
  
3.  **Restauration des bases de données**  
  
     En cas de défaillance du système, vous pouvez restaurer vos bases de données à l'aide des sauvegardes et des journaux envoyés au système de destination. Pour plus d’informations sur cette étape, consultez [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).  
  
## <a name="biztalk-server-databases"></a>Bases de données BizTalk Server  
 Le tableau suivant répertorie les bases de données utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et identifie les méthodes de sauvegarde de ces bases de données.  
  
### <a name="databases-backed-up-by-the-backup-biztalk-server-job"></a>Bases de données sauvegardées par le travail de sauvegarde de BizTalk Server  
 Le tableau suivant répertorie les bases de données sont sauvegardées et restaurées dans le cadre de la tâche de sauvegarde de BizTalk Server. Vous pouvez modifier le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à ce qu'il sauvegarde des bases de données personnalisées en les ajoutant à la table adm_OtherBackupDatabases. Pour plus d’informations, consultez [arrière des personnalisé bases de données](http://go.microsoft.com/fwlink/?LinkID=151569) (http://go.microsoft.com/fwlink/?LinkID=151569).  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Base de données dans laquelle l'analyse BAM collecte les données de suivi brutes.|  
|Base de données de l'application des services de notification BAM|BAMAlertsApplication|Cette base de données contient des informations d'alerte relatives aux notifications BAM. Par exemple, lorsque vous créez une alerte à partir du portail BAM, des entrées spécifiant les conditions et les événements auxquels l'alerte se rapporte ainsi que des éléments de données relatifs à l'alerte sont insérés dans la base de données.|  
|Base de données de l'instance des services de notification BAM|BAMAlertsNSMain|Cette base de données des informations d'instance précisant la manière dont les services de notification se connectent au système contrôlé par l'analyse BAM.|  
|Base de données des suivis BizTalk|BizTalkDTADb|Cette base de données stocke les données d'analyse du fonctionnement traitées par le moteur de suivis BizTalk Server.|  
|Base de données de gestion BizTalk|BizTalkMgmtDb|Cette base de données constitue la banque centrale de méta-informations de toutes les instances de BizTalk Server.|  
|Base de données MessageBox de BizTalk|BizTalkMsgBoxDb|Cette base de données est utilisée par le moteur de BizTalk Server pour le routage, la mise en file d'attente, la gestion des instances et de nombreuses autres tâches.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Cette base de données constitue un référentiel pour les éléments suivants :<br /><br /> -Les stratégies, qui sont des ensembles de règles associées.<br />-Les vocabulaires, qui sont des collections de noms conviviaux spécifique à un domaine pour référencer des données dans les règles.|  
|Base de données SSO|SSODB|Cette base de données Enterprise Single Sign-On stocke en toute sécurité la configuration des informations pour les emplacements de réception.|  
  
### <a name="databases-backed-up-when-backing-up-the-bam-analysis-and-tracking-analysis-server-databases"></a>Bases de données sauvegardées lors de la sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur  
 Le tableau suivant répertorie les bases de données qui sont sauvegardés en utilisant les procédures dans [sauvegarde de l’analyse BAM et de suivi de base de données Analysis Server](http://msdn.microsoft.com/library/aa578580\(v=bts.70\).aspx):  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Schémas en étoile BAM|BAMStarSchema|Cette base de données contient le tableau intermédiaire et les tables de mesures et de dimensions.|  
|Analyse BAM|BAMAnalysis|Cette base de données contient les cubes OLAP d'analyse BAM pour les analyses en ligne et hors ligne.|  
|Archives BAM|BAMArchive|Base de données dans laquelle sont archivées les anciennes données d'activité d'entreprise. Créez une base de données d'archives de l'analyse BAM pour réduire la quantité de données d'activité d'entreprise accumulées dans la base de données d'importation principale BAM.|  
|Serveur Analyse des suivis|BizTalkAnalysisDb|Cette base de données contient les cubes OLAP d'analyse de fonctionnement.|  
  
 Cette section du guide d’exploitation décrit les étapes supplémentaires que vous devez suivre pour configurer BizTalk Server des journaux.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration du système Source](../technical-guides/configuring-the-source-system.md)  
  
-   [Comment configurer le système de Destination](../technical-guides/how-to-configure-the-destination-system.md)  
  
-   [Configuration des journaux de BizTalk Server pour les bases de données supplémentaires](../technical-guides/configuring-biztalk-server-log-shipping-for-additional-databases.md)  
  
-   [Analyse de BizTalk Server des journaux](../technical-guides/monitoring-biztalk-server-log-shipping.md)
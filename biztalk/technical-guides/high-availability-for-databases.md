---
title: "Haute disponibilité pour les bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63813d87-1ce4-4645-bb2a-d55e413fcace
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 415b1bbe86df1b7ee3feaeec13c889dfe2a4a902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-databases"></a>Haute disponibilité pour les bases de données
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s’appuie essentiellement sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour le magasin de données et la persistance des données. Tous les autres composants et hôtes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jouent un rôle précis dans le processus d'intégration d'applications d'entreprise hétérogènes (par exemple : la réception, le traitement ou le routage des messages) tandis que l'ordinateur hébergeant les bases de données enregistre ces travaux pour les conserver sur le disque. Par exemple, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message entrant, l'hôte de réception le stocke dans la base de données MessageBox avant que d'autres hôtes le récupèrent pour le faire passer dans un processus d'orchestration avant de l'envoyer. Si votre solution BizTalk comprend une orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] achemine le message vers l’hôte qui exécute le processus d’entreprise (hôte de traitement) et enregistre le message à la base de données MessageBox une fois l’orchestration terminée. L'hôte d'envoi extrait ensuite le message de la base de données avant de l'envoyer à l'application externe concernée par l'intermédiaire de l'adaptateur d'envoi approprié.  
  
 Pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, utiliser le Clustering Windows pour configurer les deux ordinateurs ou plus qui sont en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour créer un cluster de serveurs. Ce cluster de serveurs fournit la redondance et tolérance de panne pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Dans un cluster à équilibrage de charge, plusieurs ordinateurs forment un groupe et fonctionnent ensemble dans le but d'augmenter la disponibilité et l'évolutivité de l'installation. En revanche, dans un cluster de serveurs, deux ordinateurs dédiés aux bases de données sont configurés sur un modèle actif/passif où l'une des machines fournit les ressources de sauvegarde à l'autre.  
  
 Le schéma suivant représente un niveau de base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible grâce à un cluster de serveurs actif/passif.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Si la machine de base de données active rencontre des problèmes ou s'arrête, la machine passive devient active et reprend le contrôle des ressources de base de données jusqu'à ce que la machine défaillante soit de nouveau opérationnelle. Le service de base de données bascule et restaure les connexions de données à l’ordinateur actif et permet à l’application BizTalk continuer à fonctionner.  
  
## <a name="biztalk-server-databases"></a>Bases de données BizTalk Server  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installe plusieurs bases de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Le tableau suivant présente les caractéristiques d’utilisation pour la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
|Base de données|Nom par défaut de la base de données|Caractéristiques d’utilisation|  
|--------------|---------------------------|---------------------------|  
|Management database|BizTalkMgmtDb|Cette base de données gère faible utilisation lire et écrire des opérations.|  
|Base de données MessageBox|BizTalkMsgBoxDb|Cet base de données gère de façon intensive lire et écrire des opérations.|  
|Base de données des suivis|BizTalkDTADb|Cette base de données gère les opérations d’écriture de potentiellement intensive selon la quantité de données que vous configurez pour être suivies et faible utilisation des opérations de lecture.|  
|Base de données SSO|SSODB|Cette base de données gère faible utilisation lire et écrire des opérations.|  
|Base de données d'analyse BAM|BAMAnalysis|Cela [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services en lecture potentiellement intensive de handles de base de données et les opérations d’écriture, selon le niveau de l’analyse effectuée.|  
|Base de données de schémas en étoile BAM|BAMStarSchema|Cela [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services en lecture potentiellement intensive de handles de base de données et les opérations d’écriture, selon le niveau de l’analyse effectuée.|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Cela [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services en lecture potentiellement intensive de handles de base de données et les opérations d’écriture, selon le niveau de l’analyse effectuée.|  
|Base de données des archives de l'analyse BAM|BAMArchive|Cela [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services en lecture potentiellement intensive de handles de base de données et les opérations d’écriture, selon le niveau de l’analyse effectuée.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Cette base de données gère potentiellement faible utilisation d’opérations de lecture et écriture, sauf si vous mettez à jour les règles.|  
|Base de données Analysis Services|BizTalkAnalysisDb|Cela [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services en lecture de handles de façon intensive la base de données et les opérations d’écriture.|  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]opérations d’exécution utilisent généralement les quatre premières bases de données (base de données de gestion, les bases de données MessageBox, suivi de base de données et base de données SSO). Selon le trafic sur ces bases de données, vous pouvez les placer sur des ordinateurs distincts qui sont en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. En fonction de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les fonctionnalités que vous utilisez, vous avez peut-être certaines ou toutes les autres bases de données dans la table. Vous pouvez monter en charge et ces bases de données de cluster en fonction des besoins.  
  
 Assurez-vous que vous suivez bien [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pratiques de déploiement, telles que l’utilisation des disques distincts pour chaque base de données. Pour plus d’informations sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les meilleures pratiques de déploiement, consultez [livre blanc : haute disponibilité : Always On Technologies](http://go.microsoft.com/fwlink/?LinkId=156812) (http://go.microsoft.com/fwlink/?LinkId=156812).  
  
 Pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, nous vous recommandons d’effectuer ce qui suit :  
  
-   **Configurer le clustering de basculement**. Permet le clustering de basculement [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de basculer automatiquement le traitement d’une instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] à partir d’un serveur défaillant et un serveur opérationnel.  
  
     La base de données d'importation principale BAM collecte les données d'événement. En cas de sinistre, les données ajoutées à cette base de données depuis la dernière sauvegarde seront perdues. Comme il n’existe aucun moyen de régénérer les événements perdus, il est particulièrement important d’activer le clustering de basculement sur votre base de données d’importation principale BAM.  
  
-   **Utilisez SQL Server RAID 1 + 0 (baie redondante de disques indépendants)**, en particulier pour la base de données MessageBox et la base de données d’importation principale BAM.  
  
 Pour plus d’informations sur la sauvegarde votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [meilleures pratiques pour la récupération d’urgence](../technical-guides/best-practices-for-disaster-recovery.md).  
  
> [!NOTE]  
>  Microsoft [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] fournissent une solution logicielle appelée mise en miroir de base de données permettant d’accroître la probabilité qu’une base de données est disponible. L’utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] mise en miroir de base de données n’est pas actuellement pris en charge pour garantir la haute disponibilité de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données en raison de certaines difficultés à maintenir la cohérence des transactions dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
>   
>  Pour plus d’informations sur la mise en miroir de base de données et des transactions de bases de données croisées dans [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], consultez [http://go.microsoft.com/fwlink/?LinkId=87977](http://go.microsoft.com/fwlink/?LinkId=87977). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]bases de données doivent être installés sur un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster pour garantir une haute disponibilité et l’envoi de journaux doit être utilisée à des fins de récupération d’urgence.  
>   
>  Pour plus d’informations sur l’envoi de journaux, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Clustering du Databases2 de BizTalk Server](../technical-guides/clustering-the-biztalk-server-databases2.md)  
  
-   [Mise à l’échelle des bases de données BizTalk Server](../technical-guides/scaling-out-the-biztalk-server-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Planification pour une haute disponibilité2](../technical-guides/planning-for-high-availability2.md)   
 [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)
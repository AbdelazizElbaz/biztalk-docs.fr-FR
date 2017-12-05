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
ms.openlocfilehash: 24e17afbf9e33f3e12553d7ded5068370d8ca085
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="high-availability-for-databases"></a>Haute disponibilité pour les bases de données
BizTalk Server s’appuie fortement sur SQL Server pour le magasin de données et la persistance des données. Tous les autres composants et hôtes de BizTalk Server jouent un rôle précis dans le processus d'intégration des applications d'entreprise (ex. : réception, traitement ou routage des messages) tandis que l'ordinateur où se trouvent les bases de données enregistre ces travaux pour les conserver sur le disque. Par exemple, lorsque BizTalk Server reçoit un message entrant, l’hôte de réception enregistre sur la base de données MessageBox avant d’autres hôtes le récupèrent le message pour l’orchestration de traitement et l’envoi. Si votre solution BizTalk comprend une orchestration, BizTalk Server achemine le message vers l’hôte qui exécute le processus d’entreprise (hôte de traitement) et enregistre le message à la base de données MessageBox une fois l’orchestration terminée. L'hôte d'envoi extrait ensuite le message de la base de données avant de l'envoyer à l'application externe concernée par l'intermédiaire de l'adaptateur d'envoi approprié.  
  
 Pour fournir une haute disponibilité pour les bases de données BizTalk Server, utilisez le Clustering Windows pour configurer deux ou plusieurs ordinateurs qui exécutent SQL Server pour créer un cluster de serveurs. Ce cluster de serveurs fournit la redondance et la tolérance de panne pour les bases de données BizTalk Server. Dans un cluster à équilibrage de charge, plusieurs ordinateurs forment un groupe et fonctionnent ensemble dans le but d'augmenter la disponibilité et l'évolutivité de l'installation. En revanche, dans un cluster de serveurs, deux ordinateurs dédiés aux bases de données sont configurés sur un modèle actif/passif où l'une des machines fournit les ressources de sauvegarde à l'autre.  
  
 Le schéma suivant représente un niveau de base de données BizTalk Server hautement disponible grâce à un cluster de serveurs actif/passif.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Si la machine de base de données active rencontre des problèmes ou s'arrête, la machine passive devient active et reprend le contrôle des ressources de base de données jusqu'à ce que la machine défaillante soit de nouveau opérationnelle. Le service de base de données bascule et restaure les connexions de données à l’ordinateur actif et permet à l’application BizTalk continuer à fonctionner.  
  
## <a name="biztalk-server-databases"></a>Bases de données BizTalk Server  
 Microsoft BizTalk Server installe plusieurs bases de données sur le serveur SQL Server. Le tableau suivant présente les caractéristiques d’utilisation pour les bases de données BizTalk Server.  
  
|Base de données|Nom par défaut de la base de données|Caractéristiques d’utilisation|  
|--------------|---------------------------|---------------------------|  
|Management database|BizTalkMgmtDb|Cette base de données gère faible utilisation lire et écrire des opérations.|  
|Base de données MessageBox|BizTalkMsgBoxDb|Cet base de données gère de façon intensive lire et écrire des opérations.|  
|Base de données des suivis|BizTalkDTADb|Cette base de données gère les opérations d’écriture de potentiellement intensive selon la quantité de données que vous configurez pour être suivies et faible utilisation des opérations de lecture.|  
|Base de données SSO|SSODB|Cette base de données gère faible utilisation lire et écrire des opérations.|  
|Base de données d'analyse BAM|BAMAnalysis|Cette base de données SQL Server Analysis Services gère potentiellement intensive opérations de lecture et écriture, selon le niveau de l’analyse effectuée.|  
|Base de données de schémas en étoile BAM|BAMStarSchema|Cette base de données SQL Server Analysis Services gère potentiellement intensive opérations de lecture et écriture, selon le niveau de l’analyse effectuée.|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Cette base de données SQL Server Analysis Services gère potentiellement intensive opérations de lecture et écriture, selon le niveau de l’analyse effectuée.|  
|Base de données des archives de l'analyse BAM|BAMArchive|Cette base de données SQL Server Analysis Services gère potentiellement intensive opérations de lecture et écriture, selon le niveau de l’analyse effectuée.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Cette base de données gère potentiellement faible utilisation d’opérations de lecture et écriture, sauf si vous mettez à jour les règles.|  
|Base de données Analysis Services|BizTalkAnalysisDb|Ce serveur SQL Server Analysis Services gère de façon intensive lire et écrire des opérations de base de données.|  
  
 Opérations d’exécution BizTalk Server utilisent généralement les quatre premières bases de données (base de données de gestion, les bases de données MessageBox, suivi de base de données et base de données SSO). Selon le trafic sur ces bases de données, vous pouvez les placer sur des ordinateurs distincts qui exécutent SQL Server. Selon la fonctionnalité BizTalk Server employée, vous pouvez disposer de tout ou partie des bases de données de ce tableau. Vous pouvez monter en charge et ces bases de données de cluster en fonction des besoins.  
  
 Assurez-vous que vous suivez les bonnes pratiques de déploiement de SQL Server, telles que l’utilisation des disques distincts pour chaque base de données.  
  
 Pour les bases de données BizTalk Server, nous vous recommandons de procéder comme suit :  
  
-   **Configurer le clustering de basculement**. Le clustering avec basculement permet à SQL Server de basculer automatiquement le traitement d’une instance de SQL Server à partir d’un serveur défaillant et un serveur opérationnel.  
  
     La base de données d'importation principale BAM collecte les données d'événement. En cas de sinistre, les données ajoutées à cette base de données depuis la dernière sauvegarde seront perdues. Comme il n’existe aucun moyen de régénérer les événements perdus, il est particulièrement important d’activer le clustering de basculement sur votre base de données d’importation principale BAM.  
  
-   **Utilisez SQL Server RAID 1 + 0 (baie redondante de disques indépendants)**, en particulier pour la base de données MessageBox et la base de données d’importation principale BAM.  
  
 Pour plus d’informations sur la sauvegarde de vos bases de données BizTalk Server, consultez [meilleures pratiques pour la récupération d’urgence](../technical-guides/best-practices-for-disaster-recovery.md).  
  
> [!NOTE]  
>  Microsoft SQL Server fournit une solution logicielle appelée mise en miroir de base de données permettant d’accroître la probabilité qu’une base de données est disponible. L’utilisation de la mise en miroir de base de données SQL Server n’est pas une solution prise en charge pour garantir une haute disponibilité des bases de données Microsoft BizTalk Server en raison de certaines difficultés à maintenir la cohérence des transactions dans les bases de données BizTalk Server.  
>   
>  Pour plus d’informations sur la mise en miroir de base de données et transactions entre bases de données dans SQL Server, consultez [Transactions - groupes de disponibilité et de la mise en miroir de base de données](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring). Bases de données BizTalk Server doivent être installés sur un cluster de SQL Server pour garantir une haute disponibilité et d’envoi de journaux doit être utilisée à des fins de récupération d’urgence.  
>   
>  Pour plus d’informations sur l’envoi de journaux, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise en cluster des bases de données BizTalk Server](../technical-guides/clustering-the-biztalk-server-databases2.md)  
  
-   [Montée en charge des bases de données BizTalk Server](../technical-guides/scaling-out-the-biztalk-server-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la haute disponibilité](../technical-guides/planning-for-high-availability2.md)   
 [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)
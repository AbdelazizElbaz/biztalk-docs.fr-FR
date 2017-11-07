---
title: "Liste de vérification : Effectuer des vérifications de Maintenance mensuelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 588b74fa-6bf5-43ad-aa15-3595adde76d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f5e5d7d6c6732c203ac7a34308c546388206c3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="checklist-complete-monthly-maintenance-checks-in-biztalk-server"></a>Liste de vérification : Maintenance mensuelle complète vérifie dans BizTalk Server
Cette rubrique décrit les étapes nécessaires pour effectuer des vérifications de maintenance de la fiabilité, administration, sécurité et des performances de tous les mois un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  

## <a name="checklist"></a>Liste de vérification
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que la clé de secret principal est sauvegardée et disponibles sur le stockage hors connexion (vérification de la fiabilité).|[Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)|  
|Vérifiez que le basculement de tous les services de cluster a été testé (vérification de la fiabilité).|[Examen et test de la configuration du cluster SQL Server pour les scénarios de basculement](../technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|Assurez-vous que le service SSO est en cluster (vérification de la fiabilité).|[Mise en cluster du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md)|  
|Assurez-vous que les bases de données BizTalk Server sont en cluster sous services de SQL Server (vérification de la fiabilité).|[Mise en cluster des bases de données BizTalk Server](../technical-guides/clustering-the-biztalk-server-databases2.md)|  
|Assurez-vous qu’au moins deux serveurs BizTalk physiques font partie du groupe BizTalk (vérification de la fiabilité).|[Vous être assuré de plusieurs serveurs appartiennent à un groupe BizTalk](../technical-guides/maintaining-reliability.md#BKMK_BTSGrp)|  
|Déterminer si n’importe quel code instable est utilisé et si tel est le cas, utilisez des hôtes distincts (vérification de la fiabilité).|[Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|Effectuez un test fonctionnel de toutes les applications BizTalk nouveau (vérification de la fiabilité).|-   [Test d’une Application](../technical-guides/testing-an-application.md)<br />-   [Tâches de mise en lots pour le déploiement d’applications BizTalk](../core/staging-tasks-for-biztalk-application-deployment.md)|  
|Configurer et planifier des travaux de sauvegarde BizTalk Server (vérification de la fiabilité).|-   [Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)<br />-   [Comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md)|  
|Vérifiez que la version correcte d’un jeu d’assemblys est installée sur chaque ordinateur BizTalk (contrôle d’intégrité).|Utilisez le **vérificateur d’Assembly BizTalk et à distance GAC** outil (BTSAssemblyChecker.exe) pour vérifier les versions des assemblys déployés dans la base de données de gestion BizTalk et pour vérifier qu’ils sont inscrits correctement dans le GAC sur tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs. Vous pouvez utiliser cet outil pour vérifier que tous les assemblys contenant les artefacts d’une certaine application BizTalk sont installés sur tous les nœuds de BizTalk. L’outil est particulièrement utile en conjonction avec une stratégie de contrôle de version solide pour vérifier que la version correcte d’un jeu d’assemblys est installée sur chaque ordinateur BizTalk, en particulier lorsque l’approche de déploiement de côte à côte est utilisé. L’outil est disponible avec le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Support\Tools\x86\BTSAssemblyChecker.exe support d’installation.|  
|Déterminer s’il existe des inutiles BizTalk applications, les artefacts et configurations (vérification de l’administration).|-Supprimez tous les inutiles BizTalk applications, les artefacts et les configurations.<br />-Pour plus d’informations sur la suppression d’une application BizTalk ou un artefact à l’aide de l’outil de ligne de commande BTSTask consultez [commande RemoveApp](../core/removeapp-command.md).<br />-Pour plus d’informations sur la suppression d’un artefact à partir d’une application à l’aide de la console Administration de BizTalk Server ou l’outil de ligne de commande BTSTask, consultez [comment supprimer un artefact d’une Application](../core/how-to-remove-an-artifact-from-an-application.md).|  
|Vérifiez la console Administration de BizTalk Server pour toutes les modifications non approuvé (vérification de l’administration).|[Utilisation de la console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md)|  
|Vérifiez BTSNTSvc.exe.config pour toutes les modifications non approuvé (vérification de l’administration).|[Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)|  
|Vérifiez les clés de Registre liés à BizTalk Server pour toutes les modifications non approuvé (vérification de l’administration).|L’article 256986 de la Base de connaissances Microsoft [informations du Registre Windows pour les utilisateurs expérimentés](https://support.microsoft.com/kb/256986)|  
|Exécuter le Best Practices Analyzer pour BizTalk Server (vérification de l’administration).|[BizTalk Server Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=43382)|  
|Assurez-vous que les derniers service packs et mises à jour sont installés (vérification de l’administration et de sécurité).|[Mise à jour Microsoft](https://support.microsoft.com/help/12373/windows-update-faq)|  
|Assurez-vous que les artefacts pour différents partenaires commerciaux ne sont pas installés sur le même hôte (vérification de sécurité).|[Configuration des hôtes et des instances d’hôte](../technical-guides/configuring-hosts-and-host-instances.md)|  
|Assurez-vous que BizTalk Server utilise uniquement au niveau du domaine utilisateurs et groupes (vérification de sécurité).|[Groupes de domaine](../core/domain-groups.md)|  
|Vérifiez que la Configuration de sécurité MSDTC est activée (vérification de sécurité).|Consultez **définir les options de Configuration de la sécurité MSDTC appropriées** dans [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).|  
|Déterminer si l’intervalle d’actualisation du cache BizTalk Server doit être augmentée (vérification de performances).|[Comment ajuster l’intervalle d’actualisation du cache de configuration](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)|  
|Déterminer si les options de limitation de chaque ordinateur hôte doivent être ajustement (vérification de performances).|-Pour plus d’informations sur la limitation de l’hôte entrant et sortant, consultez [quelle est la limitation des hôtes ?](../core/what-is-host-throttling.md).<br />-Pour plus d’informations sur les déclencheurs, les actions et les stratégies de prévention de limitation du trafic entrant et sortant, consultez **stratégies d’atténuation, les actions et les déclencheurs de la condition de limitation** à [comment BizTalk Server met en œuvre Hôte de limitation](../core/how-biztalk-server-implements-host-throttling.md).|  
|Déterminer si le suivi inutile est activé, telles que l’orchestration, la forme et du moteur de règles d’entreprise (BRE) suivi d’événements (vérification de performances).|-   [Comment désactiver le suivi de](../technical-guides/how-to-disable-tracking.md)<br />-   [Planification pour le suivi](../technical-guides/planning-for-tracking.md)<br />-   [Meilleures pratiques pour le suivi](../technical-guides/planning-for-tracking.md#BKMK_TrackingBP)|  
|Déterminez si vous utilisez un hôte dédié pour le suivi de maintenance (vérification de performances).|[Configuration d’un hôte de suivi dédié](../technical-guides/configuring-a-dedicated-tracking-host.md)|  
|Vérifiez la taille de la base de données BizTalk Server pour une tendance haussière (vérification de performances).|-Pour plus d’informations sur le dimensionnement de la base de données de suivi, consultez [instructions dimensionnement de bases de données de suivi](../core/tracking-database-sizing-guidelines.md).<br />-Pour plus d’informations sur les bases de données MessageBox, BizTalkDTADb et BAMPrimaryImport de dimensionnement, consultez [identification des goulots d’étranglement de performances](../core/identifying-performance-bottlenecks.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Listes de contrôle pour la maintenance de routine](../technical-guides/routine-maintenance-checklists.md)

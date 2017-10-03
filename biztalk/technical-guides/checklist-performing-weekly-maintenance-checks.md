---
title: "Liste de vérification : Effectuer des vérifications de Maintenance hebdomadaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b13e43ba-4bac-4d4b-aaf8-46d60c0561bf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb754c0cfd7f153e4cefa3cd610ef1633ef1e073
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-weekly-maintenance-checks"></a>Liste de vérification : Effectuer des vérifications de Maintenance hebdomadaire
Cette rubrique décrit les étapes nécessaires pour effectuer des vérifications de maintenance de la fiabilité, administration, sécurité et des performances de toutes les semaines un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Assurez-vous que chaque hôte possède une instance en cours d’exécution au moins deux serveurs BizTalk physiques (vérification de la fiabilité).|[Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|Assurez-vous que chaque emplacement de réception est redondante (vérification de la fiabilité).|[Montée en puissance parallèle de l’hôte de réception](../technical-guides/scaling-out-receiving-hosts.md)|  
|Assurez-vous que le service SQL Server Agent est en cours d’exécution sur le serveur SQL server (vérification de l’administration).|-   [Comment : démarrer l’Agent SQL Server](http://go.microsoft.com/fwlink/p/?LinkId=154672) (http://go.microsoft.com/fwlink/p/?LinkId=154672).<br />-   [L’Agent SQL Server](http://go.microsoft.com/fwlink/p/?LinkId=106728) (http://go.microsoft.com/fwlink/p/?LinkId=106728).|  
|Assurez-vous que tous les travaux de SQL Server associés à BizTalk Server fonctionnent correctement (vérification de l’administration).|[Analyse des travaux de l’Agent SQL Server](../technical-guides/monitoring-sql-server-agent-jobs.md)<br /><br /> Si les travaux de l’Agent SQL Server ne sont pas en cours d’exécution, les performances du système seront dégradent. Pour plus d’informations sur l’Agent SQL Server des travaux BizTalk Server fournit pour vous aider à gérer les bases de données BizTalk Server, consultez [Structure de base de données et les travaux](http://go.microsoft.com/fwlink/p/?LinkID=153451) (http://go.microsoft.com/fwlink/p/?LinkID=153451).|  
|Assurez-vous que les travaux de SQL Server responsables de la sauvegarde des bases de données BizTalk Server sont exécutent normalement (vérification de l’administration).|-   [Comment configurer le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkID=153813) (http://go.microsoft.com/fwlink/p/?LinkID=153813)<br />-   [Comment planifier le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkId=154674) (http://go.microsoft.com/fwlink/p/?LinkId=154674)|  
|Assurez-vous que les dernières mises à jour de sécurité sont installés (vérification de sécurité).|Site Microsoft Update à l’adresse [http://update.microsoft.com/microsoftupdate/v6/default.aspx](http://update.microsoft.com/microsoftupdate/v6/default.aspx)|  
|Analyser les performances hebdomadaire surveillance des journaux par rapport à la ligne de base et les seuils (vérification de performances).|-   [À l’aide de l’analyse des performances de l’outil de journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)<br />-   [Résolution des problèmes de performances Issues3](../technical-guides/troubleshooting-performance-issues3.md)|  
|Assurez-vous que le système ne connaît pas la croissance automatique fréquente des bases de données BizTalk Server (vérification de performances).|-   [Définition des paramètres de croissance automatique pour les bases de données](../technical-guides/defining-auto-growth-settings-for-databases.md)<br />-   [Instructions de dimensionnement de la base de données de suivi](http://go.microsoft.com/fwlink/p/?LinkId=154677) (http://go.microsoft.com/fwlink/p/?LinkId=154677).<br />-   [Identification des goulots d’étranglement au niveau de la base de données](http://go.microsoft.com/fwlink/p/?LinkId=154678) (http://go.microsoft.com/fwlink/p/?LinkId=154678).<br />-   [L’initialisation des fichiers de base de données](http://go.microsoft.com/fwlink/p/?LinkID=101579) (http://go.microsoft.com/fwlink/p/?LinkID=101579).<br />-   [Procédures de Maintenance SQL Server](~/technical-guides/checklist-configuring-sql-server.md)|  
|Exécutez le Générateur de profils SQL Server au cours d’une charge élevée pour vérifier les longs temps de réponse et l’utilisation importante des ressources (vérification de performances).|[À l’aide du Générateur de profils SQL Server](http://go.microsoft.com/fwlink/p/?LinkID=106720) (http://go.microsoft.com/fwlink/p/?LinkID=106720).|  
|Assurez-vous que le traitement par lot des messages pour tous les adaptateurs est approprié pour la consommation des ressources ou la latence (vérification de performances).|-   [Configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md)<br />-   [Comment concevoir un adaptateur Performant](http://go.microsoft.com/fwlink/p/?LinkId=154679) (http://go.microsoft.com/fwlink/p/?LinkId=154679).|  
|Assurez-vous que le seuil de messages volumineux est approprié pour la consommation des ressources (vérification de performances).|[Comment BizTalk Server traite les Messages volumineux](http://go.microsoft.com/fwlink/p/p/?LinkId=154680) (http://go.microsoft.com/fwlink/p/p/?LinkId=154680).|  
|Archiver les fichiers de sauvegarde et de spécifier les ordinateurs appropriés pour la sauvegarde|Pour éviter de perdre des données, vous devez spécifier un ordinateur pour la sauvegarde est différente de l’ordinateur avec les données d’origine et pour \<chemin d’accès de destination > vous devez spécifier un ordinateur pour stocker les journaux de base de données qui est différent de la ordinateur sur lequel les journaux de base de données d’origine.<br /><br /> Pour plus d’informations sur les meilleures pratiques pour la sauvegarde, consultez [meilleures pratiques de sauvegarde et restauration des bases de données de](http://go.microsoft.com/fwlink/p/p/?LinkID=151391) (http://go.microsoft.com/fwlink/p/p/?LinkID=151391).|  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de surveillance de routines](../technical-guides/routine-monitoring-tasks.md)
---
title: "Archivage et la purge de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- BizTalk Server, maintaining
- archiving [Tracking database]
- purging
- Tracking database, maintaining
- Tracking database, archiving
- maintaining, Tracking database
- maintaining, BizTalk Server
ms.assetid: 7014cf31-86e8-4829-8055-056442329009
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8fc75f5218ec7a189d28c7120cf23a3047c1752
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="archiving-and-purging-the-biztalk-tracking-database"></a>Archivage et purge de la base de données des suivis BizTalk
BizTalk Server traitant de plus en plus de données sur votre système, la taille de la base de données des suivis BizTalk (BizTalkDTADb) ne cesse d'augmenter. Cette croissance non contrôlée affecte la performance du système et peut générer des erreurs dans le service TDDS (Tracking Data Decode Service). Outre les données de suivi générales, les messages suivis peuvent également s'accumuler dans la base de données MessageBox, affectant ainsi les performances du disque.  
  
 Alors que les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] incluaient des exemples de script pour l'archivage des messages suivis et la purge de la base de données des suivis BizTalk, dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ces deux processus sont effectués automatiquement via le travail DTA Purge and Archive. Grâce à l'archivage et à la purge des données à partir de la base de données des suivis BizTalk, vous pouvez maintenir un bon fonctionnement du système tout en conservant vos données de suivi archivées pour une utilisation ultérieure. Les archives de la base de données des suivis BizTalk ayant tendance à s'accumuler et à saturer l'espace disque, il est recommandé de les transférer régulièrement sur un périphérique de stockage secondaire.  
  
 Lors de la purge des données de la base de données des suivis BizTalk, le travail de purge et d'archivage DTA implique l'élimination de divers types d'informations de suivis, comme les informations d'instance de service et de message, les informations d'événement d'orchestration et les données de suivi du moteur des règles.  
  
 L'âge d'un enregistrement de données de suivis est basé sur la date et l'heure auxquelles les données ont été placées dans la base de données des suivis BizTalk. Le travail de purge et d'archivage DTA utilise l'horodatage pour vérifier de manière continue si l'enregistrement est antérieur à l'intervalle de données actives. Après chaque période de données actives, la base de données des suivis BizTalk est archivée et un nouveau fichier d'archive est créé. À chaque intervalle de travail de SQL Server Agent spécifié par la planification des travaux, toutes les données de suivi terminées antérieures à la période de données actives sont purgées.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le concept de purge normale et de purge complète. La purge normale permet d'éliminer les instances terminées, alors que la purge complète permet de purger les instances non achevées.  
  
 **Purge normale**  
  
 Pour le travail de purge et d'archivage DTA, la somme du nombre d'heures et du nombre de jours d'activité est égale aux données de la fenêtre active que vous souhaitez conserver dans votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les données associées à une instance terminée et antérieures à cet intervalle de données actives sont purgées. Par défaut, le travail de purge et d'archivage DTA n'est pas activé. Vous devez d'abord configurer le travail, puis l'activer.  
  
 Par exemple, vous pouvez configurer le travail DTA Purge and Archive pour exécuter toutes les 20 minutes et définir les paramètres LiveHours = 1 et nombre = 0. La première fois que ce travail de l’Agent SQL Server s’exécute (T0), il effectue une sauvegarde de la base de données de suivi en créant une archive et une entrée est enregistrée dans la base de données avec cet horodatage. L'archivage doit avoir réussi pour pouvoir purger les données de suivi. Si l'archivage a réussi, toutes les données associées aux instances qui se sont terminées il y a plus d'une heure sont purgées. À chaque exécution du travail, les données terminées depuis plus d'une heure sont supprimées. Lors de la troisième exécution (après une heure), une nouvelle archive est créée contenant les données de toutes les instances insérées dans la base de données des suivis au cours de la dernière heure.  
  
 Voici comment configurer l'étape d'archivage et de purge du travail DTA Purge and Archive correspondant à l'exemple ci-dessus :  
  
```  
exec dtasp_BackupAndPurgeTrackingDatabase  
1, --@nLiveHours 1,   
0, --@nLiveDays   
1, --@nHardDeleteDays   
‘\\server\backup’, --@nvcFolder   
null, --@nvcValidatingServer   
0 --@fForceBackup Soft purge process  
```  
  
 L'horodatage de la dernière sauvegarde est stocké dans la base de données des suivis BizTalk et permet de garantir que les données sont purgées uniquement si elles sont contenues dans l'archive précédente. Pour plus de fiabilité, les archivages sont effectués environ toutes les 10 minutes. La figure ci-dessous, basée sur l'exemple précédent, illustre le processus de purge normale. Notez que les tâches d'archivage et de purge ne sont pas nécessairement simultanées.  
  
 **Processus de purge**  
  
 ![Processus de purge](../core/media/archivingandpurging.gif "archivingandpurging")  
  
 **Purge complète**  
  
 Seules les données associées à des instances terminées étant supprimées, si un nombre important d'instances de boucle s'exécutent indéfiniment, votre base de données risque d'augmenter de taille et d'être impossible à purger. La date de purge complète permet de purger toutes les informations antérieures à l'intervalle spécifié, à l'exception des informations indiquant l'existence d'un service. Vous définissez la purge dur à l’aide de la  **@nHardDeleteDays**  paramètre Purge et d’archivage étape dans le travail de Purge et d’archivage DTA. Le paramètre de purge complète doit toujours être supérieur à votre paramètre de purge normale. En d’autres termes,  **@nHardDeleteDays**  doit être supérieure à la somme des  **@nLiveHours**  et  **@nLiveDays** .  
  
 L'archivage et la purge incluent les fonctions décrites dans le tableau suivant :  
  
|Fonctionnalité| Description|  
|-------------|-----------------|  
|Purge complète|Vous permet de configurer un intervalle de temps pour purger les informations relatives aux instances non achevées antérieures à une date spécifiée.|  
|Copie des messages suivis dans la base de données des suivis|À l'aide de l'option CopyTrackedMessageToDTA, vous pouvez copier directement les messages suivis à partir des serveurs MessageBox vers votre base de données des suivis BizTalk. Cette opération est obligatoire pour pouvoir purger les données avec le travail DTA Purge and Archive.|  
|Validation des archives|Vous permet de configurer en option un serveur de base de données secondaire pour valider les archives à mesure de leur création.|  
|Prise en charge du suivi pour plusieurs versions de base de données des suivis BizTalk|Vous permet d'utiliser la prise en charge du suivi avec les archives des bases de données de [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].|  
|Réduction des données de suivi|Réduit de manière substantielle la quantité de données de suivi stockées sans réduire les informations de suivi générées. Ceci permet de limiter la croissance de la base de données des suivis.|  
|Opérations de suivi plus rapides, optimisation significative des schémas de base de données|Permet d'utiliser des tâches de suivi pour rechercher des messages et des instances de service dans des bases de données volumineuses. Cette fonction a été considérablement améliorée.|  
  
> [!NOTE]
>  Si vous rencontrez des problèmes de performances qui sont momentanément résolus par une purge de la base de données de suivi BizTalk, et que vous souhaitez configurer BizTalk de sorte que les informations de suivi ne soient plus collectées, vous pouvez envisager de désactiver le suivi global. Pour plus d'informations sur la désactivation du suivi global, voir la rubrique Désactivation du suivi global.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Liste de vérification : Archivage et la purge de la base de données de suivi de BizTalk](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [Comment configurer le rôle BTS_BACKUP_USERS pour l’archivage et la purge des données de la base de données de suivi de BizTalk](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [Configuration du travail de purge et d’archivage DTA](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [Purge des données de la base de données de suivi de BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [Purge manuelle des données à partir de la base de données de suivi BizTalk](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [Comment activer la Validation de l’archivage automatique](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [Comment copier des Messages suivis dans la base de données de suivi de BizTalk](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [Amélioration des performances du processus d’archivage et de purge](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [Comment désactiver le suivi Global](../core/how-to-turn-off-global-tracking.md)
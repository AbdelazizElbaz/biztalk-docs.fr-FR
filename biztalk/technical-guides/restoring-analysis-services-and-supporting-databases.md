---
title: "Restauration des Services d’analyse et la prise en charge des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da16bde7b69071b71b794c4c46407feab3ef4512
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-analysis-services-and-supporting-databases"></a>Restauration des Services d’analyse et la prise en charge des bases de données
Il existe deux [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données Analysis Services qui doivent être restaurées dans un scénario de récupération d’urgence :  
  
-   Analyse BAM (BAMAnalysis)  
  
-   Serveur d’analyse de suivi des (suivis BizTalkAnalysisdb)  
  
 L’analyse BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données peuvent être sauvegardées dans le cadre de la tâche de sauvegarde de BizTalk Server si BAM est activé mais pas configuré.  
  
> [!NOTE]  
>  La base de données d’importation principale BAM est toujours sauvegardé dans le cadre de la tâche de sauvegarde de BizTalk Server, car il participe aux transactions DTC.  
  
 Les bases de données BAM suivantes feront partie de la tâche de sauvegarde de BizTalk Server si BAM est activé mais pas configuré :  
  
-   BAMStarSchema  
  
-   BAMArchive  
  
 Suivez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) restaurer ces bases de données.  
  
 **Sinon,**  
 **Si l’analyse BAM est activé et est également configuré avec BM.exe, l’ensemble approprié de bases de données BAM doit être restauré ensemble en tant qu’ensemble.** Pour vous assurer qu’un ensemble complet des données archivées est récupéré, la base de données des archives BAM est sauvegardé après que la partition est copiée dans l’Archive de l’analyse BAM, mais avant que la partition est supprimée de la base de données d’importation principale BAM. Cette opération est effectuée en modifiant le package SSIS de maintenance de données pour chaque activité en insérant une étape pour sauvegarder la base de données des archives BAM avant la dernière étape « Fin de l’archivage ».  
  
 La procédure de restauration de bases de données BAM est : si la base de données d’importation principale BAM est restaurée avec la dernière date de la sauvegarde de x, restaurez les copies des archives BAM et des schémas en étoile BAM bases de données qui correspondent à la date la plus récente lorsque le package SSIS de maintenance de données a été exécuter avant la date de x.  
  
 Après que l’ensemble de bases de données BAM correct est identifié, restaurer le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les bases de données Analysis Services à l’aide de procédures standard comme indiqué dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne pour la restauration [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Bases de données analysis Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)
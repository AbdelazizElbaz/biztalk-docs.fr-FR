---
title: "Comment résoudre les Instances d’activité incomplètes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, incomplete [BAM]
- restoring, BAM
- Primary Import database [BAM], incomplete instances
- restoring [BAM], Primary Import database
- Primary Import database [BAM], restoring
- BAM, restoring
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81df9ee8b004a2dbd4a672eecb4f34894421a432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resolve-incomplete-activity-instances"></a>Résolution d'instances d'activités incomplètes
BAM stocke des données pour les instances d’activité incomplètes dans une spéciale *instance active* table dans la base de données.  
  
 Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde de la base de données BAMPrimaryImport et sont terminés après la sauvegarde, ils sont conservés dans une table des instances actives. En effet, après la restauration de la base de données BAMPrimaryImport, les enregistrements terminés pour ces instances sont perdus.  
  
 Si les enregistrements de la table des instances actives n'empêchent pas le fonctionnement correct de l'analyse BAM, il est recommandé de marquer ces enregistrements comme « terminés », puis de les déplacer hors de la table des instances actives.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-generate-a-list-of-incomplete-activityids-for-an-activity"></a>Pour générer la liste des ID d'activité (ActivityID) incomplète pour une activité  
  
1.  Exécutez la requête suivante sur la base de données BAMPrimaryImport :  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  Si les données des systèmes externes indiquent que l'instance d'activité est terminée, exécutez la requête suivante pour terminer manuellement l'instance :  
  
    ```  
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    ```  
  
> [!NOTE]
>  Vous pouvez suivre la même procédure pour exécuter une activité de continuation en remplaçant ActivityID par ContinuationID.  
  
> [!NOTE]
>  Si la trace principale inclut des traces de continuation actives, elle reste active jusqu'à la fin des traces de continuation.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)
---
title: "Résoudre des instances d’activité incomplètes | Documents Microsoft"
description: "Instances d’activité BAM restent actifs après avoir sauvegardé la base de données dans BizTalk Server"
ms.custom: 
ms.date: 01/17/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 616ba096062da7ede8d78122e5a6faaca2befdc4
ms.sourcegitcommit: 20d33d8b74bf129a8d1a506ac4a1ad960184966d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="resolve-incomplete-bam-activity-instances---biztalk-server"></a>Résoudre des instances d’activité BAM incomplets - BizTalk Server
BAM stocke des données pour les instances d’activité incomplètes dans une spéciale *instance active* table dans la base de données.  
  
 Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde de la base de données BAMPrimaryImport et sont terminés après la sauvegarde, ils sont conservés dans une table des instances actives. En effet, après la restauration de la base de données BAMPrimaryImport, les enregistrements terminés pour ces instances sont perdus.  
  
 Si les enregistrements de la table des instances actives n'empêchent pas le fonctionnement correct de l'analyse BAM, il est recommandé de marquer ces enregistrements comme « terminés », puis de les déplacer hors de la table des instances actives.  
  
## <a name="prerequisites"></a>Configuration requise  
Connectez-vous en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="create-a-list-of-incomplete-activityids"></a>Créer une liste d’ActivityId incomplète 
  
1.  Exécutez la requête suivante sur la base de données BAMPrimaryImport :  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  Si les données des systèmes externes indiquent que l'instance d'activité est terminée, exécutez la requête suivante pour terminer manuellement l'instance :  
  
    ```  
    begin transaction
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    commit transaction
    ```  
  
> [!NOTE]
>  Vous pouvez suivre la même procédure pour terminer une activité de continuation en remplaçant `ActivityID` avec `ContinuationID`.  
> 
>  Si la trace principale inclut des traces de continuation actives, elle reste active jusqu'à la fin des traces de continuation.  

## <a name="remove-incomplete-instances"></a>Supprimer des instances incomplètes
Vous pouvez également supprimer des instances d’activité incomplètes à partir de la base de données à l’aide d’un script SQL personnalisé. Consultez [supprimer des instances d’activité incomplètes](how-to-remove-incomplete-activity-instances.md) pour obtenir un exemple.

## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de l’analyse BAM](../core/backing-up-and-restoring-bam.md)

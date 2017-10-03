---
title: "Le marquage des Transactions en cours comme étant terminé dans l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, data recovery
- data recovery, BAM
- BAM, data loss
- data loss, BAM
ms.assetid: 8f734953-483a-481a-9ded-b48923859199
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 508001fcc1023acfd54b7d28bea7f246cb6a1a2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="marking-in-progress-transactions-as-complete-in-bam"></a>Marquage des transactions en cours comme étant terminées dans l'analyse BAM
L'analyse BAM (Business Activity Monitoring) conserve les données relatives aux instances de suivi incomplètes dans une table des instances actives spéciale. Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde mais terminés après la sauvegarde, ils sont conservés dans la table des instances actives. Si ceux-ci n'empêchent pas le fonctionnement correct du système, vous pouvez marquer manuellement ces enregistrements comme terminés afin qu'ils puissent être déplacés hors de la table des instances actives.  
  
 Pour générer la liste des ID d'activité (ActivityID) incomplète pour une activité donnée, vous devez émettre la requête suivante sur la base de données d'importation principale BAM :  
  
```  
Select ActivityID from bam_<ActivityName> where IsComplete = 0  
```  
  
 Si les données des systèmes externes indiquent que l'instance d'activité est terminée, vous pouvez utiliser la requête suivante pour terminer manuellement l'instance :  
  
```  
exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de la perte de données](../core/resolving-data-loss.md)
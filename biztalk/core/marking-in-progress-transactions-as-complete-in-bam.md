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
# <a name="marking-in-progress-transactions-as-complete-in-bam"></a><span data-ttu-id="18524-102">Marquage des transactions en cours comme étant terminées dans l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="18524-102">Marking In-Progress Transactions as Complete in BAM</span></span>
<span data-ttu-id="18524-103">L'analyse BAM (Business Activity Monitoring) conserve les données relatives aux instances de suivi incomplètes dans une table des instances actives spéciale.</span><span class="sxs-lookup"><span data-stu-id="18524-103">Business Activity Monitoring (BAM) keeps data for incomplete trace instances in a special active instance table.</span></span> <span data-ttu-id="18524-104">Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde mais terminés après la sauvegarde, ils sont conservés dans la table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="18524-104">If some instance records were started before the last backup but completed after the backup, those records will remain in the active instance table.</span></span> <span data-ttu-id="18524-105">Si ceux-ci n'empêchent pas le fonctionnement correct du système, vous pouvez marquer manuellement ces enregistrements comme terminés afin qu'ils puissent être déplacés hors de la table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="18524-105">Although this does not prevent the system from functioning, you can manually mark these records as completed so that they can be moved out of the active instance table.</span></span>  
  
 <span data-ttu-id="18524-106">Pour générer la liste des ID d'activité (ActivityID) incomplète pour une activité donnée, vous devez émettre la requête suivante sur la base de données d'importation principale BAM :</span><span class="sxs-lookup"><span data-stu-id="18524-106">A list of incomplete ActivityIDs for a given activity can be determined by issuing the following query against the BAM Primary Import database:</span></span>  
  
```  
Select ActivityID from bam_<ActivityName> where IsComplete = 0  
```  
  
 <span data-ttu-id="18524-107">Si les données des systèmes externes indiquent que l'instance d'activité est terminée, vous pouvez utiliser la requête suivante pour terminer manuellement l'instance :</span><span class="sxs-lookup"><span data-stu-id="18524-107">If data from external systems indicates that the activity instance is complete, you can use the following query to manually complete the instance:</span></span>  
  
```  
exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
```  
  
## <a name="see-also"></a><span data-ttu-id="18524-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18524-108">See Also</span></span>  
 [<span data-ttu-id="18524-109">Résolution de la perte de données</span><span class="sxs-lookup"><span data-stu-id="18524-109">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)
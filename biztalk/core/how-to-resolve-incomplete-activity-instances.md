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
# <a name="how-to-resolve-incomplete-activity-instances"></a><span data-ttu-id="e9d84-102">Résolution d'instances d'activités incomplètes</span><span class="sxs-lookup"><span data-stu-id="e9d84-102">How to Resolve Incomplete Activity Instances</span></span>
<span data-ttu-id="e9d84-103">BAM stocke des données pour les instances d’activité incomplètes dans une spéciale *instance active* table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="e9d84-103">BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="e9d84-104">Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde de la base de données BAMPrimaryImport et sont terminés après la sauvegarde, ils sont conservés dans une table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="e9d84-104">If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table.</span></span> <span data-ttu-id="e9d84-105">En effet, après la restauration de la base de données BAMPrimaryImport, les enregistrements terminés pour ces instances sont perdus.</span><span class="sxs-lookup"><span data-stu-id="e9d84-105">This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.</span></span>  
  
 <span data-ttu-id="e9d84-106">Si les enregistrements de la table des instances actives n'empêchent pas le fonctionnement correct de l'analyse BAM, il est recommandé de marquer ces enregistrements comme « terminés », puis de les déplacer hors de la table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="e9d84-106">Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9d84-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e9d84-107">Prerequisites</span></span>  
 <span data-ttu-id="e9d84-108">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e9d84-108">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-generate-a-list-of-incomplete-activityids-for-an-activity"></a><span data-ttu-id="e9d84-109">Pour générer la liste des ID d'activité (ActivityID) incomplète pour une activité</span><span class="sxs-lookup"><span data-stu-id="e9d84-109">To generate a list of incomplete ActivityIDs for an activity</span></span>  
  
1.  <span data-ttu-id="e9d84-110">Exécutez la requête suivante sur la base de données BAMPrimaryImport :</span><span class="sxs-lookup"><span data-stu-id="e9d84-110">Run the following query against the BAMPrimaryImport database:</span></span>  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  <span data-ttu-id="e9d84-111">Si les données des systèmes externes indiquent que l'instance d'activité est terminée, exécutez la requête suivante pour terminer manuellement l'instance :</span><span class="sxs-lookup"><span data-stu-id="e9d84-111">If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:</span></span>  
  
    ```  
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="e9d84-112">Vous pouvez suivre la même procédure pour exécuter une activité de continuation en remplaçant ActivityID par ContinuationID.</span><span class="sxs-lookup"><span data-stu-id="e9d84-112">You can follow the same process to complete a continuation activity by replacing ActivityID with ContinuationID.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d84-113">Si la trace principale inclut des traces de continuation actives, elle reste active jusqu'à la fin des traces de continuation.</span><span class="sxs-lookup"><span data-stu-id="e9d84-113">If the main trace has any active continuation traces, it remains active until the continuation traces are completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d84-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9d84-114">See Also</span></span>  
 [<span data-ttu-id="e9d84-115">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="e9d84-115">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)
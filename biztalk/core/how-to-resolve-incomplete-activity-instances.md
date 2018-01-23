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
# <a name="resolve-incomplete-bam-activity-instances---biztalk-server"></a><span data-ttu-id="fc469-103">Résoudre des instances d’activité BAM incomplets - BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fc469-103">Resolve incomplete BAM activity instances - BizTalk Server</span></span>
<span data-ttu-id="fc469-104">BAM stocke des données pour les instances d’activité incomplètes dans une spéciale *instance active* table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="fc469-104">BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="fc469-105">Si certains enregistrements d'instance ont été démarrés avant la dernière sauvegarde de la base de données BAMPrimaryImport et sont terminés après la sauvegarde, ils sont conservés dans une table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="fc469-105">If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table.</span></span> <span data-ttu-id="fc469-106">En effet, après la restauration de la base de données BAMPrimaryImport, les enregistrements terminés pour ces instances sont perdus.</span><span class="sxs-lookup"><span data-stu-id="fc469-106">This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.</span></span>  
  
 <span data-ttu-id="fc469-107">Si les enregistrements de la table des instances actives n'empêchent pas le fonctionnement correct de l'analyse BAM, il est recommandé de marquer ces enregistrements comme « terminés », puis de les déplacer hors de la table des instances actives.</span><span class="sxs-lookup"><span data-stu-id="fc469-107">Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc469-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc469-108">Prerequisites</span></span>  
<span data-ttu-id="fc469-109">Connectez-vous en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fc469-109">Sign in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="create-a-list-of-incomplete-activityids"></a><span data-ttu-id="fc469-110">Créer une liste d’ActivityId incomplète</span><span class="sxs-lookup"><span data-stu-id="fc469-110">Create a list of incomplete ActivityIDs</span></span> 
  
1.  <span data-ttu-id="fc469-111">Exécutez la requête suivante sur la base de données BAMPrimaryImport :</span><span class="sxs-lookup"><span data-stu-id="fc469-111">Run the following query against the BAMPrimaryImport database:</span></span>  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  <span data-ttu-id="fc469-112">Si les données des systèmes externes indiquent que l'instance d'activité est terminée, exécutez la requête suivante pour terminer manuellement l'instance :</span><span class="sxs-lookup"><span data-stu-id="fc469-112">If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:</span></span>  
  
    ```  
    begin transaction
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    commit transaction
    ```  
  
> [!NOTE]
>  <span data-ttu-id="fc469-113">Vous pouvez suivre la même procédure pour terminer une activité de continuation en remplaçant `ActivityID` avec `ContinuationID`.</span><span class="sxs-lookup"><span data-stu-id="fc469-113">You can follow the same process to complete a continuation activity by replacing `ActivityID` with `ContinuationID`.</span></span>  
> 
>  <span data-ttu-id="fc469-114">Si la trace principale inclut des traces de continuation actives, elle reste active jusqu'à la fin des traces de continuation.</span><span class="sxs-lookup"><span data-stu-id="fc469-114">If the main trace has any active continuation traces, it remains active until the continuation traces are completed.</span></span>  

## <a name="remove-incomplete-instances"></a><span data-ttu-id="fc469-115">Supprimer des instances incomplètes</span><span class="sxs-lookup"><span data-stu-id="fc469-115">Remove incomplete instances</span></span>
<span data-ttu-id="fc469-116">Vous pouvez également supprimer des instances d’activité incomplètes à partir de la base de données à l’aide d’un script SQL personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fc469-116">You can also remove incomplete activity instances from the BAMPrimaryImport database using a custom SQL script.</span></span> <span data-ttu-id="fc469-117">Consultez [supprimer des instances d’activité incomplètes](how-to-remove-incomplete-activity-instances.md) pour obtenir un exemple.</span><span class="sxs-lookup"><span data-stu-id="fc469-117">See [Remove incomplete activity instances](how-to-remove-incomplete-activity-instances.md) for a sample.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc469-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc469-118">See Also</span></span>  
 [<span data-ttu-id="fc469-119">Sauvegarde et restauration de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="fc469-119">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)

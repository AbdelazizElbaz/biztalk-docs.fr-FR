---
title: "Comment sauvegarder et restaurer des travaux de l’Agent SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82fc5a5-5ea5-476c-bed1-c5d41a50e673
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 253055f9a45dfdb9864d4d5202661e750d28b1b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-agent-jobs"></a><span data-ttu-id="d53fe-102">Sauvegarde et restauration des travaux de l'Agent SQL</span><span class="sxs-lookup"><span data-stu-id="d53fe-102">How to Back Up and Restore SQL Agent Jobs</span></span>
<span data-ttu-id="d53fe-103">Cette rubrique décrit la sauvegarde et la restauration des travaux de l'Agent SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d53fe-103">This topic describes how to back up and restore SQL Server Agent Jobs.</span></span> <span data-ttu-id="d53fe-104">Vous devez sauvegarder vos travaux SQL après les avoir configurés.</span><span class="sxs-lookup"><span data-stu-id="d53fe-104">You should back up your SQL jobs after you configure them.</span></span>  
  
## <a name="biztalk-server-jobs"></a><span data-ttu-id="d53fe-105">Travaux BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d53fe-105">BizTalk Server Jobs</span></span>  
 <span data-ttu-id="d53fe-106">Les travaux d'Agent SQL Server suivants sont associés à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d53fe-106">The following SQL Server Agent jobs are associated with BizTalk Server.</span></span> <span data-ttu-id="d53fe-107">Les travaux installés sur chaque serveur sont différentes selon les fonctionnalités qui sont installées et configurées.</span><span class="sxs-lookup"><span data-stu-id="d53fe-107">The jobs installed on each server are different depending on which features are installed and configured.</span></span> <span data-ttu-id="d53fe-108">La plupart de ces travaux sont créés lors de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d53fe-108">Most of these jobs are created during BizTalk Server setup.</span></span> <span data-ttu-id="d53fe-109">Plusieurs d'entre eux sont créés lors de la configuration de l'envoi de journaux.</span><span class="sxs-lookup"><span data-stu-id="d53fe-109">Several are created when configuring log shipping.</span></span>  
  
-   <span data-ttu-id="d53fe-110">Backup BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="d53fe-110">Backup BizTalk Server (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="d53fe-111">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-111">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span></span>  
  
-   <span data-ttu-id="d53fe-112">DTA Purge and Archive (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="d53fe-112">DTA Purge and Archive (BizTalkDTADb)</span></span>  
  
-   <span data-ttu-id="d53fe-113">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-113">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-114">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-114">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-115">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-115">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-116">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-116">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-117">MessageBox_UpdateStats_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-117">MessageBox_UpdateStats_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-118">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-118">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-119">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-119">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-120">Rules_Database_Cleanup_BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-120">Rules_Database_Cleanup_BizTalkRuleEngineDb</span></span>  
  
-   <span data-ttu-id="d53fe-121">TrackedMessages_Copy_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="d53fe-121">TrackedMessages_Copy_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="d53fe-122">Envoi de journaux de BizTalk Server - Obtenir l'historique des sauvegardes</span><span class="sxs-lookup"><span data-stu-id="d53fe-122">BTS Log Shipping Get Backup History</span></span>  
  
-   <span data-ttu-id="d53fe-123">Envoi de journaux de BizTalk Server - Restaurer la base de données</span><span class="sxs-lookup"><span data-stu-id="d53fe-123">BTS Log Shipping Restore Database</span></span>  
  
-   <span data-ttu-id="d53fe-124">Envoi de journaux de BizTalk Server - Restaurer à la marque</span><span class="sxs-lookup"><span data-stu-id="d53fe-124">BTS Log Shipping Restore To Mark</span></span>  
  
## <a name="back-up-a-job-using-a-script"></a><span data-ttu-id="d53fe-125">Sauvegarder un travail à l’aide d’un script</span><span class="sxs-lookup"><span data-stu-id="d53fe-125">Back up a job using a script</span></span>  
  
1.  <span data-ttu-id="d53fe-126">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="d53fe-126">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="d53fe-127">Développez **Agent SQL Server**, puis **Travaux**.</span><span class="sxs-lookup"><span data-stu-id="d53fe-127">Expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="d53fe-128">Avec le bouton droit de la tâche que vous souhaitez créer un script de sauvegarde, puis **tâche de Script en tant que**.</span><span class="sxs-lookup"><span data-stu-id="d53fe-128">Right-click the job you want to create a backup script for, and then select **Script Job as**.</span></span>  
  
4.  <span data-ttu-id="d53fe-129">Sélectionnez **CREATE To** ou **DROP To**, puis sélectionnez **nouvelle fenêtre d’éditeur de requête**, **fichier**, ou **Presse-papiers** Pour sélectionner une destination pour le script.</span><span class="sxs-lookup"><span data-stu-id="d53fe-129">Select **CREATE To** or **DROP To**, then select **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script.</span></span> <span data-ttu-id="d53fe-130">En règle générale, la destination est un fichier avec un **.sql** extension.</span><span class="sxs-lookup"><span data-stu-id="d53fe-130">Typically, the destination is a file with a **.sql** extension.</span></span>  
  
5.  <span data-ttu-id="d53fe-131">Répétez cette procédure depuis l'étape 3 pour chaque travail pour lequel créer un script.</span><span class="sxs-lookup"><span data-stu-id="d53fe-131">Repeat this procedure from Step 3 for each job you want to script.</span></span> <span data-ttu-id="d53fe-132">Consultez la liste des travaux liés à BizTalk Server pour identifier ceux pour lesquels créer un script.</span><span class="sxs-lookup"><span data-stu-id="d53fe-132">Refer to the list of BizTalk Server related jobs to determine which jobs you need to script.</span></span>  
  
     <span data-ttu-id="d53fe-133">Au minimum, vous devez sauvegarder le **sauvegarde de BizTalk Server (BizTalkMgmtDb)** de la tâche après sa configuration.</span><span class="sxs-lookup"><span data-stu-id="d53fe-133">At a minimum, you should back up the **Backup BizTalk Server (BizTalkMgmtDb)** job after it is configured.</span></span>  
  
## <a name="restore-a-job-from-a-script"></a><span data-ttu-id="d53fe-134">Restaurer un travail à partir d’un script</span><span class="sxs-lookup"><span data-stu-id="d53fe-134">Restore a job from a script</span></span>  
  
1.  <span data-ttu-id="d53fe-135">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="d53fe-135">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="d53fe-136">Sur le **fichier** menu, **ouvrir** le fichier contenant le travail sous forme de script.</span><span class="sxs-lookup"><span data-stu-id="d53fe-136">On the **File** menu, **Open** the file containing the scripted job.</span></span>  
  
3.  <span data-ttu-id="d53fe-137">Exécutez le script pour créer le travail.</span><span class="sxs-lookup"><span data-stu-id="d53fe-137">Execute the script to create the job.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d53fe-138">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d53fe-138">Next Steps</span></span>  
 [<span data-ttu-id="d53fe-139">Comment sauvegarder et restaurer les connexions SQL Server</span><span class="sxs-lookup"><span data-stu-id="d53fe-139">How to Back Up and Restore SQL Server Logins</span></span>](../core/how-to-back-up-and-restore-sql-server-logins.md)
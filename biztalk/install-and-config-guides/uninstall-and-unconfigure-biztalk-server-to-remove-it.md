---
title: "Désinstallez et annulez la configuration de BizTalk Server pour le supprimer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ea8757-ca49-421b-bf7b-89344201398a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 704c1f54a01ceb4c4b7b4cd80ad2df6fc34faa68
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="uninstall-and-unconfigure-biztalk-server-to-remove-it"></a><span data-ttu-id="7961a-102">Désinstallation et annulation de la configuration de BizTalk Server pour le supprimer</span><span class="sxs-lookup"><span data-stu-id="7961a-102">Uninstall and unconfigure BizTalk Server to remove it</span></span>
<span data-ttu-id="7961a-103">Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et annulez sa configuration.</span><span class="sxs-lookup"><span data-stu-id="7961a-103">Uninstall and unconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> 
  
##  <a name="BKMK_BeforeYouBegin"></a> <span data-ttu-id="7961a-104">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7961a-104">Before You Begin</span></span>  
  
-   <span data-ttu-id="7961a-105">Avant la désinstallation, vous devez annuler la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7961a-105">Before you uninstall, you must un-configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7961a-106">Cette rubrique répertorie divers travaux, packages et bases de données à supprimer.</span><span class="sxs-lookup"><span data-stu-id="7961a-106">This topic lists the different jobs, packages, and databases to be deleted.</span></span> <span data-ttu-id="7961a-107">Les noms répertoriés ici sont les noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7961a-107">The names listed are the default names.</span></span> <span data-ttu-id="7961a-108">Votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise peut-être des noms autres que les noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7961a-108">Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment may be using non-default names.</span></span>  
  
-   <span data-ttu-id="7961a-109">Effectuez les étapes dans l'ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="7961a-109">Complete the steps in the order listed.</span></span> <span data-ttu-id="7961a-110">Autrement, l'installation ne s'effectue pas complètement.</span><span class="sxs-lookup"><span data-stu-id="7961a-110">Otherwise, the uninstall is not complete.</span></span>  
  
##  <a name="BKMK_Unconfigure"></a> <span data-ttu-id="7961a-111">Annulation de la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7961a-111">Un-configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="7961a-112">Cliquez avec le bouton droit sur **Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, puis sélectionnez **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="7961a-112">Right-click **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration**, and select **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="7961a-113">Dans la configuration, sélectionnez **Annuler la configuration des composants**.</span><span class="sxs-lookup"><span data-stu-id="7961a-113">In the Configuration, select **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="7961a-114">Sélectionnez les composants dont vous souhaitez annuler la configuration, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="7961a-114">Select the features you want to unconfigure, and select **OK**.</span></span> <span data-ttu-id="7961a-115">Si vous êtes invité à continuer, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="7961a-115">If prompted to proceed, select **Yes**.</span></span> <span data-ttu-id="7961a-116">Pour tout supprimer de l’ordinateur, vous pouvez sélectionner tous les composants.</span><span class="sxs-lookup"><span data-stu-id="7961a-116">To  remove everything from the computer, you can select all the features.</span></span>  
  
4.  <span data-ttu-id="7961a-117">Sélectionnez **Suivant** et suivez les instructions de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7961a-117">Select **Next**, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="7961a-118">Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\nom_utilisateur\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log.</span><span class="sxs-lookup"><span data-stu-id="7961a-118">A log file is generated in a temp folder, similar to: C:\Users\username\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log.</span></span>  
  
##  <a name="BKMK_Uninstall"></a> <span data-ttu-id="7961a-119">Désinstallation des composants d’exécution de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7961a-119">Uninstall BizTalk Server Runtime Components</span></span>  
  
1.  <span data-ttu-id="7961a-120">Ouvrez **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="7961a-120">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="7961a-121">Sélectionnez votre version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans la liste et sélectionnez **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="7961a-121">Select  your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] version from the list, and  **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="7961a-122">**Supprimez**-la et suivez les instructions de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7961a-122">**Remove** it, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="7961a-123">Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\\*nom_utilisateur*\AppData\Local\Setup(083016 xxxxxx).htm</span><span class="sxs-lookup"><span data-stu-id="7961a-123">A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span></span>  
  
##  <a name="BKMK_UninstallSSO"></a> <span data-ttu-id="7961a-124">Désinstallation de l’authentification unique de l’entreprise</span><span class="sxs-lookup"><span data-stu-id="7961a-124">Uninstall Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="7961a-125">Ouvrez **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="7961a-125">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="7961a-126">Sélectionnez **Microsoft Enterprise Single Sign-On** dans la liste, puis sélectionnez **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="7961a-126">Select **Microsoft Enterprise Single Sign-On** from the list, and **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="7961a-127">**Supprimez** cette fonctionnalité et suivez les instructions de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7961a-127">**Remove** it, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="7961a-128">Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\\*nom_utilisateur*\AppData\Local\Setup(083016 xxxxxx).htm</span><span class="sxs-lookup"><span data-stu-id="7961a-128">A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span></span>  
  
##  <a name="BKMK_RemoveRemaining"></a> <span data-ttu-id="7961a-129">Suppression des travaux, des bases de données et des packages SQL</span><span class="sxs-lookup"><span data-stu-id="7961a-129">Delete SQL jobs, databases, and packages</span></span>  
  
#### <a name="delete-sql-server-agent-jobs"></a><span data-ttu-id="7961a-130">Suppression des travaux de l'Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="7961a-130">Delete SQL Server agent jobs</span></span>  
  
1.  <span data-ttu-id="7961a-131">Ouvrez **SQL Server Management Studio** comme administrateur.</span><span class="sxs-lookup"><span data-stu-id="7961a-131">Open **SQL Server Management Studio** as Administrator.</span></span>  
  
2.  <span data-ttu-id="7961a-132">Dans **SQL Server Management Studio**, connectez-vous au **moteur de base de données**, puis développez **SQL Server Agent** et **Travaux**.</span><span class="sxs-lookup"><span data-stu-id="7961a-132">In **SQL Server Management Studio**, connect to **Database Engine**, expand **SQL Server Agent**, and expand  **Jobs**.</span></span>  
  
3.  <span data-ttu-id="7961a-133">Supprimez les travaux suivants (cliquez avec le bouton droit sur le travail et sélectionnez **Supprimer**) :</span><span class="sxs-lookup"><span data-stu-id="7961a-133">Delete the following jobs (right-click the job, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="7961a-134">Backup BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="7961a-134">Backup BizTalk Server (BizTalkMgmtDb)</span></span>  
  
    -   <span data-ttu-id="7961a-135">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="7961a-135">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span></span>  
  
    -   <span data-ttu-id="7961a-136">DTA Purge and Archive (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="7961a-136">DTA Purge and Archive (BizTalkDTADb)</span></span>  
  
    -   <span data-ttu-id="7961a-137">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-137">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-138">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-138">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-139">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-139">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-140">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-140">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-141">MessageBox_UpdateStats_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-141">MessageBox_UpdateStats_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-142">Monitor BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="7961a-142">Monitor BizTalk Server (BizTalkMgmtDb)</span></span>  
  
    -   <span data-ttu-id="7961a-143">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-143">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-145">Rules_Database_Cleanup_BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="7961a-145">Rules_Database_Cleanup_BizTalkRuleEngineDb</span></span>  
  
    -   <span data-ttu-id="7961a-146">TrackedMessages_Copy_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-146">TrackedMessages_Copy_BizTalkMsgBoxDb</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7961a-147">Si vous avez déployé BAM, vous devez également supprimer la table bam_\<*nom du Cube*\>_\<*nom de la vue* \> travail.</span><span class="sxs-lookup"><span data-stu-id="7961a-147">If you deployed BAM, you may also need to remove the bam_\<*Cube Name*\>_\<*View Name*\> job.</span></span>  
  
#### <a name="delete-biztalk-server-databases"></a><span data-ttu-id="7961a-148">Suppression des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7961a-148">Delete BizTalk Server databases</span></span>  
  
1.  <span data-ttu-id="7961a-149">Dans l’**Explorateur d’objets**, développez **Bases de données**.</span><span class="sxs-lookup"><span data-stu-id="7961a-149">In **Object Explorer**, expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="7961a-150">Supprimez les bases de données suivantes (cliquez avec le bouton droit sur la base de données et sélectionnez **Supprimer**) :</span><span class="sxs-lookup"><span data-stu-id="7961a-150">Delete the following databases (right-click the database, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="7961a-151">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="7961a-151">BAMArchive</span></span>  
  
    -   <span data-ttu-id="7961a-152">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="7961a-152">BAMPrimaryImport</span></span>  
  
    -   <span data-ttu-id="7961a-153">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="7961a-153">BAMStarSchema</span></span>  
  
    -   <span data-ttu-id="7961a-154">BizTalkDTADb</span><span class="sxs-lookup"><span data-stu-id="7961a-154">BizTalkDTADb</span></span>  
  
    -   <span data-ttu-id="7961a-155">BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="7961a-155">BizTalkMgmtDb</span></span>  
  
    -   <span data-ttu-id="7961a-156">BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="7961a-156">BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="7961a-157">BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="7961a-157">BizTalkRuleEngineDb</span></span>  
  
    -   <span data-ttu-id="7961a-158">SSODB</span><span class="sxs-lookup"><span data-stu-id="7961a-158">SSODB</span></span>  
  
#### <a name="remove-sql-server-integration-services-packages"></a><span data-ttu-id="7961a-159">Suppression des packages SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="7961a-159">Remove SQL Server Integration Services packages</span></span>  
  
1.  <span data-ttu-id="7961a-160">Dans l’**Explorateur d’objets**, **connectez**-vous à **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="7961a-160">In **Object Explorer**,  **Connect** to **Integration Services**.</span></span>  
  
2.  <span data-ttu-id="7961a-161">Développez **Packages stockés** puis **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="7961a-161">Expand **Stored Packages**, and expand **MSDB**.</span></span>  
  
3.  <span data-ttu-id="7961a-162">Supprimez les packages avec les préfixes suivants (cliquez avec le bouton droit sur le package et sélectionnez **Supprimer**) :</span><span class="sxs-lookup"><span data-stu-id="7961a-162">Delete the packages with the following prefixes (right-click the package, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="7961a-163">BAM_AN_\<*nom du Cube*\></span><span class="sxs-lookup"><span data-stu-id="7961a-163">BAM_AN_\<*Cube Name*\></span></span>  
  
    -   <span data-ttu-id="7961a-164">BAM_DM_\<*afficher le nom*\></span><span class="sxs-lookup"><span data-stu-id="7961a-164">BAM_DM_\<*View Name*\></span></span>  
  

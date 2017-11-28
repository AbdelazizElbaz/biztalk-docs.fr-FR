---
title: "Utilisation avec le fichier de définition d’activité suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking, activity definition file
- activity definition file
- activity definition file, about activity definition file
- tracking, managing views
- activity definition file, activity fields
ms.assetid: 0592a844-aad7-4054-b1e7-344f1086f0b1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 751b05f28682ecc0a0230fc924cf706d0531784d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-the-tracking-activity-definition-file"></a><span data-ttu-id="a6935-102">Utilisation avec le fichier de définition des activités de suivi</span><span class="sxs-lookup"><span data-stu-id="a6935-102">Working with the Tracking Activity Definition File</span></span>
<span data-ttu-id="a6935-103">Le fichier de définition d’activité contient des informations sur le suivi des activités de processus et le message dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6935-103">The activity definition file contains information about the tracking process and message activities in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a6935-104">utilise ce fichier pour gérer les données de suivi dans BizTalk d’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="a6935-104"> uses this file to manage data tracking in BizTalk Business Activity Monitoring (BAM).</span></span> <span data-ttu-id="a6935-105">Le fichier de définition est un fichier XML (Tracking.xml) qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] le programme d’installation installe dans le \< *lecteur*> : \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet \BAMTracking dossier.</span><span class="sxs-lookup"><span data-stu-id="a6935-105">The definition file is an XML file (Tracking.xml) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAMTracking folder.</span></span> <span data-ttu-id="a6935-106">Les activités définies dans Tracking.xml peuvent suffire à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="a6935-106">The activities defined in Tracking.xml may be sufficient for your purposes.</span></span>  
  
 <span data-ttu-id="a6935-107">Pour plus d’informations sur le suivi des activités, des vues et tables, consultez [amélioré de suivi](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="a6935-107">For more information about the tracking activities, views, and tables, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span></span> <span data-ttu-id="a6935-108">Pour plus d’informations sur BAM, consultez « analyse BAM (Business Activity) » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="a6935-108">For more information about BAM, see "Business Activity Monitoring (BAM)" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="managing-tracking-views"></a><span data-ttu-id="a6935-109">La gestion des vues de suivi</span><span class="sxs-lookup"><span data-stu-id="a6935-109">Managing Tracking Views</span></span>  
 <span data-ttu-id="a6935-110">Vous n’utilisez pas l’éditeur de modèle de suivi BizTalk avec [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] de suivi.</span><span class="sxs-lookup"><span data-stu-id="a6935-110">You do not use the BizTalk Tracking Profile Editor with [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracking.</span></span> <span data-ttu-id="a6935-111">Les points de suivi ne sont pas personnalisables ; ne modifiez pas les définitions d’activité.</span><span class="sxs-lookup"><span data-stu-id="a6935-111">The tracking points are not customizable; do not change activity definitions.</span></span> <span data-ttu-id="a6935-112">Toutefois, vous pouvez gérer le déploiement et les vues BAM.</span><span class="sxs-lookup"><span data-stu-id="a6935-112">However, you can manage BAM views and deployment.</span></span> <span data-ttu-id="a6935-113">Pour ce faire, vous modifiez un [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul (Tracking.xls) qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] le programme d’installation installe dans le \< *lecteur*> : \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\BAMTracking dossier.</span><span class="sxs-lookup"><span data-stu-id="a6935-113">To do so, you modify an [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet (Tracking.xls) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking folder.</span></span> <span data-ttu-id="a6935-114">Pour plus d’informations, consultez « Gestion de suivi des vues » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a6935-114">For more information, see "Managing Tracking Views" below.</span></span>  
  
 <span data-ttu-id="a6935-115">Si les vues définies dans Tracking.xml ne suffisent pas à vos besoins, vous pouvez définir des vues différentes des informations de suivi de l’analyse BAM comme suit.</span><span class="sxs-lookup"><span data-stu-id="a6935-115">If the views defined in Tracking.xml are not sufficient for your needs, you can define different views of the information tracked in BAM as follows.</span></span>  
  
#### <a name="to-create-different-tracking-views"></a><span data-ttu-id="a6935-116">Pour créer des vues de suivi différent</span><span class="sxs-lookup"><span data-stu-id="a6935-116">To create different tracking views</span></span>  
  
1.  <span data-ttu-id="a6935-117">Cliquez sur **Démarrer**, puis sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="a6935-117">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="a6935-118">Entrez **cmd** dans la zone de texte Ouvrir de la boîte de dialogue Exécuter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6935-118">Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**.</span></span> <span data-ttu-id="a6935-119">Dans la boîte de dialogue ligne de commande, entrez le code suivant pour annuler le déploiement de tracking.xml, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="a6935-119">In the command line dialog box, enter the following code to undeploy tracking.xml, then click **OK**:</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm remove-all  -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking\<filename>.xml"  
    ```  
  
2.  <span data-ttu-id="a6935-120">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à  *\<lecteur >*: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM de suivi.</span><span class="sxs-lookup"><span data-stu-id="a6935-120">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *\<drive>*:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM Tracking.</span></span> <span data-ttu-id="a6935-121">Double-cliquez sur Tracking.xls.</span><span class="sxs-lookup"><span data-stu-id="a6935-121">Double-click Tracking.xls.</span></span>  
  
3.  <span data-ttu-id="a6935-122">Créer une nouvelle vue dans l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="a6935-122">Create a new view in Business Activity Monitoring.</span></span> <span data-ttu-id="a6935-123">Pour plus d’informations sur la marche à suivre, consultez « Gestion de l’analyse BAM » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="a6935-123">For information about how to do so, see "Managing Business Activity Monitoring" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
4.  <span data-ttu-id="a6935-124">Cliquez sur **BAM**, puis cliquez sur **exporter XML**.</span><span class="sxs-lookup"><span data-stu-id="a6935-124">Click **BAM**, and then click **Export XML**.</span></span> <span data-ttu-id="a6935-125">Déplacer vers l’emplacement souhaité, entrez un nom de fichier (autres que Tracking.xml), puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a6935-125">Move to the desired location, enter a file name (other than Tracking.xml), and then click **Save**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a6935-126">Lorsque vous définissez de nouveaux affichages de suivi dans un fichier XLS de suivi et exportez un fichier XML à partir du fichier XLS de suivi, certains des nouveaux noms de champs peuvent être légèrement modifiées.</span><span class="sxs-lookup"><span data-stu-id="a6935-126">When you define new tracking views in a tracking XLS file, and export an XML file from the tracking XLS file, some of the new field names may be slightly modified.</span></span> <span data-ttu-id="a6935-127">Corriger ce problème en vérifiant les champs dans votre personnalisés de suivi de fichier XML dans le champ tracking.xml standard installé par le programme d’installation BTARN.</span><span class="sxs-lookup"><span data-stu-id="a6935-127">Correct this by verifying the fields in your customized tracking XML file against the standard tracking.xml field installed by BTARN setup.</span></span>  
  
5.  <span data-ttu-id="a6935-128">Déployer le suivi de nouveau fichier XML.</span><span class="sxs-lookup"><span data-stu-id="a6935-128">Deploy the new tracking XML file.</span></span> <span data-ttu-id="a6935-129">Pour ce faire, cliquez sur **Démarrer**, puis cliquez sur **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="a6935-129">To do so, click **Start**, and then click **Run**.</span></span> <span data-ttu-id="a6935-130">Entrez **cmd** dans la zone de texte Ouvrir de la boîte de dialogue Exécuter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6935-130">Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**.</span></span> <span data-ttu-id="a6935-131">Dans la boîte de dialogue ligne de commande, entrez le code suivant pour déployer votre nouveau fichier de suivi, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6935-131">In the command line dialog box, enter the following code to deploy your new tracking file, then click **OK**.</span></span> <span data-ttu-id="a6935-132">Il est recommandé de renommer le fichier XML de suivi afin que vous ne pas Remplacez le fichier tracking.xml par défaut.</span><span class="sxs-lookup"><span data-stu-id="a6935-132">It is recommended that you rename the tracking XML file so that you do not overwrite the default tracking.xml file.</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm.exe deploy-all -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2030 Accelerator for RosettaNet\BAMTracking\<filename>.xml"  
    ```  
  
 <span data-ttu-id="a6935-133">Les informations de suivi dans BAM n’incluent pas le contenu du message, car qui est stocké dans un [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="a6935-133">The information tracked in BAM does not include the message content, because that is stored in a [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] database.</span></span>  
  
 <span data-ttu-id="a6935-134">Vous pouvez gérer le déploiement de suivi à l’aide de l’entreprise activité analyse utilitaire de gestion BAM.</span><span class="sxs-lookup"><span data-stu-id="a6935-134">You can manage deployment of BAM tracking by using the Business Activity Monitoring Management Utility.</span></span> <span data-ttu-id="a6935-135">Pour plus d’informations sur cet utilitaire, consultez « À l’aide de l’utilitaire de Business activité analyse gestion » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="a6935-135">For more information about this utility, see "Using the Business Activity Monitoring Management Utility" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="activity-fields"></a><span data-ttu-id="a6935-136">Champs d’activité</span><span class="sxs-lookup"><span data-stu-id="a6935-136">Activity Fields</span></span>  
 <span data-ttu-id="a6935-137">Les champs de l’activité d’un message dans le fichier de définition d’activité sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a6935-137">The fields of the message activity in the activity definition file are the following:</span></span>  
  
-   <span data-ttu-id="a6935-138">NomActivité</span><span class="sxs-lookup"><span data-stu-id="a6935-138">ActivityName</span></span>  
  
-   <span data-ttu-id="a6935-139">Catégorie</span><span class="sxs-lookup"><span data-stu-id="a6935-139">Category</span></span>  
  
-   <span data-ttu-id="a6935-140">ContentKey</span><span class="sxs-lookup"><span data-stu-id="a6935-140">ContentKey</span></span>  
  
-   <span data-ttu-id="a6935-141">DestinationPartyName</span><span class="sxs-lookup"><span data-stu-id="a6935-141">DestinationPartyName</span></span>  
  
-   <span data-ttu-id="a6935-142">ErrorDescription</span><span class="sxs-lookup"><span data-stu-id="a6935-142">ErrorDescription</span></span>  
  
-   <span data-ttu-id="a6935-143">HasError</span><span class="sxs-lookup"><span data-stu-id="a6935-143">HasError</span></span>  
  
-   <span data-ttu-id="a6935-144">InReplyToMessageID</span><span class="sxs-lookup"><span data-stu-id="a6935-144">InReplyToMessageID</span></span>  
  
-   <span data-ttu-id="a6935-145">IsReceived</span><span class="sxs-lookup"><span data-stu-id="a6935-145">IsReceived</span></span>  
  
-   <span data-ttu-id="a6935-146">MessageTrackingID</span><span class="sxs-lookup"><span data-stu-id="a6935-146">MessageTrackingID</span></span>  
  
-   <span data-ttu-id="a6935-147">NoFPipInstance</span><span class="sxs-lookup"><span data-stu-id="a6935-147">NoFPipInstance</span></span>  
  
-   <span data-ttu-id="a6935-148">PipCode</span><span class="sxs-lookup"><span data-stu-id="a6935-148">PipCode</span></span>  
  
-   <span data-ttu-id="a6935-149">PipInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6935-149">PipInstanceID</span></span>  
  
-   <span data-ttu-id="a6935-150">PiPVersion</span><span class="sxs-lookup"><span data-stu-id="a6935-150">PiPVersion</span></span>  
  
-   <span data-ttu-id="a6935-151">SourcePartName</span><span class="sxs-lookup"><span data-stu-id="a6935-151">SourcePartName</span></span>  
  
-   <span data-ttu-id="a6935-152">Horodateur</span><span class="sxs-lookup"><span data-stu-id="a6935-152">Timestamp</span></span>  
  
 <span data-ttu-id="a6935-153">Les champs de l’activité de processus dans le fichier de définition d’activité sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a6935-153">The fields of the process activity in the activity definition file are the following:</span></span>  
  
-   <span data-ttu-id="a6935-154">EndTime</span><span class="sxs-lookup"><span data-stu-id="a6935-154">EndTime</span></span>  
  
-   <span data-ttu-id="a6935-155">InitiatorPartyName</span><span class="sxs-lookup"><span data-stu-id="a6935-155">InitiatorPartyName</span></span>  
  
-   <span data-ttu-id="a6935-156">IsInitiatorRole</span><span class="sxs-lookup"><span data-stu-id="a6935-156">IsInitiatorRole</span></span>  
  
-   <span data-ttu-id="a6935-157">PipCode</span><span class="sxs-lookup"><span data-stu-id="a6935-157">PipCode</span></span>  
  
-   <span data-ttu-id="a6935-158">PipInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6935-158">PipInstanceID</span></span>  
  
-   <span data-ttu-id="a6935-159">PipName</span><span class="sxs-lookup"><span data-stu-id="a6935-159">PipName</span></span>  
  
-   <span data-ttu-id="a6935-160">PipVersion</span><span class="sxs-lookup"><span data-stu-id="a6935-160">PipVersion</span></span>  
  
-   <span data-ttu-id="a6935-161">ResponderPartyName</span><span class="sxs-lookup"><span data-stu-id="a6935-161">ResponderPartyName</span></span>  
  
-   <span data-ttu-id="a6935-162">StartTime</span><span class="sxs-lookup"><span data-stu-id="a6935-162">StartTime</span></span>  
  
-   <span data-ttu-id="a6935-163">État</span><span class="sxs-lookup"><span data-stu-id="a6935-163">Status</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6935-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6935-164">See Also</span></span>  
 <span data-ttu-id="a6935-165">[Suivi amélioré](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="a6935-165">[Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span></span>  
 [<span data-ttu-id="a6935-166">Gérer la configuration, les certificats, les bases de données et la sécurité</span><span class="sxs-lookup"><span data-stu-id="a6935-166">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)
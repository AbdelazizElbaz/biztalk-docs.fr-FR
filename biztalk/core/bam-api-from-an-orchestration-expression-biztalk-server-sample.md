---
title: "API BAM à partir d’une Expression d’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, BAM
- examples, orchestrations
- BAM, examples
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26b9cbc21eb93cad52a421b7df0912a37708978c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-api-from-an-orchestration-expression-biztalk-server-sample"></a><span data-ttu-id="ae3a2-102">API BAM à partir d'une expression d'orchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ae3a2-102">BAM API from an Orchestration Expression (BizTalk Server Sample)</span></span>
<span data-ttu-id="ae3a2-103">Cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="ae3a2-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="ae3a2-104">utiliser l'API BAM à partir d'une expression d'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="ae3a2-104">Use the BAM API from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration expression.</span></span>  
  
-   <span data-ttu-id="ae3a2-105">suivre des éléments répétés à l'intérieur d'un message comme des instances d'activité distinctes ;</span><span class="sxs-lookup"><span data-stu-id="ae3a2-105">Track repeating items inside a message as separate activity instances.</span></span>  
  
-   <span data-ttu-id="ae3a2-106">créer une relation entre les données BAM suivies à l'aide d'un modèle de suivi et les données BAM suivies à l'aide de l'API BAM.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-106">Create a relationship between BAM data that is tracked by using a tracking profile, and BAM data tracked by using the BAM API.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ae3a2-107">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae3a2-107">Where to Find This Sample</span></span>  
 <span data-ttu-id="ae3a2-108">Vous pouvez trouver cet exemple à  *\<exemples de chemin >*\BAM\BamFromExpression.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-108">You can find this sample at *\<Samples Path>*\BAM\BamFromExpression.</span></span>  
  
 <span data-ttu-id="ae3a2-109">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-109">The following table lists the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ae3a2-110">Fichier</span><span class="sxs-lookup"><span data-stu-id="ae3a2-110">File</span></span>|<span data-ttu-id="ae3a2-111"> Description</span><span class="sxs-lookup"><span data-stu-id="ae3a2-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ae3a2-112">BamDefinition.xls</span><span class="sxs-lookup"><span data-stu-id="ae3a2-112">BamDefinition.xls</span></span>|<span data-ttu-id="ae3a2-113">Feuille de style définition BAM.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-113">BAM definition stylesheet.</span></span>|  
|<span data-ttu-id="ae3a2-114">BamDefinition.xml</span><span class="sxs-lookup"><span data-stu-id="ae3a2-114">BamDefinition.xml</span></span>|<span data-ttu-id="ae3a2-115">Définition BAM.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-115">BAM definition.</span></span>|  
|<span data-ttu-id="ae3a2-116">BamFromExpression.btproj</span><span class="sxs-lookup"><span data-stu-id="ae3a2-116">BamFromExpression.btproj</span></span>|<span data-ttu-id="ae3a2-117">Projet de fichier de suivi [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae3a2-117">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] tracking file project.</span></span>|  
|<span data-ttu-id="ae3a2-118">BamFromExpression.sln</span><span class="sxs-lookup"><span data-stu-id="ae3a2-118">BamFromExpression.sln</span></span>|<span data-ttu-id="ae3a2-119">Solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae3a2-119">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution.</span></span>|  
|<span data-ttu-id="ae3a2-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="ae3a2-120">Cleanup.bat</span></span>|<span data-ttu-id="ae3a2-121">Fichiers de commandes pour annuler le déploiement de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-121">Batch file to undeploy the sample.</span></span>|  
|<span data-ttu-id="ae3a2-122">InputMessage.xml</span><span class="sxs-lookup"><span data-stu-id="ae3a2-122">InputMessage.xml</span></span>|<span data-ttu-id="ae3a2-123">Message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-123">Input message.</span></span>|  
|<span data-ttu-id="ae3a2-124">Orchestration1.odx</span><span class="sxs-lookup"><span data-stu-id="ae3a2-124">Orchestration1.odx</span></span>|<span data-ttu-id="ae3a2-125">Orchestration :</span><span class="sxs-lookup"><span data-stu-id="ae3a2-125">Orchestration.</span></span>|  
|<span data-ttu-id="ae3a2-126">PoSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="ae3a2-126">PoSchema.xsd</span></span>|<span data-ttu-id="ae3a2-127">Schéma de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-127">Purchase order schema.</span></span>|  
|<span data-ttu-id="ae3a2-128">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="ae3a2-128">PropertySchema.xsd</span></span>|<span data-ttu-id="ae3a2-129">Schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-129">Property schema.</span></span>|  
|<span data-ttu-id="ae3a2-130">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="ae3a2-130">Setup.bat</span></span>|<span data-ttu-id="ae3a2-131">Fichier de commandes pour compiler et déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-131">Batch file to compile and deploy the sample.</span></span>|  
|<span data-ttu-id="ae3a2-132">QueryBam.sql</span><span class="sxs-lookup"><span data-stu-id="ae3a2-132">QueryBam.sql</span></span>|<span data-ttu-id="ae3a2-133">Script SQL.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-133">SQL script.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="ae3a2-134">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ae3a2-134">How to Use This Sample</span></span>  
 <span data-ttu-id="ae3a2-135">Les procédures suivantes permettent de créer le modèle de suivi, d'exécuter l'exemple et de consulter les résultats.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-135">Use the following procedures to create the tracking profile, run the sample, and view the results.</span></span>  
  
#### <a name="to-create-the-tracking-profile"></a><span data-ttu-id="ae3a2-136">Pour créer le modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="ae3a2-136">To create the tracking profile</span></span>  
  
1.  <span data-ttu-id="ae3a2-137">Ouvrez une invite de commandes et exécutez  *\<exemples de chemin >*\BAM\BAMFromExpression\Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-137">Open a command prompt and run *\<Samples Path>*\BAM\BAMFromExpression\Setup.bat.</span></span> <span data-ttu-id="ae3a2-138">Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-138">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.</span></span> <span data-ttu-id="ae3a2-139">Setup.bat initialise l'infrastructure BAM pour cet exemple et déploie l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-139">Setup.bat initializes the BAM infrastructure for this sample, and deploys the BAM activity.</span></span>  
  
2.  <span data-ttu-id="ae3a2-140">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **éditeur**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-140">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span> <span data-ttu-id="ae3a2-141">Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], avec le bouton droit **éditeur** puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-141">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], right-click **Tracking Profile Editor** and then click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="ae3a2-142">Dans le volet gauche de la **éditeur** fenêtre, cliquez sur **cliquez ici pour importer une définition d’activité BAM**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-142">In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.</span></span>  
  
4.  <span data-ttu-id="ae3a2-143">Dans le **le nom de définition d’activité BAM** section de la **importer une définition d’activité BAM** boîte de dialogue, sélectionnez **FromExpressionPo**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-143">In the **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **FromExpressionPo**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ae3a2-144">Dans le volet droit de la **éditeur** fenêtre, cliquez sur **cliquez ici pour sélectionner une source d’événement**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-144">In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.</span></span>  
  
6.  <span data-ttu-id="ae3a2-145">Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamFromExpression**, puis cliquez sur  **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-145">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamFromExpression**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="ae3a2-146">Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamFromExpression.Orchestration1**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-146">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamFromExpression.Orchestration1**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="ae3a2-147">Cliquez sur le **Receive_1** mettre en forme, puis cliquez sur **schéma de charge utile de Message**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-147">Right-click the **Receive_1** shape, and then click **Message Payload Schema**.</span></span>  
  
9. <span data-ttu-id="ae3a2-148">Développez  **\<schéma >**, développez **PurchaseOrder**, développez **de**, puis faites glisser **PoID** dans le volet droit pour  **ID d’activité** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-148">Expand **\<Schema>**, expand **PurchaseOrder**, expand **From**, and then drag **PoID** in the right pane to **ActivityID** in the left pane.</span></span>  
  
10. <span data-ttu-id="ae3a2-149">Faites glisser les éléments suivants à partir du volet droit et déposez-les sur les nœuds nommés dans le volet gauche :</span><span class="sxs-lookup"><span data-stu-id="ae3a2-149">Drag the following elements from the right pane, and drop them onto the named nodes in the left pane:</span></span>  
  
    |<span data-ttu-id="ae3a2-150">De</span><span class="sxs-lookup"><span data-stu-id="ae3a2-150">From</span></span>|<span data-ttu-id="ae3a2-151">Pour</span><span class="sxs-lookup"><span data-stu-id="ae3a2-151">To</span></span>|  
    |----------|--------|  
    |<span data-ttu-id="ae3a2-152">Nom</span><span class="sxs-lookup"><span data-stu-id="ae3a2-152">Name</span></span>|<span data-ttu-id="ae3a2-153">De</span><span class="sxs-lookup"><span data-stu-id="ae3a2-153">From</span></span>|  
    |<span data-ttu-id="ae3a2-154">État</span><span class="sxs-lookup"><span data-stu-id="ae3a2-154">State</span></span>|<span data-ttu-id="ae3a2-155">État</span><span class="sxs-lookup"><span data-stu-id="ae3a2-155">State</span></span>|  
    |<span data-ttu-id="ae3a2-156">Ville</span><span class="sxs-lookup"><span data-stu-id="ae3a2-156">City</span></span>|<span data-ttu-id="ae3a2-157">Ville</span><span class="sxs-lookup"><span data-stu-id="ae3a2-157">City</span></span>|  
    |<span data-ttu-id="ae3a2-158">Téléphone</span><span class="sxs-lookup"><span data-stu-id="ae3a2-158">Phone</span></span>|<span data-ttu-id="ae3a2-159">Téléphone</span><span class="sxs-lookup"><span data-stu-id="ae3a2-159">Phone</span></span>|  
    |<span data-ttu-id="ae3a2-160">Total</span><span class="sxs-lookup"><span data-stu-id="ae3a2-160">Total</span></span>|<span data-ttu-id="ae3a2-161">PoTotal</span><span class="sxs-lookup"><span data-stu-id="ae3a2-161">PoTotal</span></span>|  
  
11. <span data-ttu-id="ae3a2-162">Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et des &#45; flèche](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) pour afficher l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-162">Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) to display the orchestration.</span></span>  
  
12. <span data-ttu-id="ae3a2-163">Faites glisser le **Receive_1** forme dans le volet droit pour **reçus** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-163">Drag the **Receive_1** shape in the right pane to **Received** in the left pane.</span></span>  
  
13. <span data-ttu-id="ae3a2-164">Faites glisser le **Send_1** forme dans le volet droit pour **envoyer** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-164">Drag the **Send_1** shape in the right pane to **Send** in the left pane.</span></span>  
  
14. <span data-ttu-id="ae3a2-165">Enregistrer le modèle de suivi à  *\<exemples de chemin >*\BAM\BamFromExpression\ BamFromExpression.btt.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-165">Save the tracking profile to *\<Samples Path>*\BAM\BamFromExpression\ BamFromExpression.btt.</span></span>  
  
15. <span data-ttu-id="ae3a2-166">Sur le **outils** menu, cliquez sur **appliquer le modèle de suivi**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-166">On the **Tools** menu, click **Apply Tracking Profile**.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="ae3a2-167">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae3a2-167">To build and initialize this sample</span></span>  
  
-   <span data-ttu-id="ae3a2-168">Déployez le modèle de suivi BamFromExpression.btt.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-168">Deploy the BamFromExpression.btt tracking profile.</span></span> <span data-ttu-id="ae3a2-169">Pour plus d’informations, consultez [comment déployer des profils de suivi avec le suivi des profils de l’utilitaire de gestion](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).</span><span class="sxs-lookup"><span data-stu-id="ae3a2-169">For more information, see [How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ae3a2-170">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae3a2-170">To run this sample</span></span>  
  
-   <span data-ttu-id="ae3a2-171">Copiez le fichier  *\<exemples de chemin >*\BamFromExpression\InputMessage.xml à  *\<exemples de chemin >*\BamFromExpression\Input.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-171">Copy the file *\<Samples Path>*\BamFromExpression\InputMessage.xml to *\<Samples Path>*\BamFromExpression\Input.</span></span>  
  
     <span data-ttu-id="ae3a2-172">Environ 10 secondes, le message de sortie s’affiche dans  *\<exemples de chemin >*\BamFromExpression\Output.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-172">In about 10 seconds the output message will appear in *\<Samples Path>*\BamFromExpression\Output.</span></span>  
  
#### <a name="to-view-the-bam-data"></a><span data-ttu-id="ae3a2-173">Pour afficher les données BAM</span><span class="sxs-lookup"><span data-stu-id="ae3a2-173">To view the BAM data</span></span>  
  
1.  <span data-ttu-id="ae3a2-174">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-174">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="ae3a2-175">Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-175">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="ae3a2-176">Avec le bouton droit **dbo.bam_FromExpressionPo_Completed**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-176">Right-click **dbo.bam_FromExpressionPo_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="ae3a2-177">Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-177">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="ae3a2-178">Le contenu de la table bam_FromExpressionPo_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-178">The contents of the bam_FromExpressionPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="ae3a2-179">La ligne dont l'ID d'activité est 123 représente le bon de commande d'une valeur de 345 $ que contenait le message entrant.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-179">The one row, which has an activity ID of 123, represents the purchase order for $345 that was contained in the input message.</span></span>  
  
4.  <span data-ttu-id="ae3a2-180">Avec le bouton droit **dbo.bam_FromExpressionPoItem_Completed**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-180">Right-click **dbo.bam_FromExpressionPoItem_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="ae3a2-181">Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-181">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="ae3a2-182">Le contenu de la table bam_FromExpressionPoItem_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-182">The contents of the bam_FromExpressionPoItem_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="ae3a2-183">Les deux lignes ayant activité ID 123_0 et 123_1 représentent les éléments dans l’ordre d’achat : articles Flash MC et décodeur infrarouge.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-183">The two rows, which have activity IDs 123_0 and 123_1, represent the items in the purchase order: Flash MC and Infrared Decoder.</span></span>  
  
5.  <span data-ttu-id="ae3a2-184">Avec le bouton droit **dbo.bam_FromExpressionPoItem_CompletedRelationships**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-184">Right-click **dbo.bam_FromExpressionPoItem_CompletedRelationships**, and then click **Open Table**.</span></span> <span data-ttu-id="ae3a2-185">Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-185">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="ae3a2-186">Le contenu de la table bam_FromExpressionPoItem_CompletedRelationships s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-186">The contents of the bam_FromExpressionPoItem_CompletedRelationships table are displayed in the right pane.</span></span> <span data-ttu-id="ae3a2-187">Chaque ligne de la table représente une relation entre une activité FromExpressionPoItem et une activité FromExpressionPo.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-187">Each row in the table represents a relationship between a FromExpressionPoItem activity and a FromExpressionPo activity.</span></span> <span data-ttu-id="ae3a2-188">La valeur de la **ActivityID** colonne fait référence à l’ID d’activité de l’activité FromExpressionPoItem.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-188">The value in the **ActivityID** column refers to the activity ID of the FromExpressionPoItem activity.</span></span> <span data-ttu-id="ae3a2-189">La valeur de la **ReferenceData** colonne fait référence à l’ID d’activité de l’activité FromExpressionPo.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-189">The value in the **ReferenceData** column refers to the activity ID of the FromExpressionPo activity.</span></span> <span data-ttu-id="ae3a2-190">Dans ce cas, les deux enregistrements indiquent que les articles Flash MC et décodeur infrarouge sont associés au bon de commande d'une valeur de 345 $.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-190">In this case, the two records indicate that the Flash MC and Infrared Decoder items are associated with the purchase order for $345.</span></span>  
  
#### <a name="to-re-run-the-sample"></a><span data-ttu-id="ae3a2-191">Pour réexécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae3a2-191">To re-run the sample</span></span>  
  
1.  <span data-ttu-id="ae3a2-192">Ouvrez une invite de commandes et exécutez  *\<exemples de chemin >*\BAM\BamFromExpression\Cleanup.bat pour supprimer le modèle de suivi et toute autre infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-192">Open a command prompt and run *\<Samples Path>*\BAM\BamFromExpression\Cleanup.bat to remove the tracking profile and other BAM infrastructure.</span></span> <span data-ttu-id="ae3a2-193">Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-193">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.</span></span>  
  
2.  <span data-ttu-id="ae3a2-194">Exécutez  *\<exemples de chemin >*\BAM\BamFromExpression\Setup.bat pour compiler l’exemple et le déployer.</span><span class="sxs-lookup"><span data-stu-id="ae3a2-194">Run *\<Samples Path>*\BAM\BamFromExpression\Setup.bat to compile the sample and deploy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3a2-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae3a2-195">See Also</span></span>  
 <span data-ttu-id="ae3a2-196">[Business Activity Monitoring (dossier d’exemples BizTalk Server)](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="ae3a2-196">[Business Activity Monitoring (BizTalk Server Samples Folder)](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="ae3a2-197">Relations d’activité</span><span class="sxs-lookup"><span data-stu-id="ae3a2-197">Activity Relationships</span></span>](../core/activity-relationships.md)
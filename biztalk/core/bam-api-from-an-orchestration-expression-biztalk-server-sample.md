---
title: "API BAM à partir de l’exemple d’Expression d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5413940eaba97e6f68d5e068e26625f320e6e817
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="bam-api-from-an-orchestration-expression-biztalk-server-sample"></a><span data-ttu-id="c8cb4-102">API BAM à partir d'une expression d'orchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="c8cb4-102">BAM API from an Orchestration Expression (BizTalk Server Sample)</span></span>
<span data-ttu-id="c8cb4-103">Cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="c8cb4-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="c8cb4-104">Utilisez l’API BAM à partir d’une expression d’orchestration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-104">Use the BAM API from a BizTalk Server orchestration expression.</span></span>  
  
-   <span data-ttu-id="c8cb4-105">suivre des éléments répétés à l'intérieur d'un message comme des instances d'activité distinctes ;</span><span class="sxs-lookup"><span data-stu-id="c8cb4-105">Track repeating items inside a message as separate activity instances.</span></span>  
  
-   <span data-ttu-id="c8cb4-106">créer une relation entre les données BAM suivies à l'aide d'un modèle de suivi et les données BAM suivies à l'aide de l'API BAM.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-106">Create a relationship between BAM data that is tracked by using a tracking profile, and BAM data tracked by using the BAM API.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="c8cb4-107">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="c8cb4-107">Where to Find This Sample</span></span>  
 <span data-ttu-id="c8cb4-108">Vous pouvez trouver cet exemple à  *\<exemples de chemin\>*\BAM\BamFromExpression.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-108">You can find this sample at *\<Samples Path\>*\BAM\BamFromExpression.</span></span>  
  
 <span data-ttu-id="c8cb4-109">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-109">The following table lists the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="c8cb4-110">Fichier</span><span class="sxs-lookup"><span data-stu-id="c8cb4-110">File</span></span>|<span data-ttu-id="c8cb4-111"> Description</span><span class="sxs-lookup"><span data-stu-id="c8cb4-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c8cb4-112">BamDefinition.xls</span><span class="sxs-lookup"><span data-stu-id="c8cb4-112">BamDefinition.xls</span></span>|<span data-ttu-id="c8cb4-113">Feuille de style définition BAM.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-113">BAM definition stylesheet.</span></span>|  
|<span data-ttu-id="c8cb4-114">BamDefinition.xml</span><span class="sxs-lookup"><span data-stu-id="c8cb4-114">BamDefinition.xml</span></span>|<span data-ttu-id="c8cb4-115">Définition BAM.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-115">BAM definition.</span></span>|  
|<span data-ttu-id="c8cb4-116">BamFromExpression.btproj</span><span class="sxs-lookup"><span data-stu-id="c8cb4-116">BamFromExpression.btproj</span></span>|<span data-ttu-id="c8cb4-117">Visual Studio, suivi du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-117">Visual Studio tracking file project.</span></span>|  
|<span data-ttu-id="c8cb4-118">BamFromExpression.sln</span><span class="sxs-lookup"><span data-stu-id="c8cb4-118">BamFromExpression.sln</span></span>|<span data-ttu-id="c8cb4-119">Solution de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-119">Visual Studio solution.</span></span>|  
|<span data-ttu-id="c8cb4-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="c8cb4-120">Cleanup.bat</span></span>|<span data-ttu-id="c8cb4-121">Fichiers de commandes pour annuler le déploiement de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-121">Batch file to undeploy the sample.</span></span>|  
|<span data-ttu-id="c8cb4-122">InputMessage.xml</span><span class="sxs-lookup"><span data-stu-id="c8cb4-122">InputMessage.xml</span></span>|<span data-ttu-id="c8cb4-123">Message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-123">Input message.</span></span>|  
|<span data-ttu-id="c8cb4-124">Orchestration1.odx</span><span class="sxs-lookup"><span data-stu-id="c8cb4-124">Orchestration1.odx</span></span>|<span data-ttu-id="c8cb4-125">Orchestration :</span><span class="sxs-lookup"><span data-stu-id="c8cb4-125">Orchestration.</span></span>|  
|<span data-ttu-id="c8cb4-126">PoSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="c8cb4-126">PoSchema.xsd</span></span>|<span data-ttu-id="c8cb4-127">Schéma de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-127">Purchase order schema.</span></span>|  
|<span data-ttu-id="c8cb4-128">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="c8cb4-128">PropertySchema.xsd</span></span>|<span data-ttu-id="c8cb4-129">Schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-129">Property schema.</span></span>|  
|<span data-ttu-id="c8cb4-130">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="c8cb4-130">Setup.bat</span></span>|<span data-ttu-id="c8cb4-131">Fichier de commandes pour compiler et déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-131">Batch file to compile and deploy the sample.</span></span>|  
|<span data-ttu-id="c8cb4-132">QueryBam.sql</span><span class="sxs-lookup"><span data-stu-id="c8cb4-132">QueryBam.sql</span></span>|<span data-ttu-id="c8cb4-133">Script SQL.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-133">SQL script.</span></span>|  
  
## <a name="create-the-tracking-profile"></a><span data-ttu-id="c8cb4-134">Créer le modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="c8cb4-134">Create the tracking profile</span></span>  
  
1.  <span data-ttu-id="c8cb4-135">Ouvrez une invite de commandes en tant qu’administrateur et exécutez  *\<exemples de chemin\>*\BAM\BAMFromExpression\Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-135">Open a command prompt as Administrator, and run *\<Samples Path\>*\BAM\BAMFromExpression\Setup.bat.</span></span> <span data-ttu-id="c8cb4-136">Setup.bat initialise l'infrastructure BAM pour cet exemple et déploie l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-136">Setup.bat initializes the BAM infrastructure for this sample, and deploys the BAM activity.</span></span>  
  
2.  <span data-ttu-id="c8cb4-137">À partir de votre **programmes** > **Microsoft BizTalk Server**, avec le bouton droit **éditeur**, et **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-137">From your **Programs** > **Microsoft BizTalk Server**, right-click **Tracking Profile Editor**, and **Run as administrator**.</span></span>
  
3.  <span data-ttu-id="c8cb4-138">Dans le volet gauche de la **éditeur** fenêtre, cliquez sur **cliquez ici pour importer une définition d’activité BAM**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-138">In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.</span></span>  
  
4.  <span data-ttu-id="c8cb4-139">Dans le **le nom de définition d’activité BAM** section de la **importer une définition d’activité BAM** boîte de dialogue, sélectionnez **FromExpressionPo**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-139">In the **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **FromExpressionPo**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c8cb4-140">Dans le volet droit de la **éditeur** fenêtre, cliquez sur **cliquez ici pour sélectionner une source d’événement**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-140">In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.</span></span>  
  
6.  <span data-ttu-id="c8cb4-141">Dans le **nom de l’Assembly** section de la **sélectionner l’Assembly Parent Source événement** boîte de dialogue, sélectionnez **Microsoft.Samples.BizTalk.BamFromExpression**, puis cliquez sur  **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-141">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamFromExpression**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="c8cb4-142">Dans le **nom de l’Orchestration** section de la **sélectionner une Orchestration** boîte de dialogue, sélectionnez **BamFromExpression.Orchestration1**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-142">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamFromExpression.Orchestration1**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c8cb4-143">Cliquez sur le **Receive_1** mettre en forme, puis cliquez sur **schéma de charge utile de Message**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-143">Right-click the **Receive_1** shape, and then click **Message Payload Schema**.</span></span>  
  
9. <span data-ttu-id="c8cb4-144">Développez  **\<schéma\>**, développez **PurchaseOrder**, développez **de**, puis faites glisser **PoID** à droite volet à **ActivityID** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-144">Expand **\<Schema\>**, expand **PurchaseOrder**, expand **From**, and then drag **PoID** in the right pane to **ActivityID** in the left pane.</span></span>  
  
10. <span data-ttu-id="c8cb4-145">Faites glisser les éléments suivants à partir du volet droit et déposez-les sur les nœuds nommés dans le volet gauche :</span><span class="sxs-lookup"><span data-stu-id="c8cb4-145">Drag the following elements from the right pane, and drop them onto the named nodes in the left pane:</span></span>  
  
    |<span data-ttu-id="c8cb4-146">From</span><span class="sxs-lookup"><span data-stu-id="c8cb4-146">From</span></span>|<span data-ttu-id="c8cb4-147">Pour</span><span class="sxs-lookup"><span data-stu-id="c8cb4-147">To</span></span>|  
    |----------|--------|  
    |<span data-ttu-id="c8cb4-148">Nom</span><span class="sxs-lookup"><span data-stu-id="c8cb4-148">Name</span></span>|<span data-ttu-id="c8cb4-149">From</span><span class="sxs-lookup"><span data-stu-id="c8cb4-149">From</span></span>|  
    |<span data-ttu-id="c8cb4-150">État</span><span class="sxs-lookup"><span data-stu-id="c8cb4-150">State</span></span>|<span data-ttu-id="c8cb4-151">État</span><span class="sxs-lookup"><span data-stu-id="c8cb4-151">State</span></span>|  
    |<span data-ttu-id="c8cb4-152">Ville</span><span class="sxs-lookup"><span data-stu-id="c8cb4-152">City</span></span>|<span data-ttu-id="c8cb4-153">Ville</span><span class="sxs-lookup"><span data-stu-id="c8cb4-153">City</span></span>|  
    |<span data-ttu-id="c8cb4-154">Téléphone</span><span class="sxs-lookup"><span data-stu-id="c8cb4-154">Phone</span></span>|<span data-ttu-id="c8cb4-155">Téléphone</span><span class="sxs-lookup"><span data-stu-id="c8cb4-155">Phone</span></span>|  
    |<span data-ttu-id="c8cb4-156">Total</span><span class="sxs-lookup"><span data-stu-id="c8cb4-156">Total</span></span>|<span data-ttu-id="c8cb4-157">PoTotal</span><span class="sxs-lookup"><span data-stu-id="c8cb4-157">PoTotal</span></span>|  
  
11. <span data-ttu-id="c8cb4-158">Cliquez sur l’icône de dossier avec la flèche (![bouton avec dossier et des &#45; flèche](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) pour afficher l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-158">Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) to display the orchestration.</span></span>  
  
12. <span data-ttu-id="c8cb4-159">Faites glisser le **Receive_1** forme dans le volet droit pour **reçus** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-159">Drag the **Receive_1** shape in the right pane to **Received** in the left pane.</span></span>  
  
13. <span data-ttu-id="c8cb4-160">Faites glisser le **Send_1** forme dans le volet droit pour **envoyer** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-160">Drag the **Send_1** shape in the right pane to **Send** in the left pane.</span></span>  
  
14. <span data-ttu-id="c8cb4-161">Enregistrer le modèle de suivi à  *\<exemples de chemin\>*\BAM\BamFromExpression\ BamFromExpression.btt.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-161">Save the tracking profile to *\<Samples Path\>*\BAM\BamFromExpression\ BamFromExpression.btt.</span></span>  
  
15. <span data-ttu-id="c8cb4-162">Sur le **outils** menu, cliquez sur **appliquer le modèle de suivi**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-162">On the **Tools** menu, click **Apply Tracking Profile**.</span></span>  
  
## <a name="build-and-initialize-this-sample"></a><span data-ttu-id="c8cb4-163">Créer et initialiser l’exemple</span><span class="sxs-lookup"><span data-stu-id="c8cb4-163">Build and initialize this sample</span></span>  
  
<span data-ttu-id="c8cb4-164">Déployez le modèle de suivi BamFromExpression.btt.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-164">Deploy the BamFromExpression.btt tracking profile.</span></span> <span data-ttu-id="c8cb4-165">Consultez [comment déployer des modèles de suivi avec le suivi des profils d’utilitaire de gestion](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).</span><span class="sxs-lookup"><span data-stu-id="c8cb4-165">See [How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).</span></span>  
  
## <a name="run-this-sample"></a><span data-ttu-id="c8cb4-166">Exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="c8cb4-166">Run this sample</span></span>  
  
<span data-ttu-id="c8cb4-167">Copiez le fichier  *\<exemples de chemin\>*\BamFromExpression\InputMessage.xml à  *\<exemples de chemin\>*\BamFromExpression\Input.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-167">Copy the file *\<Samples Path\>*\BamFromExpression\InputMessage.xml to *\<Samples Path\>*\BamFromExpression\Input.</span></span>  
  
<span data-ttu-id="c8cb4-168">Environ 10 secondes, le message de sortie s’affiche dans  *\<exemples de chemin\>*\BamFromExpression\Output.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-168">In about 10 seconds the output message will appear in *\<Samples Path\>*\BamFromExpression\Output.</span></span>  
  
## <a name="view-the-bam-data"></a><span data-ttu-id="c8cb4-169">Afficher les données BAM</span><span class="sxs-lookup"><span data-stu-id="c8cb4-169">View the BAM data</span></span>  
  
1.  <span data-ttu-id="c8cb4-170">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-170">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="c8cb4-171">Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-171">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="c8cb4-172">Avec le bouton droit **dbo.bam_FromExpressionPo_Completed**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-172">Right-click **dbo.bam_FromExpressionPo_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="c8cb4-173">Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-173">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="c8cb4-174">Le contenu de la table bam_FromExpressionPo_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-174">The contents of the bam_FromExpressionPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="c8cb4-175">La ligne dont l'ID d'activité est 123 représente le bon de commande d'une valeur de 345 $ que contenait le message entrant.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-175">The one row, which has an activity ID of 123, represents the purchase order for $345 that was contained in the input message.</span></span>  
  
4.  <span data-ttu-id="c8cb4-176">Avec le bouton droit **dbo.bam_FromExpressionPoItem_Completed**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-176">Right-click **dbo.bam_FromExpressionPoItem_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="c8cb4-177">Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-177">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="c8cb4-178">Le contenu de la table bam_FromExpressionPoItem_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-178">The contents of the bam_FromExpressionPoItem_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="c8cb4-179">Les deux lignes ayant activité ID 123_0 et 123_1 représentent les éléments dans l’ordre d’achat : articles Flash MC et décodeur infrarouge.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-179">The two rows, which have activity IDs 123_0 and 123_1, represent the items in the purchase order: Flash MC and Infrared Decoder.</span></span>  
  
5.  <span data-ttu-id="c8cb4-180">Avec le bouton droit **dbo.bam_FromExpressionPoItem_CompletedRelationships**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-180">Right-click **dbo.bam_FromExpressionPoItem_CompletedRelationships**, and then click **Open Table**.</span></span> <span data-ttu-id="c8cb4-181">Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-181">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="c8cb4-182">Le contenu de la table bam_FromExpressionPoItem_CompletedRelationships s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-182">The contents of the bam_FromExpressionPoItem_CompletedRelationships table are displayed in the right pane.</span></span> <span data-ttu-id="c8cb4-183">Chaque ligne de la table représente une relation entre une activité FromExpressionPoItem et une activité FromExpressionPo.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-183">Each row in the table represents a relationship between a FromExpressionPoItem activity and a FromExpressionPo activity.</span></span> <span data-ttu-id="c8cb4-184">La valeur de la **ActivityID** colonne fait référence à l’ID d’activité de l’activité FromExpressionPoItem.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-184">The value in the **ActivityID** column refers to the activity ID of the FromExpressionPoItem activity.</span></span> <span data-ttu-id="c8cb4-185">La valeur de la **ReferenceData** colonne fait référence à l’ID d’activité de l’activité FromExpressionPo.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-185">The value in the **ReferenceData** column refers to the activity ID of the FromExpressionPo activity.</span></span> <span data-ttu-id="c8cb4-186">Dans ce cas, les deux enregistrements indiquent que les articles Flash MC et décodeur infrarouge sont associés au bon de commande d'une valeur de 345 $.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-186">In this case, the two records indicate that the Flash MC and Infrared Decoder items are associated with the purchase order for $345.</span></span>  
  
## <a name="re-run-the-sample"></a><span data-ttu-id="c8cb4-187">Exécuter à nouveau l’exemple</span><span class="sxs-lookup"><span data-stu-id="c8cb4-187">Re-run the sample</span></span>  
  
1.  <span data-ttu-id="c8cb4-188">Ouvrez une invite de commandes en tant qu’administrateur et exécutez  *\<exemples de chemin\>*\BAM\BamFromExpression\Cleanup.bat pour supprimer le modèle de suivi et toute autre infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-188">Open a command prompt as Administrator, and run *\<Samples Path\>*\BAM\BamFromExpression\Cleanup.bat to remove the tracking profile and other BAM infrastructure.</span></span> 
  
2.  <span data-ttu-id="c8cb4-189">Exécutez  *\<exemples de chemin\>*\BAM\BamFromExpression\Setup.bat pour compiler l’exemple et le déployer.</span><span class="sxs-lookup"><span data-stu-id="c8cb4-189">Run *\<Samples Path\>*\BAM\BamFromExpression\Setup.bat to compile the sample and deploy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cb4-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8cb4-190">See Also</span></span>  
 <span data-ttu-id="c8cb4-191">[Business Activity Monitoring (dossier d’exemples BizTalk Server)](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="c8cb4-191">[Business Activity Monitoring (BizTalk Server Samples Folder)](../core/business-activity-monitoring-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="c8cb4-192">Relations d’activité</span><span class="sxs-lookup"><span data-stu-id="c8cb4-192">Activity Relationships</span></span>](../core/activity-relationships.md)
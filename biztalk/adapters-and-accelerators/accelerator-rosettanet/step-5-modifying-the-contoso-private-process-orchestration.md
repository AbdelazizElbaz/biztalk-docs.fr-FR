---
title: "Étape 5 : Modification de l’Orchestration de processus de privé Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, orchestrations
- private process tutorial, modifying private process orchestration
ms.assetid: a5430db8-e5f0-48a6-abb9-e268d8ec2ec4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a222ee518cf0555de60094411df73bf5a5d486a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-5-modifying-the-contoso-private-process-orchestration"></a><span data-ttu-id="fc15a-102">Étape 5 : Modification de l’Orchestration de processus de privé de Contoso</span><span class="sxs-lookup"><span data-stu-id="fc15a-102">Step 5: Modifying the Contoso Private Process Orchestration</span></span>
<span data-ttu-id="fc15a-103">Dans cette étape, vous modifiez l’orchestration de processus privé à intégrer avec le système de planification ERP (Enterprise Resource) pour Contoso.</span><span class="sxs-lookup"><span data-stu-id="fc15a-103">In this step, you modify the private process orchestration to integrate with the Enterprise Resource Planning (ERP) system for Contoso.</span></span> <span data-ttu-id="fc15a-104">Le système ERP de Contoso utilise les schémas définies en interne pour la disponibilité et le prix du produit.</span><span class="sxs-lookup"><span data-stu-id="fc15a-104">The ERP system for Contoso uses internally defined schemas for product price and availability.</span></span> <span data-ttu-id="fc15a-105">En personnalisant le processus privé pour le 3A2 - prix et la disponibilité des processus PIP (Partner Interface), vous serez en mesure d’intégrer le système ERP à l’aide des informations de mappage de schéma.</span><span class="sxs-lookup"><span data-stu-id="fc15a-105">By customizing the private process for the 3A2 - Price and Availability Partner Interface Process (PIP), you will be able to integrate with the ERP system by using schema-mapping information.</span></span>  
  
### <a name="to-add-a-reference-to-the-contoso-priceandavailability-and-rnpips-assemblies"></a><span data-ttu-id="fc15a-106">Pour ajouter une référence aux assemblys Contoso PriceAndAvailability et RNPIPs</span><span class="sxs-lookup"><span data-stu-id="fc15a-106">To add a reference to the Contoso PriceAndAvailability and RNPIPs assemblies</span></span>  
  
1.  <span data-ttu-id="fc15a-107">Avec la solution Contoso est affichée dans l’Explorateur de solutions, cliquez sur le **PrivateResponder** de projet, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-107">With the Contoso solution displayed in Solution Explorer, right-click the **PrivateResponder** project, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="fc15a-108">Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-108">In the Add Reference dialog box, click **Browse**.</span></span> <span data-ttu-id="fc15a-109">Déplacer vers  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin dossier et sélectionnez les assemblys suivants**:**</span><span class="sxs-lookup"><span data-stu-id="fc15a-109">Move to *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin folder, and then select the following assemblies**:**</span></span>  
  
    -   <span data-ttu-id="fc15a-110">Microsoft.Solutions.BTARN.CommonTypes.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-110">Microsoft.Solutions.BTARN.CommonTypes.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-111">Microsoft.Solutions.BTARN.ConfigurationManager.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-111">Microsoft.Solutions.BTARN.ConfigurationManager.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-112">Microsoft.Solutions.BTARN.GlobalSchemas.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-112">Microsoft.Solutions.BTARN.GlobalSchemas.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-113">Microsoft.Solutions.BTARN.PublicResponder.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-113">Microsoft.Solutions.BTARN.PublicResponder.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-114">Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-114">Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-115">Microsoft.Solutions.BTARN.Shared.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-115">Microsoft.Solutions.BTARN.Shared.dll</span></span>  
  
    -   <span data-ttu-id="fc15a-116">Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll</span><span class="sxs-lookup"><span data-stu-id="fc15a-116">Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll</span></span>  
  
3.  <span data-ttu-id="fc15a-117">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-117">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="fc15a-118">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **projets** onglet, sélectionnez le **ContosoPriceAndAvailability** et **HeaderHelper** projets, puis cliquez sur  **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-118">In the Add Reference dialog box, click the **Projects** tab, select the **ContosoPriceAndAvailability** and **HeaderHelper** projects, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="fc15a-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-119">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="fc15a-120">Dans la boîte de dialogue environnement de développement Microsoft, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-120">In the Microsoft Development Environment dialog box, click **OK**.</span></span>  
  
### <a name="to-create-new-message-types"></a><span data-ttu-id="fc15a-121">Pour créer des types de message</span><span class="sxs-lookup"><span data-stu-id="fc15a-121">To create new message types</span></span>  
  
1.  <span data-ttu-id="fc15a-122">Dans l’Explorateur de solutions, double-cliquez sur le **PrivateResponder** orchestration pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="fc15a-122">In Solution Explorer, double-click the **PrivateResponder** orchestration to open it.</span></span>  
  
2.  <span data-ttu-id="fc15a-123">Dans l’Explorateur de solutions, cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-123">In Solution Explorer, click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="fc15a-124">Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-124">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="fc15a-125">Dans la fenêtre Propriétés, dans le **identificateur** , tapez **PIP3A2RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-125">In the Properties window, in the **Identifier** box, type **PIP3A2RequestMessage**.</span></span>  
  
5.  <span data-ttu-id="fc15a-126">Dans le **Type de Message** , cliquez sur la flèche déroulante, développez **schémas**, puis sélectionnez  **\<sélectionner dans l’assembly référencé\>**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-126">In the **Message Type** box, click the drop-down arrow, expand **Schemas**, and then select **\<Select from referenced assembly\>**.</span></span>  
  
6.  <span data-ttu-id="fc15a-127">Dans la zone Sélectionner le Typedialog artefact, sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs** dans le volet gauche, sélectionnez **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3** dans le volet droit, et puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-127">In the Select Artifact Typedialog box, select **Microsoft.Solutions.BTARN.Schemas.RNPIPs** in the left pane, select **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3** in the right pane, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="fc15a-128">Répétez les étapes 3 à 6 pour créer tous les types de message pour la solution en utilisant les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc15a-128">Repeat steps 3 through 6 to create all the message types for the solution using the following information:</span></span>  
  
    |<span data-ttu-id="fc15a-129">Identificateur</span><span class="sxs-lookup"><span data-stu-id="fc15a-129">Identifier</span></span>|<span data-ttu-id="fc15a-130">Assembly</span><span class="sxs-lookup"><span data-stu-id="fc15a-130">Assembly</span></span>|<span data-ttu-id="fc15a-131">Type de message</span><span class="sxs-lookup"><span data-stu-id="fc15a-131">Message Type</span></span>|  
    |----------------|--------------|------------------|  
    |<span data-ttu-id="fc15a-132">PIP3A2ResponseMessage</span><span class="sxs-lookup"><span data-stu-id="fc15a-132">PIP3A2ResponseMessage</span></span>|<span data-ttu-id="fc15a-133">Microsoft.Solutions.BTARN.</span><span class="sxs-lookup"><span data-stu-id="fc15a-133">Microsoft.Solutions.BTARN.</span></span><br /><span data-ttu-id="fc15a-134">Schemas.RNPips</span><span class="sxs-lookup"><span data-stu-id="fc15a-134">Schemas.RNPips</span></span>|<span data-ttu-id="fc15a-135">_3A2PriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="fc15a-135">_3A2PriceAndAvailability</span></span><br /><span data-ttu-id="fc15a-136">ResponseMessageGuideline_v1_3</span><span class="sxs-lookup"><span data-stu-id="fc15a-136">ResponseMessageGuideline_v1_3</span></span>|  
    |<span data-ttu-id="fc15a-137">Contoso3A2ResponseMessage</span><span class="sxs-lookup"><span data-stu-id="fc15a-137">Contoso3A2ResponseMessage</span></span>|<span data-ttu-id="fc15a-138">ContosoPriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="fc15a-138">ContosoPriceAndAvailability</span></span>|<span data-ttu-id="fc15a-139">rootPriceResponse</span><span class="sxs-lookup"><span data-stu-id="fc15a-139">rootPriceResponse</span></span>|  
    |<span data-ttu-id="fc15a-140">Contoso3A2RequestMessage</span><span class="sxs-lookup"><span data-stu-id="fc15a-140">Contoso3A2RequestMessage</span></span>|<span data-ttu-id="fc15a-141">ContosoPriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="fc15a-141">ContosoPriceAndAvailability</span></span>|<span data-ttu-id="fc15a-142">rootPriceRequest</span><span class="sxs-lookup"><span data-stu-id="fc15a-142">rootPriceRequest</span></span>|  
  
8.  <span data-ttu-id="fc15a-143">Vous avez terminé la création des types de message pour la solution.</span><span class="sxs-lookup"><span data-stu-id="fc15a-143">You have finished creating the message types for the solution.</span></span>  
  
### <a name="to-create-new-variables"></a><span data-ttu-id="fc15a-144">Pour créer de nouvelles variables</span><span class="sxs-lookup"><span data-stu-id="fc15a-144">To create new variables</span></span>  
  
1.  <span data-ttu-id="fc15a-145">Dans la vue Orchestration, cliquez sur **Variables,** puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-145">In Orchestration View, right-click **Variables,** and then click **New Variable**.</span></span>  
  
2.  <span data-ttu-id="fc15a-146">Dans la fenêtre Propriétés, dans le **identificateur** , tapez **contosoResponseXML**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-146">In the Properties window, in the **Identifier** box, type **contosoResponseXML**.</span></span>  
  
3.  <span data-ttu-id="fc15a-147">Dans le **Type** boîte, sélectionnez  **\<classe .NET\>**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-147">In the **Type** box, select **\<.NET Class\>** from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="fc15a-148">Dans l’artefact sélectionnez Tapez boîte de dialogue, dans le volet gauche, sous la **projet actuel** et **références** nœuds, sélectionnez **System.Xml**, sélectionnez  **XmlDocument** à partir de la liste dans le volet droit, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-148">In the Select Artifact Type dialog box, in the left pane, under the **Current Project** and **References** nodes, select **System.Xml**, select **XmlDocument** from the list in the right pane, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="fc15a-149">Dans **Vue Orchestration**, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-149">In **Orchestration View**, click **Variables**,and then click **New Variable**.</span></span>  
  
6.  <span data-ttu-id="fc15a-150">Dans la fenêtre Propriétés, dans le **identificateur** , tapez **submitMessage**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-150">In the Properties window, in the **Identifier** box, type **submitMessage**.</span></span>  
  
7.  <span data-ttu-id="fc15a-151">Dans le **Type** boîte, sélectionnez  **\<classe .NET\>**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-151">In the **Type** box, select **\<.NET Class\>** from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="fc15a-152">Dans la boîte de dialogue Sélectionner le Type d’artefact dans le volet gauche, développez **projet actuel** et **références** nœuds, sélectionnez **Microsoft.Solutions.BTARN.Shared**, sélectionnez  **SubmitRNIF** à partir de la liste dans le volet droit, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-152">In the Select Artifact Type dialog box, in the left pane, expand **Current Project** and **References** nodes, select **Microsoft.Solutions.BTARN.Shared**, select **SubmitRNIF** from the list in the right pane, and then click **OK**.</span></span>  
  
### <a name="to-change-the-orchestration-filter-expression"></a><span data-ttu-id="fc15a-153">Pour modifier l’expression de filtre d’orchestration</span><span class="sxs-lookup"><span data-stu-id="fc15a-153">To change the orchestration filter expression</span></span>  
  
1.  <span data-ttu-id="fc15a-154">Dans le Concepteur d’Orchestration, sélectionnez la **ReceiveFromPublicProcessResponder** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-154">In Orchestration Designer, select the **ReceiveFromPublicProcessResponder** shape.</span></span>  
  
2.  <span data-ttu-id="fc15a-155">Dans la fenêtre Propriétés, dans le **Expression de filtre** zone, cliquez sur la zone de valeur, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la boîte de dialogue Expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="fc15a-155">In the Properties window, in the **Filter Expression** box, click the value box, and then click the ellipsis button (**...**) to open the Filter Expression dialog box.</span></span>  
  
3.  <span data-ttu-id="fc15a-156">Dans la boîte de dialogue Expression de filtre dans le **Group By** , cliquez sur le **ou** valeur sur la première ligne, puis sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-156">In the Filter Expression dialog box, in the **Group By** section, click the **OR** value on the first line, and then select **AND** from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="fc15a-157">Dans la boîte de dialogue Expression de filtre, cliquez sur **cliquez ici pour ajouter une nouvelle ligne**, puis sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-157">In the Filter Expression dialog box, click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="fc15a-158">Dans la même ligne, cliquez sur **valeur**, puis tapez dans **« 3A2 »**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-158">In the same row, click **Value**, and then type in **"3A2"**.</span></span>  
  
6.  <span data-ttu-id="fc15a-159">Dans la même ligne, cliquez sur **AND** dans les **Group By** zone, puis sélectionnez **ou** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-159">In the same row, click **AND** in the **Group By** box, and then select **OR** from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="fc15a-160">Dans la boîte de dialogue Expression de filtre, sélectionnez la ligne que vous venez de créer, puis cliquez sur une fois le bouton de flèche haut pour déplacer la ligne qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="fc15a-160">In the Filter Expression dialog box, select the row that you just created, and then click the up arrow button once to move the row up once.</span></span>  
  
8.  <span data-ttu-id="fc15a-161">Cliquez sur **cliquez ici pour ajouter une nouvelle ligne**, puis sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="fc15a-161">Click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="fc15a-162">Dans la même ligne, cliquez sur **valeur**, puis tapez dans **« 3A2 »**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-162">In the same row, click **Value**, and then type in **"3A2"**.</span></span>  
  
10. <span data-ttu-id="fc15a-163">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="fc15a-163">Click OK.</span></span>  
  
### <a name="to-modify-the-business-process-workflow"></a><span data-ttu-id="fc15a-164">Pour modifier le workflow de processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fc15a-164">To modify the business process workflow</span></span>  
  
1.  <span data-ttu-id="fc15a-165">Faites glisser un **assignation du Message** mettre en forme à partir de la boîte à outils vers l’aire de conception et déposez-le sous le **ReceiveFromPublicProcessResponder** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-165">Drag a **Message Assignment** shape from the Toolbox to the design surface and drop it under the **ReceiveFromPublicProcessResponder** shape.</span></span> <span data-ttu-id="fc15a-166">Sélectionnez le **ConstructMessage_1** forme qui a été créé et dans le **propriétés** fenêtre, dans le **nom** , tapez **ConstructPIP3A2RequestMessage** .</span><span class="sxs-lookup"><span data-stu-id="fc15a-166">Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructPIP3A2RequestMessage**.</span></span>  
  
2.  <span data-ttu-id="fc15a-167">Faites glisser un **transformer** forme sur l’aire de conception et déposez-le sous le **ConstructPIP3A2RequestMessage** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-167">Drag a **Transform** shape to the design surface and drop it under the **ConstructPIP3A2RequestMessage** shape.</span></span> <span data-ttu-id="fc15a-168">Sélectionnez le **ConstructMessage_1** forme qui a été créé et dans le **propriétés** fenêtre, dans le **nom** , tapez **ConstructContoso3A2RequestMessage** .</span><span class="sxs-lookup"><span data-stu-id="fc15a-168">Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructContoso3A2RequestMessage**.</span></span>  
  
3.  <span data-ttu-id="fc15a-169">Faites glisser un **envoyer** forme sur l’aire de conception et déposez-le sous le **ConstructContoso3A2RequestMessage** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-169">Drag a **Send** shape to the design surface and drop it under the **ConstructContoso3A2RequestMessage** shape.</span></span>  
  
4.  <span data-ttu-id="fc15a-170">Faites glisser un **réception** forme sur l’aire de conception et déposez-le sous le **Send_1** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-170">Drag a **Receive** shape to the design surface and drop it under the **Send_1** shape.</span></span>  
  
5.  <span data-ttu-id="fc15a-171">Dans l’aire de conception d’orchestration, cliquez sur une zone vide.</span><span class="sxs-lookup"><span data-stu-id="fc15a-171">On the orchestration design surface, click an empty area.</span></span>  
  
6.  <span data-ttu-id="fc15a-172">Dans la fenêtre Propriétés, sélectionnez le **Type de Transaction** propriété, puis cliquez sur **Long terme**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-172">In the Properties window, select the **Transaction Type** property, and then click **Long Running**.</span></span>  
  
7.  <span data-ttu-id="fc15a-173">Faites glisser un **étendue** forme sur l’aire de conception et déposez-le sous le **Receive_1** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-173">Drag a **Scope** shape to the design surface and drop it under the **Receive_1** shape.</span></span>  
  
8.  <span data-ttu-id="fc15a-174">Dans la fenêtre Propriétés, à partir de la **Type de Transaction** liste déroulante de propriétés, sélectionnez **atomique** pour le **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-174">In the Properties window, from the **Transaction Type** property drop-down list, select **Atomic** for the **Scope** shape.</span></span>  
  
9. <span data-ttu-id="fc15a-175">Faites glisser un **appeler règles** forme sur l’aire de conception et déposez-la sur l’étiquette indiquant que **déposez une forme à partir de la boîte à outils ici** à l’intérieur de la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-175">Drag a **Call Rules** shape to the design surface and drop it on the label that says **Drop a shape from the toolbox here** inside the **Scope** shape.</span></span> <span data-ttu-id="fc15a-176">Dans la fenêtre Propriétés pour le **appeler règles** mettre en forme, dans le **nom** , tapez **Execute3A2Vocabulary**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-176">In the Properties window for the **Call Rules** shape, in the **Name** box, type **Execute3A2Vocabulary**.</span></span>  
  
10. <span data-ttu-id="fc15a-177">Faites glisser un **transformer** forme sur l’aire de conception et déposez-le sous le **Scope_1** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-177">Drag a **Transform** shape to the design surface and drop it under the **Scope_1** shape.</span></span> <span data-ttu-id="fc15a-178">Cliquez sur le **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-178">Click the **ConstructMessage_1** shape.</span></span> <span data-ttu-id="fc15a-179">Dans la fenêtre Propriétés, dans le **nom** , tapez **Construct3A2ResponseMessage**.</span><span class="sxs-lookup"><span data-stu-id="fc15a-179">In the Properties window, in the **Name** box, type **Construct3A2ResponseMessage**.</span></span>  
  
11. <span data-ttu-id="fc15a-180">Faites glisser un **Expression** forme sur l’aire de conception et déposez-le sous le **Construct3A2ResponseMessageTransform** forme.</span><span class="sxs-lookup"><span data-stu-id="fc15a-180">Drag an **Expression** shape to the design surface and drop it under the **Construct3A2ResponseMessageTransform** shape.</span></span>  
  
12. <span data-ttu-id="fc15a-181">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="fc15a-181">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File**, click **Save All** to save the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc15a-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc15a-182">See Also</span></span>  
 [<span data-ttu-id="fc15a-183">Étape 6 : Configuration des formes d’orchestration (Contoso)</span><span class="sxs-lookup"><span data-stu-id="fc15a-183">Step 6: Configuring Orchestration Shapes (Contoso)</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)
---
title: "Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc4a67d9-9582-4f2b-9bc9-18fbff823d29
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 439caac8f1da151a9f203a1372039aaeedbfe83c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-add-a-trigger-event-message-schema"></a><span data-ttu-id="5eb1f-102">Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur</span><span class="sxs-lookup"><span data-stu-id="5eb1f-102">Step 3: Add a Trigger Event (Message) Schema</span></span>
<span data-ttu-id="5eb1f-103">Dans cette étape, vous créez un projet basé sur l’Empty [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-103">In this step, you create a new project based on the Empty [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Project template.</span></span> <span data-ttu-id="5eb1f-104">À ce projet, vous ajoutez le schéma qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise pour valider les messages dans le traitement par lots entrant (ADT ^ A03).</span><span class="sxs-lookup"><span data-stu-id="5eb1f-104">To this project, you add the schema that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use to validate the messages in the incoming batch (ADT^A03).</span></span> <span data-ttu-id="5eb1f-105">Vous ajoutez une référence au projet contenant les schémas courants v2.3.1, attribuez le nom fort au projet, puis déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-105">You add a reference to the project containing the v2.3.1 common schemas, assign the strong name to the project, and then deploy the project.</span></span>  
  
### <a name="to-add-the-project-containing-the-message-schema"></a><span data-ttu-id="5eb1f-106">Pour ajouter le projet contenant le schéma de message</span><span class="sxs-lookup"><span data-stu-id="5eb1f-106">To add the project containing the message schema</span></span>  
  
1.  <span data-ttu-id="5eb1f-107">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5eb1f-108">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-108">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="5eb1f-109">Dans le **modèles** section, sélectionnez **projet BTAHL7 vide**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-109">In the **Templates** section, select **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="5eb1f-110">Dans le **nom** , entrez **BTAHL7V231Body** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-110">In the **Name** box, enter **BTAHL7V231Body** as the project name.</span></span>  
  
5.  <span data-ttu-id="5eb1f-111">Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-111">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="5eb1f-112">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-112">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="5eb1f-113">Dans l’Explorateur de solutions, sous le nœud pour votre nouveau projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-113">In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="5eb1f-114">Dans la boîte de dialogue Ajouter une référence sur le **projets** , cliquez sur **BTAHL7V231Common projet** dans les **nom du projet** colonne, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-114">In the Add Reference dialog box, on the **Projects** tab, click **BTAHL7V231Common Project** in the **Project Name** column, click **Add**, and then click **OK**.</span></span>  
  
### <a name="to-add-the-schema-to-the-project"></a><span data-ttu-id="5eb1f-115">Pour ajouter le schéma au projet</span><span class="sxs-lookup"><span data-stu-id="5eb1f-115">To add the schema to the project</span></span>  
  
1.  <span data-ttu-id="5eb1f-116">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-116">In Solution Explorer, right-click **BTAHL7V231Body**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="5eb1f-117">Dans la boîte de dialogue Ajouter un nouvel élément, développez **des éléments de projet BizTalk**, puis cliquez sur **BTAHL7 schémas**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-117">In the Add New Item dialog box, expand **BizTalk Project Items**, and then click **BTAHL7 Schemas**.</span></span> <span data-ttu-id="5eb1f-118">Dans le **modèles** volet, cliquez sur **BTAHL7 schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-118">In the **Templates** pane, click **BTAHL7 Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="5eb1f-119">Dans le **sélecteur de schémas HL7** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5eb1f-119">In the **HL7 Schema Selector** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="5eb1f-120">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5eb1f-120">Use this</span></span>|<span data-ttu-id="5eb1f-121">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5eb1f-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5eb1f-122">**Classe de message**</span><span class="sxs-lookup"><span data-stu-id="5eb1f-122">**Message Class**</span></span>|<span data-ttu-id="5eb1f-123">Conserver **V2.X** comme étant sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-123">Keep **V2.X** as selected.</span></span>|  
    |<span data-ttu-id="5eb1f-124">**Version**</span><span class="sxs-lookup"><span data-stu-id="5eb1f-124">**Version**</span></span>|<span data-ttu-id="5eb1f-125">Sélectionnez **2.3.1**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-125">Select **2.3.1**.</span></span>|  
    |<span data-ttu-id="5eb1f-126">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="5eb1f-126">**Message Type**</span></span>|<span data-ttu-id="5eb1f-127">Sélectionnez **ADT**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-127">Select **ADT**.</span></span>|  
    |<span data-ttu-id="5eb1f-128">**Événement déclencheur**</span><span class="sxs-lookup"><span data-stu-id="5eb1f-128">**Trigger Event**</span></span>|<span data-ttu-id="5eb1f-129">Sélectionnez **A03**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-129">Select **A03**.</span></span>|  
  
4.  <span data-ttu-id="5eb1f-130">Cliquez sur **créer** pour ajouter le schéma au projet, puis cliquez sur **Annuler** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-130">Click **Create** to add the schema to the project, then click **Cancel** to close the dialog box.</span></span> <span data-ttu-id="5eb1f-131">Notez que BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) a ajouté le schéma ADT_A03_231_GLO_DEF.xsd au projet BTAHL7V231Body.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-131">Note that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) has added the ADT_A03_231_GLO_DEF.xsd schema to the BTAHL7V231Body project.</span></span>  
  
### <a name="to-assign-a-strong-key-and-deploy"></a><span data-ttu-id="5eb1f-132">Pour affecter une clé forte et déployer</span><span class="sxs-lookup"><span data-stu-id="5eb1f-132">To assign a strong key and deploy</span></span>  
  
1.  <span data-ttu-id="5eb1f-133">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-133">In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5eb1f-134">Dans la boîte de dialogue Page de propriétés BTAHL7V231Body, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-134">In the BTAHL7V231Body Property Page dialog box, click **Signing**.</span></span>  
  
3.  <span data-ttu-id="5eb1f-135">Vérifiez **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-135">Check **Sign the assembly** check box.</span></span>  
  
4.  <span data-ttu-id="5eb1f-136">Dans **choisir un fichier de clé de nom fort** dérouler la liste, sélectionnez  **\<Parcourir... \>.**</span><span class="sxs-lookup"><span data-stu-id="5eb1f-136">In **Choose a strong name key file** drop down list select **\<Browse…\>.**</span></span>  
  
5.  <span data-ttu-id="5eb1f-137">Accédez à  **\<* lecteur*\>: \Batching didacticiel **, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-137">Browse to **\<*drive*\>:\Batching Tutorial**, select **key.snk**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="5eb1f-138">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-138">In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Deploy**.</span></span> <span data-ttu-id="5eb1f-139">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-139">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5eb1f-140">Si un message successful-deploy n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="5eb1f-140">If a successful-deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="5eb1f-141">Passez à [étape 4 : créer un Port de réception pour accepter le Message de lot](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md).</span><span class="sxs-lookup"><span data-stu-id="5eb1f-141">Proceed to [Step 4: Create a Receive Port for Accepting the Batch Message](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md).</span></span>
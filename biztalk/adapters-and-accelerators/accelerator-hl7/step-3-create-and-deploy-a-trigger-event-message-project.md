---
title: "Étape 3 : Créer et déployer un projet d’événement (Message) de déclencheur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, trigger events
- trigger events
ms.assetid: 5d21a923-fc2c-4d50-b146-daca0aa26e2a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49fd078f64cbd4163eef648f7a0d58fe6e8db6b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-project"></a><span data-ttu-id="4e024-102">Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)</span><span class="sxs-lookup"><span data-stu-id="4e024-102">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>
<span data-ttu-id="4e024-103">Dans cette étape, vous créez le schéma pour le message d’événement déclencheur.</span><span class="sxs-lookup"><span data-stu-id="4e024-103">In this step, you create the schema for your trigger event message.</span></span> <span data-ttu-id="4e024-104">Par exemple, vous pouvez être le système (ADT) décharge d’admission et de transfert qui envoie un message à l’hôpital informations système (HIS).</span><span class="sxs-lookup"><span data-stu-id="4e024-104">For example, you might be the Admissions Discharge and Transfer system (ADT) who sends a message to the Hospital Information System (HIS).</span></span> <span data-ttu-id="4e024-105">Vous avez besoin de ce schéma pour définir le format de votre message.</span><span class="sxs-lookup"><span data-stu-id="4e024-105">You need this schema to define the format of your message.</span></span>  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a><span data-ttu-id="4e024-106">Pour créer le projet pour le message d’événement déclencheur</span><span class="sxs-lookup"><span data-stu-id="4e024-106">To create the project for the trigger event message</span></span>  
  
1.  <span data-ttu-id="4e024-107">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="4e024-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, then click **Project**.</span></span>  
  
2.  <span data-ttu-id="4e024-108">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="4e024-108">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="4e024-109">Dans la section modèles, cliquez sur **projet vide de BTAHL7**, dans le **nom** , tapez **BTAHL7V231Body projet**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e024-109">In the Templates section, click **Empty BTAHL7 Project**, in the **Name** box, type **BTAHL7V231Body Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="4e024-110">Dans l’Explorateur de solutions, sous le nœud pour votre nouveau projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="4e024-110">In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="4e024-111">Dans la boîte de dialogue Ajouter une référence sur le **projets** onglet, sélectionnez **BTAHL7V231Common Projet1**, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e024-111">In the Add Reference dialog box, on the **Projects** tab, select **BTAHL7V231Common Project1**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="step-3a-add-the-schema"></a><span data-ttu-id="4e024-112">Étape 3 a : ajouter le schéma</span><span class="sxs-lookup"><span data-stu-id="4e024-112">Step 3A: Add the Schema</span></span>  
 <span data-ttu-id="4e024-113">Utilisez la procédure suivante pour ajouter le nouveau schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="4e024-113">Use the following procedure to add the new schema to the project.</span></span>  
  
#### <a name="to-add-the-schema-to-the-project"></a><span data-ttu-id="4e024-114">Pour ajouter le schéma au projet</span><span class="sxs-lookup"><span data-stu-id="4e024-114">To add the schema to the project</span></span>  
  
1.  <span data-ttu-id="4e024-115">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4e024-115">In Solution Explorer, right-click **BTAHL7V231Body Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="4e024-116">Dans la zone Ajouter nouveau élément boîte de dialogue le **catégories** , développez **des éléments de projet BizTalk**, puis sélectionnez **BTAHL7 schémas**.</span><span class="sxs-lookup"><span data-stu-id="4e024-116">In the Add New Item dialog box, in the **Categories** section, expand **BizTalk Project Items**, and then select **BTAHL7 Schemas**.</span></span>  
  
3.  <span data-ttu-id="4e024-117">Dans la section modèles, double-cliquez sur **BTAHL7 schémas**.</span><span class="sxs-lookup"><span data-stu-id="4e024-117">In the Templates section, double-click **BTAHL7 Schemas**.</span></span>  
  
4.  <span data-ttu-id="4e024-118">Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4e024-118">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="4e024-119">Utiliser</span><span class="sxs-lookup"><span data-stu-id="4e024-119">Use this</span></span>|<span data-ttu-id="4e024-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="4e024-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4e024-121">**Classe de message**</span><span class="sxs-lookup"><span data-stu-id="4e024-121">**Message Class**</span></span>|<span data-ttu-id="4e024-122">Conservez la valeur par défaut **V2.X** sélectionné.</span><span class="sxs-lookup"><span data-stu-id="4e024-122">Leave the default of **V2.X** selected.</span></span>|  
    |<span data-ttu-id="4e024-123">**Version**</span><span class="sxs-lookup"><span data-stu-id="4e024-123">**Version**</span></span>|<span data-ttu-id="4e024-124">Sélectionnez **2.3.1**.</span><span class="sxs-lookup"><span data-stu-id="4e024-124">Select **2.3.1**.</span></span>|  
    |<span data-ttu-id="4e024-125">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="4e024-125">**Message Type**</span></span>|<span data-ttu-id="4e024-126">Sélectionnez **ADT**.</span><span class="sxs-lookup"><span data-stu-id="4e024-126">Select **ADT**.</span></span>|  
    |<span data-ttu-id="4e024-127">**Événement déclencheur**</span><span class="sxs-lookup"><span data-stu-id="4e024-127">**Trigger Event**</span></span>|<span data-ttu-id="4e024-128">Sélectionnez **A03**.</span><span class="sxs-lookup"><span data-stu-id="4e024-128">Select **A03**.</span></span>|  
  
5.  <span data-ttu-id="4e024-129">Cliquez sur **Terminer** pour ajouter le schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="4e024-129">Click **Finish** to add the schema to the project.</span></span>  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="4e024-130">Étape 3 b : assigner une clé forte à l’Assembly et le déployer</span><span class="sxs-lookup"><span data-stu-id="4e024-130">Step 3B: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="4e024-131">Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4e024-131">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="4e024-132">Pour affecter une clé forte et de déployer l’assembly</span><span class="sxs-lookup"><span data-stu-id="4e024-132">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="4e024-133">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V231Body projet**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4e024-133">In Solution Explorer, right-click **BTAHL7V231Body Project**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4e024-134">Dans la page des Pages de propriétés de projet, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="4e024-134">In the Project Property Pages page, click **Assembly**.</span></span>  
  
3.  <span data-ttu-id="4e024-135">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="4e024-135">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (**…**) button.</span></span>  
  
4.  <span data-ttu-id="4e024-136">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="4e024-136">In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="4e024-137">Dans la boîte de dialogue Pages de propriétés de projet, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="4e024-137">In the Project Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
6.  <span data-ttu-id="4e024-138">Dans l’Explorateur de solutions avec le bouton droit **BTAHL7V231Body projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="4e024-138">In Solution Explorer right-click **BTAHL7V231Body Project**, and then click **Deploy**.</span></span> <span data-ttu-id="4e024-139">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="4e024-139">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e024-140">Si un message de réussite de déploiement n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="4e024-140">If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="4e024-141">Passez à [étape 4 : créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md).</span><span class="sxs-lookup"><span data-stu-id="4e024-141">Proceed to [Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md).</span></span>
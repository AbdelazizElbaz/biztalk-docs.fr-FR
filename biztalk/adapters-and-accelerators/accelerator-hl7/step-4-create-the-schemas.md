---
title: "Étape 4 : Créer les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- creating, schemas
- schemas, creating
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ce9ea850632327e257909e1c7d4b60117865e46
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-4-create-the-schemas"></a><span data-ttu-id="aaa1c-102">Étape 4 : Créer les schémas</span><span class="sxs-lookup"><span data-stu-id="aaa1c-102">Step 4: Create the Schemas</span></span>
<span data-ttu-id="aaa1c-103">Dans cette étape, vous créez un nouveau projet (**BTAHL7 projet**) qui contient les artefacts de ce projet : les schémas, mappage et orchestration.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-103">In this step, you create a new project (**BTAHL7 Project**) that contains the artifacts for this project: the schemas, map, and orchestration.</span></span> <span data-ttu-id="aaa1c-104">Vous créez ensuite un schéma (**Doorbell.xsd**) pour le message entrant de codée au format XML, puis sélectionnez un schéma existant (**ADT_A04_22_GLO_DEF.xsd**) pour le message sortant encodé HL7.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-104">You then create a schema (**Doorbell.xsd**) for the incoming XML-encoded message, and select an existing schema (**ADT_A04_22_GLO_DEF.xsd**) for the outgoing HL7-encoded message.</span></span> <span data-ttu-id="aaa1c-105">Ces schémas vous permet de définir la structure des messages qui vous exchange au sein de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-105">You use these schemas to define the structure of the messages that you exchange within the orchestration.</span></span>  
  
### <a name="to-create-the-schemas"></a><span data-ttu-id="aaa1c-106">Pour créer les schémas</span><span class="sxs-lookup"><span data-stu-id="aaa1c-106">To create the schemas</span></span>  
  
1.  <span data-ttu-id="aaa1c-107">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="aaa1c-108">Dans la boîte de dialogue Nouveau projet, développez le **projets BizTalk** dossier, puis cliquez sur le **BTAHL7Projects** dossier.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-108">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
3.  <span data-ttu-id="aaa1c-109">Dans le **modèles** volet, cliquez sur **projet BTAHL7 vide**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-109">In the **Templates** pane, click **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="aaa1c-110">Dans le **nom** , tapez **BTAHL7 projet** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-110">In the **Name** field, type **BTAHL7 Project** as the project name.</span></span>  
  
5.  <span data-ttu-id="aaa1c-111">Dans le **Solution** champ, sélectionnez **ajouter à la Solution**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-111">In the **Solution** field, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="aaa1c-112">Dans le **emplacement** champ, vérifiez que  **\< *lecteur*\>: \Tutorial\BTAHL7V22Common** est le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-112">In the **Location** field, verify that **\<*drive*\>:\Tutorial\BTAHL7V22Common** is the path.</span></span>  
  
7.  <span data-ttu-id="aaa1c-113">Cliquez sur **OK** pour ouvrir le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-113">Click **OK** to open the new project.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="aaa1c-114">Ajoute un nouveau projet à l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-114"> adds a new project to Solution Explorer.</span></span> <span data-ttu-id="aaa1c-115">Il ajoute le dossier du projet et crée des fichiers d’également le \< *lecteur*\>: \Tutorial\\**BTAHL7V22Common** dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-115">It also adds the project folder and creates files in the \<*drive*\>:\Tutorial\\**BTAHL7V22Common** Project folder.</span></span>  
  
8.  <span data-ttu-id="aaa1c-116">Dans l’Explorateur de solutions, cliquez sur le **BTAHL7 projet** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-116">In Solution Explorer, right-click the **BTAHL7 Project** project, point to **Add**, and then click **New Item**.</span></span>  
  
9. <span data-ttu-id="aaa1c-117">Dans l’ajouter un nouvel élément - projet de BTAHL7 boîte de dialogue, dans le **catégories** volet, cliquez sur **fichiers de schéma**et dans le **modèles** volet, cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-117">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **Schema Files**, and in the **Templates** pane, click **Schema**.</span></span>  
  
10. <span data-ttu-id="aaa1c-118">Dans le **nom** , tapez **Doorbell.xsd** pour nommer le schéma.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-118">In the **Name** field, type **Doorbell.xsd** to name the schema.</span></span>  
  
11. <span data-ttu-id="aaa1c-119">Cliquez sur **ajouter** pour ouvrir le schéma vide dans l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-119">Click **Add** to open the blank schema in BizTalk Editor.</span></span>  
  
12. <span data-ttu-id="aaa1c-120">Dans le  **\<schéma\>**  d’arborescence, cliquez sur le **racine** nœud, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-120">In the **\<Schema\>** tree, right-click the **Root** node, and then click **Rename**.</span></span>  
  
13. <span data-ttu-id="aaa1c-121">Type **DoorbellRoot** comme nouveau nom, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-121">Type **DoorbellRoot** as the new name, and then press **Enter**.</span></span>  
  
14. <span data-ttu-id="aaa1c-122">Avec le bouton droit le **DoorbellRoot** nœud, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant** pour ajouter les champs suivants (Répétez cette étape pour chaque champ. élément) :</span><span class="sxs-lookup"><span data-stu-id="aaa1c-122">Right-click the **DoorbellRoot** node, point to **Insert Schema Node**, and then click **Child Field Element** to add the following fields (repeat this step for each field element):</span></span>  
  
    -   <span data-ttu-id="aaa1c-123">**Prénom**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-123">**FirstName**</span></span>  
  
    -   <span data-ttu-id="aaa1c-124">**MiddleName**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-124">**MiddleName**</span></span>  
  
    -   <span data-ttu-id="aaa1c-125">**LastName**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-125">**LastName**</span></span>  
  
    -   <span data-ttu-id="aaa1c-126">**SSN**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-126">**SSN**</span></span>  
  
15. <span data-ttu-id="aaa1c-127">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-127">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
16. <span data-ttu-id="aaa1c-128">Dans l’ajouter un nouvel élément - projet de BTAHL7 boîte de dialogue, dans le **catégories** volet, cliquez sur **BTAHL7 schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-128">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **BTAHL7 Schemas**, and then click **Add**.</span></span>  
  
17. <span data-ttu-id="aaa1c-129">Dans la boîte de dialogue Sélecteur de schémas HL7, dans le **classe de Message** boîte, sélectionnez **V2.X**et dans le **détails du schéma** volet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aaa1c-129">In the HL7 Schema Selector dialog box, in the **Message Class** box, select **V2.X**, and in the **Schema Details** pane, do the following:</span></span>  
  
    |<span data-ttu-id="aaa1c-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="aaa1c-130">Use this</span></span>|<span data-ttu-id="aaa1c-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="aaa1c-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aaa1c-132">**Version**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-132">**Version**</span></span>|<span data-ttu-id="aaa1c-133">Sélectionnez le numéro de version du message HL7.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-133">Select the version number of the HL7 message.</span></span> <span data-ttu-id="aaa1c-134">Dans ce didacticiel, utilisez **2.2**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-134">In this tutorial, use **2.2**.</span></span>|  
    |<span data-ttu-id="aaa1c-135">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-135">**Message Type**</span></span>|<span data-ttu-id="aaa1c-136">Sélectionnez le type de message HL7.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-136">Select the type of HL7 message.</span></span> <span data-ttu-id="aaa1c-137">Dans ce didacticiel, utilisez **ADT**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-137">In this tutorial, use **ADT**.</span></span>|  
    |<span data-ttu-id="aaa1c-138">**Événement déclencheur**</span><span class="sxs-lookup"><span data-stu-id="aaa1c-138">**Trigger Event**</span></span>|<span data-ttu-id="aaa1c-139">Sélectionnez la valeur de l’événement déclencheur pour le message HL7.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-139">Select the Trigger Event value for the HL7 message.</span></span> <span data-ttu-id="aaa1c-140">Dans ce didacticiel, utilisez **A04**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-140">In this tutorial, use **A04**.</span></span>|  
  
18. <span data-ttu-id="aaa1c-141">Cliquez sur **Terminer** pour ajouter le schéma ADT_A04_22_GLO_DEF.xsd (inscrire un Patient) à votre projet.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-141">Click **Finish** to add the ADT_A04_22_GLO_DEF.xsd (Register Patient) schema to your project.</span></span> <span data-ttu-id="aaa1c-142">Fermez la boîte de dialogue Sélecteur de schémas HL7.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-142">Close the HL7 Schema Selector dialog box.</span></span>  
  
19. <span data-ttu-id="aaa1c-143">Dans l’Explorateur de solutions, sous **BTAHL7 projet**, avec le bouton droit **références** puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-143">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  
  
20. <span data-ttu-id="aaa1c-144">Dans la boîte de dialogue Ajouter une référence sur le **projets** onglet, sélectionnez le **BTAHL7V22Common** de projet, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-144">In the Add Reference dialog box, on the **Projects** tab, select the **BTAHL7V22Common** project, click **Add**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aaa1c-145">Cette opération ajoute une référence au projet d’origine afin que [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] reconnaît les schémas HL7 correctement.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-145">This adds a reference to the original project so that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] recognizes the HL7 schemas correctly.</span></span>  
  
21. <span data-ttu-id="aaa1c-146">Dans l’Explorateur de solutions, sous **BTAHL7 projet**, avec le bouton droit **références** puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-146">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  
  
22. <span data-ttu-id="aaa1c-147">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** onglet. Dans le **Regarder dans** zone, atteindre \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator pour le didacticiel de bout en HL7\SDK\End \Tutorial_BTAHL7Drop\Bin.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-147">In the Add Reference dialog box, click the **Browse** tab. In the **Look In** box, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop\Bin.</span></span> <span data-ttu-id="aaa1c-148">Cliquez sur **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aaa1c-148">Click **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, click **Add**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="aaa1c-149">Passez à [étape 5 : promouvoir les propriétés d’un schéma](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).</span><span class="sxs-lookup"><span data-stu-id="aaa1c-149">Proceed to [Step 5: Promote Schema Properties](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa1c-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaa1c-150">See Also</span></span>  
 [<span data-ttu-id="aaa1c-151">Didacticiel sur l’enrichissement des messages</span><span class="sxs-lookup"><span data-stu-id="aaa1c-151">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
---
title: "Étape 2 : Création du schéma de demande de stock | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fa9ad9f-b815-4baf-8299-556869b8dde7
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06000a734856c7b9f22e78a2d5a78c4585021a21
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="step-2-create-the-inventory-request-schema"></a><span data-ttu-id="0b5c5-102">Étape 2 : création du schéma de demande de stock</span><span class="sxs-lookup"><span data-stu-id="0b5c5-102">Step 2: Create the Inventory Request Schema</span></span>
<span data-ttu-id="0b5c5-103">![Étape 2 sur 5](../core/media/step-2of5.gif "Step_2of5")</span><span class="sxs-lookup"><span data-stu-id="0b5c5-103">![Step 2 of 5](../core/media/step-2of5.gif "Step_2of5")</span></span>  
  
 <span data-ttu-id="0b5c5-104">**Durée :** 7 minutes</span><span class="sxs-lookup"><span data-stu-id="0b5c5-104">**Time to complete:** 7 minutes</span></span>  
  
 <span data-ttu-id="0b5c5-105">**Objectif :** dans cette étape, vous définissez le schéma de réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-105">**Objective:** In this step, you define the schema of the inventory replenishment message.</span></span>  <span data-ttu-id="0b5c5-106">Le système de l'entrepôt envoie ce message pour demander un réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-106">The warehouse system sends this message for requesting inventory replenishment.</span></span>  <span data-ttu-id="0b5c5-107">Voici l'un des deux schémas que vous devez créer pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-107">This is one of the two schemas you must create for this project.</span></span>  
  
 <span data-ttu-id="0b5c5-108">**Objectif :** XML non seulement les structures et identifie les informations de codes de balisage standard, mais a également la possibilité d’utiliser des schémas.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-108">**Purpose:** XML not only structures and identifies information with standardized markup codes, but also has the ability to use schemas.</span></span> <span data-ttu-id="0b5c5-109">Un schéma est un document XML organisé comme un dictionnaire qui sert de référence à d'autres documents XML.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-109">A schema is an XML document that works like a dictionary and is used as a reference by other XML documents.</span></span> <span data-ttu-id="0b5c5-110">Le code d'un schéma définit l'orthographe des éléments XML et le type de données encadrées par ces éléments.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-110">The schema code defines the spelling of XML elements and the type of data enclosed by those elements.</span></span> <span data-ttu-id="0b5c5-111">L'utilisation des schémas permet à un programme de traiter aisément des documents XML et veille à ce que la structure et le type des informations soient corrects.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-111">Using schemas provides an easy way for a program to process XML documents and ensures that the structure and type of information is correct.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b5c5-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0b5c5-112">Prerequisites</span></span>  
 <span data-ttu-id="0b5c5-113">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="0b5c5-113">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="0b5c5-114">Avant de commencer cette étape, vous devez effectuer [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md).</span><span class="sxs-lookup"><span data-stu-id="0b5c5-114">Before you begin this step you must complete [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0b5c5-115">Procédures</span><span class="sxs-lookup"><span data-stu-id="0b5c5-115">Procedures</span></span>  
 <span data-ttu-id="0b5c5-116">Dans [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md), vous avez créé un nouveau [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-116">In [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md), you created a new [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project.</span></span>  <span data-ttu-id="0b5c5-117">Si vous fermez la fenêtre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez utiliser la procédure suivante pour ouvrir le projet.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-117">If you close the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window, you can use the following procedure to open the project.</span></span>  <span data-ttu-id="0b5c5-118">Sinon, ignorez la procédure « Pour ouvrir le projet Visual Studio ».</span><span class="sxs-lookup"><span data-stu-id="0b5c5-118">Otherwise, you can skip this procedure, “To open the Visual Studio project”.</span></span>  
  
#### <a name="to-open-the-visual-studio-project"></a><span data-ttu-id="0b5c5-119">Pour ouvrir le projet Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b5c5-119">To open the Visual Studio project</span></span>  
  
1.  <span data-ttu-id="0b5c5-120">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-120">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="0b5c5-121">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-121">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="0b5c5-122">Dans le **ouvrir le projet** boîte de dialogue, cliquez sur Parcourir pour le **C:\BTSTutorials\EAISolution\EAISolution.sln** fichier solution, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-122">In the **Open Project** dialog box, browse to the **C:\BTSTutorials\EAISolution\EAISolution.sln** solution file, and then click **Open**.</span></span>  
  
 <span data-ttu-id="0b5c5-123">La procédure suivante vous permet d'ajouter un nouveau fichier de schéma de demande de réapprovisionnement de stock au projet.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-123">In the following procedure, you add a new schema file to the project for the inventory replenishment message.</span></span>  
  
#### <a name="to-add-a-new-schema-to-the-project"></a><span data-ttu-id="0b5c5-124">Pour ajouter un nouveau schéma au projet</span><span class="sxs-lookup"><span data-stu-id="0b5c5-124">To add a new schema to the project</span></span>  
  
1.  <span data-ttu-id="0b5c5-125">Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-125">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0b5c5-126">Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0b5c5-126">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="0b5c5-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="0b5c5-127">Use this</span></span>|<span data-ttu-id="0b5c5-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="0b5c5-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0b5c5-129">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-129">**Installed Templates**</span></span>|<span data-ttu-id="0b5c5-130">Cliquez sur **les fichiers de schéma**, puis cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-130">Click **Schema Files**, then click **Schema**.</span></span>|  
    |<span data-ttu-id="0b5c5-131">**Nom**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-131">**Name**</span></span>|<span data-ttu-id="0b5c5-132">Type **Request.xsd**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-132">Type **Request.xsd**.</span></span>|  
  
3.  <span data-ttu-id="0b5c5-133">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-133">Click **Add**.</span></span> <span data-ttu-id="0b5c5-134">L'arborescence du schéma et le volet XSD apparaissent.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-134">The schema tree and XSD pane appear.</span></span> <span data-ttu-id="0b5c5-135">Cette zone de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est appelée Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-135">This area of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is referred to as BizTalk Editor.</span></span> <span data-ttu-id="0b5c5-136">Le nouveau schéma s'affiche dans l'Explorateur de solutions, sous le projet EAISchemas.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-136">In addition, your new schema appears in Solution Explorer below the EAISchemas project.</span></span>  
  
     <span data-ttu-id="0b5c5-137">![Différentes parties d’un projet BizTalk](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span><span class="sxs-lookup"><span data-stu-id="0b5c5-137">![Different Parts of BizTalk Project](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span></span>  
  
#### <a name="to-add-elements-to-the-schema"></a><span data-ttu-id="0b5c5-138">Pour ajouter des éléments au schéma</span><span class="sxs-lookup"><span data-stu-id="0b5c5-138">To add elements to the schema</span></span>  
  
1.  <span data-ttu-id="0b5c5-139">Dans l’arborescence du schéma, cliquez sur le **racine** nœud.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-139">In schema tree, click the **Root** node.</span></span>  
  
2.  <span data-ttu-id="0b5c5-140">Dans le volet Propriétés, modifiez la valeur de la **nom de nœud** propriété `Request`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-140">In the Properties pane, change the value of the **Node Name** property to `Request`, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="0b5c5-141">Dans l’arborescence du schéma, cliquez sur le **demande** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-141">In schema tree, right-click the **Request** node, point to **Insert Schema Node**, and then click **Child Record**.</span></span>  
  
4.  <span data-ttu-id="0b5c5-142">Type `Header` comme nouveau nom de l’enregistrement enfant, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-142">Type `Header` as the new name for the child record, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="0b5c5-143">Répétez l’enregistrement des étapes 3 et 4 pour créer un deuxième enfant pour le **demande** nœud et nommez-le `Items`.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-143">Repeat step 3 and 4 to create a second child record for the **Request** node, and name it `Items`.</span></span>  
  
6.  <span data-ttu-id="0b5c5-144">Dans l’arborescence du schéma, cliquez sur le **en-tête** nœud **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-144">In schema tree, right-click the **Header** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
7.  <span data-ttu-id="0b5c5-145">Type `ReqID` comme nouveau nom pour l’élément et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-145">Type `ReqID` as the new name for the element, and then press ENTER.</span></span>  
  
8.  <span data-ttu-id="0b5c5-146">Élément de champ Répétez l’étape 6 et 7 pour créer un deuxième enfant pour le **en-tête** nœud et nommez-le `OrderDate`.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-146">Repeat step 6 and 7 to create a second child field element for the **Header** node, and name it `OrderDate`.</span></span>

9.  <span data-ttu-id="0b5c5-147">Élément de champ enfant Répétez l’étape 6 et 7 pour créer un tiers pour le **en-tête** nœud et nommez-le `GrandTotal`.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-147">Repeat step 6 and 7 to create a third child field element for the **Header** node, and name it `GrandTotal`.</span></span>
  
10. <span data-ttu-id="0b5c5-148">Dans l’arborescence du schéma, cliquez sur le **éléments** nœud **insérer un nœud de schémas**, puis cliquez sur **enregistrement enfant**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-148">In schema tree, right-click the **Items** node, point to **Insert Schemas Node**, and then click **Child Record**.</span></span>  
  
11. <span data-ttu-id="0b5c5-149">Type `Item` comme nouveau nom de l’enregistrement enfant, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-149">Type `Item` as the new name for the child record, and then press ENTER.</span></span>  
  
12. <span data-ttu-id="0b5c5-150">Dans l’arborescence du schéma, cliquez sur le **élément** nœud et ajoutez les éléments de champ enfant suivants :</span><span class="sxs-lookup"><span data-stu-id="0b5c5-150">In schema tree, right-click the **Item** node, and add the following child field elements:</span></span>  
  
    -   `Description`  
  
    -   `Quantity`  
  
    -   `UnitPrice`  
  
     <span data-ttu-id="0b5c5-151">Le fichier Request.xsd terminé doit ressembler à la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-151">The completed Request.xsd should look similar to the following figure.</span></span>  
  
     <span data-ttu-id="0b5c5-152">![L’Explorateur de solutions avec le schéma de demande](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")</span><span class="sxs-lookup"><span data-stu-id="0b5c5-152">![Solution Explorer with the Request Schema](../core/media/solutionexplorerwiththerequestschema.gif "SolutionExplorerwiththeRequestSchema")</span></span>  
  
 <span data-ttu-id="0b5c5-153">Lorsque vous ajoutez des nœuds à un schéma, l'Éditeur BizTalk fournit un ensemble de valeurs par défaut pour leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-153">When you add nodes to a schema, BizTalk Editor gives a set of default values for their properties.</span></span>  <span data-ttu-id="0b5c5-154">Vous devez les configurer en fonction des exigences.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-154">You must configure them based on the requirements.</span></span>  
  
#### <a name="to-configure-the-elements"></a><span data-ttu-id="0b5c5-155">Pour configurer les éléments</span><span class="sxs-lookup"><span data-stu-id="0b5c5-155">To configure the elements</span></span>  
  
1.  <span data-ttu-id="0b5c5-156">Dans l’arborescence du schéma, cliquez sur **OrderDate** pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-156">In schema tree, click **OrderDate** to select it.</span></span>  
  
2.  <span data-ttu-id="0b5c5-157">Dans le volet Propriétés, modifiez **Type de données** à **xs : DateTime**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-157">In the Properties pane, change **Data Type** to **xs:dateTime**.</span></span>  
  
3.  <span data-ttu-id="0b5c5-158">Répétez les étapes 1 et 2 pour configurer les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b5c5-158">Repeat step 1 and 2 to configure the following properties:</span></span>  
  
    |<span data-ttu-id="0b5c5-159">Élément</span><span class="sxs-lookup"><span data-stu-id="0b5c5-159">Element</span></span>|<span data-ttu-id="0b5c5-160">Propriété</span><span class="sxs-lookup"><span data-stu-id="0b5c5-160">Property</span></span>|<span data-ttu-id="0b5c5-161">Valeur</span><span class="sxs-lookup"><span data-stu-id="0b5c5-161">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="0b5c5-162">**Total général**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-162">**GrandTotal**</span></span>|<span data-ttu-id="0b5c5-163">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-163">**Data Type**</span></span>|<span data-ttu-id="0b5c5-164">**Xs : decimal**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-164">**Xs:decimal**</span></span>|  
    |<span data-ttu-id="0b5c5-165">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-165">**Item**</span></span>|<span data-ttu-id="0b5c5-166">**Max Occurs**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-166">**Max Occurs**</span></span>|<span data-ttu-id="0b5c5-167">**Non liée**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-167">**Unbounded**</span></span>|  
    |<span data-ttu-id="0b5c5-168">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-168">**Item**</span></span>|<span data-ttu-id="0b5c5-169">**Min Occurs**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-169">**Min Occurs**</span></span>|<span data-ttu-id="0b5c5-170">**1**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-170">**1**</span></span>|  
    |<span data-ttu-id="0b5c5-171">**Quantité**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-171">**Quantity**</span></span>|<span data-ttu-id="0b5c5-172">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-172">**Data Type**</span></span>|<span data-ttu-id="0b5c5-173">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="0b5c5-173">**xs:unsignedInt**</span></span>|  
  
 <span data-ttu-id="0b5c5-174">Un schéma peut comporter de nombreux éléments, mais votre application n'aura peut-être besoin que de certains d'entre eux pour traiter vos données.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-174">A schema can have many elements, but your application may only require that you use a few of them for your data processing.</span></span> <span data-ttu-id="0b5c5-175">Pour économiser les ressources de votre ordinateur,  BizTalk Server ne lit pas automatiquement tous les éléments de schéma.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-175">To save computer resources, BizTalk Server doesn't automatically read each schema element.</span></span> <span data-ttu-id="0b5c5-176">Si vous voulez que BizTalk Server lise les données d'un élément en particulier, vous devez identifier cet élément à l'aide de l'Éditeur BizTalk afin de promouvoir ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-176">If you want BizTalk Server to read data from a specific element, you must identify that element by using BizTalk Editor to promote its properties.</span></span>  
  
 <span data-ttu-id="0b5c5-177">L’orchestration que nous allons créer dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md) base sur le champ GrandTotal pour acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-177">The orchestration that we will create in [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md) will base on the GrandTotal field to route messages.</span></span>  <span data-ttu-id="0b5c5-178">Il faut donc promouvoir le champ GrandTotal.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-178">So we must promote the GrandTotal field.</span></span>  
  
#### <a name="to-promote-an-element"></a><span data-ttu-id="0b5c5-179">Pour promouvoir un élément</span><span class="sxs-lookup"><span data-stu-id="0b5c5-179">To promote an element</span></span>  
  
1.  <span data-ttu-id="0b5c5-180">Dans l’arborescence du schéma, cliquez sur **GrandTotal**, pointez sur **promouvoir**, puis cliquez sur **Promotions rapides**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-180">In Schema tree, right-click **GrandTotal**, point to **Promote**, and then click **Quick Promotions**.</span></span>  
  
2.  <span data-ttu-id="0b5c5-181">Cliquez sur **OK** pour confirmer l’ajout d’un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-181">Click **OK** to acknowledge adding a property schema.</span></span>  
  
3.  <span data-ttu-id="0b5c5-182">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-182">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="0b5c5-183">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="0b5c5-183">What did I just do?</span></span>  
 <span data-ttu-id="0b5c5-184">Cette étape vous permet de définir le schéma de la demande de réapprovisionnement de stock de l'entrepôt.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-184">In this step, you defined the warehouse inventory replenishment message schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0b5c5-185">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0b5c5-185">Next Steps</span></span>  
 <span data-ttu-id="0b5c5-186">Vous définissez le schéma du message de refus de demande.</span><span class="sxs-lookup"><span data-stu-id="0b5c5-186">You define the request decline message schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5c5-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b5c5-187">See Also</span></span>  
 <span data-ttu-id="0b5c5-188">[Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="0b5c5-188">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="0b5c5-189">[Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="0b5c5-189">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="0b5c5-190">[Étape 4 : Créer la carte](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="0b5c5-190">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="0b5c5-191">[Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="0b5c5-191">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 <span data-ttu-id="0b5c5-192">[Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md) </span><span class="sxs-lookup"><span data-stu-id="0b5c5-192">[Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md) </span></span>  
 [<span data-ttu-id="0b5c5-193">À propos des propriétés de contexte de message BizTalk</span><span class="sxs-lookup"><span data-stu-id="0b5c5-193">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)

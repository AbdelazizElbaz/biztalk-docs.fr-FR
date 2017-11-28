---
title: "Étape 4 : Créer le mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7f1f6d-0e57-4a65-b91d-c81fcc832961
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67128880233a04b6b1573f11ff5229cebe328b25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-map"></a><span data-ttu-id="8b69a-102">Étape 4 : création du mappage</span><span class="sxs-lookup"><span data-stu-id="8b69a-102">Step 4: Create the Map</span></span>
<span data-ttu-id="8b69a-103">![L’étape 4 de 5](../core/media/step-4of5.gif "Step_4of5")</span><span class="sxs-lookup"><span data-stu-id="8b69a-103">![Step 4 of 5](../core/media/step-4of5.gif "Step_4of5")</span></span>  
  
 <span data-ttu-id="8b69a-104">**Durée :** 6 minutes</span><span class="sxs-lookup"><span data-stu-id="8b69a-104">**Time to complete:** 6 minutes</span></span>  
  
 <span data-ttu-id="8b69a-105">**Objectif :** dans cette étape, vous créez un mappage qui transforme le message de demande de message RequestDecline.</span><span class="sxs-lookup"><span data-stu-id="8b69a-105">**Objective:** In this step, you create a map that transforms Request message to RequestDecline message.</span></span>  
  
 <span data-ttu-id="8b69a-106">**Objectif :** le mappage garantit que le numéro d’ID de demande et le total général sont inclus dans le message de refus de demande renvoyé au système de l’inventaire de l’entrepôt.</span><span class="sxs-lookup"><span data-stu-id="8b69a-106">**Purpose:** The map ensures that the request ID number and the grand total are included in the request decline message returned to the warehouse inventory system.</span></span> <span data-ttu-id="8b69a-107">Le Mappeur BizTalk permet de lier les champs dans un message entrant aux champs définis pour le message sortant.</span><span class="sxs-lookup"><span data-stu-id="8b69a-107">You use BizTalk Mapper to link fields in an incoming message to fields defined for the outgoing message.</span></span> <span data-ttu-id="8b69a-108">Cette opération est nécessaire car ces deux messages n'ont pas la même structure de schéma.</span><span class="sxs-lookup"><span data-stu-id="8b69a-108">This is necessary because these two messages do not have the same schema structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b69a-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8b69a-109">Prerequisites</span></span>  
 <span data-ttu-id="8b69a-110">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="8b69a-110">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="8b69a-111">Avant de commencer cette étape, vous devez effectuer [étape 2 : création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) et [étape 3 : créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8b69a-111">Before you begin this step you must complete [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) and [Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8b69a-112">Procédures</span><span class="sxs-lookup"><span data-stu-id="8b69a-112">Procedures</span></span>  
 <span data-ttu-id="8b69a-113">Le mappage dépend des schémas Request et RequestDecline.</span><span class="sxs-lookup"><span data-stu-id="8b69a-113">The map depends on the Request schema and the RequestDecline schema.</span></span>  <span data-ttu-id="8b69a-114">Avant d'utiliser les schémas sur un mappage, vous devez compiler le projet avec le schéma.</span><span class="sxs-lookup"><span data-stu-id="8b69a-114">You much compile the project with the schema before you can use them on a map.</span></span>  
  
#### <a name="to-compile-the-eaischemas-project"></a><span data-ttu-id="8b69a-115">Pour compiler le projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="8b69a-115">To compile the EAISchemas project</span></span>  
  
-   <span data-ttu-id="8b69a-116">Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-116">In Solution Explorer, right-click **EAISchemas**, and then click **Build**.</span></span>  
  
#### <a name="to-create-the-map"></a><span data-ttu-id="8b69a-117">Pour créer le mappage</span><span class="sxs-lookup"><span data-stu-id="8b69a-117">To create the map</span></span>  
  
1.  <span data-ttu-id="8b69a-118">Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-118">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="8b69a-119">Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b69a-119">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8b69a-120">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8b69a-120">Use this</span></span>|<span data-ttu-id="8b69a-121">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8b69a-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8b69a-122">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="8b69a-122">**Installed Templates**</span></span>|<span data-ttu-id="8b69a-123">Cliquez sur **les fichiers de mappage**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-123">Click **Map Files**, and then click **Map**.</span></span>|  
    |<span data-ttu-id="8b69a-124">**Nom**</span><span class="sxs-lookup"><span data-stu-id="8b69a-124">**Name**</span></span>|<span data-ttu-id="8b69a-125">Type **MapToReqDecline.btm**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-125">Type **MapToReqDecline.btm**.</span></span>|  
  
3.  <span data-ttu-id="8b69a-126">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-126">Click **Add**.</span></span>  
  
     <span data-ttu-id="8b69a-127">La figure suivante illustre le schéma source, le schéma de destination et la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="8b69a-127">The following figure shows the Source Schema, Destination Schema, and Mapper Grid.</span></span>  
  
     <span data-ttu-id="8b69a-128">![Mappage MapToReqDenied](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")</span><span class="sxs-lookup"><span data-stu-id="8b69a-128">![MapToReqDenied map](../core/media/tut1-maptoreqden1.jpg "Tut1_MapToReqDen1")</span></span>  
  
4.  <span data-ttu-id="8b69a-129">Dans le **schéma Source** volet, cliquez sur **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-129">In the **Source Schema** pane, click **Open Source Schema**.</span></span>  
  
5.  <span data-ttu-id="8b69a-130">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez **EAISchemas**, développez **schémas**, cliquez sur **EAISchemas.Request**, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-130">In the **BizTalk Type Picker** dialog box, expand **EAISchemas**, expand **Schemas**, click **EAISchemas.Request**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8b69a-131">Dans le **schéma Source** volet, avec le bouton droit  **\<schéma >**, puis cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-131">In the **Source Schema** pane, right-click **\<Schema>**, and then click **Expand Tree Node**.</span></span>  
  
7.  <span data-ttu-id="8b69a-132">Dans le **schéma de Destination** volet, cliquez sur **ouvrir le schéma de Destination**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-132">In the **Destination Schema** pane, click **Open Destination Schema**.</span></span>  
  
8.  <span data-ttu-id="8b69a-133">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez **EAISchemas**, développez **schémas**, cliquez sur **EAISchemas.RequestDecline**, puis Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-133">In the **BizTalk Type Picker** dialog box, expand **EAISchemas**, expand **Schemas**, click **EAISchemas.RequestDecline**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8b69a-134">Dans le **schéma de Destination** volet, avec le bouton droit  **\<schéma >**, puis cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="8b69a-134">In the **Destination Schema** pane, right-click **\<Schema>**, and then click **Expand Tree Node**.</span></span>  
  
10. <span data-ttu-id="8b69a-135">Dans le **schéma Source** volet, faites glisser le **ReqID** au champ la **ReqID** dans les **schéma de Destination** volet.</span><span class="sxs-lookup"><span data-stu-id="8b69a-135">In the **Source Schema** pane, drag the **ReqID** field to the **ReqID** in the **Destination Schema** pane.</span></span> <span data-ttu-id="8b69a-136">Une ligne reliant les deux éléments apparaît.</span><span class="sxs-lookup"><span data-stu-id="8b69a-136">A line appears connecting the two elements.</span></span>  
  
11. <span data-ttu-id="8b69a-137">Dans le **schéma Source** volet, faites glisser le **GrandTotal** au champ la **GrandTotal** champ dans le **schéma de Destination** volet pour mapper les données à partir d’un schéma à l’autre.</span><span class="sxs-lookup"><span data-stu-id="8b69a-137">In the **Source Schema** pane, drag the **GrandTotal** field to the **GrandTotal** field in the **Destination Schema** pane to map the data from one schema to the other.</span></span>  
  
12. <span data-ttu-id="8b69a-138">Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer votre travail.</span><span class="sxs-lookup"><span data-stu-id="8b69a-138">On the **File** menu, click **Save All** to save your work.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8b69a-139">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="8b69a-139">What did I just do?</span></span>  
 <span data-ttu-id="8b69a-140">Au cours de cette étape, vous avez créé un mappage qui transforme le message Request en message RequestDecline.</span><span class="sxs-lookup"><span data-stu-id="8b69a-140">In this step, you created a map that transforms Request message to RequestDecline message.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b69a-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8b69a-141">Next Steps</span></span>  
 <span data-ttu-id="8b69a-142">Créez le projet EAISchemas.</span><span class="sxs-lookup"><span data-stu-id="8b69a-142">You build the EAISchemas project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b69a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b69a-143">See Also</span></span>  
 <span data-ttu-id="8b69a-144">[Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="8b69a-144">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="8b69a-145">[Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="8b69a-145">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="8b69a-146">[Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="8b69a-146">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="8b69a-147">[Étape 4 : Créer la carte](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="8b69a-147">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="8b69a-148">[Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="8b69a-148">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 [<span data-ttu-id="8b69a-149">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8b69a-149">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)
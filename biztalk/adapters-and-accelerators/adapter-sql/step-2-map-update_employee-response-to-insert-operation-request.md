---
title: "Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d12014a-0147-4227-88fa-0b290eff4cce
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29a7cef00860f32aa2a493cc401e5d49d223ad3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-map-the-updateemployee-response-message-to-insert-operation-request-message"></a><span data-ttu-id="63325-102">Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération</span><span class="sxs-lookup"><span data-stu-id="63325-102">Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message</span></span>
<span data-ttu-id="63325-103">![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="63325-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="63325-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="63325-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="63325-105">**Objectif :** dans cette étape, vous créez le message de demande pour effectuer une opération d’insertion sur la **Purchase_Order** de table, puis mapper le message de réponse pour le **UPDATE_EMPLOYEE** stockées procédure pour le message de demande pour l’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="63325-105">**Objective:** In this step, you create the request message to perform an Insert operation on the **Purchase_Order** table and then map the response message for the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation.</span></span> <span data-ttu-id="63325-106">En procédant ainsi, vous passez des valeurs dans le message de réponse à insérer dans le **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="63325-106">By doing so, you pass on the values in the response message to be inserted in the **Purchase_Order** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63325-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="63325-107">Prerequisites</span></span>  
 <span data-ttu-id="63325-108">Vous devez avoir terminé [étape 1 : créer le Message de demande pour l’opération Insert sur la Table de Purchase_Order](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md).</span><span class="sxs-lookup"><span data-stu-id="63325-108">You must have completed [Step 1: Create the Request Message for Insert Operation on Purchase_Order Table](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md).</span></span>  
  
### <a name="to-map-the-messages"></a><span data-ttu-id="63325-109">Pour mapper les messages</span><span class="sxs-lookup"><span data-stu-id="63325-109">To map the messages</span></span>  
  
1.  <span data-ttu-id="63325-110">À l’orchestration existante, dans le **insérer** bloquer de la **décider** mettre en forme, sous la **ReceiveUpdateResponse** mettre en forme, ajouter un **AssignationduMessage** forme.</span><span class="sxs-lookup"><span data-stu-id="63325-110">To the existing orchestration, in the **Insert** block of the **Decide** shape, under the **ReceiveUpdateResponse** shape, add a **Message Assignment** shape.</span></span> <span data-ttu-id="63325-111">Dans la boîte à outils, faites glisser le **assignation du Message** forme à l’espace indiqué.</span><span class="sxs-lookup"><span data-stu-id="63325-111">From the Toolbox, drag the **Message Assignment** shape to the space indicated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63325-112">Lorsque vous déposez le **assignation du Message** forme sur l’aire de conception, le Concepteur d’Orchestration crée la forme **construire un Message** forme pour vous.</span><span class="sxs-lookup"><span data-stu-id="63325-112">When you drop the **Message Assignment** shape onto the design surface, Orchestration Designer creates the enclosing **Construct Message** shape for you.</span></span>  
  
2.  <span data-ttu-id="63325-113">Sur l’aire de conception, cliquez sur le **ConstructMessage_1** mettre en forme, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="63325-113">On the design surface, right-click the **ConstructMessage_1** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="63325-114">Dans le **propriétés** volet pour le **ConstructMessage_1** forme, spécifiez les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="63325-114">In the **Properties** pane for the **ConstructMessage_1** shape, specify the following values.</span></span>  
  
    |<span data-ttu-id="63325-115">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="63325-115">Set this property</span></span>|<span data-ttu-id="63325-116">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="63325-116">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="63325-117">**Messages construits**</span><span class="sxs-lookup"><span data-stu-id="63325-117">**Messages Constructed**</span></span>|<span data-ttu-id="63325-118">InsertPO</span><span class="sxs-lookup"><span data-stu-id="63325-118">InsertPO</span></span>|  
    |<span data-ttu-id="63325-119">**Nom**</span><span class="sxs-lookup"><span data-stu-id="63325-119">**Name**</span></span>|<span data-ttu-id="63325-120">ConstructInsertMessage</span><span class="sxs-lookup"><span data-stu-id="63325-120">ConstructInsertMessage</span></span>|  
  
4.  <span data-ttu-id="63325-121">Double-cliquez sur le **MessageAssignment** forme pour ouvrir la **Éditeur d’Expression BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="63325-121">Double-click the **MessageAssignment** shape to open the **BizTalk Expression Editor**.</span></span>  
  
5.  <span data-ttu-id="63325-122">Dans le **Éditeur d’Expression BizTalk**, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="63325-122">In the **BizTalk Expression Editor**, add the following:</span></span>  
  
    ```  
    InsertPO = UpdatePOMessageCreator.UpdatePOMessageCreator.XMLMessageCreator();  
    InsertPO(WCF.Action) = "TableOp/Insert/dbo/Purchase_Order";  
    ```  
  
     <span data-ttu-id="63325-123">Ici, **InsertPO** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour l’envoi de messages de demande pour l’opération d’insertion la **Purchase_Order**table.</span><span class="sxs-lookup"><span data-stu-id="63325-123">Here, **InsertPO** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) for sending request messages for Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="63325-124">Dans le **MessageAssignment** forme, vous appelez le **UpdatePOMessageCreator** classe pour créer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="63325-124">In the **MessageAssignment** shape, you invoke the **UpdatePOMessageCreator** class to create a request message.</span></span> <span data-ttu-id="63325-125">En outre, vous définir l’action de WCF pour le message de demande.</span><span class="sxs-lookup"><span data-stu-id="63325-125">Also, you set the WCF action for the request message.</span></span>  
  
6.  <span data-ttu-id="63325-126">Dans le **construire un Message** forme et après le **assignation du Message** mettre en forme, ajouter un **transformer** forme.</span><span class="sxs-lookup"><span data-stu-id="63325-126">Within the **Construct Message** shape and after the **Message Assignment** shape, add a **Transform** shape.</span></span>  
  
7.  <span data-ttu-id="63325-127">Dans le **transformer la Configuration** boîte de dialogue, dans le volet gauche, sous la **transformer** étiquette, cliquez sur **Source**.</span><span class="sxs-lookup"><span data-stu-id="63325-127">In the **Transform Configuration** dialog box, from the left pane, under the **Transform** label, click **Source**.</span></span>  
  
8.  <span data-ttu-id="63325-128">À partir de la **transformation Source** sur la droite, cliquez sur l’espace sous le **nom de la Variable**, puis sélectionnez **UpdateEmployeeResponse**.</span><span class="sxs-lookup"><span data-stu-id="63325-128">From the **Source Transform** box on the right, click the space under the **Variable Name**, and then select **UpdateEmployeeResponse**.</span></span>  
  
     <span data-ttu-id="63325-129">![Sélectionner le schéma source pour le mappage de](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")</span><span class="sxs-lookup"><span data-stu-id="63325-129">![Pick the source schema for the mapping](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")</span></span>  
  
9. <span data-ttu-id="63325-130">Dans le **transformer la Configuration** boîte de dialogue, dans le volet gauche, sous la **transformer** étiquette, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="63325-130">In the **Transform Configuration** dialog box, from the left pane, under the **Transform** label, click **Destination**.</span></span>  
  
10. <span data-ttu-id="63325-131">À partir de la **transformation de Destination** sur la droite, cliquez sur l’espace sous le **nom de la Variable**, puis sélectionnez **InsertPO**.</span><span class="sxs-lookup"><span data-stu-id="63325-131">From the **Destination Transform** box on the right, click the space under the **Variable Name**, and then select **InsertPO**.</span></span>  
  
     <span data-ttu-id="63325-132">![Sélectionner le schéma de destination pour le mappage de](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")</span><span class="sxs-lookup"><span data-stu-id="63325-132">![Pick the destination schema for mapping](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")</span></span>  
  
11. <span data-ttu-id="63325-133">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63325-133">Click **OK**.</span></span> <span data-ttu-id="63325-134">Le fichier de mappage s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="63325-134">The map file opens.</span></span>  
  
12. <span data-ttu-id="63325-135">Développez les nœuds dans les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="63325-135">Expand the nodes in the source and destination schemas.</span></span>  
  
13. <span data-ttu-id="63325-136">Mapper le Employee_ID et nommer les champs dans les deux schémas.</span><span class="sxs-lookup"><span data-stu-id="63325-136">Map the Employee_ID and name fields in both the schemas.</span></span>  
  
    -   <span data-ttu-id="63325-137">Mappage de la **Employee_ID** nœud dans le schéma source (UPDATE_EMPLOYEEResponse) pour le **Employee_ID** nœud dans le schéma de destination (Insert).</span><span class="sxs-lookup"><span data-stu-id="63325-137">Map the **Employee_ID** node in the source schema (UPDATE_EMPLOYEEResponse) to the **Employee_ID** node in the destination schema (Insert).</span></span>  
  
    -   <span data-ttu-id="63325-138">Mappage de la **nom** nœud dans le schéma source vers le **Employee_Name** dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="63325-138">Map the **Name** node in the source schema to the **Employee_Name** in the destination schema.</span></span>  
  
     <span data-ttu-id="63325-139">La figure suivante illustre les schémas mappés.</span><span class="sxs-lookup"><span data-stu-id="63325-139">The following figure shows the mapped schemas.</span></span>  
  
     <span data-ttu-id="63325-140">![Mapper les schémas source et de destination](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")</span><span class="sxs-lookup"><span data-stu-id="63325-140">![Map the source and destination schemas](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")</span></span>  
  
     <span data-ttu-id="63325-141">Enregistrez et fermez le mappage.</span><span class="sxs-lookup"><span data-stu-id="63325-141">Save and close the map.</span></span>  
  
14. <span data-ttu-id="63325-142">L’illustration suivante montre l’orchestration en cours.</span><span class="sxs-lookup"><span data-stu-id="63325-142">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="63325-143">![Orchestration avec la forme transformer](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")</span><span class="sxs-lookup"><span data-stu-id="63325-143">![Orchestration with the transform shape](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="63325-144">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="63325-144">What did I just do?</span></span>  
 <span data-ttu-id="63325-145">Dans cette étape, vous avez créé un message pour insérer des enregistrements dans la **Purchase_Order** table et ensuite mappé le message de réponse à partir de la **UPDATE_EMPLOYEE** procédure stockée pour le message de demande pour l’insertion opération.</span><span class="sxs-lookup"><span data-stu-id="63325-145">In this step, you created a message to insert records into the **Purchase_Order** table and then mapped the response message from the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="63325-146">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="63325-146">Next Steps</span></span>  
 <span data-ttu-id="63325-147">Vous envoyez le message de demande pour effectuer une opération d’insertion sur la **Purchase_Order** de table et de recevoir une réponse, comme décrit dans [étape 3 : envoyer le Message de demande pour insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span><span class="sxs-lookup"><span data-stu-id="63325-147">You send the request message to perform an Insert operation on the **Purchase_Order** table and receive a response, as described in [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63325-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63325-148">See Also</span></span>  
 <span data-ttu-id="63325-149">[Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md) </span><span class="sxs-lookup"><span data-stu-id="63325-149">[Step 1: Create the Request Message for Insert Operation on Purchase_Order Table](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md) </span></span>  
 [<span data-ttu-id="63325-150">Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat</span><span class="sxs-lookup"><span data-stu-id="63325-150">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)
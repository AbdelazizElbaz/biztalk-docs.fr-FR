---
title: "Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a8a8906-7c7d-437c-9f04-345ad4ac460e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db97afa0de19e15e5005e5647279365ea6ba023b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-send-the-request-message-to-insert-records-and-receive-a-response"></a><span data-ttu-id="8f476-102">Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="8f476-102">Step 3: Send the Request Message to Insert Records and Receive a Response</span></span>
<span data-ttu-id="8f476-103">![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="8f476-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="8f476-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="8f476-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="8f476-105">**Objectif :** dans cette étape, vous envoyez le message de demande pour insérer des enregistrements dans la **Purchase_Order** de table et de recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="8f476-105">**Objective:** In this step, you send the request message to insert records into the **Purchase_Order** table and receive a response.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f476-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8f476-106">Prerequisites</span></span>  
 <span data-ttu-id="8f476-107">Vous devez avoir terminé [étape 2 : mapper le Message de réponse UPDATE_EMPLOYEE au Message de demande d’opération Insert](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md).</span><span class="sxs-lookup"><span data-stu-id="8f476-107">You must have completed [Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md).</span></span>  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a><span data-ttu-id="8f476-108">Pour envoyer le message de demande et de recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="8f476-108">To send the request message and receive a response</span></span>  
  
1.  <span data-ttu-id="8f476-109">Ajouter les formes suivantes à l’orchestration sous la **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="8f476-109">Add the following shapes to the orchestration under the **Construct Message** shape.</span></span>  
  
    |<span data-ttu-id="8f476-110">Graphique à base de formes</span><span class="sxs-lookup"><span data-stu-id="8f476-110">Shape</span></span>|<span data-ttu-id="8f476-111">Type de forme</span><span class="sxs-lookup"><span data-stu-id="8f476-111">Shape Type</span></span>|<span data-ttu-id="8f476-112">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8f476-112">Properties</span></span>|  
    |-----------|----------------|----------------|  
    |<span data-ttu-id="8f476-113">SendInsertMessage</span><span class="sxs-lookup"><span data-stu-id="8f476-113">SendInsertMessage</span></span>|<span data-ttu-id="8f476-114">Send</span><span class="sxs-lookup"><span data-stu-id="8f476-114">Send</span></span>|<span data-ttu-id="8f476-115">-Définissez **Message** à *InsertPO*</span><span class="sxs-lookup"><span data-stu-id="8f476-115">-   Set **Message** to *InsertPO*</span></span><br /><span data-ttu-id="8f476-116">-Définissez **nom** à *SendInsertMessage*</span><span class="sxs-lookup"><span data-stu-id="8f476-116">-   Set **Name** to *SendInsertMessage*</span></span>|  
    |<span data-ttu-id="8f476-117">ReceiveInsertResponse</span><span class="sxs-lookup"><span data-stu-id="8f476-117">ReceiveInsertResponse</span></span>|<span data-ttu-id="8f476-118">Recevoir</span><span class="sxs-lookup"><span data-stu-id="8f476-118">Receive</span></span>|<span data-ttu-id="8f476-119">-Définissez **activer** à *False*</span><span class="sxs-lookup"><span data-stu-id="8f476-119">-   Set **Activate** to *False*</span></span><br /><span data-ttu-id="8f476-120">-Définissez **Message** à *InsertPOResponse*</span><span class="sxs-lookup"><span data-stu-id="8f476-120">-   Set **Message** to *InsertPOResponse*</span></span><br /><span data-ttu-id="8f476-121">-Définissez **nom** à *ReceiveInsertResponse*</span><span class="sxs-lookup"><span data-stu-id="8f476-121">-   Set **Name** to *ReceiveInsertResponse*</span></span>|  
    |<span data-ttu-id="8f476-122">SaveInsertResponse</span><span class="sxs-lookup"><span data-stu-id="8f476-122">SaveInsertResponse</span></span>|<span data-ttu-id="8f476-123">Send</span><span class="sxs-lookup"><span data-stu-id="8f476-123">Send</span></span>|<span data-ttu-id="8f476-124">-Définissez **Message** à *InsertPOResponse*</span><span class="sxs-lookup"><span data-stu-id="8f476-124">-   Set **Message** to *InsertPOResponse*</span></span><br /><span data-ttu-id="8f476-125">-Définissez **nom** à *SaveInsertResponse*</span><span class="sxs-lookup"><span data-stu-id="8f476-125">-   Set **Name** to *SaveInsertResponse*</span></span>|  
  
2.  <span data-ttu-id="8f476-126">Modifier la **SQLOutboundPort** que vous avez créé dans [étape 2 : envoyer le Message de demande à SQL Server et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).</span><span class="sxs-lookup"><span data-stu-id="8f476-126">Modify the **SQLOutboundPort** you created in [Step 2: Send the Request Message to SQL Server and Receive Response](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).</span></span>  
  
    1.  <span data-ttu-id="8f476-127">Cliquez sur le port dans le Concepteur d’Orchestration, puis cliquez sur **nouvelle opération**.</span><span class="sxs-lookup"><span data-stu-id="8f476-127">Right-click the port in the Orchestration Designer, and then click **New Operation**.</span></span> <span data-ttu-id="8f476-128">Les modifications de la forme port pour ajouter une nouvelle opération **Operation_1**.</span><span class="sxs-lookup"><span data-stu-id="8f476-128">The port shape changes to add a new operation, **Operation_1**.</span></span>  
  
    2.  <span data-ttu-id="8f476-129">Cliquez sur **Operation_1** et dans la fenêtre Propriétés, modifiez la valeur d’identificateur aux **InsertPO**.</span><span class="sxs-lookup"><span data-stu-id="8f476-129">Click **Operation_1** and in the properties window, change the value of Identifier to **InsertPO**.</span></span>  
  
3.  <span data-ttu-id="8f476-130">Ajouter un port d’envoi unidirectionnel à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8f476-130">Add a one-way send port to the orchestration.</span></span> <span data-ttu-id="8f476-131">Vous allez utiliser ce port pour envoyer le message de réponse pour l’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8f476-131">You will use this port to send the response message for the Insert operation.</span></span> <span data-ttu-id="8f476-132">Définissez les propriétés suivantes pour le port.</span><span class="sxs-lookup"><span data-stu-id="8f476-132">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="8f476-133">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="8f476-133">Set this property</span></span>|<span data-ttu-id="8f476-134">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="8f476-134">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="8f476-135">**Direction de communication**</span><span class="sxs-lookup"><span data-stu-id="8f476-135">**Communication Direction**</span></span>|<span data-ttu-id="8f476-136">Send</span><span class="sxs-lookup"><span data-stu-id="8f476-136">Send</span></span>|  
    |<span data-ttu-id="8f476-137">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="8f476-137">**Communication Pattern**</span></span>|<span data-ttu-id="8f476-138">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="8f476-138">One-Way</span></span>|  
    |<span data-ttu-id="8f476-139">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="8f476-139">**Identifier**</span></span>|<span data-ttu-id="8f476-140">SaveResponsePort</span><span class="sxs-lookup"><span data-stu-id="8f476-140">SaveResponsePort</span></span>|  
  
     <span data-ttu-id="8f476-141">En outre, modifier le nom de l’opération à partir de Operation_1 pour **InsertPO**.</span><span class="sxs-lookup"><span data-stu-id="8f476-141">Also, change the operation name from Operation_1 to **InsertPO**.</span></span>  
  
4.  <span data-ttu-id="8f476-142">Connectez le port à des formes action.</span><span class="sxs-lookup"><span data-stu-id="8f476-142">Connect the port to action shapes.</span></span> <span data-ttu-id="8f476-143">Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="8f476-143">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f476-144">Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action.</span><span class="sxs-lookup"><span data-stu-id="8f476-144">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="8f476-145">Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.</span><span class="sxs-lookup"><span data-stu-id="8f476-145">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
     <span data-ttu-id="8f476-146">Connecter les ports et les formes d’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f476-146">Connect the ports and action shapes as follows:</span></span>  
  
    -   <span data-ttu-id="8f476-147">Se connecter le **SendInsertMessage** forme action pour le **demande** gérer de la **InsertPO** opération de la **SQLOutboundPort**.</span><span class="sxs-lookup"><span data-stu-id="8f476-147">Connect the **SendInsertMessage** action shape to the **Request** handle of the **InsertPO** operation of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="8f476-148">Connecter le **ReceiveInsertResponse** forme action pour le **réponse** gérer de la **InsertPO** opération de la **SQLOutboundPort**.</span><span class="sxs-lookup"><span data-stu-id="8f476-148">Connect the **ReceiveInsertResponse** action shape to the **Response** handle of the **InsertPO** operation of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="8f476-149">Connecter le **SaveInsertResponse** forme action pour le **demande** gérer de la **SaveResponsePort**.</span><span class="sxs-lookup"><span data-stu-id="8f476-149">Connect the **SaveInsertResponse** action shape to the **Request** handle of the **SaveResponsePort**.</span></span>  
  
5.  <span data-ttu-id="8f476-150">L’illustration suivante montre l’orchestration en cours.</span><span class="sxs-lookup"><span data-stu-id="8f476-150">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="8f476-151">![Terminer l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")</span><span class="sxs-lookup"><span data-stu-id="8f476-151">![Complete orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8f476-152">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="8f476-152">What did I just do?</span></span>  
 <span data-ttu-id="8f476-153">Vous avez envoyé la demande d’insérer des enregistrements dans la **Purchase_Order** de table et de recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="8f476-153">You sent the request to insert records into the **Purchase_Order** table and receive a response.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f476-154">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8f476-154">Next Steps</span></span>  
 <span data-ttu-id="8f476-155">Vous générez le projet, comme décrit dans [étape 4 : créer le projet](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md).</span><span class="sxs-lookup"><span data-stu-id="8f476-155">You build the project, as described in [Step 4: Build the Project](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f476-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f476-156">See Also</span></span>  
 <span data-ttu-id="8f476-157">[Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span><span class="sxs-lookup"><span data-stu-id="8f476-157">[Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span></span>  
 <span data-ttu-id="8f476-158">[Étape 4 : Création du projet](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md) </span><span class="sxs-lookup"><span data-stu-id="8f476-158">[Step 4: Build the Project](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md) </span></span>  
 [<span data-ttu-id="8f476-159">Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat</span><span class="sxs-lookup"><span data-stu-id="8f476-159">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)
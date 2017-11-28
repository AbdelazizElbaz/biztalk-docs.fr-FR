---
title: "Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864d2174-d54b-4383-92bf-f6808a2a904b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce820ab6a1914e44239313588eaaefeb696e61d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a><span data-ttu-id="e01be-102">Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse</span><span class="sxs-lookup"><span data-stu-id="e01be-102">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>
<span data-ttu-id="e01be-103">![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="e01be-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="e01be-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="e01be-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="e01be-105">**Objectif :** dans cette étape, vous envoyez le message de demande pour exécuter le **UPDATE_EMPLOYEE** procédure stockée et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="e01be-105">**Objective:** In this step, you send the request message to execute the **UPDATE_EMPLOYEE** stored procedure and receive the response.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e01be-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e01be-106">Prerequisites</span></span>  
 <span data-ttu-id="e01be-107">Vous devez avoir terminé [étape 1 : créer le Message de demande pour la procédure stockée UPDATE_EMPLOYEE](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="e01be-107">You must have completed [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span></span>  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a><span data-ttu-id="e01be-108">Pour envoyer le message de demande et de recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="e01be-108">To send the request message and receive a response</span></span>  
  
1.  <span data-ttu-id="e01be-109">À l’orchestration existante, sous la **insérer** bloquer de la **décider** mettre en forme, ajouter un **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="e01be-109">To the existing orchestration, under the **Insert** block of the **Decide** shape, add a **Message Assignment** shape.</span></span> <span data-ttu-id="e01be-110">Dans la boîte à outils, faites glisser le **assignation du Message** forme à l’espace indiqué.</span><span class="sxs-lookup"><span data-stu-id="e01be-110">From the Toolbox, drag the **Message Assignment** shape to the space indicated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e01be-111">Lorsque vous déposez le **assignation du Message** forme sur l’aire de conception, le Concepteur d’Orchestration crée la forme **construire un Message** forme pour vous.</span><span class="sxs-lookup"><span data-stu-id="e01be-111">When you drop the **Message Assignment** shape onto the design surface, Orchestration Designer creates the enclosing **Construct Message** shape for you.</span></span>  
  
2.  <span data-ttu-id="e01be-112">Sur l’aire de conception, cliquez sur le **ConstructMessage_1** mettre en forme, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e01be-112">On the design surface, right-click the **ConstructMessage_1** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="e01be-113">Dans le **propriétés** volet pour le **ConstructMessage_1** forme, spécifiez les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="e01be-113">In the **Properties** pane for the **ConstructMessage_1** shape, specify the following values.</span></span>  
  
    |<span data-ttu-id="e01be-114">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="e01be-114">Set this property</span></span>|<span data-ttu-id="e01be-115">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="e01be-115">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="e01be-116">**Messages construits**</span><span class="sxs-lookup"><span data-stu-id="e01be-116">**Messages Constructed**</span></span>|<span data-ttu-id="e01be-117">UpdateEmployee</span><span class="sxs-lookup"><span data-stu-id="e01be-117">UpdateEmployee</span></span>|  
    |<span data-ttu-id="e01be-118">**Nom**</span><span class="sxs-lookup"><span data-stu-id="e01be-118">**Name**</span></span>|<span data-ttu-id="e01be-119">ConstructRequestMessage</span><span class="sxs-lookup"><span data-stu-id="e01be-119">ConstructRequestMessage</span></span>|  
  
4.  <span data-ttu-id="e01be-120">Double-cliquez sur le **MessageAssignment** forme pour ouvrir la **Éditeur d’Expression BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="e01be-120">Double-click the **MessageAssignment** shape to open the **BizTalk Expression Editor**.</span></span>  
  
5.  <span data-ttu-id="e01be-121">Dans le **Éditeur d’Expression BizTalk**, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e01be-121">In the **BizTalk Expression Editor**, add the following:</span></span>  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     <span data-ttu-id="e01be-122">Ici, **UpdateEmployee** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour l’envoi de messages de demande **UPDATE_EMPLOYEE** stockées procédure.</span><span class="sxs-lookup"><span data-stu-id="e01be-122">Here, **UpdateEmployee** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) for sending request messages for **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="e01be-123">Dans le **MessageAssignment** forme, vous appelez le **UpdateEmployeeMessageCreator** classe pour créer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="e01be-123">In the **MessageAssignment** shape, you invoke the **UpdateEmployeeMessageCreator** class to create a request message.</span></span> <span data-ttu-id="e01be-124">En outre, vous définir l’action de WCF pour le message de demande.</span><span class="sxs-lookup"><span data-stu-id="e01be-124">Also, you set the WCF action for the request message.</span></span>  
  
6.  <span data-ttu-id="e01be-125">Ajouter les formes suivantes à l’orchestration sous la **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="e01be-125">Add the following shapes to the orchestration under the **Message Assignment** shape.</span></span>  
  
    |<span data-ttu-id="e01be-126">Graphique à base de formes</span><span class="sxs-lookup"><span data-stu-id="e01be-126">Shape</span></span>|<span data-ttu-id="e01be-127">Type de forme</span><span class="sxs-lookup"><span data-stu-id="e01be-127">Shape Type</span></span>|<span data-ttu-id="e01be-128">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e01be-128">Properties</span></span>|  
    |-----------|----------------|----------------|  
    |<span data-ttu-id="e01be-129">SendUpdateMessage</span><span class="sxs-lookup"><span data-stu-id="e01be-129">SendUpdateMessage</span></span>|<span data-ttu-id="e01be-130">Send</span><span class="sxs-lookup"><span data-stu-id="e01be-130">Send</span></span>|<span data-ttu-id="e01be-131">-Définissez **Message** à *UpdateEmployee*</span><span class="sxs-lookup"><span data-stu-id="e01be-131">-   Set **Message** to *UpdateEmployee*</span></span><br /><span data-ttu-id="e01be-132">-Définissez **nom** à *SendUpdateMessage*</span><span class="sxs-lookup"><span data-stu-id="e01be-132">-   Set **Name** to *SendUpdateMessage*</span></span>|  
    |<span data-ttu-id="e01be-133">ReceiveUpdateResponse</span><span class="sxs-lookup"><span data-stu-id="e01be-133">ReceiveUpdateResponse</span></span>|<span data-ttu-id="e01be-134">Recevoir</span><span class="sxs-lookup"><span data-stu-id="e01be-134">Receive</span></span>|<span data-ttu-id="e01be-135">-Définissez **activer** à *False*</span><span class="sxs-lookup"><span data-stu-id="e01be-135">-   Set **Activate** to *False*</span></span><br /><span data-ttu-id="e01be-136">-Définissez **Message** à *UpdateEmployeeResponse*</span><span class="sxs-lookup"><span data-stu-id="e01be-136">-   Set **Message** to *UpdateEmployeeResponse*</span></span><br /><span data-ttu-id="e01be-137">-Définissez **nom** à *ReceiveUpdateResponse*</span><span class="sxs-lookup"><span data-stu-id="e01be-137">-   Set **Name** to *ReceiveUpdateResponse*</span></span>|  
  
7.  <span data-ttu-id="e01be-138">Ajouter un port d’envoi requête-réponse à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="e01be-138">Add a request-response send port to the orchestration.</span></span> <span data-ttu-id="e01be-139">Vous allez utiliser ce port pour envoyer des messages de demande à SQL Server et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="e01be-139">You will use this port to send request messages to the SQL Server and receive response.</span></span> <span data-ttu-id="e01be-140">Définissez les propriétés suivantes pour le port.</span><span class="sxs-lookup"><span data-stu-id="e01be-140">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="e01be-141">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="e01be-141">Set this property</span></span>|<span data-ttu-id="e01be-142">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="e01be-142">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="e01be-143">**Direction de communication**</span><span class="sxs-lookup"><span data-stu-id="e01be-143">**Communication Direction**</span></span>|<span data-ttu-id="e01be-144">Envoi-Réception</span><span class="sxs-lookup"><span data-stu-id="e01be-144">Send-Receive</span></span>|  
    |<span data-ttu-id="e01be-145">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="e01be-145">**Communication Pattern**</span></span>|<span data-ttu-id="e01be-146">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="e01be-146">Request-Response</span></span>|  
    |<span data-ttu-id="e01be-147">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="e01be-147">**Identifier**</span></span>|<span data-ttu-id="e01be-148">SQLOutboundPort</span><span class="sxs-lookup"><span data-stu-id="e01be-148">SQLOutboundPort</span></span>|  
  
     <span data-ttu-id="e01be-149">En outre, modifier le nom de l’opération à partir de Operation_1 pour **UpdateEmp**.</span><span class="sxs-lookup"><span data-stu-id="e01be-149">Also, change the operation name from Operation_1 to **UpdateEmp**.</span></span>  
  
8.  <span data-ttu-id="e01be-150">Connectez le port à des formes action.</span><span class="sxs-lookup"><span data-stu-id="e01be-150">Connect the port to action shapes.</span></span> <span data-ttu-id="e01be-151">Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="e01be-151">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e01be-152">Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action.</span><span class="sxs-lookup"><span data-stu-id="e01be-152">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="e01be-153">Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.</span><span class="sxs-lookup"><span data-stu-id="e01be-153">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
     <span data-ttu-id="e01be-154">Connecter les ports et les formes d’action comme suit :</span><span class="sxs-lookup"><span data-stu-id="e01be-154">Connect the ports and action shapes as follows:</span></span>  
  
    -   <span data-ttu-id="e01be-155">Connecter le **SendUpdateMessage** forme action pour le **demande** gérer de la **SQLOutboundPort**.</span><span class="sxs-lookup"><span data-stu-id="e01be-155">Connect the **SendUpdateMessage** action shape to the **Request** handle of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="e01be-156">Connecter le **ReceiveUpdateResponse** forme action pour le **réponse** gérer de la **SQLOutboundPort**.</span><span class="sxs-lookup"><span data-stu-id="e01be-156">Connect the **ReceiveUpdateResponse** action shape to the **Response** handle of the **SQLOutboundPort**.</span></span>  
  
9. <span data-ttu-id="e01be-157">L’illustration suivante montre l’orchestration en cours.</span><span class="sxs-lookup"><span data-stu-id="e01be-157">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="e01be-158">![Mise à jour de l’orchestration pour envoyer le message de mise à jour](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span><span class="sxs-lookup"><span data-stu-id="e01be-158">![Updated orchestration to send update message](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="e01be-159">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="e01be-159">What did I just do?</span></span>  
 <span data-ttu-id="e01be-160">Dans cette étape, vous mis à jour l’orchestration en ajoutant un **MessageAssignment** forme, **envoyer** et **réception** formes et un port.</span><span class="sxs-lookup"><span data-stu-id="e01be-160">In this step, you updated the orchestration by adding a **MessageAssignment** shape, **Send** and **Receive** shapes, and a port.</span></span> <span data-ttu-id="e01be-161">Vous connecté les formes et les ports pour envoyer le message de demande pour exécuter le UDPATE_EMPLOYEE message de demande et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="e01be-161">You connected the shapes and ports to send request message to execute the UDPATE_EMPLOYEE request message and receive the response.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e01be-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e01be-162">Next Steps</span></span>  
 <span data-ttu-id="e01be-163">Dans l’étape suivante, vous ajoutez des formes d’orchestration à appeler l’opération d’insertion sur la **Purchase_Order** table, comme décrit dans [leçon 4 : effectuer une opération Insert sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span><span class="sxs-lookup"><span data-stu-id="e01be-163">In the next step, you add orchestration shapes to invoke the Insert operation on the **Purchase_Order** table, as described in [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01be-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e01be-164">See Also</span></span>  
 <span data-ttu-id="e01be-165">[Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e01be-165">[Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span></span>  
 [<span data-ttu-id="e01be-166">Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés</span><span class="sxs-lookup"><span data-stu-id="e01be-166">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)
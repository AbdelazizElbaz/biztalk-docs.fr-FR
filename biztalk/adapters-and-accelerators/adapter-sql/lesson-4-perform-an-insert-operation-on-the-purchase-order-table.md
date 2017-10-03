---
title: "Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66fc64c5-a3da-4014-8545-f34e6577bd73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c966e3c10f18424b2cfb1fde0235caedbb5f58f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-4-perform-an-insert-operation-on-the-purchase-order-table"></a><span data-ttu-id="c2720-102">Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat</span><span class="sxs-lookup"><span data-stu-id="c2720-102">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>
<span data-ttu-id="c2720-103">Dans [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md), vous avez exécutée le **UPDATE_EMPLOYEE** procédure stockée et a reçu un message de réponse qui contient les détails de la nouvellement Insérer un enregistrement d’employé.</span><span class="sxs-lookup"><span data-stu-id="c2720-103">In [Lesson 3: Execute a Stored Procedure to Select New Employees Added](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md), you executed the **UPDATE_EMPLOYEE** stored procedure and received a response message that contains the details of the newly inserted employee record.</span></span> <span data-ttu-id="c2720-104">Dans cette leçon, vous allez créer dans la leçon précédente et mettre à jour de l’orchestration pour effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2720-104">In this lesson, you will build on the previous lesson and update the orchestration to perform the following steps:</span></span>  
  
1.  <span data-ttu-id="c2720-105">Dans l’orchestration, vous générez le message pour effectuer une opération d’insertion sur la **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="c2720-105">Within the orchestration, you build the message to perform an Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="c2720-106">Cette étape est similaire à [étape 1 : créer le Message de demande pour la procédure stockée UPDATE_EMPLOYEE](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="c2720-106">This step is similar to [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span></span>  
  
2.  <span data-ttu-id="c2720-107">Après avoir généré le message de demande, vous mappez le message de réponse de la **UPDATE_EMPLOYEE** procédure stockée pour le message de demande pour l’opération d’insertion sur la **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="c2720-107">After you build the request message, you map the response message of the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="c2720-108">En mappant les messages, vous transmettez les valeurs reçues à partir de messages de réponse au message de demande pour l’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="c2720-108">By mapping the messages, you pass the values received from the response messages to the request message for Insert operation.</span></span>  
  
3.  <span data-ttu-id="c2720-109">Vous envoyez le message à insérer un enregistrement dans le **Purchase_Order** de table et de recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="c2720-109">You send the message to insert a record in the **Purchase_Order** table and receive a response.</span></span>  
  
4.  <span data-ttu-id="c2720-110">Vous envoyer la réponse à un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c2720-110">You send the response to a send port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2720-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c2720-111">In This Section</span></span>  
  
-   [<span data-ttu-id="c2720-112">Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order</span><span class="sxs-lookup"><span data-stu-id="c2720-112">Step 1: Create the Request Message for Insert Operation on Purchase_Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)  
  
-   [<span data-ttu-id="c2720-113">Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération</span><span class="sxs-lookup"><span data-stu-id="c2720-113">Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)  
  
-   [<span data-ttu-id="c2720-114">Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="c2720-114">Step 3: Send the Request Message to Insert Records and Receive a Response</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)  
  
-   [<span data-ttu-id="c2720-115">Étape 4 : Création du projet</span><span class="sxs-lookup"><span data-stu-id="c2720-115">Step 4: Build the Project</span></span>](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)
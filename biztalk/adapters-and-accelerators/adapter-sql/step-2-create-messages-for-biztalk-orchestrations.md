---
title: "Étape 2 : Créer des Messages pour les Orchestrations BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47a4fb98-6085-4aeb-ab39-2f2c3858d4e0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89b121d95992eb30240e38da434d1125df9db681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-messages-for-biztalk-orchestrations"></a><span data-ttu-id="34c15-102">Étape 2 : Créer des Messages pour les Orchestrations BizTalk</span><span class="sxs-lookup"><span data-stu-id="34c15-102">Step 2: Create Messages for BizTalk Orchestrations</span></span>
<span data-ttu-id="34c15-103">![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="34c15-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="34c15-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="34c15-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="34c15-105">**Objectif :** dans cette étape, vous ajoutez une orchestration au projet BizTalk et créer des messages pour les schémas que vous avez généré dans [étape 1 : générer le schéma pour les opérations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span><span class="sxs-lookup"><span data-stu-id="34c15-105">**Objective:** In this step, you add an orchestration to the BizTalk project and create messages for the schemas you generated in [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="34c15-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="34c15-106">Prerequisites</span></span>  
 <span data-ttu-id="34c15-107">Vous devez avoir terminé [étape 1 : générer le schéma pour les opérations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span><span class="sxs-lookup"><span data-stu-id="34c15-107">You must have completed [Step 1: Generate Schema for Operations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).</span></span>  
  
### <a name="to-create-messages-in-an-orchestration"></a><span data-ttu-id="34c15-108">Pour créer des messages dans une orchestration</span><span class="sxs-lookup"><span data-stu-id="34c15-108">To create messages in an orchestration</span></span>  
  
1.  <span data-ttu-id="34c15-109">Ajouter une orchestration BizTalk au projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="34c15-109">Add a BizTalk orchestration to the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="34c15-110">À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="34c15-110">From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span>  
  
    2.  <span data-ttu-id="34c15-111">Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **catégories** , cliquez sur **fichiers d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="34c15-111">In the **Add New Item** dialog box, from the **Categories** box, click **Orchestration Files**.</span></span> <span data-ttu-id="34c15-112">À partir de la **modèles** , cliquez sur **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="34c15-112">From the **Templates** box, click **BizTalk Orchestration**.</span></span>  
  
    3.  <span data-ttu-id="34c15-113">Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="34c15-113">Type a name for the BizTalk orchestration, and then click **Add**.</span></span> <span data-ttu-id="34c15-114">Pour ce didacticiel, entrez le nom `EmployeeOrch.odx`.</span><span class="sxs-lookup"><span data-stu-id="34c15-114">For this tutorial, enter the name `EmployeeOrch.odx`.</span></span>  
  
2.  <span data-ttu-id="34c15-115">Ouvrez le **Vue Orchestration** fenêtre du projet BizTalk, s’il n’est pas déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="34c15-115">Open the **Orchestration View** window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="34c15-116">Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="34c15-116">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="34c15-117">Ajouter des messages à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="34c15-117">Add messages to the orchestration.</span></span>  
  
    1.  <span data-ttu-id="34c15-118">Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="34c15-118">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
    2.  <span data-ttu-id="34c15-119">Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="34c15-119">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
    3.  <span data-ttu-id="34c15-120">Dans le **propriétés** volet pour **Message_1**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="34c15-120">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
        |<span data-ttu-id="34c15-121">Utiliser</span><span class="sxs-lookup"><span data-stu-id="34c15-121">Use this</span></span>|<span data-ttu-id="34c15-122">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="34c15-122">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="34c15-123">Identificateur</span><span class="sxs-lookup"><span data-stu-id="34c15-123">Identifier</span></span>|<span data-ttu-id="34c15-124">Tapez `NotifyReceive`.</span><span class="sxs-lookup"><span data-stu-id="34c15-124">Type `NotifyReceive`.</span></span>|  
        |<span data-ttu-id="34c15-125">Type de message</span><span class="sxs-lookup"><span data-stu-id="34c15-125">Message Type</span></span>|<span data-ttu-id="34c15-126">Dans la liste déroulante, développez **schémas**, puis sélectionnez **Employee_PurchaseOrder.Notification**, où Employee_PurchaseOrder est le nom de votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="34c15-126">From the drop-down list, expand **Schemas**, and select **Employee_PurchaseOrder.Notification**, where Employee_PurchaseOrder is the name of your BizTalk project.</span></span> <span data-ttu-id="34c15-127">La notification est le schéma généré pour le **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="34c15-127">Notification is the schema generated for the **Notification** operation.</span></span>|  
  
    4.  <span data-ttu-id="34c15-128">Répétez l’étape précédente pour ajouter les quatre nouveaux messages, un message de demande-réponse affectez du UPDATE_EMPLOYEE appel de procédure stockée et un autre message de demande-réponse pour effectuer la **insérer** opération sur  **Purchase_Order** table.</span><span class="sxs-lookup"><span data-stu-id="34c15-128">Repeat the previous step to add four new messages—a request-response message set for invoking the UPDATE_EMPLOYEE stored procedure and another request-response message set for performing the **Insert** operation on **Purchase_Order** table.</span></span>  
  
        |<span data-ttu-id="34c15-129">Identificateur de la valeur</span><span class="sxs-lookup"><span data-stu-id="34c15-129">Set Identifier to</span></span>|<span data-ttu-id="34c15-130">Définissez le Type de Message</span><span class="sxs-lookup"><span data-stu-id="34c15-130">Set Message Type to</span></span>|  
        |-----------------------|-------------------------|  
        |<span data-ttu-id="34c15-131">UpdateEmployee</span><span class="sxs-lookup"><span data-stu-id="34c15-131">UpdateEmployee</span></span>|<span data-ttu-id="34c15-132">*Employee_PurchaseOrder.TypedProcedure_dbo. UPDATE_EMPLOYEE*, où TypedProcedure_dbo. UPDATE_EMPLOYEE est que le schéma pour le UPDATE_EMPLOYEE de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="34c15-132">*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEE*, where TypedProcedure_dbo.UPDATE_EMPLOYEE is the schema for the UPDATE_EMPLOYEE stored procedure.</span></span>|  
        |<span data-ttu-id="34c15-133">UpdateEmployeeResponse</span><span class="sxs-lookup"><span data-stu-id="34c15-133">UpdateEmployeeResponse</span></span>|<span data-ttu-id="34c15-134">*Employee_PurchaseOrder.TypedProcedure_dbo. UPDATE_EMPLOYEEResponse*</span><span class="sxs-lookup"><span data-stu-id="34c15-134">*Employee_PurchaseOrder.TypedProcedure_dbo.UPDATE_EMPLOYEEResponse*</span></span>|  
        |<span data-ttu-id="34c15-135">InsertPO</span><span class="sxs-lookup"><span data-stu-id="34c15-135">InsertPO</span></span>|<span data-ttu-id="34c15-136">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*, où TableOperation_dbo_Purchase_Order.Insert est le schéma pour l’opération d’insertion sur la table Purchase_Order.</span><span class="sxs-lookup"><span data-stu-id="34c15-136">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*, where TableOperation_dbo_Purchase_Order.Insert is the schema for the Insert operation on the Purchase_Order table.</span></span>|  
        |<span data-ttu-id="34c15-137">InsertPOResponse</span><span class="sxs-lookup"><span data-stu-id="34c15-137">InsertPOResponse</span></span>|<span data-ttu-id="34c15-138">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*</span><span class="sxs-lookup"><span data-stu-id="34c15-138">*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*</span></span>|  
  
    5.  <span data-ttu-id="34c15-139">Enregistrez le fichier d’orchestration et le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="34c15-139">Save the orchestration file and the BizTalk project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="34c15-140">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="34c15-140">What did I just do?</span></span>  
 <span data-ttu-id="34c15-141">Dans cette étape, vous avez créé des messages pour l’appel d’opérations entrantes et sortantes sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34c15-141">In this step, you created messages for invoking performing inbound and outbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="34c15-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="34c15-142">Next Steps</span></span>  
 <span data-ttu-id="34c15-143">Vous ajoutez des formes d’orchestration pour recevoir une notification à partir de SQL Server et filtrer les notifications pour l’opération d’insertion, comme décrit dans [leçon 2 : recevoir des Notifications de filtre et](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="34c15-143">You add orchestration shapes to receive notification from SQL Server and filter notifications for Insert operation, as described in [Lesson 2: Receive and Filter Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c15-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34c15-144">See Also</span></span>  
 <span data-ttu-id="34c15-145">[Leçon 1 : Générer des schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md) </span><span class="sxs-lookup"><span data-stu-id="34c15-145">[Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md) </span></span>  
 [<span data-ttu-id="34c15-146">Étape 1 : Générer le schéma pour les opérations</span><span class="sxs-lookup"><span data-stu-id="34c15-146">Step 1: Generate Schema for Operations</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)
---
title: "Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e4c6fa5-81b7-4928-84d5-39533535f862
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a33693a09d89acc5d1ad9e4514c7907b789cc75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-orchestration-shapes-to-receive-notification"></a><span data-ttu-id="facd7-102">Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification</span><span class="sxs-lookup"><span data-stu-id="facd7-102">Step 1: Add Orchestration Shapes to Receive Notification</span></span>
<span data-ttu-id="facd7-103">![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="facd7-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="facd7-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="facd7-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="facd7-105">**Objectif :** dans cette étape, vous ajoutez des formes d’orchestration pour recevoir une notification pour les modifications apportées à la **employé** table.</span><span class="sxs-lookup"><span data-stu-id="facd7-105">**Objective:** In this step, you add orchestration shapes to receive notification for changes to the **Employee** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="facd7-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="facd7-106">Prerequisites</span></span>  
 <span data-ttu-id="facd7-107">Vous devez avoir terminé les étapes de [leçon 1 : générer les schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md).</span><span class="sxs-lookup"><span data-stu-id="facd7-107">You must have completed the steps in [Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md).</span></span>  
  
### <a name="to-receive-notification-messages"></a><span data-ttu-id="facd7-108">Pour recevoir des messages de notification</span><span class="sxs-lookup"><span data-stu-id="facd7-108">To receive notification messages</span></span>  
  
1.  <span data-ttu-id="facd7-109">Ouvrez l’orchestration BizTalk, **EmployeeOrch.odx**, vous avez ajouté dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="facd7-109">Open the BizTalk orchestration, **EmployeeOrch.odx**, you added in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).</span></span>  
  
2.  <span data-ttu-id="facd7-110">Ajouter un **réception** forme à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="facd7-110">Add a **Receive** shape to the orchestration.</span></span> <span data-ttu-id="facd7-111">À partir de l’orchestration de boîte à outils, faites glisser le **réception** forme sur l’aire de conception d’orchestration et déposez-la dans l’emplacement indiqué entre le **commencer** (cercle vert) et **fin**les formes (octogone rouge).</span><span class="sxs-lookup"><span data-stu-id="facd7-111">From the orchestration Toolbox, drag the **Receive** shape to the orchestration design surface, and drop it into the space indicated between the **Begin** (green circle) and **End** (red octagon) shapes.</span></span>  
  
    |<span data-ttu-id="facd7-112">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="facd7-112">Set this property</span></span>|<span data-ttu-id="facd7-113">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="facd7-113">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="facd7-114">**Activate**</span><span class="sxs-lookup"><span data-stu-id="facd7-114">**Activate**</span></span>|<span data-ttu-id="facd7-115">True</span><span class="sxs-lookup"><span data-stu-id="facd7-115">True</span></span>|  
    |<span data-ttu-id="facd7-116">**Message**</span><span class="sxs-lookup"><span data-stu-id="facd7-116">**Message**</span></span>|<span data-ttu-id="facd7-117">NotifyReceive</span><span class="sxs-lookup"><span data-stu-id="facd7-117">NotifyReceive</span></span>|  
    |<span data-ttu-id="facd7-118">**Nom**</span><span class="sxs-lookup"><span data-stu-id="facd7-118">**Name**</span></span>|<span data-ttu-id="facd7-119">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="facd7-119">ReceiveNotification</span></span>|  
  
3.  <span data-ttu-id="facd7-120">Ajouter un unidirectionnel port de réception pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="facd7-120">Add a one-way receive port to the orchestration.</span></span> <span data-ttu-id="facd7-121">Vous allez utiliser ce port pour recevoir des messages de notification à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="facd7-121">You will use this port to receive notification messages from the SQL Server database.</span></span> <span data-ttu-id="facd7-122">Définissez les propriétés suivantes pour le port.</span><span class="sxs-lookup"><span data-stu-id="facd7-122">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="facd7-123">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="facd7-123">Set this property</span></span>|<span data-ttu-id="facd7-124">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="facd7-124">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="facd7-125">**Direction de communication**</span><span class="sxs-lookup"><span data-stu-id="facd7-125">**Communication Direction**</span></span>|<span data-ttu-id="facd7-126">Recevoir</span><span class="sxs-lookup"><span data-stu-id="facd7-126">Receive</span></span>|  
    |<span data-ttu-id="facd7-127">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="facd7-127">**Communication Pattern**</span></span>|<span data-ttu-id="facd7-128">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="facd7-128">One-Way</span></span>|  
    |<span data-ttu-id="facd7-129">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="facd7-129">**Identifier**</span></span>|<span data-ttu-id="facd7-130">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="facd7-130">ReceiveNotification</span></span>|  
  
     <span data-ttu-id="facd7-131">En outre, modifier le nom de l’opération à partir de Operation_1 pour **Notification**.</span><span class="sxs-lookup"><span data-stu-id="facd7-131">Also, change the operation name from Operation_1 to **Notification**.</span></span>  
  
4.  <span data-ttu-id="facd7-132">Connecter le **ReceiveNotification** port pour le **ReceiveNotification** forme action.</span><span class="sxs-lookup"><span data-stu-id="facd7-132">Connect the **ReceiveNotification** port to the **ReceiveNotification** action shape.</span></span> <span data-ttu-id="facd7-133">Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="facd7-133">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="facd7-134">Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action.</span><span class="sxs-lookup"><span data-stu-id="facd7-134">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="facd7-135">Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.</span><span class="sxs-lookup"><span data-stu-id="facd7-135">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
5.  <span data-ttu-id="facd7-136">L’illustration suivante montre l’orchestration en cours.</span><span class="sxs-lookup"><span data-stu-id="facd7-136">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="facd7-137">![Orchestration permettant de recevoir des messages de notification](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")</span><span class="sxs-lookup"><span data-stu-id="facd7-137">![Orchestration to receive notification messages](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="facd7-138">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="facd7-138">What did I just do?</span></span>  
 <span data-ttu-id="facd7-139">Dans cette étape, vous ajouté des formes d’orchestration et port de réception pour recevoir une notification à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="facd7-139">In this step, you added orchestration shapes and receive port to receive notification from the SQL Server database.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="facd7-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="facd7-140">Next Steps</span></span>  
 <span data-ttu-id="facd7-141">Vous ajoutez une forme expression à l’orchestration d’extraire le type de notification reçue à partir de la base de données SQL Server, comme décrit dans [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span><span class="sxs-lookup"><span data-stu-id="facd7-141">You add an expression shape to the orchestration to extract the type of notification received from the SQL Server database, as described in [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facd7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="facd7-142">See Also</span></span>  
 <span data-ttu-id="facd7-143">[Étape 2 : Extraire le Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span><span class="sxs-lookup"><span data-stu-id="facd7-143">[Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) </span></span>  
 [<span data-ttu-id="facd7-144">Leçon 2 : Réception et filtrer les Notifications</span><span class="sxs-lookup"><span data-stu-id="facd7-144">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)
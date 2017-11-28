---
title: "Étape 2 : Extraire le Type de Notification de Message de Notification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72f3e805-0f5f-42fa-8fe3-78ccbb375f74
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a4fd5e96c3593d3f47ed3c7dfc1875efca7c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-extract-notification-type-from-notification-message"></a><span data-ttu-id="868ae-102">Étape 2 : Extraire le Type de Notification de Message de Notification</span><span class="sxs-lookup"><span data-stu-id="868ae-102">Step 2: Extract Notification Type from Notification Message</span></span>
<span data-ttu-id="868ae-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="868ae-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="868ae-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="868ae-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="868ae-105">**Objectif :** dans cette étape, vous ajoutez une forme expression pour extraire le type de notification reçue à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="868ae-105">**Objective:** In this step, you add an expression shape to extract the type of notification received from the SQL Server database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="868ae-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="868ae-106">Prerequisites</span></span>  
 <span data-ttu-id="868ae-107">Vous devez avoir terminé [étape 1 : ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span><span class="sxs-lookup"><span data-stu-id="868ae-107">You must have completed [Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span></span>  
  
### <a name="to-extract-the-notification-type-from-the-notification-message"></a><span data-ttu-id="868ae-108">Pour extraire le type de notification à partir du message de notification</span><span class="sxs-lookup"><span data-stu-id="868ae-108">To extract the notification type from the notification message</span></span>  
  
1.  <span data-ttu-id="868ae-109">Ajouter une variable à l’orchestration BizTalk que vous avez créé dans [étape 1 : ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span><span class="sxs-lookup"><span data-stu-id="868ae-109">Add a variable to the BizTalk orchestration you created in [Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).</span></span>  
  
    1.  <span data-ttu-id="868ae-110">À partir de la vue Orchestration, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="868ae-110">From the Orchestration View, right-click **Variables**, and then click **New Variable**.</span></span>  
  
    2.  <span data-ttu-id="868ae-111">Avec le bouton droit de la nouvelle variable **Variable_1**, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="868ae-111">Right-click the new variable, **Variable_1**, and click **Properties Window**.</span></span> <span data-ttu-id="868ae-112">Définissez les propriétés suivantes pour la variable.</span><span class="sxs-lookup"><span data-stu-id="868ae-112">Set the following properties for the variable.</span></span>  
  
        |<span data-ttu-id="868ae-113">Définissez cette propriété</span><span class="sxs-lookup"><span data-stu-id="868ae-113">Set this property</span></span>|<span data-ttu-id="868ae-114">Cette valeur</span><span class="sxs-lookup"><span data-stu-id="868ae-114">To this value</span></span>|  
        |-----------------------|-------------------|  
        |<span data-ttu-id="868ae-115">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="868ae-115">**Identifier**</span></span>|<span data-ttu-id="868ae-116">NotificationType</span><span class="sxs-lookup"><span data-stu-id="868ae-116">NotificationType</span></span>|  
        |<span data-ttu-id="868ae-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="868ae-117">**Type**</span></span>|<span data-ttu-id="868ae-118">System.String</span><span class="sxs-lookup"><span data-stu-id="868ae-118">System.String</span></span>|  
  
2.  <span data-ttu-id="868ae-119">Ajouter un **Expression** forme à l’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="868ae-119">Add an **Expression** shape to the BizTalk orchestration.</span></span> <span data-ttu-id="868ae-120">À partir de l’orchestration de boîte à outils, faites glisser le **Expression** forme sur l’aire de conception d’orchestration et déposez-la après le **réception** forme</span><span class="sxs-lookup"><span data-stu-id="868ae-120">From the orchestration Toolbox, drag the **Expression** shape to the orchestration design surface, and drop it after the **Receive** shape</span></span>  
  
     <span data-ttu-id="868ae-121">Dans le **Expression** forme, vous allez ajouter une requête xpath pour extraire le type de message de notification reçue de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="868ae-121">Within the **Expression** shape, you will add an xpath query to extract the type of notification message received from SQL Server.</span></span> <span data-ttu-id="868ae-122">Avant de créer une requête xpath, examinons le format d’un message de notification.</span><span class="sxs-lookup"><span data-stu-id="868ae-122">Before creating an xpath query, let us look at the format of a notification message.</span></span> <span data-ttu-id="868ae-123">Un message de notification classique ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="868ae-123">A typical notification message resembles the following:</span></span>  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
3.  <span data-ttu-id="868ae-124">Comme vous le voir, les informations sur le type de la notification sont disponibles dans le `<info>` balise, au sein du parent `<Notification>` balise.</span><span class="sxs-lookup"><span data-stu-id="868ae-124">As you see, the information about the type of the notification is available within the `<info>` tag, within the parent `<Notification>` tag.</span></span> <span data-ttu-id="868ae-125">Par conséquent, ajoutez la requête xpath suivante dans le **Expression** forme :</span><span class="sxs-lookup"><span data-stu-id="868ae-125">So, add the following xpath query within the **Expression** shape:</span></span>  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     <span data-ttu-id="868ae-126">Ici, **NotificationType** est la variable que vous avez créé pour stocker la valeur extraite par la requête xpath.</span><span class="sxs-lookup"><span data-stu-id="868ae-126">Here, **NotificationType** is the variable you created to store the value extracted by the xpath query.</span></span> <span data-ttu-id="868ae-127">**NotifyReceive** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour recevoir des messages de notification.</span><span class="sxs-lookup"><span data-stu-id="868ae-127">**NotifyReceive** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) to receive notification messages.</span></span>  
  
4.  <span data-ttu-id="868ae-128">L’illustration suivante montre l’orchestration en cours avec le **Expression** forme inclus.</span><span class="sxs-lookup"><span data-stu-id="868ae-128">The following figure shows the in-progress orchestration with the **Expression** shape included.</span></span>  
  
     <span data-ttu-id="868ae-129">![Ajouter une forme Expression à l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")</span><span class="sxs-lookup"><span data-stu-id="868ae-129">![Add an Expression shape to the orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="868ae-130">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="868ae-130">What did I just do?</span></span>  
 <span data-ttu-id="868ae-131">Dans cette étape, vous avez ajouté un **Expression** forme pour extraire le type de notification reçue à partir de la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="868ae-131">In this step, you added an **Expression** shape to extract the kind of notification received from the SQL Server database.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="868ae-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="868ae-132">Next Steps</span></span>  
 <span data-ttu-id="868ae-133">Vous ajoutez une forme décider pour filtrer les notifications d’insertion, comme décrit dans [étape 3 : ajouter un filtre pour les Notifications d’insérer](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="868ae-133">You add a Decide shape to filter for Insert notifications, as described in [Step 3: Add a Filter for Insert Notifications](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868ae-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="868ae-134">See Also</span></span>  
 <span data-ttu-id="868ae-135">[Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md) </span><span class="sxs-lookup"><span data-stu-id="868ae-135">[Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md) </span></span>  
 <span data-ttu-id="868ae-136">[Étape 3 : Ajouter un filtre pour les Notifications d’insertion](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="868ae-136">[Step 3: Add a Filter for Insert Notifications](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md) </span></span>  
 [<span data-ttu-id="868ae-137">Leçon 2 : Réception et filtrer les Notifications</span><span class="sxs-lookup"><span data-stu-id="868ae-137">Lesson 2: Receive and Filter Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)
---
title: "Leçon 2 : Réception et filtrer les Notifications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5ec679c-1c67-4bf4-aa88-0787373343f5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f28d0479510078b3717d68f99976808ee19aa7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-receive-and-filter-notifications"></a><span data-ttu-id="845fc-102">Leçon 2 : Réception et filtrer les Notifications</span><span class="sxs-lookup"><span data-stu-id="845fc-102">Lesson 2: Receive and Filter Notifications</span></span>
<span data-ttu-id="845fc-103">Dans cette leçon, vous commencez à créer une orchestration qui reçoit les notifications de modifications apportées à la **employé** table.</span><span class="sxs-lookup"><span data-stu-id="845fc-103">In this lesson, you start creating an orchestration that receives notifications for changes to the **Employee** table.</span></span> <span data-ttu-id="845fc-104">Une fois que l’orchestration reçoit la notification, il extrait le type de notification et si le type de notification pour une opération d’insertion sur la **employé** table, une condition « if » est utilisée pour effectuer les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="845fc-104">After the orchestration receives the notification, it extracts the type of notification and if the notification type is for an Insert operation on the **Employee** table, an “if” condition is used to perform subsequent tasks.</span></span> <span data-ttu-id="845fc-105">Dans cette leçon, vous allez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="845fc-105">In this lesson, you will perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="845fc-106">Ajouter un unidirectionnel port de réception et un **réception** forme à l’orchestration pour recevoir le message de notification.</span><span class="sxs-lookup"><span data-stu-id="845fc-106">Add a one-way receive port and a **Receive** shape to the orchestration to receive the notification message.</span></span>  
  
2.  <span data-ttu-id="845fc-107">Ajouter un **Expression** forme qui contient une requête xpath pour extraire le type de notification.</span><span class="sxs-lookup"><span data-stu-id="845fc-107">Add an **Expression** shape that contains an xpath query to extract the type of notification.</span></span>  
  
3.  <span data-ttu-id="845fc-108">Une fois le type de notification est connu, ajouter un filtre à l’orchestration en incluant un **décider** forme.</span><span class="sxs-lookup"><span data-stu-id="845fc-108">After the notification type is known, add a filter to the orchestration by including a **Decide** shape.</span></span> <span data-ttu-id="845fc-109">Cette forme décide si la notification est d’une notification d’insertion et puis effectue les opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="845fc-109">This shape decides whether the notification is for an Insert notification and then performs subsequent operations.</span></span> <span data-ttu-id="845fc-110">Si la notification n’est pas pour une opération d’insertion, l’orchestration ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="845fc-110">If the notification is not for an Insert operation, the orchestration does not do anything.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="845fc-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="845fc-111">In This Section</span></span>  
  
-   [<span data-ttu-id="845fc-112">Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification</span><span class="sxs-lookup"><span data-stu-id="845fc-112">Step 1: Add Orchestration Shapes to Receive Notification</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)  
  
-   [<span data-ttu-id="845fc-113">Étape 2 : Extraire le Type de Notification de Message de Notification</span><span class="sxs-lookup"><span data-stu-id="845fc-113">Step 2: Extract Notification Type from Notification Message</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)  
  
-   [<span data-ttu-id="845fc-114">Étape 3 : Ajouter un filtre pour les Notifications d’insertion</span><span class="sxs-lookup"><span data-stu-id="845fc-114">Step 3: Add a Filter for Insert Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)
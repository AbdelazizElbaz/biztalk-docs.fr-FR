---
title: Gestionnaire de processus logique | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 6b69fc71-0f01-4513-9361-d7787d0cde6d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e562362fec8e13589f1860e74024ffe70dad1c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="process-manager-logic"></a><span data-ttu-id="14f05-102">Logique du Gestionnaire de processus</span><span class="sxs-lookup"><span data-stu-id="14f05-102">Process Manager Logic</span></span>
<span data-ttu-id="14f05-103">Cette section décrit comment le Gestionnaire de processus, le **OrderManager** d’orchestration, les commandes de processus.</span><span class="sxs-lookup"><span data-stu-id="14f05-103">This section describes how the process manager, the **OrderManager** orchestration, processes orders.</span></span> <span data-ttu-id="14f05-104">Elle présente les champs clés des différents messages de commande et permet de suivre les nouvelles commandes ou celles mises à jour via l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="14f05-104">It describes key fields in the various order messages and follows new and updated orders through the orchestration.</span></span>  
  
 <span data-ttu-id="14f05-105">Le **OrderManager** orchestration coordonne les orchestrations subordonnées afin de traiter la commande.</span><span class="sxs-lookup"><span data-stu-id="14f05-105">The **OrderManager** orchestration coordinates subordinate orchestrations to process the order.</span></span> <span data-ttu-id="14f05-106">Vous pouvez ajouter, supprimer ou modifier ces étapes sans devoir modifier le **OrderManager**.</span><span class="sxs-lookup"><span data-stu-id="14f05-106">You can add, delete, or modify these stages without having to change the **OrderManager**.</span></span> <span data-ttu-id="14f05-107">Le **OrderManager** effectue une grande partie de la coordination par le biais des messages personnalisés définis par les classes .NET.</span><span class="sxs-lookup"><span data-stu-id="14f05-107">The **OrderManager** does much of the coordination through custom messages defined by .NET classes.</span></span> <span data-ttu-id="14f05-108">Pour obtenir la liste de tous les messages dans la solution, consultez [référence de Message pour la Solution de gestion des processus métier](../core/message-reference-for-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="14f05-108">For a list of all messages in the solution, see [Message Reference for the Business Process Management Solution](../core/message-reference-for-the-business-process-management-solution.md).</span></span> <span data-ttu-id="14f05-109">Pour plus d’informations sur la définition des types de messages avec des classes .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="14f05-109">For information about defining message types with .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14f05-110">En raison de la taille et la portée de **OrderManager**, vous pouvez souhaiter lire ces sections, notamment la deuxième, avec l’orchestration ouverte dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14f05-110">Because of the size and scope of **OrderManager**, you may want to read these sections, especially the second, with the orchestration open in Microsoft Visual Studio.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14f05-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="14f05-111">In This Section</span></span>  
  
-   [<span data-ttu-id="14f05-112">Champs et les Messages de clé</span><span class="sxs-lookup"><span data-stu-id="14f05-112">Key Messages and Fields</span></span>](../core/key-messages-and-fields.md)  
  
-   [<span data-ttu-id="14f05-113">Flux de commandes par le biais du Gestionnaire de processus</span><span class="sxs-lookup"><span data-stu-id="14f05-113">Order Flow through the Process Manager</span></span>](../core/order-flow-through-the-process-manager.md)
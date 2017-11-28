---
title: "Étape 2 : Créer le Orchestration1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88cafbb-3b6f-4d27-8516-79a2391b4e31
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1989fe18d9c9c81741ac83bd2f96627ea818eb91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-orchestration"></a><span data-ttu-id="7dfa7-102">Étape 2 : Créer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="7dfa7-102">Step 2: Create the Orchestration</span></span>
<span data-ttu-id="7dfa7-103">Le programme d'installation de l'orchestration fait appel à un projet appelé BeginDocTest, comme décrit ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7dfa7-103">The orchestration setup is as follows using a project called BeginDocTest:</span></span>  
  
-   <span data-ttu-id="7dfa7-104">Ports</span><span class="sxs-lookup"><span data-stu-id="7dfa7-104">Ports</span></span>  
  
-   <span data-ttu-id="7dfa7-105">Messages</span><span class="sxs-lookup"><span data-stu-id="7dfa7-105">Messages</span></span>  
  
-   <span data-ttu-id="7dfa7-106">Envoi et réception</span><span class="sxs-lookup"><span data-stu-id="7dfa7-106">Send and Receive</span></span>  
  
-   <span data-ttu-id="7dfa7-107">Construire un message</span><span class="sxs-lookup"><span data-stu-id="7dfa7-107">Construct Message</span></span>  
  
-   <span data-ttu-id="7dfa7-108">Transforms</span><span class="sxs-lookup"><span data-stu-id="7dfa7-108">Transforms</span></span>  
  
 <span data-ttu-id="7dfa7-109">L'orchestration ne gère pas les exceptions.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-109">The orchestration does not do any exception handling.</span></span> <span data-ttu-id="7dfa7-110">J.D.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-110">J.D.</span></span> <span data-ttu-id="7dfa7-111">Edwards OneWorld procède à l'opération BeginDoc puis à d'autres opérations ultérieures par l'intermédiaire d'une transaction implicite, de manière qu'elle soit annulée si la connexion expire. L'orchestration BizTalk n'a donc aucune opération à effectuer pour annuler les modifications apportées par J.D.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-111">Edwards OneWorld performs the BeginDoc and subsequent operations within an implicit transaction that it will rollback if the connection times out. The BizTalk orchestration thus does not need to do anything to rollback changes J.D.</span></span> <span data-ttu-id="7dfa7-112">Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-112">Edwards OneWorld makes.</span></span> <span data-ttu-id="7dfa7-113">Toutefois, un délai d'expiration génèrera une exception au sein de l'orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-113">However, a time out will cause an exception in the BizTalk orchestration.</span></span> <span data-ttu-id="7dfa7-114">Celle-ci sera enregistrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-114">BizTalk will record the exception in the event log.</span></span> <span data-ttu-id="7dfa7-115">Si vous voulez ajouter la gestion des exceptions à l’orchestration, consultez les rubriques « Ajout d’un bloc Intercepter l’exception » et « Ajout d’un bloc de compensation » dans l’aide de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7dfa7-115">If you want to add exception handling to the orchestration, see "How to Add a Catch Exception Block" and "How to Add a Compensation Block" in the Microsoft BizTalk Server Help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7dfa7-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7dfa7-116">In This Section</span></span>  
  
-   [<span data-ttu-id="7dfa7-117">Tâche 1 : Créer les Ports</span><span class="sxs-lookup"><span data-stu-id="7dfa7-117">Task 1: Create the Ports</span></span>](../core/task-1-create-the-ports2.md)  
  
-   [<span data-ttu-id="7dfa7-118">Tâche 2 : Créer les Messages</span><span class="sxs-lookup"><span data-stu-id="7dfa7-118">Task 2: Create the Messages</span></span>](../core/task-2-create-the-messages1.md)  
  
-   [<span data-ttu-id="7dfa7-119">Tâche 3 : Configurer l’envoi et réception des formes</span><span class="sxs-lookup"><span data-stu-id="7dfa7-119">Task 3: Configure the Send and Receive Shapes</span></span>](../core/task-3-configure-the-send-and-receive-shapes1.md)  
  
-   [<span data-ttu-id="7dfa7-120">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="7dfa7-120">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape2.md)  
  
-   [<span data-ttu-id="7dfa7-121">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="7dfa7-121">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)
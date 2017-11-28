---
title: "Étape 2 : Créer le Orchestration2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08d65525-77a9-4be2-a509-40ea60fa7401
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13973edb14fbaed331a33eff429d623a33c3ff71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-orchestration"></a><span data-ttu-id="9ed47-102">Étape 2 : Créer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="9ed47-102">Step 2: Create the Orchestration</span></span>
<span data-ttu-id="9ed47-103">Le programme d'installation de l'orchestration fait appel à un projet appelé BeginDocTest, comme décrit ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9ed47-103">The orchestration setup is as follows using a project called BeginDocTest:</span></span>  
  
 <span data-ttu-id="9ed47-104">• Ports</span><span class="sxs-lookup"><span data-stu-id="9ed47-104">• Ports</span></span>  
  
 <span data-ttu-id="9ed47-105">• Messages</span><span class="sxs-lookup"><span data-stu-id="9ed47-105">• Messages</span></span>  
  
 <span data-ttu-id="9ed47-106">• Envoyer et recevoir</span><span class="sxs-lookup"><span data-stu-id="9ed47-106">• Send and Receive</span></span>  
  
 <span data-ttu-id="9ed47-107">• Construire un message</span><span class="sxs-lookup"><span data-stu-id="9ed47-107">• Construct Message</span></span>  
  
 <span data-ttu-id="9ed47-108">• Transforms</span><span class="sxs-lookup"><span data-stu-id="9ed47-108">• Transforms</span></span>  
  
 <span data-ttu-id="9ed47-109">L'orchestration ne gère pas les exceptions.</span><span class="sxs-lookup"><span data-stu-id="9ed47-109">The orchestration does not do any exception handling.</span></span> <span data-ttu-id="9ed47-110">J.D.</span><span class="sxs-lookup"><span data-stu-id="9ed47-110">J.D.</span></span> <span data-ttu-id="9ed47-111">Edwards EnterpriseOne effectue l’opération BeginDoc puis les opérations suivantes d’une transaction implicite qu’il va restauration si la connexion expire. L'orchestration BizTalk n'a donc aucune opération à effectuer pour annuler les modifications apportées par J.D.</span><span class="sxs-lookup"><span data-stu-id="9ed47-111">Edwards EnterpriseOne performs the BeginDoc and subsequent operations within an implicit transaction that it will rollback if the connection times out. The BizTalk orchestration thus does not need to do anything to rollback changes J.D.</span></span> <span data-ttu-id="9ed47-112">Edwards EnterpriseOne rend.</span><span class="sxs-lookup"><span data-stu-id="9ed47-112">Edwards EnterpriseOne makes.</span></span> <span data-ttu-id="9ed47-113">Toutefois, un délai d'expiration génèrera une exception au sein de l'orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9ed47-113">However, a time out will cause an exception in the BizTalk orchestration.</span></span> <span data-ttu-id="9ed47-114">Celle-ci sera enregistrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="9ed47-114">BizTalk will record the exception in the event log.</span></span> <span data-ttu-id="9ed47-115">Si vous voulez ajouter la gestion des exceptions à l'orchestration, consultez les rubriques « Ajout d'un bloc Intercepter l'exception » et « Ajout d'un bloc de compensation » dans l'aide principale de Microsoft BizTalk 2006.</span><span class="sxs-lookup"><span data-stu-id="9ed47-115">If you want to add exception handling to the orchestration, see "How to Add a Catch Exception Block" and "How to Add a Compensation Block" in the Microsoft BizTalk 2006 main help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ed47-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9ed47-116">In This Section</span></span>  
  
-   [<span data-ttu-id="9ed47-117">Tâche 1 : Créer les Ports</span><span class="sxs-lookup"><span data-stu-id="9ed47-117">Task 1: Create the Ports</span></span>](../core/task-1-create-the-ports1.md)  
  
-   [<span data-ttu-id="9ed47-118">Tâche 2 : Créer les Messages</span><span class="sxs-lookup"><span data-stu-id="9ed47-118">Task 2: Create the Messages</span></span>](../core/task-2-create-the-messages2.md)  
  
-   [<span data-ttu-id="9ed47-119">Tâche 3 : Configurer l’envoi et réception des formes</span><span class="sxs-lookup"><span data-stu-id="9ed47-119">Task 3: Configure the Send and Receive Shapes</span></span>](../core/task-3-configure-the-send-and-receive-shapes2.md)  
  
-   [<span data-ttu-id="9ed47-120">Tâche 4 : Configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="9ed47-120">Task 4: Configure the Construct Message Shape</span></span>](../core/task-4-configure-the-construct-message-shape1.md)  
  
-   [<span data-ttu-id="9ed47-121">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="9ed47-121">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)
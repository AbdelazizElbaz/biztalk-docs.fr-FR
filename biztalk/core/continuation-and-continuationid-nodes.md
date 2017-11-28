---
title: "Nœuds continuation et ContinuationID | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- Continuation nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- BAM, correlating activities
- activities, linking
- activities, continuation tokens
- ContinuationID nodes [Tracking Profile Editor]
ms.assetid: aa050660-66f7-4084-b6bf-b9319ce625af
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aa8956721d4a44b51b8d2c7776560aaa878f864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="continuation-and-continuationid-nodes"></a><span data-ttu-id="15909-102">Nœuds Continuation et ContinuationID</span><span class="sxs-lookup"><span data-stu-id="15909-102">Continuation and ContinuationID Nodes</span></span>
<span data-ttu-id="15909-103">Les continuations assistent l'infrastructure BAM quant aux informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="15909-103">Continuations provide guidance to the BAM infrastructure about the following information:</span></span>  
  
-   <span data-ttu-id="15909-104">L'ordre dans lequel les événements sont censés se produire</span><span class="sxs-lookup"><span data-stu-id="15909-104">The order in which events are expected to occur</span></span>  
  
-   <span data-ttu-id="15909-105">Une manière de traiter toute modification de l'ID unique avec lequel les éléments d'événement sont corrélés</span><span class="sxs-lookup"><span data-stu-id="15909-105">A way to handle any change in the unique ID to which event items are correlated</span></span>  
  
 <span data-ttu-id="15909-106">Autrement dit, les continuations définissent le transfert de ces informations entre les contributeurs d'une activité.</span><span class="sxs-lookup"><span data-stu-id="15909-106">To state this another way, continuations define the transfer of this information between contributors to an activity.</span></span> <span data-ttu-id="15909-107">Ce transfert a lieu dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="15909-107">A transfer occurs in the following situations:</span></span>  
  
-   <span data-ttu-id="15909-108">Une modification se produit dans l'ActivityID entre le moment où l'activité commence et celui où elle s'achève.</span><span class="sxs-lookup"><span data-stu-id="15909-108">There is a change in the ActivityID between the time an activity begins and ends.</span></span> <span data-ttu-id="15909-109">Par exemple vous avez deux messages associés tels qu'un numéro de bon de commande et un numéro d'ordre d'achat.</span><span class="sxs-lookup"><span data-stu-id="15909-109">For example, you have two related messages such as a Purchase Order number and Sales Order number.</span></span> <span data-ttu-id="15909-110">Ces numéros sont uniques, par exemple 123456 pour le bon de commande et 987654 pour l'ordre d'achat.</span><span class="sxs-lookup"><span data-stu-id="15909-110">Each has a unique number assigned to it, such as 123456 for the Purchase Order number and 987654 for Sales Order number.</span></span> <span data-ttu-id="15909-111">Vous utilisez ici une continuation pour mettre en équation les identificateurs uniques du bon de commande et de l'ordre d'achat de sorte que les événements puissent être mis en corrélation avec l'activité commune, quel que soit l'identificateur unique associé aux événements entrants.</span><span class="sxs-lookup"><span data-stu-id="15909-111">You would use a continuation to equate the unique identifiers for the Purchase Order and the Sales Order so that events can be correlated to the common activity regardless of which unique identifier is associated with the incoming events.</span></span>  
  
-   <span data-ttu-id="15909-112">Il existe une transition d'un environnement d'exécution à l'autre.</span><span class="sxs-lookup"><span data-stu-id="15909-112">You have a transition from one run-time environment to another.</span></span> <span data-ttu-id="15909-113">Par exemple, dans un scénario où vous disposez d’une application qui fournit un bon de commande à un pipeline de messagerie BizTalk Server, qui appelle une orchestration et l’orchestration, puis passe le contrôle à une application qui envoie un avis d’expédition, vous avez deux transitions d’environnement : à partir d’un pipeline de messagerie à un une orchestration et d’une orchestration à un pipeline de messagerie.</span><span class="sxs-lookup"><span data-stu-id="15909-113">For example, in a scenario where you have an application that supplies a purchase order to a BizTalk Server messaging pipeline, which then invokes an orchestration, and the orchestration then passes control to an application that sends a shipping notice, you have two environment transitions: from a messaging pipeline to a an orchestration and from an orchestration to a messaging pipeline.</span></span>  
  
 <span data-ttu-id="15909-114">L'un des points importants à retenir lors de la sélection d'une propriété à utiliser pour votre continuation est que les propriétés doivent être mappées à partir du même contexte.</span><span class="sxs-lookup"><span data-stu-id="15909-114">An important point to remember when selecting a property to use for your continuation is that the properties must be mapped from the same context.</span></span>  
  
 <span data-ttu-id="15909-115">Par exemple, si vous disposez des propriétés Message.InterchangeID et servicecontext.InterchangeID, vous pourrez probablement utiliser InterchangeID pour créer votre continuation.</span><span class="sxs-lookup"><span data-stu-id="15909-115">For example, if you have the propertiesy Message.InterchangeID and servicecontext.InterchangeID it might appear that you could use the InterchangeID to create your continuation.</span></span> <span data-ttu-id="15909-116">Si les messages proviennent de contextes différents, vous ne pourrez pas utiliser InterchangeID (ou une autre propriété) pour créer une continuation de manière fiable.</span><span class="sxs-lookup"><span data-stu-id="15909-116">If the messages come from different contexts you cannot use the InterchangeID (or other property) to reliably create a continuation.</span></span>  
  
## <a name="working-with-continuation-nodes"></a><span data-ttu-id="15909-117">Utilisation des nœuds Continuation</span><span class="sxs-lookup"><span data-stu-id="15909-117">Working with Continuation nodes</span></span>  
 <span data-ttu-id="15909-118">Le nœud Continuation contient des éléments de données qui indiquent un ID d’instance unique, également appelé un *jeton de continuation*.</span><span class="sxs-lookup"><span data-stu-id="15909-118">The Continuation node contains data items that indicate a unique instance ID, also called a *continuation token*.</span></span> <span data-ttu-id="15909-119">Grâce au jeton de liaison, les développeurs peuvent établir des liens avec d'autres activités utilisant le nœud ContinuationID.</span><span class="sxs-lookup"><span data-stu-id="15909-119">By using the continuation token, developers can link to other activities using the ContinuationID node.</span></span>  
  
 <span data-ttu-id="15909-120">On dénombre trois scénarios de base d'utilisation des nœuds Continuation et ContinuationID :</span><span class="sxs-lookup"><span data-stu-id="15909-120">There are three basic scenarios in which Continuation and ContinuationID nodes are used:</span></span>  
  
-   <span data-ttu-id="15909-121">Orchestration vers orchestration</span><span class="sxs-lookup"><span data-stu-id="15909-121">Orchestration to orchestration</span></span>  
  
-   <span data-ttu-id="15909-122">Orchestration vers solution BizTalk</span><span class="sxs-lookup"><span data-stu-id="15909-122">Orchestration to BizTalk solution</span></span>  
  
-   <span data-ttu-id="15909-123">Solution BizTalk vers orchestration</span><span class="sxs-lookup"><span data-stu-id="15909-123">BizTalk solution to orchestration</span></span>  
  
 <span data-ttu-id="15909-124">Dans le scénario « orchestration », l'Éditeur de modèle de suivi doit définir un nœud Continuation et un nœud ContinuationID, et les nœuds doivent porter le même nom afin que l'analyse BAM puisse mettre les activités en corrélation.</span><span class="sxs-lookup"><span data-stu-id="15909-124">In the orchestration scenario the TPE must define a Continuation node, and a ContinuationID node, and the nodes must have the same name in order for BAM to correlate the activities.</span></span>  
  
 <span data-ttu-id="15909-125">Dans le scénario « orchestration vers solution BizTalk », vous utilisez l'Éditeur de modèle de suivi (TPE) pour définir un nœud Continuation et le développeur crée une solution qui utilise l'API BAM pour gérer la partie destinataire de la continuation.</span><span class="sxs-lookup"><span data-stu-id="15909-125">In the orchestration to BizTalk solution scenario, you use the TPE to define a Continuation node and the developer creates a solution that uses the BAM API to handle the destination portion of the continuation..</span></span>  
  
 <span data-ttu-id="15909-126">Dans « solution BizTalk vers orchestration », le développeur utilise l'API BAM pour fournir l'origine de la paire de continuation et vous utilisez l'Éditeur de modèle de suivi pour définir un nœud ContinuationID.</span><span class="sxs-lookup"><span data-stu-id="15909-126">In the BizTalk solution to orchestration, the developer uses the BAM API to supply the origination of the continuation pair and you use TPE to define a ContinuationID node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15909-127">Les ports bidirectionnels peuvent opérer dans les deux sens, ce qui signifie que l'interception des données qui transitent via les ports peut, en fonction du comportement de la solution BizTalk, requérir l'activation d'une continuation.</span><span class="sxs-lookup"><span data-stu-id="15909-127">Two-way ports can operate in either direction, which means that interception of data that passes through the ports can, depending on the behavior of the BizTalk solution, require enabling of a continuation.</span></span> <span data-ttu-id="15909-128">Par exemple, si l'activité enregistre « PortEndTime » pour l'activation d'un port de messagerie BizTalk Server dans les deux sens (si les noms d'élément sont par exemple « MessageReceived » et « MessageSent », dans cet ordre), vous devez créer une continuation entre eux.</span><span class="sxs-lookup"><span data-stu-id="15909-128">For example, if the activity records “PortEndTime” for activation of a BizTalk Server messaging port in either direction (if the item names are, for example, “MessageReceived” and “MessageSent,” in that order), you need to create a continuation between them.</span></span> <span data-ttu-id="15909-129">Une continuation est nécessaire dès que plus d'un flux d'événements contribue à une activité BAM, et on distingue des flux d'événements différents pour chaque point de contact d'implémentation (entrée de la messagerie de BizTalk Server, sortie de la messagerie de BizTalk Server, orchestration, applications personnalisées et services Web).</span><span class="sxs-lookup"><span data-stu-id="15909-129">A continuation is required any time more than one event stream contributes to a BAM activity, and there are distinct event streams per implementation touch point (such as BTS Messaging in, BTS Messaging out, Orchestration, custom applications, and Web services).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15909-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15909-130">See Also</span></span>  
 <span data-ttu-id="15909-131">[Comment créer une Continuation](../core/how-to-create-a-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="15909-131">[How to Create a Continuation](../core/how-to-create-a-continuation.md) </span></span>  
 [<span data-ttu-id="15909-132">Nœuds de l’activité TPE</span><span class="sxs-lookup"><span data-stu-id="15909-132">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)
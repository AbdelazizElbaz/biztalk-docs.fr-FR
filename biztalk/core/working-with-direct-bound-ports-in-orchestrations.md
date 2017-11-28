---
title: "Utilisation de Ports à liaison directe dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a37ac0-5131-4d37-b60b-56763c460463
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e7b2b59ccdaa23271ee0707f19f4fd2cddc0508
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-direct-bound-ports-in-orchestrations"></a><span data-ttu-id="3f61b-102">Utilisation de ports à liaison directe dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="3f61b-102">Working with Direct Bound Ports in Orchestrations</span></span>
<span data-ttu-id="3f61b-103">Il existe trois types de ports à liaison directe : MessageBox, autocorrélation et orchestration partenaire.</span><span class="sxs-lookup"><span data-stu-id="3f61b-103">There are three types of direct bound ports: MessageBox, self-correlating, and partner orchestration.</span></span>  
  
 <span data-ttu-id="3f61b-104">Les ports à liaison directe MessageBox permettent des modèles de conception publication/abonnement.</span><span class="sxs-lookup"><span data-stu-id="3f61b-104">MessageBox direct bound ports allow for publish-subscribe design patterns.</span></span> <span data-ttu-id="3f61b-105">Les messages envoyés sur un port à liaison directe MessageBox sont publiés dans la base de données MessageBox, où les destinataires les récupèrent en fonction des abonnements.</span><span class="sxs-lookup"><span data-stu-id="3f61b-105">Messages sent on a MessageBox direct bound port are published to the MessageBox database, where message recipients pick them up based on subscriptions.</span></span> <span data-ttu-id="3f61b-106">Les ports logiques de réception configurés en tant que ports à liaison directe récupèrent les messages directement de la base de donnés MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3f61b-106">Logical receive ports configured as MessageBox direct bound ports get messages directly from the MessageBox database.</span></span> <span data-ttu-id="3f61b-107">Pour l’activation **réception** formes, MessageBox direct lié ports get les messages via des abonnements pour le type de message et l’expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="3f61b-107">For activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the filter expression.</span></span> <span data-ttu-id="3f61b-108">Pour l’activation non **réception** formes, MessageBox direct lié ports get les messages via des abonnements pour le type de message et l’ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="3f61b-108">For non-activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the correlation set.</span></span>  
  
 <span data-ttu-id="3f61b-109">Les ports à liaison directe d'autocorrélation vous aident à concevoir une communication asynchrone entre orchestrations.</span><span class="sxs-lookup"><span data-stu-id="3f61b-109">Self-correlating direct bound ports assist you in designing asynchronous inter-orchestration communication.</span></span> <span data-ttu-id="3f61b-110">Les messages envoyés à un port à liaison directe d'autocorrélation sont acheminés vers l'instance de l'orchestration qui a créé le point de réception du port à liaison directe autocorrélé.</span><span class="sxs-lookup"><span data-stu-id="3f61b-110">Messages sent to a self-correlating direct bound port are routed to the instance of the orchestration that created the receiving end of the self-correlated direct bound port.</span></span>  
  
 <span data-ttu-id="3f61b-111">Les ports à liaison directe d'orchestration partenaire proposent une communication entre orchestrations.</span><span class="sxs-lookup"><span data-stu-id="3f61b-111">Partner orchestration direct bound ports provide for inter-orchestration communication.</span></span> <span data-ttu-id="3f61b-112">Les messages envoyés sur un port à liaison directe d'orchestration partenaire peuvent être envoyés à une orchestration destinataire prévue, et les messages reçus sur un port à liaison directe d'orchestration partenaire peuvent l'être à partir d'une orchestration d'expédition prévue.</span><span class="sxs-lookup"><span data-stu-id="3f61b-112">Messages sent on a partner orchestration direct bound port can be sent to an intended recipient orchestration, and messages received on a partner orchestration direct bound port can be received from an intended sender orchestration.</span></span>  
  
 <span data-ttu-id="3f61b-113">Même avec une liaison directe, le message semble aller directement d'une orchestration à l'autre. En fait, tout message envoyé par n'importe quel type de port logique transite toujours par la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3f61b-113">Although with direct binding, the message appears to go directly from one orchestration to another, in fact any message sent through any type of logical port always travels through the MessageBox database.</span></span> <span data-ttu-id="3f61b-114">De plus, les ports à liaison directe sont les seuls ports logiques, par conséquent, la liaison logique n'est qu'une fonction de configuration de la conception.</span><span class="sxs-lookup"><span data-stu-id="3f61b-114">Moreover, direct bound ports are only logical ports and therefore direct binding is only a design-time configuration feature.</span></span> <span data-ttu-id="3f61b-115">Un port à liaison directe ne peut pas être lié à un port physique, et vous pouvez modifier uniquement la configuration de liaison directe au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="3f61b-115">A direct bound port cannot be bound to a physical port, and you can only change the direct binding configuration at design time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f61b-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3f61b-116">In This Section</span></span>  
  
-   [<span data-ttu-id="3f61b-117">Comment utiliser des Ports à liaison directe MessageBox</span><span class="sxs-lookup"><span data-stu-id="3f61b-117">How to Use MessageBox Direct Bound Ports</span></span>](../core/how-to-use-messagebox-direct-bound-ports.md)  
  
-   [<span data-ttu-id="3f61b-118">Ports de liaison de l’utilisation directe d’autocorrélation</span><span class="sxs-lookup"><span data-stu-id="3f61b-118">How to Use Self-Correlating Direct Bound Ports</span></span>](../core/how-to-use-self-correlating-direct-bound-ports.md)  
  
-   [<span data-ttu-id="3f61b-119">Ports de liaison de l’utilisation directe de Orchestration du partenaire</span><span class="sxs-lookup"><span data-stu-id="3f61b-119">How to Use Partner Orchestration Direct Bound Ports</span></span>](../core/how-to-use-partner-orchestration-direct-bound-ports.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f61b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f61b-120">See Also</span></span>  
 [<span data-ttu-id="3f61b-121">Liaisons de port</span><span class="sxs-lookup"><span data-stu-id="3f61b-121">Port Bindings</span></span>](../core/port-bindings.md)
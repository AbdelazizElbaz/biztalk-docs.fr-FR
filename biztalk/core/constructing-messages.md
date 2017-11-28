---
title: Construction de Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- multi-part message types
- messages, modifying
- multi-part message types, about multi-part message types
- modifying, messages
- messages, creating
ms.assetid: c9fc1e97-ff53-42e2-848c-6c8fae7c9122
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fa87c4f3400a80ce83df132747d0004232323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-messages"></a><span data-ttu-id="38c58-102">Construction de Messages</span><span class="sxs-lookup"><span data-stu-id="38c58-102">Constructing Messages</span></span>
<span data-ttu-id="38c58-103">Vous construisez un message à chaque vous fois que vous introduisez un message dans votre orchestration, soit en le recevant, soit en attribuant des valeurs à une variable de message.</span><span class="sxs-lookup"><span data-stu-id="38c58-103">You construct a message any time that you introduce a message into your orchestration, either by receiving it or by assigning values to a message variable.</span></span> <span data-ttu-id="38c58-104">Tout message que vous construisez doit avoir un type de message, de manière à ce que le moteur d'exécution dispose d'une description complète de l'objet avec lequel il travaille.</span><span class="sxs-lookup"><span data-stu-id="38c58-104">Any message that you construct must have a message type, so that the runtime engine has a complete description of the object that it is working with.</span></span> <span data-ttu-id="38c58-105">Le type de message à parties multiples peut être défini par l'utilisateur, être une classe .NET ou être un schéma.</span><span class="sxs-lookup"><span data-stu-id="38c58-105">The multi-part message type can be user-defined, it can be a .NET class, or it can be a schema.</span></span> <span data-ttu-id="38c58-106">Vous pouvez construire des messages de différentes manières : vous pouvez appeler une classe .NET pour créer un message, affecter un message à un autre ou utiliser une transformation pour mapper certaines valeurs au sein d’un message aux valeurs d’un autre message.</span><span class="sxs-lookup"><span data-stu-id="38c58-106">You can construct messages in various ways: you can invoke a .NET class to create a message, assign one message to another, or use a transform to map certain values within a message to values within another message.</span></span> <span data-ttu-id="38c58-107">Les messages peuvent également être construits par des actions de réception ou lorsque votre orchestration accepte un message en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="38c58-107">Messages are also constructed by a receive action or when your orchestration accepts a message as a parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38c58-108">Un type de message à parties multiples ne contient pas forcément plusieurs parties. Il peut très bien n'en contenir qu'une.</span><span class="sxs-lookup"><span data-stu-id="38c58-108">A multi-part message type does not necessarily contain multiple parts; it might contain just one.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38c58-109">Les messages sont immuables dans BizTalk : une fois que vous avez construit un message original, vous ne pouvez plus le modifier.</span><span class="sxs-lookup"><span data-stu-id="38c58-109">Messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original.</span></span> <span data-ttu-id="38c58-110">Si vous avez besoin d'apporter une modification, vous devez construire une nouvelle copie du message et y attribuer les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="38c58-110">If you need to make a change, you must construct a new copy of the message and assign values to it appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38c58-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="38c58-111">In This Section</span></span>  
 [<span data-ttu-id="38c58-112">Comment configurer la forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="38c58-112">How to Configure the Construct Message Shape</span></span>](../core/how-to-configure-the-construct-message-shape.md)  
  
 [<span data-ttu-id="38c58-113">Comment configurer la forme assignation du Message</span><span class="sxs-lookup"><span data-stu-id="38c58-113">How to Configure the Message Assignment Shape</span></span>](../core/how-to-configure-the-message-assignment-shape.md) 
  
 [<span data-ttu-id="38c58-114">Comment configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="38c58-114">How to Configure the Transform Shape</span></span>](../core/how-to-configure-the-transform-shape.md) 
  
 [<span data-ttu-id="38c58-115">Références de message dans la forme assignation du Message</span><span class="sxs-lookup"><span data-stu-id="38c58-115">Message References in Message Assignment Shape</span></span>](../core/message-references-in-message-assignment-shape.md)  
  
 [<span data-ttu-id="38c58-116">Références de message dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="38c58-116">Message References in User Code</span></span>](../core/message-references-in-user-code.md)  
  
 [<span data-ttu-id="38c58-117">Utilisation des XPaths dans une assignation de Message</span><span class="sxs-lookup"><span data-stu-id="38c58-117">Using XPaths in Message Assignments</span></span>](../core/using-xpaths-in-message-assignments.md)  
  
 [<span data-ttu-id="38c58-118">À l’aide de XPath Non canoniques dans une assignation de Message</span><span class="sxs-lookup"><span data-stu-id="38c58-118">Using Non-Canonical XPaths in Message Assignments</span></span>](../core/using-non-canonical-xpaths-in-message-assignments.md)  
  
 [<span data-ttu-id="38c58-119">Construction de Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="38c58-119">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)  
  
 [<span data-ttu-id="38c58-120">Ajout de nœuds pour les Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="38c58-120">Appending Nodes to Messages in User Code</span></span>](../core/appending-nodes-to-messages-in-user-code.md)  
  
## <a name="see-also"></a><span data-ttu-id="38c58-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38c58-121">See Also</span></span>  
 [<span data-ttu-id="38c58-122">À l’aide de Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="38c58-122">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)
---
title: "À l’aide de Ports d’envoi TIBCO Rendezvous à partir de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, handling
- message handling
- BizTalk Server, using send ports from
- send ports, using from BizTalk Server
- messages, generating
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e11657e8e15ac0739124178e85f0c7c5c0a70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-send-ports-from-biztalk-server"></a><span data-ttu-id="b9a97-102">Utilisation des ports d'envoi TIBCO Rendezvous à partir de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b9a97-102">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>
<span data-ttu-id="b9a97-103">Un port de transmission peut envoyer tout type de message.</span><span class="sxs-lookup"><span data-stu-id="b9a97-103">A transmit port can send any kind of message.</span></span> <span data-ttu-id="b9a97-104">Lorsque BizTalk Server envoie un message via l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous, l'adaptateur génère le message d'après les valeurs des propriétés de contexte du message ou sur la base des valeurs par défaut, puis il l'envoie vers l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9a97-104">When BizTalk Server sends a message through Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter generates the message based on message context properties values, or it uses the default and sends it to the specified subject.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9a97-105">Selon la documentation de TIBCO Rendezvous, les caractères génériques ne sont pas pris en charge dans les noms d'objets de transmission.</span><span class="sxs-lookup"><span data-stu-id="b9a97-105">According to the TIBCO Rendezvous documentation, wildcard characters are not supported in transmit subject names.</span></span>  
  
## <a name="message-handling"></a><span data-ttu-id="b9a97-106">Gestion des messages</span><span class="sxs-lookup"><span data-stu-id="b9a97-106">Message Handling</span></span>  
 <span data-ttu-id="b9a97-107">L'adaptateur conserve un état et traite les messages BizTalk Server entrants en conséquence.</span><span class="sxs-lookup"><span data-stu-id="b9a97-107">The adapter maintains a state and handles incoming BizTalk Server messages accordingly.</span></span>  
  
-   <span data-ttu-id="b9a97-108">Lorsqu'un message ne peut pas être envoyé à cause d'une défaillance au niveau du transport, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="b9a97-108">If a message cannot be sent because of transport failure, BizTalk Server is instructed to resubmit later.</span></span>  
  
-   <span data-ttu-id="b9a97-109">Lorsqu'un message ne peut pas être envoyé car l'adaptateur est toujours en cours d'initialisation, le message BizTalk Server est mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="b9a97-109">If a message cannot be sent because the adapter is still initializing, the BizTalk Server message is queued.</span></span> <span data-ttu-id="b9a97-110">Si l'initialisation échoue, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="b9a97-110">If initialization fails, BizTalk Server is instructed to resubmit later.</span></span>  
  
## <a name="message-generation"></a><span data-ttu-id="b9a97-111">Création de messages</span><span class="sxs-lookup"><span data-stu-id="b9a97-111">Message Generation</span></span>  
 <span data-ttu-id="b9a97-112">Grâce à l'adaptateur de transmission, l'adaptateur BizTalk pour TIBCO Rendezvous ignore l'espace de noms cible du message et l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="b9a97-112">With the transmit adapter, BizTalk Adapter for TIBCO Rendezvous ignores the message target namespace and root element.</span></span> <span data-ttu-id="b9a97-113">Lors de l'envoi de messages par l'adaptateur, ce dernier envoie la charge en l'état.</span><span class="sxs-lookup"><span data-stu-id="b9a97-113">If the adapter sends messages, it sends the payload as is.</span></span> <span data-ttu-id="b9a97-114">Lors de la création d'un message structuré TIBCO Rendezvous par l'adaptateur, le nom de l'élément racine est ignoré (un message n'a pas de nom).</span><span class="sxs-lookup"><span data-stu-id="b9a97-114">If the adapter generates a structured TIBCO Rendezvous message, the name of the root element is ignored (a message does not have a name).</span></span> <span data-ttu-id="b9a97-115">Dans chaque situation, l'adaptateur fait appel à une propriété de contexte pour rechercher l'objet à utiliser lors de la publication du message.</span><span class="sxs-lookup"><span data-stu-id="b9a97-115">In every case, the adapter uses a context property to find which subject to use when publishing the message.</span></span>  
  
 <span data-ttu-id="b9a97-116">Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md) et [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="b9a97-116">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md) and [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a97-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9a97-117">See Also</span></span>  
 <span data-ttu-id="b9a97-118">[Création de Ports d’envoi](../core/creating-send-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="b9a97-118">[Creating Send Ports](../core/creating-send-ports2.md) </span></span>  
 [<span data-ttu-id="b9a97-119">Création gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="b9a97-119">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
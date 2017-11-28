---
title: "À l’aide de Ports d’envoi TIBCO Rendezvous à partir de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 950c4c367fe053195ba14029405f5015381fc6be
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="using-tibco-rendezvous-send-ports"></a><span data-ttu-id="fb61c-102">À l’aide de Ports d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="fb61c-102">Using TIBCO Rendezvous Send Ports</span></span>
<span data-ttu-id="fb61c-103">Un port de transmission peut envoyer tout type de message.</span><span class="sxs-lookup"><span data-stu-id="fb61c-103">A transmit port can send any kind of message.</span></span> <span data-ttu-id="fb61c-104">Lorsque BizTalk Server envoie un message via l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous, l'adaptateur génère le message d'après les valeurs des propriétés de contexte du message ou sur la base des valeurs par défaut, puis il l'envoie vers l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="fb61c-104">When BizTalk Server sends a message through Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter generates the message based on message context properties values, or it uses the default and sends it to the specified subject.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb61c-105">Selon la documentation de TIBCO Rendezvous, les caractères génériques ne sont pas pris en charge dans les noms d'objets de transmission.</span><span class="sxs-lookup"><span data-stu-id="fb61c-105">According to the TIBCO Rendezvous documentation, wildcard characters are not supported in transmit subject names.</span></span>  
  
## <a name="message-handling"></a><span data-ttu-id="fb61c-106">Gestion des messages</span><span class="sxs-lookup"><span data-stu-id="fb61c-106">Message Handling</span></span>  
 <span data-ttu-id="fb61c-107">L'adaptateur conserve un état et traite les messages BizTalk Server entrants en conséquence.</span><span class="sxs-lookup"><span data-stu-id="fb61c-107">The adapter maintains a state and handles incoming BizTalk Server messages accordingly.</span></span>  
  
-   <span data-ttu-id="fb61c-108">Lorsqu'un message ne peut pas être envoyé à cause d'une défaillance au niveau du transport, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="fb61c-108">If a message cannot be sent because of transport failure, BizTalk Server is instructed to resubmit later.</span></span>  
  
-   <span data-ttu-id="fb61c-109">Lorsqu'un message ne peut pas être envoyé car l'adaptateur est toujours en cours d'initialisation, le message BizTalk Server est mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fb61c-109">If a message cannot be sent because the adapter is still initializing, the BizTalk Server message is queued.</span></span> <span data-ttu-id="fb61c-110">Si l'initialisation échoue, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="fb61c-110">If initialization fails, BizTalk Server is instructed to resubmit later.</span></span>  
  
## <a name="message-generation"></a><span data-ttu-id="fb61c-111">Création de messages</span><span class="sxs-lookup"><span data-stu-id="fb61c-111">Message Generation</span></span>  
 <span data-ttu-id="fb61c-112">Grâce à l'adaptateur de transmission, l'adaptateur BizTalk pour TIBCO Rendezvous ignore l'espace de noms cible du message et l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="fb61c-112">With the transmit adapter, BizTalk Adapter for TIBCO Rendezvous ignores the message target namespace and root element.</span></span> <span data-ttu-id="fb61c-113">Lors de l'envoi de messages par l'adaptateur, ce dernier envoie la charge en l'état.</span><span class="sxs-lookup"><span data-stu-id="fb61c-113">If the adapter sends messages, it sends the payload as is.</span></span> <span data-ttu-id="fb61c-114">Lors de la création d'un message structuré TIBCO Rendezvous par l'adaptateur, le nom de l'élément racine est ignoré (un message n'a pas de nom).</span><span class="sxs-lookup"><span data-stu-id="fb61c-114">If the adapter generates a structured TIBCO Rendezvous message, the name of the root element is ignored (a message does not have a name).</span></span> <span data-ttu-id="fb61c-115">Dans chaque situation, l'adaptateur fait appel à une propriété de contexte pour rechercher l'objet à utiliser lors de la publication du message.</span><span class="sxs-lookup"><span data-stu-id="fb61c-115">In every case, the adapter uses a context property to find which subject to use when publishing the message.</span></span>  
  
 <span data-ttu-id="fb61c-116">Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md) et [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="fb61c-116">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md) and [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  

## <a name="using-biztalk-to-send-messages"></a><span data-ttu-id="fb61c-117">À l’aide de BizTalk pour envoyer des Messages</span><span class="sxs-lookup"><span data-stu-id="fb61c-117">Using BizTalk to Send Messages</span></span>
<span data-ttu-id="fb61c-118">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise l'API asynchrone (Transport.Send).</span><span class="sxs-lookup"><span data-stu-id="fb61c-118">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send).</span></span> <span data-ttu-id="fb61c-119">Vous pouvez spécifier le type de message envoyé par l'adaptateur à l'aide d'une propriété de contexte de message :</span><span class="sxs-lookup"><span data-stu-id="fb61c-119">You can specify what kind of message the adapter sends using a message context property:</span></span>  
  
-   <span data-ttu-id="fb61c-120">**Structuré**: l’adaptateur génère un message structuré TIBRVMSG_MSG, basé sur les données XML reçues de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fb61c-120">**Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server.</span></span> <span data-ttu-id="fb61c-121">(*)</span><span class="sxs-lookup"><span data-stu-id="fb61c-121">(*)</span></span>  
  
 <span data-ttu-id="fb61c-122">Si BizTalk Server envoie un message avec des champs dont le nom comporte plus de 127 caractères, l'adaptateur BizTalk pour TIBCO Rendezvous tronque les noms en fonction de la taille de nom de champ maximale pour TIBCO Rendezvous (127).</span><span class="sxs-lookup"><span data-stu-id="fb61c-122">If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.</span></span>  
  
 <span data-ttu-id="fb61c-123">Si une propriété `reply subject name` est fournie, elle est utilisée pour définir l'objet de réponse sur le message TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="fb61c-123">If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message.</span></span> <span data-ttu-id="fb61c-124">Il est supposé qu'un port de réception est défini pour écouter la réponse et la transmettre à BizTalk Server, ou qu'un autre programme TIBCO Rendezvous traite la réponse.</span><span class="sxs-lookup"><span data-stu-id="fb61c-124">It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.</span></span>  
  
 <span data-ttu-id="fb61c-125">Le triplet (service, démon, réseau) constitue la configuration de transport.</span><span class="sxs-lookup"><span data-stu-id="fb61c-125">The triplet (service, daemon, network) makes up the transport configuration.</span></span> <span data-ttu-id="fb61c-126">Une configuration de transport vide (par défaut) entraîne l'envoi d'un message via l'objet de transport par défaut.</span><span class="sxs-lookup"><span data-stu-id="fb61c-126">An empty (default) transport configuration results in a message being sent through the default transport object.</span></span>  
  
 <span data-ttu-id="fb61c-127">Si la page de code n'est pas spécifiée, l'adaptateur utilise le codage UTF-8 (page de code 65001).</span><span class="sxs-lookup"><span data-stu-id="fb61c-127">If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001).</span></span> <span data-ttu-id="fb61c-128">Les messages certifiés ne sont pas pris en charge du côté transmetteur.</span><span class="sxs-lookup"><span data-stu-id="fb61c-128">Certified Messages are not supported on the transmitter side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb61c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb61c-129">See Also</span></span>  
 <span data-ttu-id="fb61c-130">[Création de Ports d’envoi](../core/creating-send-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="fb61c-130">[Creating Send Ports](../core/creating-send-ports2.md) </span></span>  
 [<span data-ttu-id="fb61c-131">Création de gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="fb61c-131">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
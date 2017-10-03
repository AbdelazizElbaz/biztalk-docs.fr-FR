---
title: "Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message context properties, BizTalk Server
- reply subjects
- send handlers, BizTalk Server message context properties
- replies
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c8e5ddb1feb02a015fdebd62d183d1b8442fe5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a><span data-ttu-id="f536c-102">Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)</span><span class="sxs-lookup"><span data-stu-id="f536c-102">BizTalk Server Message Context Properties (Send Handlers)</span></span>
<span data-ttu-id="f536c-103">En plus de la charge de message, les informations supplémentaires composant un message doivent être accessibles à partir de l'orchestration BizTalk Server au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f536c-103">In addition to the message payload, the supplementary information that a message contains must be accessible from the BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="f536c-104">Informations de message TIBCO RV promues en tant que propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="f536c-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
  
|<span data-ttu-id="f536c-105">Identification des données</span><span class="sxs-lookup"><span data-stu-id="f536c-105">Data Identification</span></span>|<span data-ttu-id="f536c-106">Type</span><span class="sxs-lookup"><span data-stu-id="f536c-106">Type</span></span>|<span data-ttu-id="f536c-107">Routable</span><span class="sxs-lookup"><span data-stu-id="f536c-107">Routable</span></span>|<span data-ttu-id="f536c-108">Emplacement d'envoi</span><span class="sxs-lookup"><span data-stu-id="f536c-108">Send Location</span></span>|  
|-------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="f536c-109">Objet d'envoi</span><span class="sxs-lookup"><span data-stu-id="f536c-109">Send Subject</span></span>|<span data-ttu-id="f536c-110">chaîne</span><span class="sxs-lookup"><span data-stu-id="f536c-110">string</span></span>|<span data-ttu-id="f536c-111">Oui</span><span class="sxs-lookup"><span data-stu-id="f536c-111">Yes</span></span>|<span data-ttu-id="f536c-112">L'orchestration spécifie l'objet d'envoi TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="f536c-112">Orchestration specifies the TIBCO Rendezvous send subject.</span></span> <span data-ttu-id="f536c-113">Valeur par défaut est Null.</span><span class="sxs-lookup"><span data-stu-id="f536c-113">Default value is Null.</span></span> <span data-ttu-id="f536c-114">Obligatoire, sauf si un objet par défaut est spécifié dans la configuration du port.</span><span class="sxs-lookup"><span data-stu-id="f536c-114">Mandatory unless a default subject is specified in the port configuration.</span></span>|  
|<span data-ttu-id="f536c-115">Objet de réponse</span><span class="sxs-lookup"><span data-stu-id="f536c-115">Reply Subject</span></span>|<span data-ttu-id="f536c-116">chaîne</span><span class="sxs-lookup"><span data-stu-id="f536c-116">string</span></span>|<span data-ttu-id="f536c-117">Oui</span><span class="sxs-lookup"><span data-stu-id="f536c-117">Yes</span></span>|<span data-ttu-id="f536c-118">L'orchestration fournit un objet pour les messages de réponse lorsque c'est approprié.</span><span class="sxs-lookup"><span data-stu-id="f536c-118">Orchestration provides a subject for reply messages, when pertinent.</span></span> <span data-ttu-id="f536c-119">Valeur par défaut est Null.</span><span class="sxs-lookup"><span data-stu-id="f536c-119">Default value is Null.</span></span>|  
  
## <a name="getting-a-tibco-reply"></a><span data-ttu-id="f536c-120">Obtention d'une réponse TIBCO</span><span class="sxs-lookup"><span data-stu-id="f536c-120">Getting a TIBCO Reply</span></span>  
 <span data-ttu-id="f536c-121">**Question :** en quoi l’adaptateur BizTalk pour TIBCO Rendezvous de lecture de manipuler l’objet de réponse à l’intérieur d’une orchestration afin que vous pouvez l’utiliser comme objet d’envoi pour la réponse ?</span><span class="sxs-lookup"><span data-stu-id="f536c-121">**Question:** How does BizTalk Adapter for TIBCO Rendezvous read and manipulate the reply subject inside an orchestration so that you can use it as the send subject for the response?</span></span> <span data-ttu-id="f536c-122">Comment l'adaptateur obtient-il le contexte d'un message entrant de Rendezvous ?</span><span class="sxs-lookup"><span data-stu-id="f536c-122">How does the adapter get to the message context of an incoming message from Rendezvous?</span></span>  
  
 <span data-ttu-id="f536c-123">**Réponse :** l’objet de réponse est renseigné dans le contexte du message entrant et l’orchestration peut le lire.</span><span class="sxs-lookup"><span data-stu-id="f536c-123">**Answer:** The reply subject is populated in the context of the incoming message, and the orchestration can read it.</span></span> <span data-ttu-id="f536c-124">Si l'orchestration fournit finalement une réponse, il peut utiliser la valeur pour définir l'objet d'envoi du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="f536c-124">If the orchestration ultimately produces a reply, it can use that value to set the send subject of the reply message.</span></span>  
  
1.  <span data-ttu-id="f536c-125">Dans un projet BizTalk Server, ajoutez une référence à <répertoire d'installation>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll..</span><span class="sxs-lookup"><span data-stu-id="f536c-125">In a BizTalk Server project, add a reference to <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span>  
  
2.  <span data-ttu-id="f536c-126">Dans l'orchestration (quelque part entre la forme Réception qui remet le message Rendezvous entrant et la forme forme Envoi qui envoie la réponse), ajoutez à la réponse que vous avez construite une forme de construction/d'affectation de message (ou une forme Expression) pour obtenir quelque chose comme l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f536c-126">In the orchestration (somewhere between the Receive shape that is handed the incoming Rendezvous message and the Send shape that is sending the reply), add a message construction/assignment shape (or an expression shape) to do something like the following example to the reply you constructed:</span></span>  
  
    ```  
    OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
    (Rendezvous.ReplySubject);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f536c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f536c-127">See Also</span></span>  
 <span data-ttu-id="f536c-128">[Mappage de Type de données pour les gestionnaires d’envoi dans TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="f536c-128">[Data Type Mapping for Send Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="f536c-129">Création gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="f536c-129">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
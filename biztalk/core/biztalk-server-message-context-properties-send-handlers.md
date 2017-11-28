---
title: "Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0504e13115229f1325938e8ca48acc17fa5bc1d
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a><span data-ttu-id="e6b62-102">Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)</span><span class="sxs-lookup"><span data-stu-id="e6b62-102">BizTalk Server Message Context Properties (Send Handlers)</span></span>
<span data-ttu-id="e6b62-103">En plus de la charge de message, les informations supplémentaires composant un message doivent être accessibles à partir de l'orchestration BizTalk Server au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e6b62-103">In addition to the message payload, the supplementary information that a message contains must be accessible from the BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="e6b62-104">Informations de message TIBCO RV promues en tant que propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="e6b62-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
  
|<span data-ttu-id="e6b62-105">Identification des données</span><span class="sxs-lookup"><span data-stu-id="e6b62-105">Data Identification</span></span>|<span data-ttu-id="e6b62-106">Type</span><span class="sxs-lookup"><span data-stu-id="e6b62-106">Type</span></span>|<span data-ttu-id="e6b62-107">Routable</span><span class="sxs-lookup"><span data-stu-id="e6b62-107">Routable</span></span>|<span data-ttu-id="e6b62-108">Emplacement d'envoi</span><span class="sxs-lookup"><span data-stu-id="e6b62-108">Send Location</span></span>|  
|-------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="e6b62-109">Objet d'envoi</span><span class="sxs-lookup"><span data-stu-id="e6b62-109">Send Subject</span></span>|<span data-ttu-id="e6b62-110">chaîne</span><span class="sxs-lookup"><span data-stu-id="e6b62-110">string</span></span>|<span data-ttu-id="e6b62-111">Oui</span><span class="sxs-lookup"><span data-stu-id="e6b62-111">Yes</span></span>|<span data-ttu-id="e6b62-112">L'orchestration spécifie l'objet d'envoi TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="e6b62-112">Orchestration specifies the TIBCO Rendezvous send subject.</span></span> <span data-ttu-id="e6b62-113">Valeur par défaut est Null.</span><span class="sxs-lookup"><span data-stu-id="e6b62-113">Default value is Null.</span></span> <span data-ttu-id="e6b62-114">Obligatoire, sauf si un objet par défaut est spécifié dans la configuration du port.</span><span class="sxs-lookup"><span data-stu-id="e6b62-114">Mandatory unless a default subject is specified in the port configuration.</span></span>|  
|<span data-ttu-id="e6b62-115">Objet de réponse</span><span class="sxs-lookup"><span data-stu-id="e6b62-115">Reply Subject</span></span>|<span data-ttu-id="e6b62-116">chaîne</span><span class="sxs-lookup"><span data-stu-id="e6b62-116">string</span></span>|<span data-ttu-id="e6b62-117">Oui</span><span class="sxs-lookup"><span data-stu-id="e6b62-117">Yes</span></span>|<span data-ttu-id="e6b62-118">L'orchestration fournit un objet pour les messages de réponse lorsque c'est approprié.</span><span class="sxs-lookup"><span data-stu-id="e6b62-118">Orchestration provides a subject for reply messages, when pertinent.</span></span> <span data-ttu-id="e6b62-119">Valeur par défaut est Null.</span><span class="sxs-lookup"><span data-stu-id="e6b62-119">Default value is Null.</span></span>|  
  
## <a name="getting-a-tibco-reply"></a><span data-ttu-id="e6b62-120">Obtention d'une réponse TIBCO</span><span class="sxs-lookup"><span data-stu-id="e6b62-120">Getting a TIBCO Reply</span></span>  
 <span data-ttu-id="e6b62-121">**Question :** en quoi l’adaptateur BizTalk pour TIBCO Rendezvous de lecture de manipuler l’objet de réponse à l’intérieur d’une orchestration afin que vous pouvez l’utiliser comme objet d’envoi pour la réponse ?</span><span class="sxs-lookup"><span data-stu-id="e6b62-121">**Question:** How does BizTalk Adapter for TIBCO Rendezvous read and manipulate the reply subject inside an orchestration so that you can use it as the send subject for the response?</span></span> <span data-ttu-id="e6b62-122">Comment l'adaptateur obtient-il le contexte d'un message entrant de Rendezvous ?</span><span class="sxs-lookup"><span data-stu-id="e6b62-122">How does the adapter get to the message context of an incoming message from Rendezvous?</span></span>  
  
 <span data-ttu-id="e6b62-123">**Réponse :** l’objet de réponse est renseigné dans le contexte du message entrant et l’orchestration peut le lire.</span><span class="sxs-lookup"><span data-stu-id="e6b62-123">**Answer:** The reply subject is populated in the context of the incoming message, and the orchestration can read it.</span></span> <span data-ttu-id="e6b62-124">Si l'orchestration fournit finalement une réponse, il peut utiliser la valeur pour définir l'objet d'envoi du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="e6b62-124">If the orchestration ultimately produces a reply, it can use that value to set the send subject of the reply message.</span></span>  
  
1.  <span data-ttu-id="e6b62-125">Dans un projet BizTalk Server, ajoutez une référence à <répertoire d'installation>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span><span class="sxs-lookup"><span data-stu-id="e6b62-125">In a BizTalk Server project, add a reference to <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span>  
  
2.  <span data-ttu-id="e6b62-126">Dans l'orchestration (quelque part entre la forme Réception qui remet le message Rendezvous entrant et la forme forme Envoi qui envoie la réponse), ajoutez à la réponse que vous avez construite une forme de construction/d'affectation de message (ou une forme Expression) pour obtenir quelque chose comme l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e6b62-126">In the orchestration (somewhere between the Receive shape that is handed the incoming Rendezvous message and the Send shape that is sending the reply), add a message construction/assignment shape (or an expression shape) to do something like the following example to the reply you constructed:</span></span>  
  
    ```  
    OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
    (Rendezvous.ReplySubject);  
    ```  
## <a name="management-assembly"></a><span data-ttu-id="e6b62-127">Assembly de gestion</span><span class="sxs-lookup"><span data-stu-id="e6b62-127">Management assembly</span></span>
<span data-ttu-id="e6b62-128">TIBCO Rendezvous n'inclut pas de référentiels de métadonnées. Par ailleurs, l'assembly de gestion de l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'inclut pas de fonctionnalités de navigation ou de génération de schémas.</span><span class="sxs-lookup"><span data-stu-id="e6b62-128">TIBCO Rendezvous does not provide metadata repositories, and Microsoft BizTalk Adapter for TIBCO Rendezvous management assembly does not provide browsing capabilities or schema generation.</span></span> <span data-ttu-id="e6b62-129">Vous devez donc fournir un schéma à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e6b62-129">Therefore, you must provide a schema to BizTalk Server.</span></span> <span data-ttu-id="e6b62-130">Pour plus d’informations, consultez [installation, les schémas et les limitations](../core/installing-biztalk-adapter-for-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="e6b62-130">For more information, see [Install, schemas, & limitations](../core/installing-biztalk-adapter-for-tibco-rendezvous.md).</span></span>
  
 <span data-ttu-id="e6b62-131">L'adaptateur BizTalk pour TIBCO Rendezvous inclut un schéma avec des types prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="e6b62-131">BizTalk Adapter for TIBCO Rendezvous includes a schema with predefined types.</span></span> <span data-ttu-id="e6b62-132">L'adaptateur utilise ces types lors de la génération de messages pour certains types de données spécifiques (tableaux).</span><span class="sxs-lookup"><span data-stu-id="e6b62-132">The adapter uses these types when generating messages for some specific data types (arrays).</span></span>

  
## <a name="see-also"></a><span data-ttu-id="e6b62-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6b62-133">See Also</span></span>  
 <span data-ttu-id="e6b62-134">[Mappage de Type de données pour les gestionnaires d’envoi dans TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="e6b62-134">[Data Type Mapping for Send Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="e6b62-135">Création de gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="e6b62-135">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
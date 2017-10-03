---
title: Adaptateurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- adapters
- send adapters
- adapters, about adapters
- send adapters, about send adapters
- receive adapters, about receive adapters
- adapters, adapter framework
- receive adapters
- adapters, send adapters
ms.assetid: 7803a806-3396-4662-877f-eae11cb5e3e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a7f58a9d67b9702cfbb7b21788f751717ac61e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapters"></a><span data-ttu-id="3a9ef-102">Adaptateurs</span><span class="sxs-lookup"><span data-stu-id="3a9ef-102">Adapters</span></span>
<span data-ttu-id="3a9ef-103">Pour échanger des messages avec des systèmes externes, des applications et des entités, Microsoft BizTalk Server fait appel aux adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-103">To exchange messages with external systems, applications, and entities Microsoft BizTalk Server uses the concept of an adapter.</span></span> <span data-ttu-id="3a9ef-104">*Adaptateurs* sont COM ou. Les composants NET qui transfèrent les messages vers et à partir de la terminaison de l’entreprise (par exemple, les systèmes de fichiers, les bases de données et les applications d’entreprise personnalisées) à l’aide de divers protocoles de communication.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-104">*Adapters* are COM or .NET-based components that transfer messages to and from business endpoints (such as file systems, databases, and custom business applications) using various communication protocols.</span></span>  
  
 <span data-ttu-id="3a9ef-105">BizTalk Server les utilisent pour échanger des messages avec des entités externes dans le cadre d'opérations d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="3a9ef-105">Adapters are used by BizTalk Server to exchange messages with external entities in send and receive operations</span></span>  
  
-   <span data-ttu-id="3a9ef-106">Les opérations d'envoi (ou côté envoi) ont lieu lorsque des informations sont envoyées par BizTalk Server à une entité externe à l'aide des divers protocoles pris en charge par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-106">Send (or send-side) operations occur when information is being sent by BizTalk Server to an external entity using the protocols supported by the adapter.</span></span>  
  
-   <span data-ttu-id="3a9ef-107">Les opérations de réception (ou côté réception) ont lieu lorsque l'adaptateur reçoit des informations provenant d'une entité externe et les transmet au moteur de messagerie BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-107">Receive (or receive-side) operations occur when the adapter receives information from an external entity and passes it into the BizTalk Server Messaging Engine.</span></span>  
  
## <a name="the-adapter-framework"></a><span data-ttu-id="3a9ef-108">Infrastructure de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="3a9ef-108">The Adapter Framework</span></span>  
 <span data-ttu-id="3a9ef-109">La figure suivante montre comment fonctionnent un adaptateur et l'infrastructure d'adaptateurs pour connecter votre application à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-109">The following figure shows how an adapter and the Adapter Framework work together to connect your application to BizTalk Server.</span></span>  
  
1.  <span data-ttu-id="3a9ef-110">Les données sont reçues à un emplacement de réception qui écoute les messages d'un protocole donné à une adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-110">Data is received through a receive location that is listening for messages of a certain protocol at a specified address.</span></span> <span data-ttu-id="3a9ef-111">Cet emplacement de réception est associé à un adaptateur et à un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-111">The receive location is associated with an adapter and a receive pipeline.</span></span> <span data-ttu-id="3a9ef-112">Vous pouvez configurer à la fois l'adaptateur et les composants de pipeline pour appliquer une logique spécifique aux messages associés à un protocole prédéterminé.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-112">You can configure both the adapter and the pipeline components to perform certain logic on messages having a predetermined protocol.</span></span>  
  
2.  <span data-ttu-id="3a9ef-113">Une fois que le message a été reçu à l'emplacement de réception, il est transmis à l'adaptateur, qui, à sont tour, crée un message BizTalk Server. L'adaptateur joint ensuite le flux de données au message (généralement dans le corps du message), ajoute les métadonnées appartenant au point de terminaison depuis lequel les données ont été reçues, puis soumet le message au moteur de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-113">After the message is received by the receive location, the message is sent to the adapter, which creates a new BizTalk Server message, attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint over which the data was received, and then submits that message into the Messaging Engine.</span></span>  
  
3.  <span data-ttu-id="3a9ef-114">Le moteur de messagerie envoie le message au pipeline de réception au sein duquel plusieurs opérations ont lieu : conversion des données au format XML, authentification de l'expéditeur du message, décryptage du message et validation des données XML.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-114">The Messaging Engine sends the message to the receive pipeline where the data is transformed into XML, the message sender is authenticated, the message is decrypted, and the XML is validated.</span></span>  
  
4.  <span data-ttu-id="3a9ef-115">Le moteur de messagerie publie le message dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-115">The Messaging Engine publishes the message to the MessageBox.</span></span> <span data-ttu-id="3a9ef-116">Cette base de données est une table Microsoft SQL Server qui contient les messages à traiter.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-116">The MessageBox is a Microsoft SQL Server table containing messages to be processed.</span></span> <span data-ttu-id="3a9ef-117">Les orchestrations et les ports d'envoi peuvent s'y abonner.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-117">Both orchestrations and send ports can subscribe to the MessageBox.</span></span>  
  
5.  <span data-ttu-id="3a9ef-118">Le moteur de messagerie envoie le message soit à une orchestration, soit à un port d'envoi abonné en fonction des propriétés de contexte du message correspondant aux spécifications définies dans le filtre de l'abonné.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-118">The Messaging Engine sends the message to either an orchestration or a send port subscriber based upon the message context properties matching the specifications set in the filter on the subscriber.</span></span>  
  
6.  <span data-ttu-id="3a9ef-119">Si une orchestration est l’abonné, il traite le message et l’envoie à l’aide d’un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-119">If an orchestration is the subscriber, it processes the message and sends it out using a send port.</span></span> <span data-ttu-id="3a9ef-120">Une fois que le port d'envoi a envoyé le message ou s'il n'est que le seul abonné, le message passe par le pipeline d'envoi, puis par un adaptateur d'envoi avant d'être transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-120">After the send port has it, or is the only subscriber, the message passes through the send pipeline into a send adapter before being transmitted over the wire.</span></span>  
  
 <span data-ttu-id="3a9ef-121">Infrastructure de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="3a9ef-121">The Adapter Framework</span></span>  
  
 <span data-ttu-id="3a9ef-122">![L’infrastructure d’adaptateurs](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span><span class="sxs-lookup"><span data-stu-id="3a9ef-122">![The adapter framework](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span></span>  
  
## <a name="receive-adapters"></a><span data-ttu-id="3a9ef-123">Adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="3a9ef-123">Receive Adapters</span></span>  
 <span data-ttu-id="3a9ef-124">Un adaptateur de réception est chargé de créer un message BizTalk Server en joignant le flux de données réseau/sources au corps du message.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-124">Receive adapters are responsible for creating a new BizTalk Server message by attaching the network/data source stream to the message body.</span></span> <span data-ttu-id="3a9ef-125">Il ajoute également les métadonnées pertinentes au point de terminaison sur lequel les données a été reçues, puis soumet le message au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-125">It also adds any metadata pertinent to the endpoint over which the data was received, then submits that message to the Messaging Engine.</span></span>  
  
 <span data-ttu-id="3a9ef-126">L'adaptateur supprime les données du point de terminaison de réception ou envoie l'accusé de réception approprié au client en lui indiquant que les données ont été acceptées dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-126">The adapter deletes the data from the receive endpoint or sends the appropriate acknowledgement message to the client indicating that the data has been accepted into BizTalk Server.</span></span>  
  
## <a name="send-adapters"></a><span data-ttu-id="3a9ef-127">Adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="3a9ef-127">Send Adapters</span></span>  
 <span data-ttu-id="3a9ef-128">Un adaptateur d'envoi est chargé d'envoyer un message BizTalk à un point de terminaison spécifié à l'aide d'un protocole qui lui est spécifique.</span><span class="sxs-lookup"><span data-stu-id="3a9ef-128">Send adapters are responsible for sending a BizTalk message to the specified endpoint using its specific transport protocol.</span></span>  
  
 <span data-ttu-id="3a9ef-129">Pour plus d’informations à propos des adaptateurs, la structure d’un adaptateur et l’écriture des adaptateurs personnalisés, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="3a9ef-129">For more information about adapters, the structure of an adapter, and writing custom adapters, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9ef-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a9ef-130">See Also</span></span>  
 [<span data-ttu-id="3a9ef-131">Artefacts</span><span class="sxs-lookup"><span data-stu-id="3a9ef-131">Artifacts</span></span>](../core/artifacts.md)
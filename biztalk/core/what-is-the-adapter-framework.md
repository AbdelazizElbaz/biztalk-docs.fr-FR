---
title: "Présentation de l'infrastructure d'adaptateurs | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd1e2fd7-4e77-49c4-839d-c2bf16b10ba2
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 648c22a52e543b24458daa73146836e1e3a5463e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-adapter-framework"></a><span data-ttu-id="3c4cd-103">Présentation de l'infrastructure d'adaptateurs</span><span class="sxs-lookup"><span data-stu-id="3c4cd-103">What Is the Adapter Framework?</span></span>
<span data-ttu-id="3c4cd-104">L'infrastructure d'adaptateurs BizTalk offre un mécanisme ouvert et stable permettant à tous les adaptateurs d'implémenter des données ou d'y accéder à partir du moteur de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c4cd-104">The BizTalk Adapter Framework offers a stable, open mechanism for all adapters to implement or access work from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messaging Engine.</span></span> <span data-ttu-id="3c4cd-105">Les interfaces décrites dans le **Microsoft.BizTalk.adaptateur.Framework** espace de noms permettent aux adaptateurs fournissent un moyen de modifier des pages de propriétés de configuration.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-105">The interfaces described in the **Microsoft.BizTalk.Adapter.Framework** namespace enable adapters to provide a means to modify configuration property pages.</span></span> <span data-ttu-id="3c4cd-106">Elles sont également un moyen d'importer des services et des schémas dans le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-106">It also is a means to import services and schemas into the BizTalk project.</span></span>  
  
 <span data-ttu-id="3c4cd-107">La figure suivante montre comment un adaptateur et l'infrastructure d'adaptateurs s'associent pour connecter votre application à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c4cd-107">The following figure shows how an adapter and the Adapter Framework work together to connect your application to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3c4cd-108">![L’infrastructure d’adaptateurs](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span><span class="sxs-lookup"><span data-stu-id="3c4cd-108">![The adapter framework](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span></span>  
  
 <span data-ttu-id="3c4cd-109">Les étapes suivantes décrivent la séquence d'étapes montrées dans cette figure :</span><span class="sxs-lookup"><span data-stu-id="3c4cd-109">The following steps describe the sequence of steps shown in this figure:</span></span>  
  
1.  <span data-ttu-id="3c4cd-110">Les données sont reçues d'un emplacement de réception qui écoute les messages ayant un protocole donné à une adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-110">Data is received from a receive location that is listening for messages with a certain protocol at a specified address.</span></span> <span data-ttu-id="3c4cd-111">Cet emplacement de réception est associé à un adaptateur et à un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-111">The receive location is associated with an adapter and a receive pipeline.</span></span> <span data-ttu-id="3c4cd-112">Vous pouvez configurer à la fois l'adaptateur et les composants de pipeline pour appliquer une logique spécifique aux messages d'un protocole prédéterminé.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-112">You can configure both the adapter and the pipeline components to perform certain logic on messages of a predetermined protocol.</span></span>  
  
2.  <span data-ttu-id="3c4cd-113">Une fois que le message a été reçu à l'emplacement de réception, il est transmis à l'adaptateur, qui, à sont tour, crée un message BizTalk. L'adaptateur joint ensuite le flux de données au message (généralement dans le corps du message), ajoute les métadonnées appartenant au point de terminaison depuis lequel les données ont été reçues, puis soumet le message au moteur de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-113">After the message is received by the receive location, the message is sent to the adapter, which creates a new BizTalk message, attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint over which the data was received, and then submits that message into the Messaging Engine.</span></span>  
  
3.  <span data-ttu-id="3c4cd-114">Le moteur de messagerie envoie le message au pipeline de réception au sein duquel plusieurs opérations ont lieu : conversion des données au format XML, authentification de l'expéditeur du message, décryptage du message et validation des données XML.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-114">The Messaging Engine sends the message to the receive pipeline where the data is transformed into XML, the message sender is authenticated, the message is decrypted, and the XML is validated.</span></span>  
  
4.  <span data-ttu-id="3c4cd-115">Le moteur de messagerie publie le message sur la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-115">The Messaging Engine publishes the message to the MessageBox database.</span></span> <span data-ttu-id="3c4cd-116">Cette base de données est une table Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui contient les messages à traiter.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-116">The MessageBox is a Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] table containing messages to be processed.</span></span> <span data-ttu-id="3c4cd-117">Les orchestrations et les ports d'envoi peuvent s'y abonner.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-117">Both orchestrations and send ports can subscribe to the MessageBox.</span></span>  
  
5.  <span data-ttu-id="3c4cd-118">Le moteur de messagerie envoie le message soit à une orchestration, soit à un port d'envoi abonné en fonction des propriétés de contexte du message correspondant aux spécifications définies dans le filtre de l'abonné.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-118">The Messaging Engine sends the message to either an orchestration or a send port subscriber based upon the message context properties matching the specifications set in the filter on the subscriber.</span></span>  
  
6.  <span data-ttu-id="3c4cd-119">Si une orchestration est l'abonné, elle traite le message et l'envoie via un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-119">If an orchestration is the subscriber, it processes the message and sends it out through a send port.</span></span> <span data-ttu-id="3c4cd-120">Si l'abonné est un port d'envoi, le message passe par le pipeline d'envoi, puis par un adaptateur d'envoi avant d'être transmis.</span><span class="sxs-lookup"><span data-stu-id="3c4cd-120">If the subscriber is a send the message passes through the send pipeline into a send adapter before being transmitted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c4cd-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3c4cd-121">In This Section</span></span>  
  
-   [<span data-ttu-id="3c4cd-122">L’utilisation des outils de Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="3c4cd-122">Using the Adapter Framework Tools</span></span>](../core/using-the-adapter-framework-tools.md)  
  
-   [<span data-ttu-id="3c4cd-123">Modèles d’échange de Message de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3c4cd-123">Adapter Message Exchange Patterns</span></span>](../core/adapter-message-exchange-patterns.md)  
  
-   [<span data-ttu-id="3c4cd-124">Composants d’adaptateur Framework</span><span class="sxs-lookup"><span data-stu-id="3c4cd-124">Adapter Framework Components</span></span>](../core/adapter-framework-components.md)  
  
-   [<span data-ttu-id="3c4cd-125">Modèle d’hébergement de carte</span><span class="sxs-lookup"><span data-stu-id="3c4cd-125">Adapter Hosting Model</span></span>](../core/adapter-hosting-model.md)  
  
-   [<span data-ttu-id="3c4cd-126">Composants de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3c4cd-126">Adapter Components</span></span>](../core/adapter-components.md)
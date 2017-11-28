---
title: "Présentation de l'adaptateur MQSeries | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, about MQSeries adapters
- MQSeries adapters
ms.assetid: fd3dfa9a-344a-46e5-a342-bc56da7c1c50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f72d0012050fc8022b53120377aeb648641d21f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-mqseries-adapter"></a><span data-ttu-id="6b23b-103">Présentation de l'adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6b23b-103">What Is the MQSeries Adapter?</span></span>
<span data-ttu-id="6b23b-104">L'adaptateur MQSeries permet d'envoyer et de recevoir des messages avec les systèmes MQSeries à l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b23b-104">With the MQSeries adapter you can send and receive messages to MQSeries systems using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6b23b-105">Cet adaptateur s'appuie sur MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="6b23b-105">The adapter relies on MQSeries Server for Windows.</span></span> <span data-ttu-id="6b23b-106">Cette conception garantit la fiabilité de la messagerie du fait que MQSeries Server pour Windows prend en charge le composant MSDTC (Microsoft Distributed Transaction Coordinator).</span><span class="sxs-lookup"><span data-stu-id="6b23b-106">This design guarantees reliable messaging because MQSeries Server for Windows supports Microsoft Distributed Transaction Coordinator (MSDTC).</span></span>  
  
 <span data-ttu-id="6b23b-107">L'adaptateur prend en charge les serveurs MQSeries et les gestionnaires de file d'attente MQSeries mis en clusters, ainsi que les serveurs BizTalk mis en cluster.</span><span class="sxs-lookup"><span data-stu-id="6b23b-107">The adapter supports clustered MQSeries Servers and clustered MQSeries Queue Managers, and also clustered BizTalk servers.</span></span>  
  
 <span data-ttu-id="6b23b-108">Vous pouvez utiliser l'adaptateur MQSeries pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b23b-108">You can do the following with the MQSeries adapter:</span></span>  
  
-   <span data-ttu-id="6b23b-109">Envoyer des messages aux files d'attente de définitions distantes MQSeries, aux files d'attente locales, aux files d'attente de transmission et aux files d'attente d'alias depuis BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6b23b-109">Send messages to MQSeries remote definition queues, local queues, transmission queues, and alias queues from BizTalk Server.</span></span>  
  
-   <span data-ttu-id="6b23b-110">Recevoir des messages à partir de files d'attente de transmission MQSeries, de files d'attente locales et de files d'attente d'alias.</span><span class="sxs-lookup"><span data-stu-id="6b23b-110">Receive messages from MQSeries transmission queues, local queues, and alias queues.</span></span>  
  
-   <span data-ttu-id="6b23b-111">Envoyer et recevoir des messages depuisMQSeries Server pour Windows (MQSeries Server peut être exécuté sur le même ordinateur que BizTalk Server ou sur une installation distante).</span><span class="sxs-lookup"><span data-stu-id="6b23b-111">Send and receive messages from MQSeries Server for Windows (MQSeries Server can run on the same computer as BizTalk Server or on a remote installation).</span></span> <span data-ttu-id="6b23b-112">Vous ne devez déployer qu'une copie de MQSAgent (le composant COM+ de l'adaptateur) pour prendre en charge l'ensemble de vos installations BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6b23b-112">You only have to deploy one copy of MQSAgent (the COM+ component of the adapter) to support all your BizTalk Server installations.</span></span>  
  
-   <span data-ttu-id="6b23b-113">Interroger MQSeries Server avec un intervalle d'attente.</span><span class="sxs-lookup"><span data-stu-id="6b23b-113">Poll MQSeries Server with a wait interval.</span></span>  
  
-   <span data-ttu-id="6b23b-114">Utiliser des ports d'envoi dynamiques pour contrôler l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6b23b-114">Use dynamic send ports to control the adapter.</span></span>  
  
-   <span data-ttu-id="6b23b-115">Créer des files d'attente de manière dynamique lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6b23b-115">Dynamically create queues at run time.</span></span>  
  
-   <span data-ttu-id="6b23b-116">Recevoir des messages de manière dynamique à partir de files d'attente basées sur MQSeries MatchOptions.</span><span class="sxs-lookup"><span data-stu-id="6b23b-116">Dynamically receive messages from queues based upon MQSeries MatchOptions.</span></span>  
  
-   <span data-ttu-id="6b23b-117">Mettre en correspondance les propriétés de contexte aux propriétés d'en-tête, à la fois pour la transmission et la réception de messages.</span><span class="sxs-lookup"><span data-stu-id="6b23b-117">Map context properties to header properties for both transmitting and receiving messages.</span></span> <span data-ttu-id="6b23b-118">Vous pouvez obtenir et définir les propriétés d'en-tête MQSeries (y compris MQMD, MQXQH, MQCIH et MQIIH) par le biais des propriétés de contexte BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6b23b-118">You can get and set MQSeries header properties (including MQMD, MQXQH, MQCIH, and MQIIH) through BizTalk Server context properties.</span></span>  
  
-   <span data-ttu-id="6b23b-119">Permettre la corrélation avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou MQSeries Server qui crée l'identificateur de corrélation.</span><span class="sxs-lookup"><span data-stu-id="6b23b-119">Enable correlation with either [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or MQSeries Server creating the correlation identifier.</span></span>  
  
-   <span data-ttu-id="6b23b-120">Demander la remise transactionnelle et non transactionnelle de messages pour l'envoi et la réception.</span><span class="sxs-lookup"><span data-stu-id="6b23b-120">Request transactional and nontransactional delivery of messages for send and receive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b23b-121">Lors de l'utilisation de fonctionnalités telles que MQSeries qui effectuent des appels DCOM (Distributed Component Object Model) au serveur, vérifiez que vous n'avez pas de pare-feu de traduction d'adresses réseau (NAT, Network Address Translation) activé.</span><span class="sxs-lookup"><span data-stu-id="6b23b-121">When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled.</span></span> <span data-ttu-id="6b23b-122">Le client doit pouvoir accéder au serveur par son adresse IP réelle, or les pare-feu NAT convertissent cette adresse en un élément non reconnu par le client.</span><span class="sxs-lookup"><span data-stu-id="6b23b-122">The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b23b-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6b23b-123">In This Section</span></span>  
  
-   [<span data-ttu-id="6b23b-124">Composants de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6b23b-124">Components of the MQSeries Adapter</span></span>](../core/components-of-the-mqseries-adapter.md)  
  
-   [<span data-ttu-id="6b23b-125">Architecture de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6b23b-125">MQSeries Adapter Architecture</span></span>](../core/mqseries-adapter-architecture.md)  
  
-   [<span data-ttu-id="6b23b-126">À l’aide de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6b23b-126">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)  
  
-   [<span data-ttu-id="6b23b-127">Sécurité de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6b23b-127">MQSeries Adapter Security</span></span>](../core/mqseries-adapter-security.md)
---
title: "Vue d’ensemble de la boîte à outils ESB dans BizTalk Server | Documents Microsoft"
description: "Explication de la boîte à outils ESB, et ce qu’il fait dans BizTalk Server"
caps.latest.revision: "6"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: mandia
ms.openlocfilehash: 9ce0bbe3710530a63127701447db87b0a3135b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-biztalk-esb-toolkit"></a><span data-ttu-id="9478b-103">Nouveautés de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="9478b-103">What is the BizTalk ESB Toolkit</span></span>

## <a name="overview"></a><span data-ttu-id="9478b-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="9478b-104">Overview</span></span>
<span data-ttu-id="9478b-105">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour prendre en charge une architecture de messagerie faiblement couplée.</span><span class="sxs-lookup"><span data-stu-id="9478b-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the capabilities of BizTalk Server to support a loosely coupled messaging architecture.</span></span> <span data-ttu-id="9478b-106">La plupart des développeurs connaissent des paradigmes de développement orienté code, procédures ou orientée objet.</span><span class="sxs-lookup"><span data-stu-id="9478b-106">Most developers are familiar with code-oriented, procedural, or object-oriented development paradigms.</span></span> <span data-ttu-id="9478b-107">Toutefois, lors du démarrage de développer des solutions BizTalk, les développeurs ont tendance à ignorer les fonctionnalités orienté messages de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9478b-107">However, when starting to develop BizTalk solutions, developers tend to overlook the message-oriented capabilities of BizTalk Server.</span></span>  
  
 <span data-ttu-id="9478b-108">BizTalk Server comprend un mécanisme de publication/abonnement puissant qui fonctionne en créant et en remplissant des abonnements.</span><span class="sxs-lookup"><span data-stu-id="9478b-108">BizTalk Server includes a powerful publish/subscribe mechanism that works by creating and filling subscriptions.</span></span> <span data-ttu-id="9478b-109">Lorsqu’un nouveau message arrive dans la base de données MessageBox de BizTalk, un agent de message identifie les abonnés et envoie le message à des points de terminaison qui ont des abonnements.</span><span class="sxs-lookup"><span data-stu-id="9478b-109">When a new message arrives in the BizTalk Message Box database, a message agent identifies subscribers and sends the message to any endpoints that have subscriptions.</span></span> <span data-ttu-id="9478b-110">Abonnements peuvent être créés de différentes façons, notamment la liaison d’une orchestration à un port de réception ayant une réception corrélée en attente d’un message ou la création d’un port d’envoi d’une condition de filtre qui correspond à une propriété du message (par exemple, le type, la réception point, ou la valeur d’une propriété routable).</span><span class="sxs-lookup"><span data-stu-id="9478b-110">Subscriptions can be created in several ways, including binding an orchestration to a receive port, having a correlated receive waiting for a message, or creating a send port with a filter condition that matches a property of the message (such as the type, the receive point, or the value of a routable property).</span></span>  
  
 <span data-ttu-id="9478b-111">Grâce à cette approche efficace et évolutive, BizTalk Server permet aux développeurs de créer une série de sous-processus discrètes, définir les types de messages qui déclenchent leur appel et ne vous inquiétez pas sur la séquence.</span><span class="sxs-lookup"><span data-stu-id="9478b-111">By providing this efficient and scalable approach, BizTalk Server enables developers to create a series of discrete sub-processes, define the types of messages that trigger their invocation, and not worry about the sequence.</span></span> <span data-ttu-id="9478b-112">Un processus initié par l’arrivée d’un message effectue son traitement du message ; Lorsqu’il a traité le message, il peut fournir ou dans un autre message à la base de données MessageBox, qui, à son tour, peut-être y activer un ou plusieurs sous-processus.</span><span class="sxs-lookup"><span data-stu-id="9478b-112">A process initiated by the arrival of a message performs its processing on the message; after it processes the message, it can deliver this or another message to the Message Box database, which, in turn, may activate one or more sub-processes.</span></span>  
  
 <span data-ttu-id="9478b-113">Microsoft fournit les blocs de construction clés qui sont requis pour la création d’Infrastructures de Service-Oriented complète, y compris Windows Server, le .NET Framework et BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9478b-113">Microsoft provides key building blocks that are required for building comprehensive Service-Oriented Infrastructures, including Windows Server, the .NET Framework, and BizTalk Server.</span></span> <span data-ttu-id="9478b-114">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est basée sur BizTalk Server, car il fournit la base pour les services ESB courants, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9478b-114">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is based on BizTalk Server because it provides the basis for the most common ESB services, including the following:</span></span>  
  
-   <span data-ttu-id="9478b-115">Routage des messages</span><span class="sxs-lookup"><span data-stu-id="9478b-115">Message routing</span></span>  
  
-   <span data-ttu-id="9478b-116">Validation de message</span><span class="sxs-lookup"><span data-stu-id="9478b-116">Message validation</span></span>  
  
-   <span data-ttu-id="9478b-117">Transformation des messages</span><span class="sxs-lookup"><span data-stu-id="9478b-117">Message transformation</span></span>  
  
-   <span data-ttu-id="9478b-118">Structure d’adaptateur extensible pour la connectivité</span><span class="sxs-lookup"><span data-stu-id="9478b-118">Extensible adapter framework for connectivity</span></span>  
  
-   <span data-ttu-id="9478b-119">Orchestration des services</span><span class="sxs-lookup"><span data-stu-id="9478b-119">Service orchestration</span></span>  
  
-   <span data-ttu-id="9478b-120">Moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="9478b-120">Business rules engine</span></span>  
  
-   <span data-ttu-id="9478b-121">L’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="9478b-121">Business activity monitoring</span></span>  
  
-   <span data-ttu-id="9478b-122">Service Web et WS-* intégration (adaptateur WCF)</span><span class="sxs-lookup"><span data-stu-id="9478b-122">Web service and WS-* integration (WCF adapter)</span></span>  

## <a name="core-capabilities"></a><span data-ttu-id="9478b-123">Fonctionnalités principales</span><span class="sxs-lookup"><span data-stu-id="9478b-123">Core capabilities</span></span>  
 <span data-ttu-id="9478b-124">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour fournir une plage de nouvelles fonctionnalités de focus sur la création d’applications orientées service robustes, connectées.</span><span class="sxs-lookup"><span data-stu-id="9478b-124">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications.</span></span> <span data-ttu-id="9478b-125">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] traite des composants de BizTalk Server comme des unités de travail qui peuvent être connectés, comme vous le souhaitez, pour former faiblement couplés solutions.</span><span class="sxs-lookup"><span data-stu-id="9478b-125">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] treats BizTalk Server components as individual units of work that can be connected, as desired, to form loosely coupled solutions.</span></span> <span data-ttu-id="9478b-126">Voici certaines des fonctionnalités de base qui le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit pour améliorer les fonctionnalités de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="9478b-126">The following are some of the core capabilities that the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides to enhance the capabilities of BizTalk Server:</span></span>  
  
-   <span data-ttu-id="9478b-127">**Fonction de médiation des stratégies.**</span><span class="sxs-lookup"><span data-stu-id="9478b-127">**Policy driven mediation.**</span></span> <span data-ttu-id="9478b-128">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9478b-128">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
    -   <span data-ttu-id="9478b-129">Il fournit le routage basé sur un itinéraire qui prend en charge la composition légère de service au moment de la publication des messages.</span><span class="sxs-lookup"><span data-stu-id="9478b-129">It provides itinerary-based routing that supports lightweight service composition at the time of message publication.</span></span> <span data-ttu-id="9478b-130">Cette approche permet la découverte dynamique des points de terminaison de service et les exigences de médiation pour le routage des messages à l’aide d’un Registre de service ou de la stratégie de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="9478b-130">This approach allows dynamic discovery of service endpoints and mediation requirements for message routing using a service registry or the business rules policy.</span></span>  
  
    -   <span data-ttu-id="9478b-131">Il ajoute la prise en charge de centralisation de la stratégie du routage à l’aide d’itinéraires côté serveur qui sont résolus et ajoutés au contexte du message après un message dynamiquement en fonction des itinéraire est reçu.</span><span class="sxs-lookup"><span data-stu-id="9478b-131">It adds support for policy centralization for itinerary-based routing using server-side itineraries that are dynamically resolved and added to the message context after a message is received.</span></span> <span data-ttu-id="9478b-132">La gestion des itinéraires dans un emplacement central permet le traitement des messages à partir de clients qui ne connaissent pas complètement comment leurs demandes sont routés.</span><span class="sxs-lookup"><span data-stu-id="9478b-132">Managing itineraries in a central location enables the processing of messages from clients that are completely unaware of how their requests are being routed.</span></span>  
  
    -   <span data-ttu-id="9478b-133">Elle utilise une version améliorée de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et l’infrastructure du fournisseur de carte, ce qui permet une résolution dynamique des points de terminaison et les exigences de la transformation ; Cela dissocie efficacement le consommateur à partir des services.</span><span class="sxs-lookup"><span data-stu-id="9478b-133">It uses an enhanced version of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework, which enables dynamic resolution of endpoints and transformation requirements; this effectively decouples the consumer from the services.</span></span>  
  
-   <span data-ttu-id="9478b-134">**Connexion de systèmes.**</span><span class="sxs-lookup"><span data-stu-id="9478b-134">**Connecting systems.**</span></span> <span data-ttu-id="9478b-135">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9478b-135">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
    -   <span data-ttu-id="9478b-136">Il fournit des composants de pipeline normalisent les espaces de noms de message XML.</span><span class="sxs-lookup"><span data-stu-id="9478b-136">It provides pipeline components that normalize XML message namespaces.</span></span>  
  
    -   <span data-ttu-id="9478b-137">Il s’intègre avec JMS via l’adaptateur WebSphere MQ pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9478b-137">It integrates with JMS through the WebSphere MQ adapter for BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="9478b-138">Il facilite les modèles d’échange de message qui permettent une agrégation dynamique, le routage des messages, validation de message et transformation des messages.</span><span class="sxs-lookup"><span data-stu-id="9478b-138">It facilitates message exchange patterns that enable dynamic service aggregation, message routing, message validation, and message transformation.</span></span>  
  
    -   <span data-ttu-id="9478b-139">Il prend en charge la découverte de point de terminaison de service à partir du Registre et intégration du référentiel à l’aide de UDDI 3.0.</span><span class="sxs-lookup"><span data-stu-id="9478b-139">It supports service endpoint discovery from registry and repository integration using UDDI 3.0.</span></span>  
  
    -   <span data-ttu-id="9478b-140">Il prend en charge le routage des messages via des cartes de métier (LOB) à l’aide de l’adaptateur BizTalk WCF-Custom pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9478b-140">It supports message routing through line-of-business (LOB) adapters by using the WCF-Custom BizTalk Adapter for BizTalk Server.</span></span>  
  
-   <span data-ttu-id="9478b-141">**Gestion et surveillance.**</span><span class="sxs-lookup"><span data-stu-id="9478b-141">**Management and monitoring.**</span></span> <span data-ttu-id="9478b-142">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9478b-142">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
    -   <span data-ttu-id="9478b-143">Il fournit des outils et infrastructure de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="9478b-143">It provides exception management framework and tools.</span></span>  
  
    -   <span data-ttu-id="9478b-144">Il facilite le message repair et renvoyés à l’aide d’un portail de gestion fournis comme exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="9478b-144">It facilitates message repair and resubmission using a management portal, shipped as a sample application.</span></span> <span data-ttu-id="9478b-145">Cette application Web prend également en charge les notifications par courrier électronique personnalisable lorsqu’une erreur spécifique se produit.</span><span class="sxs-lookup"><span data-stu-id="9478b-145">This Web application also supports customizable e-mail notifications when a specific error occurs.</span></span>  
  
    -   <span data-ttu-id="9478b-146">Elle permet l’intégration de point de terminaison et le Registre de BizTalk Server, la gestion et la publication.</span><span class="sxs-lookup"><span data-stu-id="9478b-146">It allows BizTalk Server endpoint and registry integration, management, and publication.</span></span>  
  
    -   <span data-ttu-id="9478b-147">Il fournit un référentiel centralisé des itinéraires de côté serveur avec version.</span><span class="sxs-lookup"><span data-stu-id="9478b-147">It provides a centralized repository of versioned server-side itineraries.</span></span>  
  
    -   <span data-ttu-id="9478b-148">Il prend en charge analytique et création de rapports pour les applications BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9478b-148">It supports reporting and analytics for BizTalk Server applications.</span></span>  
  
    -   <span data-ttu-id="9478b-149">Il inclut des composants de l’analyse BAM pour effectuer le suivi de l’exécution de la feuille de route de service, y compris l’heure de début, heure de fin et de séquences de médiation de service.</span><span class="sxs-lookup"><span data-stu-id="9478b-149">It includes Business Activity Monitoring components to track itinerary service execution, including start time, end time, and service mediation sequence.</span></span>  
  
-   <span data-ttu-id="9478b-150">**Gouvernance SOA.**</span><span class="sxs-lookup"><span data-stu-id="9478b-150">**SOA governance.**</span></span> <span data-ttu-id="9478b-151">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9478b-151">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
    -   <span data-ttu-id="9478b-152">Il s’intègre avec les solutions de gouvernance SOA tierces, y compris les agents de gestion intégrée pour BizTalk Server à partir de AmberPoint et SOA logiciel.</span><span class="sxs-lookup"><span data-stu-id="9478b-152">It integrates with third-party SOA governance solutions, including embedded management agents for BizTalk Server from AmberPoint and SOA Software.</span></span>  

> [!TIP]
> <span data-ttu-id="9478b-153">[Présentation de BizTalk Server](../core/understanding-biztalk-server.md) fournit plus de détails sur le moteur de messagerie et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="9478b-153">[Understanding BizTalk Server](../core/understanding-biztalk-server.md) provides more details on the messaging engine, and more.</span></span>

## <a name="get-some-help"></a><span data-ttu-id="9478b-154">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="9478b-154">Get some help</span></span>
<span data-ttu-id="9478b-155">Obtenir de l’aide et aider les autres à le [BizTalk ESB Toolkit forums](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="9478b-155">Get some help, and help others at the [BizTalk ESB Toolkit forums](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9478b-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9478b-156">Next steps</span></span>
[<span data-ttu-id="9478b-157">Contenu de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="9478b-157">Contents of the BizTalk ESB Toolkit</span></span>](contents-of-the-biztalk-esb-toolkit.md)  

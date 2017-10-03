---
title: Microsoft BizTalk ESB Toolkit | Documents Microsoft
description: "Introduction, les scénarios courants et les composants de la boîte à outils ESB dans BizTalk Server"
caps.latest.revision: "14"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17ffaebc-7e33-4de8-8e94-109cd5d16ca0
ms.author: mandia
ms.openlocfilehash: 1763ed4bb7f090b91565c3a5f5f480d2c081b48c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-biztalk-esb-toolkit"></a><span data-ttu-id="d6715-103">Microsoft BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-103">Microsoft BizTalk ESB Toolkit</span></span>
<span data-ttu-id="d6715-104">![Logo BizTalk ESB Toolkit](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")</span><span class="sxs-lookup"><span data-stu-id="d6715-104">![BizTalk ESB Toolkit Logo](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="d6715-105">Résumé</span><span class="sxs-lookup"><span data-stu-id="d6715-105">Summary</span></span>  
 <span data-ttu-id="d6715-106">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] pour prendre en charge une architecture de messagerie faiblement couplée.</span><span class="sxs-lookup"><span data-stu-id="d6715-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to support a loosely coupled messaging architecture.</span></span> <span data-ttu-id="d6715-107">BizTalk Server inclut un mécanisme de publication/d'abonnement puissant pour les applications de messagerie qui crée et définit des abonnements, et offre une plateforme hautement efficace et évolutive pour les applications à l'architecture orientée services.</span><span class="sxs-lookup"><span data-stu-id="d6715-107">BizTalk Server includes a powerful publish/subscribe mechanism for messaging applications that works by creating and filling subscriptions, which provides a highly efficient and scalable platform for service-oriented architecture (SOA) applications.</span></span>  
  
 <span data-ttu-id="d6715-108">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour fournir une plage de nouvelles fonctionnalités de focus sur la création d’applications robustes, connectées, orientées service qui incorporent d’appel de service basé sur la feuille de route pour le service léger composition, résolution dynamique des points de terminaison et des cartes, le service Web et WS-* intégration, la gestion des erreurs et création de rapports et l’intégration avec les solutions de gouvernance SOA tierces.</span><span class="sxs-lookup"><span data-stu-id="d6715-108">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications that incorporate itinerary-based service invocation for lightweight service composition, dynamic resolution of endpoints and maps, Web service and WS-* integration, fault management and reporting, and integration with third-party SOA governance solutions.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d6715-109">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="d6715-109">Overview</span></span>  
 <span data-ttu-id="d6715-110">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit une collection de composants de BizTalk Server et .NET Framework pour simplifier le développement un Bus de Service d’entreprise (ESB) sur la plateforme Microsoft et pour permettre aux clients de Microsoft étendre, les modèles et les guides d’architecture leurs propres solutions de messagerie et l’intégration.</span><span class="sxs-lookup"><span data-stu-id="d6715-110">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides architectural guidance, patterns, and a collection of BizTalk Server and .NET Framework components to simplify the development of an Enterprise Service Bus (ESB) on the Microsoft platform and to allow Microsoft customers to extend their own messaging and integration solutions.</span></span>  
  
## <a name="common-scenarios"></a><span data-ttu-id="d6715-111">Scénarios courants</span><span class="sxs-lookup"><span data-stu-id="d6715-111">Common Scenarios</span></span>  
 <span data-ttu-id="d6715-112">Le terme ESB (Enterprise Service Bus) est largement utilisé dans le cadre de l'implémentation d'une infrastructure pour mettre en place une architecture orientée services (SOA, Service-Oriented Architecture).</span><span class="sxs-lookup"><span data-stu-id="d6715-112">The term Enterprise Service Bus (ESB) is widely used in the context of implementing an infrastructure for enabling a service-oriented architecture (SOA).</span></span> <span data-ttu-id="d6715-113">L'expérience réelle de déploiement des SOA a toutefois montré qu'une architecture ESB n'est qu'un des blocs de construction permettant de former une infrastructure orientée services (SOI, Service-Oriented Infrastructure) complète.</span><span class="sxs-lookup"><span data-stu-id="d6715-113">However, real-world experience with the deployment of SOAs has shown that an ESB is only one of many building blocks that make up a comprehensive Service-Oriented Infrastructure (SOI).</span></span> <span data-ttu-id="d6715-114">Le terme ESB a évolué dans différentes directions. Sa définition dépend de l'interprétation des fournisseurs de plateforme ESB et d'intégration individuels d'une part, et des conditions associées aux initiatives SOA spécifiques d'autre part.</span><span class="sxs-lookup"><span data-stu-id="d6715-114">The term ESB has morphed in a number of different directions, and its definition depends on the interpretation of individual ESB and integration platform vendors and on the requirements of particular SOA initiatives.</span></span>  
  
 <span data-ttu-id="d6715-115">Selon l'expérience accumulée par Microsoft lors d'implémentations SOI réelles, une architecture ESB peut être comparée à un ensemble de modèles d'architecture basé sur l'intégration traditionnelle des applications de l'entreprise, des applications intermédiaires orientées messagerie, des services Web, l'interopérabilité .NET et Java, l'intégration des systèmes hôtes, l'interopérabilité avec les registres de services et les référentiels de ressources.</span><span class="sxs-lookup"><span data-stu-id="d6715-115">Based on the experience Microsoft has gathered from many successful real-world SOI implementations, you can think of an ESB as a collection of architectural patterns based on traditional enterprise application integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.</span></span>  
  
 <span data-ttu-id="d6715-116">Figure 1 montre une vue d’ensemble du type d’interconnexion une architecture ESB peut fournir.</span><span class="sxs-lookup"><span data-stu-id="d6715-116">Figure 1 shows a high-level view of the type of interconnectivity that an ESB architecture can provide.</span></span>  
  
 <span data-ttu-id="d6715-117">![Vue d’ensemble d’ESB](../esb-toolkit/media/esboverview.gif "ESBOverview")</span><span class="sxs-lookup"><span data-stu-id="d6715-117">![ESB Overview](../esb-toolkit/media/esboverview.gif "ESBOverview")</span></span>  
  
 <span data-ttu-id="d6715-118">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="d6715-118">**Figure 1**</span></span>  
  
 <span data-ttu-id="d6715-119">**Un exemple de haut niveau de la connectivité fourni l’architecture Enterprise Service Bus**</span><span class="sxs-lookup"><span data-stu-id="d6715-119">**A high-level example of the connectivity provided the Enterprise Service Bus architecture**</span></span>  
  
## <a name="audience-requirements"></a><span data-ttu-id="d6715-120">Public</span><span class="sxs-lookup"><span data-stu-id="d6715-120">Audience Requirements</span></span>  
 <span data-ttu-id="d6715-121">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est destiné aux développeurs qui créent des solutions Microsoft BizTalk Server ou autres solutions qui utilisent la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants.</span><span class="sxs-lookup"><span data-stu-id="d6715-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is intended for developers who create Microsoft BizTalk Server solutions or other solutions that use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] components.</span></span> <span data-ttu-id="d6715-122">Pour tirer pleinement parti de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], les développeurs doivent posséder des connaissances et expérience d’utilisation avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d6715-122">To take full advantage of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], developers should possess knowledge and experience working with the following:</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

- [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]
  
-   <span data-ttu-id="d6715-123">techniques de développement Microsoft .NET, notamment le développement de services Web ASP.NET Web et de composants .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6715-123">Microsoft .NET development techniques, including the development of ASP.NET Web services and .NET Framework components</span></span>  
  
## <a name="design-goals"></a><span data-ttu-id="d6715-124">Objectifs de conception</span><span class="sxs-lookup"><span data-stu-id="d6715-124">Design Goals</span></span>  
 <span data-ttu-id="d6715-125">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] se compose d’une série de l’interaction des composants qui prennent en charge et implémentent un environnement de messagerie faiblement couplé qui facilite la génération d’applications d’entreprise basée sur le message.</span><span class="sxs-lookup"><span data-stu-id="d6715-125">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] consists of a series of interoperating components that support and implement a loosely coupled messaging environment that makes it easier to build message-based enterprise applications.</span></span> <span data-ttu-id="d6715-126">Les services et les composants se répartissent naturellement sept catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6715-126">The services and components fall naturally into the following seven categories:</span></span>  
  
-   <span data-ttu-id="d6715-127">**Services Web** : celles-ci exposent les services internes telles que feuille de route le traitement, gestion des exceptions, la résolution de points de terminaison et des cartes, des opérations de BizTalk Server et transformation des messages.</span><span class="sxs-lookup"><span data-stu-id="d6715-127">**Web services** : These expose internal services such as itinerary processing, exception management, resolution of endpoints and maps, BizTalk Server operations, and message transformation.</span></span>  
  
-   <span data-ttu-id="d6715-128">**Services d’itinéraire** : notamment les services basés sur la messagerie et d’orchestration pour effectuer le routage basé sur la feuille de route pour [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6715-128">**Itinerary services** : These include orchestration-based and messaging-based services for performing itinerary-based routing for [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6715-129">Vous pouvez créer des services personnalisés pour le routage basé sur l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="d6715-129">You can create custom services for itinerary-based routing.</span></span>  
  
-   <span data-ttu-id="d6715-130">**Itinéraire sur écarts.**</span><span class="sxs-lookup"><span data-stu-id="d6715-130">**Itinerary on-ramps.**</span></span> <span data-ttu-id="d6715-131">Ces recevoir des messages externes, attachement l’itinéraire approprié pour chaque message et traiter les données d’itinéraire ; ils utilisent la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d6715-131">These receive external messages, attach the appropriate itinerary for each message, and perform itinerary processing; they use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="d6715-132">**Sur les écarts** : ces recevoir des messages externes dans une gamme de formats et transports, tels que HTTP, JMS, WMQ, FTP, fichier plat et XML.</span><span class="sxs-lookup"><span data-stu-id="d6715-132">**On-ramps** : These receive external messages in a range of formats and transports, such as HTTP, JMS, WMQ, FTP, Flat File, and XML.</span></span> <span data-ttu-id="d6715-133">Ils sont par défaut de BizTalk Server emplacements de réception qui utilisent éventuellement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d6715-133">They are typical BizTalk Server receive locations that optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="d6715-134">**Écarter** : ces filtres implémentent les ports d’envoi pour la remise des messages à l’aide de formats et transports, tels que SOAP, WCF, JMS, WMQ, FTP, HTTP, fichier plat, XML ou tous les autres formats personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d6715-134">**Off-ramps** : These implement send ports for the delivery of messages using formats and transports such as SOAP, WCF, JMS, WMQ, FTP, HTTP, Flat File, XML, or any other custom formats.</span></span> <span data-ttu-id="d6715-135">Ils sont des ports d’envoi dynamiques BizTalk Server standards qui sont directement liés à la boîte de Message et qui utilisent éventuellement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d6715-135">They are typical BizTalk Server dynamic send ports that are direct-bound to the Message Box and that optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="d6715-136">**Infrastructure de gestion des exceptions** : Cela inclut l’exception du service Web, l’API de gestion des exceptions, et les composants d’enrichissement, traiter et transmettre les détails de l’exception au portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="d6715-136">**Exception Management Framework** : This includes the exception Web service, the exception management API, and components that enrich, process, and pass exception details to the ESB Management Portal.</span></span>  
  
-   <span data-ttu-id="d6715-137">**Portail de gestion ESB** : cela fournit la configuration du Registre médiation d’exception, notification d’alerte et analytique.</span><span class="sxs-lookup"><span data-stu-id="d6715-137">**ESB Management Portal** : This provides registry provisioning, exception mediation, alert notification, and analytics.</span></span>  
  
 <span data-ttu-id="d6715-138">La plupart de ces composants et services s’appuient sur les fonctionnalités implémentées par [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], tels que les moteurs d’Orchestration, de Transformation et de règles d’entreprise et de la base de données de la boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="d6715-138">Many of these components and services rely on features implemented by [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], such as the Orchestration, Transformation, and Business Rules engines and the Message Box database.</span></span> <span data-ttu-id="d6715-139">La figure 2 montre une vue schématique des catégories ; les composants et services qui se produisent généralement dans chaque catégorie ; et les composants centraux du système BizTalk Server utilisés par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6715-139">Figure 2 shows a schematic view of the categories; the components and services typically occurring within each category; and the core BizTalk Server system components used by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="d6715-140">![Architecture ESB](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")</span><span class="sxs-lookup"><span data-stu-id="d6715-140">![ESB Architecture](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")</span></span>  
  
 <span data-ttu-id="d6715-141">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="d6715-141">**Figure 2**</span></span>  
  
 <span data-ttu-id="d6715-142">**L’architecture et les composants de la[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="d6715-142">**The architecture and components of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**</span></span>  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a><span data-ttu-id="d6715-143">Fonctionnement de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-143">How the BizTalk ESB Toolkit Works</span></span>  
 <span data-ttu-id="d6715-144">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepte les messages entrants et agit sur eux, éventuellement (mais pas toujours) en effectuant des processus tels que la transformation, remise ou tout autre processus personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d6715-144">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepts inbound messages and operates on them, perhaps (but not always) by performing processes such as transformation, delivery, or any other custom defined process.</span></span> <span data-ttu-id="d6715-145">Pour spécifier les opérations requises, les instructions ou métadonnées associées qui définissent les processus à appliquer et les tâches à exécuter sur le contenu d'un message doivent être incluses dans le message.</span><span class="sxs-lookup"><span data-stu-id="d6715-145">To specify the operations required, the core processing components require a message to contain associated instructions or metadata that define the processes to apply and the tasks to execute with the message content.</span></span>  
  
 <span data-ttu-id="d6715-146">Cette approche fournit un couplage faible entre les services ; Cela signifie que l’architecture ESB ne nécessite pas la connaissance préalable du traitement spécifique pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="d6715-146">This approach provides loose coupling between services; this means that the ESB does not require prior knowledge of the specific processing for each message.</span></span> <span data-ttu-id="d6715-147">Elle doit simplement connaître les processus possibles et les modalités d'application de chaque processus.</span><span class="sxs-lookup"><span data-stu-id="d6715-147">It just has to know the possible range of processes and how to apply each process.</span></span> <span data-ttu-id="d6715-148">Les diverses options de spécification des processus disponibles et du mappage entre les processus, de même que les instructions au sein des messages, fournissent un mécanisme flexible pour configurer et ajuster le comportement, sans modification du code ni redéploiement des composants.</span><span class="sxs-lookup"><span data-stu-id="d6715-148">The wide range of options for specifying the available processes and the mapping between the processes and the instructions within messages provides a flexible mechanism for configuring and adjusting behavior, without requiring changes to code and redeployment of components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6715-149">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="d6715-149">In this section</span></span>

- [<span data-ttu-id="d6715-150">Installer et configurer Microsoft BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-150">Install and configure the Microsoft BizTalk ESB Toolkit</span></span>](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)

- [<span data-ttu-id="d6715-151">Présentation de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-151">Introduction to the BizTalk ESB Toolkit</span></span>](introduction-to-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="d6715-152">Prise en main et présentation de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-152">Getting started and understanding the BizTalk ESB Toolkit</span></span>](getting-started-with-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="d6715-153">Les tâches de développement et les scénarios clés</span><span class="sxs-lookup"><span data-stu-id="d6715-153">Key scenarios and development tasks</span></span>](key-scenarios-and-development-tasks.md)

- [<span data-ttu-id="d6715-154">Création d’itinéraires à l’aide du Concepteur d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="d6715-154">Creating itineraries using itinerary designer</span></span>](creating-itineraries-using-itinerary-designer.md)

- [<span data-ttu-id="d6715-155">Exemples d’applications BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-155">BizTalk ESB Toolkit sample applications</span></span>](biztalk-esb-toolkit-sample-applications.md)

- [<span data-ttu-id="d6715-156">Modification et l’extension de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-156">Modifying and extending the BizTalk ESB Toolkit</span></span>](modifying-and-extending-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="d6715-157">Administration de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-157">Administration with the BizTalk ESB Toolkit</span></span>](administration-with-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="d6715-158">Intégration de gouvernance SOA</span><span class="sxs-lookup"><span data-stu-id="d6715-158">SOA governance integration</span></span>](soa-governance-integration.md)

- [<span data-ttu-id="d6715-159">Résolution des problèmes de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="d6715-159">Troubleshooting the BizTalk ESB Toolkit</span></span>](troubleshooting-the-biztalk-esb-toolkit.md)
  
## <a name="related-topics"></a><span data-ttu-id="d6715-160">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d6715-160">Related topics</span></span>  
  
-   [<span data-ttu-id="d6715-161">Solutions orientée services BizTalk</span><span class="sxs-lookup"><span data-stu-id="d6715-161">BizTalk Service Oriented Solutions</span></span>](../core/service-oriented-solution.md)

- [<span data-ttu-id="d6715-162">À l’aide des Services Web avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6715-162">Using Web Services with BizTalk Server</span></span>](../core/using-web-services.md)  
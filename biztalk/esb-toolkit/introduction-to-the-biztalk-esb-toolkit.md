---
title: Présentation de BizTalk ESB Toolkit | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ESBToolkitV2.introduction
ms.assetid: 98a957b8-5855-4872-b7e7-58a2e1d6b2b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e44d3a100cdaefe04cf9d3aedfa8cf969811fc5e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a><span data-ttu-id="8d8ee-102">Présentation de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-102">Introduction to the BizTalk ESB Toolkit</span></span>
<span data-ttu-id="8d8ee-103">Décrit l’architecture et le contenu de Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d8ee-103">Explains the architecture and contents of the Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="8d8ee-104">La documentation montre également comment appliquer un modèle d’architecture de Bus de Service d’entreprise (ESB) pour développer des applications d’entreprise qui permettent de flexible et sécurisée, et les services réutilisables et organisation rapide des services existants dans la nouvelle de bout en bout processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d8ee-104">The documentation also demonstrates how to apply an Enterprise Service Bus (ESB) architecture pattern to develop enterprise applications that enable flexible, secure, and reusable services and rapid organization of existing services into new end-to-end business processes.</span></span>  
  
## <a name="what-is-an-enterprise-service-bus"></a><span data-ttu-id="8d8ee-105">Qu’est un Bus de Service d’entreprise ?</span><span class="sxs-lookup"><span data-stu-id="8d8ee-105">What Is an Enterprise Service Bus?</span></span>  
 <span data-ttu-id="8d8ee-106">Le terme Qu'enterprise Service Bus est largement utilisé dans le contexte de l’implémentation d’une infrastructure permettant d’Architecture orientée services (SOA).</span><span class="sxs-lookup"><span data-stu-id="8d8ee-106">The term Enterprise Service Bus is widely used in the context of implementing an infrastructure for enabling Service-Oriented Architecture (SOA).</span></span> <span data-ttu-id="8d8ee-107">Toutefois, l’expérience réelle avec le déploiement de solutions SOA a démontré qu’une architecture ESB n'est qu’un des nombreux composants requis pour générer une Infrastructure de Service-Oriented complète (SOI).</span><span class="sxs-lookup"><span data-stu-id="8d8ee-107">However, real-world experience with the deployment of SOA solutions has demonstrated that an ESB is only one of many components required to build a comprehensive Service-Oriented Infrastructure (SOI).</span></span> <span data-ttu-id="8d8ee-108">Le terme « ESB » a évolué dans différentes directions : varie en fonction de sa définition de l’interprétation des fournisseurs de plateforme ESB et d’intégration individuels et les spécifications de particuliers initiatives SOA.</span><span class="sxs-lookup"><span data-stu-id="8d8ee-108">The term "ESB" has evolved in a number of directions—its definition varies with the interpretation of individual ESB and integration platform vendors and with the requirements of particular SOA initiatives.</span></span>  
  
 <span data-ttu-id="8d8ee-109">En fonction de l’expérience de que Microsoft a collectées à partir de nombreuses implémentations de SOI réelles réussies, Microsoft considère un Bus de Service d’entreprise doit être une collection de modèles d’architecture basée sur traditionnel Enterprise Application IAE (intégration), logiciel intermédiaire orienté messages, les services Web, l’interopérabilité .NET et Java, intégration des systèmes hôtes et l’interopérabilité avec les référentiels de ressources et les registres de service.</span><span class="sxs-lookup"><span data-stu-id="8d8ee-109">Based on the experience Microsoft has gathered from many successful real-world SOI implementations, Microsoft considers an Enterprise Service Bus to be a collection of architectural patterns based on traditional Enterprise Application Integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.</span></span> <span data-ttu-id="8d8ee-110">La figure 1 illustre l’architecture d’un Bus de Service d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d8ee-110">Figure 1 illustrates the architecture of an Enterprise Service Bus.</span></span>  
  
 <span data-ttu-id="8d8ee-111">![Vue d’ensemble d’ESB](../esb-toolkit/media/esboverview.gif "ESBOverview")</span><span class="sxs-lookup"><span data-stu-id="8d8ee-111">![ESB Overview](../esb-toolkit/media/esboverview.gif "ESBOverview")</span></span>  
  
 <span data-ttu-id="8d8ee-112">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="8d8ee-112">**Figure 1**</span></span>  
  
 <span data-ttu-id="8d8ee-113">**Une représentation sous forme de haut niveau de la connectivité fournie par l’architecture Enterprise Service Bus**</span><span class="sxs-lookup"><span data-stu-id="8d8ee-113">**A high-level representation of the connectivity provided by the Enterprise Service Bus architecture**</span></span>  

<!---  Old text with old links
## The Industry View of ESB  
 There are many sources of information about ESB design, architecture, infrastructure, and implementation available from industry suppliers, system integrators, and independent sources.  
-->
<!---    
 IBM defines ESB as a system that "...enables a business to make use of a comprehensive, flexible, and consistent approach to integration while also reducing the complexity of the applications being integrated. Due to the complex and varying nature of business needs, ESB is an evolutional progression that unifies message oriented, event driven and service oriented approaches for integrating applications and service." IBM describes the advantages as "...greater reuse of IT assets by separating application logics and integration tasks, so you can reduce the number, size, and complexity of integration interfaces," and the ability to "...add or change services with minimal interruption to existing IT environment; reduce cost and risk involved as business changes and new opportunities arise." For more information, see [WebSphere software](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958))on the IBM Web site.  
-->
<!---    Old text with old links
 Sonic Solutions provide a comprehensive examination of ESB, discussing the principle aspects, and the IT and business benefits. They describe the requirement for ESB: "To integrate old and new, service-oriented architecture (SOA) needs an infrastructure that can connect any IT resource, whatever its technology or wherever it is deployed." For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) on the Sonic Solutions Web site.  
-->
<!---    Old text with old links
 TIBCO Software define ESB as "...a standards-based communication layer in a service- oriented architecture (SOA) that enables services to be used across multiple communication protocols [to] simplify service deployment and management, and promote service reuse in a heterogeneous environment." They suggest, in order to provide these capabilities, ESBs "...support both open standards and proprietary technologies, including Web services and UDDI-based registries to discover and publish services, Java Message Service (JMS) and other widely deployed messaging protocols, standards-based (XML) transformations, and basic message routing." For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) on the TIBCO Web site.  
-->
<!---    Old text with old links
 In the description of his book, Enterprise Service Bus, author David Chappell states that "Rather than conform to the hub-and-spoke architecture of traditional enterprise application integration products, ESB provides a highly distributed approach to integration." He adds "...with unique capabilities that allow individual departments or business units to build out their integration projects in incremental, digestible chunks, maintaining their own local control and autonomy, while still being able to connect together each integration project into a larger, more global integration fabric, or grid." For more information, see Enterprise Service Bus by David Chappell:  
-->
<!---    Old text with old links
-   Chappell, David. Enterprise Service Bus. Sebastopol, CA: O'Reilly Media, Inc. 2004.  
-->

  
## <a name="the-biztalk-esb-toolkit"></a><span data-ttu-id="8d8ee-114">BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-114">The BizTalk ESB Toolkit</span></span>
 <span data-ttu-id="8d8ee-115">Cette documentation, dans son ensemble, introduit des architectes et développeurs aux concepts d’architecture ESB que traité par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et décrit les fonctionnalités des composants ESB via un ensemble de cas d’usage ESB couramment acceptées.</span><span class="sxs-lookup"><span data-stu-id="8d8ee-115">This documentation, as a whole, introduces architects and developers to ESB architectural concepts as addressed by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and explains the functionality of the ESB components through a set of commonly accepted ESB use cases.</span></span>  
  
 <span data-ttu-id="8d8ee-116">Cette section fournit une introduction à la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et comprend les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d8ee-116">This section provides an introduction to the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and includes the following topics:</span></span>  
  
-   [<span data-ttu-id="8d8ee-117">Vue d’ensemble de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-117">Overview of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="8d8ee-118">Contenu de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-118">Contents of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  
  
 <span data-ttu-id="8d8ee-119">Cette documentation comprend également les sections suivantes de la rubrique :</span><span class="sxs-lookup"><span data-stu-id="8d8ee-119">This documentation also includes the following topic sections:</span></span>  
  
-   [<span data-ttu-id="8d8ee-120">Bien démarrer avec BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-120">Getting Started with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="8d8ee-121">Scénarios clés et tâches de développement</span><span class="sxs-lookup"><span data-stu-id="8d8ee-121">Key Scenarios and Development Tasks</span></span>](../esb-toolkit/key-scenarios-and-development-tasks.md)  
  
-   [<span data-ttu-id="8d8ee-122">Création d’itinéraires à l’aide du concepteur d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="8d8ee-122">Creating Itineraries Using Itinerary Designer</span></span>](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  
  
-   [<span data-ttu-id="8d8ee-123">Exemples d’applications BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-123">BizTalk ESB Toolkit Sample Applications</span></span>](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  
  
-   [<span data-ttu-id="8d8ee-124">Modification et l’extension de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-124">Modifying and Extending the BizTalk ESB Toolkit</span></span>](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="8d8ee-125">Administration avec BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="8d8ee-125">Administration with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="8d8ee-126">Intégration de la gouvernance SOA</span><span class="sxs-lookup"><span data-stu-id="8d8ee-126">SOA Governance Integration</span></span>](../esb-toolkit/soa-governance-integration.md)  
  
-   [<span data-ttu-id="8d8ee-127">Dépannage</span><span class="sxs-lookup"><span data-stu-id="8d8ee-127">Troubleshooting</span></span>](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)
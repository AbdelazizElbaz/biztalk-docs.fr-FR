---
title: "Présentation de BizTalk ESB Toolkit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ESBToolkitV2.introduction
ms.assetid: 98a957b8-5855-4872-b7e7-58a2e1d6b2b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e44d3a100cdaefe04cf9d3aedfa8cf969811fc5e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a>Présentation de BizTalk ESB Toolkit
Décrit l’architecture et le contenu de Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. La documentation montre également comment appliquer un modèle d’architecture de Bus de Service d’entreprise (ESB) pour développer des applications d’entreprise qui permettent de flexible et sécurisée, et les services réutilisables et organisation rapide des services existants dans la nouvelle de bout en bout processus d’entreprise.  
  
## <a name="what-is-an-enterprise-service-bus"></a>Qu’est un Bus de Service d’entreprise ?  
 Le terme Qu'enterprise Service Bus est largement utilisé dans le contexte de l’implémentation d’une infrastructure permettant d’Architecture orientée services (SOA). Toutefois, l’expérience réelle avec le déploiement de solutions SOA a démontré qu’une architecture ESB n'est qu’un des nombreux composants requis pour générer une Infrastructure de Service-Oriented complète (SOI). Le terme « ESB » a évolué dans différentes directions : varie en fonction de sa définition de l’interprétation des fournisseurs de plateforme ESB et d’intégration individuels et les spécifications de particuliers initiatives SOA.  
  
 En fonction de l’expérience de que Microsoft a collectées à partir de nombreuses implémentations de SOI réelles réussies, Microsoft considère un Bus de Service d’entreprise doit être une collection de modèles d’architecture basée sur traditionnel Enterprise Application IAE (intégration), logiciel intermédiaire orienté messages, les services Web, l’interopérabilité .NET et Java, intégration des systèmes hôtes et l’interopérabilité avec les référentiels de ressources et les registres de service. La figure 1 illustre l’architecture d’un Bus de Service d’entreprise.  
  
 ![Vue d’ensemble d’ESB](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **Figure 1**  
  
 **Une représentation sous forme de haut niveau de la connectivité fournie par l’architecture Enterprise Service Bus**  

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

  
## <a name="the-biztalk-esb-toolkit"></a>BizTalk ESB Toolkit
 Cette documentation, dans son ensemble, introduit des architectes et développeurs aux concepts d’architecture ESB que traité par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et décrit les fonctionnalités des composants ESB via un ensemble de cas d’usage ESB couramment acceptées.  
  
 Cette section fournit une introduction à la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et comprend les rubriques suivantes :  
  
-   [Vue d’ensemble de BizTalk ESB Toolkit](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  
  
-   [Contenu de BizTalk ESB Toolkit](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  
  
 Cette documentation comprend également les sections suivantes de la rubrique :  
  
-   [Bien démarrer avec BizTalk ESB Toolkit](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  
  
-   [Scénarios clés et tâches de développement](../esb-toolkit/key-scenarios-and-development-tasks.md)  
  
-   [Création d’itinéraires à l’aide du concepteur d’itinéraire](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  
  
-   [Exemples d’applications BizTalk ESB Toolkit](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  
  
-   [Modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  
  
-   [Administration avec BizTalk ESB Toolkit](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  
  
-   [Intégration de la gouvernance SOA](../esb-toolkit/soa-governance-integration.md)  
  
-   [Dépannage](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)
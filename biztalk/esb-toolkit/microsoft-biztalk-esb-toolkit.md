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
# <a name="microsoft-biztalk-esb-toolkit"></a>Microsoft BizTalk ESB Toolkit
![Logo BizTalk ESB Toolkit](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")  
  
## <a name="summary"></a>Résumé  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] pour prendre en charge une architecture de messagerie faiblement couplée. BizTalk Server inclut un mécanisme de publication/d'abonnement puissant pour les applications de messagerie qui crée et définit des abonnements, et offre une plateforme hautement efficace et évolutive pour les applications à l'architecture orientée services.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour fournir une plage de nouvelles fonctionnalités de focus sur la création d’applications robustes, connectées, orientées service qui incorporent d’appel de service basé sur la feuille de route pour le service léger composition, résolution dynamique des points de terminaison et des cartes, le service Web et WS-* intégration, la gestion des erreurs et création de rapports et l’intégration avec les solutions de gouvernance SOA tierces.  
  
## <a name="overview"></a>Vue d'ensemble  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit une collection de composants de BizTalk Server et .NET Framework pour simplifier le développement un Bus de Service d’entreprise (ESB) sur la plateforme Microsoft et pour permettre aux clients de Microsoft étendre, les modèles et les guides d’architecture leurs propres solutions de messagerie et l’intégration.  
  
## <a name="common-scenarios"></a>Scénarios courants  
 Le terme ESB (Enterprise Service Bus) est largement utilisé dans le cadre de l'implémentation d'une infrastructure pour mettre en place une architecture orientée services (SOA, Service-Oriented Architecture). L'expérience réelle de déploiement des SOA a toutefois montré qu'une architecture ESB n'est qu'un des blocs de construction permettant de former une infrastructure orientée services (SOI, Service-Oriented Infrastructure) complète. Le terme ESB a évolué dans différentes directions. Sa définition dépend de l'interprétation des fournisseurs de plateforme ESB et d'intégration individuels d'une part, et des conditions associées aux initiatives SOA spécifiques d'autre part.  
  
 Selon l'expérience accumulée par Microsoft lors d'implémentations SOI réelles, une architecture ESB peut être comparée à un ensemble de modèles d'architecture basé sur l'intégration traditionnelle des applications de l'entreprise, des applications intermédiaires orientées messagerie, des services Web, l'interopérabilité .NET et Java, l'intégration des systèmes hôtes, l'interopérabilité avec les registres de services et les référentiels de ressources.  
  
 Figure 1 montre une vue d’ensemble du type d’interconnexion une architecture ESB peut fournir.  
  
 ![Vue d’ensemble d’ESB](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **Figure 1**  
  
 **Un exemple de haut niveau de la connectivité fourni l’architecture Enterprise Service Bus**  
  
## <a name="audience-requirements"></a>Public  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est destiné aux développeurs qui créent des solutions Microsoft BizTalk Server ou autres solutions qui utilisent la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants. Pour tirer pleinement parti de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], les développeurs doivent posséder des connaissances et expérience d’utilisation avec les éléments suivants :  

- [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

- [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]
  
-   techniques de développement Microsoft .NET, notamment le développement de services Web ASP.NET Web et de composants .NET Framework.  
  
## <a name="design-goals"></a>Objectifs de conception  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] se compose d’une série de l’interaction des composants qui prennent en charge et implémentent un environnement de messagerie faiblement couplé qui facilite la génération d’applications d’entreprise basée sur le message. Les services et les composants se répartissent naturellement sept catégories suivantes :  
  
-   **Services Web** : celles-ci exposent les services internes telles que feuille de route le traitement, gestion des exceptions, la résolution de points de terminaison et des cartes, des opérations de BizTalk Server et transformation des messages.  
  
-   **Services d’itinéraire** : notamment les services basés sur la messagerie et d’orchestration pour effectuer le routage basé sur la feuille de route pour [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez créer des services personnalisés pour le routage basé sur l’itinéraire.  
  
-   **Itinéraire sur écarts.** Ces recevoir des messages externes, attachement l’itinéraire approprié pour chaque message et traiter les données d’itinéraire ; ils utilisent la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.  
  
-   **Sur les écarts** : ces recevoir des messages externes dans une gamme de formats et transports, tels que HTTP, JMS, WMQ, FTP, fichier plat et XML. Ils sont par défaut de BizTalk Server emplacements de réception qui utilisent éventuellement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.  
  
-   **Écarter** : ces filtres implémentent les ports d’envoi pour la remise des messages à l’aide de formats et transports, tels que SOAP, WCF, JMS, WMQ, FTP, HTTP, fichier plat, XML ou tous les autres formats personnalisés. Ils sont des ports d’envoi dynamiques BizTalk Server standards qui sont directement liés à la boîte de Message et qui utilisent éventuellement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et les métadonnées.  
  
-   **Infrastructure de gestion des exceptions** : Cela inclut l’exception du service Web, l’API de gestion des exceptions, et les composants d’enrichissement, traiter et transmettre les détails de l’exception au portail de gestion ESB.  
  
-   **Portail de gestion ESB** : cela fournit la configuration du Registre médiation d’exception, notification d’alerte et analytique.  
  
 La plupart de ces composants et services s’appuient sur les fonctionnalités implémentées par [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], tels que les moteurs d’Orchestration, de Transformation et de règles d’entreprise et de la base de données de la boîte de Message. La figure 2 montre une vue schématique des catégories ; les composants et services qui se produisent généralement dans chaque catégorie ; et les composants centraux du système BizTalk Server utilisés par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 ![Architecture ESB](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
 **Figure 2**  
  
 **L’architecture et les composants de la[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>Fonctionnement de BizTalk ESB Toolkit  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepte les messages entrants et agit sur eux, éventuellement (mais pas toujours) en effectuant des processus tels que la transformation, remise ou tout autre processus personnalisé. Pour spécifier les opérations requises, les instructions ou métadonnées associées qui définissent les processus à appliquer et les tâches à exécuter sur le contenu d'un message doivent être incluses dans le message.  
  
 Cette approche fournit un couplage faible entre les services ; Cela signifie que l’architecture ESB ne nécessite pas la connaissance préalable du traitement spécifique pour chaque message. Elle doit simplement connaître les processus possibles et les modalités d'application de chaque processus. Les diverses options de spécification des processus disponibles et du mappage entre les processus, de même que les instructions au sein des messages, fournissent un mécanisme flexible pour configurer et ajuster le comportement, sans modification du code ni redéploiement des composants.  
  
## <a name="in-this-section"></a>Contenu de cette section

- [Installer et configurer Microsoft BizTalk ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)

- [Présentation de BizTalk ESB Toolkit](introduction-to-the-biztalk-esb-toolkit.md)

- [Prise en main et présentation de BizTalk ESB Toolkit](getting-started-with-the-biztalk-esb-toolkit.md)

- [Les tâches de développement et les scénarios clés](key-scenarios-and-development-tasks.md)

- [Création d’itinéraires à l’aide du Concepteur d’itinéraire](creating-itineraries-using-itinerary-designer.md)

- [Exemples d’applications BizTalk ESB Toolkit](biztalk-esb-toolkit-sample-applications.md)

- [Modification et l’extension de BizTalk ESB Toolkit](modifying-and-extending-the-biztalk-esb-toolkit.md)

- [Administration de BizTalk ESB Toolkit](administration-with-the-biztalk-esb-toolkit.md)

- [Intégration de gouvernance SOA](soa-governance-integration.md)

- [Résolution des problèmes de BizTalk ESB Toolkit](troubleshooting-the-biztalk-esb-toolkit.md)
  
## <a name="related-topics"></a>Rubriques connexes  
  
-   [Solutions orientée services BizTalk](../core/service-oriented-solution.md)

- [À l’aide des Services Web avec BizTalk Server](../core/using-web-services.md)  
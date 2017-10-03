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
ms.openlocfilehash: 9763e55c44fc3ea45ab93127ffae8c9c742f0dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a>Présentation de BizTalk ESB Toolkit
Décrit l’architecture et le contenu de Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. La documentation montre également comment appliquer un modèle d’architecture de Bus de Service d’entreprise (ESB) pour développer des applications d’entreprise qui permettent de flexible et sécurisée, et les services réutilisables et organisation rapide des services existants dans la nouvelle de bout en bout processus d’entreprise.  
  
## <a name="what-is-an-enterprise-service-bus"></a>Qu’est un Bus de Service d’entreprise ?  
 Le terme Qu'enterprise Service Bus est largement utilisé dans le contexte de l’implémentation d’une infrastructure permettant d’Architecture orientée services (SOA). Toutefois, l’expérience réelle avec le déploiement de solutions SOA a démontré qu’une architecture ESB n'est qu’un des nombreux composants requis pour générer une Infrastructure de Service-Oriented complète (SOI). Le terme « ESB » a évolué dans différentes directions : varie en fonction de sa définition de l’interprétation des fournisseurs de plateforme ESB et d’intégration individuels et les spécifications de particuliers initiatives SOA.  
  
 En fonction de l’expérience de que Microsoft a collectées à partir de nombreuses implémentations de SOI réelles réussies, Microsoft considère un Bus de Service d’entreprise doit être une collection de modèles d’architecture basée sur traditionnel Enterprise Application IAE (intégration), logiciel intermédiaire orienté messages, les services Web, l’interopérabilité .NET et Java, intégration des systèmes hôtes et l’interopérabilité avec les référentiels de ressources et les registres de service. La figure 1 illustre l’architecture d’un Bus de Service d’entreprise.  
  
 ![Vue d’ensemble d’ESB](../esb-toolkit/media/esboverview.gif "ESBOverview")  
  
 **Figure 1**  
  
 **Une représentation sous forme de haut niveau de la connectivité fournie par l’architecture Enterprise Service Bus**  

\<!---Ancien texte avec des liens ancien
## <a name="the-industry-view-of-esb"></a>La vue de l’industrie de ESB  
 Il existe de nombreuses sources d’informations sur la conception ESB, architecture, infrastructure et d’implémentation disponibles auprès de fournisseurs de l’industrie, les intégrateurs système et sources indépendantes.  
-->
\<!---    
 IBM définit ESB en tant que système qui «.. .vous une entreprise pour rendre l’utilisation d’une gamme complète, flexible et une approche cohérente tout en réduisant la complexité des applications en cours d’intégration de l’intégration. En raison de la nature complexe et différents besoins professionnels, ESB est une évolution evolutional qui unifie orienté messages, pilotés par des événements et le service orienté approches permettant l’intégration des applications et le service. » IBM décrit les avantages en tant que «.. réutilisation .supérieures des ressources informatiques en séparant la logique d’application et les tâches d’intégration, afin de réduire le nombre, la taille et la complexité des interfaces d’intégration, « et la capacité de ».. .add ou modifier les services avec un minimum interruption de l’environnement informatique ; réduire le coût et des risques en tant que les modifications de l’entreprise et se présentent de nouvelles opportunités ». Pour plus d’informations, consultez [WebSphere logiciel](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958)) sur le site Web d’IBM.  
-->
\<!---Ancien texte avec des liens ancien Sonic proposent un examen minutieux de ESB, traitant les aspects de principe et de l’informatique et les avantages de l’entreprise. Ils décrivent la configuration requise pour ESB : « Pour intégrer les anciennes et nouvelles, architecture orientée services (SOA) a besoin une infrastructure qui peut se connecter à n’importe quelle ressource informatique, quelle que soit sa technologie ou partout où il est déployé. » Pour plus d’informations, consultez [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) sur le site Web de Sonic Solutions.  
-->
\<!---Ancien texte avec des liens ancien TIBCO logiciel définir ESB en tant que «.. couche de communication basée sur des normes .a dans une architecture ciblée sur les services (SOA) qui permet aux services d’être utilisé sur plusieurs protocoles de communication [to] pour simplifier le déploiement de service et gestion et favorise la réutilisation de service dans un environnement hétérogène. » Ils indiquent, afin de fournir ces fonctionnalités, ESB «.. .support ouverts tous les deux normes et des technologies propriétaires, y compris les services Web et les registres de base UDDI pour découvrir et publier des services, Java Message Service (JMS) et autres largement déployé protocoles de messagerie, basée sur des normes (XML) des transformations et routage des messages de base. » Pour plus d’informations, consultez [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) sur le site Web de TIBCO.  
-->
\<!---Ancien texte avec des liens ancien dans la description de son ouvrage, Enterprise Service Bus, auteur David Chappell indique que « plutôt qu’est conforme à l’architecture hub and spoke de produits d’intégration d’application entreprise traditionnel, ESB fournit une haute approche distribuée à l’intégration. » Il ajoute «.. with fonctionnalités uniques qui permettent à des départements ou des unités commerciales pour générer du délai d’attente leurs projets d’intégration en segments digestibles, incrémentiels, maintenir leur propre contrôle local et autonomie, tout en continuant à relier chaque projet d’intégration dans un plus grand, plus global l’infrastructure d’intégration ou grille. » Pour plus d’informations, consultez Enterprise Service Bus de David Chappell :  
-->
\<!---Ancien texte avec des liens ancien
-   Chappell, David. Bus de Service d’entreprise. Sebastopol, CA : O ' Reilly Media, Inc. 2004.  
-->

  
## <a name="the-biztalk-esb-toolkit"></a>BizTalk ESB Toolkit
 Cette documentation, dans son ensemble, introduit des architectes et développeurs aux concepts d’architecture ESB que traité par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et décrit les fonctionnalités des composants ESB via un ensemble de cas d’usage ESB couramment acceptées.  
  
 Cette section fournit une introduction à la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et comprend les rubriques suivantes :  
  
-   [Vue d’ensemble de BizTalk ESB Toolkit](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  
  
-   [Contenu de BizTalk ESB Toolkit](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  
  
 Cette documentation comprend également les sections suivantes de la rubrique :  
  
-   [Prise en main de BizTalk ESB Toolkit](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  
  
-   [Les tâches de développement et les scénarios clés](../esb-toolkit/key-scenarios-and-development-tasks.md)  
  
-   [Création d’itinéraires à l’aide du Concepteur d’itinéraire](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  
  
-   [BizTalk ESB Toolkit exemple Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  
  
-   [Modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  
  
-   [Administration de BizTalk ESB Toolkit](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  
  
-   [Intégration de gouvernance SOA](../esb-toolkit/soa-governance-integration.md)  
  
-   [Dépannage](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)
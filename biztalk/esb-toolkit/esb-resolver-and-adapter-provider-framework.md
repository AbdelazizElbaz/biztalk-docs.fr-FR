---
title: "Programme de résolution ESB et d’infrastructure d’adaptateurs fournisseur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c82c2247-1f0a-48bd-98c2-9c816f4d68d7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c23fa8aca6def654b594d8b4fccf5d584e12fed4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="esb-resolver-and-adapter-provider-framework"></a>Programme de résolution ESB et d’infrastructure d’adaptateurs fournisseur
Le programme de résolution et l’infrastructure d’adaptateurs fournisseur fournit une architecture enfichable complète pour la résolution dynamiquement les informations de point de terminaison et les types de mappage de BizTalk Server. Il utilise des composants extensibles, qui permettent aux développeurs de modifier le comportement pour leurs propres besoins et étendre le mécanisme pour prendre en charge la résolution de l’autre et les méthodes de routage.  
  
 Le programme de résolution et l’infrastructure d’adaptateurs fournisseur prend en charge Universal Description, Discovery et intégration UDDI (), du moteur de règles d’entreprise (BRE) et XML Path Language (XPath). Il expose également les interfaces de programmation (**IResolveProvider** et **IAdapterProvider**) pour permettre la création de composants de programme de résolution et de l’adaptateur personnalisés. Voici les trois principaux composants de l’infrastructure de fournisseur de carte et de programme de résolution :  
  
-   **Programmes de résolution.** Ils sont définis par un schéma, la chaîne de connexion et via l’implémentation de la **IResolveProvider** interface dans un assembly .NET Framework. Ceux-ci sont chargés et mis en cache au moment de l’exécution et prend en charge un éventail de résolution et les chaînes de connexion.  
  
-   **Fournisseurs de carte.** Elles sont définies via l’implémentation de la **IAdapterProvider** interface dans un assembly .NET Framework. Ils sont inscrits par leur type de transport de BizTalk Server, lequel définie les informations de point de terminaison fournies par un programme de résolution de l’adaptateur de BizTalk Server approprié.  
  
-   **Composants de pipeline d’itinéraire.** Ces instructions de résolution des chaînes de connexion ou des en-têtes SOAP d’itinéraire ESB d’analyser, et de point de terminaison résolution ou transformation des capacités d’exécution à l’aide de l’infrastructure de fournisseur de carte et de programme de résolution. Les composants pouvant dynamiquement définir les propriétés de point de terminaison de BizTalk Server ou exécuter une transformation de mappage BizTalk Server selon les instructions de résolution à partir de la chaîne de connexion ou d’en-têtes SOAP d’itinéraire ESB. Ces composants sont responsables de la gestion, la mise à jour et la persistance de l’itinéraire au-delà des limites de processus et de service. Le composant facultatif du désassembleur fournit l’analyse BizTalk Server natif du message et implémente la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fonctionnalité de routage vers plusieurs points de terminaison sans recourir à un service d’orchestration.  
  
 Pour plus d’informations sur la résolution dynamique et le routage dynamique, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md) et [à l’aide de la Transformation dynamique](../esb-toolkit/using-dynamic-transformation.md). Pour plus d’informations sur la résolution et le fournisseur d’infrastructure d’adaptateurs, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).
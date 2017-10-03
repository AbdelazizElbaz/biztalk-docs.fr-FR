---
title: "Développement de composants de Pipeline personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom]
- pipeline components [custom], about pipeline components
- pipeline components [custom], creating
- customizing, pipeline components
- pipeline interfaces
- IDisassemblerComponent
- pipeline interfaces, about pipeline interfaces
- creating, pipeline components [custom]
- IAssemblerComponent
- IComponent
- pipeline components [custom], customizing
- pipeline interfaces, interface types
- pipeline components [custom], interfaces
- pipeline components [custom], component types
ms.assetid: cce61e0d-f1e3-4ec2-b38c-7c6eaf83ac10
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723cd04a2a907fdb5d770975c27d47e1752d08ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-pipeline-components"></a>Développement de composants de Pipeline personnalisé
Cette section décrit comment développer un composant de pipeline. Vous pouvez créer trois types de composants de pipeline : général, le désassemblage et assemblage. Chacun de ces trois types peut aussi implémenter une fonctionnalité de sonde. Chaque type de composant de pipeline possède une interface associée qui doit être implémentée pour le composant à intégrer le moteur de messagerie BizTalk ; les interfaces de pipeline qui distinguent les types de composants sont **IComponent**, **IAssemblerComponent**, et **IDisassemblerComponent**. Pour les composants de sonde, vous devez implémenter la **IProbeMessage** interface.  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient un exemple de composant de pipeline que vous pouvez référencer lors de la création de votre propre composant. L'exemple de composant illustre comment ajouter des données à la fin et au début d'un message. Pour plus d’informations sur l’exemple de composant de pipeline, consultez [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md).  
  
> [!CAUTION]
>  Si vous référencez un composant de pipeline personnalisé à partir d'un pipeline dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], une erreur de compilation peut se produire. Pour corriger cette erreur, fermez le Concepteur de pipeline et rouvrez-le avant la compilation. Vous pouvez également supprimer le composant, puis l'ajouter.  
  
> [!IMPORTANT]
>  Lors de la mise à niveau vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], vérifiez que les variables de chaîne des composants de pipeline personnalisés existants ne contiennent pas de caractères de saut de ligne, comme ‘\n’. À défaut, une erreur « saut de ligne dans la constante » se produit lors de la compilation du composant dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À l’aide des Interfaces de Pipeline](../core/using-pipeline-interfaces.md)  
  
-   [Développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md)  
  
-   [Développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md)  
  
-   [Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [Développement d’un composant de Pipeline de sonde](../core/developing-a-probing-pipeline-component.md)  
  
-   [Implémentation d’une méthode Seek dans un composant de Pipeline managé de diffusion en continu](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [À l’aide de moteurs d’analyse et de sérialisation](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md)  
  
-   [Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md)  
  
-   [Débogage des Pipelines personnalisés](../core/debugging-custom-pipelines.md)
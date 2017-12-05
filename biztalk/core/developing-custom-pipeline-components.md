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
ms.openlocfilehash: 186c95c7ddf19c1d29b6ea76a63ccb5c92d6ba9d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="developing-custom-pipeline-components"></a>Développement de composants de Pipeline personnalisé
Cette section décrit comment développer un composant de pipeline. Vous pouvez créer trois types de composants de pipeline : général, le désassemblage et assemblage. Chacun de ces trois types peut aussi implémenter une fonctionnalité de sonde. Chaque type de composant de pipeline possède une interface associée qui doit être implémentée pour le composant à intégrer le moteur de messagerie BizTalk ; les interfaces de pipeline qui distinguent les types de composants sont **IComponent**, **IAssemblerComponent**, et **IDisassemblerComponent**. Pour les composants de sonde, vous devez implémenter la **IProbeMessage** interface.  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient un exemple de composant de pipeline que vous pouvez référencer lors de la création de votre propre composant. L'exemple de composant illustre comment ajouter des données à la fin et au début d'un message. Pour plus d’informations sur l’exemple de composant de pipeline, consultez [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md).  
  
> [!CAUTION]
>  Si vous référencez un composant de pipeline personnalisé à partir d'un pipeline dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], une erreur de compilation peut se produire. Pour corriger cette erreur, fermez le Concepteur de pipeline et rouvrez-le avant la compilation. Vous pouvez également supprimer le composant, puis l'ajouter.  
  
> [!IMPORTANT]
>  Lors de la mise à niveau vers BizTalk Server, vérifiez que les variables de chaîne dans des composants de pipeline personnalisés existants ne contiennent pas les caractères de saut de ligne, comme '\n'. À défaut, une erreur « saut de ligne dans la constante » se produit lors de la compilation du composant dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation des interfaces de pipeline](../core/using-pipeline-interfaces.md)  
  
-   [Développement d’un composant de pipeline général](../core/developing-a-general-pipeline-component.md)  
  
-   [Développement d’un composant de pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md)  
  
-   [Développement d’un composant de pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [Développement d’un composant de pipeline de sonde](../core/developing-a-probing-pipeline-component.md)  
  
-   [Implémentation d’une méthode Seek dans un composant de pipeline en continu géré](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [Utilisation des moteurs d’analyse et de sérialisation](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [Signalement d’erreurs par les composants de pipeline](../core/reporting-errors-from-pipeline-components.md)  
  
-   [Déploiement des composants de pipeline](../core/deploying-pipeline-components.md)  
  
-   [Débogage des pipelines personnalisés](../core/debugging-custom-pipelines.md)
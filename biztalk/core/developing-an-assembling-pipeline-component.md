---
title: "Développement d’assemblage d’un composant de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IComponentUI interface, assembling
- IBaseComponent interface, assembling
- pipeline interfaces, IBaseComponent
- pipeline components [custom], interfaces
- pipeline interfaces, IComponentUI
- IAssemblerComponent interface, assembling
- pipeline interfaces, IAssemblerComponent
- pipeline components [custom], assembling
ms.assetid: 2f85421d-2010-4a36-82b5-ea8016f8aa99
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de06a815e1c5a6bf71700ad373ae3f278b3a9a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-an-assembling-pipeline-component"></a>Développement d’un composant de Pipeline d’assemblage
Un composant de pipeline d’assemblage est un composant .NET ou COM qui reçoit plusieurs messages en entrée et produit un message en sortie. Les composants d’assemblage sont utilisés pour collecter des documents individuels dans le lot d'échange de messages.  
  
> [!NOTE]
>  La fonctionnalité d'assemblage n'est pas utilisée, par conséquent BizTalk Server transmet toujours un document à la sortie de composant.  
  
 Un composant d’assemblage doit implémenter les interfaces suivantes :  
  
-   `IBaseComponent`  
  
-   `IAssemblerComponent`
  
-   `IComponentUI`
  
-   **IPersistPropertyBag.** Pour cette interface, consultez la documentation .NET Framework SDK.  
  
> [!NOTE]
>  Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie. Ceci les empêche d'effectuer un autre traitement dans le pipeline.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md)   
 [Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)   
 [Développement d’un composant de Pipeline de sonde](../core/developing-a-probing-pipeline-component.md)   
 [Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md)   
 [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md)
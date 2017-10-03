---
title: "Développement d’un composant de Pipeline général | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63f5d8d1-30fb-4a1e-b4bd-2be07b618b20
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b85992eb0691b7f27ec1a52812d986429d9e31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-general-pipeline-component"></a>Développement d’un composant de Pipeline général

## <a name="interfaces"></a>Interfaces
Un composant de pipeline général est un composant .NET ou COM qui implémente les interfaces suivantes :  
  
-   Interface IBaseComponent (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   Interface IComponent (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   Interface IComponentUI (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [IPersistPropertyBag](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
 Un composant de pipeline général reçoit un message du moteur de messagerie BizTalk, le traite, puis le renvoie au moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les composants généraux peuvent également être configurés de sorte à ne pas renvoyer les messages au serveur. Ces composants sont appelés composants de consommation, car ils se contentent de recevoir les messages sans en renvoyer.  
  
> [!NOTE]
>  Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie. Ceci les empêche d'effectuer un autre traitement dans le pipeline.  
  
## <a name="more-pipeline-resources"></a>Plus de ressources de pipeline
 [Développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md)   
 [Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)   
 [Développement d’un composant de Pipeline de sonde](../core/developing-a-probing-pipeline-component.md)   
 [Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md)   
 [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md)
---
title: "Composant de Pipeline du développement d’un désassemblage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDisassemblerComponent interface, disassembling
- pipeline components [custom], IDisassemblerComponent
- pipeline components [custom], IBaseComponent
- IBaseComponent interface, disassembling
- pipeline components [custom], disassembling
ms.assetid: 77c0aa7d-4d1b-4a8f-bef8-d38e7e4045c6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc4e831561f9940ad7e8ee91479a2fada1fcd910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-disassembling-pipeline-component"></a>Développement d’un composant de Pipeline de désassemblage
Un composant de pipeline de désassemblage reçoit un message en entrée et produit zéro ou plusieurs messages en sortie. Les composants de désassemblage sont utilisés pour fractionner des échanges de messages en documents individuels. Les composants du désassembleur doivent implémenter les interfaces suivantes :  
  
-   `IBaseComponent`
  
-   `IDisassemblerComponent`
  
-   `IComponentUI`
  
-   **IPersistPropertyBag.** Pour cette interface, consultez la documentation .NET Framework SDK.  
  
 Vous pouvez créer votre propre désassemblage composant en étendant le **FFDasmComp** ou **XMLDasmComp** classe.  
  
> [!WARNING]
>  Si votre désassembleur personnalisé définit la propriété de contexte MessageDestination sur SuspendQueue, le flux renvoyé par le désassembleur doit prendre en charge Seek(0) pour que la suspension opère.  
  
> [!NOTE]
>  Les composants de pipeline personnalisés doivent copier les parties supplémentaires du message d'entrée vers le ou les messages de sortie. Ceci les empêche d'effectuer un autre traitement dans le pipeline.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [La gestion des flux de données entrantes dans les composants de Pipeline](../core/handling-incoming-data-streams-in-pipeline-components.md)  
  
-   [Gestion du codage dans un composant de Pipeline désassembleur](../core/handling-encoding-in-a-disassembler-pipeline-component.md)  
  
-   [Étendre le composant de Pipeline de désassembleur de fichier plat](../core/extending-the-flat-file-disassembler-pipeline-component.md)
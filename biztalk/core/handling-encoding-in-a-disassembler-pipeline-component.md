---
title: "Gestion du codage dans un composant de Pipeline désassembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], encoding
- pipeline components [custom], disassembling
ms.assetid: 33420357-421f-4ad0-8eee-d445376676db
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcbfb8f86847668436fae04db7bee1703dfb60ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a>Gestion du codage dans un composant de Pipeline désassembleur
Assurez-vous que votre composant Désassembleur personnalisé code les documents sortants dans l'un des formats suivants :  
  
-   UTF-8  
  
-   UTF-16  
  
-   UTF-32  
  
-   UTF-16LE  
  
-   UTF-16BE  
  
 Tout autre format de codage pourrait empêcher le moteur d'orchestration de traiter le document.  
  
 UTF-32LE et UTF-32BE ne sont pas pris en charge par .NET Framework. Pour utiliser ces formats, vous devez créer une implémentation personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)
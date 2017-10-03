---
title: "Traitement des échanges récupérables | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interchange processing [Messaging Engine], modes
- parties, party resolution
- Messaging Engine, examples
- messages, interchange modes
- interchange processing [Messaging Engine], examples
- Messaging Engine, Recoverable Interchange Processing property
- Messaging Engine, failures
- interchange processing [Messaging Engine], party resolution
- Messaging Engine, interchange processing
- disassembly stage, pipelines
- Recoverable Interchange Processing property
- Messaging Engine, interchange modes
- receive pipelines, disassembly stage
- interchange processing [Messaging Engine], failures
- interchange processing [Messaging Engine], restrictions
- System.Xml.XmlReader
- interchange modes [Messaging Engine]
ms.assetid: d9e366fe-b2a0-4f1a-b6b9-1264717e4731
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b341b3673cd7118d459197fecea1eca25efe4e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="recoverable-interchange-processing"></a>Traitement des échanges récupérables
Cette section traite des **le traitement des échanges récupérables** fonctionnalité qui permet à un échange d’être entièrement traité même si un ou plusieurs messages dans l’échange échouent sur les étapes/phases suivantes :  
  
-   Étape Désassembler d'un pipeline de réception  
  
-   Étape Validation XML d'un pipeline de réception  
  
-   Phase d'exécution du mappage d'un port de réception  
  
 Le traitement des échanges récupérables est motivé par le besoin de prendre en charge le traitement réussi d'un seul échange contenant plusieurs messages identifiables de sorte que les messages valides soient propagés via le parcours de messagerie et que les messages non valides soient suspendus. Avec le traitement des échanges standard, l'existence de tout message non valide dans un échange donné provoque la suspension totale de ce dernier même s'il contient un ou plusieurs messages valides.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Phase de désassemblage (traitement des échanges récupérables)](../core/disassembly-stage-recoverable-interchange-processing.md)  
  
-   [Étape de Validation XML (traitement des échanges récupérables)](../core/xml-validation-stage-recoverable-interchange-processing.md)  
  
-   [Phase de mappage (traitement des échanges récupérables)](../core/mapping-phase-recoverable-interchange-processing.md)
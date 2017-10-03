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
# <a name="recoverable-interchange-processing"></a><span data-ttu-id="9c2d0-102">Traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="9c2d0-102">Recoverable Interchange Processing</span></span>
<span data-ttu-id="9c2d0-103">Cette section traite des **le traitement des échanges récupérables** fonctionnalité qui permet à un échange d’être entièrement traité même si un ou plusieurs messages dans l’échange échouent sur les étapes/phases suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c2d0-103">This section discusses **recoverable interchange processing** feature, which allows an interchange to be processed completely even if one or more messages in the interchange fail at the following stages/phases:</span></span>  
  
-   <span data-ttu-id="9c2d0-104">Étape Désassembler d'un pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="9c2d0-104">Disassembly stage of a receive pipeline</span></span>  
  
-   <span data-ttu-id="9c2d0-105">Étape Validation XML d'un pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="9c2d0-105">XML validation stage of a receive pipeline</span></span>  
  
-   <span data-ttu-id="9c2d0-106">Phase d'exécution du mappage d'un port de réception</span><span class="sxs-lookup"><span data-stu-id="9c2d0-106">Map execution phase of a receive port</span></span>  
  
 <span data-ttu-id="9c2d0-107">Le traitement des échanges récupérables est motivé par le besoin de prendre en charge le traitement réussi d'un seul échange contenant plusieurs messages identifiables de sorte que les messages valides soient propagés via le parcours de messagerie et que les messages non valides soient suspendus.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-107">Recoverable interchange processing is motivated by the need to support successful processing of a single interchange that contains multiple identifiable messages so that valid messages are propagated through the messaging pathway and invalid messages are suspended.</span></span> <span data-ttu-id="9c2d0-108">Avec le traitement des échanges standard, l'existence de tout message non valide dans un échange donné provoque la suspension totale de ce dernier même s'il contient un ou plusieurs messages valides.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-108">With standard interchange processing, the existence of any invalid message in a given interchange causes the entire interchange to be suspended even if it contains one or more valid messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c2d0-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9c2d0-109">In This Section</span></span>  
  
-   [<span data-ttu-id="9c2d0-110">Phase de désassemblage (traitement des échanges récupérables)</span><span class="sxs-lookup"><span data-stu-id="9c2d0-110">Disassembly Stage (Recoverable Interchange Processing)</span></span>](../core/disassembly-stage-recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="9c2d0-111">Étape de Validation XML (traitement des échanges récupérables)</span><span class="sxs-lookup"><span data-stu-id="9c2d0-111">XML Validation Stage (Recoverable Interchange Processing)</span></span>](../core/xml-validation-stage-recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="9c2d0-112">Phase de mappage (traitement des échanges récupérables)</span><span class="sxs-lookup"><span data-stu-id="9c2d0-112">Mapping Phase (Recoverable Interchange Processing)</span></span>](../core/mapping-phase-recoverable-interchange-processing.md)
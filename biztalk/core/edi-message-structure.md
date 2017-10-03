---
title: Structure des messages EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c9a0447-447f-483c-825d-547c06ad691e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9395ed5e0b03bda48e19d6413f95ca2e74a3f1e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-structure"></a>Structure d'un message EDI
Les messages EDI sont constitués d'une enveloppe et d'un ensemble hiérarchique d'éléments structurels. L'enveloppe contient un ensemble d'en-têtes et de codes de fin, chaque ensemble décrivant et contenant un élément structurel. Les éléments structurels disponibles sont les suivants :  
  
```  
Interchange  
   Group  
      Transaction set/message  
         Segment  
            Data Element  
               Sub Element  
```  
  
 La structure hiérarchique d'un message EDI permet de traiter les documents informatisés/messages et groupes par lot. Même si un échange ne contient qu'un document informatisé/message et qu'un groupe, il est constitué des mêmes éléments structurels de base que s'il était traité par lot, sauf qu'il n'y a pas plusieurs éléments de document informatisé/message ou de groupe.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Les en-têtes EDI et les codes de fin](../core/edi-headers-and-trailers.md)  
  
-   [Élément structurel d’un échange EDI](../core/edi-interchange-structural-element.md)  
  
-   [Élément structurel d’un groupe EDI](../core/edi-group-structural-element.md)  
  
-   [Élément structurel d’un Message à l’ensemble de transactions EDI](../core/edi-transaction-set-message-structural-element.md)  
  
-   [Élément structurel d’un Segment EDI](../core/edi-segment-structural-element.md)  
  
-   [Élément structurel d’élément données EDI](../core/edi-data-element-structural-element.md)
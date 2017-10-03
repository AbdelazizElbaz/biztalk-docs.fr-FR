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
# <a name="edi-message-structure"></a><span data-ttu-id="1ad23-102">Structure d'un message EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-102">EDI Message Structure</span></span>
<span data-ttu-id="1ad23-103">Les messages EDI sont constitués d'une enveloppe et d'un ensemble hiérarchique d'éléments structurels.</span><span class="sxs-lookup"><span data-stu-id="1ad23-103">EDI messages consist of an envelope and a hierarchical series of structural elements.</span></span> <span data-ttu-id="1ad23-104">L'enveloppe contient un ensemble d'en-têtes et de codes de fin, chaque ensemble décrivant et contenant un élément structurel.</span><span class="sxs-lookup"><span data-stu-id="1ad23-104">The envelope contains a set of headers and trailers, each set of which describes and contains a structural element.</span></span> <span data-ttu-id="1ad23-105">Les éléments structurels disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1ad23-105">These structural elements are as follows:</span></span>  
  
```  
Interchange  
   Group  
      Transaction set/message  
         Segment  
            Data Element  
               Sub Element  
```  
  
 <span data-ttu-id="1ad23-106">La structure hiérarchique d'un message EDI permet de traiter les documents informatisés/messages et groupes par lot.</span><span class="sxs-lookup"><span data-stu-id="1ad23-106">The hierarchical structure of an EDI message enables transaction sets/messages and groups to be batched.</span></span> <span data-ttu-id="1ad23-107">Même si un échange ne contient qu'un document informatisé/message et qu'un groupe, il est constitué des mêmes éléments structurels de base que s'il était traité par lot, sauf qu'il n'y a pas plusieurs éléments de document informatisé/message ou de groupe.</span><span class="sxs-lookup"><span data-stu-id="1ad23-107">Even if an interchange contains only one transaction set/message and only one group, that interchange is structured with the same basic structural elements that it would have if it were batched, with the exception that there would not be multiple transaction set/message or group elements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ad23-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1ad23-108">In This Section</span></span>  
  
-   [<span data-ttu-id="1ad23-109">Les en-têtes EDI et les codes de fin</span><span class="sxs-lookup"><span data-stu-id="1ad23-109">EDI Headers and Trailers</span></span>](../core/edi-headers-and-trailers.md)  
  
-   [<span data-ttu-id="1ad23-110">Élément structurel d’un échange EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-110">EDI Interchange Structural Element</span></span>](../core/edi-interchange-structural-element.md)  
  
-   [<span data-ttu-id="1ad23-111">Élément structurel d’un groupe EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-111">EDI Group Structural Element</span></span>](../core/edi-group-structural-element.md)  
  
-   [<span data-ttu-id="1ad23-112">Élément structurel d’un Message à l’ensemble de transactions EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-112">EDI Transaction Set-Message Structural Element</span></span>](../core/edi-transaction-set-message-structural-element.md)  
  
-   [<span data-ttu-id="1ad23-113">Élément structurel d’un Segment EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-113">EDI Segment Structural Element</span></span>](../core/edi-segment-structural-element.md)  
  
-   [<span data-ttu-id="1ad23-114">Élément structurel d’élément données EDI</span><span class="sxs-lookup"><span data-stu-id="1ad23-114">EDI Data Element Structural Element</span></span>](../core/edi-data-element-structural-element.md)
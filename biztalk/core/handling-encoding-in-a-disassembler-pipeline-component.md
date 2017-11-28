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
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a><span data-ttu-id="0282f-102">Gestion du codage dans un composant de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="0282f-102">Handling Encoding in a Disassembler Pipeline Component</span></span>
<span data-ttu-id="0282f-103">Assurez-vous que votre composant Désassembleur personnalisé code les documents sortants dans l'un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="0282f-103">Ensure that your custom disassembler component encodes outbound documents in one of the following formats:</span></span>  
  
-   <span data-ttu-id="0282f-104">UTF-8</span><span class="sxs-lookup"><span data-stu-id="0282f-104">UTF-8</span></span>  
  
-   <span data-ttu-id="0282f-105">UTF-16</span><span class="sxs-lookup"><span data-stu-id="0282f-105">UTF-16</span></span>  
  
-   <span data-ttu-id="0282f-106">UTF-32</span><span class="sxs-lookup"><span data-stu-id="0282f-106">UTF-32</span></span>  
  
-   <span data-ttu-id="0282f-107">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="0282f-107">UTF-16LE</span></span>  
  
-   <span data-ttu-id="0282f-108">UTF-16BE</span><span class="sxs-lookup"><span data-stu-id="0282f-108">UTF-16BE</span></span>  
  
 <span data-ttu-id="0282f-109">Tout autre format de codage pourrait empêcher le moteur d'orchestration de traiter le document.</span><span class="sxs-lookup"><span data-stu-id="0282f-109">The orchestration engine may not be able to process documents with other encoding formats.</span></span>  
  
 <span data-ttu-id="0282f-110">UTF-32LE et UTF-32BE ne sont pas pris en charge par .NET Framework. Pour utiliser ces formats, vous devez créer une implémentation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0282f-110">UTF-32LE and UTF-32BE are not supported by the .NET Framework; to use these formats, you must create a custom encoding implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0282f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0282f-111">See Also</span></span>  
 [<span data-ttu-id="0282f-112">Développement d’un composant de Pipeline de désassemblage</span><span class="sxs-lookup"><span data-stu-id="0282f-112">Developing a Disassembling Pipeline Component</span></span>](../core/developing-a-disassembling-pipeline-component.md)
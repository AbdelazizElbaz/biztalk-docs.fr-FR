---
title: "Envoi dynamique de l’adaptateur d’envoi SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 105972fe-9dc0-480a-a4d1-2ec682fa7ad9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75d63df8f38346e4f77e2b7bfa8e3effc93f2fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-dynamic-send"></a><span data-ttu-id="550a4-102">Envoi dynamique de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="550a4-102">SWIFT Send Adapter Dynamic Send</span></span>
<span data-ttu-id="550a4-103">Le mode d’envoi dynamique de l’adaptateur envoi extrait les messages de la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="550a4-103">The send adapter dynamic send mode pulls messages from the queue.</span></span> <span data-ttu-id="550a4-104">L’URI d’envoi dynamique est :</span><span class="sxs-lookup"><span data-stu-id="550a4-104">The URI for dynamic send is:</span></span>  
  
```  
SWIFT://<queue name>/<Force Acquire>/<Session Mode>/<Order By>/<Recovery mode>  
```  
  
 <span data-ttu-id="550a4-105">Vous pouvez utiliser une orchestration ou un pipeline pour construire l’URI.</span><span class="sxs-lookup"><span data-stu-id="550a4-105">You can use an orchestration or a pipeline to construct the URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550a4-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="550a4-106">See Also</span></span>  
 <span data-ttu-id="550a4-107">[Architecture de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="550a4-107">[SWIFT Send Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span></span>  
 <span data-ttu-id="550a4-108">[Adaptateur d’envoi SWIFT URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="550a4-108">[SWIFT Send Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md) </span></span>  
 <span data-ttu-id="550a4-109">[Initialisation de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="550a4-109">[SWIFT Send Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md) </span></span>  
 <span data-ttu-id="550a4-110">[Mode synchrone de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md) </span><span class="sxs-lookup"><span data-stu-id="550a4-110">[SWIFT Send Adapter Synchronous Mode](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md) </span></span>  
 [<span data-ttu-id="550a4-111">Arrêt de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="550a4-111">SWIFT Send Adapter Termination</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)
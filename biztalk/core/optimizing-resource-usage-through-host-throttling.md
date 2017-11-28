---
title: "Optimisation de l’utilisation des ressources via la limitation des hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host throttling
- performance, host throttling
ms.assetid: 823b431d-707d-4201-9a6e-4a879e767b66
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa30cb66371ef519741658dec47e08f6f92e871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-resource-usage-through-host-throttling"></a><span data-ttu-id="8c35a-102">Optimisation de l'utilisation des ressources par l'intermédiaire de la limitation des hôtes</span><span class="sxs-lookup"><span data-stu-id="8c35a-102">Optimizing Resource Usage Through Host Throttling</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8c35a-103">utilise plusieurs technologies Microsoft, chacun d’eux peut consommer une partie significative de la mémoire, disque et les ressources processeur disponibles sur le serveur BizTalk server et le serveur SQL qui contient les bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8c35a-103"> makes use of several different Microsoft technologies, each of which can consume a significant portion of the memory, disk, and CPU resources available on the BizTalk server and the SQL server that contains the BizTalk Server databases.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8c35a-104">utilise un mécanisme de limitation pour aider à gérer l’utilisation des ressources disponibles pour limiter la contention d’utilisation de ressources.</span><span class="sxs-lookup"><span data-stu-id="8c35a-104"> employs a throttling mechanism to help manage the use of available resources to minimize resource use contention.</span></span> <span data-ttu-id="8c35a-105">Cette rubrique explique comment ce mécanisme est conçu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-105">This topic discusses the design of this mechanism.</span></span> <span data-ttu-id="8c35a-106">Pour plus d’informations sur la façon d’ajuster les valeurs de limitation, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="8c35a-106">For information on how to adjust the throttling values, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c35a-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8c35a-107">In This Section</span></span>  
  
-   [<span data-ttu-id="8c35a-108">Ce qui est la limitation des hôtes ?</span><span class="sxs-lookup"><span data-stu-id="8c35a-108">What Is Host Throttling?</span></span>](../core/what-is-host-throttling.md)  
  
-   [<span data-ttu-id="8c35a-109">Comment BizTalk Server implémente la limitation de l’hôte</span><span class="sxs-lookup"><span data-stu-id="8c35a-109">How BizTalk Server Implements Host Throttling</span></span>](../core/how-biztalk-server-implements-host-throttling.md)  
  
-   [<span data-ttu-id="8c35a-110">Limitation des compteurs de performances de l’hôte</span><span class="sxs-lookup"><span data-stu-id="8c35a-110">Host Throttling Performance Counters</span></span>](../core/host-throttling-performance-counters.md)  
  
-   [<span data-ttu-id="8c35a-111">Limitation des recommandations sur la conception</span><span class="sxs-lookup"><span data-stu-id="8c35a-111">Throttling Design Recommendations</span></span>](../core/throttling-design-recommendations.md)
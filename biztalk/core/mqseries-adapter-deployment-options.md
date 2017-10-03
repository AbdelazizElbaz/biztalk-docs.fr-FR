---
title: "Options de déploiement de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, deploying
- deploying, MQSeries adapters
ms.assetid: d9380aff-40ea-419b-88e2-1e2ec3f023cb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88fa674c38df8b31c1954234846fd3939ed8568
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-deployment-options"></a><span data-ttu-id="b36e6-102">Options de déploiement de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="b36e6-102">MQSeries Adapter Deployment Options</span></span>
<span data-ttu-id="b36e6-103">L'adaptateur MQSeries vous permet de configurer votre matériel avec une grande flexibilité.</span><span class="sxs-lookup"><span data-stu-id="b36e6-103">The MQSeries adapter gives you great flexibility in configuring your hardware.</span></span> <span data-ttu-id="b36e6-104">Il existe au moins 3 principaux modèles d'utilisation :</span><span class="sxs-lookup"><span data-stu-id="b36e6-104">There are at least three main patterns of use:</span></span>  
  
-   <span data-ttu-id="b36e6-105">BizTalk Server, l'adaptateur, et MQSeries Server pour Windows sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b36e6-105">BizTalk Server, the adapter, and MQSeries Server for Windows on the same computer.</span></span>  
  
-   <span data-ttu-id="b36e6-106">BizTalk Server et l'adaptateur sur un premier ordinateur, et un serveur MQSeries pour Windows (y compris le MQSAgent) sur un second ordinateur, relié à un ou plusieurs ordinateurs supplémentaires qui exécutent un serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="b36e6-106">BizTalk Server and the adapter on one computer, and MQSeries Server for Windows (including the MQSAgent) on a second computer, which connects to one or more additional computers that are running MQSeries Server.</span></span>  
  
-   <span data-ttu-id="b36e6-107">Installations multiples de BizTalk Server dans un groupe et l'adaptateur, et le serveur MQSeries (y compris MQSAgent) sur un ordinateur séparé.</span><span class="sxs-lookup"><span data-stu-id="b36e6-107">Multiple BizTalk Server installations in a group and the adapter, and MQSeries Server (including MQSAgent) on a separate computer.</span></span>  
  
-   <span data-ttu-id="b36e6-108">L'adaptateur fonctionne correctement si vous mettez en cluster le serveur MQSeries et les gestionnaires de file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="b36e6-108">The adapter functions correctly if you cluster MQSeries Server and the MQSeries Queue Managers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b36e6-109">Dans ce cas, l'application MQSAgent COM+ ne doit pas être mise en cluster.</span><span class="sxs-lookup"><span data-stu-id="b36e6-109">The MQSAgent COM+ application should not be clustered in this case.</span></span> <span data-ttu-id="b36e6-110">A la place, l'application MQSAgent COM+ doit être installée et configurée au niveau des deux nœuds du cluster.</span><span class="sxs-lookup"><span data-stu-id="b36e6-110">Instead, both nodes of the cluster should have the MQSAgent COM+ application installed and configured.</span></span> <span data-ttu-id="b36e6-111">Dans ce scénario, si l'application MQSAgent COM+ s'arrête, le prochain appel de la part du client la redémarre.</span><span class="sxs-lookup"><span data-stu-id="b36e6-111">In this scenario, if the MQSAgent COM+ application stops, the next call from the client will restart it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36e6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b36e6-112">See Also</span></span>  
 [<span data-ttu-id="b36e6-113">À l’aide de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="b36e6-113">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)
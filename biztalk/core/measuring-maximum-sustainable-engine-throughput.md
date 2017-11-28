---
title: "Mesurer le débit de moteur maximal acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST)
- maximum sustainable throughput (MST), about maximum sustainable throughput (MST)
- performance, maximum sustainable thoughput (MST)
ms.assetid: d83f734f-1a44-4da0-a755-45ba204cadaf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5507aca58669ed5c81034ba91e16d1183e07188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="measuring-maximum-sustainable-engine-throughput"></a><span data-ttu-id="ec05b-102">Mesure du débit maximal acceptable du moteur</span><span class="sxs-lookup"><span data-stu-id="ec05b-102">Measuring Maximum Sustainable Engine Throughput</span></span>
<span data-ttu-id="ec05b-103">L'une des principaux points à prendre en compte lors de la planification d'un système BizTalk Server est le débit maximal acceptable du système.</span><span class="sxs-lookup"><span data-stu-id="ec05b-103">One of the primary considerations when planning a BizTalk Server system should be to determine the maximum sustainable throughput (MST) of the system.</span></span> <span data-ttu-id="ec05b-104">Le débit maximal acceptable d'un système BizTalk Server correspond à la charge maximale de flux de messages qu'un système BizTalk est capable de gérer indéfiniment dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="ec05b-104">The MST of a BizTalk Server system is measured as the highest load of message traffic that the BizTalk system can handle indefinitely in production.</span></span> <span data-ttu-id="ec05b-105">Cette valeur est très importante car lorsque la charge dépasse le débit maximal acceptable, les messages sont mis en file d'attente dans la base de données MessageBox, ce qui peut en retarder la livraison.</span><span class="sxs-lookup"><span data-stu-id="ec05b-105">This is important because as load exceeds MST, messages are backlogged in the MessageBox database and message delivery may be delayed.</span></span> <span data-ttu-id="ec05b-106">Si vous calculez le débit maximal acceptable de votre système BizTalk Server dans le cadre d'un test normal, vous pouvez adapter votre système de façon à éviter des scénarios de surcharge étendue dans l'environnement de production.</span><span class="sxs-lookup"><span data-stu-id="ec05b-106">If you calculate the MST of your BizTalk Server system as part of normal testing then you can scale your system to avoid extended overload scenarios in production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec05b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ec05b-107">In This Section</span></span>  
  
-   [<span data-ttu-id="ec05b-108">Facteurs qui affectent les performances maximales admissibles</span><span class="sxs-lookup"><span data-stu-id="ec05b-108">Factors that Affect Maximum Sustainable Performance</span></span>](../core/factors-that-affect-maximum-sustainable-performance.md)  
  
-   [<span data-ttu-id="ec05b-109">Scénarios de test pour mesurer le débit maximal acceptable du moteur</span><span class="sxs-lookup"><span data-stu-id="ec05b-109">Test Scenarios for Measuring MST of the Engine</span></span>](../core/test-scenarios-for-measuring-mst-of-the-engine.md)  
  
-   [<span data-ttu-id="ec05b-110">Recommandations pour le test de performances du moteur</span><span class="sxs-lookup"><span data-stu-id="ec05b-110">Recommendations When Testing Engine Performance</span></span>](../core/recommendations-when-testing-engine-performance.md)
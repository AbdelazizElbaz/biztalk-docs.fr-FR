---
title: Planification de Message et le suivi des instances | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HAT, planning
- planning, HAT
ms.assetid: 69b0d30e-77df-4847-9a59-6dd806152b71
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506dcd8342b016b325544f63f95c76c87dcc0772
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-message-and-instance-tracking"></a><span data-ttu-id="90961-102">Planification du suivi des messages et des instances</span><span class="sxs-lookup"><span data-stu-id="90961-102">Planning for Message and Instance Tracking</span></span>
<span data-ttu-id="90961-103">Vous devriez décider au cours des étapes de planification de quelles informations doivent faire l'objet d'un suivi, de sorte qu'après avoir déployé le projet, vous puissiez définir les options de suivi et limiter le volume de données suivies afin de n'obtenir que les informations dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="90961-103">You should decide during the planning stages which information you need to track, so that after you deploy the project you can set the tracking options and limit the amount of tracked data to give you only the information you need.</span></span>  
  
 <span data-ttu-id="90961-104">Il est déconseillé de suivre tous les messages, car le dispositif de suivi des instances du serveur et des messages BizTalk Server crée une copie de chaque message suivi.</span><span class="sxs-lookup"><span data-stu-id="90961-104">We recommend that you do not track all messages, because each time a message is touched, BizTalk Server message and server instance tracking makes another copy.</span></span> <span data-ttu-id="90961-105">Vous pouvez par exemple limiter l'étendue du suivi en ne l'activant que sur un port spécifique.</span><span class="sxs-lookup"><span data-stu-id="90961-105">For example, you can narrow the scope by tracking only a specific port.</span></span> <span data-ttu-id="90961-106">Les performances de votre système s'en trouveront optimisées et la base de données ne risquera pas d'être encombrée.</span><span class="sxs-lookup"><span data-stu-id="90961-106">This helps to maximize the performance of your system and keep the databases uncluttered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90961-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90961-107">See Also</span></span>  
 [<span data-ttu-id="90961-108">Gestion et l’Architecture de suivi</span><span class="sxs-lookup"><span data-stu-id="90961-108">Management and Tracking Architecture</span></span>](../core/management-and-tracking-architecture.md)
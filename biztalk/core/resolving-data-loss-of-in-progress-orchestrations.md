---
title: "Résolution de la perte de données d’Orchestrations d’en cours | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, MessageBox database
- data recovery
- data loss, recovery
- data loss, orchestrations
- data recovery, MessageBox database
- data recovery, orchestrations
- data loss, data recovery
- orchestrations, data recovery
- orchestrations, data loss
ms.assetid: dc6f1fd2-1976-40f2-ab57-41c7db40705e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eca757b80e31ee5db829d2d2079bf657d01079b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-data-loss-of-in-progress-orchestrations"></a><span data-ttu-id="f1a92-102">Résolution de la perte de données dans les orchestrations de type In-Progress</span><span class="sxs-lookup"><span data-stu-id="f1a92-102">Resolving Data Loss of In-Progress Orchestrations</span></span>
<span data-ttu-id="f1a92-103">Les bases de données MessageBox contiennent l'état des orchestrations actuellement en cours.</span><span class="sxs-lookup"><span data-stu-id="f1a92-103">MessageBox databases contain the state of orchestrations that are currently in progress.</span></span> <span data-ttu-id="f1a92-104">Bien qu'il n'existe aucune méthode permettant de savoir précisément quelles données ont été perdues dans ces bases de données, procédez comme suit afin de collecter des informations concernant les pertes de données :</span><span class="sxs-lookup"><span data-stu-id="f1a92-104">Although there is no way to tell exactly what data has been lost from the MessageBox databases, there are some steps you can take to gather information about the lost data:</span></span>  
  
-   <span data-ttu-id="f1a92-105">Déterminez les messages qui ont été envoyés et reçus dans les orchestrations actuelles, ainsi que les systèmes externes qui ont été utilisés après le point de récupération.</span><span class="sxs-lookup"><span data-stu-id="f1a92-105">Determine what messages have been sent and received in the current orchestrations, and what external systems have been used after the point of recovery.</span></span> <span data-ttu-id="f1a92-106">Par exemple, si votre système conserve un journal externe des messages et des événements, examinez celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f1a92-106">For example, if your system maintains an external log of messages and events, you can examine that log.</span></span> <span data-ttu-id="f1a92-107">Vous pouvez également consulter manuellement les systèmes externes pour savoir quelles activités se sont produites.</span><span class="sxs-lookup"><span data-stu-id="f1a92-107">You may also need to manually review the external systems to see what activities have occurred.</span></span>  
  
-   <span data-ttu-id="f1a92-108">Après avoir déterminé la cause de la perte de données, vous pouvez commencer à corriger le système restauré, en choisissant les processus qui peuvent continuer, ceux qui doivent être terminés et redémarrés (en renvoyant les messages d'activation perdus) et ceux qui ont été correctement exécutés et peuvent à présent être fermés.</span><span class="sxs-lookup"><span data-stu-id="f1a92-108">After you determine the cause of the data loss, you can begin to correct the restored system, deciding which processes can continue, which processes must be terminated and restarted (by resubmitting the lost activation messages), and which processes have completed successfully and can be terminated.</span></span> <span data-ttu-id="f1a92-109">Ce processus repose en grande partie sur l'architecture de votre système : il doit donc être considéré comme partie intégrante de votre stratégie de récupération du système.</span><span class="sxs-lookup"><span data-stu-id="f1a92-109">This process depends largely on the architecture of your system and must be considered as part of your system recovery planning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a92-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1a92-110">See Also</span></span>  
 [<span data-ttu-id="f1a92-111">Résolution de la perte de données</span><span class="sxs-lookup"><span data-stu-id="f1a92-111">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)
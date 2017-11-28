---
title: "Pour gérer plusieurs emplacements à l’aide de l’adaptateur MSMQ de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, threads
- receive locations, multiple
- threads
- receive locations, MSMQ adapters
- receive locations, threads
- configuring [MSMQ adapters], receive locations
ms.assetid: 5b2ee043-bcc9-443b-84b0-df7f487159eb
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72438551d2ecab09b918808d43e7d7de6d600677
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-multiple-receive-locations-using-the-msmq-adapter"></a><span data-ttu-id="bfa4f-102">Gestion de plusieurs emplacements de réception à l'aide de l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="bfa4f-102">How to Manage Multiple Receive Locations Using the MSMQ Adapter</span></span>
<span data-ttu-id="bfa4f-103">Afin améliorer les performances, l'adaptateur MSMQ est du type multithread.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-103">To increase performance, the MSMQ adapter is multithreaded.</span></span> <span data-ttu-id="bfa4f-104">Si vous disposez de plusieurs emplacements de réception, il risque de ne pas y avoir suffisamment de threads disponibles pour chacun d'entre eux.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-104">If you have many receive locations, there may not be enough threads available for all the receive locations.</span></span> <span data-ttu-id="bfa4f-105">Cette restriction empêche ainsi certains emplacements de réception de récupérer des messages.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-105">This prevents some of the receive locations from picking up messages.</span></span> <span data-ttu-id="bfa4f-106">Il existe trois méthodes permettant de résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="bfa4f-106">There are three ways to solve this problem:</span></span>  
  
-   <span data-ttu-id="bfa4f-107">ajouter des hôtes BizTalk à vos ordinateurs et répartir les emplacements de réception parmi les hôtes.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-107">Add BizTalk Hosts to your computer and divide the receive locations among the hosts.</span></span> <span data-ttu-id="bfa4f-108">L'ajout d'hôtes augmente le nombre de threads disponibles pour les emplacements de réception ;</span><span class="sxs-lookup"><span data-stu-id="bfa4f-108">Adding hosts makes more threads available for the receive locations.</span></span>  
  
-   <span data-ttu-id="bfa4f-109">Définir le **traitement en série** propriété `True` sur chaque emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-109">Set the **Serial Processing** property to `True` on each receive location.</span></span> <span data-ttu-id="bfa4f-110">La propriété `True` attribue un seul thread à chaque emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-110">Setting the property to `True` assigns a single thread to each receive location.</span></span> <span data-ttu-id="bfa4f-111">Ainsi, davantage de threads sont disponibles dans le pool.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-111">This leaves more threads available in the pool.</span></span> <span data-ttu-id="bfa4f-112">Toutefois, cela risque d'entraîner la réduction des performances ;</span><span class="sxs-lookup"><span data-stu-id="bfa4f-112">However, this may also cause a decrease in performance.</span></span>  
  
-   <span data-ttu-id="bfa4f-113">modifier le Registre de manière à augmenter le nombre de threads accessibles à l'hôte pour le gestionnaire de réception de l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bfa4f-113">Modify the registry to increase the number of threads that are available to the host for the MSMQ adapter receive handler.</span></span> <span data-ttu-id="bfa4f-114">Pour plus d’informations, consultez la **modifier les valeurs de thread CLR Hosting de l’hôte** section de [les paramètres de Configuration qui affectent les performances carte](../core/configuration-parameters-that-affect-adapter-performance.md).</span><span class="sxs-lookup"><span data-stu-id="bfa4f-114">For more information see the **Modify the CLR Hosting thread values for the host** section of [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa4f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfa4f-115">See Also</span></span>  
 [<span data-ttu-id="bfa4f-116">Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="bfa4f-116">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)
---
title: "Architecture réduite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
ms.assetid: e25798aa-4a1e-418c-9e0c-db964e8b5a80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a112f3f737a1a5aec0cfac16b7689d3dada1e8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-down-architecture"></a><span data-ttu-id="fa42b-102">Architecture réduite</span><span class="sxs-lookup"><span data-stu-id="fa42b-102">Scaled Down Architecture</span></span>
<span data-ttu-id="fa42b-103">Pour plus d’informations sur l’architecture système pour[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).</span><span class="sxs-lookup"><span data-stu-id="fa42b-103">For complete information about the system architecture for[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="fa42b-104">La figure suivante fournit un exemple d'architecture [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui combine certains domaines et serveurs BizTalk pour réduire le nombre de serveurs et de pare-feu nécessaires.</span><span class="sxs-lookup"><span data-stu-id="fa42b-104">The following figure provides a sample [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture that combines some of the domains and BizTalk Servers to reduce the number of servers and firewalls you need.</span></span> <span data-ttu-id="fa42b-105">Bien que cette architecture ne soit pas la plus distribuée, elle différencie toujours les serveurs BizTalk Server selon leur fonction.</span><span class="sxs-lookup"><span data-stu-id="fa42b-105">While this architecture is not the most distributed, it still separates the BizTalk Servers based on their function.</span></span>  
  
 <span data-ttu-id="fa42b-106">![Architecture réduite](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")</span><span class="sxs-lookup"><span data-stu-id="fa42b-106">![Scaled down architecture](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")</span></span>  
  
        Scaled Down Architecture  
  
 <span data-ttu-id="fa42b-107">Dans la figure précédente, les serveurs des interfaces de service et du domaine des services correspondent aux hôtes BizTalk, et non aux serveurs physiques.</span><span class="sxs-lookup"><span data-stu-id="fa42b-107">In the previous figure, the servers in the service interfaces and services domain correspond to BizTalk Hosts, and not physical servers.</span></span> <span data-ttu-id="fa42b-108">Même s'il est recommandé de conserver le serveur de secret principal et les outils d'administration dans des ordinateurs isolés, vous pouvez avoir des instances d'hôte pour le suivi, le traitement, l'envoi et la réception des hôtes exécutés sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="fa42b-108">While it is recommended to keep the master secret server and the administrative tools in stand-alone computers, you can have host instances for the tracking, processing, send, and receive hosts running on multiple computers.</span></span> <span data-ttu-id="fa42b-109">De même, les serveurs du réseau de périmètre correspondent aux emplacements logiques.</span><span class="sxs-lookup"><span data-stu-id="fa42b-109">Similarly, the servers in the perimeter network correspond to logical locations.</span></span>  
  
 <span data-ttu-id="fa42b-110">Les serveurs du réseau de périmètre pour SMTP, Message Queuing, FILE, et SQL correspondent respectivement aux serveurs de messagerie, à la file d'attente, au répertoire et aux serveurs SQL Server à partir desquels les hôtes BizTalk envoient et reçoivent des messages dans le domaine des services.</span><span class="sxs-lookup"><span data-stu-id="fa42b-110">The servers in the perimeter network for SMTP, Message Queuing, File, and SQL correspond to the mail servers, queue, directory, or SQL Server respectively from which the BizTalk receive and send hosts in the processing and services domain receive and send messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa42b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa42b-111">See Also</span></span>  
 <span data-ttu-id="fa42b-112">[Architecture réduite avec des Services destinés aux travailleurs](../core/scaled-down-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="fa42b-112">[Scaled Down Architecture with Information Worker Services](../core/scaled-down-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="fa42b-113">[Architecture distribuée](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="fa42b-113">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="fa42b-114">[Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="fa42b-114">[Designing a Secure Architecture](../core/designing-a-secure-architecture.md) </span></span>  
 [<span data-ttu-id="fa42b-115">Exemples d’architecture BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fa42b-115">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)
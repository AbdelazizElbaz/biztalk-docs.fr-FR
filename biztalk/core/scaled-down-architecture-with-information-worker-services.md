---
title: "Architecture réduite avec des Services destinés aux travailleurs | Documents Microsoft"
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
ms.assetid: ce1217bf-84a5-4888-89ba-dce85dc38340
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d02558e5904bf740c09ea0db614b2189555ac75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-down-architecture-with-information-worker-services"></a><span data-ttu-id="d92f7-102">Architecture réduite avec des services destinés aux travailleurs de l'information</span><span class="sxs-lookup"><span data-stu-id="d92f7-102">Scaled Down Architecture with Information Worker Services</span></span>
<span data-ttu-id="d92f7-103">Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).</span><span class="sxs-lookup"><span data-stu-id="d92f7-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="d92f7-104">La figure suivante fournit un exemple d'architecture BizTalk Server incluant les services destinés aux travailleurs de l'information et qui combine certains domaines et serveurs BizTalk Server pour réduire le nombre de serveurs et de pare-feu nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d92f7-104">The following figure provides a sample BizTalk Server architecture including the information worker services that combines some of the domains and BizTalk Servers to reduce the number of servers and firewalls you need.</span></span> <span data-ttu-id="d92f7-105">Bien que cette architecture ne soit pas la plus distribuée, elle différencie toujours les serveurs BizTalk Server selon leur fonction.</span><span class="sxs-lookup"><span data-stu-id="d92f7-105">While this architecture is not the most distributed, it still separates the BizTalk Servers based on their function.</span></span>  
  
 <span data-ttu-id="d92f7-106">![Topologie de réduction](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")</span><span class="sxs-lookup"><span data-stu-id="d92f7-106">![Scaledown Topology](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")</span></span>  
  
        Scaled Down Architecture with Information Worker Services  
  
 <span data-ttu-id="d92f7-107">Dans la figure précédente, les serveurs des interfaces de service et du domaine des services correspondent aux hôtes BizTalk, et non aux serveurs physiques.</span><span class="sxs-lookup"><span data-stu-id="d92f7-107">In the previous figure, the servers in the service interfaces and services domain correspond to BizTalk Hosts, and not physical servers.</span></span> <span data-ttu-id="d92f7-108">Même s'il est recommandé de conserver le serveur de secret principal et les outils d'administration dans des ordinateurs isolés, vous pouvez avoir des instances d'hôte pour le suivi, le traitement, l'envoi et la réception des hôtes exécutés sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d92f7-108">While it is recommended to keep the master secret server and the administrative tools in stand-alone computers, you can have host instances for the tracking, processing, send, and receive hosts running on multiple computers.</span></span> <span data-ttu-id="d92f7-109">De même, les serveurs du réseau de périmètre correspondent aux emplacements logiques.</span><span class="sxs-lookup"><span data-stu-id="d92f7-109">Similarly, the servers in the perimeter network correspond to logical locations.</span></span>  
  
 <span data-ttu-id="d92f7-110">Les serveurs du réseau de périmètre pour SMTP, Windows Message Queuing (également nommé MSMQ), File et SQL correspondent respectivement aux serveurs de messagerie, à la file d'attente, au répertoire et aux serveurs SQL Server à partir desquels les hôtes de BizTalk reçoivent et envoient des messages dans le domaine des interfaces de service.</span><span class="sxs-lookup"><span data-stu-id="d92f7-110">The servers in the perimeter network for SMTP, Windows Message Queuing (also known as MSMQ), File, and SQL correspond to the mail servers, queue, directory, or SQL Server respectively from which the BizTalk receive and send hosts in the service interfaces domain receive and send messages.</span></span>  
  
 <span data-ttu-id="d92f7-111">Les bases de données BAM du domaine de données sont les bases de données d'importation principale BAM, d'analyse BAM, de schémas en étoile BAM et des archives BAM.</span><span class="sxs-lookup"><span data-stu-id="d92f7-111">The BAM databases in the data domain are BAM Primary Import, BAM Analysis, BAM Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="d92f7-112">BizTalk Server utilise les bases de données d'analyse et des suivis du domaine de données pour le stockage des informations de suivi.</span><span class="sxs-lookup"><span data-stu-id="d92f7-112">The Tracking and Analysis databases in the Data domain are the ones BizTalk Server uses for storing tracking information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92f7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d92f7-113">See Also</span></span>  
 <span data-ttu-id="d92f7-114">[Architecture réduite](../core/scaled-down-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="d92f7-114">[Scaled Down Architecture](../core/scaled-down-architecture.md) </span></span>  
 <span data-ttu-id="d92f7-115">[Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="d92f7-115">[Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="d92f7-116">[Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="d92f7-116">[Designing a Secure Architecture](../core/designing-a-secure-architecture.md) </span></span>  
 [<span data-ttu-id="d92f7-117">Exemples d’architecture BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d92f7-117">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)
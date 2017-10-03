---
title: "Comportement des Instances d’hôte BizTalk Server au cours de basculement SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5642417-d27f-4539-a369-5fa11bec4a4f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f244ce0fe00fe05f73db5f43ec867254b7a61fb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="behavior-of-biztalk-server-host-instances-during-sql-server-failover"></a><span data-ttu-id="037bb-102">Comportement des instances de l'hôte BizTalk Server pendant le basculement de SQL Server</span><span class="sxs-lookup"><span data-stu-id="037bb-102">Behavior of BizTalk Server Host Instances during SQL Server Failover</span></span>
<span data-ttu-id="037bb-103">Les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergées sur une instance de Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] mise en cluster sont provisoirement inaccessibles si l'instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] subit un basculement.</span><span class="sxs-lookup"><span data-stu-id="037bb-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases housed on a clustered instance of Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are temporarily unavailable if the clustered instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] experiences a failover.</span></span> <span data-ttu-id="037bb-104">Cette rubrique présente le comportement des instances de l'hôte associées à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lorsque les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="037bb-104">This section documents the behavior of the host instances associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable.</span></span>  
  
## <a name="behavior-of-in-process-host-instances-during-sql-server-failover"></a><span data-ttu-id="037bb-105">Comportement des instances de l'hôte In-process au cours d'un basculement SQL Server</span><span class="sxs-lookup"><span data-stu-id="037bb-105">Behavior of In-Process Host Instances during SQL Server Failover</span></span>  
 <span data-ttu-id="037bb-106">Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont inaccessibles, une instance en cours d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôte va être recyclé jusqu'à ce que la connexion à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est restaurée.</span><span class="sxs-lookup"><span data-stu-id="037bb-106">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable, then an in-process instance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host will be recycled until the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is restored.</span></span> <span data-ttu-id="037bb-107">Une fois la connexion à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données est restaurée, le traitement des documents reprend normalement.</span><span class="sxs-lookup"><span data-stu-id="037bb-107">Once the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases is restored, document processing resumes normally.</span></span>  
  
## <a name="behavior-of-isolated-host-instances-during-sql-server-failover"></a><span data-ttu-id="037bb-108">Comportement des instances de l'hôte isolé au cours d'un basculement de SQL Server</span><span class="sxs-lookup"><span data-stu-id="037bb-108">Behavior of Isolated Host Instances During SQL Server Failover</span></span>  
 <span data-ttu-id="037bb-109">Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont inaccessibles, une instance isolée de l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est suspendue et une erreur identique à la suivante est générée dans le journal de l'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="037bb-109">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable, then an isolated instance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host will pause and an error similar to the following will be generated in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application log:</span></span>  
  
```  
All receive locations are being temporarily disabled because either   
the MessageBox or Configuration database is not available.   
When these databases become available, the receive locations will be automatically enabled.  
```  
  
 <span data-ttu-id="037bb-110">Une fois la connexion aux bases de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] rétablie, un message d'information identique au suivant est inscrit dans le journal de l'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et le traitement des documents reprend normalement :</span><span class="sxs-lookup"><span data-stu-id="037bb-110">Once the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases is restored an informational message similar to the following is written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application log and document processing resumes normally:</span></span>  
  
```  
All receive locations are being enabled because both the MessageBox and Configuration databases are back online.  
```  
  
## <a name="see-also"></a><span data-ttu-id="037bb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="037bb-111">See Also</span></span>  
 [<span data-ttu-id="037bb-112">Ordinateurs hôtes</span><span class="sxs-lookup"><span data-stu-id="037bb-112">Hosts</span></span>](../core/hosts.md)
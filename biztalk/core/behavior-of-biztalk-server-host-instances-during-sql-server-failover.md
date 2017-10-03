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
# <a name="behavior-of-biztalk-server-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte BizTalk Server pendant le basculement de SQL Server
Les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergées sur une instance de Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] mise en cluster sont provisoirement inaccessibles si l'instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] subit un basculement. Cette rubrique présente le comportement des instances de l'hôte associées à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lorsque les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont inaccessibles.  
  
## <a name="behavior-of-in-process-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte In-process au cours d'un basculement SQL Server  
 Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont inaccessibles, une instance en cours d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôte va être recyclé jusqu'à ce que la connexion à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est restaurée. Une fois la connexion à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données est restaurée, le traitement des documents reprend normalement.  
  
## <a name="behavior-of-isolated-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte isolé au cours d'un basculement de SQL Server  
 Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont inaccessibles, une instance isolée de l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est suspendue et une erreur identique à la suivante est générée dans le journal de l'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
```  
All receive locations are being temporarily disabled because either   
the MessageBox or Configuration database is not available.   
When these databases become available, the receive locations will be automatically enabled.  
```  
  
 Une fois la connexion aux bases de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] rétablie, un message d'information identique au suivant est inscrit dans le journal de l'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et le traitement des documents reprend normalement :  
  
```  
All receive locations are being enabled because both the MessageBox and Configuration databases are back online.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ordinateurs hôtes](../core/hosts.md)
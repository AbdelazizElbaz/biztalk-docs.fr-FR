---
title: "Exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 906c6352-44f3-4624-9e32-aea3fbb7510d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36a1ff6e4b2c7d4d56855ce1531f99cd490a2a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-composite-operations-in-sql-server--using-the-sql-adapter"></a>Exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données SQL Server. Une opération composite peut inclure plusieurs des opérations suivantes et dans n’importe quel ordre :  
  
-   Les opérations Insert, Update et Delete sur les tables et les vues.  
  
-   Procédures stockées qui sont signalées en tant qu’opérations dans l’adaptateur.  
  
 Les opérations dans une opération composite *doit* ciblent des tables et des vues uniquement dans une base de données.  
  
 Pour plus d’informations sur :  
  
-   Comment effectuer des opérations composites dans [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md).  
  
-   Schémas pour l’opération composite de messages, consultez [des schémas de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).  
  
> [!IMPORTANT]
>  S’il existe un nombre « n » des opérations dans une opération composite qui retournent des résultats ensemble puis « n + 1 » nombre de connexions est requis pour l’opération composite doit être exécuté. Par conséquent, vous devez vous assurer que la valeur spécifiée pour le **MaxConnectionPoolSize** propriété de liaison est n + 1 ou supérieur. Pour plus d’informations sur la **MaxConnectionPoolSize** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)
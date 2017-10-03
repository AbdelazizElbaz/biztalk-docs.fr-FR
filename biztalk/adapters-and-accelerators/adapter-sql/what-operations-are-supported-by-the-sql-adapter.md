---
title: "Les opérations sont prises en charge par l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f4099-df19-48c4-a135-1ec264af3513
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59d413a763823f49b0bf905b42d8513cbbb1e745
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-sql-adapter"></a>Les opérations sont prises en charge par l’adaptateur SQL
Vous pouvez utiliser les clients de la carte pour effectuer des opérations sur la base de données SQL Server par :  
  
-   Création de projets BizTalk  
  
-   À l’aide du modèle de service WCF  
  
-   À l’aide du modèle de canal WCF  
  
 Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal. Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).  
  
 Cette section fournit des informations sur les opérations prises en charge sur la base de données SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)
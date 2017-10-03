---
title: "Se connecter à SQL Server à l’aide de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727d73e6-fb84-48ce-ae72-5de70dcae8b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9b837aa4e0bc0a815434307b10d249dccf54d70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-using-the-adapter"></a>Se connecter à SQL Server à l’aide de l’adaptateur
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exige que les clients de l’adaptateur fournir une chaîne de connexion, appelée la connexion identificateur URI (Uniform Resource), pour se connecter à la base de données SQL Server. En interne, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] mappe l’URI vers une chaîne de connexion de base de données pour se connecter à la base de données SQL Server. Avec un URI de connexion, les clients de carte peuvent spécifier des paramètres de connexion pour se connecter à un système externe. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
 Dans l’URI de connexion, vous pouvez également spécifier le nom d’une base de données de basculement SQL Server sur un ordinateur de secours pour se connecter à, si la base de données SQL Server principal n’est pas disponible. La base de données de basculement SQL Server doit être un miroir de la base de données SQL Server principal. La base de données de basculement SQL Server est spécifié à l’aide d’un paramètre facultatif, FailoverPartner, dans l’URI de connexion. En fournissant une base de données de basculement SQL Server garantit la haute disponibilité et la redondance des données. Pour plus d’informations sur la haute disponibilité par rapport à SQL Server, consultez [mise en miroir de base de données dans SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).
  
 Veillez à que respecter les consignes de sécurité lors de l’établissement d’une connexion avec la base de données SQL Server. Pour plus d’informations sur les règles de sécurité, consultez [sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [Créer une connexion à SQL Server](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)
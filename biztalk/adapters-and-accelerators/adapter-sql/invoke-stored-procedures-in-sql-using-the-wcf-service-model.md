---
title: "Appeler les procédures stockées de SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edd2fac-0b54-4406-932e-e3044a66b2e6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2d707c37ba92fb6f1d1608ae43d02d1e964cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-stored-procedures-in-sql-using-the-wcf-service-model"></a>Appeler les procédures stockées de SQL à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte les procédures stockées en tant qu’opérations que les clients de l’adaptateur peuvent appeler sur le client WCF pour appeler la procédure stockée. Selon la façon dont la procédure stockée retourne le jeu de résultats, l’adaptateur de classe toutes les procédures stockées en tant que :  
  
-   **Procédures**. Appel de procédures stockées à partir de la **procédures** nœud retourne un tableau du jeu de données.  
  
-   **Fortement typée procédures**. Appel de procédures stockées à partir de la **fortement typée procédures** nœud retourne un jeu de résultats de fortement typée.  
  
 Notez que le même jeu de procédures stockées dans la base de données vous connecté seront répertoriés à la fois le **procédures** et **fortement typée procédures** nœud. Selon le type de jeu de résultats, vous devez appeler la procédure stockée à partir du nœud approprié. Pour plus d’informations sur la façon dont [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge les procédures stockées, consultez [exécuter les procédures stockées de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  
  
 Cette section fournit des instructions sur la façon d’appeler des procédures stockées à partir du **procédures** et **fortement typée procédures** nœud à l’aide d’un client WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Involk faiblement typée de procédures stockées dans SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [Appeler fortement typée de procédure stockée dans SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
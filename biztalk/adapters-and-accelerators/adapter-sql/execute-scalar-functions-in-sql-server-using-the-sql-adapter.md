---
title: "Exécuter des fonctions scalaires dans SQL Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ef70114-215e-49ed-87d2-7590db605a2c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbd039039535f87ef32ec86bfc6bc982ced4210
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-scalar-functions-in-sql-server-using-the-sql-adapter"></a>Exécuter des fonctions scalaires dans SQL Server à l’aide de l’adaptateur SQL
Les fonctions scalaires Transact-SQL et CLR dans SQL Server sont exposées en tant que des opérations dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]. Le nom de l’opération dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est le même que le nom de la fonction scalaire dans SQL Server.  
  
 Tous les paramètres dans la fonction scalaire sont exposés dans l’opération correspondante. La valeur de retour de l’opération dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est identique à la valeur de retour définie dans la fonction scalaire dans SQL Server.  
  
 Pour plus d’informations sur l’exécution de fonctions scalaires, consultez [appeler les fonctions scalaires dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)
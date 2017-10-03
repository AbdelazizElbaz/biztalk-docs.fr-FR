---
title: "Exécuter des fonctions de table dans SQL Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fb8c81c-9384-4eba-b0a0-baed1782245b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69877f214a2a4b700de22ec043094510707114d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-table-valued-functions-in-sql-server-using-the-sql-adapter"></a>Exécuter des fonctions de table dans SQL Server à l’aide de l’adaptateur SQL
Les fonctions table Transact-SQL et CLR dans SQL Server sont exposées en tant que des opérations dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]. Le nom de l’opération dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est le même que le nom de la table table fonction dans SQL Server.  
  
 Tous les paramètres dans la fonction table sont exposés dans l’opération correspondante. Si vous ne spécifiez pas un paramètre d’entrée pour une fonction table, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en interne appelle la fonction à l’aide du mot clé DEFAULT. Cela implique que la fonction table est exécutée à l’aide de la valeur par défaut spécifiée lors de la définition de la fonction.  
  
 Pour plus d’informations sur :  
  
-   À l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec BizTalk Server pour appeler des fonctions table dans SQL Server, consultez [Invoking Table-Valued des fonctions dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).  
  
-   Structure et des actions SOAP pour les fonctions table des messages, consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)
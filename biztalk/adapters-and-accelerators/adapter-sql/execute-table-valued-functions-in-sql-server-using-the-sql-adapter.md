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
# <a name="execute-table-valued-functions-in-sql-server-using-the-sql-adapter"></a><span data-ttu-id="c8501-102">Exécuter des fonctions de table dans SQL Server à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="c8501-102">Execute Table-Valued Functions in SQL Server using the SQL adapter</span></span>
<span data-ttu-id="c8501-103">Les fonctions table Transact-SQL et CLR dans SQL Server sont exposées en tant que des opérations dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8501-103">The Transact-SQL and CLR table valued functions in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="c8501-104">Le nom de l’opération dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est le même que le nom de la table table fonction dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c8501-104">The operation name in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the name of the table valued function in SQL Server.</span></span>  
  
 <span data-ttu-id="c8501-105">Tous les paramètres dans la fonction table sont exposés dans l’opération correspondante.</span><span class="sxs-lookup"><span data-stu-id="c8501-105">All the parameters in the table valued function are exposed in the corresponding operation.</span></span> <span data-ttu-id="c8501-106">Si vous ne spécifiez pas un paramètre d’entrée pour une fonction table, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en interne appelle la fonction à l’aide du mot clé DEFAULT.</span><span class="sxs-lookup"><span data-stu-id="c8501-106">If you do not specify an input parameter for a table valued function, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] internally invokes the function using the DEFAULT keyword.</span></span> <span data-ttu-id="c8501-107">Cela implique que la fonction table est exécutée à l’aide de la valeur par défaut spécifiée lors de la définition de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c8501-107">This implies that the table valued function is executed using the default value specified while defining the function.</span></span>  
  
 <span data-ttu-id="c8501-108">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="c8501-108">For more information about:</span></span>  
  
-   <span data-ttu-id="c8501-109">À l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec BizTalk Server pour appeler des fonctions table dans SQL Server, consultez [Invoking Table-Valued des fonctions dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="c8501-109">Using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with BizTalk Server to invoke table valued functions in SQL Server, see [Invoking Table-Valued Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c8501-110">Structure et des actions SOAP pour les fonctions table des messages, consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c8501-110">Message structure and SOAP actions for table valued functions, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8501-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8501-111">See Also</span></span>  
 <span data-ttu-id="c8501-112">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="c8501-112">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>
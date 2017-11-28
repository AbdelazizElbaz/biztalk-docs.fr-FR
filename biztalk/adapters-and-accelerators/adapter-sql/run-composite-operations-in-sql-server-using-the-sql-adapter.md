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
# <a name="run-composite-operations-in-sql-server--using-the-sql-adapter"></a><span data-ttu-id="86f89-102">Exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="86f89-102">Run composite operations in SQL Server  using the SQL adapter</span></span>
<span data-ttu-id="86f89-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="86f89-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] enables adapter clients to perform composite operations on the SQL Server database.</span></span> <span data-ttu-id="86f89-104">Une opération composite peut inclure plusieurs des opérations suivantes et dans n’importe quel ordre :</span><span class="sxs-lookup"><span data-stu-id="86f89-104">A composite operation can include any number of the following operations, and in any order:</span></span>  
  
-   <span data-ttu-id="86f89-105">Les opérations Insert, Update et Delete sur les tables et les vues.</span><span class="sxs-lookup"><span data-stu-id="86f89-105">The Insert, Update, and Delete operations on the tables and views.</span></span>  
  
-   <span data-ttu-id="86f89-106">Procédures stockées qui sont signalées en tant qu’opérations dans l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="86f89-106">Stored procedures that are surfaced as operations in the adapter.</span></span>  
  
 <span data-ttu-id="86f89-107">Les opérations dans une opération composite *doit* ciblent des tables et des vues uniquement dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="86f89-107">The operations in a composite operation *must* target tables and views only in a single database.</span></span>  
  
 <span data-ttu-id="86f89-108">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="86f89-108">For information about:</span></span>  
  
-   <span data-ttu-id="86f89-109">Comment effectuer des opérations composites dans [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="86f89-109">How to perform composite operations in [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Composite Operations on SQL Server Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="86f89-110">Schémas pour l’opération composite de messages, consultez [des schémas de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).</span><span class="sxs-lookup"><span data-stu-id="86f89-110">Message schemas for the composite operation, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="86f89-111">S’il existe un nombre « n » des opérations dans une opération composite qui retournent des résultats ensemble puis « n + 1 » nombre de connexions est requis pour l’opération composite doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="86f89-111">If there are “n” number of operations in a composite operation that return a result set then “n+1” number of connections are required for the composite operation to be executed.</span></span> <span data-ttu-id="86f89-112">Par conséquent, vous devez vous assurer que la valeur spécifiée pour le **MaxConnectionPoolSize** propriété de liaison est n + 1 ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="86f89-112">Therefore, you must ensure that the value specified for the **MaxConnectionPoolSize** binding property is n+1 or greater.</span></span> <span data-ttu-id="86f89-113">Pour plus d’informations sur la **MaxConnectionPoolSize** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="86f89-113">For more information about the **MaxConnectionPoolSize** binding property, see [Read about BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f89-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f89-114">See Also</span></span>  
 <span data-ttu-id="86f89-115">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="86f89-115">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>
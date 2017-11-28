---
title: "Exécuter des opérations composites dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b877d8e3-2016-40e8-888f-6b768021d6b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5595823fab4f25948e3d88db759ae525f62130
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-composite-operations-in-oracle-database"></a><span data-ttu-id="71d21-102">Exécuter des opérations composites dans la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="71d21-102">Run Composite Operations in Oracle Database</span></span>
<span data-ttu-id="71d21-103">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients d’adaptateur effectuer des opérations composites qui peuvent inclure plusieurs des opérations suivantes et dans n’importe quel ordre :</span><span class="sxs-lookup"><span data-stu-id="71d21-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to perform composite operations that can include any number of the following operations, and in any order:</span></span>  
  
-   <span data-ttu-id="71d21-104">Sélectionnez, Insert, Update et les opérations Delete sur les tables et les vues.</span><span class="sxs-lookup"><span data-stu-id="71d21-104">Select, Insert, Update, and Delete operations on tables and views.</span></span>  
  
-   <span data-ttu-id="71d21-105">Procédures stockées, fonctions et procédures ou fonctions dans des packages qui sont signalées en tant qu’opérations dans l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="71d21-105">Stored procedures, functions, and procedures or functions within packages that are surfaced as operations in the adapter.</span></span>  
  
 <span data-ttu-id="71d21-106">Les opérations dans une opération composite peuvent cibler des tables et des vues dans la même base de données ou les bases de données différentes.</span><span class="sxs-lookup"><span data-stu-id="71d21-106">The operations in a composite operation can target tables and views in the same database or different databases.</span></span> <span data-ttu-id="71d21-107">Toutefois, les données ne peut pas être partagées ou réutilisées dans plusieurs opérations dans une opération composite.</span><span class="sxs-lookup"><span data-stu-id="71d21-107">However, data cannot be shared or reused across different operations in a composite operation.</span></span> <span data-ttu-id="71d21-108">Par exemple, dans une opération composite, le jeu de résultats d’une opération de sélection ne peut pas être utilisé comme paramètre d’entrée pour une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="71d21-108">For example, in a composite operation, the result set of a Select operation cannot be used as the input parameter for a stored procedure.</span></span>  
  
 <span data-ttu-id="71d21-109">Chaque opération dans une opération composite est effectuée à l’aide d’une connexion distincte.</span><span class="sxs-lookup"><span data-stu-id="71d21-109">Each operation in a composite operation is performed using a separate connection.</span></span> <span data-ttu-id="71d21-110">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme autant de connexions à partir du pool de connexions ODP.NET en tant que le nombre d’opérations dans une opération composite et libère les connexions que les opérations sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="71d21-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consumes as many connections from the ODP.NET connection pool as the number of operations in a composite operation, and then releases the connections as the operations get executed.</span></span> <span data-ttu-id="71d21-111">Toutefois, si une opération dans l’opération composite renvoie un jeu de résultats, la connexion est libérée uniquement après que le message est utilisé.</span><span class="sxs-lookup"><span data-stu-id="71d21-111">However, if an operation in the composite operation returns a result set, the connection is released only after the message is consumed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71d21-112">Si vous rencontrez des problèmes de délai d’attente lors de l’exécution d’une opération composite ce peut être, car le nombre de connexions est inférieur au nombre d’opérations dans une opération composite impliquant :</span><span class="sxs-lookup"><span data-stu-id="71d21-112">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
>   
>  -   <span data-ttu-id="71d21-113">Les procédures stockées contenant des BFILE, BLOB, CLOB, NCLOB et REF CURSOR comme OUT ou IN OUT.</span><span class="sxs-lookup"><span data-stu-id="71d21-113">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
> -   <span data-ttu-id="71d21-114">Sélectionnez l’opération.</span><span class="sxs-lookup"><span data-stu-id="71d21-114">Select operation.</span></span>  
>   
>  <span data-ttu-id="71d21-115">Pour résoudre ce problème, vous devez vous assurer que s’il existe le nombre de « n » de ces opérations dans une opération composite, la valeur spécifiée pour le **MinPoolSize** propriété de liaison est « n + 1 » ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="71d21-115">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="71d21-116">Pour plus d’informations sur la **MinPoolSize** liaison de propriété, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="71d21-116">For more information about the **MinPoolSize** binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="71d21-117">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="71d21-117">For information about:</span></span>  
  
-   <span data-ttu-id="71d21-118">Comment effectuer des opérations composites dans [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="71d21-118">How to perform composite operations in [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run Composite Operations on Oracle Database by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="71d21-119">Schémas pour l’opération composite de messages, consultez [des schémas de Message pour l’opération Composite](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).</span><span class="sxs-lookup"><span data-stu-id="71d21-119">Message schemas for the composite operation, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d21-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71d21-120">See Also</span></span>  
 <span data-ttu-id="71d21-121">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="71d21-121">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>
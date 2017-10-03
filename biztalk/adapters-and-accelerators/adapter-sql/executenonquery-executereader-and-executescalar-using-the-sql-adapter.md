---
title: "Exécuter ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fda0544-a028-4a95-aae6-1f6a90764c5d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f68f4378a4d89d2a997f5a78a524e4f6bfca2c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a><span data-ttu-id="02097-102">Exécuter ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="02097-102">Run ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations using the SQL adapter</span></span>
<span data-ttu-id="02097-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose les opérations suivantes à la racine :</span><span class="sxs-lookup"><span data-stu-id="02097-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the following operations at the root level:</span></span>  
  
-   <span data-ttu-id="02097-104">**ExecuteNonQuery**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server si vous ne souhaitez pas que n’importe quel jeu de résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="02097-104">**ExecuteNonQuery**: Use this operation to execute any arbitrary SQL statements in SQL Server if you do not want any result set to be returned.</span></span> <span data-ttu-id="02097-105">Vous pouvez cette opération permet de créer des objets de base de données ou modifier des données dans une base de données en exécutant UPDATE, INSERT ou DELETE.</span><span class="sxs-lookup"><span data-stu-id="02097-105">You can use this operation to create database objects or change data in a database by executing UPDATE, INSERT, or DELETE statements.</span></span> <span data-ttu-id="02097-106">La valeur de retour de cette opération est de type de données Int32 et :</span><span class="sxs-lookup"><span data-stu-id="02097-106">The return value of this operation is of Int32 data type, and:</span></span>  
  
    -   <span data-ttu-id="02097-107">Pour les instructions UPDATE, INSERT et DELETE, la valeur de retour est le nombre de lignes affectées par l’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="02097-107">For the UPDATE, INSERT, and DELETE statements, the return value is the number of rows affected by the SQL statement.</span></span>  
  
    -   <span data-ttu-id="02097-108">Pour tous les autres types d’instructions, la valeur de retour est **-1**.</span><span class="sxs-lookup"><span data-stu-id="02097-108">For all other types of statements, the return value is **-1**.</span></span>  
  
-   <span data-ttu-id="02097-109">**ExecuteReader**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server, si vous souhaitez que le jeu de résultats à retourner, si elle existe, comme un tableau de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="02097-109">**ExecuteReader**: Use this operation to execute any arbitrary SQL statements in SQL Server if you want the result set to be returned, if any, as an array of DataSet.</span></span> <span data-ttu-id="02097-110">Pour plus d’informations sur le jeu de données, consultez « Classe DataSet » à [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).</span><span class="sxs-lookup"><span data-stu-id="02097-110">For information about DataSet, see “DataSet Class” at [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).</span></span>  
  
-   <span data-ttu-id="02097-111">**ExecuteScalar**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server pour retourner une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="02097-111">**ExecuteScalar**: Use this operation to execute any arbitrary SQL statements in SQL Server to return a single value.</span></span> <span data-ttu-id="02097-112">Cette opération retourne la valeur uniquement dans la première colonne de la première ligne du jeu de résultats retourné par l’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="02097-112">This operation returns the value only in the first column of the first row in the result set returned by the SQL statement.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02097-113">L’avantage de ExecuteScalar ExecuteReader est que la charge de message de réponse de l’opération ExecuteScalar est beaucoup plus petit comparée à celui retourné par l’opération ExecuteReader.</span><span class="sxs-lookup"><span data-stu-id="02097-113">The advantage of ExecuteScalar over ExecuteReader is that the response message payload of the ExecuteScalar operation is much smaller compared to the one returned by the ExecuteReader operation.</span></span> <span data-ttu-id="02097-114">Par conséquent, si vous avez ne besoin qu’une seule valeur doit être retournée, vous devez utiliser ExecuteScalar au lieu de ExecuteReader.</span><span class="sxs-lookup"><span data-stu-id="02097-114">Therefore, if you require only one value to be returned, you should use ExecuteScalar instead of ExecuteReader.</span></span>  
  
 <span data-ttu-id="02097-115">Vous pouvez utiliser l’opération ExecuteNonQuery, ExecuteReader ou ExecuteScalar d’exécuter plusieurs instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="02097-115">You can use the ExecuteNonQuery, ExecuteReader or ExecuteScalar operation to execute multiple SQL statements.</span></span>  
  
 <span data-ttu-id="02097-116">Pour plus d’informations sur ces opérations à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span><span class="sxs-lookup"><span data-stu-id="02097-116">For more information about performing these operations using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02097-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02097-117">See Also</span></span>  
 <span data-ttu-id="02097-118">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="02097-118">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)</span></span>
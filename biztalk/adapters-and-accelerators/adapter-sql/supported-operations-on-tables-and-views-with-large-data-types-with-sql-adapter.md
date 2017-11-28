---
title: "Opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70f3b863-da3c-45b0-98f2-469a62286ebf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1d6d2c52ce0772297bb2834c13f31a55d7b7a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-and-views-that-contain-large-data-types-using-the-sql-adapter"></a><span data-ttu-id="7bfb6-102">Opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="7bfb6-102">Operations on tables and views that contain large data types using the SQL adapter</span></span>
<span data-ttu-id="7bfb6-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] fournit la prise en charge pour les types de données de grande taille de SQL Server suivants :</span><span class="sxs-lookup"><span data-stu-id="7bfb6-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] provides supports for the following SQL Server large data types:</span></span>  
  
-   <span data-ttu-id="7bfb6-104">Varchar (max)</span><span class="sxs-lookup"><span data-stu-id="7bfb6-104">Varchar(Max)</span></span>  
  
-   <span data-ttu-id="7bfb6-105">Nvarchar (max)</span><span class="sxs-lookup"><span data-stu-id="7bfb6-105">Nvarchar(Max)</span></span>  
  
-   <span data-ttu-id="7bfb6-106">Varbinary (max)</span><span class="sxs-lookup"><span data-stu-id="7bfb6-106">Varbinary(Max)</span></span>  
  
 <span data-ttu-id="7bfb6-107">Pour lire les valeurs de données de grande taille à partir de SQL Server, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="7bfb6-107">To read large data values from SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Select operation.</span></span>  
  
 <span data-ttu-id="7bfb6-108">Pour écrire des valeurs de données de grande taille dans SQL Server, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose l’opération de définition < nom_colonne >, où < nom_colonne > est le nom de la colonne de type varchar (max), nvarchar (max) ou varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="7bfb6-108">To write large data values to SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Set<column_name> operation, where <column_name> is the name of the column of type Varchar(Max), Nvarchar(Max) or Varbinary(Max).</span></span> <span data-ttu-id="7bfb6-109">L’opération Set < nom_colonne > permet également aux clients de carte d’écrire des données FILESTREAM dans SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7bfb6-109">The Set<column_name> operation also allows adapter clients to write FILESTREAM data in SQL Server 2008.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bfb6-110">L’opération Set < nom_colonne > est disponible uniquement pour les tables et les vues qui contiennent des colonnes avec un des trois types de données de grande taille mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="7bfb6-110">The Set<column_name> operation is available only for those tables and views that contain columns with any of the three large data types mentioned earlier.</span></span>  
  
 <span data-ttu-id="7bfb6-111">Pour plus d’informations sur l’exécution d’opérations sur les tables et les vues dans SQL Server qui contiennent des types de données de grande taille, consultez [opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="7bfb6-111">For detailed information about performing operations on tables and views in SQL Server that contain large data types, see [Operations on tables and views that contain large data types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfb6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bfb6-112">See Also</span></span>  
 [<span data-ttu-id="7bfb6-113">Se connecter à un système SAP à l’aide de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="7bfb6-113">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)
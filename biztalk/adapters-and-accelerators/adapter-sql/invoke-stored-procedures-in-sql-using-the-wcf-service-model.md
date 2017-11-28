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
# <a name="invoke-stored-procedures-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="140e8-102">Appeler les procédures stockées de SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="140e8-102">Invoke Stored Procedures in SQL using the WCF Service Model</span></span>
<span data-ttu-id="140e8-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte les procédures stockées en tant qu’opérations que les clients de l’adaptateur peuvent appeler sur le client WCF pour appeler la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="140e8-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers the stored procedures as operations that the adapter clients can invoke on the WCF client to invoke the stored procedure.</span></span> <span data-ttu-id="140e8-104">Selon la façon dont la procédure stockée retourne le jeu de résultats, l’adaptateur de classe toutes les procédures stockées en tant que :</span><span class="sxs-lookup"><span data-stu-id="140e8-104">Based on how the stored procedure returns the result set, the adapter categorizes all the stored procedures as:</span></span>  
  
-   <span data-ttu-id="140e8-105">**Procédures**.</span><span class="sxs-lookup"><span data-stu-id="140e8-105">**Procedures**.</span></span> <span data-ttu-id="140e8-106">Appel de procédures stockées à partir de la **procédures** nœud retourne un tableau du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="140e8-106">Invoking stored procedures from the **Procedures** node returns an array of DataSet.</span></span>  
  
-   <span data-ttu-id="140e8-107">**Fortement typée procédures**.</span><span class="sxs-lookup"><span data-stu-id="140e8-107">**Strongly-Typed Procedures**.</span></span> <span data-ttu-id="140e8-108">Appel de procédures stockées à partir de la **fortement typée procédures** nœud retourne un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="140e8-108">Invoking stored procedures from the **Strongly-Typed Procedures** node returns a strongly-typed result set.</span></span>  
  
 <span data-ttu-id="140e8-109">Notez que le même jeu de procédures stockées dans la base de données vous connecté seront répertoriés à la fois le **procédures** et **fortement typée procédures** nœud.</span><span class="sxs-lookup"><span data-stu-id="140e8-109">Note that the same set of stored procedures in the database you connected to will be listed both under the **Procedures** and **Strongly-Typed Procedures** node.</span></span> <span data-ttu-id="140e8-110">Selon le type de jeu de résultats, vous devez appeler la procédure stockée à partir du nœud approprié.</span><span class="sxs-lookup"><span data-stu-id="140e8-110">Based on the kind of result set you want, you must invoke the stored procedure from the relevant node.</span></span> <span data-ttu-id="140e8-111">Pour plus d’informations sur la façon dont [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge les procédures stockées, consultez [exécuter les procédures stockées de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="140e8-111">For more information about how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports stored procedures, see [Execute Stored Procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="140e8-112">Cette section fournit des instructions sur la façon d’appeler des procédures stockées à partir du **procédures** et **fortement typée procédures** nœud à l’aide d’un client WCF.</span><span class="sxs-lookup"><span data-stu-id="140e8-112">This section provides instructions on how to invoke stored procedures from both the **Procedures** and **Strongly-Typed Procedures** node by using a WCF client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="140e8-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="140e8-113">In This Section</span></span>  
  
-   [<span data-ttu-id="140e8-114">Involk faiblement typée de procédures stockées dans SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="140e8-114">Involk Weakly-typed Stored Procedures in SQL Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [<span data-ttu-id="140e8-115">Appeler fortement typée de procédure stockée dans SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="140e8-115">Invoke Strongly-typed Stored Procedure in SQL Using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="140e8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="140e8-116">See Also</span></span>  
[<span data-ttu-id="140e8-117">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="140e8-117">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
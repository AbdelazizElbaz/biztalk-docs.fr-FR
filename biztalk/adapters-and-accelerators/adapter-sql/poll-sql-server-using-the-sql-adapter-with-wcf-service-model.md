---
title: "Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20d0ab576e5feddb0b5f3e867ca549a45bb2af97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a><span data-ttu-id="afa67-102">Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="afa67-102">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>
<span data-ttu-id="afa67-103">Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages d’interrogation de données modifiées à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="afa67-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server.</span></span> <span data-ttu-id="afa67-104">Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="afa67-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="afa67-105">L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="afa67-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="afa67-106">Selon le type de message d’interrogation reçue, l’adaptateur expose des opérations d’interrogation différente :</span><span class="sxs-lookup"><span data-stu-id="afa67-106">Based on the type of polling message received, the adapter exposes different polling operations:</span></span>  
  
-   <span data-ttu-id="afa67-107">**L’interrogation**.</span><span class="sxs-lookup"><span data-stu-id="afa67-107">**Polling**.</span></span> <span data-ttu-id="afa67-108">Cette opération retourne un jeu de données en tant que partie du message d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="afa67-108">This operation returns a data set as part of the polling message.</span></span>  
  
-   <span data-ttu-id="afa67-109">**TypedPolling**.</span><span class="sxs-lookup"><span data-stu-id="afa67-109">**TypedPolling**.</span></span> <span data-ttu-id="afa67-110">Cette opération renvoie un message d’interrogation fortement typée.</span><span class="sxs-lookup"><span data-stu-id="afa67-110">This operation returns a strongly-typed polling message.</span></span>  
  
-   <span data-ttu-id="afa67-111">**XmlPolling**.</span><span class="sxs-lookup"><span data-stu-id="afa67-111">**XmlPolling**.</span></span> <span data-ttu-id="afa67-112">Cette opération renvoie le message d’interrogation en tant qu’un message XML.</span><span class="sxs-lookup"><span data-stu-id="afa67-112">This operation returns the polling message as an XML message.</span></span> <span data-ttu-id="afa67-113">Vous devez utiliser cette opération si vous souhaitez utiliser des instructions SELECT ou des procédures stockées qui utilisent la clause FOR XML pour retourner des données en tant que messages XML.</span><span class="sxs-lookup"><span data-stu-id="afa67-113">You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages.</span></span> <span data-ttu-id="afa67-114">[Clause FOR XML](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) fournit plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="afa67-114">[FOR XML clause](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) provides more info.</span></span> 
  
 <span data-ttu-id="afa67-115">Pour plus d’informations sur ces opérations d’interrogation, consultez [d’interrogation dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="afa67-115">For more information about these polling operations, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afa67-116">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients de carte avoir une application unique avec plusieurs d’interrogation ou TypedPolling des opérations pour la même base de données ou une table.</span><span class="sxs-lookup"><span data-stu-id="afa67-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single application with more than one Polling or TypedPolling operations for the same database or table.</span></span> <span data-ttu-id="afa67-117">Pour prendre en charge un tel scénario, l’adaptateur inclut un ID unique : **InboundID**: dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="afa67-117">To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI.</span></span> <span data-ttu-id="afa67-118">Cet ID, lors de l’ajout à la connexion URI, rend unique, ce qui permet à plusieurs opérations d’interrogation dans une application unique.</span><span class="sxs-lookup"><span data-stu-id="afa67-118">This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single application.</span></span>  
  
 <span data-ttu-id="afa67-119">Les rubriques de cette section fournissent des instructions sur l’utilisation des opérations d’interrogation et TypedPolling dans une application .NET.</span><span class="sxs-lookup"><span data-stu-id="afa67-119">The topics in this section provide instructions on how to use both Polling and TypedPolling operations in a .NET application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afa67-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="afa67-120">In This Section</span></span>  
  
-   [<span data-ttu-id="afa67-121">Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server en utilisant le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="afa67-121">Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [<span data-ttu-id="afa67-122">Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="afa67-122">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="afa67-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa67-123">See Also</span></span>  
[<span data-ttu-id="afa67-124">Développer des applications SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="afa67-124">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
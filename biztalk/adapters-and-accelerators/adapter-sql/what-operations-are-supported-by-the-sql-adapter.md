---
title: "Les opérations sont prises en charge par l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f4099-df19-48c4-a135-1ec264af3513
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59d413a763823f49b0bf905b42d8513cbbb1e745
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-sql-adapter"></a><span data-ttu-id="b82f8-102">Les opérations sont prises en charge par l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="b82f8-102">What operations are supported by the SQL adapter</span></span>
<span data-ttu-id="b82f8-103">Vous pouvez utiliser les clients de la carte pour effectuer des opérations sur la base de données SQL Server par :</span><span class="sxs-lookup"><span data-stu-id="b82f8-103">You can use the adapter clients to perform operations on the SQL Server database by:</span></span>  
  
-   <span data-ttu-id="b82f8-104">Création de projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="b82f8-104">Creating BizTalk projects</span></span>  
  
-   <span data-ttu-id="b82f8-105">À l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="b82f8-105">Using the WCF service model</span></span>  
  
-   <span data-ttu-id="b82f8-106">À l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="b82f8-106">Using the WCF channel model</span></span>  
  
 <span data-ttu-id="b82f8-107">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="b82f8-107">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="b82f8-108">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="b82f8-108">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="b82f8-109">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="b82f8-109">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="b82f8-110">Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="b82f8-110">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>  
  
 <span data-ttu-id="b82f8-111">Cette section fournit des informations sur les opérations prises en charge sur la base de données SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b82f8-111">This section provides information about the operations supported on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="b82f8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b82f8-112">See Also</span></span>  
 [<span data-ttu-id="b82f8-113">Vue d’ensemble de l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="b82f8-113">Overview of BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)
---
title: "Résoudre les problèmes de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1be376ba-ad4c-4fa7-b94b-82bfbc8f34cc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8b574a372ed365a22ff9d87d40bf4ab9af8ae4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-sql-adapter"></a><span data-ttu-id="3b19f-102">Résoudre les problèmes de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3b19f-102">Troubleshoot the SQL adapter</span></span>
<span data-ttu-id="3b19f-103">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] utilise ou dépend de plusieurs technologies Microsoft, y compris mais non limité à la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)], et [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b19f-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)], and [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="3b19f-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] repose sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], à son tour, ce qui nécessite le [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] ou [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b19f-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires the [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] or [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="3b19f-105">Les cartes peuvent être utilisés, soit en écrivant des applications à l’aide de la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou en créant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3b19f-105">The adapters can be consumed either by writing applications using the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="3b19f-106">Pour les problèmes liés à chacun de ces produits et technologies, consultez la documentation respective.</span><span class="sxs-lookup"><span data-stu-id="3b19f-106">For issues related to each of these technologies and products, see the respective documentation.</span></span>  
  
 <span data-ttu-id="3b19f-107">Cette section fournit des informations sur le dépannage de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], y compris :</span><span class="sxs-lookup"><span data-stu-id="3b19f-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="3b19f-108">L’activation du traçage diagnostiquer les problèmes avec les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="3b19f-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="3b19f-109">Gestion des problèmes d’installation et opérationnels que vous pouvez rencontrer lorsque vous travaillez avec les adaptateurs, y compris la cause probable et une résolution.</span><span class="sxs-lookup"><span data-stu-id="3b19f-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="3b19f-110">À l’aide des compteurs de performance pour mesurer les performances de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3b19f-110">Using performance counters to gauge adapter performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b19f-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3b19f-111">In This Section</span></span>  
  
-   [<span data-ttu-id="3b19f-112">Diagnostic de suivi et de journalisation des messages dans l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3b19f-112">Diagnostic Tracing and Message Logging in the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md)  
  
-   [<span data-ttu-id="3b19f-113">Résoudre les problèmes d’Installation avec l’adaptateur SQl</span><span class="sxs-lookup"><span data-stu-id="3b19f-113">Troubleshoot Installation Issues with the SQl adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-installation-issues-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="3b19f-114">Résoudre les problèmes opérationnels avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3b19f-114">Troubleshoot Operational Issues with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-operational-issues-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="3b19f-115">Utiliser des compteurs de Performance avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3b19f-115">Use Performance Counters with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)
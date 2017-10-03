---
title: "Dépanner l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: 2a3da42b-413b-479a-90d2-02f262abff41
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3cf2e8c5f9a3f0baa743f86eaf6527ed9847019
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-oracle-database-adapter"></a><span data-ttu-id="7ccd0-102">Dépanner l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-102">Troubleshoot the Oracle Database adapter</span></span>
<span data-ttu-id="7ccd0-103">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] utilise ou dépend de plusieurs technologies Microsoft, y compris mais non limité à la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]et Microsoft [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ccd0-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and the Microsoft [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="7ccd0-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] repose sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], à son tour, ce qui nécessite le [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ccd0-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires the [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="7ccd0-105">Les cartes peuvent être utilisés, soit en écrivant des applications à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou en créant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-105">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="7ccd0-106">Pour les problèmes liés à chacun de ces produits et technologies, consultez la documentation respective.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-106">For issues related to each of these technologies and products, see the respective documentation.</span></span>  
  
 <span data-ttu-id="7ccd0-107">Cette section fournit des informations sur le dépannage de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], y compris :</span><span class="sxs-lookup"><span data-stu-id="7ccd0-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="7ccd0-108">L’activation du traçage diagnostiquer les problèmes avec les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="7ccd0-109">Gestion des problèmes d’installation et opérationnels que vous pouvez rencontrer lorsque vous travaillez avec les adaptateurs, y compris la cause probable et une résolution.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="7ccd0-110">À l’aide des compteurs de performance pour mesurer les performances de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-110">Using performance counters to gauge adapter performance.</span></span>  
  
-   <span data-ttu-id="7ccd0-111">Gestion des exceptions et erreurs, y compris la cause probable et une résolution.</span><span class="sxs-lookup"><span data-stu-id="7ccd0-111">Handling exceptions and errors, including probable cause, and a resolution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ccd0-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7ccd0-112">In This Section</span></span>  
  
-   [<span data-ttu-id="7ccd0-113">Le suivi de diagnostic et de journalisation des messages pour l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-113">Diagnostic tracing and message logging for the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md)
  
-   [<span data-ttu-id="7ccd0-114">Résoudre les problèmes d’installation de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-114">Troubleshoot installation issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)
  
-   [<span data-ttu-id="7ccd0-115">Résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-115">Troubleshoot operational issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)
  
-   [<span data-ttu-id="7ccd0-116">Résoudre les problèmes de performances de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-116">Troubleshoot performance issues with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-performance-issues-with-the-oracle-database-adapter.md)
  
-   [<span data-ttu-id="7ccd0-117">Utiliser des compteurs de performance avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-117">Use performance counters with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/use-performance-counters-with-the-oracle-database-adapter.md)
  
-   [<span data-ttu-id="7ccd0-118">Exceptions et gestion des erreurs avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="7ccd0-118">Exceptions and error handling with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)
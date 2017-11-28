---
title: "Dépanner l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: de11ffe3-3622-40df-b9c5-11c96f8460e0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e12b877eaabb629bb9e9e1da81cf5343e1780cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-siebel-adapter"></a><span data-ttu-id="e5818-102">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-102">Troubleshoot the Siebel adapter</span></span>
<span data-ttu-id="e5818-103">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] utilise ou dépend de plusieurs technologies Microsoft, y compris mais non limité à [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]et Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] / [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5818-103">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several different Microsoft technologies including but not limited to [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and the Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]/[!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="e5818-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] repose sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], qui à son tour nécessite [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] et [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5818-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which in turn requires [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] and [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)].</span></span> <span data-ttu-id="e5818-105">Les cartes peuvent être utilisés, soit en écrivant des applications à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou en créant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e5818-105">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> <span data-ttu-id="e5818-106">Pour les problèmes liés à chacun de ces produits et technologies, reportez-vous à la documentation respective.</span><span class="sxs-lookup"><span data-stu-id="e5818-106">For issues related to each of these technologies and products, refer to the respective documentation.</span></span>  
  
 <span data-ttu-id="e5818-107">Cette section fournit des informations sur le dépannage de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], y compris :</span><span class="sxs-lookup"><span data-stu-id="e5818-107">This section provides information about troubleshooting the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], including:</span></span>  
  
-   <span data-ttu-id="e5818-108">L’activation du traçage diagnostiquer les problèmes avec les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="e5818-108">Enabling tracing to diagnose issues with the adapters.</span></span>  
  
-   <span data-ttu-id="e5818-109">Gestion des problèmes d’installation et opérationnels que vous pouvez rencontrer lorsque vous travaillez avec les adaptateurs, y compris la cause probable et une résolution.</span><span class="sxs-lookup"><span data-stu-id="e5818-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause, and a resolution.</span></span>  
  
-   <span data-ttu-id="e5818-110">À l’aide des compteurs de performance pour mesurer les performances de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e5818-110">Using performance counters to gauge adapter performance.</span></span>  
  
-   <span data-ttu-id="e5818-111">Gestion des exceptions et erreurs, y compris la cause probable et une résolution.</span><span class="sxs-lookup"><span data-stu-id="e5818-111">Handling exceptions and errors, including probable cause, and a resolution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5818-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e5818-112">In This Section</span></span>  
  
-   [<span data-ttu-id="e5818-113">Le suivi de diagnostic et de journalisation des messages pour l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-113">Diagnostic Tracing and Message Logging for the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/diagnostic-tracing-and-message-logging-for-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="e5818-114">Résoudre les problèmes d’Installation avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-114">Troubleshoot Installation Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-installation-issues-with-the-siebel-adapter.md) 
  
-   [<span data-ttu-id="e5818-115">Résoudre les problèmes opérationnels avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-115">Troubleshoot Operational Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-operational-issues-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="e5818-116">Résoudre les problèmes de performances de l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-116">Troubleshoot Performance Issues with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-performance-issues-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="e5818-117">Résoudre les problèmes avec le fournisseur de données pour Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-117">Troubleshoot Issues with the Data Provider for Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-issues-with-the-data-provider-for-siebel.md) 
  
-   [<span data-ttu-id="e5818-118">Utiliser des compteurs de Performance avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-118">Use Performance Counters with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md)  
  
-   [<span data-ttu-id="e5818-119">Exceptions et gestion des erreurs avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5818-119">Exceptions and Error Handling with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)
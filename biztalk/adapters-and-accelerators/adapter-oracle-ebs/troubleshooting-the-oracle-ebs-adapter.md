---
title: "Dépannage de l’adaptateur Oracle eBusiness Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78d5335-b860-47d9-9f3a-7f74d628d8ff
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7b36316612bda541d9bf608f7da22c399ade045
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-oracle-ebs-adapter"></a><span data-ttu-id="7c7fb-102">Dépannage de l’adaptateur Oracle eBusiness Suite</span><span class="sxs-lookup"><span data-stu-id="7c7fb-102">Troubleshooting the Oracle EBS adapter</span></span>
## <a name="overview"></a><span data-ttu-id="7c7fb-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="7c7fb-103">Overview</span></span>
<span data-ttu-id="7c7fb-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] utilise ou dépend de plusieurs technologies Microsoft, y compris mais non limité à la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], et [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c7fb-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] uses or depends on several Microsoft technologies, including but not limited to the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="7c7fb-105">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] repose sur le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], qui utilise également le [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c7fb-105">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], which also uses the [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)].</span></span> <span data-ttu-id="7c7fb-106">Les cartes peuvent être utilisés, soit en écrivant des applications à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou en créant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7c7fb-106">The adapters can be consumed either by writing applications using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or by creating BizTalk applications.</span></span> 
  
 <span data-ttu-id="7c7fb-107">Cette section fournit des informations sur la résolution des problèmes, notamment :</span><span class="sxs-lookup"><span data-stu-id="7c7fb-107">This section provides information about troubleshooting, including:</span></span>  
  
-   <span data-ttu-id="7c7fb-108">L’activation du traçage diagnostiquer les problèmes avec les adaptateurs</span><span class="sxs-lookup"><span data-stu-id="7c7fb-108">Enabling tracing to diagnose issues with the adapters</span></span>
  
-   <span data-ttu-id="7c7fb-109">La gestion des problèmes d’installation et opérationnels que vous pouvez rencontrer lorsque vous travaillez avec les adaptateurs, y compris la cause probable et une résolution</span><span class="sxs-lookup"><span data-stu-id="7c7fb-109">Handling installation and operational issues that you might encounter when working with the adapters, including probable cause and a resolution</span></span>
  
-   <span data-ttu-id="7c7fb-110">À l’aide des compteurs de performances pour passer en revue les performances de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="7c7fb-110">Using performance counters to review adapter performance</span></span>
  
-   <span data-ttu-id="7c7fb-111">Gestion des exceptions et erreurs, y compris la cause probable et une résolution</span><span class="sxs-lookup"><span data-stu-id="7c7fb-111">Handling exceptions and errors, including probable cause, and a resolution</span></span>
  
## <a name="lets-get-started"></a><span data-ttu-id="7c7fb-112">C’est parti</span><span class="sxs-lookup"><span data-stu-id="7c7fb-112">Let's get started</span></span>  
  
-   [<span data-ttu-id="7c7fb-113">Diagnostic de suivi et de journalisation des messages dans l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c7fb-113">Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md) 
  
-   [<span data-ttu-id="7c7fb-114">Résoudre les problèmes d’Installation avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c7fb-114">Troubleshoot Installation Issues with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshoot-installation-issues-with-the-oracle-e-business-suite-adapter.md)  
  
-   [<span data-ttu-id="7c7fb-115">Résoudre les problèmes opérationnels avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c7fb-115">Troubleshoot Operational Issues with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshoot-operational-issues-with-the-oracle-e-business-suite-adapter.md)
  
-   [<span data-ttu-id="7c7fb-116">Utiliser des compteurs de Performance avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c7fb-116">Use Performance Counters with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/use-performance-counters-with-the-oracle-e-business-suite-adapter.md)
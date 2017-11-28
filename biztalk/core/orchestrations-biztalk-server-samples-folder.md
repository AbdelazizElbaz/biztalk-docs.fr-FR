---
title: "Orchestrations (dossier d’exemples BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- SDK examples
ms.assetid: f70f8d67-763f-4e3c-b233-c7156026b514
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a018f52985e54f72749903aef58f40236d0618
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrations-biztalk-server-samples-folder"></a><span data-ttu-id="71b20-102">Orchestrations (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="71b20-102">Orchestrations (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="71b20-103">Le Kit de développement logiciel (SDK) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut plusieurs exemples d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="71b20-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several orchestration samples in its software development kit (SDK).</span></span> <span data-ttu-id="71b20-104">Cette section fournit des informations détaillées sur les fonctionnalités utilisées dans les exemples d'orchestration, des instructions sur la création et l'exécution des exemples et les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="71b20-104">This section provides detailed information about the functionality demonstrated by these orchestration samples, instructions for building and running the samples, and the results you can expect.</span></span> <span data-ttu-id="71b20-105">Les exemples ci-dessous sont triés par complexité, HelloWorld étant l'exemple le plus basique dans la liste.</span><span class="sxs-lookup"><span data-stu-id="71b20-105">The samples listed below are sorted by complexity, that is, HelloWorld is the most basic sample in the list.</span></span> <span data-ttu-id="71b20-106">Les exemples plus bas dans la liste peuvent être basés sur des fonctionnalités illustrées dans d'autres exemples situés plus haut dans la liste.</span><span class="sxs-lookup"><span data-stu-id="71b20-106">Samples later in the list might be based upon functionalities shown in samples earlier in the list.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71b20-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="71b20-107">In This Section</span></span>  
  
-   <span data-ttu-id="71b20-108">[HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-108">[HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-109">Montre comment traiter les messages XML dans les types de messages XML liés mais distincts, à l’aide des orchestrations BizTalk et est mappé.</span><span class="sxs-lookup"><span data-stu-id="71b20-109">Demonstrates how to process XML messages into related, but distinct, types of XML messages by using BizTalk orchestrations and maps.</span></span>  
  
-   <span data-ttu-id="71b20-110">[MethodCall (exemple BizTalk Server)](../core/methodcall-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-110">[MethodCall (BizTalk Server Sample)](../core/methodcall-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-111">Montre comment appeler un. Méthode NET à partir d’une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="71b20-111">Demonstrates how to call a .NET-based method from a BizTalk orchestration.</span></span>  
  
-   <span data-ttu-id="71b20-112">[CallOrchestration (exemple BizTalk Server)](../core/callorchestration-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-112">[CallOrchestration (BizTalk Server Sample)](../core/callorchestration-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-113">Montre comment appeler une orchestration BizTalk à partir d’une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="71b20-113">Demonstrates how to call a BizTalk orchestration from another orchestration.</span></span>  
  
-   <span data-ttu-id="71b20-114">[Compensation (exemple BizTalk Server)](../core/compensation-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-114">[Compensation (BizTalk Server Sample)](../core/compensation-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-115">Montre comment utiliser le **compenser** forme dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="71b20-115">Demonstrates how to use the **Compensate** shape in an orchestration.</span></span>  
  
-   <span data-ttu-id="71b20-116">[PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-116">[PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-117">Montre comment utiliser des orchestrations BizTalk avec la résolution de tiers pour router les messages d’instance.</span><span class="sxs-lookup"><span data-stu-id="71b20-117">Demonstrates how to use BizTalk orchestrations with party resolution to route instance messages.</span></span>  
  
-   <span data-ttu-id="71b20-118">[L’importation BPEL (exemple BizTalk Server)](../core/bpel-import-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="71b20-118">[BPEL Import (BizTalk Server Sample)](../core/bpel-import-biztalk-server-sample.md).</span></span> <span data-ttu-id="71b20-119">Montre comment créer une orchestration à partir d’une description de l’exécution du langage BPEL (Business Process) d’un processus et des artefacts associés.</span><span class="sxs-lookup"><span data-stu-id="71b20-119">Demonstrates how to create an orchestration from a Business Process Execution Language (BPEL) description of a process and related artifacts.</span></span>
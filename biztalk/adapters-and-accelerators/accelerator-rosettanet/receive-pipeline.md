---
title: "Pipeline de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd8f03aa-f5c3-49e7-946b-c8c91fe3abc7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7461ce357b3fa9cb6216dfce6381876100bb4287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-pipeline"></a><span data-ttu-id="6c6a9-102">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="6c6a9-102">Receive Pipeline</span></span>
<span data-ttu-id="6c6a9-103">Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pipeline que vous pouvez personnaliser pour votre application de réception.</span><span class="sxs-lookup"><span data-stu-id="6c6a9-103">This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive pipeline that you can customize for your application.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6c6a9-104">Montre</span><span class="sxs-lookup"><span data-stu-id="6c6a9-104">Demonstrates</span></span>  
 <span data-ttu-id="6c6a9-105">Cet exemple montre comment traiter un message RNIF entrant en message XML équivalent à l'aide du pipeline de réception BTARN (PipelineReceive.btp).</span><span class="sxs-lookup"><span data-stu-id="6c6a9-105">This sample demonstrates how to process an incoming RNIF message into the equivalent XML message using the BTARN receive pipeline (PipelineReceive.btp).</span></span> <span data-ttu-id="6c6a9-106">PipelineReceive.btp se trouve dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\RNPipelines.</span><span class="sxs-lookup"><span data-stu-id="6c6a9-106">PipelineReceive.btp is located in *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="6c6a9-107">Il comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c6a9-107">It includes the following stages:</span></span>  
  
-   <span data-ttu-id="6c6a9-108">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="6c6a9-108">ReceiveMessageNonRepudiate</span></span>  
  
-   <span data-ttu-id="6c6a9-109">RNMimeDecoder (préprocesseur/décodeur MIME)</span><span class="sxs-lookup"><span data-stu-id="6c6a9-109">RNMimeDecoder (MIME Preprocessor/Decoder)</span></span>  
  
-   <span data-ttu-id="6c6a9-110">RNDAsm (désassembleur XML)</span><span class="sxs-lookup"><span data-stu-id="6c6a9-110">RNDAsm (XML Disassembler)</span></span>  
  
-   <span data-ttu-id="6c6a9-111">RNPartyRes (composant Résolution du tiers)</span><span class="sxs-lookup"><span data-stu-id="6c6a9-111">RNPartyRes (Party Resolution component)</span></span>  
  
-   <span data-ttu-id="6c6a9-112">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="6c6a9-112">MessageUpdater</span></span>  
  
 <span data-ttu-id="6c6a9-113">Pour plus d’informations sur les composants de ce pipeline et le flux de messages dans ce pipeline, consultez [le Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="6c6a9-113">For more information about the components of this pipeline, and the message flow in this pipeline, see [BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6a9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c6a9-114">See Also</span></span>  
 <span data-ttu-id="6c6a9-115">[Exemples de pipeline](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span><span class="sxs-lookup"><span data-stu-id="6c6a9-115">[Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span></span>  
 [<span data-ttu-id="6c6a9-116">Pipeline de réception BTARN</span><span class="sxs-lookup"><span data-stu-id="6c6a9-116">BTARN Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)
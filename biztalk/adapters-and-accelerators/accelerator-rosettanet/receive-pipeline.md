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
ms.openlocfilehash: 3d5374c46411e0c4924585647736bfde7f1e4428
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-pipeline"></a>Pipeline de réception
Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pipeline que vous pouvez personnaliser pour votre application de réception.  
  
## <a name="demonstrates"></a>Montre  
 Cet exemple montre comment traiter un message RNIF entrant en message XML équivalent à l'aide du pipeline de réception BTARN (PipelineReceive.btp). PipelineReceive.btp se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. Il comprend les étapes suivantes :  
  
-   ReceiveMessageNonRepudiate  
  
-   RNMimeDecoder (préprocesseur/décodeur MIME)  
  
-   RNDAsm (désassembleur XML)  
  
-   RNPartyRes (composant Résolution du tiers)  
  
-   MessageUpdater  
  
 Pour plus d’informations sur les composants de ce pipeline et le flux de messages dans ce pipeline, consultez [le Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de pipeline](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)
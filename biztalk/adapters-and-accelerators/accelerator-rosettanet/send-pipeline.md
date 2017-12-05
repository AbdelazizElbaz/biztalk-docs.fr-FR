---
title: "Pipeline d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58ca6a63-525a-4b16-932d-6d26e68f6fab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b7ee5ad712466df79a4e6961062ea56b73ad248
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="send-pipeline"></a>Pipeline d'envoi
Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pipeline d’envoi que vous pouvez personnaliser pour votre application.  
  
## <a name="demonstrates"></a>Montre  
 Cet exemple montre comment traiter un message XML sortant dans le message RNIF équivalent via le pipeline d’envoi BTARN (PipelineSend.btp). PipelineSend.btp se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. Il comprend les étapes suivantes :  
  
-   Assembleur XML  
  
-   Encodeur MIME  
  
-   Envoyer le message désolidariser par Non  
  
> [!NOTE]
>  Si vous sélectionnez un des composants ci-dessus de la BTARN pipeline d’envoi dans le Concepteur de Pipeline dans Visual Studio, les propriétés de ce composant seront affichera pas dans le volet Propriétés. Pour afficher les propriétés du composant, vous devez ajouter le composant à la boîte à outils à l’aide de la **choisir des éléments de boîte à outils** commande dans le menu Outils ; supprimer le composant existant dans le pipeline d’envoi ; puis ajoutez le composant à partir du Boîte à outils vers l’étape appropriée dans le Concepteur de Pipeline. Si vous sélectionnez ensuite le composant, ses propriétés seront affichera dans le volet Propriétés.  
  
 Pour plus d’informations sur les composants de ce pipeline et le flux de messages dans ce pipeline, consultez [le Pipeline d’envoi BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de pipeline](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md)   
 [Pipeline d’envoi BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)
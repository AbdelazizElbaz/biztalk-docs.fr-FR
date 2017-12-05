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
# <a name="send-pipeline"></a><span data-ttu-id="c2314-102">Pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="c2314-102">Send Pipeline</span></span>
<span data-ttu-id="c2314-103">Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pipeline d’envoi que vous pouvez personnaliser pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c2314-103">This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] send pipeline that you can customize for your application.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c2314-104">Montre</span><span class="sxs-lookup"><span data-stu-id="c2314-104">Demonstrates</span></span>  
 <span data-ttu-id="c2314-105">Cet exemple montre comment traiter un message XML sortant dans le message RNIF équivalent via le pipeline d’envoi BTARN (PipelineSend.btp).</span><span class="sxs-lookup"><span data-stu-id="c2314-105">This sample demonstrates how to process an outgoing XML message into the equivalent RNIF message using the BTARN send pipeline (PipelineSend.btp).</span></span> <span data-ttu-id="c2314-106">PipelineSend.btp se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span><span class="sxs-lookup"><span data-stu-id="c2314-106">PipelineSend.btp is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="c2314-107">Il comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2314-107">It includes the following stages:</span></span>  
  
-   <span data-ttu-id="c2314-108">Assembleur XML</span><span class="sxs-lookup"><span data-stu-id="c2314-108">XML Assembler</span></span>  
  
-   <span data-ttu-id="c2314-109">Encodeur MIME</span><span class="sxs-lookup"><span data-stu-id="c2314-109">MIME Encoder</span></span>  
  
-   <span data-ttu-id="c2314-110">Envoyer le message désolidariser par Non</span><span class="sxs-lookup"><span data-stu-id="c2314-110">Send message Non-repudiate</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2314-111">Si vous sélectionnez un des composants ci-dessus de la BTARN pipeline d’envoi dans le Concepteur de Pipeline dans Visual Studio, les propriétés de ce composant seront affichera pas dans le volet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="c2314-111">If you select one of the above components of the BTARN send pipeline in the Pipeline Designer in Visual Studio, the properties for that component will not be displayed in the Properties pane.</span></span> <span data-ttu-id="c2314-112">Pour afficher les propriétés du composant, vous devez ajouter le composant à la boîte à outils à l’aide de la **choisir des éléments de boîte à outils** commande dans le menu Outils ; supprimer le composant existant dans le pipeline d’envoi ; puis ajoutez le composant à partir du Boîte à outils vers l’étape appropriée dans le Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="c2314-112">To display the properties of the component, you must add the component to the Toolbox by using the **Choose Toolbox Items** command in the Tools menu; delete the existing component from the send pipeline; and then add the component from the Toolbox into the appropriate stage in the Pipeline Designer.</span></span> <span data-ttu-id="c2314-113">Si vous sélectionnez ensuite le composant, ses propriétés seront affichera dans le volet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="c2314-113">If you then select the component, its properties will be displayed in the Properties pane.</span></span>  
  
 <span data-ttu-id="c2314-114">Pour plus d’informations sur les composants de ce pipeline et le flux de messages dans ce pipeline, consultez [le Pipeline d’envoi BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="c2314-114">For more information about the components of this pipeline, and the message flow within this pipeline, see [BTARN Send Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2314-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2314-115">See Also</span></span>  
 <span data-ttu-id="c2314-116">[Exemples de pipeline](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span><span class="sxs-lookup"><span data-stu-id="c2314-116">[Pipeline Samples](../../adapters-and-accelerators/accelerator-rosettanet/pipeline-samples.md) </span></span>  
 [<span data-ttu-id="c2314-117">Pipeline d’envoi BTARN</span><span class="sxs-lookup"><span data-stu-id="c2314-117">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)
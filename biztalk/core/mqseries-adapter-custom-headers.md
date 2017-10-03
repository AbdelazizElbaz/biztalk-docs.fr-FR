---
title: "En-têtes personnalisés de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, custom headers
ms.assetid: b0e18203-a33f-4d50-8483-396699cdff23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09a05b8c73cd7be84af01eb4465681816e429bc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-custom-headers"></a><span data-ttu-id="39c23-102">En-têtes personnalisés de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="39c23-102">MQSeries Adapter Custom Headers</span></span>
<span data-ttu-id="39c23-103">Compte tenu des structures d'en-tête utilisées dans les messages MQSeries, vous devez gérer les en-têtes personnalisés que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="39c23-103">Because of the header structures used in MQSeries messages, you must manage any custom headers you want to use.</span></span> <span data-ttu-id="39c23-104">Les en-têtes personnalisés doivent faire partie du corps d'un message pour éviter toute interférence avec le traitement des en-têtes MQSeries.</span><span class="sxs-lookup"><span data-stu-id="39c23-104">Custom headers must be part of the message body to avoid interfering with the processing of the MQSeries headers.</span></span> <span data-ttu-id="39c23-105">Veillez à ne pas rétrograder une propriété promue automatiquement.</span><span class="sxs-lookup"><span data-stu-id="39c23-105">Make sure that you avoid demoting any one of the automatically promoted properties.</span></span> <span data-ttu-id="39c23-106">Pour plus d’informations sur les propriétés promues automatiquement, consultez [propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md).</span><span class="sxs-lookup"><span data-stu-id="39c23-106">For more information about automatically promoted properties, see [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md).</span></span>  
  
 <span data-ttu-id="39c23-107">L'incorporation d'en-têtes personnalisés dans le corps du message nécessite un traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="39c23-107">In turn, the incorporation of custom headers in the message body requires additional processing.</span></span> <span data-ttu-id="39c23-108">Une solution consiste à traiter les en-têtes personnalisés dans les pipelines de l'application.</span><span class="sxs-lookup"><span data-stu-id="39c23-108">One solution is to handle the custom headers in the pipelines of the application.</span></span> <span data-ttu-id="39c23-109">Le pipeline de réception extraie les informations de l'en-tête personnalisé et promeut les informations en tant que propriétés de contexte.</span><span class="sxs-lookup"><span data-stu-id="39c23-109">A receive pipeline extracts the custom header information and promotes the information as context properties.</span></span> <span data-ttu-id="39c23-110">De la même manière, le pipeline d'envoi récupère les propriétés de contexte correspondant à l'en-tête personnalisé et rétrograde les propriétés dans le corps du message.</span><span class="sxs-lookup"><span data-stu-id="39c23-110">Similarly, the send pipeline takes the context properties corresponding to the custom header and demotes the properties in the body of the message.</span></span>  
  
 <span data-ttu-id="39c23-111">Pour obtenir un exemple d’utilisation des en-têtes personnalisés dans un composant de pipeline, consultez [MQSSendPipelineComponent (exemple BizTalk Server)](../core/mqssendpipelinecomponent-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39c23-111">For an example of using custom headers in a pipeline component, see [MQSSendPipelineComponent (BizTalk Server Sample)](../core/mqssendpipelinecomponent-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c23-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39c23-112">See Also</span></span>  
 [<span data-ttu-id="39c23-113">Propriétés de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="39c23-113">MQSeries Adapter Properties</span></span>](../core/mqseries-adapter-properties.md)
---
title: "Propriétés de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQXQH_MsgDesc_ReplyToQMgr property [MQSeries adapters]
- UserHttpHeaders property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQXQH_MsgDesc_MsgId property [MQSeries adapters]
- MQXQH_MsgDesc_ReplyToQ property [MQSeries adapters]
- SubmissionHandle property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- EnableChunkedEncoding property [MQSeries adapters]
- MQSeries adapters, properties
- MQXQH_MsgDesc_CorrelId property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: c3cfbc8c-4c9b-431e-b0b6-4c065a69ce6b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fae8cc1ed67f077b6ae12945da10c58cf0f147da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-properties"></a><span data-ttu-id="c994a-102">Propriétés de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="c994a-102">MQSeries Adapter Properties</span></span>
<span data-ttu-id="c994a-103">Pour accéder aux propriétés d'en-tête MQSeries depuis une orchestration BizTalk, vous devez ajouter une référence à l'assembly MQSeries.dll dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="c994a-103">To access MQSeries header properties from a BizTalk orchestration, you must add a reference to the MQSeries.dll assembly to your project.</span></span> <span data-ttu-id="c994a-104">Cet assembly est situé à l'emplacement d'installation de l'adaptateur MQSeries (par exemple, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="c994a-104">This assembly is located where you installed the MQSeries adapter, for example, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="c994a-105">Une fois le schéma de propriété MQSeries référencé, les propriétés de contexte supplémentaires sont disponibles pour les divers outils de développement BizTalk Server (par exemple, le **assignation du Message** forme dans le Concepteur d’Orchestration).</span><span class="sxs-lookup"><span data-stu-id="c994a-105">After you reference the MQSeries property schema, additional context properties are available to various BizTalk Server development tools (for example, the **Message Assignment** shape in Orchestration Designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c994a-106">Veillez à suivre les instructions de la documentation IBM WebSphere MQ lorsque vous utilisez les propriétés d'en-tête MQSeries.</span><span class="sxs-lookup"><span data-stu-id="c994a-106">Make sure that you follow the guidelines in the IBM WebSphere MQ documentation when you work with MQSeries header properties.</span></span>  
  
 <span data-ttu-id="c994a-107">L'adaptateur promeut automatiquement certaines propriétés MQSeries.</span><span class="sxs-lookup"><span data-stu-id="c994a-107">The adapter automatically promotes some MQSeries properties.</span></span> <span data-ttu-id="c994a-108">Vos applications et composants personnalisés doivent éviter de rétrograder ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="c994a-108">Your applications and custom components must avoid demoting these properties.</span></span> <span data-ttu-id="c994a-109">Vous pouvez promouvoir d'autres propriétés à l'aide de composants de pipeline personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c994a-109">You can promote additional properties by using custom pipeline components.</span></span> <span data-ttu-id="c994a-110">Les propriétés suivantes sont promues automatiquement :</span><span class="sxs-lookup"><span data-stu-id="c994a-110">The automatically promoted properties are as follows:</span></span>  
  
-   <span data-ttu-id="c994a-111">**BizTalk_CorrelationID**</span><span class="sxs-lookup"><span data-stu-id="c994a-111">**BizTalk_CorrelationID**</span></span>  
  
-   <span data-ttu-id="c994a-112">**MQMD_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="c994a-112">**MQMD_CorrelId**</span></span>  
  
-   <span data-ttu-id="c994a-113">**MQMD_MsgId**</span><span class="sxs-lookup"><span data-stu-id="c994a-113">**MQMD_MsgId**</span></span>  
  
-   <span data-ttu-id="c994a-114">**MQMD_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="c994a-114">**MQMD_ReplyToQ**</span></span>  
  
-   <span data-ttu-id="c994a-115">**MQMD_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="c994a-115">**MQMD_ReplyToQMgr**</span></span>  
  
-   <span data-ttu-id="c994a-116">**MQXQH_RemoteQMgrName**</span><span class="sxs-lookup"><span data-stu-id="c994a-116">**MQXQH_RemoteQMgrName**</span></span>  
  
-   <span data-ttu-id="c994a-117">**MQXQH_RemoteQName**</span><span class="sxs-lookup"><span data-stu-id="c994a-117">**MQXQH_RemoteQName**</span></span>  
  
-   <span data-ttu-id="c994a-118">**MQXQH_MsgDesc_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="c994a-118">**MQXQH_MsgDesc_CorrelId**</span></span>  
  
-   <span data-ttu-id="c994a-119">**MQXQH_MsgDesc_MsgId**</span><span class="sxs-lookup"><span data-stu-id="c994a-119">**MQXQH_MsgDesc_MsgId**</span></span>  
  
-   <span data-ttu-id="c994a-120">**MQXQH_MsgDesc_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="c994a-120">**MQXQH_MsgDesc_ReplyToQ**</span></span>  
  
-   <span data-ttu-id="c994a-121">**MQXQH_MsgDesc_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="c994a-121">**MQXQH_MsgDesc_ReplyToQMgr**</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c994a-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c994a-122">In This Section</span></span>  
  
-   [<span data-ttu-id="c994a-123">Conversion de Type de données de propriétés</span><span class="sxs-lookup"><span data-stu-id="c994a-123">Data Type Conversion of Properties</span></span>](../core/data-type-conversion-of-properties.md)  
  
-   [<span data-ttu-id="c994a-124">Propriétés relatives à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c994a-124">Properties Related to BizTalk Server</span></span>](../core/properties-related-to-biztalk-server.md)  
  
-   [<span data-ttu-id="c994a-125">Propriétés de contexte MQSeries</span><span class="sxs-lookup"><span data-stu-id="c994a-125">MQSeries Context Properties</span></span>](../core/mqseries-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="c994a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c994a-126">See Also</span></span>  
 [<span data-ttu-id="c994a-127">Configuration de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="c994a-127">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)
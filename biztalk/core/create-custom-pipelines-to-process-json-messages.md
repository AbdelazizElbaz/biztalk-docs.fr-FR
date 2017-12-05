---
title: "Créer des pipelines personnalisés pour traiter les messages JSON | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b04faad1-b14b-4146-82c7-88a38d2a46a5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4c329bce3ee8f9e2e4faf11a60e5e38a82ff467
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="create-custom-pipelines-to-process-json-messages"></a><span data-ttu-id="41086-102">Créer des pipelines personnalisés pour traiter les messages JSON</span><span class="sxs-lookup"><span data-stu-id="41086-102">Create custom pipelines to process JSON messages</span></span>
> [!NOTE]
>  <span data-ttu-id="41086-103">Ce didacticiel s’applique uniquement à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="41086-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="41086-104"> fournit des composants de pipeline pouvant être utilisés pour traiter les messages JSON dans une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41086-104"> provides pipeline components that can be used to process JSON messages within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="41086-105">Dans cette étape, nous utilisons ces composants de pipeline pour créer des pipelines personnalisés pouvant être utilisés lors de la configuration d'une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41086-105">In this step, we use those pipeline components to create custom pipelines that can be used when configuring a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="41086-106">Créer un pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="41086-106">Create a custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="41086-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, à partir de l’Explorateur de solutions, cliquez sur le projet, puis pointez sur **ajouter** > **un nouvel élément** > **Pipeline de réception**.</span><span class="sxs-lookup"><span data-stu-id="41086-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Receive Pipeline**.</span></span> <span data-ttu-id="41086-108">Indiquez le nom du pipeline en tant que `JSONToXmlReceivePipeline.btp`, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="41086-108">Provide the pipeline name as `JSONToXmlReceivePipeline.btp`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="41086-109">Dans le **Decode** étape Ajouter les nouveaux **décodeur JSON**.</span><span class="sxs-lookup"><span data-stu-id="41086-109">Within the **Decode** stage add the new **JSON decoder**.</span></span> <span data-ttu-id="41086-110">Dans les autres étapes et autres composants de pipeline, comme indiqué dans la capture d'écran, enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="41086-110">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
     <span data-ttu-id="41086-111">![Pipeline de réception personnalisé](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span><span class="sxs-lookup"><span data-stu-id="41086-111">![Custom receive pipeline](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span></span>  
  
## <a name="create-a-custom-send-pipeline"></a><span data-ttu-id="41086-112">Création d'un pipeline d'envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="41086-112">Create a custom send pipeline</span></span>  
  
1.  <span data-ttu-id="41086-113">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, à partir de l’Explorateur de solutions, cliquez sur le projet, puis pointez sur **ajouter** > **un nouvel élément** > **le Pipeline d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="41086-113">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Send Pipeline**.</span></span> <span data-ttu-id="41086-114">Indiquez le nom du pipeline en tant que `XmlToJSONSendPipeline.btp`, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="41086-114">Provide the pipeline name as `XmlToJSONSendPipeline.btp`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="41086-115">Dans le **Encode** étape Ajouter les nouveaux **encodeur JSON**.</span><span class="sxs-lookup"><span data-stu-id="41086-115">Within the **Encode** stage add the new **JSON encoder**.</span></span> <span data-ttu-id="41086-116">Dans les autres étapes et autres composants de pipeline, comme indiqué dans la capture d'écran, enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="41086-116">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
     <span data-ttu-id="41086-117">![Pipeline d’envoi personnalisé](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span><span class="sxs-lookup"><span data-stu-id="41086-117">![Custom send pipeline](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41086-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41086-118">See Also</span></span>  
 [<span data-ttu-id="41086-119">Traitement des messages JSON à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="41086-119">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)
---
title: "Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario (Pull) avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55eec1f3-b920-48f8-946a-9ad7afa36fd6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b289d8478eb020067d9231fb1d4f135c7b43b289
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-bind-the-orchestration-with-dynamic-send-port-for-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="38f08-102">Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant</span><span class="sxs-lookup"><span data-stu-id="38f08-102">Step 3B: Bind the orchestration with dynamic send port for InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="38f08-103">Avant de commencer cette étape, vous devez effectuer [étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario (Pull) avant](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-interact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="38f08-103">Before you begin this step, you must complete [Step 3A: Create an orchestration for dynamic send port for InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-interact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="38f08-104">Pour ajouter un emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="38f08-104">To add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="38f08-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="38f08-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="38f08-106">Dans la Console Administration de BizTalk Server, dans le volet gauche, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis Cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="38f08-106">In the BizTalk Server Administration Console, in the left pane, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="38f08-107">Vérifiez que l’état de la **BizTalkServerApplication** héberger l’instance et l’instance d’hôte interagir est **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="38f08-107">Verify that the status for the **BizTalkServerApplication** host instance and Interact host instance is **running**.</span></span> <span data-ttu-id="38f08-108">Dans le cas contraire, cliquez sur les instances d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="38f08-108">If not, right-click the host instances, and click **Start**.</span></span>  
  
3.  <span data-ttu-id="38f08-109">Dans le volet gauche, développez des Applications, puis BizTalk Application 1.</span><span class="sxs-lookup"><span data-stu-id="38f08-109">In the left pane, expand Applications, and then expand BizTalk Application 1.</span></span> <span data-ttu-id="38f08-110">Cliquez sur Orchestrations.</span><span class="sxs-lookup"><span data-stu-id="38f08-110">Click Orchestrations.</span></span>  
  
4.  <span data-ttu-id="38f08-111">Avec le bouton droit **DynamicSendOrchestration** et cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="38f08-111">Right-click **DynamicSendOrchestration** and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="38f08-112">Dans le **propriétés d’Orchestration** boîte de dialogue, dans le volet gauche, cliquez sur **liaisons** et procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38f08-112">In the **Orchestration Properties** dialog box, in the left pane, click **Bindings** and do the following:</span></span>  
  
    |<span data-ttu-id="38f08-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="38f08-113">**Use this**</span></span>|<span data-ttu-id="38f08-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="38f08-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38f08-115">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="38f08-115">**Host**</span></span>|<span data-ttu-id="38f08-116">Dans la liste déroulante, sélectionnez **BizTalkServer Application**.</span><span class="sxs-lookup"><span data-stu-id="38f08-116">From the drop-down list, select **BizTalkServer Application**.</span></span>|  
    |<span data-ttu-id="38f08-117">**Extraction dynamique**</span><span class="sxs-lookup"><span data-stu-id="38f08-117">**Dynamic Pull**</span></span>|<span data-ttu-id="38f08-118">Dans la liste déroulante, sélectionnez **Tutorial_IA_DynamicSendPort**.</span><span class="sxs-lookup"><span data-stu-id="38f08-118">From the drop-down list, select **Tutorial_IA_DynamicSendPort**.</span></span>|  
    |<span data-ttu-id="38f08-119">**SendPullResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="38f08-119">**SendPullResponseToSender**</span></span>|<span data-ttu-id="38f08-120">Dans la liste déroulante, sélectionnez **Tutorial_IA_SendPullResponsetoReceiver**.</span><span class="sxs-lookup"><span data-stu-id="38f08-120">From the drop-down list, select **Tutorial_IA_SendPullResponsetoReceiver**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38f08-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38f08-121">See Also</span></span>  
 [<span data-ttu-id="38f08-122">Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour interagir magasin et scénario de (Pull) vers l’avant</span><span class="sxs-lookup"><span data-stu-id="38f08-122">Step 3A: Create an orchestration for dynamic send port for InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-interact-store-and-forward.md)
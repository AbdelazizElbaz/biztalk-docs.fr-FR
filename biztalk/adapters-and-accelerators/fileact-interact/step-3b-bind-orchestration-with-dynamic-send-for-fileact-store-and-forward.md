---
title: "Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb973066-8797-4f51-a89e-3845f2811605
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10111de1080aacd532be96f501be1d20acda1dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-bind-the-orchestration-with-dynamic-send-port-for-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="d582f-102">Étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct</span><span class="sxs-lookup"><span data-stu-id="d582f-102">Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="d582f-103">Avant de commencer cette étape, vous devez effectuer [étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="d582f-103">Before you begin this step, you must complete [Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="d582f-104">Pour ajouter un emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="d582f-104">To add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="d582f-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d582f-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d582f-106">Dans la Console Administration de BizTalk Server, dans le volet gauche, développez Administration de BizTalk Server, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **les Instances d’hôte** .</span><span class="sxs-lookup"><span data-stu-id="d582f-106">In the BizTalk Server Administration Console, in the left pane, expand BizTalk Server Administration, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="d582f-107">Vérifiez que l’état de la **BizTalkServerApplication** héberger l’instance et l’instance de FileActhost est **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="d582f-107">Verify that the status for the **BizTalkServerApplication** host instance and FileActhost instance is **running**.</span></span> <span data-ttu-id="d582f-108">Dans le cas contraire, cliquez sur les instances d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d582f-108">If not, right-click the host instances, and click **Start**.</span></span>  
  
3.  <span data-ttu-id="d582f-109">Dans le volet gauche, développez des Applications, puis BizTalk Application 1.</span><span class="sxs-lookup"><span data-stu-id="d582f-109">In the left pane, expand Applications, and then expand BizTalk Application 1.</span></span> <span data-ttu-id="d582f-110">Cliquez sur Orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d582f-110">Click Orchestrations.</span></span>  
  
4.  <span data-ttu-id="d582f-111">Avec le bouton droit **DynamicSendOrchestration** et cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d582f-111">Right-click **DynamicSendOrchestration** and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d582f-112">Dans le **propriétés d’Orchestration** boîte de dialogue, dans le volet gauche, cliquez sur **liaisons** et procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d582f-112">In the **Orchestration Properties** dialog box, in the left pane, click **Bindings** and do the following:</span></span>  
  
    |<span data-ttu-id="d582f-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="d582f-113">**Use this**</span></span>|<span data-ttu-id="d582f-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="d582f-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="d582f-115">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="d582f-115">**Host**</span></span>|<span data-ttu-id="d582f-116">Dans la liste déroulante, sélectionnez **BizTalkServer Application**.</span><span class="sxs-lookup"><span data-stu-id="d582f-116">From the drop-down list, select **BizTalkServer Application**.</span></span>|  
    |<span data-ttu-id="d582f-117">**Extraction dynamique**</span><span class="sxs-lookup"><span data-stu-id="d582f-117">**Dynamic Pull**</span></span>|<span data-ttu-id="d582f-118">Dans la liste déroulante, sélectionnez **Tutorial_FA_DynamicSendPort**.</span><span class="sxs-lookup"><span data-stu-id="d582f-118">From the drop-down list, select **Tutorial_FA_DynamicSendPort**.</span></span>|  
    |<span data-ttu-id="d582f-119">**SendPullResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="d582f-119">**SendPullResponseToSender**</span></span>|<span data-ttu-id="d582f-120">Dans la liste déroulante, sélectionnez **Tutorial_FA_SendPullResponsetoReceiver**.</span><span class="sxs-lookup"><span data-stu-id="d582f-120">From the drop-down list, select **Tutorial_FA_SendPullResponsetoReceiver**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d582f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d582f-121">See Also</span></span>  
 [<span data-ttu-id="d582f-122">Étape 3 a : création d’une orchestration pour le port d’envoi dynamique pour le scénario (Pull) avant d’et de FileAct</span><span class="sxs-lookup"><span data-stu-id="d582f-122">Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)
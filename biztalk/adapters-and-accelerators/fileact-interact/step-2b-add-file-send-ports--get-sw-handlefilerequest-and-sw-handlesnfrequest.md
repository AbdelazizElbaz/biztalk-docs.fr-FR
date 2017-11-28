---
title: "Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et scénario Sw:HandleSnFRequest des Messages pour le magasin de FileAct et le transfert (par extraction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21d055e9-ff7c-4af1-983b-d03e8d4a94f6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c2eb55cd6aca9b26b8a8ac47ab6dbe192f174d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="b2a15-102">Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et scénario Sw:HandleSnFRequest des Messages pour le magasin de FileAct et le transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="b2a15-102">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="b2a15-103">Avant de commencer cette étape, vous devez effectuer la [étape 2 : ajouter des emplacements de réception fichier pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) section.</span><span class="sxs-lookup"><span data-stu-id="b2a15-103">Before you begin this step, you must complete the [Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) section.</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-the-sw-handlefilerequest-message"></a><span data-ttu-id="b2a15-104">Pour ajouter un fichier de port d’envoi pour le logiciel de capture : HandleFileRequest message</span><span class="sxs-lookup"><span data-stu-id="b2a15-104">To add a FILE send port to capture the Sw: HandleFileRequest message</span></span>  
  
1.  <span data-ttu-id="b2a15-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b2a15-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="b2a15-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="b2a15-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="b2a15-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="b2a15-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_FA_SendPullResponsetoReceiver**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-108">In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendPullResponsetoReceiver**.</span></span>  
  
5.  <span data-ttu-id="b2a15-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="b2a15-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** , tapez **C:\SWIFTAdapterTutorial\FileAct\PullResponse**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\FileAct\PullResponse**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="b2a15-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b2a15-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="b2a15-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="b2a15-112">**Use this**</span></span>|<span data-ttu-id="b2a15-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="b2a15-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="b2a15-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="b2a15-114">**Send handler**</span></span>|<span data-ttu-id="b2a15-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="b2a15-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="b2a15-116">**Send pipeline**</span></span>|<span data-ttu-id="b2a15-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="b2a15-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b2a15-119">Répétez l’étape 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="b2a15-119">Repeat step 1 and 2.</span></span>  
  
10. <span data-ttu-id="b2a15-120">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi dynamique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-120">Right-click **Send Ports**, point to **New**, and then click **Dynamic Solicit-Response Send Port**.</span></span>  
  
11. <span data-ttu-id="b2a15-121">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi**, Tutorial_IA_DynamicSendPort**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-121">In the **Send Port Properties** window, name the send port**, Tutorial_IA_DynamicSendPort**.</span></span>  
  
12. <span data-ttu-id="b2a15-122">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b2a15-122">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="b2a15-123">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="b2a15-123">**Use this**</span></span>|<span data-ttu-id="b2a15-124">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="b2a15-124">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="b2a15-125">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="b2a15-125">**Send pipeline**</span></span>|<span data-ttu-id="b2a15-126">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-126">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="b2a15-127">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="b2a15-127">**Receive pipeline**</span></span>|<span data-ttu-id="b2a15-128">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-128">From the drop-down list, select **XMLReceive**.</span></span>|  
  
13. <span data-ttu-id="b2a15-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2a15-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a15-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2a15-130">See Also</span></span>  
 <span data-ttu-id="b2a15-131">[Étape 2 a : ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="b2a15-131">[Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="b2a15-132">Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct</span><span class="sxs-lookup"><span data-stu-id="b2a15-132">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)
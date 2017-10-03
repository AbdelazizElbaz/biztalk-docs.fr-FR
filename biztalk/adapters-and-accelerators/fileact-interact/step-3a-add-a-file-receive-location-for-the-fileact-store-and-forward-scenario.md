---
title: "Étape 3 a : ajouter un fichier emplacement de réception pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ecbf4a-a2b4-4534-8ca1-3bfbb6a697bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e02f636500ed21d4442a43078bcd407c91d69d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="ef512-102">Étape 3 a : ajouter un fichier emplacement de réception pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef512-102">Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="ef512-103">Avant de commencer cette étape, vous devez effectuer [étape 2 : ajouter une Configuration pour le Paramfile pour et le scénario de transfert de FileAct SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="ef512-103">Before you begin this step, you must complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="ef512-104">Pour ajouter un fichier emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="ef512-104">To add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="ef512-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ef512-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ef512-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="ef512-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="ef512-107">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="ef512-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="ef512-108">Dans le **propriétés du Port de réception** fenêtre, nom du port de réception, Tutorial_FA_InputRequest_SnF.</span><span class="sxs-lookup"><span data-stu-id="ef512-108">In the **Receive Port Properties** window, name the receive port, Tutorial_FA_InputRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="ef512-109">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="ef512-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="ef512-110">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ef512-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="ef512-111">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** zone, tapez C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef512-111">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="ef512-112">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ef512-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="ef512-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="ef512-113">**Use this**</span></span>|<span data-ttu-id="ef512-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="ef512-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="ef512-115">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="ef512-115">**Receive handler**</span></span>|<span data-ttu-id="ef512-116">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="ef512-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="ef512-117">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="ef512-117">**Receive pipeline**</span></span>|<span data-ttu-id="ef512-118">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="ef512-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="ef512-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef512-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef512-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef512-120">See Also</span></span>  
 <span data-ttu-id="ef512-121">[Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-121">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="ef512-122">[Étape 3 b : ajouter un FILEACT emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-122">[Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="ef512-123">[Étape 3c : ajouter un Port d’envoi FILE pour capturer les Messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span><span class="sxs-lookup"><span data-stu-id="ef512-123">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span></span>  
 [<span data-ttu-id="ef512-124">Étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef512-124">Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)
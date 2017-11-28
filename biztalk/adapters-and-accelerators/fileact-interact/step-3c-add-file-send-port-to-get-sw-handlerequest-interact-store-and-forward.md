---
title: "Étape 3c : ajouter le port d’envoi FILE pour obtenir Sw:HandleRequest-interagir de stocker et transférer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c872b4be-ef8b-4e42-b5ef-63dfd120793f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b82c57f2f3a6e2fcfc199e56d34c44aa7667451d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-store-and-forward"></a><span data-ttu-id="59ad0-102">Étape 3c : ajouter le port d’envoi FILE pour obtenir Sw:HandleRequest-interagir de stocker et transférer</span><span class="sxs-lookup"><span data-stu-id="59ad0-102">Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct Store and Forward</span></span>
<span data-ttu-id="59ad0-103">Avant de commencer cette étape, vous devez effectuer [étape 3 b : ajouter une interaction un emplacement de réception pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="59ad0-103">Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a><span data-ttu-id="59ad0-104">Pour ajouter un fichier de port d’envoi pour capturer le message Sw:HandleRequest</span><span class="sxs-lookup"><span data-stu-id="59ad0-104">To add a FILE send port to capture the Sw:HandleRequest message</span></span>  
  
1.  <span data-ttu-id="59ad0-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="59ad0-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="59ad0-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="59ad0-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="59ad0-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="59ad0-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_IA_SendResponseToReceiver.</span><span class="sxs-lookup"><span data-stu-id="59ad0-108">In the **Send Port Properties** window, name the send port, Tutorial_IA_SendResponseToReceiver.</span></span>  
  
5.  <span data-ttu-id="59ad0-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="59ad0-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Interact\HandleRequest, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Interact\HandleRequest, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="59ad0-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="59ad0-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="59ad0-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="59ad0-112">**Use this**</span></span>|<span data-ttu-id="59ad0-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="59ad0-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="59ad0-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="59ad0-114">**Send handler**</span></span>|<span data-ttu-id="59ad0-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="59ad0-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="59ad0-116">**Send pipeline**</span></span>|<span data-ttu-id="59ad0-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="59ad0-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="59ad0-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="59ad0-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="59ad0-119">**Use this**</span></span>|<span data-ttu-id="59ad0-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="59ad0-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="59ad0-121">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="59ad0-121">**Property**</span></span>|<span data-ttu-id="59ad0-122">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-122">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="59ad0-123">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="59ad0-123">**Operator**</span></span>|<span data-ttu-id="59ad0-124">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="59ad0-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="59ad0-125">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="59ad0-125">**Value**</span></span>|<span data-ttu-id="59ad0-126">Type **Tutorial_IA_InputRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-126">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="59ad0-127">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="59ad0-127">**Group by**</span></span>|<span data-ttu-id="59ad0-128">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="59ad0-128">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="59ad0-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59ad0-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ad0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59ad0-130">See Also</span></span>  
 <span data-ttu-id="59ad0-131">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="59ad0-131">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="59ad0-132">[Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="59ad0-132">[Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="59ad0-133">[Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="59ad0-133">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="59ad0-134">Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="59ad0-134">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)
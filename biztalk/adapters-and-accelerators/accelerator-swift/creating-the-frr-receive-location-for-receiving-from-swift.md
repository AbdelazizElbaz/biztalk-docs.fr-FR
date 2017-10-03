---
title: "Création de la FRR emplacement de réception pour recevoir des SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: e10857f4-21cb-4c09-8eed-cb6e9b0a0aa9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43ac2ac0fab9b2a29a44784032f9d3369833ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-swift"></a><span data-ttu-id="94820-102">Création de la FRR emplacement de réception pour recevoir des SWIFT</span><span class="sxs-lookup"><span data-stu-id="94820-102">Creating the FRR Receive Location for Receiving from SWIFT</span></span>
<span data-ttu-id="94820-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer un emplacement de réception qui reçoit un message à partir du réseau SWIFT dans A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="94820-103">To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the SWIFT Network into A4SWIFT.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94820-104">Il est recommandé de configurer deux emplacements de réception pour recevoir des messages de SAA : un pour la réception de panoramique/valeurs NaN et l’autre pour recevoir tous les autres messages.</span><span class="sxs-lookup"><span data-stu-id="94820-104">It is advisable to set up two receive locations for receiving messages from SAA: one to receive PAN/NANs and one to receive all other messages.</span></span> <span data-ttu-id="94820-105">Pour configurer les deux emplacements de réception, vous devez recevoir des messages de deux les files d’attente MQSeries à SAA : un pour panoramique/valeurs NaN et un pour tous les autres types de messages.</span><span class="sxs-lookup"><span data-stu-id="94820-105">To set up the two receive locations, you must receive messages from two MQSeries queues at SAA: one for PAN/NANs and one for all other message types.</span></span>  
  
 <span data-ttu-id="94820-106">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="94820-106">**Summary**</span></span>  
  
 <span data-ttu-id="94820-107">Créer un emplacement de réception avec les propriétés suivantes et les composants :</span><span class="sxs-lookup"><span data-stu-id="94820-107">Create a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="94820-108">Propriété/composant</span><span class="sxs-lookup"><span data-stu-id="94820-108">Property/Component</span></span>|<span data-ttu-id="94820-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="94820-109">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="94820-110">Port de réception</span><span class="sxs-lookup"><span data-stu-id="94820-110">Receive port</span></span>|<span data-ttu-id="94820-111">Port unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="94820-111">One-way port</span></span>|  
|<span data-ttu-id="94820-112">Type de transport </span><span class="sxs-lookup"><span data-stu-id="94820-112">Transport type</span></span>|<span data-ttu-id="94820-113">MQSeries</span><span class="sxs-lookup"><span data-stu-id="94820-113">MQSeries</span></span>|  
|<span data-ttu-id="94820-114">Définition de la file d’attente (MQSeries)</span><span class="sxs-lookup"><span data-stu-id="94820-114">Queue Definition (MQSeries)</span></span>|<span data-ttu-id="94820-115">MQSeries server</span><span class="sxs-lookup"><span data-stu-id="94820-115">MQSeries server</span></span><br /><span data-ttu-id="94820-116">Gestionnaire de file d’attente</span><span class="sxs-lookup"><span data-stu-id="94820-116">Queue manager</span></span><br /><span data-ttu-id="94820-117">File d'attente</span><span class="sxs-lookup"><span data-stu-id="94820-117">Queue</span></span>|  
|<span data-ttu-id="94820-118">Gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="94820-118">Receive handler</span></span>|<span data-ttu-id="94820-119">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="94820-119">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="94820-120">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="94820-120">Receive pipeline</span></span>|<span data-ttu-id="94820-121">Le A4SWIFT pipeline de réception qui vous avez créé pour FRR</span><span class="sxs-lookup"><span data-stu-id="94820-121">The A4SWIFT receive pipeline that you created for FRR</span></span>|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-swift"></a><span data-ttu-id="94820-122">Pour ajouter un FRR provenant de l’emplacement de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="94820-122">To add an FRR receive location for receiving from SWIFT</span></span>  
  
1.  <span data-ttu-id="94820-123">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** nœuds.</span><span class="sxs-lookup"><span data-stu-id="94820-123">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and  **BizTalk Application 1** nodes.</span></span>  
  
2.  <span data-ttu-id="94820-124">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="94820-124">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="94820-125">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception, par exemple FRRSWIFTReceivePort.</span><span class="sxs-lookup"><span data-stu-id="94820-125">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRSWIFTReceivePort.</span></span>  
  
4.  <span data-ttu-id="94820-126">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="94820-126">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="94820-127">Dans la Console d’Administration, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="94820-127">In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
6.  <span data-ttu-id="94820-128">Dans la boîte de dialogue un Port de réception, sélectionnez, sélectionnez le port de réception que vous venez créé, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="94820-128">In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="94820-129">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception, par exemple FRRSWIFTReceiveLocation.</span><span class="sxs-lookup"><span data-stu-id="94820-129">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location, such as FRRSWIFTReceiveLocation.</span></span>  
  
8.  <span data-ttu-id="94820-130">Dans le **Transport** section, pour le **Type** zone de texte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="94820-130">In the **Transport** section, for the **Type** text box, select **MQSeries**.</span></span>  
  
9. <span data-ttu-id="94820-131">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="94820-131">Click **Configure**.</span></span>  
  
10. <span data-ttu-id="94820-132">Dans la boîte de dialogue Propriétés du Transport MQSeries, cliquez sur **définition file d’attente**, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="94820-132">In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis (**…**) button.</span></span>  
  
11. <span data-ttu-id="94820-133">Dans le **définition file d’attente** boîte de dialogue, entrez le serveur MQSeries, Gestionnaire de file d’attente et la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="94820-133">In the **Queue Definition** dialog box, enter the MQSeries server, queue manager, and queue.</span></span> <span data-ttu-id="94820-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="94820-134">Click **OK**.</span></span>  
  
12. <span data-ttu-id="94820-135">Dans le **propriétés du Transport MQSeries** boîte de dialogue, vérifiez que les propriétés sont en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="94820-135">In the **MQSeries Transport Properties** dialog box, verify that the properties are as needed.</span></span> <span data-ttu-id="94820-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="94820-136">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94820-137">Pour plus d’informations sur les propriétés du transport MQSeries, consultez la documentation de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="94820-137">For more information about MQSeries transport properties, see the MQSeries documentation.</span></span>  
  
13. <span data-ttu-id="94820-138">Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Gestionnaire de réception**, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="94820-138">In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.</span></span>  
  
14. <span data-ttu-id="94820-139">Pour **Pipeline de réception** section, sélectionnez le A4SWIFT pipeline de réception qui vous avez créé pour FRR.</span><span class="sxs-lookup"><span data-stu-id="94820-139">For **Receive Pipeline** section, select the A4SWIFT receive pipeline that you created for FRR.</span></span>  
  
15. <span data-ttu-id="94820-140">Cliquez sur **appliquer**, puis cliquez sur **OK**</span><span class="sxs-lookup"><span data-stu-id="94820-140">Click **Apply**, and then click **OK**</span></span>  
  
16. <span data-ttu-id="94820-141">Dans l’Explorateur BizTalk, cliquez sur l’emplacement de réception que vous venez créé, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="94820-141">In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.</span></span>
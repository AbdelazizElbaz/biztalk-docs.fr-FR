---
title: "Création du Port d’envoi FRR pour l’envoi à SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 1ad766db-d1da-437a-a520-a3b04f0695c4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75cbda5d505f17f2dd7462cb0b16868a340f625c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-send-port-for-sending-to-swift"></a><span data-ttu-id="4cb70-102">Création du Port d’envoi FRR pour l’envoi à SWIFT</span><span class="sxs-lookup"><span data-stu-id="4cb70-102">Creating the FRR Send Port for Sending to SWIFT</span></span>
<span data-ttu-id="4cb70-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer un port d’envoi qui envoie un message à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] au réseau SWIFT.</span><span class="sxs-lookup"><span data-stu-id="4cb70-103">To perform FIN Response Reconciliation, you need to create a send port that sends a message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Network.</span></span>  
  
 <span data-ttu-id="4cb70-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="4cb70-104">**Summary**</span></span>  
  
 <span data-ttu-id="4cb70-105">Créer un port d’envoi avec les propriétés suivantes et les composants :</span><span class="sxs-lookup"><span data-stu-id="4cb70-105">Create a send port with the following properties and components:</span></span>  
  
|<span data-ttu-id="4cb70-106">Propriété/composant</span><span class="sxs-lookup"><span data-stu-id="4cb70-106">Property/Component</span></span>|<span data-ttu-id="4cb70-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4cb70-107">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="4cb70-108">Port d'envoi</span><span class="sxs-lookup"><span data-stu-id="4cb70-108">Send port</span></span>|<span data-ttu-id="4cb70-109">Port statique unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="4cb70-109">Static one-way port</span></span>|  
|<span data-ttu-id="4cb70-110">Type de transport </span><span class="sxs-lookup"><span data-stu-id="4cb70-110">Transport type</span></span>|<span data-ttu-id="4cb70-111">MQSeries</span><span class="sxs-lookup"><span data-stu-id="4cb70-111">MQSeries</span></span>|  
|<span data-ttu-id="4cb70-112">Définition de la file d’attente (MQSeries)</span><span class="sxs-lookup"><span data-stu-id="4cb70-112">Queue Definition (MQSeries)</span></span>|<span data-ttu-id="4cb70-113">Gestionnaire de file d’attente MQSeries server file d’attente</span><span class="sxs-lookup"><span data-stu-id="4cb70-113">MQSeries server Queue manager Queue</span></span>|  
|<span data-ttu-id="4cb70-114">Pipeline d’envoi</span><span class="sxs-lookup"><span data-stu-id="4cb70-114">Send pipeline</span></span>|<span data-ttu-id="4cb70-115">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline d’envoi que vous avez créé pour FRR</span><span class="sxs-lookup"><span data-stu-id="4cb70-115">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR</span></span>|  
|<span data-ttu-id="4cb70-116">Filtres</span><span class="sxs-lookup"><span data-stu-id="4cb70-116">Filters</span></span>|<span data-ttu-id="4cb70-117">Comme indiqué dans le tableau ci-dessous</span><span class="sxs-lookup"><span data-stu-id="4cb70-117">As shown in the table below</span></span>|  
  
### <a name="to-add-a-custom-send-port-for-sending-to-swift"></a><span data-ttu-id="4cb70-118">Pour ajouter un port d’envoi personnalisé pour l’envoi à SWIFT</span><span class="sxs-lookup"><span data-stu-id="4cb70-118">To add a custom send port for sending to SWIFT</span></span>  
  
1.  <span data-ttu-id="4cb70-119">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Static-waySend un Port**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-119">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.</span></span>  
  
2.  <span data-ttu-id="4cb70-120">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi, par exemple FRRSWIFTSendPort.</span><span class="sxs-lookup"><span data-stu-id="4cb70-120">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRSWIFTSendPort.</span></span>  
  
3.  <span data-ttu-id="4cb70-121">Pour **Type**, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-121">For **Type**, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="4cb70-122">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-122">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="4cb70-123">Dans la boîte de dialogue Propriétés du Transport MQSeries, cliquez sur **définition file d’attente**, puis cliquez sur les points de suspension ().</span><span class="sxs-lookup"><span data-stu-id="4cb70-123">In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis () button.</span></span>  
  
6.  <span data-ttu-id="4cb70-124">Dans la boîte de dialogue Définition file d’attente, entrez le serveur MQSeries, le Gestionnaire de file d’attente et la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="4cb70-124">In the Queue Definition dialog box, enter the MQSeries server, queue manager, and queue.</span></span> <span data-ttu-id="4cb70-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-125">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="4cb70-126">Dans la boîte de dialogue Propriétés du Transport MQSeries, vérifiez que les propriétés sont en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="4cb70-126">In the MQSeries Transport Properties dialog box, verify that the properties are as needed.</span></span> <span data-ttu-id="4cb70-127">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-127">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4cb70-128">Pour plus d’informations sur les propriétés du transport MQSeries, consultez la documentation de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="4cb70-128">For more information about MQSeries transport properties, see the MQSeries documentation.</span></span>  
  
8.  <span data-ttu-id="4cb70-129">Dans la boîte de dialogue Propriétés de Port d’envoi pour **Gestionnaire d’envoi**, vérifiez que BizTalkServerApplication est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="4cb70-129">In the Send Port Properties dialog box, for **Send handler**, verify that BizTalkServerApplication is selected.</span></span>  
  
9. <span data-ttu-id="4cb70-130">Pour **Pipeline d’envoi**, sélectionnez le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline d’envoi que vous avez créé pour FRR.</span><span class="sxs-lookup"><span data-stu-id="4cb70-130">For **Send Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR.</span></span>  
  
10. <span data-ttu-id="4cb70-131">Cliquez sur **filtres** dans le volet gauche, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4cb70-131">Click **Filters** in the left pane, and then do the following:</span></span>  
  
    |<span data-ttu-id="4cb70-132">Utiliser</span><span class="sxs-lookup"><span data-stu-id="4cb70-132">Use this</span></span>|<span data-ttu-id="4cb70-133">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="4cb70-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4cb70-134">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4cb70-134">**Property**</span></span>|<span data-ttu-id="4cb70-135">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-135">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span></span>|  
    |<span data-ttu-id="4cb70-136">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="4cb70-136">**Operator**</span></span>|<span data-ttu-id="4cb70-137">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="4cb70-137">Select **==**.</span></span>|  
    |<span data-ttu-id="4cb70-138">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4cb70-138">**Value**</span></span>|<span data-ttu-id="4cb70-139">Type **False**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-139">Type **False**.</span></span>|  
    |<span data-ttu-id="4cb70-140">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="4cb70-140">**Group**</span></span>|<span data-ttu-id="4cb70-141">Sélectionnez **et**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-141">Select **And**.</span></span>|  
    |<span data-ttu-id="4cb70-142">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4cb70-142">**Property**</span></span>|<span data-ttu-id="4cb70-143">Type **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-143">Type **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**.</span></span>|  
    |<span data-ttu-id="4cb70-144">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="4cb70-144">**Operator**</span></span>|<span data-ttu-id="4cb70-145">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="4cb70-145">Select **==**.</span></span>|  
    |<span data-ttu-id="4cb70-146">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4cb70-146">**Value**</span></span>|<span data-ttu-id="4cb70-147">Type **True**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-147">Type **True**.</span></span>|  
  
11. <span data-ttu-id="4cb70-148">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-148">Click **Apply**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="4cb70-149">Cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="4cb70-149">Right-click the send port, and then click **Start**.</span></span>
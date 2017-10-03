---
title: "Création d’un Port d’envoi A4SWIFT | Documents Microsoft"
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
ms.assetid: d1ee18f8-a6aa-4cd5-9e65-fb2e0fa2d0c2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf24cb99643acc869123450ce14fd5050ee7408
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-send-port"></a><span data-ttu-id="55c39-102">Création d’un Port d’envoi A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="55c39-102">Creating an A4SWIFT Send Port</span></span>
<span data-ttu-id="55c39-103">Vous devez créer un port d’envoi pour activer [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour envoyer un message au réseau rapide, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="55c39-103">You must create a send port to enable [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to send a message to the SWIFT network, as shown in the following figure.</span></span> <span data-ttu-id="55c39-104">Ce port d’envoi envoie les messages de fichier plat vers un dossier sortant.</span><span class="sxs-lookup"><span data-stu-id="55c39-104">This send port will send flat file messages to an outbound file folder.</span></span> <span data-ttu-id="55c39-105">Ce port d’envoi est conçu pour fonctionner avec la fonctionnalité de Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="55c39-105">This send port is designed to work with the Message Repair and New Submission feature.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-send-port-configuration.gif "A4SWIFT_Send_Port_Configuration")  
  
 <span data-ttu-id="55c39-106">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="55c39-106">**Summary**</span></span>  
  
 <span data-ttu-id="55c39-107">Créer et démarrer un port d’envoi unidirectionnel statique avec les propriétés et les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="55c39-107">Create and start a static one-way send port with the following properties and components:</span></span>  
  
|<span data-ttu-id="55c39-108">Propriété/composant</span><span class="sxs-lookup"><span data-stu-id="55c39-108">Property/Component</span></span>|<span data-ttu-id="55c39-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="55c39-109">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="55c39-110">Port d'envoi</span><span class="sxs-lookup"><span data-stu-id="55c39-110">Send port</span></span>|<span data-ttu-id="55c39-111">Port statique unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="55c39-111">Static one-way port</span></span>|  
|<span data-ttu-id="55c39-112">Type de transport </span><span class="sxs-lookup"><span data-stu-id="55c39-112">Transport type</span></span>|<span data-ttu-id="55c39-113">FILE</span><span class="sxs-lookup"><span data-stu-id="55c39-113">FILE</span></span>|  
|<span data-ttu-id="55c39-114">Dossier de destination (adresse URI)</span><span class="sxs-lookup"><span data-stu-id="55c39-114">Destination folder (Address URI)</span></span>|<span data-ttu-id="55c39-115">Nom du dossier que vous souhaitez envoyer des messages à partir de</span><span class="sxs-lookup"><span data-stu-id="55c39-115">Name of the folder that you want to send messages from</span></span>|  
|<span data-ttu-id="55c39-116">Nom de fichier (adresse URI)</span><span class="sxs-lookup"><span data-stu-id="55c39-116">File Name (Address URI)</span></span>|<span data-ttu-id="55c39-117">%MessageID%.txt</span><span class="sxs-lookup"><span data-stu-id="55c39-117">%MessageID%.txt</span></span>|  
|<span data-ttu-id="55c39-118">Filtres</span><span class="sxs-lookup"><span data-stu-id="55c39-118">Filters</span></span>|<span data-ttu-id="55c39-119">Comme décrit dans le tableau ci-dessous</span><span class="sxs-lookup"><span data-stu-id="55c39-119">As described in the table below</span></span>|  
  
### <a name="to-add-the-sent-port"></a><span data-ttu-id="55c39-120">Pour ajouter le port d’envoi</span><span class="sxs-lookup"><span data-stu-id="55c39-120">To add the sent port</span></span>  
  
1.  <span data-ttu-id="55c39-121">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="55c39-121">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="55c39-122">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="55c39-122">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port.</span></span>  
  
3.  <span data-ttu-id="55c39-123">Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="55c39-123">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="55c39-124">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="55c39-124">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="55c39-125">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="55c39-125">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="55c39-126">Dans la boîte de dialogue Rechercher un dossier, déplacer vers le dossier que vous souhaitez envoyer des messages à partir de.</span><span class="sxs-lookup"><span data-stu-id="55c39-126">In the Browse For Folder dialog box, move to the folder that you want to send messages from.</span></span> <span data-ttu-id="55c39-127">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c39-127">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55c39-128">Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.</span><span class="sxs-lookup"><span data-stu-id="55c39-128">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
7.  <span data-ttu-id="55c39-129">Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c39-129">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="55c39-130">Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur la liste déroulante pour le **pipeline d’envoi** zone, puis sélectionnez le pipeline d’envoi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="55c39-130">In the **Send Port Properties** dialog box, click the drop-down list for the **Send pipeline** box, and then select your custom send pipeline.</span></span>  
  
9. <span data-ttu-id="55c39-131">Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="55c39-131">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="55c39-132">Utiliser</span><span class="sxs-lookup"><span data-stu-id="55c39-132">Use this</span></span>|<span data-ttu-id="55c39-133">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="55c39-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="55c39-134">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="55c39-134">**Property**</span></span>|<span data-ttu-id="55c39-135">Sélectionnez **BTS. Opération**.</span><span class="sxs-lookup"><span data-stu-id="55c39-135">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="55c39-136">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="55c39-136">**Operator**</span></span>|<span data-ttu-id="55c39-137">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="55c39-137">Select **==**.</span></span>|  
    |<span data-ttu-id="55c39-138">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="55c39-138">**Value**</span></span>|<span data-ttu-id="55c39-139">Type **A4SWIFT_MRSRCompleted**.</span><span class="sxs-lookup"><span data-stu-id="55c39-139">Type **A4SWIFT_MRSRCompleted**.</span></span>|  
    |<span data-ttu-id="55c39-140">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="55c39-140">**Group**</span></span>|<span data-ttu-id="55c39-141">Sélectionnez **ou.**</span><span class="sxs-lookup"><span data-stu-id="55c39-141">Select **Or.**</span></span>|  
    |<span data-ttu-id="55c39-142">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="55c39-142">**Property**</span></span>|<span data-ttu-id="55c39-143">Sélectionnez **BTS. Opération**.</span><span class="sxs-lookup"><span data-stu-id="55c39-143">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="55c39-144">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="55c39-144">**Operator**</span></span>|<span data-ttu-id="55c39-145">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="55c39-145">Select **==**.</span></span>|  
    |<span data-ttu-id="55c39-146">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="55c39-146">**Value**</span></span>|<span data-ttu-id="55c39-147">Type **A4SWIFT_MRSRFailed**.</span><span class="sxs-lookup"><span data-stu-id="55c39-147">Type **A4SWIFT_MRSRFailed**.</span></span>|  
    |<span data-ttu-id="55c39-148">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="55c39-148">**Group**</span></span>|<span data-ttu-id="55c39-149">Sélectionnez **ou**.</span><span class="sxs-lookup"><span data-stu-id="55c39-149">Select **Or**.</span></span>|  
    |<span data-ttu-id="55c39-150">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="55c39-150">**Property**</span></span>|<span data-ttu-id="55c39-151">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span><span class="sxs-lookup"><span data-stu-id="55c39-151">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span></span>|  
    |<span data-ttu-id="55c39-152">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="55c39-152">**Operator**</span></span>|<span data-ttu-id="55c39-153">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="55c39-153">Select **==**.</span></span>|  
    |<span data-ttu-id="55c39-154">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="55c39-154">**Value**</span></span>|<span data-ttu-id="55c39-155">Type **True**.</span><span class="sxs-lookup"><span data-stu-id="55c39-155">Type **True**.</span></span>|  
  
10. <span data-ttu-id="55c39-156">Cliquez sur **appliquer**, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="55c39-156">Click **Apply**, and then click **OK.**</span></span>  
  
11. <span data-ttu-id="55c39-157">Dans le **Ports d’envoi** volet, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="55c39-157">In the **Send Ports** pane, right-click the send port, and then click **Start**.</span></span>
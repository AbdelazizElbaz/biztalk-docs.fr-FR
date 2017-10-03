---
title: "Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 796570ca-8178-4679-9213-d67a2a189bf9
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b513725024aec755515ccac998745220ee5dfa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configure-a-send-port-to-send-data-to-your-organization"></a><span data-ttu-id="394f9-102">Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation</span><span class="sxs-lookup"><span data-stu-id="394f9-102">Step 6: Configure a Send Port to Send Data to Your Organization</span></span>
<span data-ttu-id="394f9-103">![Étape 6 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span><span class="sxs-lookup"><span data-stu-id="394f9-103">![Step 6 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span></span>  
  
 <span data-ttu-id="394f9-104">Cette étape permet de configurer un port d'envoi pour envoyer le message 850 depuis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au tiers OrderSystem qui représente votre organisation.</span><span class="sxs-lookup"><span data-stu-id="394f9-104">In this step you configure a send port to send the 850 message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the OrderSystem party that represents your organization.</span></span> <span data-ttu-id="394f9-105">Ce port d’envoi s’applique le **Inbound4010850_to_OrderFile** table, transformer le message de sortie à partir du format du message d’entrée au format spécifié dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="394f9-105">This send port applies the **Inbound4010850_to_OrderFile** map, transforming the output message from the format of the input message to the format specified in the map.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="394f9-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="394f9-106">Prerequisites</span></span>  
 <span data-ttu-id="394f9-107">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="394f9-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-send-port-for-the-850-message"></a><span data-ttu-id="394f9-108">Pour configurer un port d'envoi pour le message 850</span><span class="sxs-lookup"><span data-stu-id="394f9-108">To configure a send port for the 850 message</span></span>  
  
1.  <span data-ttu-id="394f9-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Pipelines**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="394f9-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Pipelines**, and then click **Refresh**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-110">L'actualisation de la liste de pipelines peut être nécessaire pour sélectionner le pipeline SendOrderFilePipeline pour le port d'envoi que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="394f9-110">Refreshing the pipelines list may be necessary to be able to select the SendOrderFilePipeline for the send port that you will create.</span></span>  
  
2.  <span data-ttu-id="394f9-111">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="394f9-111">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="394f9-112">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="394f9-112">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="394f9-113">Utiliser</span><span class="sxs-lookup"><span data-stu-id="394f9-113">Use this</span></span>|<span data-ttu-id="394f9-114">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="394f9-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="394f9-115">**Nom**</span><span class="sxs-lookup"><span data-stu-id="394f9-115">**Name**</span></span>|<span data-ttu-id="394f9-116">Entrez `toOrderSystem`.</span><span class="sxs-lookup"><span data-stu-id="394f9-116">Enter `toOrderSystem`.</span></span>|  
    |<span data-ttu-id="394f9-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="394f9-117">**Type**</span></span>|<span data-ttu-id="394f9-118">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="394f9-118">Select **FILE**.</span></span>|  
    |<span data-ttu-id="394f9-119">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="394f9-119">**Configure**</span></span>|<span data-ttu-id="394f9-120">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="394f9-120">Click **Configure**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-121">Le type de transport du port d'envoi est FILE car le message test est un fichier plat envoyé dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="394f9-121">The transport type of the send port is FILE because the test message is a flat file to be delivered into a folder.</span></span>  
  
4.  <span data-ttu-id="394f9-122">Dans le **propriétés du Transport FILE** boîte de dialogue zone, procédez comme suit, puis sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="394f9-122">In the **FILE Transport Properties** dialog box, do the following and then click **OK**:</span></span>  
  
    |<span data-ttu-id="394f9-123">Utiliser</span><span class="sxs-lookup"><span data-stu-id="394f9-123">Use this</span></span>|<span data-ttu-id="394f9-124">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="394f9-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="394f9-125">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="394f9-125">**Destination folder**</span></span>|<span data-ttu-id="394f9-126">Cliquez sur **Parcourir**et dans le **rechercher un dossier** boîte de dialogue, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer tutorial\processedi_testlocations\scenario A\toOrderSystem</span><span class="sxs-lookup"><span data-stu-id="394f9-126">Click **Browse**, and in the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ Scenario A\toOrderSystem</span></span>|  
    |<span data-ttu-id="394f9-127">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="394f9-127">**File name**</span></span>|<span data-ttu-id="394f9-128">Entrez `%MessageID%.txt`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="394f9-128">Enter `%MessageID%.txt`, and then click **OK**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-129">La valeur définie pour le **nom de fichier** propriété garantit que le fichier de sortie aura une extension .txt.</span><span class="sxs-lookup"><span data-stu-id="394f9-129">The value set for the **File name** property ensures that the output file will have a .txt extension.</span></span>  
  
5.  <span data-ttu-id="394f9-130">Dans le **propriétés de Port d’envoi** boîte de dialogue, pour **pipeline d’envoi**, sélectionnez **SendOrderFilePipeline**.</span><span class="sxs-lookup"><span data-stu-id="394f9-130">In the **Send Port Properties** dialog box, for **Send pipeline**, select **SendOrderFilePipeline**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-131">Le **SendOrderFilePipeline** pipeline inclut un assembleur de fichier plat qui assemble le fichier de sortie .txt, à l’aide des données mappées depuis le message 850 d’entrée d’envoi.</span><span class="sxs-lookup"><span data-stu-id="394f9-131">The **SendOrderFilePipeline** send pipeline includes a flat-file assembler that assembles the .txt output file, using data mapped from the input 850 message.</span></span> <span data-ttu-id="394f9-132">Comme le fichier de sortie est un fichier .txt, il ne figure pas dans le rapport État de l'échange/de l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="394f9-132">Since the output file is a .txt file, it will not show up in the Interchange/ACK status report.</span></span>  
  
6.  <span data-ttu-id="394f9-133">Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="394f9-133">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="394f9-134">Utiliser</span><span class="sxs-lookup"><span data-stu-id="394f9-134">Use this</span></span>|<span data-ttu-id="394f9-135">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="394f9-135">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="394f9-136">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="394f9-136">**Property**</span></span>|<span data-ttu-id="394f9-137">Sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="394f9-137">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="394f9-138">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="394f9-138">**Operator**</span></span>|<span data-ttu-id="394f9-139">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="394f9-139">Select **==**.</span></span>|  
    |<span data-ttu-id="394f9-140">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="394f9-140">**Value**</span></span>|<span data-ttu-id="394f9-141">Entrez `ReceiveEDI_fromTHEM_A`.</span><span class="sxs-lookup"><span data-stu-id="394f9-141">Enter `ReceiveEDI_fromTHEM_A`.</span></span>|  
    |<span data-ttu-id="394f9-142">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="394f9-142">**Group by**</span></span>|<span data-ttu-id="394f9-143">Sélectionnez **et**.</span><span class="sxs-lookup"><span data-stu-id="394f9-143">Select **And**.</span></span>|  
    |<span data-ttu-id="394f9-144">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="394f9-144">**Property**</span></span>|<span data-ttu-id="394f9-145">Sur la ligne suivante, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="394f9-145">On the next line, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="394f9-146">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="394f9-146">**Operator**</span></span>|<span data-ttu-id="394f9-147">Sélectionnez **! =**.</span><span class="sxs-lookup"><span data-stu-id="394f9-147">Select **!=**.</span></span>|  
    |<span data-ttu-id="394f9-148">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="394f9-148">**Value**</span></span>|<span data-ttu-id="394f9-149">Entrez `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span><span class="sxs-lookup"><span data-stu-id="394f9-149">Enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-150">Le filtre vérifie que le port d'envoi récupère les messages reçus par l'emplacement de réception Receive_EDI_fromTHEM_A, et que le port d'envoi récupère uniquement les messages 850, et non les accusés de réception 997.</span><span class="sxs-lookup"><span data-stu-id="394f9-150">The filter ensures that the send port will pick up messages that were received by the Receive_EDI_fromTHEM_A receive location, and that the send port will not pick up 997 acknowledgments, but will pick only 850 messages.</span></span>  
  
7.  <span data-ttu-id="394f9-151">Dans l’arborescence de la console, cliquez sur **OutboundMaps**.</span><span class="sxs-lookup"><span data-stu-id="394f9-151">In the console tree, click **OutboundMaps**.</span></span> <span data-ttu-id="394f9-152">Dans le **mappages sortants** volet, dans le **carte** colonne, sur la première ligne, sélectionnez **Inbound4010850_to_OrderFile**.</span><span class="sxs-lookup"><span data-stu-id="394f9-152">In the **Outbound Maps** pane, in the **Map** column, on the first row, select **Inbound4010850_to_OrderFile**.</span></span> <span data-ttu-id="394f9-153">(L’entrée dans le **Document Source** colonne sera X12_00401_850.)</span><span class="sxs-lookup"><span data-stu-id="394f9-153">(The entry in the **Source Document** column will be X12_00401_850.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="394f9-154">Cette étape permet de s’assurer que le message de sortie se compose uniquement des données mappées depuis le message d’entrée en fonction de la **Inbound4010850_to_OrderFile** carte.</span><span class="sxs-lookup"><span data-stu-id="394f9-154">This step ensures that the output message will consist only of the data mapped from the input message according to the **Inbound4010850_to_OrderFile** map.</span></span>  
  
8.  <span data-ttu-id="394f9-155">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="394f9-155">Click **OK**.</span></span>  
  
9. <span data-ttu-id="394f9-156">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="394f9-156">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Send Ports**.</span></span> <span data-ttu-id="394f9-157">Avec le bouton droit **toOrderSystem**, puis cliquez sur **Démarrer** pour inscrire et démarrer le port.</span><span class="sxs-lookup"><span data-stu-id="394f9-157">Right-click **toOrderSystem**, and then click **Start** to enlist and start the port.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="394f9-158">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="394f9-158">Next Steps</span></span>  
 <span data-ttu-id="394f9-159">Configurer le port d’envoi (**toTHEM_997**) pour envoyer le 997 accusé de réception vers Fabrikam, comme décrit dans [étape 7 : configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md).</span><span class="sxs-lookup"><span data-stu-id="394f9-159">You configure the send port (**toTHEM_997**) to send the 997 acknowledgment back to Fabrikam, as described in [Step 7: Configure a Send Port to Send the Acknowledgment to Your Trading Partner](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394f9-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="394f9-160">See Also</span></span>  
 [<span data-ttu-id="394f9-161">Configuration d’un Port d’envoi statique pour envoyer des échanges EDI et les accusés de réception</span><span class="sxs-lookup"><span data-stu-id="394f9-161">Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments</span></span>](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)
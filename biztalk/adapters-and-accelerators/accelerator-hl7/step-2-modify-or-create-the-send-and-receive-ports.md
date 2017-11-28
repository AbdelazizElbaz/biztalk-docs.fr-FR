---
title: "Étape 2 : Modifier ou créer l’envoi et Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61f201f8b20d5824b1b037cc61edaa1d64729135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-modify-or-create-the-send-and-receive-ports"></a><span data-ttu-id="a9b31-102">Étape 2 : Modifier ou créer l’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="a9b31-102">Step 2: Modify or Create the Send and Receive Ports</span></span>
<span data-ttu-id="a9b31-103">Vous avez besoin d’envoi de fichiers et les ports de réception pour le lot dans / Out didacticiel du lot.</span><span class="sxs-lookup"><span data-stu-id="a9b31-103">You need FILE send and receive ports for the Batch In/Batch Out tutorial.</span></span> <span data-ttu-id="a9b31-104">Si vous avez cliqué sur le **lancer le didacticiel** bouton à la fin de l’installation de l’édition Enterprise de [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] créé ces ports : un port d’envoi nommé Tutorial_BTAHL7Drop et un port de réception nommé Tutorial_BTAHL7PickUp.</span><span class="sxs-lookup"><span data-stu-id="a9b31-104">If you clicked the **Launch Tutorial** button at the end of installing the Enterprise Edition of [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] created these ports for you: a send port named Tutorial_BTAHL7Drop, and a receive port named Tutorial_BTAHL7PickUp.</span></span> <span data-ttu-id="a9b31-105">Si vous disposez de ces ports, vous devez modifier le port d’envoi Tutorial_BTAHL7Drop.</span><span class="sxs-lookup"><span data-stu-id="a9b31-105">If you have these ports, you still need to modify the send port Tutorial_BTAHL7Drop.</span></span>  
  
 <span data-ttu-id="a9b31-106">Si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation ne pas créer de l’envoi et ports de réception pour vous, consultez « Pour créer le BIBOTutorialPickup port de réception » la procédure dans cette rubrique et puis consultez « Pour créer le BIBOTutorialDrop port d’envoi » la procédure dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a9b31-106">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup did not create the send and receive ports for you, see "To create the BIBOTutorialPickup receive port" procedure in this topic, and then see "To create the BIBOTutorialDrop send port" procedure also in this topic.</span></span>  
  
### <a name="to-modify-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="a9b31-107">Pour modifier le port d’envoi Tutorial_BTAHL7Drop</span><span class="sxs-lookup"><span data-stu-id="a9b31-107">To modify the Tutorial_BTAHL7Drop send port</span></span>  
  
1.  <span data-ttu-id="a9b31-108">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-108">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a9b31-109">Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-109">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="a9b31-110">Cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-110">Click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a9b31-111">Dans l’arborescence de la console, cliquez sur **filtres**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-111">In the console tree, click **Filters**.</span></span>  
  
5.  <span data-ttu-id="a9b31-112">Dans le **filtres** volet, dans la deuxième ligne, sélectionnez **BTAHL7Schemas.MessageClass** pour **propriétés**, sélectionnez  **==**  pour **Opérateur**et le type **MessageClass2X** pour **valeur**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-112">In the **Filters** pane, in the second row, select **BTAHL7Schemas.MessageClass** for **Properties**, select **==** for **Operator**, and type **MessageClass2X** for **Value**.</span></span> <span data-ttu-id="a9b31-113">Cliquez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-113">Click **Enter**.</span></span>  
  
6.  <span data-ttu-id="a9b31-114">Définissez **regrouper par** sur la **BTS. ReceivePortName** à la ligne **ou**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-114">Set **Group By** on the **BTS.ReceivePortName** line to **Or**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a9b31-115">Dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fenêtre Administration, développez **paramètres de plateforme**, développez **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-115">In the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration window, expand **Platform Settings**, and expand **Host Instances**.</span></span> <span data-ttu-id="a9b31-116">Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-116">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9b31-117">Utilisez uniquement les procédures suivantes si vous avez installé l’Édition Standard de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], ou si vous n’avez pas cliqué sur le **lancer le didacticiel** bouton lorsque vous configurez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9b31-117">Only use the following procedures if you installed the Standard Edition of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], or if you did not click the **Launch Tutorial** button when you set up [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span>  
  
### <a name="to-create-the-tutorialbtahl7pickup-receive-port-and-location"></a><span data-ttu-id="a9b31-118">Pour créer le Tutorial_BTAHL7Pickup port de réception et emplacement</span><span class="sxs-lookup"><span data-stu-id="a9b31-118">To create the Tutorial_BTAHL7Pickup receive port and location</span></span>  
  
1.  <span data-ttu-id="a9b31-119">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-119">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a9b31-120">Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-120">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="a9b31-121">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="a9b31-122">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **Tutorial_BTAHL7PickUp**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-122">In the Receive Port Properties dialog box, in the **Name** box, type **Tutorial_BTAHL7PickUp**.</span></span>  
  
5.  <span data-ttu-id="a9b31-123">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="a9b31-124">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-124">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="a9b31-125">Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **Tutorial_BTAHL7PickUp**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-125">In the Select a Receive Port dialog box, click **Tutorial_BTAHL7PickUp**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="a9b31-126">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **Tutorial_FileReceiveLoc**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-126">In the Receive Location Properties dialog box, in the **Name** box, type **Tutorial_FileReceiveLoc**.</span></span>  
  
9. <span data-ttu-id="a9b31-127">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-127">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="a9b31-128">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="a9b31-128">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="a9b31-129">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9b31-129">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a9b31-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a9b31-130">Use this</span></span>|<span data-ttu-id="a9b31-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a9b31-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a9b31-132">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="a9b31-132">**Receive Folder**</span></span>|<span data-ttu-id="a9b31-133">Accédez à  **\<**  *lecteur***> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7PickUp** .</span><span class="sxs-lookup"><span data-stu-id="a9b31-133">Browse to **\<***drive***>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp**.</span></span> <span data-ttu-id="a9b31-134">**Remarque :** il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] prennent en charge le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9b31-134">**Note:**  This is the path to the location on the file system or public share from where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will pick up the file.</span></span>|  
    |<span data-ttu-id="a9b31-135">**Masque de fichier**</span><span class="sxs-lookup"><span data-stu-id="a9b31-135">**File mask**</span></span>|<span data-ttu-id="a9b31-136">Type  **\*.txt**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-136">Type **\*.txt**.</span></span>|  
  
12. <span data-ttu-id="a9b31-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-137">Click **OK**.</span></span>  
  
13. <span data-ttu-id="a9b31-138">Dans la boîte de dialogue Propriétés de l’emplacement de réception, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9b31-138">In the Receive Location Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a9b31-139">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a9b31-139">Use this</span></span>|<span data-ttu-id="a9b31-140">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a9b31-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a9b31-141">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="a9b31-141">**Receive Handler**</span></span>|<span data-ttu-id="a9b31-142">Conserver **BizTalkServerApplication** comme étant sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="a9b31-142">Keep **BizTalkServerApplication** as selected.</span></span>|  
    |<span data-ttu-id="a9b31-143">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="a9b31-143">**Receive Pipeline**</span></span>|<span data-ttu-id="a9b31-144">Sélectionnez **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-144">Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span></span>|  
  
14. <span data-ttu-id="a9b31-145">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-145">Click **OK**.</span></span>  
  
15. <span data-ttu-id="a9b31-146">Dans l’Explorateur BizTalk, cliquez sur **Tutorial_FileReceiveLoc**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-146">In BizTalk Explorer, right-click **Tutorial_FileReceiveLoc**, and then click **Enable**.</span></span>  
  
### <a name="to-create-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="a9b31-147">Pour créer le port d’envoi Tutorial_BTAHL7Drop</span><span class="sxs-lookup"><span data-stu-id="a9b31-147">To create the Tutorial_BTAHL7Drop send port</span></span>  
  
1.  <span data-ttu-id="a9b31-148">Dans le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-148">In the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="a9b31-149">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9b31-149">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a9b31-150">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a9b31-150">Use this</span></span>|<span data-ttu-id="a9b31-151">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a9b31-151">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a9b31-152">**Nom**</span><span class="sxs-lookup"><span data-stu-id="a9b31-152">**Name**</span></span>|<span data-ttu-id="a9b31-153">Type **Tutorial_BTAHL7Drop**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-153">Type **Tutorial_BTAHL7Drop**.</span></span>|  
    |<span data-ttu-id="a9b31-154">**Type**</span><span class="sxs-lookup"><span data-stu-id="a9b31-154">**Type**</span></span>|<span data-ttu-id="a9b31-155">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a9b31-155">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="a9b31-156">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="a9b31-156">**Configure**</span></span>|<span data-ttu-id="a9b31-157">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport FILE** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a9b31-157">Click **Configure** to open the **FILE Transport Properties** dialog box.</span></span>|  
  
3.  <span data-ttu-id="a9b31-158">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9b31-158">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a9b31-159">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a9b31-159">Use this</span></span>|<span data-ttu-id="a9b31-160">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a9b31-160">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a9b31-161">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="a9b31-161">**Destination folder**</span></span>|<span data-ttu-id="a9b31-162">Accédez à  **\<**  *lecteur***: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7Drop** .</span><span class="sxs-lookup"><span data-stu-id="a9b31-162">Browse to **\<***drive***:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop**.</span></span> <span data-ttu-id="a9b31-163">**Remarque :** le chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9b31-163">**Note:**  This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file.</span></span>|  
    |<span data-ttu-id="a9b31-164">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="a9b31-164">**File name**</span></span>|<span data-ttu-id="a9b31-165">Type **%MessageID%.txt** (Notez que l’extension est txt, xml pas).</span><span class="sxs-lookup"><span data-stu-id="a9b31-165">Type **%MessageID%.txt** (note that the extension is txt, not xml).</span></span>|  
  
4.  <span data-ttu-id="a9b31-166">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-166">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a9b31-167">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a9b31-167">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline** from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="a9b31-168">Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9b31-168">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="a9b31-169">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a9b31-169">Use this</span></span>|<span data-ttu-id="a9b31-170">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a9b31-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a9b31-171">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="a9b31-171">**Property**</span></span>|<span data-ttu-id="a9b31-172">Sélectionnez **BTS. ReceivePortName** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a9b31-172">Select **BTS.ReceivePortName** from the drop-down list.</span></span>|  
    |<span data-ttu-id="a9b31-173">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="a9b31-173">**Operator**</span></span>|<span data-ttu-id="a9b31-174">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="a9b31-174">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="a9b31-175">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="a9b31-175">**Value**</span></span>|<span data-ttu-id="a9b31-176">Type **Tutorial_BTAHL7PickUp**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-176">Type **Tutorial_BTAHL7PickUp**.</span></span>|  
    |<span data-ttu-id="a9b31-177">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="a9b31-177">**Group By**</span></span>|<span data-ttu-id="a9b31-178">Sélectionnez **ou** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a9b31-178">Select **Or** from the drop-down list.</span></span>|  
    |<span data-ttu-id="a9b31-179">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="a9b31-179">**Property**</span></span>|<span data-ttu-id="a9b31-180">Sélectionnez **BTAHL7Schemas.MessageClass**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-180">Select **BTAHL7Schemas.MessageClass**.</span></span>|  
    |<span data-ttu-id="a9b31-181">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="a9b31-181">**Operator**</span></span>|<span data-ttu-id="a9b31-182">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="a9b31-182">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="a9b31-183">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="a9b31-183">**Value**</span></span>|<span data-ttu-id="a9b31-184">Type **MessageClass2X**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-184">Type **MessageClass2X**.</span></span>|  
  
7.  <span data-ttu-id="a9b31-185">Cliquez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-185">Click **Enter**.</span></span> <span data-ttu-id="a9b31-186">Dans le volet du bas de la boîte de dialogue, vérifiez que l’expression de filtre est correcte.</span><span class="sxs-lookup"><span data-stu-id="a9b31-186">Verify in the pane at the bottom of the dialog box that the filter expression is correct.</span></span>  
  
8.  <span data-ttu-id="a9b31-187">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-187">Click **OK**.</span></span>  
  
9. <span data-ttu-id="a9b31-188">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-188">In the Administration Console, click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Start**.</span></span>  
  
10. <span data-ttu-id="a9b31-189">Développez **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-189">Expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="a9b31-190">Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="a9b31-190">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="a9b31-191">Passez à [étape 3 : tester le lot dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="a9b31-191">Proceed to [Step 3: Test the Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).</span></span>
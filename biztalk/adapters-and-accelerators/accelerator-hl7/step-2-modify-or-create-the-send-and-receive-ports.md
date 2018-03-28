---
title: 'Étape 2 : Modifier ou créer l’envoi et Ports de réception | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa94183f0eb83dc51fc0add22ba50484f7282fb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-2-modify-or-create-the-send-and-receive-ports"></a><span data-ttu-id="50528-102">Étape 2 : Modifier ou créer l’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="50528-102">Step 2: Modify or Create the Send and Receive Ports</span></span>
<span data-ttu-id="50528-103">Vous avez besoin d’envoi de fichiers et les ports de réception pour le lot dans / Out didacticiel du lot.</span><span class="sxs-lookup"><span data-stu-id="50528-103">You need FILE send and receive ports for the Batch In/Batch Out tutorial.</span></span> <span data-ttu-id="50528-104">Si vous avez cliqué sur le **lancer le didacticiel** bouton à la fin de l’installation de l’édition Enterprise de [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] créé ces ports : un port d’envoi nommé Tutorial_BTAHL7Drop et un port de réception nommé Tutorial_BTAHL7PickUp.</span><span class="sxs-lookup"><span data-stu-id="50528-104">If you clicked the **Launch Tutorial** button at the end of installing the Enterprise Edition of [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] created these ports for you: a send port named Tutorial_BTAHL7Drop, and a receive port named Tutorial_BTAHL7PickUp.</span></span> <span data-ttu-id="50528-105">Si vous disposez de ces ports, vous devez modifier le port d’envoi Tutorial_BTAHL7Drop.</span><span class="sxs-lookup"><span data-stu-id="50528-105">If you have these ports, you still need to modify the send port Tutorial_BTAHL7Drop.</span></span>  
  
 <span data-ttu-id="50528-106">Si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation ne pas créer de l’envoi et ports de réception pour vous, consultez « Pour créer le BIBOTutorialPickup port de réception » la procédure dans cette rubrique et puis consultez « Pour créer le BIBOTutorialDrop port d’envoi » la procédure dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="50528-106">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup did not create the send and receive ports for you, see "To create the BIBOTutorialPickup receive port" procedure in this topic, and then see "To create the BIBOTutorialDrop send port" procedure also in this topic.</span></span>  
  
### <a name="to-modify-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="50528-107">Pour modifier le port d’envoi Tutorial_BTAHL7Drop</span><span class="sxs-lookup"><span data-stu-id="50528-107">To modify the Tutorial_BTAHL7Drop send port</span></span>  
  
1.  <span data-ttu-id="50528-108">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="50528-108">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="50528-109">Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="50528-109">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="50528-110">Cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="50528-110">Click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="50528-111">Dans l’arborescence de la console, cliquez sur **filtres**.</span><span class="sxs-lookup"><span data-stu-id="50528-111">In the console tree, click **Filters**.</span></span>  
  
5.  <span data-ttu-id="50528-112">Dans le **filtres** volet, dans la deuxième ligne, sélectionnez **BTAHL7Schemas.MessageClass** pour **propriétés**, sélectionnez **==** pour **Opérateur**et le type **MessageClass2X** pour **valeur**.</span><span class="sxs-lookup"><span data-stu-id="50528-112">In the **Filters** pane, in the second row, select **BTAHL7Schemas.MessageClass** for **Properties**, select **==** for **Operator**, and type **MessageClass2X** for **Value**.</span></span> <span data-ttu-id="50528-113">Cliquez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="50528-113">Click **Enter**.</span></span>  
  
6.  <span data-ttu-id="50528-114">Définissez **regrouper par** sur la **BTS. ReceivePortName** à la ligne **ou**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-114">Set **Group By** on the **BTS.ReceivePortName** line to **Or**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="50528-115">Dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fenêtre Administration, développez **paramètres de plateforme**, développez **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="50528-115">In the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration window, expand **Platform Settings**, and expand **Host Instances**.</span></span> <span data-ttu-id="50528-116">Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="50528-116">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50528-117">Utilisez uniquement les procédures suivantes si vous avez installé l’Édition Standard de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], ou si vous n’avez pas cliqué sur le **lancer le didacticiel** bouton lorsque vous configurez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50528-117">Only use the following procedures if you installed the Standard Edition of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], or if you did not click the **Launch Tutorial** button when you set up [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span>  
  
### <a name="to-create-the-tutorialbtahl7pickup-receive-port-and-location"></a><span data-ttu-id="50528-118">Pour créer le Tutorial_BTAHL7Pickup port de réception et emplacement</span><span class="sxs-lookup"><span data-stu-id="50528-118">To create the Tutorial_BTAHL7Pickup receive port and location</span></span>  
  
1.  <span data-ttu-id="50528-119">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="50528-119">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="50528-120">Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="50528-120">In the Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="50528-121">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="50528-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="50528-122">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **Tutorial_BTAHL7PickUp**.</span><span class="sxs-lookup"><span data-stu-id="50528-122">In the Receive Port Properties dialog box, in the **Name** box, type **Tutorial_BTAHL7PickUp**.</span></span>  
  
5.  <span data-ttu-id="50528-123">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="50528-124">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="50528-124">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="50528-125">Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **Tutorial_BTAHL7PickUp**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-125">In the Select a Receive Port dialog box, click **Tutorial_BTAHL7PickUp**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="50528-126">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **Tutorial_FileReceiveLoc**.</span><span class="sxs-lookup"><span data-stu-id="50528-126">In the Receive Location Properties dialog box, in the **Name** box, type **Tutorial_FileReceiveLoc**.</span></span>  
  
9. <span data-ttu-id="50528-127">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="50528-127">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="50528-128">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="50528-128">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="50528-129">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50528-129">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="50528-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="50528-130">Use this</span></span>|<span data-ttu-id="50528-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="50528-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="50528-132">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="50528-132">**Receive Folder**</span></span>|<span data-ttu-id="50528-133">Accédez à  **\< ***lecteur***\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7PickUp**.</span><span class="sxs-lookup"><span data-stu-id="50528-133">Browse to **\<***drive***\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp**.</span></span> <span data-ttu-id="50528-134">**Remarque :** il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] prennent en charge le fichier.</span><span class="sxs-lookup"><span data-stu-id="50528-134">**Note:**  This is the path to the location on the file system or public share from where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will pick up the file.</span></span>|  
    |<span data-ttu-id="50528-135">**Masque de fichier**</span><span class="sxs-lookup"><span data-stu-id="50528-135">**File mask**</span></span>|<span data-ttu-id="50528-136">Type  **\*.txt**.</span><span class="sxs-lookup"><span data-stu-id="50528-136">Type **\*.txt**.</span></span>|  
  
12. <span data-ttu-id="50528-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-137">Click **OK**.</span></span>  
  
13. <span data-ttu-id="50528-138">Dans la boîte de dialogue Propriétés de l’emplacement de réception, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50528-138">In the Receive Location Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="50528-139">Utiliser</span><span class="sxs-lookup"><span data-stu-id="50528-139">Use this</span></span>|<span data-ttu-id="50528-140">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="50528-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="50528-141">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="50528-141">**Receive Handler**</span></span>|<span data-ttu-id="50528-142">Conserver **BizTalkServerApplication** comme étant sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="50528-142">Keep **BizTalkServerApplication** as selected.</span></span>|  
    |<span data-ttu-id="50528-143">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="50528-143">**Receive Pipeline**</span></span>|<span data-ttu-id="50528-144">Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span><span class="sxs-lookup"><span data-stu-id="50528-144">Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span></span>|  
  
14. <span data-ttu-id="50528-145">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-145">Click **OK**.</span></span>  
  
15. <span data-ttu-id="50528-146">Dans l’Explorateur BizTalk, cliquez sur **Tutorial_FileReceiveLoc**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="50528-146">In BizTalk Explorer, right-click **Tutorial_FileReceiveLoc**, and then click **Enable**.</span></span>  
  
### <a name="to-create-the-tutorialbtahl7drop-send-port"></a><span data-ttu-id="50528-147">Pour créer le port d’envoi Tutorial_BTAHL7Drop</span><span class="sxs-lookup"><span data-stu-id="50528-147">To create the Tutorial_BTAHL7Drop send port</span></span>  
  
1.  <span data-ttu-id="50528-148">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="50528-148">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="50528-149">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50528-149">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="50528-150">Utiliser</span><span class="sxs-lookup"><span data-stu-id="50528-150">Use this</span></span>|<span data-ttu-id="50528-151">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="50528-151">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="50528-152">**Nom**</span><span class="sxs-lookup"><span data-stu-id="50528-152">**Name**</span></span>|<span data-ttu-id="50528-153">Type **Tutorial_BTAHL7Drop**.</span><span class="sxs-lookup"><span data-stu-id="50528-153">Type **Tutorial_BTAHL7Drop**.</span></span>|  
    |<span data-ttu-id="50528-154">**Type**</span><span class="sxs-lookup"><span data-stu-id="50528-154">**Type**</span></span>|<span data-ttu-id="50528-155">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50528-155">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="50528-156">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="50528-156">**Configure**</span></span>|<span data-ttu-id="50528-157">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport FILE** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="50528-157">Click **Configure** to open the **FILE Transport Properties** dialog box.</span></span>|  
  
3.  <span data-ttu-id="50528-158">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50528-158">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="50528-159">Utiliser</span><span class="sxs-lookup"><span data-stu-id="50528-159">Use this</span></span>|<span data-ttu-id="50528-160">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="50528-160">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="50528-161">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="50528-161">**Destination folder**</span></span>|<span data-ttu-id="50528-162">Accédez à  **\< ***lecteur***:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7Drop**.</span><span class="sxs-lookup"><span data-stu-id="50528-162">Browse to **\<***drive***:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop**.</span></span> <span data-ttu-id="50528-163">**Remarque :** le chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier.</span><span class="sxs-lookup"><span data-stu-id="50528-163">**Note:**  This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file.</span></span>|  
    |<span data-ttu-id="50528-164">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="50528-164">**File name**</span></span>|<span data-ttu-id="50528-165">Type **%MessageID%.txt** (Notez que l’extension est txt, xml pas).</span><span class="sxs-lookup"><span data-stu-id="50528-165">Type **%MessageID%.txt** (note that the extension is txt, not xml).</span></span>|  
  
4.  <span data-ttu-id="50528-166">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-166">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="50528-167">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50528-167">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline** from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="50528-168">Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50528-168">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="50528-169">Utiliser</span><span class="sxs-lookup"><span data-stu-id="50528-169">Use this</span></span>|<span data-ttu-id="50528-170">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="50528-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="50528-171">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="50528-171">**Property**</span></span>|<span data-ttu-id="50528-172">Sélectionnez **BTS. ReceivePortName** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50528-172">Select **BTS.ReceivePortName** from the drop-down list.</span></span>|  
    |<span data-ttu-id="50528-173">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="50528-173">**Operator**</span></span>|<span data-ttu-id="50528-174">Laissez **==** comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="50528-174">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="50528-175">**Value**</span><span class="sxs-lookup"><span data-stu-id="50528-175">**Value**</span></span>|<span data-ttu-id="50528-176">Type **Tutorial_BTAHL7PickUp**.</span><span class="sxs-lookup"><span data-stu-id="50528-176">Type **Tutorial_BTAHL7PickUp**.</span></span>|  
    |<span data-ttu-id="50528-177">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="50528-177">**Group By**</span></span>|<span data-ttu-id="50528-178">Sélectionnez **ou** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50528-178">Select **Or** from the drop-down list.</span></span>|  
    |<span data-ttu-id="50528-179">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="50528-179">**Property**</span></span>|<span data-ttu-id="50528-180">Sélectionnez **BTAHL7Schemas.MessageClass**.</span><span class="sxs-lookup"><span data-stu-id="50528-180">Select **BTAHL7Schemas.MessageClass**.</span></span>|  
    |<span data-ttu-id="50528-181">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="50528-181">**Operator**</span></span>|<span data-ttu-id="50528-182">Laissez **==** comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="50528-182">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="50528-183">**Value**</span><span class="sxs-lookup"><span data-stu-id="50528-183">**Value**</span></span>|<span data-ttu-id="50528-184">Type **MessageClass2X**.</span><span class="sxs-lookup"><span data-stu-id="50528-184">Type **MessageClass2X**.</span></span>|  
  
7.  <span data-ttu-id="50528-185">Cliquez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="50528-185">Click **Enter**.</span></span> <span data-ttu-id="50528-186">Dans le volet du bas de la boîte de dialogue, vérifiez que l’expression de filtre est correcte.</span><span class="sxs-lookup"><span data-stu-id="50528-186">Verify in the pane at the bottom of the dialog box that the filter expression is correct.</span></span>  
  
8.  <span data-ttu-id="50528-187">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50528-187">Click **OK**.</span></span>  
  
9. <span data-ttu-id="50528-188">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="50528-188">In the Administration Console, click **Send Ports**, right-click **Tutorial_BTAHL7Drop**, and then click **Start**.</span></span>  
  
10. <span data-ttu-id="50528-189">Développez **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="50528-189">Expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="50528-190">Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="50528-190">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="50528-191">Passez à [étape 3 : tester le lot dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="50528-191">Proceed to [Step 3: Test the Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).</span></span>
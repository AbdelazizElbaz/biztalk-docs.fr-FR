---
title: "Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: 66c4b524-c8ff-43b5-9c44-6d7bc759ae2c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c25a348fb739f4558f1507eda0d46d209cd44c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-the-adta03-message-to-the-rx-system-using-the-file-adapter"></a><span data-ttu-id="35c57-102">Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="35c57-102">Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter</span></span>
<span data-ttu-id="35c57-103">Dans cette étape, vous créez le port d’envoi pour le système pharmacie (RX) à l’aide de l’adaptateur File.</span><span class="sxs-lookup"><span data-stu-id="35c57-103">In this step, you create the send port for the Pharmacy System (RX) using the File adapter.</span></span>  
  
### <a name="to-create-the-tutorialsendmsgrx-send-port"></a><span data-ttu-id="35c57-104">Pour créer le port d’envoi Tutorial_sendMsg_RX</span><span class="sxs-lookup"><span data-stu-id="35c57-104">To create the Tutorial_sendMsg_RX send port</span></span>  
  
1.  <span data-ttu-id="35c57-105">Dans le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="35c57-105">In the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="35c57-106">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, effectuez les actions suivantes, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="35c57-106">In the **Send Port Properties** dialog box, do the following actions and then click **OK**.</span></span>  
  
    |<span data-ttu-id="35c57-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="35c57-107">Use this</span></span>|<span data-ttu-id="35c57-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="35c57-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="35c57-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="35c57-109">**Name**</span></span>|<span data-ttu-id="35c57-110">Type **Tutorial_sendMsg_RX**.</span><span class="sxs-lookup"><span data-stu-id="35c57-110">Type **Tutorial_sendMsg_RX**.</span></span>|  
    |<span data-ttu-id="35c57-111">**Type de transport**</span><span class="sxs-lookup"><span data-stu-id="35c57-111">**Transport type**</span></span>|<span data-ttu-id="35c57-112">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-112">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-113">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="35c57-113">**Configure**</span></span>|<span data-ttu-id="35c57-114">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="35c57-114">Click **Configure** to open the **File Transport Properties** dialog box.</span></span>|  
  
3.  <span data-ttu-id="35c57-115">Dans la boîte de dialogue Propriétés du Transport FILE, effectuez les actions suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="35c57-115">In the FILE Transport Properties dialog box, do the following actions and then click **OK**.</span></span>  
  
    |<span data-ttu-id="35c57-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="35c57-116">Use this</span></span>|<span data-ttu-id="35c57-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="35c57-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="35c57-118">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="35c57-118">**Destination folder**</span></span>|<span data-ttu-id="35c57-119">Accédez à  **\<**  *lecteur***: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendMsg_RX** .</span><span class="sxs-lookup"><span data-stu-id="35c57-119">Browse to **\<***drive***:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX**.</span></span>|  
    |<span data-ttu-id="35c57-120">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="35c57-120">**File name**</span></span>|<span data-ttu-id="35c57-121">Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).</span><span class="sxs-lookup"><span data-stu-id="35c57-121">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
  
4.  <span data-ttu-id="35c57-122">Dans le **propriétés de Port d’envoi** boîte de dialogue, pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="35c57-122">In the **Send Port Properties** dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="35c57-123">Dans le volet gauche, sélectionnez **filtres**, puis effectuez les actions suivantes.</span><span class="sxs-lookup"><span data-stu-id="35c57-123">In the left pane, select **Filters**, and then do the following actions.</span></span> <span data-ttu-id="35c57-124">Pour continuer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="35c57-124">Click **OK** to continue.</span></span>  
  
    |<span data-ttu-id="35c57-125">Utiliser</span><span class="sxs-lookup"><span data-stu-id="35c57-125">Use this</span></span>|<span data-ttu-id="35c57-126">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="35c57-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="35c57-127">**Propriété** (première ligne)</span><span class="sxs-lookup"><span data-stu-id="35c57-127">**Property** (first line)</span></span>|<span data-ttu-id="35c57-128">Sélectionnez **BTS. MessageType** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-128">Select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-129">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="35c57-129">**Operator**</span></span>|<span data-ttu-id="35c57-130">Sélectionnez **! =** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-130">Select **!=** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-131">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="35c57-131">**Value**</span></span>|<span data-ttu-id="35c57-132">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="35c57-132">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="35c57-133">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="35c57-133">**Group By**</span></span>|<span data-ttu-id="35c57-134">Sélectionnez **ou** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-134">Select **OR** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-135">**Propriété** (deuxième ligne)</span><span class="sxs-lookup"><span data-stu-id="35c57-135">**Property** (second line)</span></span>|<span data-ttu-id="35c57-136">Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-136">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-137">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="35c57-137">**Operator**</span></span>|<span data-ttu-id="35c57-138">Sélectionnez **! =** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-138">Select **!=** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-139">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="35c57-139">**Value**</span></span>|<span data-ttu-id="35c57-140">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span><span class="sxs-lookup"><span data-stu-id="35c57-140">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span></span>|  
    |<span data-ttu-id="35c57-141">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="35c57-141">**Group By**</span></span>|<span data-ttu-id="35c57-142">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-142">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-143">**Propriété** ((troisième ligne)</span><span class="sxs-lookup"><span data-stu-id="35c57-143">**Property** (third line)</span></span>|<span data-ttu-id="35c57-144">Sélectionnez **BTAHL7Schemas.MSH3_1**.</span><span class="sxs-lookup"><span data-stu-id="35c57-144">Select **BTAHL7Schemas.MSH3_1**.</span></span>|  
    |<span data-ttu-id="35c57-145">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="35c57-145">**Operator**</span></span>|<span data-ttu-id="35c57-146">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="35c57-146">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="35c57-147">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="35c57-147">**Value**</span></span>|<span data-ttu-id="35c57-148">Type **Tutorial_ADTSystem**.</span><span class="sxs-lookup"><span data-stu-id="35c57-148">Type **Tutorial_ADTSystem**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="35c57-149">Le premier filtre signifie que le système d’informations hôpital (HIS) s’abonnant à un message, pas un accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="35c57-149">The first filter means that the Hospital Information System (HIS) is subscribing to a message, not an acknowledgment.</span></span> <span data-ttu-id="35c57-150">Le deuxième filtre signifie que son s’abonne aux messages dont la source est la décharge d’admission et le système de transfert (ADT).</span><span class="sxs-lookup"><span data-stu-id="35c57-150">The second filter means that HIS is subscribing to messages whose source is the Admissions Discharge and Transfer (ADT) System.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35c57-151">BTAHL7 dépose le message à l’emplacement de dépôt du fichier \< *lecteur*> : programme FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd en bout TutorialTutorial_sendMsg_RX.</span><span class="sxs-lookup"><span data-stu-id="35c57-151">BTAHL7 drops the message at the file drop location \<*drive*>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendMsg_RX.</span></span>  
  
6.  <span data-ttu-id="35c57-152">Cliquez sur **appliquer**, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="35c57-152">Click **Apply**, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="35c57-153">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_sendMsg_RX**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="35c57-153">In the Administration Console, click **Send Ports**, right-click **Tutorial_sendMsg_RX**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="35c57-154">Passez à [étape 7 : créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="35c57-154">Proceed to [Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md).</span></span>
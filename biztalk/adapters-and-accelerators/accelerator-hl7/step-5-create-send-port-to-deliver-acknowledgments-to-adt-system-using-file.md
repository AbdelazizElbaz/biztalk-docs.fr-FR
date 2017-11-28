---
title: "Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 926a13d443e7002a71e2b9f6509c3a377f0af0be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-send-port-to-deliver-acknowledgments-to-the-adt-system-using-the-file-adapter"></a><span data-ttu-id="f391f-102">Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="f391f-102">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>
<span data-ttu-id="f391f-103">Dans cette étape, vous créez le port d’envoi pour générer des accusés de réception à l’aide de l’adaptateur File.</span><span class="sxs-lookup"><span data-stu-id="f391f-103">In this step, you create the send port to generate acknowledgments using the File adapter.</span></span>  
  
### <a name="to-create-the-tutorialsendackadt-send-port"></a><span data-ttu-id="f391f-104">Pour créer le port d’envoi Tutorial_sendAck_ADT</span><span class="sxs-lookup"><span data-stu-id="f391f-104">To create the Tutorial_sendAck_ADT send port</span></span>  
  
1.  <span data-ttu-id="f391f-105">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, créer le \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendAck_ADT dossier.</span><span class="sxs-lookup"><span data-stu-id="f391f-105">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, create the \<*drive*:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT folder.</span></span>  
  
2.  <span data-ttu-id="f391f-106">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f391f-106">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="f391f-107">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f391f-107">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f391f-108">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f391f-108">Use this</span></span>|<span data-ttu-id="f391f-109">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f391f-109">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f391f-110">**Nom**</span><span class="sxs-lookup"><span data-stu-id="f391f-110">**Name**</span></span>|<span data-ttu-id="f391f-111">Type **Tutorial_sendAck_ADT**.</span><span class="sxs-lookup"><span data-stu-id="f391f-111">Type **Tutorial_sendAck_ADT**.</span></span>|  
    |<span data-ttu-id="f391f-112">**Type de transport**</span><span class="sxs-lookup"><span data-stu-id="f391f-112">**Transport type**</span></span>|<span data-ttu-id="f391f-113">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-113">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-114">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="f391f-114">**Configure**</span></span>|<span data-ttu-id="f391f-115">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f391f-115">Click **Configure** to open the **File Transport Properties** dialog box.</span></span>|  
  
4.  <span data-ttu-id="f391f-116">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="f391f-116">In the FILE Transport Properties dialog box, do the following and then click **OK**.</span></span>  
  
    |<span data-ttu-id="f391f-117">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f391f-117">Use this</span></span>|<span data-ttu-id="f391f-118">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f391f-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f391f-119">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="f391f-119">**Destination folder**</span></span>|<span data-ttu-id="f391f-120">Accédez à  **\<**  *lecteur***: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendAck_ADT** .</span><span class="sxs-lookup"><span data-stu-id="f391f-120">Browse to **\<***drive***:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT**.</span></span>|  
    |<span data-ttu-id="f391f-121">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="f391f-121">**File name**</span></span>|<span data-ttu-id="f391f-122">Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).</span><span class="sxs-lookup"><span data-stu-id="f391f-122">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
  
5.  <span data-ttu-id="f391f-123">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="f391f-123">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="f391f-124">Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f391f-124">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f391f-125">Le premier filtre signifie que vous vous abonnez pour le message d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="f391f-125">The first filter means that you are subscribing for the acknowledgment message.</span></span> <span data-ttu-id="f391f-126">Le deuxième filtre signifie que vous vous abonnez à l’accusé de réception vers le serveur de publication Tutorial_ADTSystem.</span><span class="sxs-lookup"><span data-stu-id="f391f-126">The second filter means that you are subscribing to the acknowledgment that is destined for the publisher Tutorial_ADTSystem.</span></span>  
  
     <span data-ttu-id="f391f-127">Cliquez sur **OK** lorsque vous êtes prêt à continuer.</span><span class="sxs-lookup"><span data-stu-id="f391f-127">Click **OK** when you are ready to continue.</span></span>  
  
    |<span data-ttu-id="f391f-128">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f391f-128">Use this</span></span>|<span data-ttu-id="f391f-129">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f391f-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f391f-130">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="f391f-130">**Property**</span></span>|<span data-ttu-id="f391f-131">Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-131">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-132">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="f391f-132">**Operator**</span></span>|<span data-ttu-id="f391f-133">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-133">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-134">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="f391f-134">**Value**</span></span>|<span data-ttu-id="f391f-135">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="f391f-135">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="f391f-136">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="f391f-136">**Group By**</span></span>|<span data-ttu-id="f391f-137">Sélectionnez **ou** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-137">Select **OR** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-138">**Propriété (deuxième ligne)**</span><span class="sxs-lookup"><span data-stu-id="f391f-138">**Property (second line)**</span></span>|<span data-ttu-id="f391f-139">Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-139">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-140">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="f391f-140">**Operator**</span></span>|<span data-ttu-id="f391f-141">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-141">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-142">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="f391f-142">**Value**</span></span>|<span data-ttu-id="f391f-143">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span><span class="sxs-lookup"><span data-stu-id="f391f-143">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span></span>|  
    |<span data-ttu-id="f391f-144">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="f391f-144">**Group By**</span></span>|<span data-ttu-id="f391f-145">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-145">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-146">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="f391f-146">**Property**</span></span>|<span data-ttu-id="f391f-147">Dans la première propriété, cliquez sur la zone vierge, puis **BTAHL7Schemas.MSH5_1**.</span><span class="sxs-lookup"><span data-stu-id="f391f-147">Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**.</span></span>|  
    |<span data-ttu-id="f391f-148">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="f391f-148">**Operator**</span></span>|<span data-ttu-id="f391f-149">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f391f-149">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="f391f-150">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="f391f-150">**Value**</span></span>|<span data-ttu-id="f391f-151">Type **Tutorial_ADTSystem**.</span><span class="sxs-lookup"><span data-stu-id="f391f-151">Type **Tutorial_ADTSystem**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="f391f-152">Pour le port d’envoi Tutorial_sendAck_ADT BTAHL7 supprime les accusés de réception à l’emplacement de dépôt du fichier \< *lecteur*> : programme FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd en bout TutorialTutorial _sendAck_ADT.</span><span class="sxs-lookup"><span data-stu-id="f391f-152">For the send port Tutorial_sendAck_ADT, BTAHL7 drops the acknowledgments at the file drop location \<*drive*>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendAck_ADT.</span></span>  
  
7.  <span data-ttu-id="f391f-153">Cliquez sur **appliquer**, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="f391f-153">Click **Apply**, and then click **OK.**</span></span>  
  
8.  <span data-ttu-id="f391f-154">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_sendAck_ADT**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f391f-154">In the Administration Console, click **Send Ports**, right-click **Tutorial_sendAck_ADT**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="f391f-155">Passez à [étape 6 : créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md).</span><span class="sxs-lookup"><span data-stu-id="f391f-155">Proceed to [Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md).</span></span>
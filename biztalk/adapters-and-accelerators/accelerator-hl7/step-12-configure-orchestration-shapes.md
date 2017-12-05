---
title: "Étape 12 : Configurer les formes d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, orchestration shapes
- orchestrations, shapes
- message enrichment tutorial, orchestrations
ms.assetid: 9388254b-2841-4489-838e-de913ceff151
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f21c373aacc949b95588c66f1243936b15ea9e89
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-12-configure-orchestration-shapes"></a><span data-ttu-id="e82ec-102">Étape 12 : Configurer les formes d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="e82ec-102">Step 12: Configure Orchestration Shapes</span></span>
<span data-ttu-id="e82ec-103">Dans cette étape, vous terminez la configuration des formes d’orchestration afin de supprimer les balises actives de configuration insuffisante.</span><span class="sxs-lookup"><span data-stu-id="e82ec-103">In this step, you complete the configuration of the orchestration shapes in order to remove the insufficient configuration smart tags.</span></span> <span data-ttu-id="e82ec-104">Vous désignez **DoorbellOutputMessage** en tant que la sortie du premier processus de transformation, la désignation **DoorbellMap.btm** en tant que le mappage utilisé dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="e82ec-104">You designate **DoorbellOutputMessage** as the output of the first transform process, designating **DoorbellMap.btm** as the map used in that process.</span></span> <span data-ttu-id="e82ec-105">Vous désignez puis **DoorbellFinalMessage** en tant que la sortie du deuxième transformer les processus et ajoutez l’expression qui enrichit le message avec les données des champs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e82ec-105">You then designate **DoorbellFinalMessage** as the output of the second transform process, and add the expression that enriches the message with additional field data.</span></span>  
  
 <span data-ttu-id="e82ec-106">**Condition préalable :** [l’article 941261](http://support.microsoft.com/kb/941261) doivent être appliquées avant de définir la Configuration de l’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="e82ec-106">**Prerequisite:** [KB article 941261](http://support.microsoft.com/kb/941261) must be applied before setting up Orchestration Configuration.</span></span>  
  
### <a name="to-configure-orchestration-shapes"></a><span data-ttu-id="e82ec-107">Pour configurer les formes d’orchestration</span><span class="sxs-lookup"><span data-stu-id="e82ec-107">To configure orchestration shapes</span></span>  
  
1.  <span data-ttu-id="e82ec-108">Sur la surface en mode Design d’orchestration de Visual Studio, cliquez sur le **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="e82ec-108">On the orchestration Design view surface of Visual Studio, click the **ConstructMessage_1** shape.</span></span>  
  
2.  <span data-ttu-id="e82ec-109">Dans le **propriétés** fenêtre, cliquez sur le **Messages construits** propriété, sélectionnez **DoorbellOutputMessage** dans la liste déroulante, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="e82ec-109">In the **Properties** window, click the **Messages Constructed** property, select **DoorbellOutputMessage** from the drop-down list, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="e82ec-110">Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellTransform** mettre en forme à l’intérieur de la **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="e82ec-110">On the orchestration Design view surface, click the **DoorbellTransform** shape inside of the **ConstructMessage_1** shape.</span></span> <span data-ttu-id="e82ec-111">Dans le **propriétés** fenêtre, cliquez sur **nom de mappage**, puis cliquez sur le bouton de sélection (...) dans le champ d’attribut.</span><span class="sxs-lookup"><span data-stu-id="e82ec-111">In the **Properties** window, click **Map Name**, and then click the ellipsis (…) button in the attribute field.</span></span>  
  
4.  <span data-ttu-id="e82ec-112">Dans la boîte de dialogue, sélectionnez **mappage existant**.</span><span class="sxs-lookup"><span data-stu-id="e82ec-112">In the Transform Configuration dialog box, select **Existing Map**.</span></span> <span data-ttu-id="e82ec-113">Dans le **nom de mappage complet** la liste déroulante, cliquez sur **BTAHL7_Project.DoorbellMap**.</span><span class="sxs-lookup"><span data-stu-id="e82ec-113">In the **Fully Qualified Map Name** drop-down list, click **BTAHL7_Project.DoorbellMap**.</span></span>  
  
5.  <span data-ttu-id="e82ec-114">Cliquez sur **Source** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="e82ec-114">Click **Source** in the left pane.</span></span>  
  
6.  <span data-ttu-id="e82ec-115">Cliquez sur la zone vide sous **nom de la Variable** et cliquez sur **DoorBellInputMessage** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e82ec-115">Click the empty box under **Variable Name** and click **DoorBellInputMessage** from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="e82ec-116">Cliquez sur **Destination** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="e82ec-116">Click **Destination** in the left pane.</span></span>  
  
8.  <span data-ttu-id="e82ec-117">Cliquez sur la zone vide sous **nom de la Variable** et cliquez sur **DoorbellOutputMessage** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e82ec-117">Click the empty box under **Variable Name** and click **DoorbellOutputMessage** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="e82ec-118">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="e82ec-118">Click **OK** to save changes.</span></span>  
  
10. <span data-ttu-id="e82ec-119">Sur la surface en mode Design d’orchestration, cliquez sur le **ConstructMessage_2** forme.</span><span class="sxs-lookup"><span data-stu-id="e82ec-119">On the orchestration Design view surface, click the **ConstructMessage_2** shape.</span></span>  
  
11. <span data-ttu-id="e82ec-120">Dans le **propriétés** fenêtre, cliquez sur **Messages construits**, sélectionnez **DoorbellFinalMessage** dans la liste déroulante, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e82ec-120">In the **Properties** window, click **Messages Constructed**, select **DoorbellFinalMessage** from the drop-down list, and then press **Enter**.</span></span>  
  
12. <span data-ttu-id="e82ec-121">Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellFinalTransform** mettre en forme à l’intérieur de la **ConstructMessage_2** forme.</span><span class="sxs-lookup"><span data-stu-id="e82ec-121">On the orchestration Design view surface, click the **DoorbellFinalTransform** shape inside of the **ConstructMessage_2** shape.</span></span> <span data-ttu-id="e82ec-122">Dans le **propriétés** fenêtre, cliquez sur **Expression**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e82ec-122">In the **Properties** window, click **Expression**, and then click the ellipsis (…) button to open BizTalk Expression Editor.</span></span>  
  
13. <span data-ttu-id="e82ec-123">Dans Éditeur d’Expression BizTalk, cliquez dans le champ de texte et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="e82ec-123">In BizTalk Expression Editor, click in the text field and paste the following text:</span></span>  
  
    ```  
    HeaderInfo = new System.Xml.XmlDocument();   
    HeaderInfo.LoadXml("<ns0:MSH_25_GLO_DEF xmlns:ns0=\"http://microsoft.com/HealthCare/HL7/2X\">  
        <MSH><MSH.2_EncodingCharacters>^~\\&</MSH.2_EncodingCharacters><MSH.3_SendingApplication>  
        <HD.0_NamespaceId>SrcApp</HD.0_NamespaceId><HD.1_UniversalId>SrcAppUid</HD.1_UniversalId>  
        </MSH.3_SendingApplication><MSH.4_SendingFacility><HD.0_NamespaceId>srcFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>srcFacUid</HD.1_UniversalId></MSH.4_SendingFacility><MSH.5_ReceivingApplication>  
        <HD.0_NamespaceId>dstApp</HD.0_NamespaceId><HD.1_UniversalId>dstAppUid</HD.1_UniversalId>  
        </MSH.5_ReceivingApplication><MSH.6_ReceivingFacility><HD.0_NamespaceId>dstFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>dstFacUid</HD.1_UniversalId></MSH.6_ReceivingFacility><MSH.7_DateTimeOfMessage>  
        <TS.1>200307092343</TS.1></MSH.7_DateTimeOfMessage><MSH.8_Security>sec</MSH.8_Security>  
        <MSH.9_MessageType><CM_MSG.0_MessageType>ADT</CM_MSG.0_MessageType>  
        <CM_MSG.1_TriggerEvent>A04</CM_MSG.1_TriggerEvent></MSH.9_MessageType>  
        <MSH.10_MessageControlId>msgid2134</MSH.10_MessageControlId><MSH.11_ProcessingId>  
        <PT.0_ProcessingId>P</PT.0_ProcessingId></MSH.11_ProcessingId><MSH.12_VersionId>  
       <VID_0_VersionId>2.2</VID_0_VersionId></MSH.12_VersionId></MSH></ns0:MSH_25_GLO_DEF>");  
  
    DoorbellFinalMessage.MSHSegment = HeaderInfo;  
    DoorbellFinalMessage.BodySegments = DoorbellOutputMessage;  
    DoorbellFinalMessage.ZSegments = "";  
  
    DoorbellFinalMessage(BTAHL7Schemas.MSH1) = 124;   
    DoorbellFinalMessage(BTAHL7Schemas.MessageEncoding) = 65001;  
    DoorbellFinalMessage(BTAHL7Schemas.MSH2) = "^~\\&";  
    DoorbellFinalMessage(BTAHL7Schemas.ParseError) = false;   
    DoorbellFinalMessage(BTAHL7Schemas.ZPartPresent) = false;  
    DoorbellFinalMessage(BTAHL7Schemas.SegmentDelimiter2Char) = true;  
  
    ```  
  
14. <span data-ttu-id="e82ec-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e82ec-124">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e82ec-125">Dans l’expression « HeaderInfo.LoadXml », supprimez les retours chariot et les espaces dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="e82ec-125">In the "HeaderInfo.LoadXml" expression, delete the carriage returns and spaces within the expression.</span></span> <span data-ttu-id="e82ec-126">L’instruction « HeaderInfo.LoadXml » doit être sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e82ec-126">The "HeaderInfo.LoadXml" statement should be on one line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e82ec-127">Le premier bloc de texte précédent est un exemple d’un en-tête XML codé en dur.</span><span class="sxs-lookup"><span data-stu-id="e82ec-127">The first block of the preceding text is an example of a hard-coded XML header.</span></span> <span data-ttu-id="e82ec-128">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur nécessite un segment d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="e82ec-128">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a header segment.</span></span> <span data-ttu-id="e82ec-129">Vous pouvez personnaliser ces valeurs d’en-tête en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="e82ec-129">You can customize these header values according to the needs of your environment.</span></span> <span data-ttu-id="e82ec-130">Le deuxième bloc de texte précédent définit les trois parties de message requis dans un message à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="e82ec-130">The second block of the preceding text defines the three message parts required in a multipart message.</span></span> <span data-ttu-id="e82ec-131">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur nécessite un message à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="e82ec-131">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a multipart message.</span></span> <span data-ttu-id="e82ec-132">Le troisième bloc du texte précédent contient les propriétés promues qui le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur examine afin de sérialiser un message XML en un message de fichier plat HL7.</span><span class="sxs-lookup"><span data-stu-id="e82ec-132">The third block of the preceding text contains the promoted properties that the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer examines in order to serialize an XML message into an HL7 flat-file message.</span></span>  
  
 <span data-ttu-id="e82ec-133">Passez à [étape 13 : créer et configurer des Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e82ec-133">Proceed to [Step 13: Create and Configure Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82ec-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e82ec-134">See Also</span></span>  
 [<span data-ttu-id="e82ec-135">Didacticiel sur l’enrichissement des messages</span><span class="sxs-lookup"><span data-stu-id="e82ec-135">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
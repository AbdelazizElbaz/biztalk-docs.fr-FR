---
title: "Étape 11 : Créer des Variables d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
- message enrichment tutorial, orchestrations
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c12a437371c5412cfafa4140e74733655962fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-11-create-orchestration-variables"></a><span data-ttu-id="37c4e-102">Étape 11 : Créer des Variables d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="37c4e-102">Step 11: Create Orchestration Variables</span></span>
<span data-ttu-id="37c4e-103">Dans cette étape, vous créez les variables d’orchestration pour les instances de message envoyés et reçus par l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="37c4e-103">In this step, you create the orchestration variables for the message instances sent and received by the orchestration.</span></span>  
  
 <span data-ttu-id="37c4e-104">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) sérialiseur nécessite les noms suivants de la partie.</span><span class="sxs-lookup"><span data-stu-id="37c4e-104">The BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) serializer expects the following part names.</span></span> <span data-ttu-id="37c4e-105">Si vous créez un message à parties multiples avec d’autres noms de partie, le sérialiseur rejette le message.</span><span class="sxs-lookup"><span data-stu-id="37c4e-105">If you create a multipart message with any other part names, the serializer rejects the message.</span></span> <span data-ttu-id="37c4e-106">Les noms de partie de message sont :</span><span class="sxs-lookup"><span data-stu-id="37c4e-106">The message part names are:</span></span>  
  
-   <span data-ttu-id="37c4e-107">MSHSegment</span><span class="sxs-lookup"><span data-stu-id="37c4e-107">MSHSegment</span></span>  
  
-   <span data-ttu-id="37c4e-108">BodySegments</span><span class="sxs-lookup"><span data-stu-id="37c4e-108">BodySegments</span></span>  
  
-   <span data-ttu-id="37c4e-109">Segments Z</span><span class="sxs-lookup"><span data-stu-id="37c4e-109">Z segments</span></span>  
  
 <span data-ttu-id="37c4e-110">Vous trouverez ci-dessous des informations importantes sur les parties de segment Z :</span><span class="sxs-lookup"><span data-stu-id="37c4e-110">The following is important information about Z segment parts:</span></span>  
  
-   <span data-ttu-id="37c4e-111">Tous les messages contient trois parties, comme décrit ci-dessus, qu’un segment Z soit présent ou non.</span><span class="sxs-lookup"><span data-stu-id="37c4e-111">All messages contain three parts as described above, regardless of whether a Z segment is present or not.</span></span>  
  
-   <span data-ttu-id="37c4e-112">Une partie du segment Z permet de contenir des données de l’instance de message, qui est à droite et non définies dans le schéma (ce qui signifie également qu’il n’est pas déclaré).</span><span class="sxs-lookup"><span data-stu-id="37c4e-112">You use a Z segment part to contain data from the message instance, which is trailing and not defined in the schema (which also means that it is undeclared).</span></span>  
  
-   <span data-ttu-id="37c4e-113">Si aucune donnée non déclarée, la partie du segment Z est vide.</span><span class="sxs-lookup"><span data-stu-id="37c4e-113">If there is no undeclared data, the Z segment part is blank.</span></span> <span data-ttu-id="37c4e-114">Vous ne voyez pas les parties du segment Z lorsque vous affichez le fichier XML intermédiaire dans le Mappeur BizTalk ; Toutefois, dans l’outil de contrôle d’intégrité de BizTalk et l’activité de suivi du fonctionnement (HAT), consultez trois parties pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="37c4e-114">You do not see the Z segment parts when viewing the intermediate XML within BizTalk Mapper; however, in the BizTalk Health and Activity Tracking (HAT) tool, you see three parts to each message.</span></span>  
  
### <a name="to-create-orchestration-variables"></a><span data-ttu-id="37c4e-115">Pour créer des variables d’orchestration</span><span class="sxs-lookup"><span data-stu-id="37c4e-115">To create orchestration variables</span></span>  
  
1.  <span data-ttu-id="37c4e-116">Cliquez sur le **Vue Orchestration** onglet à côté du **l’Explorateur de solutions** sous l’Explorateur de Solutions.</span><span class="sxs-lookup"><span data-stu-id="37c4e-116">Click the **Orchestration View** tab next to the **Solution Explorer** tab beneath the Solutions Explorer.</span></span>  
  
2.  <span data-ttu-id="37c4e-117">Dans le **Vue Orchestration** volet, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-117">In the **Orchestration View** pane, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="37c4e-118">Modifier la **identificateur** propriété dans le **propriétés** volet pour **DoorbellInputMessage**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-118">Change the **Identifier** property in the **Properties** pane to **DoorbellInputMessage**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="37c4e-119">Dans le **propriétés** volet, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7_Project.Doorbell**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-119">In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.</span></span>  
  
5.  <span data-ttu-id="37c4e-120">Répétez les étapes 2 et 3 pour créer un autre message nommé **DoorbellOutputMessage**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-120">Repeat steps 2 and 3 to create another message named **DoorbellOutputMessage**.</span></span>  
  
6.  <span data-ttu-id="37c4e-121">Dans le **propriétés** volet, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-121">In the **Properties** pane, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.</span></span>  
  
7.  <span data-ttu-id="37c4e-122">Dans le **Vue Orchestration** volet, développez le **Types** nœud.</span><span class="sxs-lookup"><span data-stu-id="37c4e-122">In the **Orchestration View** pane, expand the **Types** node.</span></span> <span data-ttu-id="37c4e-123">Avec le bouton droit **Types Message à parties multiples**, puis cliquez sur **nouveau Type de Message de parties multiples**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-123">Right-click **Multi-part Message Types**, and then click **New Multi-part Message Type**.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="37c4e-124">Crée un type de message nommé **MultipartType_1** ainsi que d’un nouveau message nommé **MessagePart_1**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-124"> creates a new message type named **MultipartType_1** along with a new message named **MessagePart_1**.</span></span>  
  
8.  <span data-ttu-id="37c4e-125">Cliquez sur **MultipartType_1**et dans le **propriétés** fenêtre, cliquez sur **identificateur** et tapez le nouveau nom **DoorbellFinalMessageType**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-125">Click **MultipartType_1**, and in the **Properties** window, click **Identifier** and type the new name **DoorbellFinalMessageType**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37c4e-126">Dans les étapes 9 à 15, vous allez créer les parties du message à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="37c4e-126">In steps 9 through 15, you will create the parts of the multipart message.</span></span> <span data-ttu-id="37c4e-127">L’ordre dans lequel vous créez les parties d’un message à parties multiples est important.</span><span class="sxs-lookup"><span data-stu-id="37c4e-127">The order in which you create the parts of a multipart message is important.</span></span> <span data-ttu-id="37c4e-128">Toujours créer l’en-tête, puis le corps et le segment Z.</span><span class="sxs-lookup"><span data-stu-id="37c4e-128">Always create the header, then the body, then the Z segment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37c4e-129">Une fois que vous avez créé et nommé les parties de message, ne pas les renommer.</span><span class="sxs-lookup"><span data-stu-id="37c4e-129">Once you have created and named the message parts, do not rename them.</span></span> <span data-ttu-id="37c4e-130">Si nécessaire, supprimez l’ancienne partie de corps et créer un nouveau corps avec un nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="37c4e-130">If necessary, delete the old body part, and create a new body part with a new name.</span></span>  
  
9. <span data-ttu-id="37c4e-131">Dans le **Types** fenêtre, sous **Types Message à parties multiples**, développez **DoorbellFinalMessageType**, puis cliquez sur **MessagePart_1**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-131">In the **Types** window, under **Multi-part Message Types**, expand **DoorbellFinalMessageType**, and then click **MessagePart_1**.</span></span> <span data-ttu-id="37c4e-132">Dans le **propriétés** volet, entrez **MSHSegment** pour **identificateur**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-132">In the **Properties** pane, enter **MSHSegment** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="37c4e-133">Dans la liste déroulante pour **Type**, développez **Classes .NET**, puis cliquez sur \< **sélectionner à partir des assemblys référencés >**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-133">In the drop-down list for **Type**, expand **.NET Classes**, and then click \<**Select from referenced assemblies>**.</span></span>  
  
10. <span data-ttu-id="37c4e-134">Dans le **sélectionner le Type d’artefact** boîte de dialogue, dans le volet gauche, cliquez sur **System.Xml**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-134">In the **Select Artifact Type** dialog box, in the left pane, click **System.Xml**.</span></span> <span data-ttu-id="37c4e-135">Dans le volet droit, cliquez sur **XmlDocument**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-135">In the right pane, click **XmlDocument**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="37c4e-136">Dans la fenêtre Vue Orchestration, cliquez sur **DoorbellFinalMessageType**, puis cliquez sur **nouvelle partie de Message** créer MessagePart_1.</span><span class="sxs-lookup"><span data-stu-id="37c4e-136">In the Orchestration View window, right-click **DoorbellFinalMessageType**, and then click **New Message Part** to create MessagePart_1.</span></span>  
  
12. <span data-ttu-id="37c4e-137">Dans le **propriétés** fenêtre, entrez **BodySegments** pour **identificateur**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-137">In the **Properties** window, enter **BodySegments** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="37c4e-138">Dans la liste déroulante pour **Type**, développez **schémas**, puis sélectionnez **BTAHL7Schemas.ADT_A04_22_GLO_DEF** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="37c4e-138">In the drop-down list for **Type**, expand **Schemas**, and then select **BTAHL7Schemas.ADT_A04_22_GLO_DEF** from the drop-down list.</span></span>  
  
13. <span data-ttu-id="37c4e-139">Définir le **corps du Message** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-139">Set the **Message Body Part** property to **True**.</span></span>  
  
14. <span data-ttu-id="37c4e-140">Dans le **Vue Orchestration** fenêtre, avec le bouton droit **DoorbellFinalMessageType**, puis cliquez sur **nouvelle partie de Message**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-140">In the **Orchestration View** window, right-click **DoorbellFinalMessageType**, and then click **New Message Part**.</span></span>  
  
15. <span data-ttu-id="37c4e-141">Dans le **propriétés** volet, entrez **ZSegments** pour **identificateur**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-141">In the **Properties** pane, enter **ZSegments** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="37c4e-142">Cliquez sur **Type**, développez **Classes .NET**, puis cliquez sur **System.String** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="37c4e-142">Click **Type**, expand **.NET Classes**, and then click **System.String** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37c4e-143">Vous utilisez **System.String** pour les segments de la Z partie du message, car un segment Z contient des données de chaîne qui ne doivent pas se conformer à un schéma.</span><span class="sxs-lookup"><span data-stu-id="37c4e-143">You use **System.String** for the Z segments message part, because a Z segment contains string data that does not need to conform to a schema.</span></span>  
  
16. <span data-ttu-id="37c4e-144">Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-144">In the **Orchestration View** window, right-click **Messages**, and then click **New Message**.</span></span>  
  
17. <span data-ttu-id="37c4e-145">Dans le **propriétés** fenêtre, entrez **DoorbellFinalMessage** pour **identificateur**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-145">In the **Properties** window, enter **DoorbellFinalMessage** for **Identifier**, and then press **Enter**.</span></span> <span data-ttu-id="37c4e-146">Dans la liste déroulante pour **Type de Message**, développez **Types Message à parties multiples**, puis cliquez sur **BTAHL7_Project.DoorbellFinalMessageType**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-146">In the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.</span></span>  
  
18. <span data-ttu-id="37c4e-147">Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Variables**, puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-147">In the **Orchestration View** window, right-click **Variables**, and then click **New Variable**.</span></span>  
  
19. <span data-ttu-id="37c4e-148">Dans le **propriétés** volet, entrez **HeaderInfo** pour **identificateur**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-148">In the **Properties** pane, enter **HeaderInfo** for **Identifier**, then press **Enter**.</span></span> <span data-ttu-id="37c4e-149">Dans la liste déroulante pour **Type**, double-cliquez sur \< **classe .NET >**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-149">In the drop-down list for **Type**, double-click \<**.NET Class>**.</span></span>  
  
20. <span data-ttu-id="37c4e-150">Dans le **sélectionner le Type d’artefact** , dans le volet gauche, cliquez sur **System.Xml**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-150">In the **Select Artifact Type** window, in the left pane, click **System.Xml**.</span></span> <span data-ttu-id="37c4e-151">Dans le volet droit, cliquez sur **XmlDocument**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-151">In the right pane, click **XmlDocument**, and then click **OK**.</span></span>  
  
21. <span data-ttu-id="37c4e-152">Dans le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="37c4e-152">In the **File** menu, click **Save All**.</span></span>  
  
 <span data-ttu-id="37c4e-153">Passez à [étape 12 : configurer les formes d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="37c4e-153">Proceed to [Step 12: Configure Orchestration Shapes](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c4e-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37c4e-154">See Also</span></span>  
 [<span data-ttu-id="37c4e-155">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="37c4e-155">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
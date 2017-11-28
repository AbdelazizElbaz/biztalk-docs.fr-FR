---
title: "Étape 4 : Configurez la partie de la Source pour le scénario de traitement par lots Créer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12f7ca9eebb28bb97ae925aec4fc34cefd5a2dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-the-source-party-for-the-create-batch-scenario"></a><span data-ttu-id="f8252-102">Étape 4 : Configurez la partie de la Source pour le scénario de traitement par lots Créer</span><span class="sxs-lookup"><span data-stu-id="f8252-102">Step 4: Configure the Source Party for the Create-Batch Scenario</span></span>
<span data-ttu-id="f8252-103">Dans cette étape, vous configurez la partie de la source pour le scénario de traitement par lots de créer.</span><span class="sxs-lookup"><span data-stu-id="f8252-103">In this step, you configure the source party for the Create-Batch scenario.</span></span> <span data-ttu-id="f8252-104">Vous également sélectionnez les accusés de réception que BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) lot, tel que défini pour ce tiers.</span><span class="sxs-lookup"><span data-stu-id="f8252-104">You also select the acknowledgments that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will batch, as defined for this party.</span></span> <span data-ttu-id="f8252-105">Vous définissez la planification pour le traitement de l’accusé de réception que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] créera le lot après le nombre de messages atteint 2.</span><span class="sxs-lookup"><span data-stu-id="f8252-105">You set the scheduling for the acknowledgment batch such that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will create the batch after the message count reaches 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8252-106">Dans ce scénario, vous utilisez la même partie source que vous avez créé dans [étape 7 : créer et configurer un tiers Source](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md) de la partie 1 de ce didacticiel (la fragmentation lot scénario entrant).</span><span class="sxs-lookup"><span data-stu-id="f8252-106">In this scenario, you use the same source party that you created in [Step 7: Create and Configure a Source Party](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md) of Part 1 of this tutorial (the Fragmented Inbound Batch Scenario).</span></span>  
  
### <a name="to-configure-the-source-party-for-the-create-batch-scenario"></a><span data-ttu-id="f8252-107">Pour configurer le tiers source pour le scénario de traitement par lots de créer</span><span class="sxs-lookup"><span data-stu-id="f8252-107">To configure the source party for the Create-Batch scenario</span></span>  
  
1.  <span data-ttu-id="f8252-108">Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans l’arborescence de la console, cliquez sur **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="f8252-108">In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchSource**.</span></span>  
  
2.  <span data-ttu-id="f8252-109">Cliquez sur le **accusé de réception** onglet dans le volet détails.</span><span class="sxs-lookup"><span data-stu-id="f8252-109">Click the **Acknowledgment** tab in the Details pane.</span></span> <span data-ttu-id="f8252-110">Vérifiez que le **type d’accusé de réception** est **OriginalMode**.</span><span class="sxs-lookup"><span data-stu-id="f8252-110">Verify that the **Acknowledgment type** is **OriginalMode**.</span></span>  
  
3.  <span data-ttu-id="f8252-111">Cliquez sur le **définition de lot** onglet. Sous **accusés de réception de Message disponibles**, cliquez sur **BTAHL7Schemas.ADT_A03_231_GLO_DEF**, cliquez sur le déplacement vers la droite (**>>**) pour ajouter ce schéma au  **Sélectionné des accusés de réception de Message**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="f8252-111">Click the **Batch Definition** tab. Under **Available Message Acks**, click **BTAHL7Schemas.ADT_A03_231_GLO_DEF**, click the Move to the right arrow (**>>**) to add this schema to **Selected Message Acks**, and then click **Save**.</span></span>  
  
4.  <span data-ttu-id="f8252-112">Cliquez sur le **planification par lot** onglet. Dans le **Répétez le traitement par lots après** section, sélectionnez **Messages**, puis tapez **2** dans les **Messages** boîte.</span><span class="sxs-lookup"><span data-stu-id="f8252-112">Click the **Batch Schedule** tab. In the **Repeat Batch After** section, select **Messages**, and then type **2** in the **Messages** box.</span></span>  
  
5.  <span data-ttu-id="f8252-113">Cliquez sur **démarrer planification**.</span><span class="sxs-lookup"><span data-stu-id="f8252-113">Click **Start Schedule**.</span></span>  
  
 <span data-ttu-id="f8252-114">Passez à [étape 5 : créer le Port d’envoi pour le lot de messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md).</span><span class="sxs-lookup"><span data-stu-id="f8252-114">Proceed to [Step 5: Create the Send Port for the Message Batch](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md).</span></span>
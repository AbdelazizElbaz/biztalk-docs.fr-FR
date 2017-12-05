---
title: "Étape 7 : Créer et configurer un tiers Source | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8788a9c-ae6f-461b-82e5-f4276d1d5e0c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba84bd9a0ab8c6f7d5ccd24b27e90ef9c441b93
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-create-and-configure-a-source-party"></a><span data-ttu-id="32021-102">Étape 7 : Créer et configurer une partie de la Source</span><span class="sxs-lookup"><span data-stu-id="32021-102">Step 7: Create and Configure a Source Party</span></span>
<span data-ttu-id="32021-103">Dans cette étape, créer et configurer une partie de la source et attribuer des ports d’envoi pour activer les transformations d’en-tête de message pour le message sortant.</span><span class="sxs-lookup"><span data-stu-id="32021-103">In this step, you create and configure a source party, and assign send ports to enable message header transformations for the outgoing message.</span></span>  
  
### <a name="to-create-and-configure-a-source-party"></a><span data-ttu-id="32021-104">Pour créer et configurer une partie de la source</span><span class="sxs-lookup"><span data-stu-id="32021-104">To create and configure a source party</span></span>  
  
1.  <span data-ttu-id="32021-105">Dans la Console Administration de BizTalk, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="32021-105">In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="32021-106">Dans le **propriétés de tiers** boîte de dialogue, dans le champ nom, type **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="32021-106">In the **Party Properties** dialog box, in the Name field, type **Tutorial_BatchSource**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32021-107">La valeur que vous tapez dans cette zone est à partir de FHS3.1 d’origine [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] message traité par lot, FragmentedInboundBatch.txt.</span><span class="sxs-lookup"><span data-stu-id="32021-107">The value that you type in this box is from FHS3.1 of the original [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batched message, FragmentedInboundBatch.txt.</span></span>  
  
3.  <span data-ttu-id="32021-108">Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="32021-108">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="32021-109">Dans le volet Ports d’envoi, le champ nom, sélectionnez **Tutorial_2wayAck**.</span><span class="sxs-lookup"><span data-stu-id="32021-109">In the Send Ports pane, for the Name field, select **Tutorial_2wayAck**.</span></span>  
  
5.  <span data-ttu-id="32021-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="32021-110">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="32021-111">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur **BTAHL7 Configuration Explorer**.</span><span class="sxs-lookup"><span data-stu-id="32021-111">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
7.  <span data-ttu-id="32021-112">Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** , cliquez sur **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="32021-112">In BTAHL7 Configuration Explorer, on the **Parties** tab, click **Tutorial_BatchSource**.</span></span>  
  
8.  <span data-ttu-id="32021-113">Sélectionnez le **définition de lot** onglet de l’Explorateur de Configuration de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="32021-113">Select the **Batch Definition** tab of BTAHL7 Configuration Explorer.</span></span> <span data-ttu-id="32021-114">Sélectionnez **Oui** pour **Fragmentation requise**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="32021-114">Select **Yes** for **Fragmentation Required**, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="32021-115">Sélectionnez le **accusé de réception** onglet. Pour **Type d’accusé de réception**, sélectionnez **OriginalMode**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="32021-115">Select the **Acknowledgment** tab. For **Acknowledgment Type**, select **OriginalMode**, and then click **Save**.</span></span>  
  
 <span data-ttu-id="32021-116">Passez à [étape 8 : redémarrez BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="32021-116">Proceed to [Step 8: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md).</span></span>
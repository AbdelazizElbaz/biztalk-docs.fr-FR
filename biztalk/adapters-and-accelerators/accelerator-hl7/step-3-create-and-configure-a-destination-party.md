---
title: "Étape 3 : Créer et configurer un tiers de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8746f115-9f69-4593-9943-9ccda45cd900
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34fb3ef45123817f747ab9aa956e961c5bb9a1c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-and-configure-a-destination-party"></a><span data-ttu-id="917cc-102">Étape 3 : Créer et configurer un tiers de Destination</span><span class="sxs-lookup"><span data-stu-id="917cc-102">Step 3: Create and Configure a Destination Party</span></span>
<span data-ttu-id="917cc-103">Dans cette étape, vous créez et configurez un tiers de destination pour le scénario de traitement par lots de créer.</span><span class="sxs-lookup"><span data-stu-id="917cc-103">In this step, you create and configure a destination party for the Create-Batch scenario.</span></span> <span data-ttu-id="917cc-104">Vous sélectionnez également les messages qui [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] lots et le lot planifie, tel que défini pour ce tiers.</span><span class="sxs-lookup"><span data-stu-id="917cc-104">You also select the messages that [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] batches and the batch schedules, as defined for that party.</span></span> <span data-ttu-id="917cc-105">Vous planifiez l’heure d’envoi lot comme une heure après avoir copié les fichiers dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="917cc-105">You schedule the batch send time as one hour after copying the files into the folder.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="917cc-106">traite les messages reçus par la suite avec une fréquence d’une heure.</span><span class="sxs-lookup"><span data-stu-id="917cc-106"> batches any messages received thereafter with a frequency of one hour.</span></span>  
  
### <a name="to-create-and-configure-a-destination-party"></a><span data-ttu-id="917cc-107">Pour créer et configurer un tiers de destination</span><span class="sxs-lookup"><span data-stu-id="917cc-107">To create and configure a destination party</span></span>  
  
1.  <span data-ttu-id="917cc-108">Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="917cc-108">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="917cc-109">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_BatchDest**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="917cc-109">In the Party Properties dialog box, in the **Name** box, type **Tutorial_BatchDest**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="917cc-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="917cc-110">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
4.  <span data-ttu-id="917cc-111">Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans l’arborescence de la console, cliquez sur **Tutorial_BatchDest**.</span><span class="sxs-lookup"><span data-stu-id="917cc-111">In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchDest**.</span></span>  
  
5.  <span data-ttu-id="917cc-112">Cliquez sur le **accusé de réception** onglet dans le volet détails.</span><span class="sxs-lookup"><span data-stu-id="917cc-112">Click the **Acknowledgment** tab in the Details pane.</span></span> <span data-ttu-id="917cc-113">Vérifiez que le **type d’accusé de réception** est **aucun**.</span><span class="sxs-lookup"><span data-stu-id="917cc-113">Verify that the **Acknowledgment type** is **None**.</span></span>  
  
6.  <span data-ttu-id="917cc-114">Cliquez sur le **définition de lot** onglet. Dans le **Messages disponibles** volet, sélectionnez **BTAHL7Schemas.ADT_A03_231_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="917cc-114">Click the **Batch Definition** tab. In the **Available Messages** pane, select **BTAHL7Schemas.ADT_A03_231_GLO_DEF**.</span></span> <span data-ttu-id="917cc-115">Cliquez sur le déplacement vers la droite (**>>**) pour ajouter ce schéma à **les Messages sélectionnés**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="917cc-115">Click the Move to the right arrow (**>>**) to add this schema to **Selected Messages**, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="917cc-116">Cliquez sur le **planification par lot** onglet. Dans le **Répétez le traitement par lots après** section, vérifiez que **heures** est sélectionné, puis tapez **1** dans les **heures** boîte.</span><span class="sxs-lookup"><span data-stu-id="917cc-116">Click the **Batch Schedule** tab. In the **Repeat Batch After** section, verify that **Hours** is selected, and then type **1** in the **Hours** box.</span></span> <span data-ttu-id="917cc-117">Dans le **heures avant le premier lot** , tapez **1**, puis cliquez sur **démarrer la planification**.</span><span class="sxs-lookup"><span data-stu-id="917cc-117">In the **Hours before first batch** box, type **1**, and then click **Start Schedule**.</span></span>  
  
 <span data-ttu-id="917cc-118">Passez à [étape 4 : configurez la partie de la Source pour le scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="917cc-118">Proceed to [Step 4: Configure the Source Party for the Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md).</span></span>
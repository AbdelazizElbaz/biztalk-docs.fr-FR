---
title: Configurer le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, configuring
- configuring, batching
ms.assetid: 33c72d5e-31dd-44a8-8418-1faab3239e8e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9ab9ead01273e54826db670e7e6d6a2e9af6200
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching"></a><span data-ttu-id="e6869-102">Configurer le traitement par lot</span><span class="sxs-lookup"><span data-stu-id="e6869-102">Configuring Batching</span></span>
<span data-ttu-id="e6869-103">Vous utilisez [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Explorer de Configuration pour créer le lot, lot dans / de traitement par lot et pour sélectionner les schémas disponibles pour le traitement par lot sortant du lot.</span><span class="sxs-lookup"><span data-stu-id="e6869-103">You use [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Configuration Explorer to create batch, batch in/batch out batching, and to select available schemas for outbound batching.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6869-104">Vous devez configurer des partenaires commerciaux à l’aide de l’Explorateur BizTalk avant de pouvoir configurer le traitement par lots du message.</span><span class="sxs-lookup"><span data-stu-id="e6869-104">You must configure trading partners using BizTalk Explorer before you can configure message batching.</span></span>  
  
 <span data-ttu-id="e6869-105">L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **définition de lot** onglet.</span><span class="sxs-lookup"><span data-stu-id="e6869-105">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Batch Definition** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")  
  
 <span data-ttu-id="e6869-106">Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et configurer le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="e6869-106">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and configure batching.</span></span>  
  
### <a name="to-enable-message-batching-for-outbound-batching-create-batch"></a><span data-ttu-id="e6869-107">Pour activer le traitement par lots du message pour le traitement par lot sortant (créer un lot)</span><span class="sxs-lookup"><span data-stu-id="e6869-107">To enable message batching for outbound batching (Create Batch)</span></span>  
  
1.  <span data-ttu-id="e6869-108">Dans le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e6869-108">In the **Start** menu, open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e6869-109">Dans la Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="e6869-109">In the Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="e6869-110">Cliquez sur **Orchestrations**, avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e6869-110">Click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="e6869-111">Dans la boîte de dialogue Propriétés de l’Orchestration, cliquez sur **liaisons** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="e6869-111">In the Orchestration Properties dialog box, click **Bindings** in the console tree.</span></span>  
  
5.  <span data-ttu-id="e6869-112">Dans le **liaisons** volet, sélectionnez l’hôte approprié pour **hôte**.</span><span class="sxs-lookup"><span data-stu-id="e6869-112">In the **Bindings** pane, select the appropriate host for **Host**.</span></span> <span data-ttu-id="e6869-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6869-113">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e6869-114">Avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="e6869-114">Right-click **BatchOrchestration.Orchestration_1**, and then select **Enlist**.</span></span>  
  
7.  <span data-ttu-id="e6869-115">Avec le bouton droit **BatchOrchestration.Orchestration_1**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="e6869-115">Right-click **BatchOrchestration.Orchestration_1**, and then select **Start**.</span></span>  
  
### <a name="to-run-btahl7-configuration-explorer"></a><span data-ttu-id="e6869-116">Pour exécuter l’Explorateur de Configuration de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="e6869-116">To run BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="e6869-117">Dans le **Démarrer** menu, ouvrir **Microsoft BizTalk Accelerator pour HL7** , puis cliquez sur **BTAHL7 Configuration Explorer**.</span><span class="sxs-lookup"><span data-stu-id="e6869-117">In the **Start** menu, open **Microsoft BizTalk Accelerator for HL7** , and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-configure-batching"></a><span data-ttu-id="e6869-118">Pour configurer le traitement par lot</span><span class="sxs-lookup"><span data-stu-id="e6869-118">To configure batching</span></span>  
  
-   <span data-ttu-id="e6869-119">Dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration, dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **lot Définition** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e6869-119">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, in the **BTAHL7 Configuration Explorer** dialog box, on the **Parties** tab, select the party you want to configure, and then on the **Batch Definition** tab, do the following:</span></span>  
  
    |<span data-ttu-id="e6869-120">Utiliser</span><span class="sxs-lookup"><span data-stu-id="e6869-120">Use this</span></span>|<span data-ttu-id="e6869-121">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="e6869-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e6869-122">**Fragmentation requise**</span><span class="sxs-lookup"><span data-stu-id="e6869-122">**Fragmentation required**</span></span>|<span data-ttu-id="e6869-123">Sélectionnez l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6869-123">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="e6869-124">-   **Oui**.</span><span class="sxs-lookup"><span data-stu-id="e6869-124">-   **Yes**.</span></span> <span data-ttu-id="e6869-125">Pour activer la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="e6869-125">To enable fragmentation.</span></span><br /><span data-ttu-id="e6869-126">-   **Ne**.</span><span class="sxs-lookup"><span data-stu-id="e6869-126">-   **No**.</span></span> <span data-ttu-id="e6869-127">Pour désactiver la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="e6869-127">To disable fragmentation.</span></span> <span data-ttu-id="e6869-128">**Remarque :** pour un tiers, **Fragmentation requise** par défaut est **non**.</span><span class="sxs-lookup"><span data-stu-id="e6869-128">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>|  
    |<span data-ttu-id="e6869-129">**Sélectionner les Messages**</span><span class="sxs-lookup"><span data-stu-id="e6869-129">**Select Messages**</span></span>|<span data-ttu-id="e6869-130">Sélectionnez les types de messages que vous souhaitez envoyer en tant que lot à partir de la **Messages disponibles** fenêtre, puis cliquez sur le déplacement vers la droite (**>>**).</span><span class="sxs-lookup"><span data-stu-id="e6869-130">Select the message types you want to send as a batch from the **Available Messages** window, and then click the Move to the right arrow (**>>**).</span></span>|  
    |<span data-ttu-id="e6869-131">**Sélectionnez les accusés de réception de Message**</span><span class="sxs-lookup"><span data-stu-id="e6869-131">**Select Message Acknowledgments**</span></span>|<span data-ttu-id="e6869-132">Sélectionnez les types de message pour lequel vous souhaitez les accusés de réception à envoyer en tant que lot à partir de la **accusés de réception de Message disponibles** fenêtre, puis cliquez sur le déplacement vers la droite (**>>**).</span><span class="sxs-lookup"><span data-stu-id="e6869-132">Select the message types for which you want the acknowledgments to send as a batch from the **Available Message Acks** window, and then click the Move to the right (**>>**).</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="e6869-133">Vous ne pouvez pas voir les schémas que vous ajoutez à votre dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] projet tout en étant dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6869-133">You may not see schemas that you add to your In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] project while In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer is running.</span></span> <span data-ttu-id="e6869-134">Pour afficher ces fichiers, vous devrez peut-être redémarrer dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="e6869-134">In order to view these files, you may need to restart In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6869-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6869-135">See Also</span></span>  
 [<span data-ttu-id="e6869-136">Planification de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="e6869-136">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)
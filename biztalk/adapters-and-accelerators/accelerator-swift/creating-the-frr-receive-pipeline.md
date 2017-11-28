---
title: "Pipeline de réception de création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, creating
- FRR, creating receive pipelines
- creating, receive pipelines
ms.assetid: 5884176b-8522-4dd3-8f93-8695858b59ac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad31a69d579cf2bbe9f646fc87be1bea9f561a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-pipeline"></a><span data-ttu-id="3ed7c-102">Création de la FRR le Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="3ed7c-102">Creating the FRR Receive Pipeline</span></span>
<span data-ttu-id="3ed7c-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer un pipeline de réception qui contient les composants de pipeline SWIFT FRR l’ensemblecorrélations résolveur, outre le désassembleur SWIFT SWIFT FRR décodeur.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-103">To perform FIN Response Reconciliation, you must create a receive pipeline that contains the SWIFT FRR Decoder and SWIFT FRR CorrelationSet Resolver pipeline components, in addition to the SWIFT disassembler.</span></span>  
  
 <span data-ttu-id="3ed7c-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="3ed7c-104">**Summary**</span></span>  
  
 <span data-ttu-id="3ed7c-105">Créer un pipeline de réception avec les étapes/propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ed7c-105">Create a receive pipeline with the following stages/properties:</span></span>  
  
|<span data-ttu-id="3ed7c-106">/ Propriété de l’étape</span><span class="sxs-lookup"><span data-stu-id="3ed7c-106">Stage/Property</span></span>|<span data-ttu-id="3ed7c-107">Paramètre du composant /</span><span class="sxs-lookup"><span data-stu-id="3ed7c-107">Component/Setting</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="3ed7c-108">Étape Désassembler</span><span class="sxs-lookup"><span data-stu-id="3ed7c-108">Disassemble stage</span></span>|<span data-ttu-id="3ed7c-109">Désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="3ed7c-109">SWIFT Disassembler</span></span>|  
|<span data-ttu-id="3ed7c-110">Propriété de Validation du moteur BRE (désassembleur SWIFT)</span><span class="sxs-lookup"><span data-stu-id="3ed7c-110">BRE Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="3ed7c-111">True</span><span class="sxs-lookup"><span data-stu-id="3ed7c-111">True</span></span>|  
|<span data-ttu-id="3ed7c-112">Propriété de Validation XML (désassembleur SWIFT)</span><span class="sxs-lookup"><span data-stu-id="3ed7c-112">XML Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="3ed7c-113">True</span><span class="sxs-lookup"><span data-stu-id="3ed7c-113">True</span></span>|  
|<span data-ttu-id="3ed7c-114">Propriété de schéma d’en-tête SWIFT (désassembleur SWIFT)</span><span class="sxs-lookup"><span data-stu-id="3ed7c-114">SWIFT Header Schema property (SWIFT Disassembler)</span></span>|<span data-ttu-id="3ed7c-115">(Aucun)</span><span class="sxs-lookup"><span data-stu-id="3ed7c-115">(None)</span></span>|  
|<span data-ttu-id="3ed7c-116">Phase de décodeur</span><span class="sxs-lookup"><span data-stu-id="3ed7c-116">Decoder stage</span></span>|<span data-ttu-id="3ed7c-117">Décodeur de MQSeries FRR SWIFT</span><span class="sxs-lookup"><span data-stu-id="3ed7c-117">SWIFT FRR MQSeries Decoder</span></span>|  
|<span data-ttu-id="3ed7c-118">Phase de résolution de tiers</span><span class="sxs-lookup"><span data-stu-id="3ed7c-118">Party Resolution stage</span></span>|<span data-ttu-id="3ed7c-119">Programme de résolution de jeu de corrélations de FRR SWIFT</span><span class="sxs-lookup"><span data-stu-id="3ed7c-119">SWIFT FRR Correlation Set Resolver</span></span>|  
  
### <a name="to-create-a-custom-receive-pipeline-for-frr"></a><span data-ttu-id="3ed7c-120">Pour créer un pipeline de réception personnalisé pour FRR</span><span class="sxs-lookup"><span data-stu-id="3ed7c-120">To create a custom receive pipeline for FRR</span></span>  
  
1.  <span data-ttu-id="3ed7c-121">Dans l’Explorateur de solutions de Visual Studio, cliquez sur le projet contenant votre [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-121">In Solution Explorer of Visual Studio, right-click the project containing your [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="3ed7c-122">Dans la boîte de dialogue Ajouter un nouvel élément, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-122">In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** in the Templates pane.</span></span>  
  
3.  <span data-ttu-id="3ed7c-123">Dans le **nom** , tapez un nom pour votre pipeline de réception, tel que **FRRReceivePipeline.btp**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-123">In the **Name** box, type a name for your receive pipeline, such as **FRRReceivePipeline.btp**.</span></span> <span data-ttu-id="3ed7c-124">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-124">Click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ed7c-125">Avant d’effectuer l’étape 4, vous devez avoir ajouté le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR leurs composants à la boîte à outils, comme décrit dans [Ajout des composants de Pipeline SWIFT à la boîte à outils](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="3ed7c-125">Before you perform step 4, you must have added the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR pipeline components to the toolbox, as described in [Adding SWIFT Pipeline Components to the Toolbox](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).</span></span>  
  
4.  <span data-ttu-id="3ed7c-126">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** puis cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-126">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then click **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="3ed7c-127">Dans le volet de la boîte à outils des composants de Pipeline BizTalk, faites glisser le **SWIFT désassembleur** à la **Déposer ici** zone ci-dessous le **désassembler** forme dans le Concepteur de Pipeline à l’étape.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-127">From the BizTalk Pipeline Components Toolbox pane, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in Pipeline Designer.</span></span>  
  
6.  <span data-ttu-id="3ed7c-128">Avec la **désassembleur SWIFT** sélectionné dans le Concepteur de Pipeline, dans **propriétés**, vérifiez que le **BRE Validation** et **laValidationXML** propriétés sont définies sur **True**et le **schéma d’en-tête SWIFT** est définie sur **(aucun)**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-128">With the **SWIFT Disassembler Component** selected in Pipeline Designer, in **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**, and the **SWIFT Header Schema** property is set to **(None)**.</span></span>  
  
7.  <span data-ttu-id="3ed7c-129">Dans la boîte à outils composants de Pipeline de BizTalk, faites glisser **SWIFT FRR MQSeries décodeur** à la **Déposer ici** zone ci-dessous le **décodeur** forme dans le Concepteur de Pipeline à l’étape.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-129">In the BizTalk Pipeline Components Toolbox, drag **SWIFT FRR MQSeries Decoder** to the **Drop Here** box below the **Decoder** stage shape in Pipeline Designer.</span></span>  
  
8.  <span data-ttu-id="3ed7c-130">Dans le volet de la boîte à outils des composants de Pipeline BizTalk, faites glisser **SWIFT FRR corrélation définir résolution** à la **Déposer ici** zone ci-dessous le **Résoudretiers** forme dans le Pipeline à l’étape Concepteur.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-130">From the BizTalk Pipeline Components Toolbox pane, drag **SWIFT FRR Correlation Set Resolver** to the **Drop Here** box below the **ResolveParty** stage shape in Pipeline Designer.</span></span>  
  
9. <span data-ttu-id="3ed7c-131">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-131">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then click **Save All**.</span></span>
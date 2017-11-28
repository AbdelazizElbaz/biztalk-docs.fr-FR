---
title: "Création d’un projet de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b584e3ab-e824-4977-b4ed-4fc197a6cf7a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eead267abbb990933e6fd3150d099d07b007526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-pipeline-project"></a><span data-ttu-id="00e47-102">Création d’un projet de Pipeline</span><span class="sxs-lookup"><span data-stu-id="00e47-102">Creating a Pipeline Project</span></span>
<span data-ttu-id="00e47-103">Pour créer un projet de pipeline :</span><span class="sxs-lookup"><span data-stu-id="00e47-103">To create a pipeline project:</span></span>  
  
1.  <span data-ttu-id="00e47-104">Dans Visual Studio, créez un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="00e47-104">In Visual Studio, create a new BizTalk project.</span></span>  
  
2.  <span data-ttu-id="00e47-105">Ajouter un élément de pipeline de réception et un élément de pipeline d’envoi pour le projet.</span><span class="sxs-lookup"><span data-stu-id="00e47-105">Add a receive pipeline item and a send pipeline item to the project.</span></span>  
  
3.  <span data-ttu-id="00e47-106">Ouvrez le fichier ReceivePipeline.btp.</span><span class="sxs-lookup"><span data-stu-id="00e47-106">Open the ReceivePipeline.btp file.</span></span>  
  
4.  <span data-ttu-id="00e47-107">Dans le Concepteur de Pipeline, ouvrez la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="00e47-107">In Pipeline Designer, open the Toolbox.</span></span>  
  
5.  <span data-ttu-id="00e47-108">Cliquez sur le **boîte à outils** surface, puis sélectionnez **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="00e47-108">Right-click the **Toolbox** surface, and then select **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="00e47-109">Dans la fenêtre Choisir des éléments de boîte à outils, cliquez sur le **composants de Pipeline** onglet et sélectionnez les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="00e47-109">In the Choose Toolbox Items window, click the **Pipeline Components** tab, and then select the following pipeline components:</span></span>  
  
    -   <span data-ttu-id="00e47-110">SwiftMXDisassembler</span><span class="sxs-lookup"><span data-stu-id="00e47-110">SwiftMXDisassembler</span></span>  
  
    -   <span data-ttu-id="00e47-111">SwiftMXAssembler</span><span class="sxs-lookup"><span data-stu-id="00e47-111">SwiftMXAssembler</span></span>  
  
    -   <span data-ttu-id="00e47-112">Composant d’encodeur MXRR SWIFT</span><span class="sxs-lookup"><span data-stu-id="00e47-112">Swift MXRR Encoder Component</span></span>  
  
    -   <span data-ttu-id="00e47-113">Composant du décodeur MXRR SWIFT</span><span class="sxs-lookup"><span data-stu-id="00e47-113">Swift MXRR Decoder Component</span></span>  
  
    -   <span data-ttu-id="00e47-114">Composant de programme de résolution de tiers de corrélation MXRR SWIFT</span><span class="sxs-lookup"><span data-stu-id="00e47-114">Swift MXRR Correlation Party Resolver Component</span></span>  
  
7.  <span data-ttu-id="00e47-115">Faites glisser le **SwiftMXDisassembler** composant dans l’espace réservé du désassembleur dans le Pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="00e47-115">Drag the **SwiftMXDisassembler** component into the Disassembler placeholder in the Receive Pipeline.</span></span>  
  
8.  <span data-ttu-id="00e47-116">Dans les propriétés du composant SwiftMXDisassembler, définissez le **BRE Validation** propriété à TRUE ou FALSE selon que vous souhaitez activer la Validation des règles d’entreprise sur les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="00e47-116">In the SwiftMXDisassembler component properties, set the **BRE Validation** property to TRUE or FALSE depending on whether you want to enable Business Rules Validation on the incoming messages.</span></span> <span data-ttu-id="00e47-117">Définir le **TransportHeaderRequired** propriété à TRUE ou FALSE selon que vous souhaitez fournir l’en-tête de transport dans les messages.</span><span class="sxs-lookup"><span data-stu-id="00e47-117">Set the **TransportHeaderRequired** property to TRUE or FALSE depending on whether you want to provide transport header in messages.</span></span>  
  
9. <span data-ttu-id="00e47-118">Faites glisser le composant décodeur de MXRR Swift et résolution de tiers Swift MXRR corrélation dans le décodeur et l’espace réservé du programme de résolution de tiers dans le Pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="00e47-118">Drag the Swift MXRR Decoder and Swift MXRR Correlation Party Resolver component into the Decoder and the Party Resolver placeholder inside the Receive Pipeline.</span></span>  
  
10. <span data-ttu-id="00e47-119">Sélectionnez le **résolution de tiers de corrélation MXRR** dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="00e47-119">Select the **MXRR Correlation Party Resolver** in the pipeline.</span></span> <span data-ttu-id="00e47-120">Dans la fenêtre Propriétés du composant de Pipeline, définissez la **activer la journalisation BAM pour rapprochement** propriété à TRUE ou FALSE, selon que vous souhaitez activer le rapprochement entre les réponses SWIFT.</span><span class="sxs-lookup"><span data-stu-id="00e47-120">In the Pipeline Component Properties window, set the **Enable BAM Logging for Reconciliation** property to TRUE or FALSE, depending on whether you want to enable reconciliation for the SWIFT responses.</span></span>  
  
11. <span data-ttu-id="00e47-121">Ouvrez le **SendPipeline.btp** fichier, dans le Concepteur de Pipeline, ouvrir le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="00e47-121">Open the **SendPipeline.btp** file, In the Pipeline Designer, open the **Toolbox**.</span></span>  
  
12. <span data-ttu-id="00e47-122">Dans la boîte à outils, faites glisser le **SwiftMXAssembler** composant dans l’espace réservé d’assembleur dans le Pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="00e47-122">In Toolbox, drag the **SwiftMXAssembler** component into the Assembler placeholder inside the Send Pipeline.</span></span>  
  
13. <span data-ttu-id="00e47-123">Faites glisser le **Swift MXRR encodeur** composant dans les espaces réservés d’encodeur du Pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="00e47-123">Drag the **Swift MXRR Encoder** component into the Encoder placeholders of the Send Pipeline.</span></span>  
  
14. <span data-ttu-id="00e47-124">Sélectionnez le **MXRR encodeur tiers résolveur** dans le pipeline, puis, dans la fenêtre Propriétés du composant de Pipeline, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="00e47-124">Select the **MXRR Encoder Party Resolver** in the pipeline, and then in the Pipeline Component Properties window, set the following properties.</span></span>  
  
15. <span data-ttu-id="00e47-125">Activer **journalisation de l’analyse BAM pour rapprochement** TRUE ou FALSE selon que vous souhaitez activer le rapprochement entre les réponses SWIFT.</span><span class="sxs-lookup"><span data-stu-id="00e47-125">Enable **BAM Logging for Reconciliation** to TRUE or FALSE depending on whether you want to enable reconciliation for the SWIFT responses.</span></span>  
  
16. <span data-ttu-id="00e47-126">Définir le **LAU requis** TRUE ou FALSE selon que vous disposez activer la signature du message à l’accès de Alliance SWIFT (SAA).</span><span class="sxs-lookup"><span data-stu-id="00e47-126">Set the **LAU Required** to TRUE or FALSE depending on whether you have to enable the signing of the message at the SWIFT Alliance Access (SAA).</span></span>  
  
17. <span data-ttu-id="00e47-127">Si la propriété LAU requis a été a été défini à TRUE, puis fournissez LAU clé première partie et le deuxième partie LAU clé (les valeurs doivent être les mêmes que ceux qui ont été fournies lors de la configuration de la SAA.)</span><span class="sxs-lookup"><span data-stu-id="00e47-127">If the LAU Required property has been has been set to TRUE, then provide LAU Key First Part and LAU Key Second Part (the values have to be the same ones that were provided while configuring the SAA.)</span></span>  
  
18. <span data-ttu-id="00e47-128">Générez et déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="00e47-128">Build and then deploy the project.</span></span>
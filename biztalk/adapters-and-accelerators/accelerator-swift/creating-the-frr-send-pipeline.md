---
title: "Pipeline d’envoi de création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, creating send pipelines
- creating, send pipelines
- send pipelines, creating
ms.assetid: c6cd2047-ea53-425f-80cc-b02a1deb5292
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87733b6b3a93d2543d26cd6d11b366b84218d207
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-send-pipeline"></a><span data-ttu-id="4ada1-102">Créer le Pipeline d’envoi FRR</span><span class="sxs-lookup"><span data-stu-id="4ada1-102">Creating the FRR Send Pipeline</span></span>
<span data-ttu-id="4ada1-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer un pipeline d’envoi qui contient le composant de pipeline SWIFTAsmFrrMQSeriesHelper, en plus de l’assembleur SWIFT.</span><span class="sxs-lookup"><span data-stu-id="4ada1-103">To perform FIN Response Reconciliation, you need to create a send pipeline that contains the SWIFTAsmFrrMQSeriesHelper pipeline component, in addition to the SWIFT assembler.</span></span>  
  
 <span data-ttu-id="4ada1-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="4ada1-104">**Summary**</span></span>  
  
 <span data-ttu-id="4ada1-105">Créer un pipeline d’envoi avec les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ada1-105">Create a send pipeline with the following stages:</span></span>  
  
|<span data-ttu-id="4ada1-106">Étape</span><span class="sxs-lookup"><span data-stu-id="4ada1-106">Stage</span></span>|<span data-ttu-id="4ada1-107">Composant</span><span class="sxs-lookup"><span data-stu-id="4ada1-107">Component</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="4ada1-108">Étape Assembler</span><span class="sxs-lookup"><span data-stu-id="4ada1-108">Assemble stage</span></span>|<span data-ttu-id="4ada1-109">Assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="4ada1-109">SWIFT assembler</span></span>|  
|<span data-ttu-id="4ada1-110">Étape Coder</span><span class="sxs-lookup"><span data-stu-id="4ada1-110">Encode stage</span></span>|<span data-ttu-id="4ada1-111">Composant de MQSeries envoi Frr SWIFT</span><span class="sxs-lookup"><span data-stu-id="4ada1-111">SWIFT Frr MQSeries Send Component</span></span>|  
  
### <a name="to-create-a-custom-send-pipeline-for-frr"></a><span data-ttu-id="4ada1-112">Pour créer un pipeline d’envoi personnalisé pour FRR</span><span class="sxs-lookup"><span data-stu-id="4ada1-112">To create a custom send pipeline for FRR</span></span>  
  
1.  <span data-ttu-id="4ada1-113">Dans l’Explorateur de solutions de Visual Studio, votre projet de pipeline avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-113">In Solution Explorer of Visual Studio, right-click your pipeline project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="4ada1-114">Dans la boîte de dialogue Ajouter un nouvel élément, sélectionnez **Pipeline d’envoi** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="4ada1-114">In the Add New Item dialog box, select **Send Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="4ada1-115">Dans le **nom** , tapez un nom pour votre pipeline de réception, tel que **FRRSendPipeline.btp**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-115">In the **Name** box, type a name for your receive pipeline, such as **FRRSendPipeline.btp**.</span></span> <span data-ttu-id="4ada1-116">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-116">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="4ada1-117">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-117">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="4ada1-118">Dans la palette de composants de Pipeline BizTalk, faites glisser **SWIFT assembleur** à la **Déposer ici** zone ci-dessous le **assemblage** forme dans l’étape **BizTalk Pipeline Concepteur**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-118">From the BizTalk Pipeline Components Toolbox, drag **SWIFT Assembler** to the **Drop Here** box below the **Assemble** stage shape in **BizTalk Pipeline Designer**.</span></span>  
  
6.  <span data-ttu-id="4ada1-119">Dans la palette de composants de Pipeline BizTalk, faites glisser **SWIFT Frr MQSeries envoyer composant** à la **Déposer ici** zone ci-dessous le **Encode** forme dans l’étape  **Le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-119">From the BizTalk Pipeline Components Toolbox, drag **SWIFT Frr MQSeries Send Component** to the **Drop Here** box below the **Encode** stage shape in **BizTalk Pipeline Designer**.</span></span>  
  
7.  <span data-ttu-id="4ada1-120">Dans l’Explorateur BizTalk, votre projet de pipeline avec le bouton droit, cliquez sur **annuler le déploiement**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-120">In BizTalk Explorer, right-click your pipeline project, click **Undeploy**, and then click **Yes**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ada1-121">Après l’annulation du déploiement, puis le redéployer votre projet de pipeline, vous devez réinitialiser les ports d’envoi ou emplacements de réception qui utilisent des pipelines dans le projet déployé précédemment.</span><span class="sxs-lookup"><span data-stu-id="4ada1-121">After undeploying and then redeploying your pipeline project, you must reset any send ports or receive locations that use pipelines in the previously deployed project.</span></span>  
  
8.  <span data-ttu-id="4ada1-122">Dans l’Explorateur de solutions, cliquez sur votre projet de pipeline, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-122">In Solution Explorer, right-click your pipeline project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="4ada1-123">Une fois la génération a réussi, avec le bouton droit de votre projet de pipeline, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="4ada1-123">After the build has succeeded, right-click your pipeline project, and then click **Deploy**.</span></span>
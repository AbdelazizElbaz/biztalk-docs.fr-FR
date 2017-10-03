---
title: "Ajout de composants de Pipeline SWIFT à la boîte à outils | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox, adding pipelines
- pipelines, adding to toolbox
ms.assetid: 3821c10e-ef9b-4657-b934-cff6d096f654
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaef345994a1d849e09025d9ad1bb0f133c1b224
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-swift-pipeline-components-to-the-toolbox"></a><span data-ttu-id="38a1b-102">Ajout de composants de Pipeline SWIFT à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="38a1b-102">Adding SWIFT Pipeline Components to the Toolbox</span></span>
<span data-ttu-id="38a1b-103">Vous devez ajouter les composants de pipeline SWIFT à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] boîte à outils, qui vous pouvez de créer des pipelines personnalisés à l’aide de ces composants.</span><span class="sxs-lookup"><span data-stu-id="38a1b-103">You must add the SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox, so that you can create custom pipelines using these components.</span></span> <span data-ttu-id="38a1b-104">Cela est nécessaire pour créer des pipelines pour Message Repair et New Submission ou rapprochement de réponse de FIN.</span><span class="sxs-lookup"><span data-stu-id="38a1b-104">This is required to create pipelines for either Message Repair and New Submission or FIN Response Reconciliation.</span></span>  
  
 <span data-ttu-id="38a1b-105">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="38a1b-105">**Summary**</span></span>  
  
 <span data-ttu-id="38a1b-106">Ajouter les composants de pipeline SWIFT suivant à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] boîte à outils :</span><span class="sxs-lookup"><span data-stu-id="38a1b-106">Add the following SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox:</span></span>  
  
-   <span data-ttu-id="38a1b-107">Assembleur SWIFT (pour Message Repair et New Submission ou rapprochement de réponse FIN (FRR))</span><span class="sxs-lookup"><span data-stu-id="38a1b-107">SWIFT Assembler (for Message Repair and New Submission or FIN Response Reconciliation (FRR))</span></span>  
  
-   <span data-ttu-id="38a1b-108">Désassembleur SWIFT (pour Message Repair et New Submission ou FRR)</span><span class="sxs-lookup"><span data-stu-id="38a1b-108">SWIFT Disassembler (for Message Repair and New Submission or FRR)</span></span>  
  
-   <span data-ttu-id="38a1b-109">Programme de résolution ensemble de corrélation Frr SWIFT (pour FRR)</span><span class="sxs-lookup"><span data-stu-id="38a1b-109">SWIFT Frr Correlation Set Resolver (for FRR)</span></span>  
  
-   <span data-ttu-id="38a1b-110">Décodeur de MQSeries Frr SWIFT (pour FRR)</span><span class="sxs-lookup"><span data-stu-id="38a1b-110">SWIFT Frr MQSeries Decoder (for FRR)</span></span>  
  
-   <span data-ttu-id="38a1b-111">Composant d’envoi SWIFT Frr MQSeries (pour FRR)</span><span class="sxs-lookup"><span data-stu-id="38a1b-111">SWIFT Frr MQSeries Send Component (for FRR)</span></span>  
  
### <a name="to-add-a4swift-pipeline-components-to-the-toolbox"></a><span data-ttu-id="38a1b-112">Pour ajouter des composants de pipeline A4SWIFT à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="38a1b-112">To add A4SWIFT pipeline components to the toolbox</span></span>  
  
1.  <span data-ttu-id="38a1b-113">Dans Visual Studio, sur le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="38a1b-113">In Visual Studio, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
2.  <span data-ttu-id="38a1b-114">Dans le **choisir des éléments de boîte à outils** boîte de dialogue le **composants de Pipeline BizTalk** onglet, sélectionnez **SWIFT assembleur** et **SWIFT désassembleur**.</span><span class="sxs-lookup"><span data-stu-id="38a1b-114">In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Components** tab, select **SWIFT Assembler** and **SWIFT Disassembler**.</span></span> <span data-ttu-id="38a1b-115">Si vous utilisez Rapprochement de réponse de FIN, sélectionnez **SWIFT Frr corrélation définir résolution**, **SWIFT Frr MQSeries décodeur**, et **SWIFT Frr MQSeries envoyer composant**.</span><span class="sxs-lookup"><span data-stu-id="38a1b-115">If you will be using FIN Response Reconciliation, select **SWIFT Frr Correlation Set Resolver**, **SWIFT Frr MQSeries Decoder**, and **SWIFT Frr MQSeries Send Component**.</span></span>  
  
3.  <span data-ttu-id="38a1b-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38a1b-116">Click **OK**.</span></span>
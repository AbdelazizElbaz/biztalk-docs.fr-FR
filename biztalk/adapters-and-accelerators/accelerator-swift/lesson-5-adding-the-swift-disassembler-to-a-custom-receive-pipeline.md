---
title: "Leçon 5 : Ajouter le désassembleur SWIFT à un Pipeline de réception personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04feeaf88cef2f4ab876b22eda1b1e060a1e0173
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a><span data-ttu-id="e3e87-102">Leçon 5 : Ajouter le désassembleur SWIFT à un Pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="e3e87-102">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>
<span data-ttu-id="e3e87-103">Dans cette leçon, vous ajoutez le désassembleur personnalisé SWIFT (DASM) à votre pipeline.</span><span class="sxs-lookup"><span data-stu-id="e3e87-103">In this lesson, you add the custom SWIFT disassembler (DASM) to your pipeline.</span></span> <span data-ttu-id="e3e87-104">Un composant de pipeline DASM est un composant de pipeline qui divise les messages dans un lot en documents individuels.</span><span class="sxs-lookup"><span data-stu-id="e3e87-104">A DASM pipeline component is a pipeline component that divides messages in a batch into individual documents.</span></span>  
  
 <span data-ttu-id="e3e87-105">Les composants de pipeline DASM fournis dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] sont :</span><span class="sxs-lookup"><span data-stu-id="e3e87-105">The DASM pipeline components provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] are:</span></span>  
  
-   <span data-ttu-id="e3e87-106">Désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="e3e87-106">Flat file disassembler</span></span>  
  
-   <span data-ttu-id="e3e87-107">Désassembleur BizTalk Framework</span><span class="sxs-lookup"><span data-stu-id="e3e87-107">BizTalk Framework disassembler</span></span>  
  
-   <span data-ttu-id="e3e87-108">Désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="e3e87-108">XML disassembler</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="e3e87-109">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] ajoute un désassembleur SWIFT supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e3e87-109"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] adds an additional SWIFT disassembler.</span></span>  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a><span data-ttu-id="e3e87-110">Pour ajouter le désassembleur personnalisé SWIFT à votre pipeline</span><span class="sxs-lookup"><span data-stu-id="e3e87-110">To add the SWIFT custom disassembler to your pipeline</span></span>  
  
1.  <span data-ttu-id="e3e87-111">Dans le menu Affichage, cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-111">From the View menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="e3e87-112">À partir de la **boîte à outils des composants de Pipeline BizTalk**, cliquez sur **SWIFT désassembleur** et faites-la glisser vers le **Déposer ici** zone ci-dessous le **désassembler**forme dans l’étape **le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-112">From the **BizTalk Pipeline Components Toolbox**, click **SWIFT Disassembler** and drag it to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**.</span></span> <span data-ttu-id="e3e87-113">Laissez le **SWIFT désassembleur** forme sélectionnée dans le **le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-113">Leave the **SWIFT Disassembler** shape selected in the **BizTalk Pipeline Designer**.</span></span>  
  
3.  <span data-ttu-id="e3e87-114">Dans le **propriétés** volet, sélectionnez **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** pour le **schéma d’en-tête SWIFT** propriété.</span><span class="sxs-lookup"><span data-stu-id="e3e87-114">In the **Properties** pane, select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for the **SWIFT Header Schema** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3e87-115">Ne confondez pas **schéma d’en-tête SWIFT** et le schéma d’en-tête de Message.</span><span class="sxs-lookup"><span data-stu-id="e3e87-115">Do not confuse **SWIFT Header Schema** and Message Header Schema.</span></span> <span data-ttu-id="e3e87-116">Vous devez définir **schéma d’en-tête SWIFT** à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="e3e87-116">You must set **SWIFT Header Schema** in step 3.</span></span>  
  
4.  <span data-ttu-id="e3e87-117">Dans le **propriétés** volet, vérifiez que le **BRE Validation** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-117">In the **Properties** pane, ensure that the **BRE Validation** property is set to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3e87-118">Le moteur de règles d’entreprise (BRE) est décrit ci-dessous plus loin dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="e3e87-118">An explanation of the Business Rule Engine (BRE) follows later in this tutorial.</span></span>  
  
5.  <span data-ttu-id="e3e87-119">Dans le **propriétés** volet, vérifiez que le **Validation XML** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-119">In the **Properties** pane, ensure that the **XML Validation** property is set to **True**.</span></span>  
  
6.  <span data-ttu-id="e3e87-120">Dans le **propriétés** volet, vérifiez que le **entrant Debatching** est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="e3e87-120">In the **Properties** pane, ensure that the **Inbound Debatching** property is set to **False**.</span></span>  
  
7.  <span data-ttu-id="e3e87-121">Sur le **fichier** menu, sélectionnez **Enregistrer tout** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="e3e87-121">On the **File** menu, select **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="e3e87-122">Passez à [Leçon 6 : création d’un fichier Pipeline d’envoi](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="e3e87-122">Proceed to [Lesson 6: Creating a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).</span></span>
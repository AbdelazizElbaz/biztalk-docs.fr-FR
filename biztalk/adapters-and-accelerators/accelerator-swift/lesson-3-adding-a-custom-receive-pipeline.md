---
title: "Leçon 3 : Ajout d’un Pipeline de réception personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating custom pipelines
- custom pipelines
ms.assetid: 1917b8e2-4f1c-4c20-abe4-ea18a406eeeb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76abee50cce743dde6c62ea078f5ef9dada0c998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-adding-a-custom-receive-pipeline"></a><span data-ttu-id="f3755-102">Leçon 3 : Ajout d’un Pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="f3755-102">Lesson 3: Adding a Custom Receive Pipeline</span></span>
<span data-ttu-id="f3755-103">Dans cette leçon, vous créez un pipeline de réception personnalisé à l’aide du Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f3755-103">In this lesson you create a custom receive pipeline using BizTalk Pipeline Designer.</span></span> <span data-ttu-id="f3755-104">Un pipeline de réception personnalisé est un pipeline est exécuté sur les messages une fois que l’adaptateur reçoit les messages, mais avant que [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] les publie dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f3755-104">A custom receive pipeline is a pipeline that is run on messages after the adapter receives the messages, but before [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] publishes them to the MessageBox database.</span></span>  
  
 <span data-ttu-id="f3755-105">Vous configurez le pipeline personnalisé pour utiliser le composant désassembleur SWIFT (DASM).</span><span class="sxs-lookup"><span data-stu-id="f3755-105">You configure the custom pipeline to use the SWIFT disassembler (DASM) component.</span></span> <span data-ttu-id="f3755-106">Le désassembleur SWIFT accepte un fichier plat au format SWIFT et convertit ou l’analyse, le contenu du message SWIFT dans une représentation XML, ce qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] peut consommer.</span><span class="sxs-lookup"><span data-stu-id="f3755-106">The SWIFT disassembler takes a SWIFT-formatted flat file and converts, or parses, the content of the SWIFT message into an XML-based representation, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can consume.</span></span>  
  
 <span data-ttu-id="f3755-107">Le schéma d’exécution MT103 que vous avez ajouté à l’étape précédente ([leçon 2 : ajout de références de projet](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) est le format que vous utilisez pour la conversion.</span><span class="sxs-lookup"><span data-stu-id="f3755-107">The MT103 runtime schema that you added in the previous step ([Lesson 2: Adding Project References](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) is the format that you use for the conversion.</span></span>  
  
### <a name="to-create-a-new-custom-receive-pipeline"></a><span data-ttu-id="f3755-108">Pour créer une nouvelle personnalisée pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="f3755-108">To create a new custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="f3755-109">Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="f3755-109">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="f3755-110">Dans la boîte de dialogue Ajouter nouvel élément-SWIFTPipelines, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="f3755-110">In the Add New Item-SWIFTPipelines dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="f3755-111">Dans le **nom** , tapez **MT103ReceivePipeline.btp**.</span><span class="sxs-lookup"><span data-stu-id="f3755-111">In the **Name** box, type **MT103ReceivePipeline.btp**.</span></span>  
  
4.  <span data-ttu-id="f3755-112">Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f3755-112">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
 <span data-ttu-id="f3755-113">Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f3755-113">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> <span data-ttu-id="f3755-114">Visual Studio ajoute également le nouveau pipeline de l’Explorateur de solutions sous le projet SWIFTPipelines.</span><span class="sxs-lookup"><span data-stu-id="f3755-114">Visual Studio also adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
 <span data-ttu-id="f3755-115">Passez à [leçon 4 : ajout de SWIFT assembleur et désassembleur à la boîte à outils](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="f3755-115">Proceed to [Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md).</span></span>
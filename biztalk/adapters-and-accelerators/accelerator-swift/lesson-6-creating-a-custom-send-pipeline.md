---
title: "Leçon 6 : Création d’un fichier Pipeline d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom pipelines
- send pipelines, custom pipelines
ms.assetid: 73a3a546-1e43-4b93-87d3-9bfb32685a57
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a82801b0084f2d1b82a2c25cfc0fa2a9f8f1376c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-6-creating-a-custom-send-pipeline"></a><span data-ttu-id="8a57f-102">Leçon 6 : Création d’un Pipeline d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="8a57f-102">Lesson 6: Creating a Custom Send Pipeline</span></span>
<span data-ttu-id="8a57f-103">Dans cette leçon, vous créez un pipeline d’envoi personnalisé à l’aide du Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8a57f-103">In this lesson, you create a custom send pipeline using BizTalk Pipeline Designer.</span></span> <span data-ttu-id="8a57f-104">Un pipeline d’envoi est un pipeline que vous exécutez sur les messages avant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] envoie les messages à leur destination.</span><span class="sxs-lookup"><span data-stu-id="8a57f-104">A send pipeline is a pipeline you run on messages before [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sends the messages to their destination.</span></span>  
  
 <span data-ttu-id="8a57f-105">Vous configurez le pipeline personnalisé pour utiliser le composant assembleur SWIFT (ASM).</span><span class="sxs-lookup"><span data-stu-id="8a57f-105">You configure the custom pipeline to use the SWIFT assembler (ASM) component.</span></span> <span data-ttu-id="8a57f-106">Le module ASM prend en charge un message au format XML et convertit ou sérialise le contenu dans un fichier plat SWIFT.</span><span class="sxs-lookup"><span data-stu-id="8a57f-106">The ASM takes an XML-formatted message and converts or serializes the content into a SWIFT flat file.</span></span> <span data-ttu-id="8a57f-107">Cette conversion est basée sur le schéma MT103 que vous avez créé dans [leçon 3 : ajout d’un Pipeline de réception personnalisé](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="8a57f-107">This conversion is based upon the MT103 schema you created in [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span></span>  
  
### <a name="to-create-a-custom-send-pipeline"></a><span data-ttu-id="8a57f-108">Pour créer un pipeline d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="8a57f-108">To create a custom send pipeline</span></span>  
  
1.  <span data-ttu-id="8a57f-109">Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8a57f-109">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="8a57f-110">Dans la boîte de dialogue Ajouter nouvel élément-SWIFTPipelines, vérifiez que **fichiers de Pipeline** est sélectionné dans le volet des catégories, puis sélectionnez **Pipeline d’envoi** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="8a57f-110">In the Add New Item-SWIFTPipelines dialog box, verify that **Pipeline Files** is selected in the Categories pane, and then select **Send Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="8a57f-111">Dans le **nom** , tapez **MT103SendPipeline.btp**.</span><span class="sxs-lookup"><span data-stu-id="8a57f-111">In the **Name** box, type **MT103SendPipeline.btp**.</span></span>  
  
4.  <span data-ttu-id="8a57f-112">Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8a57f-112">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a57f-113">Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8a57f-113">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="8a57f-114">Ajoute le nouveau pipeline à l’Explorateur de solutions sous le projet SWIFTPipelines.</span><span class="sxs-lookup"><span data-stu-id="8a57f-114"> adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
 <span data-ttu-id="8a57f-115">Passez à [la leçon 7 : ajout de l’assembleur SWIFT personnalisée Pipeline d’envoi](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="8a57f-115">Proceed to [Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md).</span></span>
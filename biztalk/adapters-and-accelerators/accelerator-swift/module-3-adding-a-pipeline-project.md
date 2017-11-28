---
title: "Module 3 : Ajout d’un projet de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorial, creating pipelines
- projects, pipelines
- pipelines, adding to projects
ms.assetid: 38bf1629-df29-4bea-840b-60b354b06430
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d14e0f334514fd35a7f8de963f7fb457e3fbbd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="module-3-adding-a-pipeline-project"></a><span data-ttu-id="854f3-102">Module 3 : Ajout d’un projet de Pipeline</span><span class="sxs-lookup"><span data-stu-id="854f3-102">Module 3: Adding a Pipeline Project</span></span>
<span data-ttu-id="854f3-103">Dans ce module, vous ajoutez un nouveau projet à votre solution qui contient votre envoi personnalisé et des pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="854f3-103">In this module, you add a new project to your solution that contains your custom send and receive pipelines.</span></span> <span data-ttu-id="854f3-104">Étant donné que vous travaillez avec des messages SWIFT, qui sont des fichiers plats par nature, vous ne pouvez pas utiliser les pipelines par défaut qui sont inclus dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="854f3-104">Because you are working with SWIFT messages, which are flat file in nature, you cannot use the default pipelines that are included with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span>  
  
 <span data-ttu-id="854f3-105">Messages SWIFT requièrent des niveaux de validation supplémentaires donc [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] inclut personnalisé (DASM) composants désassembleur et assembleur (ASM) pour une utilisation avec des messages SWIFT.</span><span class="sxs-lookup"><span data-stu-id="854f3-105">SWIFT messages require additional levels of validation so [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes custom disassembler (DASM) and assembler (ASM) components for use with SWIFT messages.</span></span>  
  
 <span data-ttu-id="854f3-106">Dans ce module, vous ajoutez également un nouveau pipeline de projet d’équipe, ajouter de réception et pipelines d’envoi et utiliser le SWIFT DASM et ASM.</span><span class="sxs-lookup"><span data-stu-id="854f3-106">In this module, you also add a new pipeline project, add receive and send pipelines, and use the SWIFT DASM and ASM.</span></span>  
  
 <span data-ttu-id="854f3-107">Sélectionnez le modèle de projet BizTalk expose les outils de BizTalk, tels que le Mappeur BizTalk, dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="854f3-107">Selecting the BizTalk project template exposes the BizTalk tools, such as BizTalk Mapper, within the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] development environment.</span></span>  
  
 <span data-ttu-id="854f3-108">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="854f3-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="854f3-109">Leçon 1 : Ajout d’un projet de Pipelines à la Solution</span><span class="sxs-lookup"><span data-stu-id="854f3-109">Lesson 1: Adding a Pipelines Project to the Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-adding-a-pipelines-project-to-the-solution.md)  
  
-   [<span data-ttu-id="854f3-110">Leçon 2 : Ajout de références de projet</span><span class="sxs-lookup"><span data-stu-id="854f3-110">Lesson 2: Adding Project References</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)  
  
-   [<span data-ttu-id="854f3-111">Leçon 3 : Ajout d’un Pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="854f3-111">Lesson 3: Adding a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="854f3-112">Leçon 4 : Ajout SWIFT assembleur et désassembleur à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="854f3-112">Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md)  
  
-   [<span data-ttu-id="854f3-113">Leçon 5 : Ajouter le désassembleur SWIFT à un Pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="854f3-113">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="854f3-114">Leçon 6 : Création d’un Pipeline d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="854f3-114">Lesson 6: Creating a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="854f3-115">Leçon 7 : Ajout de l’assembleur SWIFT à un Pipeline d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="854f3-115">Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="854f3-116">Leçon 8 : Création et déploiement de l’Assembly</span><span class="sxs-lookup"><span data-stu-id="854f3-116">Lesson 8: Building and Deploying the Assembly</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-8-building-and-deploying-the-assembly.md)
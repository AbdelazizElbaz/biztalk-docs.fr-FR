---
title: Tutorial2 de bout en bout | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorial, about the tutorial
- tutorial
- tutorial, workflow
ms.assetid: 1aba93b9-6991-46ef-a3bc-3815a5ff473f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c4022595ed05cb779d11e09d66080024ac76654
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="e070e-102">Didacticiel de bout en bout</span><span class="sxs-lookup"><span data-stu-id="e070e-102">End-to-End Tutorial</span></span>
<span data-ttu-id="e070e-103">Ce didacticiel contient des procédures détaillées qui expliquent comment créer et configurer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="e070e-103">This tutorial contains detailed steps that describe how to create and set up a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] solution.</span></span> <span data-ttu-id="e070e-104">L’utilisation de modules et des leçons [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] pour créer le schéma, mappe les orchestrations et les composants de pipeline à l’aide d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="e070e-104">The modules and lessons use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create the schema, maps orchestrations, and pipeline components using A4SWIFT.</span></span>  
  
 <span data-ttu-id="e070e-105">La figure suivante illustre le flux de travail d’un scénario d’utilisation de moteur d’intégration courantes pour une solution d’A4SWIFT de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="e070e-105">The following figure shows the workflow of a common Integration Engine usage scenario for an end-to-end A4SWIFT solution.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-tut-wklw.gif "FSA_Tut_wklw")  
  
|<span data-ttu-id="e070e-106">Clé de flux de travail didacticiel A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="e070e-106">A4SWIFT Tutorial Workflow Key</span></span>|  
|-----------------------------------|  
|<span data-ttu-id="e070e-107">**ASM** = assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="e070e-107">**ASM** = SWIFT Assembler</span></span>|  
|<span data-ttu-id="e070e-108">**DASM** = désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="e070e-108">**DASM** = SWIFT Disassembler</span></span>|  
|<span data-ttu-id="e070e-109">**MTxxx** = type de Message d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="e070e-109">**MTxxx** = A4SWIFT Message type</span></span>|  
|<span data-ttu-id="e070e-110">**SIPN** = réseau IP sécurisé SWIFT</span><span class="sxs-lookup"><span data-stu-id="e070e-110">**SIPN** = SWIFT Secure IP Network</span></span>|  
  
 <span data-ttu-id="e070e-111">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="e070e-111">This section contains:</span></span>  
  
-   [<span data-ttu-id="e070e-112">Module 1 : Création d’une Solution rapide</span><span class="sxs-lookup"><span data-stu-id="e070e-112">Module 1: Creating a SWIFT Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/module-1-creating-a-swift-solution.md)  
  
-   [<span data-ttu-id="e070e-113">Module 2 : Ajout d’un nouveau projet de schémas</span><span class="sxs-lookup"><span data-stu-id="e070e-113">Module 2: Adding a New Schemas Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)  
  
-   [<span data-ttu-id="e070e-114">Module 3 : Ajout d’un projet de Pipeline</span><span class="sxs-lookup"><span data-stu-id="e070e-114">Module 3: Adding a Pipeline Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)  
  
-   [<span data-ttu-id="e070e-115">Module 4 : Ajout d’un document XML emplacement de réception et Port d’envoi de fichier plat</span><span class="sxs-lookup"><span data-stu-id="e070e-115">Module 4: Adding an XML Receive Location and Flat File Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)  
  
-   [<span data-ttu-id="e070e-116">Module 5 : Ajout d’un fichier plat emplacement de réception et le Port d’envoi XML</span><span class="sxs-lookup"><span data-stu-id="e070e-116">Module 5: Adding a Flat File Receive Location and XML Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)  
  
-   [<span data-ttu-id="e070e-117">Module 6 : Déployer les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="e070e-117">Module 6: Deploying the Business Rules</span></span>](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)  
  
-   [<span data-ttu-id="e070e-118">Module 7 : Tester une Instance valide de fichier plat</span><span class="sxs-lookup"><span data-stu-id="e070e-118">Module 7: Testing a Valid Flat File Instance</span></span>](../../adapters-and-accelerators/accelerator-swift/module-7-testing-a-valid-flat-file-instance.md)
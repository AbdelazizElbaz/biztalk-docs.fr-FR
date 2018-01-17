---
title: "Leçon 4 : Création et déploiement de l’Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ca5a539fdaea9026a7c18cae6f076e72df9efe2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a><span data-ttu-id="91dd0-102">Leçon 4 : Création et déploiement de l’Assembly</span><span class="sxs-lookup"><span data-stu-id="91dd0-102">Lesson 4: Building and Deploying the Assembly</span></span>
<span data-ttu-id="91dd0-103">Dans cette leçon, vous générez et déployez le projet pour générer un assembly qui contient les schémas que vous avez créé dans les leçons précédentes.</span><span class="sxs-lookup"><span data-stu-id="91dd0-103">In this lesson, you build and deploy the project to generate an assembly that contains the schemas you created in the previous lessons.</span></span> <span data-ttu-id="91dd0-104">Cette tâche s’assure aucune erreur de compilation dans le travail que vous avez créé jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="91dd0-104">This task ensures there are no compilation errors in the work you created so far.</span></span>  
  
 <span data-ttu-id="91dd0-105">Déploiement d’un assembly place une copie de l’assembly dans la base de données de Configuration et l’installe dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="91dd0-105">Deploying an assembly places a copy of the assembly in the Configuration database and installs it in the global assembly cache (GAC).</span></span> <span data-ttu-id="91dd0-106">Dans la procédure suivante, vous déployez directement à partir de l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="91dd0-106">In the following procedure, you deploy directly from Solution Explorer.</span></span>  
  
 <span data-ttu-id="91dd0-107">Lorsque le projet se compile dans un assembly (fichier DLL), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] enregistre la DLL dans le \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour Dossier SWIFT\bin\Development dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="91dd0-107">When the project compiles into an assembly (DLL file), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] saves the DLL in the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for SWIFT\bin\Development folder within the project folder.</span></span>  
  
### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="91dd0-108">Pour créer et déployer le projet</span><span class="sxs-lookup"><span data-stu-id="91dd0-108">To build and deploy the project</span></span>  
  
1.  <span data-ttu-id="91dd0-109">Dans l’Explorateur de solutions, cliquez sur **SWIFTSchemas**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="91dd0-109">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91dd0-110">Vérifiez que **génération a réussi** s’affiche dans le coin inférieur gauche de l’écran.</span><span class="sxs-lookup"><span data-stu-id="91dd0-110">Verify that **Build Succeeded** appears in the lower left-hand corner of the screen.</span></span> <span data-ttu-id="91dd0-111">Pendant le processus de compilation, vous pouvez voir certains messages d’état.</span><span class="sxs-lookup"><span data-stu-id="91dd0-111">During the compilation process, you may see some status messages.</span></span> <span data-ttu-id="91dd0-112">Ces messages sont normaux lorsque vous traitez des schémas SWIFT.</span><span class="sxs-lookup"><span data-stu-id="91dd0-112">These messages are normal when dealing with the SWIFT schemas.</span></span> <span data-ttu-id="91dd0-113">Si des erreurs s’affiche, cliquez sur Outils, puis cliquez sur Administration de BizTalk Server pour ouvrir la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="91dd0-113">If any errors appear, click Tools, and then click BizTalk Server Administration to open the BizTalk Server Administration Console.</span></span> <span data-ttu-id="91dd0-114">Utilisez la fonctionnalité de l’Observateur d’événements et l’intégrité et l’activité de suivi du fonctionnement (HAT) dans la Console Administration de BizTalk pour corriger les erreurs et la régénérer.</span><span class="sxs-lookup"><span data-stu-id="91dd0-114">Use the Event Viewer and the Health and Activity Tracking (HAT) feature in the BizTalk Administration Console to correct your errors and rebuild.</span></span>  
  
2.  <span data-ttu-id="91dd0-115">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\< *lecteur*\>: \labs\SWIFTProject\SWIFTSchemas\bin\Development** dossier et vérifiez que le  **SWIFTSchemas.dll** fichier existe dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="91dd0-115">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\labs\SWIFTProject\SWIFTSchemas\bin\Development** folder, and verify that the **SWIFTSchemas.dll** file exists in this folder.</span></span>  
  
3.  <span data-ttu-id="91dd0-116">Dans l’Explorateur de solutions, cliquez sur **SWIFTSchemas**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="91dd0-116">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91dd0-117">Vérifiez que **déploiement réussi** s’affiche dans l’angle inférieur gauche de l’écran.</span><span class="sxs-lookup"><span data-stu-id="91dd0-117">Verify that **Deploy Succeeded** appears in the lower left corner of the screen.</span></span>  
  
### <a name="to-confirm-deployment-success"></a><span data-ttu-id="91dd0-118">Pour confirmer la réussite du déploiement</span><span class="sxs-lookup"><span data-stu-id="91dd0-118">To confirm deployment success</span></span>  
  
1.  <span data-ttu-id="91dd0-119">Cliquez sur **vue** puis cliquez sur **l’Explorateur BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="91dd0-119">Click **View** and then click **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="91dd0-120">Développez le **assemblys** nœud et vérifiez que **SWIFTSchemas (1.0.0.0)** apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="91dd0-120">Expand the **Assemblies** node and confirm that **SWIFTSchemas (1.0.0.0)** appears in the list.</span></span>  
  
     <span data-ttu-id="91dd0-121">Si SWIFTSchemas apparaît dans la liste, l’assembly a été correctement déployé et peut être référencé et utilisé à partir d’autres [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets.</span><span class="sxs-lookup"><span data-stu-id="91dd0-121">If SWIFTSchemas appears in the list, the assembly deployed successfully and can be referenced and used from other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects.</span></span>  
  
 <span data-ttu-id="91dd0-122">Passez à [Module 3 : ajout d’un projet de Pipeline](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).</span><span class="sxs-lookup"><span data-stu-id="91dd0-122">Proceed to [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).</span></span>
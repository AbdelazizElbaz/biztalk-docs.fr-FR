---
title: "Comment créer des Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building, orchestrations
- building, solutions
- building, projects
- solutions, building
- projects, building
- orchestrations, building
ms.assetid: f12d5da0-fbae-4f0e-85bf-1ca2e9bf7d62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79e91ec6ecfa061aa4621effba9a1f868cad5d96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-build-orchestrations"></a><span data-ttu-id="9e605-102">Création d'orchestrations</span><span class="sxs-lookup"><span data-stu-id="9e605-102">How to Build Orchestrations</span></span>
<span data-ttu-id="9e605-103">Après avoir terminé le dessin d'une orchestration, vous construisez votre projet BizTalk dans un assembly qui encapsule une orchestration exécutable.</span><span class="sxs-lookup"><span data-stu-id="9e605-103">After you have completed an orchestration drawing, you build your BizTalk project into an assembly that encapsulates an executable orchestration.</span></span>  
  
 <span data-ttu-id="9e605-104">Pendant le processus de construction, le Concepteur d'Orchestration BizTalk examine chaque forme pour déterminer si elle est complète et correcte, et signale une erreur dans la liste des tâches si ce n'est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="9e605-104">During the build process, BizTalk Orchestration Designer examines each shape to determine whether it is complete and correct, and reports an error in the task list if it is not.</span></span>  
  
 <span data-ttu-id="9e605-105">Il existe plusieurs options de construction dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="9e605-105">You have several options for building in Visual Studio:</span></span>  
  
-   <span data-ttu-id="9e605-106">Vous pouvez construire l'ensemble de la solution dans laquelle votre orchestration réside.</span><span class="sxs-lookup"><span data-stu-id="9e605-106">You can build the entire solution in which your orchestration resides.</span></span>  
  
-   <span data-ttu-id="9e605-107">Vous pouvez construire un projet unique au sein de la solution.</span><span class="sxs-lookup"><span data-stu-id="9e605-107">You can build a single project within the solution.</span></span>  
  
-   <span data-ttu-id="9e605-108">Vous pouvez ignorer l'orchestration lorsque vous construisez le projet ou la solution.</span><span class="sxs-lookup"><span data-stu-id="9e605-108">You can skip the orchestration when building the project or solution.</span></span>  
  
 <span data-ttu-id="9e605-109">Si vous voulez construire d'autres composants, dont d'autres orchestrations, mais pas une orchestration en particulier, vous pouvez indiquer dans les propriétés de fichier du fichier .odx de cette orchestration que vous ne souhaitez pas la construire. Elle sera alors ignorée.</span><span class="sxs-lookup"><span data-stu-id="9e605-109">If you want to build other components, including other orchestrations, but do not want to build a particular orchestration, you can indicate in the file properties for the orchestration's .odx file that you do not want to build it, and it will be skipped.</span></span>  
  
### <a name="to-build-an-orchestration"></a><span data-ttu-id="9e605-110">Pour construire une orchestration</span><span class="sxs-lookup"><span data-stu-id="9e605-110">To build an orchestration</span></span>  
  
-   <span data-ttu-id="9e605-111">Après avoir créé votre orchestration, vous devez construire le projet BizTalk qui la contient avant de pouvoir la tester ou l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="9e605-111">After creating your orchestration, you need to build the BizTalk project that contains it before you can test or use the orchestration.</span></span> <span data-ttu-id="9e605-112">Vous pouvez construire l'ensemble de la solution ou un projet unique au sein de la solution.</span><span class="sxs-lookup"><span data-stu-id="9e605-112">You can build the entire solution, or a single project within the solution.</span></span>  
  
### <a name="to-build-a-solution"></a><span data-ttu-id="9e605-113">Pour construire une solution</span><span class="sxs-lookup"><span data-stu-id="9e605-113">To build a solution</span></span>  
  
-   <span data-ttu-id="9e605-114">Dans l’Explorateur de solutions, cliquez sur la solution et sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="9e605-114">In Solution Explorer, right-click the solution and select **Build Solution**.</span></span>  
  
### <a name="to-build-a-project"></a><span data-ttu-id="9e605-115">Pour construire un projet</span><span class="sxs-lookup"><span data-stu-id="9e605-115">To build a project</span></span>  
  
-   <span data-ttu-id="9e605-116">Cliquez sur un projet et sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="9e605-116">Right-click a project and select **Build**.</span></span>  
  
### <a name="to-build-a-project-or-solution-without-compiling-a-particular-orchestration"></a><span data-ttu-id="9e605-117">Pour générer un projet ou une solution sans compiler une orchestration en particulier</span><span class="sxs-lookup"><span data-stu-id="9e605-117">To build a project or solution without compiling a particular orchestration</span></span>  
  
-   <span data-ttu-id="9e605-118">Cliquez sur le fichier .odx correspondant à l’orchestration et dans la fenêtre Propriétés, cliquez sur le **Action de génération** et sélectionnez **aucun**.</span><span class="sxs-lookup"><span data-stu-id="9e605-118">Click the .odx file corresponding to the orchestration, and in the Properties window, click the **Build Action** property and select **None**.</span></span>
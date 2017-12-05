---
title: "Considérations relatives à la création de projets BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, size
- map type name
- projects, naming conventions
- projects, planning
ms.assetid: f6c3dc71-105f-46af-9e6e-9a4c3b982d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0302d2329f848352f55d15f0c6e21bbdf72b0ca
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="considerations-when-creating-biztalk-projects"></a><span data-ttu-id="fe305-102">Considérations à prendre en compte lors de la création de projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="fe305-102">Considerations When Creating BizTalk Projects</span></span>
<span data-ttu-id="fe305-103">Cette section fournit des informations à prendre en compte lors de la création de projets BizTalk à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe305-103">This section provides information that you should take into consideration when creating BizTalk projects using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="avoid-compilation-errors-caused-by-projects-that-are-too-large"></a><span data-ttu-id="fe305-104">Éviter les erreurs de compilation causées par des projets trop volumineux</span><span class="sxs-lookup"><span data-stu-id="fe305-104">Avoid compilation errors caused by projects that are too large</span></span>  
 <span data-ttu-id="fe305-105">Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ne réussira pas la compilation d’un projet si elle donne lieu à un assembly supérieur à 75 Mo.</span><span class="sxs-lookup"><span data-stu-id="fe305-105">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler will not successfully compile a project if it would result in an assembly larger than 75 megabytes.</span></span> <span data-ttu-id="fe305-106">Lorsque le compilateur atteint une contrainte de taille elle émet l’erreur irrécupérable CS0013 « erreur inattendue lors de l’écriture au fichier \<nom de fichier\>» et s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="fe305-106">When the compiler reaches a size constraint it will emit fatal error CS0013 "Unexpected error writing metadata to file \<filename\>" and halt.</span></span>  
  
 <span data-ttu-id="fe305-107">Afin d’éviter ce problème, nous préconisons que les projets n’excèdent pas 10 Mo, sauf en cas de nécessité absolue.</span><span class="sxs-lookup"><span data-stu-id="fe305-107">To avoid this problem, we recommend that projects not exceed 10 megabytes unless absolutely necessary.</span></span> <span data-ttu-id="fe305-108">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="fe305-108">Why?</span></span>  
  
-   <span data-ttu-id="fe305-109">Les projets plus petits sont potentiellement plus simples à déployer en raison du nombre limité d’étapes de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fe305-109">Smaller projects are potentially simpler to deploy because there are fewer deployment steps.</span></span> <span data-ttu-id="fe305-110">Et ces étapes ont des chances d’être étroitement liées, par exemple, la gestion des remises des partenaires commerciaux ou la gestion des appels d'offres.</span><span class="sxs-lookup"><span data-stu-id="fe305-110">And with smaller projects the steps are more likely to be closely related -- managing trading partner discounts or handling RFPs.</span></span>  
  
-   <span data-ttu-id="fe305-111">Il est plus facile d’identifier les bogues, les problèmes de déploiement et autres lors de l’utilisation de projets plus petits.</span><span class="sxs-lookup"><span data-stu-id="fe305-111">It is easier to isolate bugs, deployment issues, and other problems when using smaller projects.</span></span> <span data-ttu-id="fe305-112">Repérer un bogue dans un projet comportant 140 schémas et de nombreux mappages et scripts personnalisés sera beaucoup plus difficile que dans un projet ne comprenant que 10 schémas et quelques mappages et scripts personnalisés.</span><span class="sxs-lookup"><span data-stu-id="fe305-112">Finding a bug in a project with 140 schemas and many custom maps and scripts will be more difficult than finding one in a project with only 10 schemas and a few custom maps and scripts.</span></span>  
  
-   <span data-ttu-id="fe305-113">La division d’un gros projet en plus petits projets peut permettre de réduire la complexité.</span><span class="sxs-lookup"><span data-stu-id="fe305-113">Separating a large project into smaller projects can reduce complexity.</span></span> <span data-ttu-id="fe305-114">Les projets de plus petite taille sont plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="fe305-114">The smaller projects are more manageable.</span></span>  
  
-   <span data-ttu-id="fe305-115">La compilation des projets plus petits est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="fe305-115">Smaller projects compile faster.</span></span>  
  
-   <span data-ttu-id="fe305-116">La division d’un gros projet comportant de nombreux schémas non apparentés en projets plus petits avec des schémas étroitement liés peut améliorer les performances,</span><span class="sxs-lookup"><span data-stu-id="fe305-116">Splitting a large project with many unrelated schemas into smaller projects with strongly related schemas may result in better performance.</span></span> <span data-ttu-id="fe305-117">Il s’agit, car seules certaines des assemblys seront chargé à la fois.</span><span class="sxs-lookup"><span data-stu-id="fe305-117">This is because only some of the assemblies will be loaded at a time.</span></span>  
  
## <a name="avoid-using-the-project-name-as-the-map-type-name"></a><span data-ttu-id="fe305-118">Éviter d’utiliser le nom de projet comme nom de type de mappage</span><span class="sxs-lookup"><span data-stu-id="fe305-118">Avoid using the Project Name as the Map Type Name</span></span>  
 <span data-ttu-id="fe305-119">Lors de l’ajout d’un nouveau mappage à un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], n’utilisez pas le nom du projet comme nom de type.</span><span class="sxs-lookup"><span data-stu-id="fe305-119">When adding a new map to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not use the project name as the type name.</span></span> <span data-ttu-id="fe305-120">Dans ce cas, le compilateur génère une ou plusieurs erreurs semblables à « le nom de type \<nom\>' n’existe pas dans le type ».</span><span class="sxs-lookup"><span data-stu-id="fe305-120">If you do, the compiler will generate one or more errors similar to "The type name \<name\>' does not exist in the type".</span></span>  
  
 <span data-ttu-id="fe305-121">Pour modifier le nom de type pour un mappage à partir d’un projet BizTalk, cliquez sur la carte dans le volet Explorateur de solutions, puis vérifiez la propriété de nom de type dans le volet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="fe305-121">To change the type name for a map from within a BizTalk project, click the map in the Solution Explorer pane, then verify the type name property in the Properties pane.</span></span> <span data-ttu-id="fe305-122">Si elle est identique, vous devez la modifier en veillant à changer les configurations associées.</span><span class="sxs-lookup"><span data-stu-id="fe305-122">If it is the same, you need to modify it making sure to change any configurations that rely on it.</span></span>  
  
## <a name="visual-studio-team-system-support"></a><span data-ttu-id="fe305-123">Prise en charge de Visual Studio Team System</span><span class="sxs-lookup"><span data-stu-id="fe305-123">Visual Studio Team System Support</span></span>  
 <span data-ttu-id="fe305-124">Les projets BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ne prennent pas directement en charge l'ensemble des composants de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System.</span><span class="sxs-lookup"><span data-stu-id="fe305-124">BizTalk projects in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] do not directly support all features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System.</span></span> <span data-ttu-id="fe305-125">Les fonctionnalités de contrôle de source de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System sont pris en charge pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe305-125">The source control features of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System are supported for BizTalk Server.</span></span> <span data-ttu-id="fe305-126">Visual Source Safe est également entièrement pris en charge pour le suivi et la gestion des versions des artefacts de projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fe305-126">Visual SourceSafe is also fully supported for the tracking and versioning of BizTalk project artifacts.</span></span>
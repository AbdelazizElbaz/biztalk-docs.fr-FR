---
title: "Installation de l’exemple de Service de programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b06c7383dee805612a3f599148f1d631891ace79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-resolver-service-sample"></a><span data-ttu-id="2be29-102">Installation de l’exemple de Service de programme de résolution</span><span class="sxs-lookup"><span data-stu-id="2be29-102">Installing the Resolver Service Sample</span></span>
<span data-ttu-id="2be29-103">Cette section décrit le processus d’installation de l’exemple de Service de résolution.</span><span class="sxs-lookup"><span data-stu-id="2be29-103">This section describes the process for installing the Resolver Service sample.</span></span> <span data-ttu-id="2be29-104">Le Service de résolution varie selon le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] solution de base.</span><span class="sxs-lookup"><span data-stu-id="2be29-104">The Resolver Service depends on the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core solution.</span></span> <span data-ttu-id="2be29-105">L’installation de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core copie automatiquement et installe les principaux assemblys requis par cet exemple, les emplacements corrects.</span><span class="sxs-lookup"><span data-stu-id="2be29-105">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the core assemblies required by this sample to the correct locations.</span></span>  
  
 <span data-ttu-id="2be29-106">**Pour installer l’exemple de Service de résolution à partir du projet de la solution**</span><span class="sxs-lookup"><span data-stu-id="2be29-106">**To install the Resolver Service sample from the solution project**</span></span>  
  
1.  <span data-ttu-id="2be29-107">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService\Install\Scripts.</span><span class="sxs-lookup"><span data-stu-id="2be29-107">In Windows Explorer, open the \Source\Samples\ResolverService\Install\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="2be29-108">Double-cliquez sur le fichier Setup_bin.cmd.</span><span class="sxs-lookup"><span data-stu-id="2be29-108">Double-click the Setup_bin.cmd file.</span></span>  
  
3.  <span data-ttu-id="2be29-109">Pour confirmer la réussite de l’installation de l’exemple, ou si vous rencontrez des problèmes lorsque vous exécutez des applications, vous pouvez utiliser la liste fournie dans le tableau suivant pour vérifier la présence d’assemblys requis et d’autres artefacts.</span><span class="sxs-lookup"><span data-stu-id="2be29-109">To confirm successful installation of the sample, or if you are encountering issues when you run applications, you can use the list provided in the following table to check for the presence of the required assemblies and other artifacts.</span></span>  
  
|<span data-ttu-id="2be29-110">Emplacement</span><span class="sxs-lookup"><span data-stu-id="2be29-110">Location</span></span>|<span data-ttu-id="2be29-111">Catégorie</span><span class="sxs-lookup"><span data-stu-id="2be29-111">Category</span></span>|<span data-ttu-id="2be29-112">Nom et la version du composant</span><span class="sxs-lookup"><span data-stu-id="2be29-112">Name and version of the component</span></span>|  
|--------------|--------------|---------------------------------------|  
|<span data-ttu-id="2be29-113">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-113">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-114">Orchestrations</span><span class="sxs-lookup"><span data-stu-id="2be29-114">Orchestrations</span></span>|<span data-ttu-id="2be29-115">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-115">(none)</span></span>|  
|<span data-ttu-id="2be29-116">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-116">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-117">Ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="2be29-117">Send Ports</span></span>|<span data-ttu-id="2be29-118">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-118">(none)</span></span>|  
|<span data-ttu-id="2be29-119">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-119">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-120">Ports de réception</span><span class="sxs-lookup"><span data-stu-id="2be29-120">Receive Ports</span></span>|<span data-ttu-id="2be29-121">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-121">(none)</span></span>|  
|<span data-ttu-id="2be29-122">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-122">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-123">Emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="2be29-123">Receive Locations</span></span>|<span data-ttu-id="2be29-124">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-124">(none)</span></span>|  
|<span data-ttu-id="2be29-125">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-125">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-126">Schémas</span><span class="sxs-lookup"><span data-stu-id="2be29-126">Schemas</span></span>|<span data-ttu-id="2be29-127">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-127">(none)</span></span>|  
|<span data-ttu-id="2be29-128">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-128">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-129">Pipelines</span><span class="sxs-lookup"><span data-stu-id="2be29-129">Pipelines</span></span>|<span data-ttu-id="2be29-130">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-130">(none)</span></span>|  
|<span data-ttu-id="2be29-131">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-131">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-132">Ressources</span><span class="sxs-lookup"><span data-stu-id="2be29-132">Resources</span></span>|<span data-ttu-id="2be29-133">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-133">(none)</span></span>|  
|<span data-ttu-id="2be29-134">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-134">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-135">Stratégies</span><span class="sxs-lookup"><span data-stu-id="2be29-135">Policies</span></span>|<span data-ttu-id="2be29-136">ResolveEndpoint</span><span class="sxs-lookup"><span data-stu-id="2be29-136">ResolveEndpoint</span></span>|  
|||<span data-ttu-id="2be29-137">ResolveMap</span><span class="sxs-lookup"><span data-stu-id="2be29-137">ResolveMap</span></span>|  
|<span data-ttu-id="2be29-138">Application BizTalk GlobalBank.ESB</span><span class="sxs-lookup"><span data-stu-id="2be29-138">BizTalk application GlobalBank.ESB</span></span>|<span data-ttu-id="2be29-139">Cartes</span><span class="sxs-lookup"><span data-stu-id="2be29-139">Maps</span></span>|<span data-ttu-id="2be29-140">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-140">(none)</span></span>|  
|<span data-ttu-id="2be29-141">Cache d’assembly global</span><span class="sxs-lookup"><span data-stu-id="2be29-141">Global assembly cache</span></span>|<span data-ttu-id="2be29-142">Assemblys</span><span class="sxs-lookup"><span data-stu-id="2be29-142">Assemblies</span></span>|<span data-ttu-id="2be29-143">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-143">(none)</span></span>|  
|<span data-ttu-id="2be29-144">%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline composants</span><span class="sxs-lookup"><span data-stu-id="2be29-144">%Program Files%\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline Components</span></span>|<span data-ttu-id="2be29-145">Composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="2be29-145">Pipeline components</span></span>|<span data-ttu-id="2be29-146">(aucun)</span><span class="sxs-lookup"><span data-stu-id="2be29-146">(none)</span></span>|
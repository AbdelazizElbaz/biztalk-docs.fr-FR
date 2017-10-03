---
title: "Résolution du tiers personnalisé (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, parties
- pipeline components [custom], examples
- pipeline components [custom], parties
- examples, pipeline components [custom]
- parties, pipeline components [custom]
- parties, custom
ms.assetid: 1f88450f-5fe9-486d-bfb8-fd11181c78b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b88d8126a1d63760888edbcd7691ad4bd76426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-party-resolution-biztalk-server-sample"></a><span data-ttu-id="5aa7e-102">Résolution du tiers personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5aa7e-102">Custom Party Resolution (BizTalk Server Sample)</span></span>
<span data-ttu-id="5aa7e-103">L'exemple Custom Party Resolution décrit l'écriture d'un composant de pipeline personnalisé pour résoudre un tiers personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-103">The Custom Party Resolution sample demonstrates how to write a custom pipeline component to resolve a custom party.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5aa7e-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5aa7e-104">What This Sample Does</span></span>  
 <span data-ttu-id="5aa7e-105">L'exemple Custom Party Resolution accomplit sa tâche en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="5aa7e-105">The Custom Party Resolution sample accomplishes its task using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="5aa7e-106">Un document XML est extrait d'un dossier.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-106">An XML document is retrieved from a folder.</span></span>  
  
2.  <span data-ttu-id="5aa7e-107">Le pipeline résout le tiers.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-107">The pipeline resolves the party.</span></span>  
  
3.  <span data-ttu-id="5aa7e-108">Le message XML est écrit dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-108">The XML message is written to a folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5aa7e-109">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5aa7e-109">Where to Find This Sample</span></span>  
 <span data-ttu-id="5aa7e-110">*\<Exemples de chemin d’accès >*\Pipelines\CustomPartyResolution\\</span><span class="sxs-lookup"><span data-stu-id="5aa7e-110">*\<Samples Path>*\Pipelines\CustomPartyResolution\\</span></span>  
  
 <span data-ttu-id="5aa7e-111">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-111">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5aa7e-112">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5aa7e-112">File(s)</span></span>|<span data-ttu-id="5aa7e-113"> Description</span><span class="sxs-lookup"><span data-stu-id="5aa7e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5aa7e-114">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="5aa7e-114">AssemblyInfo.cs</span></span>|<span data-ttu-id="5aa7e-115">Fichier source C# d'informations de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-115">Assembly information C# source file.</span></span>|  
|<span data-ttu-id="5aa7e-116">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5aa7e-116">Cleanup.bat</span></span>|<span data-ttu-id="5aa7e-117">Fichier de commandes de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-117">Cleanup batch file.</span></span>|  
|<span data-ttu-id="5aa7e-118">CustomPartyResolution.sln</span><span class="sxs-lookup"><span data-stu-id="5aa7e-118">CustomPartyResolution.sln</span></span>|<span data-ttu-id="5aa7e-119">Fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-119">Solution file.</span></span>|  
|<span data-ttu-id="5aa7e-120">CustomPartyResolutionBinding.xml</span><span class="sxs-lookup"><span data-stu-id="5aa7e-120">CustomPartyResolutionBinding.xml</span></span>|<span data-ttu-id="5aa7e-121">Fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-121">Binding file.</span></span>|  
|<span data-ttu-id="5aa7e-122">CustomPartyResolutionPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="5aa7e-122">CustomPartyResolutionPipeline.btp</span></span>|<span data-ttu-id="5aa7e-123">Fichier de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-123">Pipeline file.</span></span>|  
|<span data-ttu-id="5aa7e-124">CustomPartyResolutionPipeline.btproj</span><span class="sxs-lookup"><span data-stu-id="5aa7e-124">CustomPartyResolutionPipeline.btproj</span></span>|<span data-ttu-id="5aa7e-125">Fichier de projet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-125">Pipeline project file.</span></span>|  
|<span data-ttu-id="5aa7e-126">CustomPartyResolutionPipelineComponent.cs</span><span class="sxs-lookup"><span data-stu-id="5aa7e-126">CustomPartyResolutionPipelineComponent.cs</span></span>|<span data-ttu-id="5aa7e-127">Code source C# du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-127">Pipeline component C# source code.</span></span>|  
|<span data-ttu-id="5aa7e-128">CustomPartyResolutionPipelineComponent.csproj</span><span class="sxs-lookup"><span data-stu-id="5aa7e-128">CustomPartyResolutionPipelineComponent.csproj</span></span>|<span data-ttu-id="5aa7e-129">Fichier de projet Visual Studio du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-129">Pipeline component Visual Studio project file.</span></span>|  
|<span data-ttu-id="5aa7e-130">InboundDocumentSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5aa7e-130">InboundDocumentSchema.xsd</span></span>|<span data-ttu-id="5aa7e-131">Schéma de document entrant.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-131">Inbound document schema.</span></span>|  
|<span data-ttu-id="5aa7e-132">PartyResolutionStream.cs</span><span class="sxs-lookup"><span data-stu-id="5aa7e-132">PartyResolutionStream.cs</span></span>|<span data-ttu-id="5aa7e-133">Code source C# du flux de résolution de tiers.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-133">Party resolution stream C# source code.</span></span>|  
|<span data-ttu-id="5aa7e-134">RoutingPropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5aa7e-134">RoutingPropertySchema.xsd</span></span>|<span data-ttu-id="5aa7e-135">Fichier de schéma de propriété de routage.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-135">Routing property schema file.</span></span>|  
|<span data-ttu-id="5aa7e-136">SampleInboundDocumentSchema.xml</span><span class="sxs-lookup"><span data-stu-id="5aa7e-136">SampleInboundDocumentSchema.xml</span></span>|<span data-ttu-id="5aa7e-137">Fichier de schéma de document entrant.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-137">Inbound document schema file.</span></span>|  
|<span data-ttu-id="5aa7e-138">SampleInboundDocumentSchema_Party1.xml</span><span class="sxs-lookup"><span data-stu-id="5aa7e-138">SampleInboundDocumentSchema_Party1.xml</span></span>|<span data-ttu-id="5aa7e-139">Exemple d'instance de données.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-139">Sample data instance.</span></span>|  
|<span data-ttu-id="5aa7e-140">SampleInboundDocumentSchema_Party2.xml</span><span class="sxs-lookup"><span data-stu-id="5aa7e-140">SampleInboundDocumentSchema_Party2.xml</span></span>|<span data-ttu-id="5aa7e-141">Exemple d'instance de données.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-141">Sample data instance.</span></span>|  
|<span data-ttu-id="5aa7e-142">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5aa7e-142">Setup.bat</span></span>|<span data-ttu-id="5aa7e-143">Fichier de commandes de l'exemple de composant de pipeline de création et de configuration</span><span class="sxs-lookup"><span data-stu-id="5aa7e-143">Build and setup sample pipeline component batch file.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5aa7e-144">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5aa7e-144">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-custom-party-resolution-sample"></a><span data-ttu-id="5aa7e-145">Pour créer et initialiser l'exemple Custom Party Resolution</span><span class="sxs-lookup"><span data-stu-id="5aa7e-145">To build and initialize the Custom Party Resolution sample</span></span>  
  
1.  <span data-ttu-id="5aa7e-146">Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5aa7e-146">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="5aa7e-147">*\<Exemples de chemin d’accès >*\Pipelines\CustomPartyResolution\\</span><span class="sxs-lookup"><span data-stu-id="5aa7e-147">*\<Samples Path>*\Pipelines\CustomPartyResolution\\</span></span>  
  
2.  <span data-ttu-id="5aa7e-148">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5aa7e-148">Run the file Setup.bat, which will perform the following actions:</span></span>  
  
    -   <span data-ttu-id="5aa7e-149">crée les répertoires d'entrée et de sortie utilisés dans l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="5aa7e-149">Creates the input and output directories used in the sample.</span></span>  
  
    -   <span data-ttu-id="5aa7e-150">Création d'un nouveau fichier clé ;</span><span class="sxs-lookup"><span data-stu-id="5aa7e-150">Generates a new key file.</span></span>  
  
    -   <span data-ttu-id="5aa7e-151">crée et déploie le composant de pipeline Custom Party Resolution ;</span><span class="sxs-lookup"><span data-stu-id="5aa7e-151">Builds and deploys the Custom Party Resolution pipeline component.</span></span>  
  
    -   <span data-ttu-id="5aa7e-152">Copie le composant de pipeline créé à le  *\<chemin d’Installation >*répertoire \Pipeline Components.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-152">Copies the built pipeline component to the *\<Installation Path>*\Pipeline Components directory.</span></span>  
  
    -   <span data-ttu-id="5aa7e-153">crée les ports d'envoi et de réception ;</span><span class="sxs-lookup"><span data-stu-id="5aa7e-153">Creates the send and receive ports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aa7e-154">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-154">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="5aa7e-155">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5aa7e-155">Running This Sample</span></span>  
  
#### <a name="to-run-the-custom-party-resolution-sample"></a><span data-ttu-id="5aa7e-156">Pour exécuter l'exemple Custom Party Resolution</span><span class="sxs-lookup"><span data-stu-id="5aa7e-156">To run the Custom Party Resolution sample</span></span>  
  
1.  <span data-ttu-id="5aa7e-157">Copiez le fichier SampleInboundDocumentSchema_Party1.xml ou SampleInboundDocumentSchema_Party2.xml dans le dossier \In.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-157">Copy to file SampleInboundDocumentSchema_Party1.xml or SampleInboundDocumentSchema_Party2.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="5aa7e-158">Les résultats s’affichent dans le dossier \Out avec le nom de fichier *guid*.xml.</span><span class="sxs-lookup"><span data-stu-id="5aa7e-158">The results will appear in the \Out folder with the filename *guid*.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa7e-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aa7e-159">See Also</span></span>  
 [<span data-ttu-id="5aa7e-160">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5aa7e-160">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)
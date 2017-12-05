---
title: Composant Schema Resolver (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], examples
- examples, schemas
- schemas, examples
- examples, Flat File Disassembler [pipeline component]
ms.assetid: 9ef68988-c4ee-42d5-83b5-a5c978b2007d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b59a0606b3cb30827078e28a89d0a51f52c430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="schema-resolver-component-biztalk-server-sample"></a><span data-ttu-id="ad027-102">Composant Schema Resolver (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ad027-102">Schema Resolver Component (BizTalk Server Sample)</span></span>
<span data-ttu-id="ad027-103">L'exemple de composant Schema Resolver illustre l'extension des fonctionnalités du composant Désassembleur de fichier plat de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad027-103">The Schema Resolver Component sample demonstrates how to extend the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] flat file disassembler component.</span></span>  
  
 <span data-ttu-id="ad027-104">Le composant Désassembleur de fichier plat nécessite généralement de définir un schéma d'analyse au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="ad027-104">The flat file disassembler component normally requires you to define a parsing schema at design time.</span></span> <span data-ttu-id="ad027-105">Par conséquent, si vous envisagez de recevoir différents documents de fichier plat dans un même emplacement de réception, incluez plusieurs désassembleurs de fichier plat dans le pipeline de réception, un pour chaque schéma.</span><span class="sxs-lookup"><span data-stu-id="ad027-105">So if you expect to receive different flat file documents on the same receive location, you typically include several flat file disassemblers in the receive pipeline, one for each schema.</span></span> <span data-ttu-id="ad027-106">Au moment de l'exécution, le composant Désassembleur approprié est sélectionné à l'aide d'un mécanisme de sonde de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-106">At run time, the correct disassembler component is selected using a pipeline probing mechanism.</span></span> <span data-ttu-id="ad027-107">Il s'agit toutefois d'une approche coûteuse si vous disposez de nombreux schémas de fichier plat car le sondage de chaque composant Désassembleur correspondant dégrade les performances du pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-107">However, this approach is expensive if you have many flat file schemas because probing for every corresponding disassembler component degrades pipeline performance.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ad027-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ad027-108">What This Sample Does</span></span>  
 <span data-ttu-id="ad027-109">Le composant Schema Resolver présente une autre méthode de sélection de schéma pour un Désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="ad027-109">The Schema Resolver component demonstrates an alternative method of selecting the schema for a flat file disassembler.</span></span> <span data-ttu-id="ad027-110">Dans cet exemple, quatre schémas sont définis et les deux premiers caractères d'un message pour chaque schéma sont uniques.</span><span class="sxs-lookup"><span data-stu-id="ad027-110">In this sample, four schemas are defined and the first two characters of a message for each schema are unique.</span></span> <span data-ttu-id="ad027-111">Un mappage est défini entre les deux premiers caractères uniques et le schéma correspondant.</span><span class="sxs-lookup"><span data-stu-id="ad027-111">A mapping is defined between the unique first two characters and the corresponding schema.</span></span> <span data-ttu-id="ad027-112">Lorsque le message d'entrée est transmis au composant Schema Resolver, il lit les deux premiers caractères, détermine le schéma à pour le document correspondant, enregistre les informations de schéma dans le contexte de message, puis appelle le composant Désassembleur de fichier plat standard.</span><span class="sxs-lookup"><span data-stu-id="ad027-112">When the input message is given to the Schema Resolver component, it reads the first two characters, determines which schema to use for the corresponding document, saves the schema information on the message context, and then calls into the standard flat file disassembler component.</span></span> <span data-ttu-id="ad027-113">Le composant Désassembleur de fichier plat standard lit les informations de schéma à partir du contexte du message et utilise ce schéma pour analyser le document.</span><span class="sxs-lookup"><span data-stu-id="ad027-113">The standard flat file disassembler component reads the schema information from the message context and uses that schema to parse the document.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ad027-114">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ad027-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="ad027-115">*\<Exemples de chemin d’accès\>*\Pipelines\SchemaResolverComponent\\</span><span class="sxs-lookup"><span data-stu-id="ad027-115">*\<Samples Path\>*\Pipelines\SchemaResolverComponent\\</span></span>  
  
 <span data-ttu-id="ad027-116">Le tableau suivant montre les fichiers utilisés dans cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ad027-116">The following table shows the files used in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ad027-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="ad027-117">File(s)</span></span>|<span data-ttu-id="ad027-118"> Description</span><span class="sxs-lookup"><span data-stu-id="ad027-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad027-119">SchemaResolverSample.sln</span><span class="sxs-lookup"><span data-stu-id="ad027-119">SchemaResolverSample.sln</span></span>|<span data-ttu-id="ad027-120">Solution pour le projet BizTalk qui utilise le composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ad027-120">Solution for the BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="ad027-121">SchemaResolverSample.btproj</span><span class="sxs-lookup"><span data-stu-id="ad027-121">SchemaResolverSample.btproj</span></span>|<span data-ttu-id="ad027-122">Projet BizTalk qui utilise le composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ad027-122">BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="ad027-123">SchemaResolverRP.btp</span><span class="sxs-lookup"><span data-stu-id="ad027-123">SchemaResolverRP.btp</span></span>|<span data-ttu-id="ad027-124">Pipeline de réception contenant le composant personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ad027-124">Receive pipeline that contains the custom component.</span></span>|  
|<span data-ttu-id="ad027-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span><span class="sxs-lookup"><span data-stu-id="ad027-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span></span>|<span data-ttu-id="ad027-126">Schémas de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="ad027-126">Flat file schemas.</span></span>|  
|<span data-ttu-id="ad027-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span><span class="sxs-lookup"><span data-stu-id="ad027-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span></span>|<span data-ttu-id="ad027-128">Instances de document de fichier plat correspondantes.</span><span class="sxs-lookup"><span data-stu-id="ad027-128">Corresponding flat file document instances.</span></span>|  
|<span data-ttu-id="ad027-129">SchemaResolverFlatFileDasm.sln</span><span class="sxs-lookup"><span data-stu-id="ad027-129">SchemaResolverFlatFileDasm.sln</span></span>|<span data-ttu-id="ad027-130">Solution pour l'implémentation du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-130">Solution for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="ad027-131">SchemaResolverFlatFileDasm.csproj</span><span class="sxs-lookup"><span data-stu-id="ad027-131">SchemaResolverFlatFileDasm.csproj</span></span>|<span data-ttu-id="ad027-132">Projet C# pour l'implémentation du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-132">C# project for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="ad027-133">SchemaResolverFlatFileDasmComp.cs</span><span class="sxs-lookup"><span data-stu-id="ad027-133">SchemaResolverFlatFileDasmComp.cs</span></span>|<span data-ttu-id="ad027-134">Implémentation du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-134">Implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="ad027-135">SeekableReadOnlyStream.cs</span><span class="sxs-lookup"><span data-stu-id="ad027-135">SeekableReadOnlyStream.cs</span></span>|<span data-ttu-id="ad027-136">Implémentation du flux en lecture seule identifiable utilisé par le composant.</span><span class="sxs-lookup"><span data-stu-id="ad027-136">Implementation of the seekable read-only stream used by component.</span></span>|  
|<span data-ttu-id="ad027-137">VirtualStream.cs</span><span class="sxs-lookup"><span data-stu-id="ad027-137">VirtualStream.cs</span></span>|<span data-ttu-id="ad027-138">Implémentation du flux virtuel utilisé par le composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ad027-138">Implementation of the virtual stream used by pipeline component.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="ad027-139">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ad027-139">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="ad027-140">La procédure suivante permet de créer et d'initialiser l'exemple de composant Schema Resolver.</span><span class="sxs-lookup"><span data-stu-id="ad027-140">Use the following procedure to build and initialize the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="ad027-141">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="ad027-141">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="ad027-142">Dans une fenêtre de commande, accédez au répertoire (cd) suivant :</span><span class="sxs-lookup"><span data-stu-id="ad027-142">In a command window, change directory (cd) to the following folder:</span></span>  
  
     <span data-ttu-id="ad027-143">*\<Exemples de chemin d’accès\>*\Pipelines\SchemaResolverComponent</span><span class="sxs-lookup"><span data-stu-id="ad027-143">*\<Samples Path\>*\Pipelines\SchemaResolverComponent</span></span>  
  
2.  <span data-ttu-id="ad027-144">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad027-144">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="ad027-145">Génère le composant.</span><span class="sxs-lookup"><span data-stu-id="ad027-145">Builds the component.</span></span>  
  
    -   <span data-ttu-id="ad027-146">Copie l'assembly de composant dans le dossier de composants \Pipeline de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad027-146">Copies the component assembly into the BizTalk \Pipeline components folder.</span></span>  
  
    -   <span data-ttu-id="ad027-147">Crée et déploie l'exemple de projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad027-147">Builds and deploys the sample BizTalk project.</span></span>  
  
    -   <span data-ttu-id="ad027-148">Configure et démarre l'emplacement de réception et le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ad027-148">Configures the receive location and send port, and starts them.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad027-149">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="ad027-149">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="ad027-150">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="ad027-150">Running This Sample</span></span>  
 <span data-ttu-id="ad027-151">La procédure suivante permet d'exécuter l'exemple de composant Schema Resolver.</span><span class="sxs-lookup"><span data-stu-id="ad027-151">Use the following procedure to run the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ad027-152">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ad027-152">To run this sample</span></span>  
  
1.  <span data-ttu-id="ad027-153">Déplacer des fichiers fichiers POInstance.txt, PRInstance.txt, SOInstance.txt et SRInstance.txt dans l’emplacement de réception \< *chemin d’Installation*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In</span><span class="sxs-lookup"><span data-stu-id="ad027-153">Drop the POInstance.txt, PRInstance.txt, SOInstance.txt, and SRInstance.txt files into the receive location \<*Installation Path*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In</span></span>  
  
2.  <span data-ttu-id="ad027-154">Observez les quatre fichiers .xml écrits dans le \<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out dossier.</span><span class="sxs-lookup"><span data-stu-id="ad027-154">Observe the four .xml files written to the \<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad027-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad027-155">See Also</span></span>  
 [<span data-ttu-id="ad027-156">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ad027-156">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)
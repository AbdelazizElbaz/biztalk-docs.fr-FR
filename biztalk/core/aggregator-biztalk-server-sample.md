---
title: "Agrégation (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- pipelines, examples
- orchestrations, messages
- examples, pipelines
- messages, correlating to orchestrations
ms.assetid: eb8121df-4f5b-4f36-8228-4b5ad1abfb4e
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f4d28214a815aca88f214e5efb9cd883e7192
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="aggregator-biztalk-server-sample"></a><span data-ttu-id="417a9-102">Agrégation (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="417a9-102">Aggregator (BizTalk Server Sample)</span></span>
<span data-ttu-id="417a9-103">La fonction de cet exemple est de générer une fonctionnalité d'agrégation de messages à l'aide des orchestrations et des pipelines.</span><span class="sxs-lookup"><span data-stu-id="417a9-103">The purpose of this sample is to build a message aggregation functionality using orchestration and pipelines.</span></span> <span data-ttu-id="417a9-104">Plus précisément, l'orchestration que nous allons générer :</span><span class="sxs-lookup"><span data-stu-id="417a9-104">Specifically we will build an orchestration that:</span></span>  
  
1.  <span data-ttu-id="417a9-105">Reçoit un ensemble de messages corrélé.</span><span class="sxs-lookup"><span data-stu-id="417a9-105">Receives a set of correlated messages.</span></span> <span data-ttu-id="417a9-106">Les messages sont corrélés en fonction de l'URI du partenaire de destination qui est extrait du contenu d'un message.</span><span class="sxs-lookup"><span data-stu-id="417a9-106">Messages are correlated based on the destination partner URI information that is extracted from message content.</span></span>  
  
2.  <span data-ttu-id="417a9-107">Regroupe les messages reçus au sein d'un seul lot d'échange via l'exécution d'un pipeline d'envoi XML.</span><span class="sxs-lookup"><span data-stu-id="417a9-107">Aggregates received messages into a single interchange batch by executing an XML send pipeline.</span></span>  
  
3.  <span data-ttu-id="417a9-108">Génère un message d'échange XML toutes les minutes ou dès qu'elle dispose d'un nombre de messages suffisant à agréger.</span><span class="sxs-lookup"><span data-stu-id="417a9-108">Produces an XML interchange message every minute or as soon as it has enough messages to aggregate.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="417a9-109">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="417a9-109">Where to Find This Sample</span></span>  
 <span data-ttu-id="417a9-110">*\<Exemples de chemin d’accès\>*\Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="417a9-110">*\<Samples Path\>*\Pipelines\Aggregator</span></span>  
  
 <span data-ttu-id="417a9-111">Le tableau suivant répertorie les fichiers de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-111">The following table lists the files for this sample.</span></span>  
  
|<span data-ttu-id="417a9-112">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="417a9-112">File(s)</span></span>|<span data-ttu-id="417a9-113"> Description</span><span class="sxs-lookup"><span data-stu-id="417a9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="417a9-114">Aggregator.sln</span><span class="sxs-lookup"><span data-stu-id="417a9-114">Aggregator.sln</span></span>|<span data-ttu-id="417a9-115">Fichier de solution Visual Studio pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-115">Visual Studio solution file for the sample.</span></span>|  
|<span data-ttu-id="417a9-116">AggretatorBinding.xml</span><span class="sxs-lookup"><span data-stu-id="417a9-116">AggretatorBinding.xml</span></span>|<span data-ttu-id="417a9-117">Fichier de liaison pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-117">Binding file for the sample.</span></span>|  
|<span data-ttu-id="417a9-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="417a9-118">Cleanup.bat</span></span>|<span data-ttu-id="417a9-119">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="417a9-119">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="417a9-120">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="417a9-120">Removes send and receive ports.</span></span> <span data-ttu-id="417a9-121">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="417a9-121">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="417a9-122">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="417a9-122">Setup.bat</span></span>|<span data-ttu-id="417a9-123">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-123">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="417a9-124">Dans le dossier Aggregate :</span><span class="sxs-lookup"><span data-stu-id="417a9-124">In Aggregate folder:</span></span><br /><br /> <span data-ttu-id="417a9-125">Aggregate.btproj</span><span class="sxs-lookup"><span data-stu-id="417a9-125">Aggregate.btproj</span></span>|<span data-ttu-id="417a9-126">Projet BizTalk pour l'agrégation d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="417a9-126">BizTalk project for aggregating orchestration.</span></span>|  
|<span data-ttu-id="417a9-127">Dans le dossier Aggregator :</span><span class="sxs-lookup"><span data-stu-id="417a9-127">In Aggregator folder:</span></span><br /><br /> <span data-ttu-id="417a9-128">Aggregate.odx</span><span class="sxs-lookup"><span data-stu-id="417a9-128">Aggregate.odx</span></span>|<span data-ttu-id="417a9-129">Orchestration qui collecte et regroupe les messages corrélés, puis qui exécute le pipeline d'envoi afin de les assembler en un seul échange.</span><span class="sxs-lookup"><span data-stu-id="417a9-129">Orchestration that collects correlated messages together and then executes send pipeline to assemble them into a single interchange.</span></span>|  
|<span data-ttu-id="417a9-130">Dans le dossier Aggregate :</span><span class="sxs-lookup"><span data-stu-id="417a9-130">In Aggregate folder:</span></span><br /><br /> <span data-ttu-id="417a9-131">SuspendMessage.odx</span><span class="sxs-lookup"><span data-stu-id="417a9-131">SuspendMessage.odx</span></span>|<span data-ttu-id="417a9-132">Orchestration permettant d'interrompre les messages qui ne peuvent pas être traités au sein de l'agrégation d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="417a9-132">Orchestration used for suspending messages that cannot be processed within aggregating orchestration.</span></span>|  
|<span data-ttu-id="417a9-133">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-133">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-134">FFReceivePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="417a9-134">FFReceivePipeline.btp</span></span>|<span data-ttu-id="417a9-135">Pipeline de réception avec Désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="417a9-135">Receive pipeline with flat file disassembler.</span></span>|  
|<span data-ttu-id="417a9-136">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-136">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-137">Instance1.txt, Instance2.txt, Instance3.txt, Instance4.txt</span><span class="sxs-lookup"><span data-stu-id="417a9-137">Instance1.txt, Instance2.txt, Instance3.txt, Instance4.txt</span></span>|<span data-ttu-id="417a9-138">Instances de document pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-138">Document instances for the sample.</span></span> <span data-ttu-id="417a9-139">Instance1.txt et Instance2.txt, doivent être ajoutés à un échange partenaire de destination [http://www.contoso.com](http://www.contoso.com/) tandis que Instance3.txt et Instance4.txt doivent être ajoutés à un échange partenaire de destination [ http://www.Northwind.com](http://www.northwind.com/).</span><span class="sxs-lookup"><span data-stu-id="417a9-139">Instance1.txt and Instance2.txt should be added to an interchange for destination partner [http://www.contoso.com](http://www.contoso.com/) while Instance3.txt and Instance4.txt should be added to an interchange for destination partner [http://www.northwind.com](http://www.northwind.com/).</span></span>|  
|<span data-ttu-id="417a9-140">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-140">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-141">Invoice.xsd, InvoiceEnvelope.xsd</span><span class="sxs-lookup"><span data-stu-id="417a9-141">Invoice.xsd, InvoiceEnvelope.xsd</span></span>|<span data-ttu-id="417a9-142">Schémas du document et de l'enveloppe pour l'échange de sortie.</span><span class="sxs-lookup"><span data-stu-id="417a9-142">Document schema and envelope schema for output interchange.</span></span>|  
|<span data-ttu-id="417a9-143">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-143">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-144">PipelinesAndSchemas.btproj</span><span class="sxs-lookup"><span data-stu-id="417a9-144">PipelinesAndSchemas.btproj</span></span>|<span data-ttu-id="417a9-145">Projet BizTalk pour les schémas et les pipelines.</span><span class="sxs-lookup"><span data-stu-id="417a9-145">BizTalk project for the schemas and pipelines.</span></span>|  
|<span data-ttu-id="417a9-146">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-146">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-147">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="417a9-147">PropertySchema.xsd</span></span>|<span data-ttu-id="417a9-148">Schéma de propriété pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-148">Property schema for the sample.</span></span>|  
|<span data-ttu-id="417a9-149">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="417a9-149">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="417a9-150">XMLAggregatingPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="417a9-150">XMLAggregatingPipeline.btp</span></span>|<span data-ttu-id="417a9-151">Pipeline d'envoi exécuté à partir de l'orchestration afin d'assembler les messages collectés en un échange XML.</span><span class="sxs-lookup"><span data-stu-id="417a9-151">Send pipeline that is executed from orchestration to assemble collected messages into an XML interchange.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="417a9-152">Création et initialisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="417a9-152">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="417a9-153">La procédure suivante permet de créer et d'initialiser l'exemple Aggregator.</span><span class="sxs-lookup"><span data-stu-id="417a9-153">Use the following procedure to build and initialize the Aggregator sample.</span></span>  
  
#### <a name="to-build-and-initialize-the-aggregator-sample"></a><span data-ttu-id="417a9-154">Pour créer et initialiser l'exemple Aggregator</span><span class="sxs-lookup"><span data-stu-id="417a9-154">To build and initialize the Aggregator sample</span></span>  
  
1.  <span data-ttu-id="417a9-155">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="417a9-155">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="417a9-156">\<Exemples de chemin d’accès\>\Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="417a9-156">\<Samples Path\>\Pipelines\Aggregator</span></span>  
  
2.  <span data-ttu-id="417a9-157">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="417a9-157">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="417a9-158">Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier :</span><span class="sxs-lookup"><span data-stu-id="417a9-158">Creates the input (In) and output (Out) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="417a9-159">\<Exemples de chemin d’accès\>\Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="417a9-159">\<Samples Path\>\Pipelines\Aggregator</span></span>  
  
    -   <span data-ttu-id="417a9-160">Compilation des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="417a9-160">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    -   <span data-ttu-id="417a9-161">Création d'une application appelée « Aggregator Sample » et déploiement des assemblys de l'exemple au sein de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="417a9-161">Creates a new application called "Aggregator Sample" and deploys the sample assemblies into it.</span></span>  
  
    -   <span data-ttu-id="417a9-162">crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :</span><span class="sxs-lookup"><span data-stu-id="417a9-162">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="417a9-163">Inscription et démarrage de l'orchestration, activation de l'emplacement de réception et démarrage du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="417a9-163">Enlists and starts orchestration, enables the receive location, and starts the send port.</span></span>  
  
         <span data-ttu-id="417a9-164">Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="417a9-164">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="417a9-165">Utilisez cette paire de clés pour signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="417a9-165">Use this key pair is used to sign the resulting assemblies.</span></span>  
  
3.  <span data-ttu-id="417a9-166">Avant de tenter d'exécuter cet exemple, vous devez vérifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="417a9-166">Before attempting to run this sample, confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process.</span></span>  
  
     <span data-ttu-id="417a9-167">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="417a9-167">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="417a9-168">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="417a9-168">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="417a9-169">Exécution de l’exemple</span><span class="sxs-lookup"><span data-stu-id="417a9-169">Running the Sample</span></span>  
 <span data-ttu-id="417a9-170">La procédure suivante permet d'exécuter l'exemple Aggregator.</span><span class="sxs-lookup"><span data-stu-id="417a9-170">Use the following procedure to run the Aggregator sample.</span></span>  
  
#### <a name="to-run-the-aggregator-sample"></a><span data-ttu-id="417a9-171">Pour exécuter l'exemple Aggregator</span><span class="sxs-lookup"><span data-stu-id="417a9-171">To run the Aggregator sample</span></span>  
  
1.  <span data-ttu-id="417a9-172">Ouvrez les fichiers Instance1.txt et Instance2.txt, situés dans le dossier PipelinesAndSchemas, afin d'examiner leur contenu.</span><span class="sxs-lookup"><span data-stu-id="417a9-172">Open Instance1.txt and Instance2.txt files located in PipelinesAndSchemas folder to inspect their content.</span></span>  
  
     <span data-ttu-id="417a9-173">Notez que dans les deux fichiers de l’élément DestinationPartnerURI contient la valeur http://www.contoso.com. Cette valeur permet de corréler les deux messages entre eux afin qu’ils peuvent être ajoutés à un échange.</span><span class="sxs-lookup"><span data-stu-id="417a9-173">Notice that in both files the DestinationPartnerURI element contains the value http://www.contoso.com. This value will be used to correlate these two messages together so that they can be added to one interchange.</span></span>  
  
     <span data-ttu-id="417a9-174">De même, l'élément DestinationPatnerURI est défini sur http://www.northwind.com dans les fichiers Instance3.txt et Instance4.txt.</span><span class="sxs-lookup"><span data-stu-id="417a9-174">Similarly Instance3.txt and Instance4.txt files have DestinationPatnerURI element set to http://www.northwind.com.</span></span>  
  
     <span data-ttu-id="417a9-175">Ces deux messages seront ajoutés ensemble dans un autre échange.</span><span class="sxs-lookup"><span data-stu-id="417a9-175">These two messages together will be added to a different interchange.</span></span>  
  
2.  <span data-ttu-id="417a9-176">Collez des copies des fichiers texte Instance1.txt, Instance2.txt, Instance3.txt et Instance4.txt dans le dossier In.</span><span class="sxs-lookup"><span data-stu-id="417a9-176">Paste copies of the text files Instance1.txt, Instance2.txt, Instance3.txt, and Instance4.txt into the folder In.</span></span>  
  
3.  <span data-ttu-id="417a9-177">L'agrégation d'orchestrations génère des échanges de sortie après avoir collecté 10 messages ou après un délai d'expiration d'1 minute.</span><span class="sxs-lookup"><span data-stu-id="417a9-177">Aggregating orchestrations produce output interchanges as soon as they collect 10 messages or after timeout of 1 minute.</span></span> <span data-ttu-id="417a9-178">Les fichiers risquent donc d'apparaître dans le dossier Out après un certain délai.</span><span class="sxs-lookup"><span data-stu-id="417a9-178">Because of that, the files in the Out folder may appear with delay.</span></span>  
  
     <span data-ttu-id="417a9-179">Pour éviter ce délai, vous pouvez coller les quatre fichiers d'entrée quatre fois supplémentaires, ce qui aura pour effet de déclencher la génération des échanges par les orchestrations d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="417a9-179">To avoid the timeout, you can paste the four input files four more times, which would trigger the aggregating orchestrations to produce the interchanges.</span></span>  
  
4.  <span data-ttu-id="417a9-180">Observez les fichiers XML créés dans le dossier Out. Il doit y avoir deux fichiers (un pour chaque URI du partenaire de destination).</span><span class="sxs-lookup"><span data-stu-id="417a9-180">Observe the XML files created in the folder Out. There should be two files – one per each destination partner URI.</span></span>  
  
     <span data-ttu-id="417a9-181">Ouvrez l'un des fichiers et examinez son contenu.</span><span class="sxs-lookup"><span data-stu-id="417a9-181">Open one of the file to inspect its content.</span></span> <span data-ttu-id="417a9-182">Le fichier doit contenir un échange XML comportant une enveloppe et deux documents XML.</span><span class="sxs-lookup"><span data-stu-id="417a9-182">The file should contain an XML interchange that consists of an envelope and two XML documents within it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="417a9-183">Dans un scénario de convoi, l'implémentation de l'exemple risque de générer des messages « Envoyé, non utilisé » ou « Terminé avec des messages non utilisés » en cas de charge élevée.</span><span class="sxs-lookup"><span data-stu-id="417a9-183">The sample implementation may cause "Delivered, not consumed messages" or "Completed with discarded messages" under high load in a convoy scenario.</span></span> <span data-ttu-id="417a9-184">Cela risque de se produire chaque fois qu'un message est acheminé vers un processus d'entreprise en phase finale ou que des messages inattendus arrivent dans un processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="417a9-184">This occurs any time a message routes to a business process that is in the process of ending, or any time unexpected messages arrive into a business process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417a9-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="417a9-185">See Also</span></span>  
 [<span data-ttu-id="417a9-186">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="417a9-186">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)
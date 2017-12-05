---
title: Outils de pipeline | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline tools, XMLAsm.exe
- pipeline tools, FFDasm.exe
- Pipeline.exe
- FFDasm.exe
- pipeline tools, XMLDasm.exe
- pipeline tools
- XMLAsm.exe
- pipeline tools, DSDump.exe
- FFAsm.exe
- pipeline tools, FFAsm.exe
- pipeline tools, how to
- pipeline tools, about pipeline tools
- pipeline tools, Pipeline.exe
- utilities, pipeline tools
- XMLDasm.exe
ms.assetid: ca4d053a-1473-4d40-8cd0-1ed3a3af988a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c567ea50f151f0ee36505bd6d8a71af059eb67d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="pipeline-tools"></a><span data-ttu-id="a1706-102">Outils de pipeline</span><span class="sxs-lookup"><span data-stu-id="a1706-102">Pipeline Tools</span></span>
<span data-ttu-id="a1706-103">Les outils de pipeline fournis avec le Kit de développement logiciel (SDK) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permettent de vérifier qu'un pipeline fonctionne correctement sans avoir à configurer l'environnement BizTalk Server et notamment des ports d'envoi/réception.</span><span class="sxs-lookup"><span data-stu-id="a1706-103">The pipeline tools supplied with the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Software Development Kit (SDK) enable you to verify that a pipeline is functioning correctly without having to configure the BizTalk Server environment, such as send/receive ports.</span></span> <span data-ttu-id="a1706-104">Vous pouvez aussi utiliser les outils de pipeline pour :</span><span class="sxs-lookup"><span data-stu-id="a1706-104">You can also use the pipeline tools to:</span></span>  
  
-   <span data-ttu-id="a1706-105">déboguer des composants de pipeline tiers hors de l'environnement serveur ;</span><span class="sxs-lookup"><span data-stu-id="a1706-105">Debug third-party pipeline components outside of the server environment.</span></span>  
  
-   <span data-ttu-id="a1706-106">diagnostiquer les messages d'erreur du moteur d'analyse ;</span><span class="sxs-lookup"><span data-stu-id="a1706-106">Diagnose parsing engine error messages.</span></span>  
  
-   <span data-ttu-id="a1706-107">essayer différents schémas sans avoir à compiler, déployer, annuler le déploiement et recompiler ;</span><span class="sxs-lookup"><span data-stu-id="a1706-107">Experiment with different schemas without the burden of compiling, deploying, undeploying, and recompiling.</span></span>  
  
-   <span data-ttu-id="a1706-108">explorer le comportement de l'assembleur/désassembleur de fichier plat et XML ;</span><span class="sxs-lookup"><span data-stu-id="a1706-108">Explore flat file and XML assembler/disassembler behavior.</span></span>  
  
-   <span data-ttu-id="a1706-109">visualiser les résultats du désassembleur et découvrir quelles propriétés de contexte de message sont promues et leurs valeurs ;</span><span class="sxs-lookup"><span data-stu-id="a1706-109">View disassembler output and discover which message context properties are promoted and their values.</span></span>  
  
-   <span data-ttu-id="a1706-110">exécuter des pipelines d'envoi/réception sans composants de désassembleur ou d'assembleur (vous pouvez par exemple visualiser les résultats du décodeur S/MIME) ;</span><span class="sxs-lookup"><span data-stu-id="a1706-110">Run send/receive pipelines without disassembler and assembler components (for example, you can view the output of the S/MIME decoder).</span></span>  
  
-   <span data-ttu-id="a1706-111">effectuer des mesures précises des performances du pipeline seul (plutôt que de l'ensemble du sous-système de messagerie).</span><span class="sxs-lookup"><span data-stu-id="a1706-111">Make fine-grained performance measurements of the pipeline alone (rather than the entire messaging subsystem).</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="a1706-112">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="a1706-112">Location in SDK</span></span>  
 <span data-ttu-id="a1706-113">\<*Chemin d’installation*\>\SDK\Utilities\PipelineTools</span><span class="sxs-lookup"><span data-stu-id="a1706-113">\<*Installation Path*\>\SDK\Utilities\PipelineTools</span></span>  
  
 <span data-ttu-id="a1706-114">Utilisez les outils de pipeline pour exécuter, déboguer et profiler les pipelines et les composants de pipeline (c'est-à-dire les composants de l'assembleur/désassembleur de fichier plat et XML).</span><span class="sxs-lookup"><span data-stu-id="a1706-114">You use pipeline tools for executing, debugging, and profiling pipelines, and pipeline components (that is, flat file and XML assembler/disassembler components).</span></span>  
  
## <a name="file-inventory"></a><span data-ttu-id="a1706-115">Inventaire des fichiers</span><span class="sxs-lookup"><span data-stu-id="a1706-115">File Inventory</span></span>  
 <span data-ttu-id="a1706-116">Le tableau suivant répertorie les fichiers des outils de pipeline et décrit leur finalité.</span><span class="sxs-lookup"><span data-stu-id="a1706-116">The following table lists the pipeline tools files and describes their purpose.</span></span>  
  
|<span data-ttu-id="a1706-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="a1706-117">File(s)</span></span>|<span data-ttu-id="a1706-118"> Description</span><span class="sxs-lookup"><span data-stu-id="a1706-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1706-119">DSDump.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-119">DSDump.exe</span></span>|<span data-ttu-id="a1706-120">Vous permet de vider la structure des schémas de document (représentation simplifiée en mémoire du ou des schémas XSD) avec ou sans annotations de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="a1706-120">Enables you to dump the document schema structure, which is an in-memory lightweight representation of the one or more XSD schemas, with or without flat file annotations.</span></span> <span data-ttu-id="a1706-121">Cet outil pourra vous être utile si le moteur d'analyse vous envoie des erreurs comme $Root$0$3$2 et que vous devez les décoder.</span><span class="sxs-lookup"><span data-stu-id="a1706-121">This tool can be helpful when you get parsing engine errors such as $Root$0$3$2 and you need to decode them.</span></span> <span data-ttu-id="a1706-122">Les chiffres suivants $ représentent les index ou les enregistrements de base 0 tels qu'ils apparaissent dans le schéma de document.</span><span class="sxs-lookup"><span data-stu-id="a1706-122">Numbers after $ mean 0-based index or records as they appear in the document schema.</span></span>|  
|<span data-ttu-id="a1706-123">FFAsm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-123">FFAsm.exe</span></span>|<span data-ttu-id="a1706-124">Exécute le composant Assembleur de fichier plat, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise ou assemble le ou les documents XML d'un utilisateur en un document de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="a1706-124">Runs the flat file assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes or assembles a user's XML document(s) into a flat file document.</span></span>|  
|<span data-ttu-id="a1706-125">FFDasm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-125">FFDasm.exe</span></span>|<span data-ttu-id="a1706-126">Exécute le composant Désassembleur de fichier plat, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse ou désassemble le document de fichier plat d'un utilisateur en un ou plusieurs documents XML.</span><span class="sxs-lookup"><span data-stu-id="a1706-126">Runs the flat file disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses or disassembles a user's flat file document into one or more XML documents.</span></span>|  
|<span data-ttu-id="a1706-127">Pipeline.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-127">Pipeline.exe</span></span>|<span data-ttu-id="a1706-128">Exécute un pipeline d'envoi ou de réception, accepte un ou plusieurs documents d'entrée ainsi que leurs parties, leurs schémas XSD et les informations connexes, et produit un document de sortie une fois le pipeline exécuté.</span><span class="sxs-lookup"><span data-stu-id="a1706-128">Runs a send or receive pipeline; accepts one or more input documents and their parts, XSD schemas and related information; and produces an output document after the pipeline runs.</span></span> <span data-ttu-id="a1706-129">Pipeline.exe n'ayant pas accès aux bases de données BizTalk Server, les pipelines contenant les composants d'assembleur et de désassembleur BizTalk Framework qui accèdent aux bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] durant l'exécution sont susceptibles de ne pas être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a1706-129">Pipeline.exe does not access BizTalk Server databases, so pipelines containing BizTalk Framework assembler and disassembler components that access [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases during execution may not be supported.</span></span>|  
|<span data-ttu-id="a1706-130">XMLAsm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-130">XMLAsm.exe</span></span>|<span data-ttu-id="a1706-131">Exécute le composant Assembleur XML, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise, assemble ou enveloppe le ou les documents XML d'un utilisateur en un document XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1706-131">Runs the XML assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes, assembles, or envelopes a user's XML document(s) into an output XML document.</span></span>|  
|<span data-ttu-id="a1706-132">XMLDasm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-132">XMLDasm.exe</span></span>|<span data-ttu-id="a1706-133">Exécute le composant Désassembleur XML, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse, désassemble ou désenveloppe le document XML d'un utilisateur en un ou plusieurs documents XML.</span><span class="sxs-lookup"><span data-stu-id="a1706-133">Runs the XML disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses, disassembles, or un-envelopes a user's XML document into one or more XML documents.</span></span>|  
  
## <a name="usage"></a><span data-ttu-id="a1706-134">Utilisation</span><span class="sxs-lookup"><span data-stu-id="a1706-134">Usage</span></span>  
 <span data-ttu-id="a1706-135">Une description plus détaillée de chaque fichier est fournie dans les sections qui suivent.</span><span class="sxs-lookup"><span data-stu-id="a1706-135">A more detailed description of each file is provided in the sections that follow.</span></span>  
  
### <a name="dsdumpexe"></a><span data-ttu-id="a1706-136">DSDump.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-136">DSDump.exe</span></span>  
 <span data-ttu-id="a1706-137">DSDump.exe vous permet de vider la structure des schémas de document (représentation simplifiée en mémoire d'un ou de plusieurs schémas XSD) avec ou sans annotations de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="a1706-137">DSDump.exe enables you to dump the document schema structure, which is an in-memory lightweight representation of one or more XSD schemas, with or without flat file annotations.</span></span>  
  
 <span data-ttu-id="a1706-138">DSDump.exe (outil de vidage de schémas de documents) prend en charge le paramètre de ligne de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="a1706-138">DSDump.exe (document schema dump tool) supports the following command-line parameter:</span></span>  
  
```  
DSDump.exe schemaFileName  
```  
  
 <span data-ttu-id="a1706-139">En cas de réussite, DSDump imprime le schéma de document sur la console.</span><span class="sxs-lookup"><span data-stu-id="a1706-139">In case of success, DSDump prints the document schema to the console.</span></span>  
  
### <a name="ffasmexe"></a><span data-ttu-id="a1706-140">FFAsm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-140">FFAsm.exe</span></span>  
 <span data-ttu-id="a1706-141">FFAsm.exe (assembleur de fichier plat) prend en charge les paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="a1706-141">FFAsm.exe (flat file assembler) supports the following command-line parameters:</span></span>  
  
```  
usage: ffasm document... [-dm documentMask...]-bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -c ] [ -d ] [ -sb ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -c                 Display assembled FF message on the console  
  -d                 Demote properties  
  -sb                Set body schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Output message encoding name (e.g. windows-1252) or   
                         code page (e.g. 936)  
  -v                 Verbose mode  
  
file name macros:  
  %MessageID%        FF message identifier (Guid)  
  %MessagePartID%    FF message part identifier (Guid)  
  
```  
  
 <span data-ttu-id="a1706-142">Par exemple, si vous souhaitez assembler trois documents XML d'entrée en un seul document de fichier plat avec une rétrogradation d'en-têtes et de propriétés, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a1706-142">For example, if you want to assemble three input XML documents into a single flat file document with a header and property demotion, use the following command:</span></span>  
  
```  
FFAsm.exe file_in1.xml file_in2.xml file_in3.xml –hs myHeaderSchema.xsd –bs myBodySchema.xsd -d  
```  
  
### <a name="ffdasmexe"></a><span data-ttu-id="a1706-143">FFDasm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-143">FFDasm.exe</span></span>  
 <span data-ttu-id="a1706-144">FFDasm.exe (désassembleur de fichier plat) prend en charge les paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="a1706-144">FFDasm.exe (flat file disassembler) supports the following command-line parameters:</span></span>  
  
```  
usage: ffdasm document -bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -s ] [ -c ] [ -p ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           Flat File document  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  encoding           Input message body part encoding name (e.g. windows-1252) or code page (e.g., 396)  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 <span data-ttu-id="a1706-145">Par exemple, si vous souhaitez désassembler un document de fichier plat comportant un en-tête, un corps et un code de fin, et afficher les résultats dans la console, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a1706-145">For example, if you want to disassemble a flat file document that has a header, body, and trailer, and display the results to the console, use the following command:</span></span>  
  
```  
FFDasm.exe file_in.txt –hs myHeaderSchema.xsd –bs myBodySchema.xsd –ts myTrailerSchema.xsd –c  
```  
  
### <a name="pipelineexe"></a><span data-ttu-id="a1706-146">Pipeline.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-146">Pipeline.exe</span></span>  
 <span data-ttu-id="a1706-147">Pipeline.exe (l'outil de pipeline) prend en charge les paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="a1706-147">Pipeline.exe (the Pipeline tool) supports the following command-line parameters:</span></span>  
  
```  
usage: pipeline ( pipeline[.btp] | -pt pipelineTypeName [ -an assemblyName ] ) -d document... [ -part part... ] [ -s schema[.xsd][:namespace.type]... ] [ -proj project[.btproj] ] [ -p ] [ -c ] [ -t ] [ -m filenamemask ] [ -pm partfilenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  pipeline                Pipeline file name  
  pipelineTypeName     Compiled pipeline assembly qualified type name (e.g.   
"MyPipelines.ReceivePipeline, MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66" or full name (e.g.   
"MyPipelines.ReceivePipeline") if assembly name is   
specified  
  assemblyName         Compiled pipeline assembly file name (e.g.   
MyPipelines.dll) or name (e.g. "MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66")  
  document             Input document(s)  
  part                 Input document's part  
  schema               Schema file name  
  namespace            Schema namespace (as in BizTalk project system)  
  type                 Schema type (as in BizTalk project system)  
  project              BizTalk project file  
  -p                   Display promoted context properties for receive and   
send pipelines, and promote context properties for   
send pipelines  
  -c                      Display output document on the console  
  -t                      Display elapsed time of components execution  
  filenamemask         Output message file name mask (default is   
Message_%MessageID%.out)  
  partfilenamemask     Output part file name mask (default is   
Part_%MessagePartID%.out)  
  encoding             Output message encoding name (e.g. windows-1252)   
or code page (e.g. 936)  
  -v                   Verbous mode  
  
note:  
You can specify namespace and type for schemas either using namespace.type notation in schema file reference or by using BizTalk project file.  
  
file name macros:  
  %MessageID%           Message identifier (Guid)  
  %MessagePartID%       Message part identifier (Guid)  
  %MessageNumber%       Message number  
  
```  
  
 <span data-ttu-id="a1706-148">Si vous souhaitez par exemple exécuter un pipeline de réception à partir du fichier ReceivePipeline.btp (qui comporte des composants Désassembleur XML et Valideur XML) à l'aide de mySchema.xsd et afficher les résultats dans la console, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a1706-148">For example, if you want to run a receive pipeline from the file ReceivePipeline.btp (which has XML disassembler and XML validator components) using mySchema.xsd and display the results to the console, use the following command:</span></span>  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd:MyProject.MySchema -c  
  
```  
  
 <span data-ttu-id="a1706-149">\- Ou -</span><span class="sxs-lookup"><span data-stu-id="a1706-149">\- Or -</span></span>  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd –proj MyProject.btproj -c  
  
```  
  
 <span data-ttu-id="a1706-150">Dans le premier exemple, un nom qualifié (**MyProject.MySchema**) pour le schéma est inclus comme un argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a1706-150">In the first example, a qualified type name (**MyProject.MySchema**) for the schema is included as a command-line argument.</span></span> <span data-ttu-id="a1706-151">Dans le deuxième exemple, le schéma est obtenu à partir du fichier de projet BizTalk spécifié.</span><span class="sxs-lookup"><span data-stu-id="a1706-151">In the second example, the schema is obtained from the specified BizTalk project file.</span></span>  
  
 <span data-ttu-id="a1706-152">Vous pouvez aussi exécuter des pipelines à partir des fichiers de projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compilés, comme le montre l'exemple ci-dessous (le pipeline est référencé par son nom de type qualifié d'assembly) :</span><span class="sxs-lookup"><span data-stu-id="a1706-152">You can also run pipelines from the compiled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project files, as in the following example (the pipeline is referenced by its assembly-qualified type name):</span></span>  
  
```  
Pipeline.exe -pt "TestBtsProject.ReceivePipeline, TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 <span data-ttu-id="a1706-153">Dans l'exemple suivant, un pipeline est référencé séparément par son nom de type et son nom de fichier d'assembly :</span><span class="sxs-lookup"><span data-stu-id="a1706-153">In the following example, a pipeline is referenced by its type name and assembly file name separately:</span></span>  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an TestBtsProject.dll -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c   
```  
  
 <span data-ttu-id="a1706-154">L'exemple suivant montre un pipeline référencé par son nom d'assemby :</span><span class="sxs-lookup"><span data-stu-id="a1706-154">The following example shows a pipeline referenced by its assembly name:</span></span>  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an "TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 <span data-ttu-id="a1706-155">Pipeline.exe s'exécute avec les informations d'identification (quelles qu'elles soient) que vous avez utilisées pour le lancer.</span><span class="sxs-lookup"><span data-stu-id="a1706-155">Pipeline.exe runs with whatever credentials you have used to launch it.</span></span> <span data-ttu-id="a1706-156">Il n'utilise pas le compte sous lequel les instances d'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] normales sont exécutées. Il est donc possible que vous ne puissiez pas exécuter les pipelines qui contiennent des composants requérant un accès aux bases de données.</span><span class="sxs-lookup"><span data-stu-id="a1706-156">It does not use the account that normal [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instances run under, so you may not be able to run pipelines that contain components that require database access.</span></span> <span data-ttu-id="a1706-157">Veillez à exécuter Pipeline.exe sous un compte disposant de tous les privilèges requis.</span><span class="sxs-lookup"><span data-stu-id="a1706-157">Make sure you run Pipeline.exe under an account that has all the required privileges.</span></span>  
  
 <span data-ttu-id="a1706-158">N'utilisez Pipeline.exe que pour vérifier les pipelines personnalisés sans composants personnalisés tiers.</span><span class="sxs-lookup"><span data-stu-id="a1706-158">You should only use Pipeline.exe to verify custom pipelines without third-party custom components.</span></span> <span data-ttu-id="a1706-159">Si vous vous en servez pour vérifier des pipelines personnalisés comportant des composants personnalisés tiers, il génèrera les résultats souhaités,</span><span class="sxs-lookup"><span data-stu-id="a1706-159">If you use pipeline.exe to verify a custom pipeline with third-party custom components, Pipeline.exe will produce the desired output.</span></span> <span data-ttu-id="a1706-160">mais si vous déployez le même pipeline personnalisé avec des composants personnalisés tiers, utilisez ce pipeline dans un port de réception ou d'envoi, puis employez Pipeline.exe pour lui envoyer un message. Le pipeline échouera et BizTalk Server retournera une erreur.</span><span class="sxs-lookup"><span data-stu-id="a1706-160">However, if you deploy the same custom pipeline with third-party custom components, use the pipeline in a receive or send port, and then use Pipeline.exe to submit a message to the pipeline, the pipeline will fail and BizTalk Server will return an error.</span></span>  
  
### <a name="xmlasmexe"></a><span data-ttu-id="a1706-161">XMLAsm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-161">XMLAsm.exe</span></span>  
 <span data-ttu-id="a1706-162">XMLAsm.exe (l'outil Assembleur XML) prend en charge les paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="a1706-162">XMLAsm.exe  (XML Assembler tool) supports the following command-line parameters:</span></span>  
  
```  
usage: xmlasm document...[-dm documentmask...] -ds documentSchema... [ -es envelopeSchema... ] [ -c ] [ -d ] [ -sd ] [ -m filenamemask ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -c                 Display assembled XML message on the console  
  -d                 Demote properties  
  -sd                Set document schema(s) as design-time property  
  -d                 Demote properties  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 <span data-ttu-id="a1706-163">Par exemple, si vous souhaitez assembler deux documents XML d'entrée en un seul document XML avec une enveloppe, et afficher les résultats dans la console, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a1706-163">For example, if you want to assemble two input XML documents into a single XML document with an envelope and display the results to the console, use the following command:</span></span>  
  
```  
FFAsm.exe file_in1.xml file_in2.xml–es myEnvelopeSchema.xsd –ds myBodySchema.xsd –c  
```  
  
### <a name="xmldasmexe"></a><span data-ttu-id="a1706-164">XMLDasm.exe</span><span class="sxs-lookup"><span data-stu-id="a1706-164">XMLDasm.exe</span></span>  
 <span data-ttu-id="a1706-165">XMLDasm.exe prend en charge les paramètres de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="a1706-165">XMLDasm.exe supports the following command-line parameters:</span></span>  
  
```  
usage: xmldasm document -ds documentSchema... [ -es envelopeSchema... ] [ -s ] [ -c ] [ -p ] [ -sd ] [ -se ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  -sd                Set document schema(s) as design-time property  
  -se                Set envelope schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Input message body part encoding name (e.g., windows-1252) or code page (e.g., 936)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  %MessageNumber%    XML message number  
  
```  
  
 <span data-ttu-id="a1706-166">Par exemple, si vous souhaitez désassembler un document XML avec deux enveloppes imbriquées et afficher les résultats dans la console, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a1706-166">For example, if you want to disassemble an XML document with two nested envelopes and display the results to the console, use the following command:</span></span>  
  
```  
XmlDasm.exe file_in.txt –ds myDocumentSchema.xsd –es myEnvelopeSchema1.xsd –es myEnvelopeSchema2.xsd –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1706-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1706-167">See Also</span></span>  
 [<span data-ttu-id="a1706-168">Utilitaires du SDK</span><span class="sxs-lookup"><span data-stu-id="a1706-168">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)
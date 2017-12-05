---
title: MIME (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, MIME/SMIME Encoder [pipeline component]
- examples, send pipelines
- MIME/SMIME Encoder [pipeline component], send pipelines
- MIME/SMIME Encoder [pipeline component], examples
- examples, MIME/SMIME Encoder [pipeline component]
ms.assetid: f76c720d-3798-4f15-a5f9-885ddf421d57
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec6e6e290761ba6d1be2ed08c8519e96c2846fa7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mime-biztalk-server-sample"></a><span data-ttu-id="b67dd-102">MIME (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="b67dd-102">MIME (BizTalk Server Sample)</span></span>
<span data-ttu-id="b67dd-103">L'exemple MIME illustre l'exécution du codage MIME dans un pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b67dd-103">The MIME sample demonstrates how to perform MIME encoding within a send pipeline.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="b67dd-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="b67dd-104">What This Sample Does</span></span>  
 <span data-ttu-id="b67dd-105">Cet exemple permet de configurer le dossier MIMEIn en tant qu'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b67dd-105">This sample configures the folder MIMEIn as a receive location.</span></span> <span data-ttu-id="b67dd-106">Lorsque vous placez un fichier tel que le fichier d'exemple ImageInput.gif dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message contenu dans ce fichier comme suit :</span><span class="sxs-lookup"><span data-stu-id="b67dd-106">When you place a file, such as the sample file ImageInput.gif, in this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following steps:</span></span>  
  
1.  <span data-ttu-id="b67dd-107">Il récupère le fichier de message du dossier MIMEIn de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b67dd-107">Retrieve the message file from the receive location folder MIMEIn.</span></span>  
  
2.  <span data-ttu-id="b67dd-108">Dans le pipeline de réception, il transmet le message sans modification.</span><span class="sxs-lookup"><span data-stu-id="b67dd-108">In the receive pipeline, pass the message through unchanged.</span></span>  
  
3.  <span data-ttu-id="b67dd-109">Dans la base de données MessageBox, il achemine le message au pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="b67dd-109">In the MessageBox database, route the message to the send pipeline.</span></span>  
  
4.  <span data-ttu-id="b67dd-110">Dans le pipeline d'envoi, il exécute le codage MIME et place le fichier dans le dossier MIMEOut de l'adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b67dd-110">In the send pipeline, perform MIME encoding and place the file into the send adapter folder MIMEOut.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="b67dd-111">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="b67dd-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="b67dd-112">\<*Exemples de chemin d’accès*\>\Pipelines\MIME\\</span><span class="sxs-lookup"><span data-stu-id="b67dd-112">\<*Samples Path*\>\Pipelines\MIME\\</span></span>  
  
 <span data-ttu-id="b67dd-113">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="b67dd-113">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="b67dd-114">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="b67dd-114">File(s)</span></span>|<span data-ttu-id="b67dd-115"> Description</span><span class="sxs-lookup"><span data-stu-id="b67dd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b67dd-116">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="b67dd-116">Cleanup.bat</span></span>|<span data-ttu-id="b67dd-117">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="b67dd-117">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="b67dd-118">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="b67dd-118">Removes send and receive ports.</span></span> <span data-ttu-id="b67dd-119">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b67dd-119">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="b67dd-120">ImageInput.GIF</span><span class="sxs-lookup"><span data-stu-id="b67dd-120">ImageInput.GIF</span></span>|<span data-ttu-id="b67dd-121">Exemple de fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="b67dd-121">Sample input file.</span></span>|  
|<span data-ttu-id="b67dd-122">SampleMimeEncoding.btproj</span><span class="sxs-lookup"><span data-stu-id="b67dd-122">SampleMimeEncoding.btproj</span></span><br /><br /> <span data-ttu-id="b67dd-123">SampleMimeEncoding.sln</span><span class="sxs-lookup"><span data-stu-id="b67dd-123">SampleMimeEncoding.sln</span></span>|<span data-ttu-id="b67dd-124">Fichiers projet et solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="b67dd-124">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="b67dd-125">SampleMimeEncodingBinding.xml</span><span class="sxs-lookup"><span data-stu-id="b67dd-125">SampleMimeEncodingBinding.xml</span></span>|<span data-ttu-id="b67dd-126">Utilisé pour l’installation automatique, notamment la liaison de port.</span><span class="sxs-lookup"><span data-stu-id="b67dd-126">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="b67dd-127">SendMimePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="b67dd-127">SendMimePipeline.btp</span></span>|<span data-ttu-id="b67dd-128">Fichier du pipeline d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec le composant Encodeur MIME.</span><span class="sxs-lookup"><span data-stu-id="b67dd-128">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send pipeline file with the MIME Encoder component.</span></span>|  
|<span data-ttu-id="b67dd-129">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="b67dd-129">Setup.bat</span></span>|<span data-ttu-id="b67dd-130">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b67dd-130">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="b67dd-131">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="b67dd-131">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="b67dd-132">La procédure suivante permet de créer et d'initialiser l'exemple MIME.</span><span class="sxs-lookup"><span data-stu-id="b67dd-132">Use the following procedure to build and initialize the MIME sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="b67dd-133">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="b67dd-133">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="b67dd-134">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="b67dd-134">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="b67dd-135">\<*Exemples de chemin d’accès*\>\Pipelines\MIME</span><span class="sxs-lookup"><span data-stu-id="b67dd-135">\<*Samples Path*\>\Pipelines\MIME</span></span>  
  
2.  <span data-ttu-id="b67dd-136">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b67dd-136">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="b67dd-137">création des dossiers d'entrée (MIMEIn) et de sortie (MIMEOut) associés à cet exemple dans le dossier :</span><span class="sxs-lookup"><span data-stu-id="b67dd-137">Creates the input (MIMEIn) and output (MIMEOut) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="b67dd-138">\<*Exemples de chemin d’accès*\>\Pipelines\MIME</span><span class="sxs-lookup"><span data-stu-id="b67dd-138">\<*Samples Path*\>\Pipelines\MIME</span></span>  
  
    -   <span data-ttu-id="b67dd-139">compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="b67dd-139">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="b67dd-140">crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :</span><span class="sxs-lookup"><span data-stu-id="b67dd-140">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b67dd-141">Cet exemple affiche l’avertissement suivant lors de la création et la liaison des ports :</span><span class="sxs-lookup"><span data-stu-id="b67dd-141">This sample displays the following warning when creating and binding the ports:</span></span>  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "MIMEReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  <span data-ttu-id="b67dd-142">Vous pouvez ignorer ces avertissements sans problème.</span><span class="sxs-lookup"><span data-stu-id="b67dd-142">You can safely ignore these warnings.</span></span> <span data-ttu-id="b67dd-143">(Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)</span><span class="sxs-lookup"><span data-stu-id="b67dd-143">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="b67dd-144">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b67dd-144">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b67dd-145">Si vous exécutez cet exemple à partir d’un emplacement autre qu’où il est installé, vous devez d’abord ajouter une référence à la **Microsoft.BizTalk.Pipeline.Components** assembly.</span><span class="sxs-lookup"><span data-stu-id="b67dd-145">If you run this sample from a location other than where it is installed, you must first add a reference to the **Microsoft.BizTalk.Pipeline.Components** assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b67dd-146">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b67dd-146">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b67dd-147">Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de l'utilitaire.NET Framework Strong Name (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="b67dd-147">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="b67dd-148">Utilisez cette paire de clés pour signer l'assembly obtenu.</span><span class="sxs-lookup"><span data-stu-id="b67dd-148">Use this key pair to sign the resulting assembly.</span></span> <span data-ttu-id="b67dd-149">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="b67dd-149">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="b67dd-150">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="b67dd-150">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="b67dd-151">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="b67dd-151">Running This Sample</span></span>  
 <span data-ttu-id="b67dd-152">La procédure suivante permet d'exécuter l'exemple MIME.</span><span class="sxs-lookup"><span data-stu-id="b67dd-152">Use the following procedure to run the MIME sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="b67dd-153">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b67dd-153">To run this sample</span></span>  
  
1.  <span data-ttu-id="b67dd-154">Placez une copie du fichier ImageInput.gif dans le dossier MIMEIn.</span><span class="sxs-lookup"><span data-stu-id="b67dd-154">Put a copy of the file ImageInput.gif into the folder MIMEIn.</span></span>  
  
2.  <span data-ttu-id="b67dd-155">Observez le fichier texte créé dans le dossier MIMEOut.</span><span class="sxs-lookup"><span data-stu-id="b67dd-155">Observe the text file created in the folder MIMEOut.</span></span> <span data-ttu-id="b67dd-156">Le nom du fichier texte a pour base le GUID de l'ID du message.</span><span class="sxs-lookup"><span data-stu-id="b67dd-156">The name of this text file is based on the message ID GUID.</span></span> <span data-ttu-id="b67dd-157">Ce fichier inclut le contenu MIME du fichier d'entrée ImageInput.gif.</span><span class="sxs-lookup"><span data-stu-id="b67dd-157">This file contains MIME-encoded content of the input file ImageInput.gif.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67dd-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b67dd-158">See Also</span></span>  
 [<span data-ttu-id="b67dd-159">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="b67dd-159">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)
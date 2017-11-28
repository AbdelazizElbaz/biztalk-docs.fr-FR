---
title: XSLT transformer le composant (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
- XSLT, examples
- examples, XSLT
ms.assetid: 9152e897-4db9-4924-b37e-fd9e908dbef1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8374e2069660998a46265986125b6b0159ea1961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xslt-transform-component-biztalk-server-sample"></a><span data-ttu-id="86d29-102">Composant Transformation XSLT (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="86d29-102">XSLT Transform Component (BizTalk Server Sample)</span></span>
<span data-ttu-id="86d29-103">L'exemple de composant Transformation XSLT décrit l'écriture d'un composant de pipeline personnalisé permettant de transformer un message XML à l'aide de XSLT.</span><span class="sxs-lookup"><span data-stu-id="86d29-103">The XSLT Transform Component sample demonstrates how to write a custom pipeline component to transform an XML message using XSLT.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="86d29-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="86d29-104">What This Sample Does</span></span>  
 <span data-ttu-id="86d29-105">Cet exemple effectue la transformation selon la procédure suivante :</span><span class="sxs-lookup"><span data-stu-id="86d29-105">The sample accomplishes the transformation with the following steps:</span></span>  
  
1.  <span data-ttu-id="86d29-106">Un document XML est extrait d'un dossier.</span><span class="sxs-lookup"><span data-stu-id="86d29-106">An XML document is retrieved from a folder.</span></span>  
  
2.  <span data-ttu-id="86d29-107">Le pipeline transforme le document XML en un corps de message électronique HTML à l'aide de Transform.xsl.</span><span class="sxs-lookup"><span data-stu-id="86d29-107">The pipeline transforms the XML document into the HTML body of an e-mail message using Transform.xsl.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="86d29-108">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="86d29-108">Where to Find This Sample</span></span>  
 <span data-ttu-id="86d29-109">*\<Exemples de chemin d’accès >*\Pipelines\XslTransformComponent\\</span><span class="sxs-lookup"><span data-stu-id="86d29-109">*\<Samples Path>*\Pipelines\XslTransformComponent\\</span></span>  
  
 <span data-ttu-id="86d29-110">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="86d29-110">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="86d29-111">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="86d29-111">File(s)</span></span>|<span data-ttu-id="86d29-112"> Description</span><span class="sxs-lookup"><span data-stu-id="86d29-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86d29-113">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="86d29-113">AssemblyInfo.cs</span></span>|<span data-ttu-id="86d29-114">Fichier d'assembly C#.</span><span class="sxs-lookup"><span data-stu-id="86d29-114">C# assembly file.</span></span>|  
|<span data-ttu-id="86d29-115">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="86d29-115">Cleanup.bat</span></span>|<span data-ttu-id="86d29-116">Exemple de fichier de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="86d29-116">Sample cleanup file.</span></span>|  
|<span data-ttu-id="86d29-117">Confirmation.xsd</span><span class="sxs-lookup"><span data-stu-id="86d29-117">Confirmation.xsd</span></span>|<span data-ttu-id="86d29-118">Exemple de fichier de schéma.</span><span class="sxs-lookup"><span data-stu-id="86d29-118">Sample schema file.</span></span>|  
|<span data-ttu-id="86d29-119">DocInstance.xml</span><span class="sxs-lookup"><span data-stu-id="86d29-119">DocInstance.xml</span></span>|<span data-ttu-id="86d29-120">Exemple de fichier .xml à transformer.</span><span class="sxs-lookup"><span data-stu-id="86d29-120">Sample .xml file to transform.</span></span>|  
|<span data-ttu-id="86d29-121">SendHtmlMessage.btproj</span><span class="sxs-lookup"><span data-stu-id="86d29-121">SendHtmlMessage.btproj</span></span>|<span data-ttu-id="86d29-122">Projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="86d29-122">BizTalk project.</span></span>|  
|<span data-ttu-id="86d29-123">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="86d29-123">Setup.bat</span></span>|<span data-ttu-id="86d29-124">Fichier de commandes de configuration.</span><span class="sxs-lookup"><span data-stu-id="86d29-124">Configuration batch file.</span></span>|  
|<span data-ttu-id="86d29-125">Xml2HtmlSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="86d29-125">Xml2HtmlSendPipeline.btp</span></span>|<span data-ttu-id="86d29-126">Fichier de pipeline BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="86d29-126">BizTalk Server pipeline file.</span></span>|  
|<span data-ttu-id="86d29-127">XslTransform.csproj</span><span class="sxs-lookup"><span data-stu-id="86d29-127">XslTransform.csproj</span></span>|<span data-ttu-id="86d29-128">Projet C#.</span><span class="sxs-lookup"><span data-stu-id="86d29-128">C# project.</span></span>|  
|<span data-ttu-id="86d29-129">XslTransformComponent.sln</span><span class="sxs-lookup"><span data-stu-id="86d29-129">XslTransformComponent.sln</span></span>|<span data-ttu-id="86d29-130">Exemple de fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="86d29-130">Sample solution file.</span></span>|  
|<span data-ttu-id="86d29-131">XslTransformComponentBinding.XML</span><span class="sxs-lookup"><span data-stu-id="86d29-131">XslTransformComponentBinding.XML</span></span>|<span data-ttu-id="86d29-132">Fichier de liaison XML.</span><span class="sxs-lookup"><span data-stu-id="86d29-132">XML binding file.</span></span>|  
|<span data-ttu-id="86d29-133">XslTransformer.cs</span><span class="sxs-lookup"><span data-stu-id="86d29-133">XslTransformer.cs</span></span>|<span data-ttu-id="86d29-134">Code source C#.</span><span class="sxs-lookup"><span data-stu-id="86d29-134">C# source code.</span></span>|  
|<span data-ttu-id="86d29-135">Transform.xsl</span><span class="sxs-lookup"><span data-stu-id="86d29-135">Transform.xsl</span></span>|<span data-ttu-id="86d29-136">Fichier XSLT permettant de transformer DocInstance.xml.</span><span class="sxs-lookup"><span data-stu-id="86d29-136">XSLT file used to transform DocInstance.xml.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="86d29-137">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="86d29-137">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="86d29-138">La procédure suivante permet de créer et d'initialiser l'exemple de composant Transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="86d29-138">Use the following procedure to build and initialize the XSLT Transform Component sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="86d29-139">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="86d29-139">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="86d29-140">Dans une fenêtre de commande, accédez au répertoire (**cd)** dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="86d29-140">In a command window, change directory (**cd)** to the following folder:</span></span>  
  
     <span data-ttu-id="86d29-141">*\<Exemples de chemin d’accès >*\Pipelines\XslTransformComponent</span><span class="sxs-lookup"><span data-stu-id="86d29-141">*\<Samples Path>*\Pipelines\XslTransformComponent</span></span>  
  
2.  <span data-ttu-id="86d29-142">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="86d29-142">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="86d29-143">Création des dossiers d'entrée (\In) et de sortie (\Out) utilisés dans l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="86d29-143">Creates the input (\In) and output (\Out) folders used in the sample.</span></span>  
  
    -   <span data-ttu-id="86d29-144">Création d'un nouveau fichier clé ;</span><span class="sxs-lookup"><span data-stu-id="86d29-144">Generates a new key file.</span></span>  
  
    -   <span data-ttu-id="86d29-145">Création et déploiement du pipeline de composant Transformation XSLT ;</span><span class="sxs-lookup"><span data-stu-id="86d29-145">Builds and deploys the XSLT Transform Component pipeline.</span></span>  
  
    -   <span data-ttu-id="86d29-146">Copie le composant de pipeline créé à le \<chemin d’Installation > dossier \Pipeline Components.</span><span class="sxs-lookup"><span data-stu-id="86d29-146">Copies the built pipeline component to the \<Installation Path>\Pipeline Components folder.</span></span>  
  
    -   <span data-ttu-id="86d29-147">crée les ports d'envoi et de réception ;</span><span class="sxs-lookup"><span data-stu-id="86d29-147">Creates the send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86d29-148">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="86d29-148">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86d29-149">Pour annuler les modifications apportées par Setup.bat, arrêtez puis redémarrez l'instance de l'hôte à partir de la console MMC Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="86d29-149">To undo changes made by Setup.bat, you must first stop and restart the host instance from the BizTalk Server Administration MMC console.</span></span> <span data-ttu-id="86d29-150">Ensuite, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="86d29-150">Next, run Cleanup.bat.</span></span> <span data-ttu-id="86d29-151">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="86d29-151">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="86d29-152">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="86d29-152">Running This Sample</span></span>  
 <span data-ttu-id="86d29-153">La procédure suivante permet d'exécuter l'exemple de composant Transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="86d29-153">Use the following procedure to run the XSLT Transform Component sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="86d29-154">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="86d29-154">To run this sample</span></span>  
  
1.  <span data-ttu-id="86d29-155">Copiez le fichier DocInstance.xml dans le dossier \In.</span><span class="sxs-lookup"><span data-stu-id="86d29-155">Copy DocInstance.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="86d29-156">Examinez les résultats dans le dossier \Out (le nom du fichier de sortie est guid.htm).</span><span class="sxs-lookup"><span data-stu-id="86d29-156">Examine the results in the \Out folder (the output filename is guid.htm).</span></span>  
  
## <a name="configuring-this-sample-using-smtp"></a><span data-ttu-id="86d29-157">Configuration de l'exemple à l'aide de SMTP</span><span class="sxs-lookup"><span data-stu-id="86d29-157">Configuring This Sample Using SMTP</span></span>  
 <span data-ttu-id="86d29-158">La procédure suivante permet de configurer l'exemple de composant Transformation XSLT à des fins de compatibilité avec un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="86d29-158">Use the following procedure to configure the XSLT Transform Component sample to work with an SMTP server.</span></span>  
  
#### <a name="to-configure-this-sample-using-smtp"></a><span data-ttu-id="86d29-159">Pour configurer l'exemple à l'aide de SMTP</span><span class="sxs-lookup"><span data-stu-id="86d29-159">To configure this sample using SMTP</span></span>  
  
1.  <span data-ttu-id="86d29-160">Reconfigurez le port d'envoi du composant Transformation XSLT de manière à ce qu'il utilise un type de transport SMTP.</span><span class="sxs-lookup"><span data-stu-id="86d29-160">Reconfigure the XSLT Transform Component send port to use an SMTP transport type.</span></span>  
  
2.  <span data-ttu-id="86d29-161">Configurez le paramètre SMTP en modifiant les paramètres d'adresse (URI) de manière à ce qu'ils correspondent à votre configuration SMTP.</span><span class="sxs-lookup"><span data-stu-id="86d29-161">Configure the SMTP setting by changing the address (URI) parameters to match your SMTP configuration.</span></span>  
  
## <a name="running-this-sample-with-output-to-an-smtp-port"></a><span data-ttu-id="86d29-162">Exécution de l'exemple avec une sortie vers un port SMTP</span><span class="sxs-lookup"><span data-stu-id="86d29-162">Running This Sample with Output to an SMTP Port</span></span>  
 <span data-ttu-id="86d29-163">La procédure suivante permet d'exécuter l'exemple de composant Transformation XSLT avec une sortie vers un port SMTP.</span><span class="sxs-lookup"><span data-stu-id="86d29-163">Use the following procedure to run the XSLT Transform Component sample with output to an SMTP port.</span></span>  
  
#### <a name="to-run-this-sample-with-output-to-an-smtp-port"></a><span data-ttu-id="86d29-164">Pour exécuter l'exemple avec une sortie vers un port SMTP</span><span class="sxs-lookup"><span data-stu-id="86d29-164">To run this sample with output to an SMTP port</span></span>  
  
1.  <span data-ttu-id="86d29-165">Copiez le fichier DocInstance.xml dans le dossier \In.</span><span class="sxs-lookup"><span data-stu-id="86d29-165">Copy DocInstance.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="86d29-166">Examinez les résultats dans le client de messagerie associé au destinataire configuré pour le port SMTP.</span><span class="sxs-lookup"><span data-stu-id="86d29-166">Examine the results in the mail client for the recipient that SMTP is configured to send to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d29-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86d29-167">See Also</span></span>  
 [<span data-ttu-id="86d29-168">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="86d29-168">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)
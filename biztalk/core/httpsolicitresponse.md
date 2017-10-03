---
title: HTTPSolicitResponse | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: b149544e-3279-4ac9-b31f-fff3e41ec8e7
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59f5c2821af02fb87727a4096f4b6e586bfd5b4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="httpsolicitresponse"></a><span data-ttu-id="5ce73-102">HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="5ce73-102">HTTPSolicitResponse</span></span>
<span data-ttu-id="5ce73-103">L'exemple HTTPSolicitResponse montre comment créer une orchestration Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui se sert d'une application ASP.NET pour faciliter le traitement des données d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5ce73-103">The HTTPSolicitResponse sample demonstrates how to create a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that leverages an ASP.NET application to help process orchestration data.</span></span> <span data-ttu-id="5ce73-104">Dans cet exemple, l'orchestration utilise un port de requête/réponse pour envoyer un message à l'application ASP.NET et pour récupérer la réponse.</span><span class="sxs-lookup"><span data-stu-id="5ce73-104">In this sample, the orchestration makes use of a request/response port to send a message to the ASP.NET application and to retrieve the response.</span></span> <span data-ttu-id="5ce73-105">L'intégration entre l'orchestration BizTalk Server et l'application ASP.NET est effectuée à l'aide de l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="5ce73-105">You achieve the integration between the BizTalk Server orchestration and the ASP.NET application by using the HTTP adapter.</span></span> <span data-ttu-id="5ce73-106">Pour plus d’informations, consultez [adaptateur HTTP](../core/http-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="5ce73-106">For more information, see [HTTP Adapter](../core/http-adapter.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5ce73-107">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-107">What This Sample Does</span></span>  
 <span data-ttu-id="5ce73-108">Cet exemple consiste en une orchestration BizTalk Server qui reçoit une requête contenant deux nombres à multiplier, et qui satisfait cette requête au moyen de la séquence d'étapes suivante :</span><span class="sxs-lookup"><span data-stu-id="5ce73-108">This sample consists of a BizTalk Server orchestration that receives a request containing two numbers to be multiplied, and satisfies that request using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="5ce73-109">L'orchestration BizTalk Server récupère un fichier d'entrée .xml dans un dossier spécifique.</span><span class="sxs-lookup"><span data-stu-id="5ce73-109">The BizTalk Server orchestration retrieves an .xml input file from a specific folder.</span></span>  
  
2.  <span data-ttu-id="5ce73-110">L'orchestration utilise une requête HTTP pour transmettre le XML du fichier vers une application ASP.NET de multiplication.</span><span class="sxs-lookup"><span data-stu-id="5ce73-110">The orchestration uses an HTTP request to forward the XML from the file to a multiplier ASP.NET application.</span></span>  
  
3.  <span data-ttu-id="5ce73-111">L'application ASP.NET de multiplication répond à la requête HTTP en effectuant la multiplication et en renvoyant le résultat sous forme de XML dans la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="5ce73-111">The multiplier ASP.NET application responds to the HTTP request by performing the multiplication and returning the result as XML in the HTTP response.</span></span>  
  
4.  <span data-ttu-id="5ce73-112">L'orchestration reçoit le résultat sous forme de XML dans une réponse XML et écrit ce résultat dans un fichier .xml dans un dossier spécifique.</span><span class="sxs-lookup"><span data-stu-id="5ce73-112">The orchestration receives the result as XML in an HTTP response, and writes that result to an .xml file in a specific folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5ce73-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="5ce73-114">\<*Exemples de chemin d’accès*> \AdaptersUsage\HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="5ce73-114">\<*Samples Path*>\AdaptersUsage\HTTPSolicitResponse</span></span>  
  
 <span data-ttu-id="5ce73-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5ce73-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5ce73-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5ce73-116">File(s)</span></span>|<span data-ttu-id="5ce73-117"> Description</span><span class="sxs-lookup"><span data-stu-id="5ce73-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ce73-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5ce73-118">Cleanup.bat</span></span>|<span data-ttu-id="5ce73-119">Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="5ce73-119">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="5ce73-120">HttpSolicitResponse.btproj, HttpSolicitResponse.sln</span><span class="sxs-lookup"><span data-stu-id="5ce73-120">HttpSolicitResponse.btproj, HttpSolicitResponse.sln</span></span>|<span data-ttu-id="5ce73-121">Fournissent des fichiers projet et source pour le projet BizTalk contenant l'orchestration qui utilise l'application ASP.NET de multiplication, les schémas associés, etc.</span><span class="sxs-lookup"><span data-stu-id="5ce73-121">Provides project and source files for the BizTalk project that contains the orchestration that uses the multiplier ASP.NET application, the associated schemas, and so on.</span></span>|  
|<span data-ttu-id="5ce73-122">HttpSolicitResponseBinding.xml</span><span class="sxs-lookup"><span data-stu-id="5ce73-122">HttpSolicitResponseBinding.xml</span></span>|<span data-ttu-id="5ce73-123">Fournit une configuration automatisée notamment la liaison de port.</span><span class="sxs-lookup"><span data-stu-id="5ce73-123">Provides for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="5ce73-124">MultiplyRequest.xsd, MultiplyResponse.xsd</span><span class="sxs-lookup"><span data-stu-id="5ce73-124">MultiplyRequest.xsd, MultiplyResponse.xsd</span></span>|<span data-ttu-id="5ce73-125">Fournissent respectivement des schémas pour la requête de multiplication et les messages XML de réponse.</span><span class="sxs-lookup"><span data-stu-id="5ce73-125">Provides schemas for the multiplication request and response XML messages, respectively.</span></span>|  
|<span data-ttu-id="5ce73-126">MultiplyTwoIntegers.odx</span><span class="sxs-lookup"><span data-stu-id="5ce73-126">MultiplyTwoIntegers.odx</span></span>|<span data-ttu-id="5ce73-127">Fournit une orchestration BizTalk Server qui reçoit un fichier .xml demandant une opération de multiplication, transfère la requête à l'application ASP.NET de multiplication, et écrit la réponse dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="5ce73-127">Provides a BizTalk Server orchestration that receives an .xml file requesting a multiplication operation, forwards the request to the multiplier ASP.NET application, and writes its response to a file.</span></span>|  
|<span data-ttu-id="5ce73-128">request_in.xml</span><span class="sxs-lookup"><span data-stu-id="5ce73-128">request_in.xml</span></span>|<span data-ttu-id="5ce73-129">Exemple de fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5ce73-129">Sample input file.</span></span>|  
|<span data-ttu-id="5ce73-130">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5ce73-130">Setup.bat</span></span>|<span data-ttu-id="5ce73-131">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5ce73-131">Builds and initializes this sample.</span></span>|  
|<span data-ttu-id="5ce73-132">Dans le dossier \Multiplier :</span><span class="sxs-lookup"><span data-stu-id="5ce73-132">In the \Multiplier folder:</span></span><br /><br /> <span data-ttu-id="5ce73-133">Multiplier.aspx, Multiplier.aspx.cs, Multiplier.sln</span><span class="sxs-lookup"><span data-stu-id="5ce73-133">Multiplier.aspx, Multiplier.aspx.cs, Multiplier.sln</span></span>|<span data-ttu-id="5ce73-134">Contiennent des fichiers constituant l'application ASP.NET qui effectue le service de multiplication, y compris les fichiers de projet et de solution, les fichiers ASPX, Microsoft Visual C# .NET, les fichiers sources, etc.</span><span class="sxs-lookup"><span data-stu-id="5ce73-134">Contains files that constitute the ASP.NET application that implements the multiplier service, including project and solution files, ASPX files, Microsoft Visual C# .NET source files, and so on.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="5ce73-135">Création et initialisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-135">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="5ce73-136">Les procédures suivantes permettent de créer et d'initialiser l'exemple HTTPSolicitResponse.</span><span class="sxs-lookup"><span data-stu-id="5ce73-136">Use the following procedure to build and initialize the HTTPSolicitResponse sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ce73-137">Cet exemple ne fonctionne pas si le nom de l'emplacement de réception contient des caractères en majuscules.</span><span class="sxs-lookup"><span data-stu-id="5ce73-137">This sample doesn't work if the name of the receive location contains any uppercase characters.</span></span>  
  
#### <a name="to-build-and-initialize-the-sample"></a><span data-ttu-id="5ce73-138">Pour créer et initialiser l’exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-138">To build and initialize the sample</span></span>  
  
1.  <span data-ttu-id="5ce73-139">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5ce73-139">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="5ce73-140">\<*Exemples de chemin d’accès*> \AdaptersUsage\HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="5ce73-140">\<*Samples Path*>\AdaptersUsage\HTTPSolicitResponse</span></span>  
  
2.  <span data-ttu-id="5ce73-141">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ce73-141">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="5ce73-142">Création des dossiers d'entrée et de sortie pour cet exemple :</span><span class="sxs-lookup"><span data-stu-id="5ce73-142">Creates the input and output folders for this sample:</span></span>  
  
         <span data-ttu-id="5ce73-143">\<*Exemples de chemin d’accès*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput</span><span class="sxs-lookup"><span data-stu-id="5ce73-143">\<*Samples Path*>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput</span></span>  
  
         <span data-ttu-id="5ce73-144">\<*Exemples de chemin d’accès*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput</span><span class="sxs-lookup"><span data-stu-id="5ce73-144">\<*Samples Path*>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput</span></span>  
  
    -   <span data-ttu-id="5ce73-145">Compilation et configuration l'application ASP.NET de multiplication utilisée par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5ce73-145">Compiles and configures the multiplier ASP.NET application used by this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-146">Lors de la création de pool d’applications dans IIS Manager, définissez la **DefaultAppPool** version .NET Framework à **.Net Framework v4.0**.</span><span class="sxs-lookup"><span data-stu-id="5ce73-146">While creating application pool in IIS Manager, set the **DefaultAppPool** .NET Framework version to **.Net Framework v4.0**.</span></span>  
  
    -   <span data-ttu-id="5ce73-147">Compilation et déploiement de l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisée dans l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="5ce73-147">Compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration used in this sample.</span></span>  
  
    -   <span data-ttu-id="5ce73-148">Création et liaison de l'emplacement et des ports [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de réception nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5ce73-148">Creates and binds the necessary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-149">Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :</span><span class="sxs-lookup"><span data-stu-id="5ce73-149">This sample displays the following warnings when creating and binding the ports:</span></span>  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "HttpSolicitResponseReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.HttpSolicitResponse.MultiplyTwoIntegers"; updating with first available host.`  
  
    -   <span data-ttu-id="5ce73-150">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5ce73-150">Enables the receive location, and starts the send port.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-151">Dans cet exemple, l'orchestration utilise un port bidirectionnel pour l'interaction HTTP avec l'application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ce73-151">The orchestration in this sample uses a two-way port for the HTTP interaction with the ASP.NET application.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-152">Avant de tenter d'exécuter cet exemple, vous devez confirmer que BizTalk n'a signalé aucune erreur durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="5ce73-152">You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-153">Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="5ce73-153">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="5ce73-154">Celle-ci permet de signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="5ce73-154">Use this key pair to sign the resulting assemblies.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ce73-155">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="5ce73-155">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="5ce73-156">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="5ce73-156">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="5ce73-157">Exécution de l’exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-157">Running the Sample</span></span>  
 <span data-ttu-id="5ce73-158">La procédure suivante permet d'exécuter l'exemple HTTPSolicitResponse.</span><span class="sxs-lookup"><span data-stu-id="5ce73-158">Use the following procedure to run the HTTPSolicitResponse sample.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="5ce73-159">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="5ce73-159">To run the sample</span></span>  
  
1.  <span data-ttu-id="5ce73-160">Collez une copie du fichier request_in.xml dans le dossier HttpSolicitResponseInput.</span><span class="sxs-lookup"><span data-stu-id="5ce73-160">Paste a copy of the file request_in.xml into the folder HttpSolicitResponseInput.</span></span>  
  
2.  <span data-ttu-id="5ce73-161">Observez le fichier .xml créé dans le dossier HttpSolicitResponseOutput.</span><span class="sxs-lookup"><span data-stu-id="5ce73-161">Observe the .xml file created in the folder HttpSolicitResponseOutput.</span></span> <span data-ttu-id="5ce73-162">Le nom de ce fichier .xml a pour base le GUID de l'ID du message.</span><span class="sxs-lookup"><span data-stu-id="5ce73-162">The name of this .xml file is based on the message ID GUID.</span></span> <span data-ttu-id="5ce73-163">Ce fichier contient le résultat au format XML de l'opération de multiplication.</span><span class="sxs-lookup"><span data-stu-id="5ce73-163">This file contains the XML-formatted result of the multiplication operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ce73-164">Vous pouvez modifier les valeurs d'opérande dans le fichier d'entrée pour effectuer une autre opération de multiplication.</span><span class="sxs-lookup"><span data-stu-id="5ce73-164">You can change the operand values in the input file to perform a different multiplication operation.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="5ce73-165">Commentaires</span><span class="sxs-lookup"><span data-stu-id="5ce73-165">Comments</span></span>  
 <span data-ttu-id="5ce73-166">Vous pouvez adapter cet exemple pour communiquer avec un autre système externe qui présente une interface HTTP.</span><span class="sxs-lookup"><span data-stu-id="5ce73-166">You can adapt this sample to communicate with a different external system that exposes an HTTP interface.</span></span>  
  
 <span data-ttu-id="5ce73-167">Les fichiers MultiplyRequest.xsd et MultiplyResponse.xsd sont les schémas XML qui définissent le format des données d'entrée et de sortie de l'application ASP.NET de multiplication.</span><span class="sxs-lookup"><span data-stu-id="5ce73-167">The files MultiplyRequest.xsd and MultiplyResponse.xsd are the XML schemas that define the format of the input and output data for the multiplier ASP.NET application.</span></span> <span data-ttu-id="5ce73-168">L'orchestration utilise ces fichiers pour définir les types de message requête et réponse.</span><span class="sxs-lookup"><span data-stu-id="5ce73-168">The orchestration uses these files to define the request and response message types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce73-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ce73-169">See Also</span></span>  
 [<span data-ttu-id="5ce73-170">Exemples d’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="5ce73-170">HTTP Adapter Samples</span></span>](../core/http-adapter-samples.md)
---
title: MethodCall (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, calling
- examples, orchestrations
- orchestrations, methods
ms.assetid: 6bdc72da-9478-403a-b706-3089b7374ac7
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16b97b7c81b36774bcf2eaff53a1a4ff91b6f9e8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="methodcall-biztalk-server-sample"></a><span data-ttu-id="ea2c3-102">MethodCall (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ea2c3-102">MethodCall (BizTalk Server Sample)</span></span>
<span data-ttu-id="ea2c3-103">L'exemple MethodCall illustre l'appel d'une méthode .NET à partir d'une orchestration BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-103">The MethodCall sample demonstrates how to call a .NET-based method from a BizTalk Server orchestration.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ea2c3-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ea2c3-104">What This Sample Does</span></span>  
 <span data-ttu-id="ea2c3-105">Cet exemple interagit avec une méthode .NET en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-105">This sample interacts with a .NET-based method using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="ea2c3-106">L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère un fichier d'entrée XML dans le dossier In.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-106">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an XML input file from the In folder.</span></span> <span data-ttu-id="ea2c3-107">Ce fichier contient des informations sur une addition ou une soustraction que vous souhaitez voir la bibliothèque d'écritures mathématiques effectuer.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-107">This file contains information about an addition or subtraction you want the math library to perform.</span></span>  
  
2.  <span data-ttu-id="ea2c3-108">L'orchestration appelle la bibliothèque d'écritures mathématiques intégrée afin de réaliser l'addition ou la soustraction spécifiée dans le fichier d'entrée XML.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-108">The orchestration calls the included math library to perform the addition or subtraction specified in the XML input file.</span></span>  
  
3.  <span data-ttu-id="ea2c3-109">L’approprié à la méthode de la bibliothèque mathématique, soit **ajouter** ou **soustraction**, effectue le calcul demandé et empaquette le résultat sous forme de document XML.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-109">The appropriate math library method, either **Add** or **Subtract**, performs the requested calculation and packages the result as an XML document.</span></span>  
  
4.  <span data-ttu-id="ea2c3-110">L'orchestration place le fichier .xml résultant dans le dossier Out.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-110">The orchestration places the resulting .xml file in the Out folder.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="ea2c3-111">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="ea2c3-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="ea2c3-112">Il illustre les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-112">This sample demonstrates the following functionalities:</span></span>  
  
-   <span data-ttu-id="ea2c3-113">Exploitation des propriétés promues dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-113">Leveraging the promoted properties in an orchestration.</span></span> <span data-ttu-id="ea2c3-114">Les trois éléments dans InputSchema.xsd sont promus en tant que champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-114">The three elements in InputSchema.xsd are promoted as distinguished fields.</span></span> <span data-ttu-id="ea2c3-115">Lorsque l'orchestration reçoit le message d'entrée, elle récupère les valeurs de ces trois champs et les affecte aux variables correspondantes qui sont déclarées dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-115">When the orchestration receives the input message, it gets the values of these three fields and assigns them to the corresponding variables declared in the orchestration.</span></span>  
  
-   <span data-ttu-id="ea2c3-116">À l’aide de la **décider** forme pour exprimer la logique « if-then-else » dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-116">Using the **Decide** shape to express "if-then-else" logic in an orchestration.</span></span> <span data-ttu-id="ea2c3-117">Une fois que l’orchestration assigne les valeurs des champs distinctifs à des variables internes, il passe à la **décider** forme pour vérifier si une addition ou soustraction doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-117">After the orchestration assigns the values of distinguished fields to internal variables, it enters the **Decide** shape to check whether an addition or subtraction should be performed.</span></span> <span data-ttu-id="ea2c3-118">Si aucune opération ne doit être effectuée, l'orchestration est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-118">If no operation needs to be performed, the orchestration terminates.</span></span>  
  
-   <span data-ttu-id="ea2c3-119">Appel d'un assembly externe à partir d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-119">Calling an external assembly from an orchestration.</span></span> <span data-ttu-id="ea2c3-120">Lorsqu'une addition doit être effectuée, l'orchestration appelle un assembly C# externe et transmet deux paramètres nécessaires pour effectuer l'opération.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-120">If an addition is to be performed, the orchestration calls an external C# assembly and passes in two parameters to perform the addition.</span></span> <span data-ttu-id="ea2c3-121">La même procédure s'applique dans le cas d'une soustraction.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-121">The same procedures apply to a subtraction.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea2c3-122">Vous devez installer l'assembly dans le GAC (Global Assembly Cache) avant de pouvoir l'appeler à partir de l'orchestration ; sinon, vous recevez une erreur XLANG au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-122">You need to install the assembly to the global assembly cache before you can call it from the orchestration; otherwise you will receive an XLANG error during run time.</span></span>  
  
-   <span data-ttu-id="ea2c3-123">À l’aide de la **assignation du Message** forme pour construire le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-123">Using the **Message Assignment** shape to construct the output message.</span></span>  
  
-   <span data-ttu-id="ea2c3-124">Débogage de l'orchestration en ajoutant le code suivant dans la forme Expression :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-124">Debugging the orchestration by putting the following code in the Expression shape:</span></span>  
  
    ```  
    System.Diagnostics.Debug.WriteLine(iResult);  
    ```  
  
     <span data-ttu-id="ea2c3-125">Vous pouvez également écrire le résultat dans le journal des événements comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-125">You can also write the result to the event log by using:</span></span>  
  
    ```  
    System.Diagnostics.EventLog.WriteEntry("MethodCall SDK Sample Debug", System.String.Format("Result = {0}", iResult);  
    ```  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ea2c3-126">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ea2c3-126">Where to Find This Sample</span></span>  
 <span data-ttu-id="ea2c3-127">\<*Exemples de chemin d’accès*\>\Orchestrations\MethodCall\\</span><span class="sxs-lookup"><span data-stu-id="ea2c3-127">\<*Samples Path*\>\Orchestrations\MethodCall\\</span></span>  
  
 <span data-ttu-id="ea2c3-128">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-128">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ea2c3-129">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="ea2c3-129">File(s)</span></span>|<span data-ttu-id="ea2c3-130"> Description</span><span class="sxs-lookup"><span data-stu-id="ea2c3-130">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea2c3-131">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="ea2c3-131">Cleanup.bat</span></span>|<span data-ttu-id="ea2c3-132">Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-132">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="ea2c3-133">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-133">Removes send and receive ports.</span></span> <span data-ttu-id="ea2c3-134">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-134">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="ea2c3-135">Input.xml</span><span class="sxs-lookup"><span data-stu-id="ea2c3-135">Input.xml</span></span>|<span data-ttu-id="ea2c3-136">Exemple de fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-136">Sample input file.</span></span>|  
|<span data-ttu-id="ea2c3-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="ea2c3-137">Setup.bat</span></span>|<span data-ttu-id="ea2c3-138">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-138">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="ea2c3-139">Dans le dossier \MathLibrary :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-139">In the \MathLibrary folder:</span></span><br /><br /> <span data-ttu-id="ea2c3-140">AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj</span><span class="sxs-lookup"><span data-stu-id="ea2c3-140">AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj</span></span>|<span data-ttu-id="ea2c3-141">Projet et fichiers sources pour la bibliothèque d'écritures mathématiques utilisée par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-141">Project and source files for the math library used by this sample.</span></span>|  
|<span data-ttu-id="ea2c3-142">Dans le dossier \MethodCallSample :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-142">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="ea2c3-143">InputSchema.xsd, OutputSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="ea2c3-143">InputSchema.xsd, OutputSchema.xsd</span></span>|<span data-ttu-id="ea2c3-144">Schémas pour les fichiers .xml d'entrée et de sortie, respectivement.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-144">Schemas for the input and output .xml files, respectively.</span></span>|  
|<span data-ttu-id="ea2c3-145">Dans le dossier \MethodCallSample :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-145">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="ea2c3-146">MethodCallSample.btproj, MethodCallSample.sln</span><span class="sxs-lookup"><span data-stu-id="ea2c3-146">MethodCallSample.btproj, MethodCallSample.sln</span></span>|<span data-ttu-id="ea2c3-147">Fichiers projet et solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-147">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="ea2c3-148">Dans le dossier \MethodCallSample :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-148">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="ea2c3-149">MethodCallSampleBinding.xml</span><span class="sxs-lookup"><span data-stu-id="ea2c3-149">MethodCallSampleBinding.xml</span></span>|<span data-ttu-id="ea2c3-150">Utilisé pour l’installation automatique, notamment la liaison de port.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-150">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="ea2c3-151">Dans le dossier \MethodCallSample :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-151">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="ea2c3-152">MethodCallService.odx</span><span class="sxs-lookup"><span data-stu-id="ea2c3-152">MethodCallService.odx</span></span>|<span data-ttu-id="ea2c3-153">Orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui appelle la bibliothèque d'écritures mathématiques afin d'effectuer le calcul demandé.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-153">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that calls the math library to perform the requested calculation.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="ea2c3-154">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ea2c3-154">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-methodcall-sample"></a><span data-ttu-id="ea2c3-155">Pour créer et initialiser l'exemple MethodCall</span><span class="sxs-lookup"><span data-stu-id="ea2c3-155">To build and initialize the MethodCall sample</span></span>  
  
1.  <span data-ttu-id="ea2c3-156">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-156">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="ea2c3-157">\<*Exemples de chemin d’accès*\>\Orchestrations\MethodCall</span><span class="sxs-lookup"><span data-stu-id="ea2c3-157">\<*Samples Path*\>\Orchestrations\MethodCall</span></span>  
  
2.  <span data-ttu-id="ea2c3-158">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea2c3-158">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="ea2c3-159">Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier MethodCall.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-159">Creates the input (In) and output (Out) folders for this sample in the MethodCall folder.</span></span>  
  
    -   <span data-ttu-id="ea2c3-160">Compilation des projets de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, puis déploiement des assemblys qui en résultent.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-160">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, and deploys the resulting assemblies.</span></span>  
  
    -   <span data-ttu-id="ea2c3-161">Création et liaison à l'orchestration de l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-161">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.</span></span>  
  
    -   <span data-ttu-id="ea2c3-162">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-162">Enables the receive location, and starts the send port.</span></span> <span data-ttu-id="ea2c3-163">Inscrit et démarre l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-163">Enlists and starts orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea2c3-164">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-164">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="ea2c3-165">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="ea2c3-165">Running This Sample</span></span>  
  
#### <a name="to-run-the-methodcall-sample"></a><span data-ttu-id="ea2c3-166">Pour exécuter l'exemple MethodCall</span><span class="sxs-lookup"><span data-stu-id="ea2c3-166">To run the MethodCall sample</span></span>  
  
1.  <span data-ttu-id="ea2c3-167">Collez une copie du fichier Input.xml dans le dossier In.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-167">Paste a copy of the file Input.xml into the In folder.</span></span>  
  
2.  <span data-ttu-id="ea2c3-168">Observez le fichier .xml créé dans le dossier Out.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-168">Observe the .xml file created in the Out folder.</span></span> <span data-ttu-id="ea2c3-169">Ce fichier contient le résultat de l'opération d'addition ou de soustraction demandée.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-169">This file contains the result of the requested addition or subtraction calculation.</span></span> <span data-ttu-id="ea2c3-170">Le format du nom de ce fichier est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le message .</span><span class="sxs-lookup"><span data-stu-id="ea2c3-170">The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  
  
3.  <span data-ttu-id="ea2c3-171">Vous pouvez modifier le fichier d'entrée de manière à réaliser des additions ou des soustractions différentes.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-171">You can modify the input file to request different addition or subtraction calculations.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="ea2c3-172">Désinstallation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ea2c3-172">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-methodcall-sample"></a><span data-ttu-id="ea2c3-173">Pour désinstaller l'exemple MethodCall</span><span class="sxs-lookup"><span data-stu-id="ea2c3-173">To uninstall the MethodCall sample</span></span>  
  
1.  <span data-ttu-id="ea2c3-174">À un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à \< *exemples de chemin*\>\Orchestrations\MethodCall\\.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-174">At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*\>\Orchestrations\MethodCall\\.</span></span>  
  
2.  <span data-ttu-id="ea2c3-175">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="ea2c3-175">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2c3-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea2c3-176">See Also</span></span>  
 [<span data-ttu-id="ea2c3-177">Orchestrations (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ea2c3-177">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)
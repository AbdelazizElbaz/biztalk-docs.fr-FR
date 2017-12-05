---
title: "Énumérer les emplacements (exemple BizTalk Server) de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enumerating
- examples, receive locations
ms.assetid: 27ff8ac6-7e8e-4dde-84d1-d21bf417ddd7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fcdc400395d7bbfd6de8f9bc0fca85114a25dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="enumerate-receive-locations-biztalk-server-sample"></a><span data-ttu-id="88867-102">Énumérer les emplacements (exemple BizTalk Server) de réception</span><span class="sxs-lookup"><span data-stu-id="88867-102">Enumerate Receive Locations (BizTalk Server Sample)</span></span>
<span data-ttu-id="88867-103">L'exemple d'énumération des emplacements de réception décrit la récupération d'informations détaillées sur un ou plusieurs emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="88867-103">The Enumerate Receive Locations sample demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="88867-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="88867-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="88867-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="88867-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="88867-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="88867-106">What This Sample Does</span></span>  
 <span data-ttu-id="88867-107">Cet exemple inclut une version de Visual Basic Scripting Edition (VBScript) qui accède au modèle objet WMI Windows et une version Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88867-107">This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows WMI object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework.</span></span> <span data-ttu-id="88867-108">En dernier lieu, ces deux versions accèdent au fournisseur WMI de BizTalk Server pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="88867-108">Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:</span></span>  
  
-   <span data-ttu-id="88867-109">requête pour obtenir le jeu d'emplacements de réception configurés ou un emplacement de réception particulier, d'après son nom ;</span><span class="sxs-lookup"><span data-stu-id="88867-109">Query for the set of configured receive locations or for a specific receive location, given its name.</span></span>  
  
-   <span data-ttu-id="88867-110">récupération et affichage des détails concernant chaque emplacement de réception qui vous intéresse ;</span><span class="sxs-lookup"><span data-stu-id="88867-110">Retrieve and display details about each receive location of interest.</span></span>  
  
-   <span data-ttu-id="88867-111">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="88867-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="88867-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="88867-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="88867-113">Les exemples se trouvent dans les emplacements du Kit de développement logiciel (SDK) suivants :</span><span class="sxs-lookup"><span data-stu-id="88867-113">The samples are located in the following SDK locations:</span></span>  
  
-   <span data-ttu-id="88867-114">Version VBScript : \< *exemples de chemin*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="88867-114">VBScript version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span></span>  
  
-   <span data-ttu-id="88867-115">Version Visual c# : \< *exemples de chemin*\>\Admin\WMI\Enumerate Receive Locations\CSharp\\</span><span class="sxs-lookup"><span data-stu-id="88867-115">Visual C# version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\\</span></span>  
  
 <span data-ttu-id="88867-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="88867-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="88867-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="88867-117">File(s)</span></span>|<span data-ttu-id="88867-118"> Description</span><span class="sxs-lookup"><span data-stu-id="88867-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88867-119">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="88867-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="88867-120">EnumRecLocs.vbs</span><span class="sxs-lookup"><span data-stu-id="88867-120">EnumRecLocs.vbs</span></span>|<span data-ttu-id="88867-121">Fichier VBScript qui récupère les détails concernant tous les emplacements de réception configurés.</span><span class="sxs-lookup"><span data-stu-id="88867-121">VBScript file that retrieves details about all configured receive locations.</span></span>|  
|<span data-ttu-id="88867-122">Dans le dossier \CSharp :</span><span class="sxs-lookup"><span data-stu-id="88867-122">In the \CSharp folder:</span></span><br /><br /> <span data-ttu-id="88867-123">App.ico, AssemblyInfo.cs, BTSampleEnumerateRLs.csproj, BTSampleEnumerateRLs.sln, EnumRLs.cs</span><span class="sxs-lookup"><span data-stu-id="88867-123">App.ico, AssemblyInfo.cs, BTSampleEnumerateRLs.csproj, BTSampleEnumerateRLs.sln, EnumRLs.cs</span></span>|<span data-ttu-id="88867-124">Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui récupère les détails sur tous les emplacements de réception configurés ou sur un emplacement de réception particulier.</span><span class="sxs-lookup"><span data-stu-id="88867-124">Project, solution, and source files for building a Visual C# command-line application that retrieves details about all configured receive locations, or about a specific receive location.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="88867-125">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="88867-125">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="88867-126">La version VBScript de l'exemple d'énumération des emplacements de réception comporte un seul fichier de script Visual Basic, que vous ne devez ni installer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="88867-126">The VBScript version of the Enumerate Receive Locations sample consists of a single Visual Basic script file that you do not need to build or initialize.</span></span>  
  
#### <a name="to-build-the-visual-c-version-of-the-enumerate-receive-locations-sample"></a><span data-ttu-id="88867-127">Pour créer la version Visual C# de l'exemple d'énumération des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="88867-127">To build the Visual C# version of the Enumerate Receive Locations sample</span></span>  
  
1.  <span data-ttu-id="88867-128">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution BTSampleEnumerateRLs.sln.</span><span class="sxs-lookup"><span data-stu-id="88867-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnumerateRLs.sln.</span></span>  
  
2.  <span data-ttu-id="88867-129">Dans le **générer** menu, cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="88867-129">In the **Build** menu, click **Build Solution**.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="88867-130">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="88867-130">Running This Sample</span></span>  
  
#### <a name="to-run-the-enumerate-receive-locations-sample"></a><span data-ttu-id="88867-131">Pour exécuter l'exemple d'énumération des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="88867-131">To run the Enumerate Receive Locations sample</span></span>  
  
1.  <span data-ttu-id="88867-132">Dans une fenêtre de commandes, accédez à l'un des dossiers suivants, selon que vous ayez choisi d'exécuter la version VBScript ou Visual C# de cet exemple, respectivement :</span><span class="sxs-lookup"><span data-stu-id="88867-132">In a command window, navigate to one of the following folders, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively:</span></span>  
  
     <span data-ttu-id="88867-133">\<*Exemples de chemin d’accès*\>\Admin\WMI\Enumerate Locations\VBScript\ de réception</span><span class="sxs-lookup"><span data-stu-id="88867-133">\<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span></span>  
  
     <span data-ttu-id="88867-134">\<*Exemples de chemin d’accès*\>\Admin\WMI\Enumerate Locations\CSharp\bin\Debug\ de réception</span><span class="sxs-lookup"><span data-stu-id="88867-134">\<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="88867-135">En fonction de votre choix pour l'exécution de cet exemple (à savoir soit la version VBScript soit la version Visual C#), exécutez respectivement le fichier EnumRecLocs.vbs à l'aide du programme cscript ou le fichier EnumRl.exe.</span><span class="sxs-lookup"><span data-stu-id="88867-135">Either run the file EnumRecLocs.vbs using the cscript program, or run the file EnumRl.exe, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively.</span></span> <span data-ttu-id="88867-136">Pour la version Visual C#, exécutez l'un des deux arguments de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="88867-136">For the Visual C# version, pass one of the following two command-line arguments:</span></span>  
  
    -   <span data-ttu-id="88867-137">**\<ReceiveLocationName\>.**</span><span class="sxs-lookup"><span data-stu-id="88867-137">**\<ReceiveLocationName\>.**</span></span> <span data-ttu-id="88867-138">Correspond au nom de l'emplacement de réception pour lequel les détails seront affichés.</span><span class="sxs-lookup"><span data-stu-id="88867-138">The name of the receive location for which details will be displayed.</span></span> <span data-ttu-id="88867-139">Si le nom de l'emplacement de réception contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="88867-139">If the receive location name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="88867-140">**/?.**</span><span class="sxs-lookup"><span data-stu-id="88867-140">**/?.**</span></span> <span data-ttu-id="88867-141">Affiche l’aide.</span><span class="sxs-lookup"><span data-stu-id="88867-141">Displays help.</span></span>  
  
         <span data-ttu-id="88867-142">Par exemple (VBScript) :</span><span class="sxs-lookup"><span data-stu-id="88867-142">For example (VBScript):</span></span>  
  
        ```  
        cscript EnumRecLocs.vbs  
        ```  
  
         <span data-ttu-id="88867-143">- OU - (version Visual C#) :</span><span class="sxs-lookup"><span data-stu-id="88867-143">-OR- (Visual C#):</span></span>  
  
        ```  
        EnumRl "My Receive Location #3"  
        ```  
  
         <span data-ttu-id="88867-144">- OU - (version Visual C#) :</span><span class="sxs-lookup"><span data-stu-id="88867-144">-OR- (Visual C#):</span></span>  
  
        ```  
        EnumRl /?  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="88867-145">La version VBScript de cet exemple n'accepte aucun paramètre de ligne de commande ; elle est donc uniquement capable de récupérer et d'afficher les détails concernant tous les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="88867-145">The VBScript version of this sample does not accept any command-line parameters, and therefore is only capable of retrieving and displaying details about all configured receive locations.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="88867-146">Commentaires</span><span class="sxs-lookup"><span data-stu-id="88867-146">Comments</span></span>  
 <span data-ttu-id="88867-147">Toutes les tâches que vous pouvez effectuer dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration peut également être effectuée à l’aide de script qui accède au modèle objet WMI Windows et à l’aide de Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88867-147">All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.</span></span>  
  
 <span data-ttu-id="88867-148">Le fichier de script EnumRecLocs.vbs et le fichier source Visual C# EnumRLs.cs contiennent des commentaires détaillés avec des explications plus précises sur les opérations qu'ils exécutent.</span><span class="sxs-lookup"><span data-stu-id="88867-148">The script file EnumRecLocs.vbs and the Visual C# source file EnumRLs.cs contain detailed comments with further explanation about the operations that they perform.</span></span> <span data-ttu-id="88867-149">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="88867-149">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88867-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88867-150">See Also</span></span>  
 [<span data-ttu-id="88867-151">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="88867-151">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)
---
title: "Inscrire l’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, enlisting
- examples, orchestrations
ms.assetid: d8d53e59-2313-40dd-a278-0a29d8eb4ce8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8d85a49b410f0571e8e9cb0be816f1feda139e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="enlist-orchestration-biztalk-server-sample"></a><span data-ttu-id="68940-102">Inscrire l’Orchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="68940-102">Enlist Orchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="68940-103">L'exemple d'inscription de l'orchestration décrit l'inscription d'une orchestration BizTalk Server dans un hôte.</span><span class="sxs-lookup"><span data-stu-id="68940-103">The Enlist Orchestration sample demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="68940-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="68940-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="68940-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="68940-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="68940-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="68940-106">What This Sample Does</span></span>  
 <span data-ttu-id="68940-107">Cet exemple inclut une version de Visual Basic Scripting Edition (VBScript) qui accède au modèle objet Windows Management Instrumentation (WMI) et une version Visual c# qui accède à la **System.Management** fournis par des objets le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68940-107">This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows Management Instrumentation (WMI) object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework.</span></span> <span data-ttu-id="68940-108">En dernier lieu, ces deux versions accèdent au fournisseur WMI de BizTalk Server pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="68940-108">Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:</span></span>  
  
-   <span data-ttu-id="68940-109">pour un nom d'orchestration et un nom d'assembly, création d'une requête pour une orchestration BizTalk Server déployée spécifique ;</span><span class="sxs-lookup"><span data-stu-id="68940-109">Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.</span></span>  
  
-   <span data-ttu-id="68940-110">inscription de l'orchestration dans l'hôte par défaut ;</span><span class="sxs-lookup"><span data-stu-id="68940-110">Enlist that orchestration to the default host.</span></span>  
  
-   <span data-ttu-id="68940-111">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="68940-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="68940-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="68940-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="68940-113">Les exemples se trouvent dans les emplacements du Kit de développement logiciel (SDK) suivants :</span><span class="sxs-lookup"><span data-stu-id="68940-113">The samples are located in the following SDK locations:</span></span>  
  
-   <span data-ttu-id="68940-114">Version VBScript : \< *exemples de chemin*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="68940-114">VBScript version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span></span>  
  
-   <span data-ttu-id="68940-115">Version Visual c# : \< *exemples de chemin*\>\Admin\WMI\Enlist Orchestration\CSharp\\</span><span class="sxs-lookup"><span data-stu-id="68940-115">Visusal C# version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\CSharp\\</span></span>  
  
 <span data-ttu-id="68940-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="68940-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="68940-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="68940-117">File(s)</span></span>|<span data-ttu-id="68940-118"> Description</span><span class="sxs-lookup"><span data-stu-id="68940-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68940-119">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="68940-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="68940-120">EnlistOrch.vbs</span><span class="sxs-lookup"><span data-stu-id="68940-120">EnlistOrch.vbs</span></span>|<span data-ttu-id="68940-121">Fichier VBScript qui utilise des paramètres pour spécifier une orchestration à inscrire dans un hôte.</span><span class="sxs-lookup"><span data-stu-id="68940-121">VBScript file that takes parameters to specify an orchestration to be enlisted to a host.</span></span>|  
|<span data-ttu-id="68940-122">Dans le dossier \CSharp :</span><span class="sxs-lookup"><span data-stu-id="68940-122">In the \CSharp folder:</span></span><br /><br /> <span data-ttu-id="68940-123">App.ico, AssemblyInfo.cs, BTSampleEnlistOrc.csproj, BTSampleEnlistOrc.sln, EnlistOrc.cs</span><span class="sxs-lookup"><span data-stu-id="68940-123">App.ico, AssemblyInfo.cs, BTSampleEnlistOrc.csproj, BTSampleEnlistOrc.sln, EnlistOrc.cs</span></span>|<span data-ttu-id="68940-124">Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui utilise des paramètres pour spécifier une orchestration à inscrire dans un hôte.</span><span class="sxs-lookup"><span data-stu-id="68940-124">Project, solution, and source files for building a Visual C# command-line application that takes parameters to specify an orchestration to be enlisted to a host.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="68940-125">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="68940-125">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="68940-126">La version VBScript de l'exemple d'inscription de l'orchestration comporte un seul fichier de script Visual Basic, que vous ne devez ni installer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="68940-126">The VBScript version of the Enlist Orchestration sample consists of a single Visual Basic script file that you do not need to build or initialize.</span></span>  
  
#### <a name="to-build-the-visual-c-version-of-the-enlist-orchestration-sample"></a><span data-ttu-id="68940-127">Pour créer la version Visual C# de l'exemple d'inscription de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="68940-127">To build the Visual C# version of the Enlist Orchestration sample</span></span>  
  
1.  <span data-ttu-id="68940-128">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution BTSampleEnlistOrc.sln.</span><span class="sxs-lookup"><span data-stu-id="68940-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnlistOrc.sln.</span></span>  
  
2.  <span data-ttu-id="68940-129">Dans le **générer** menu, cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="68940-129">In the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-the-enlist-orchestration-sample"></a><span data-ttu-id="68940-130">Pour exécuter l'exemple d'inscription de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="68940-130">To run the Enlist Orchestration sample.</span></span>  
  
1.  <span data-ttu-id="68940-131">Dans une fenêtre de commandes, accédez à l'un des dossiers suivants, selon que vous envisagiez d'exécuter la version VBScript ou Visual C# de cet exemple, respectivement :</span><span class="sxs-lookup"><span data-stu-id="68940-131">In a command window, navigate to one of the following folders, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively:</span></span>  
  
     <span data-ttu-id="68940-132">\<*Exemples de chemin d’accès*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="68940-132">\<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span></span>  
  
     <span data-ttu-id="68940-133">\<*Exemples de chemin d’accès*\>AdminWMIEnlist OrchestrationCSharpbinDebug</span><span class="sxs-lookup"><span data-stu-id="68940-133">\<*Samples Path*\>AdminWMIEnlist OrchestrationCSharpbinDebug</span></span>  
  
2.  <span data-ttu-id="68940-134">En fonction de votre choix pour l'exécution de cet exemple (à savoir soit la version VBScript soit la version Visual C#), exécutez respectivement le fichier EnlistOrch.vbs à l'aide du programme cscript ou le fichier EnlistOrc.exe.</span><span class="sxs-lookup"><span data-stu-id="68940-134">Either run the file EnlistOrch.vbs using the cscript program, or run the file EnlistOrc.exe, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively.</span></span> <span data-ttu-id="68940-135">Dans les deux cas, exécutez les arguments de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="68940-135">In any event, pass the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="68940-136">**\<** ***OrchestrationName* \>.**</span><span class="sxs-lookup"><span data-stu-id="68940-136">**\<** ***OrchestrationName* \>.**</span></span> <span data-ttu-id="68940-137">Nom de l'orchestration à inscrire.</span><span class="sxs-lookup"><span data-stu-id="68940-137">The name of the orchestration to be enlisted.</span></span>  
  
    -   <span data-ttu-id="68940-138">**\<** ***AssemblyName* \>.**</span><span class="sxs-lookup"><span data-stu-id="68940-138">**\<** ***AssemblyName* \>.**</span></span> <span data-ttu-id="68940-139">Nom de l'assembly dans lequel l'orchestration a été déployée.</span><span class="sxs-lookup"><span data-stu-id="68940-139">The name of the assembly in which the orchestration was deployed.</span></span> <span data-ttu-id="68940-140">Si le nom de l'assembly contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="68940-140">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
         <span data-ttu-id="68940-141">Par exemple : (VBScript) :</span><span class="sxs-lookup"><span data-stu-id="68940-141">For example: (VBScript):</span></span>  
  
        ```  
        cscript EnlistOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         <span data-ttu-id="68940-142">- OU - (version Visual C#) :</span><span class="sxs-lookup"><span data-stu-id="68940-142">-OR- (Visual C#):</span></span>  
  
        ```  
        EnlistOrc MyBusinessOrchestration "My Business Assembly"  
        ```  
  
## <a name="comments"></a><span data-ttu-id="68940-143">Commentaires</span><span class="sxs-lookup"><span data-stu-id="68940-143">Comments</span></span>  
 <span data-ttu-id="68940-144">Toutes les tâches que vous pouvez effectuer dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration peut également être effectuée à l’aide de script qui accède au modèle objet WMI Windows et à l’aide de Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68940-144">All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.</span></span>  
  
 <span data-ttu-id="68940-145">Le fichier de script EnlistOrch.vbs et le fichier source Visual C# EnlistOrc.cs contiennent des commentaires détaillés avec des explications plus précises sur les opérations qu'ils exécutent.</span><span class="sxs-lookup"><span data-stu-id="68940-145">The script file EnlistOrch.vbs and the Visual C# source file EnlistOrc.cs contain detailed comments with further explanation about the operations that they perform.</span></span> <span data-ttu-id="68940-146">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="68940-146">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68940-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68940-147">See Also</span></span>  
 [<span data-ttu-id="68940-148">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="68940-148">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)
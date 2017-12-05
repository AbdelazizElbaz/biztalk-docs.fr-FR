---
title: OrchestrationBinding (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea14c0db-ea83-4bf9-b417-f877b3cb1bf9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b361968ddb28d629244515281cc02147af533cd0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="orchestrationbinding-biztalk-server-sample"></a><span data-ttu-id="ce865-102">OrchestrationBinding (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ce865-102">OrchestrationBinding (BizTalk Server Sample)</span></span>
<span data-ttu-id="ce865-103">L'exemple de liaison d'orchestration illustre l'utilisation des objets d'administration de [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) pour configurer et gérer les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="ce865-103">The Orchestration Binding sample demonstrates using the [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) administrative objects to configure and manage orchestrations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ce865-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ce865-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="ce865-105">Cet exemple requiert que l’exemple HelloWorld soit déployé en exécutant le fichier setup.bat situé dans le \< *exemples de chemin*\>\Orchestrations\HelloWorld active.</span><span class="sxs-lookup"><span data-stu-id="ce865-105">This sample requires that the HelloWorld sample be deployed by running setup.bat located in the \<*Samples Path*\>\Orchestrations\HelloWorld directory.</span></span>  
  
-   <span data-ttu-id="ce865-106">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ce865-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="ce865-107">L'exemple de script Windows PowerShell requiert que la stratégie d'exécution de Windows PowerShell autorise l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="ce865-107">The Windows PowerShell script example requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="ce865-108">Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="ce865-108">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ce865-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce865-109">What This Sample Does</span></span>  
 <span data-ttu-id="ce865-110">Cet exemple présente l'utilisation des objets d'administration dans l'espace de noms **Microsoft.BizTalk.ExplorerOM** en vue de gérer les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="ce865-110">This sample demonstrates using the administrative objects in the **Microsoft.BizTalk.ExplorerOM** namespace to manage orchestrations.</span></span> <span data-ttu-id="ce865-111">L'exemple illustre les opérations suivantes utilisant les objets **ExplorerOM** :</span><span class="sxs-lookup"><span data-stu-id="ce865-111">The sample demonstrates the following operations using the **ExplorerOM** objects:</span></span>  
  
-   <span data-ttu-id="ce865-112">connexion à la base de données de gestion BizTalk à l'aide de la classe[Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.btscatalogexplorer.aspx) ;</span><span class="sxs-lookup"><span data-stu-id="ce865-112">Connecting to the BizTalk Management database by using the[Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.btscatalogexplorer.aspx) class.</span></span>  
  
-   <span data-ttu-id="ce865-113">arrêt et démarrage des orchestrations en changeant la propriété **État** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) ;</span><span class="sxs-lookup"><span data-stu-id="ce865-113">Stopping and starting orchestrations by changing the **Status** property of the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
-   <span data-ttu-id="ce865-114">inscription et désinscription des orchestrations en changeant la propriété **État** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) ;</span><span class="sxs-lookup"><span data-stu-id="ce865-114">Enlisting and unenlisting orchestrations by changing the **Status** property of the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
-   <span data-ttu-id="ce865-115">liaison et annulation de liaison des orchestrations à l'aide de la collection **Ports** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) .</span><span class="sxs-lookup"><span data-stu-id="ce865-115">Binding and unbinding orchestrations by using the **Ports** collection on the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ce865-116">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce865-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="ce865-117">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="ce865-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="ce865-118">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\OrchestrationBinding</span><span class="sxs-lookup"><span data-stu-id="ce865-118">\<*Samples Path*\>\Admin\ExplorerOM\OrchestrationBinding</span></span>  
  
 <span data-ttu-id="ce865-119">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ce865-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ce865-120">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="ce865-120">File(s)</span></span>|<span data-ttu-id="ce865-121">Description</span><span class="sxs-lookup"><span data-stu-id="ce865-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce865-122">OrchestrationBinding.cs</span><span class="sxs-lookup"><span data-stu-id="ce865-122">OrchestrationBinding.cs</span></span>|<span data-ttu-id="ce865-123">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ce865-123">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="ce865-124">OrchestrationBinding.sln, OrchestrationBinding.csproj, OrchestrationBinding.suo</span><span class="sxs-lookup"><span data-stu-id="ce865-124">OrchestrationBinding.sln, OrchestrationBinding.csproj, OrchestrationBinding.suo</span></span>|<span data-ttu-id="ce865-125">Fichiers de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ce865-125">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="ce865-126">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce865-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="ce865-127">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce865-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="ce865-128">Assurez-vous d'avoir effectué les étapes de création et d'initialisation de l'exemple HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="ce865-128">Make sure you have completed the steps for building and initializing the HelloWorld sample.</span></span> <span data-ttu-id="ce865-129">Ces étapes sont décrites dans [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ce865-129">Those steps are provided in [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="ce865-130">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution OrchestrationBinding.sln.</span><span class="sxs-lookup"><span data-stu-id="ce865-130">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file OrchestrationBinding.sln.</span></span>  
  
3.  <span data-ttu-id="ce865-131">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="ce865-131">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ce865-132">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce865-132">To run this sample</span></span>  
  
1.  <span data-ttu-id="ce865-133">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ce865-133">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="ce865-134">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\OrchestrationBinding\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="ce865-134">\<*Samples Path*\>\Admin\ExplorerOM\OrchestrationBinding\bin\Debug</span></span>  
  
2.  <span data-ttu-id="ce865-135">Exécutez le fichier OrchestrationBinding.exe et suivez les instructions de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ce865-135">Run the file OrchestrationBinding.exe and follow the directions provided by the sample.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="ce865-136">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ce865-136">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="ce865-137">L'exemple de script Windows PowerShell suivant permet d'illustrer les mêmes fonctionnalités des classes **ExplorerOM** .</span><span class="sxs-lookup"><span data-stu-id="ce865-137">The following Windows PowerShell script can be used to demonstrate the same features of the **ExplorerOM** classes.</span></span>  
  
```  
  
Function RefreshPrompt($oldstatus,$newstatus)  
{  
  Write-Host Orchestration Status should now be `"$oldstatus`"  
  Write-Host Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify   
  
  if ($newstatus)  
  {  
    Write-Host Pressing `<Enter`> now will $newstatus the orchestration using ExplorerOM`.`.`.  
    Read-Host  
    Write-Host "=== Please wait, attempting to $newstatus the orchestration... ===`r`n"  
  }  
  else  
  {  
    write-host `r`n  
  }  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== This sample expects the HelloWorld sample orchestration to be using the ===#  
#=== default name "Biztalk Application 1"                                    ===#  
  
$HelloWorldApp = $Catalog.Applications["Biztalk Application 1"]  
$orch = $HelloWorldApp.orchestrations["Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule"]  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we need to re-enlist, ===#  
#=== re-bind, or restart the orchestration.                     ===#  
#==================================================================#  
  
$ErrorActionPreference="silentlycontinue"  
trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution...`r`n";$Catalog.DiscardChanges();}  
  
write-host `r`nMake sure the "HelloWorld" sample application is deployed and running.  
write-host By default it will be listed in the BizTalk Server Administration Console  
write-host with the application name: `"BizTalk.Application.1`"`r`n  
  
#==========================================================#  
#=== Change orchestration state from Started to stopped ===#  
#==========================================================#  
  
RefreshPrompt Started stop  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Enlisted"  
$Catalog.SaveChanges()  
  
#=============================================================#  
#=== Change orchestration state from stopped to unenlisted ===#  
#=============================================================#  
  
RefreshPrompt Stopped unenlist  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Unenlisted"  
$Catalog.SaveChanges()  
  
#=============================================================#  
#=== Change orchestration state from unenlisted to unbound ===#  
#=============================================================#  
  
RefreshPrompt Unenlisted unbind  
$orch.Ports["SendInvoicePort"].SendPort = $null  
$orch.Ports["ReceivePOPort"].ReceivePort = $null;  
$orch.Host = $null  
$Catalog.SaveChanges()  
  
#==================================================================#  
#=== Change orchestration state from unbound back to unenlisted ===#  
#==================================================================#  
  
RefreshPrompt Unenlisted`(Unbound`) re-bind  
$orch.Ports["SendInvoicePort"].SendPort = $Catalog.SendPorts["HelloWorldSendPort"]  
$orch.Ports["ReceivePOPort"].ReceivePort = $Catalog.ReceivePorts["HelloWorldReceivePort"]  
$orch.Host = $Catalog.Hosts["BizTalkServerApplication"]  
$Catalog.SaveChanges()  
  
#==================================================================#  
#=== Change orchestration state from unenlisted back to stopped ===#  
#==================================================================#  
  
RefreshPrompt Unenlisted enlist  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Enlisted"  
$Catalog.SaveChanges()  
  
#===============================================================#  
#=== Change orchestration state from stopped back to started ===#  
#===============================================================#  
  
RefreshPrompt Stopped restart  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Started"  
$Catalog.SaveChanges()  
  
RefreshPrompt Started  
  
```  
  
 <span data-ttu-id="ce865-138">Voici un exemple de sortie généré par l'exécution du script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce865-138">Here is an example output from running the Windows PowerShell script.</span></span>  
  
```  
PS C:\> .\OrchestrationBind.ps1  
  
Make sure the HelloWorld sample application is deployed and running.  
By default it will be listed in the BizTalk Server Administration Console  
with the application name: "BizTalk.Application.1"  
  
Orchestration Status should now be "Started"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will stop the orchestration using ExplorerOM...  
  
=== Please wait, attempting to stop the orchestration... ===  
  
Orchestration Status should now be "Stopped"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will unenlist the orchestration using ExplorerOM...  
  
=== Please wait, attempting to unenlist the orchestration... ===  
  
Orchestration Status should now be "Unenlisted"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will unbind the orchestration using ExplorerOM...  
  
=== Please wait, attempting to unbind the orchestration... ===  
  
Orchestration Status should now be "Unenlisted(Unbound)"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will re-bind the orchestration using ExplorerOM...  
  
=== Please wait, attempting to re-bind the orchestration... ===  
  
Orchestration Status should now be "Unenlisted"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will enlist the orchestration using ExplorerOM...  
  
=== Please wait, attempting to enlist the orchestration... ===  
  
Orchestration Status should now be "Stopped"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will restart the orchestration using ExplorerOM...  
  
=== Please wait, attempting to restart the orchestration... ===  
  
Orchestration Status should now be "Started"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce865-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce865-139">See Also</span></span>  
 <span data-ttu-id="ce865-140">[Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="ce865-140">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="ce865-141">HelloWorld (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ce865-141">HelloWorld (BizTalk Server Sample)</span></span>](../core/helloworld-biztalk-server-sample.md)
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
# <a name="orchestrationbinding-biztalk-server-sample"></a>OrchestrationBinding (exemple BizTalk Server)
L'exemple de liaison d'orchestration illustre l'utilisation des objets d'administration de [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) pour configurer et gérer les orchestrations.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Cet exemple requiert que l’exemple HelloWorld soit déployé en exécutant le fichier setup.bat situé dans le \< *exemples de chemin*\>\Orchestrations\HelloWorld active.  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   L'exemple de script Windows PowerShell requiert que la stratégie d'exécution de Windows PowerShell autorise l'exécution des scripts. Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple présente l'utilisation des objets d'administration dans l'espace de noms **Microsoft.BizTalk.ExplorerOM** en vue de gérer les orchestrations. L'exemple illustre les opérations suivantes utilisant les objets **ExplorerOM** :  
  
-   connexion à la base de données de gestion BizTalk à l'aide de la classe[Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.btscatalogexplorer.aspx) ;  
  
-   arrêt et démarrage des orchestrations en changeant la propriété **État** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) ;  
  
-   inscription et désinscription des orchestrations en changeant la propriété **État** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) ;  
  
-   liaison et annulation de liaison des orchestrations à l'aide de la collection **Ports** de la classe [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) .  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\OrchestrationBinding  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)|Description|  
|---------------|-----------------|  
|OrchestrationBinding.cs|Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.|  
|OrchestrationBinding.sln, OrchestrationBinding.csproj, OrchestrationBinding.suo|Fichiers de projet et de solution de l'exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Assurez-vous d'avoir effectué les étapes de création et d'initialisation de l'exemple HelloWorld. Ces étapes sont décrites dans [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md).  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution OrchestrationBinding.sln.  
  
3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de commande, puis accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\OrchestrationBinding\bin\Debug  
  
2.  Exécutez le fichier OrchestrationBinding.exe et suivez les instructions de l'exemple.  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 L'exemple de script Windows PowerShell suivant permet d'illustrer les mêmes fonctionnalités des classes **ExplorerOM** .  
  
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
  
 Voici un exemple de sortie généré par l'exécution du script Windows PowerShell.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)   
 [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md)
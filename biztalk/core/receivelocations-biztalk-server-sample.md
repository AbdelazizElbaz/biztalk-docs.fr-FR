---
title: ReceiveLocations (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d75941-3973-4166-91b0-f1192b25a804
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c907ca8db5b9655d83889b75e7439de46ebeb59c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocations-biztalk-server-sample"></a>ReceiveLocations (exemple BizTalk Server)
L’exemple ReceiveLocations illustre comment créer des emplacements de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la **ExplorerOM** objets d’administration. Pour plus d’informations sur les emplacements de réception en général, consultez [emplacements de réception](../core/receive-locations.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts. Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment utiliser le **ExplorerOM** des classes d’administration pour créer et configurer des ports de réception et emplacements de réception. Un exemple de script Windows PowerShell est également inclus dans cette rubrique. L'exemple effectue les opérations suivantes :  
  
-   création d'un port de réception nommé « My Receive Port » ;  
  
-   création d'un emplacement de réception associé au nouveau port et configuré pour utiliser le protocole de transport HTTP.  
  
-   Cet exemple contient également des procédures de suppression et d'énumération des ports et des emplacements de réception.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans l’emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\ExplorerOM\ReceiveLocations  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|ReceiveLocations.cs|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]fichier source pour les opérations présentés dans cet exemple.|  
|ReceiveLocations.sln et ReceiveLocations.csproj|Fichiers solution et projet de cet exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution ReceiveLocations.sln.  
  
2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une invite de commandes avec des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Remplacez par le \< *exemples*> \Admin\ExplorerOM\ReceiveLocations\bin\debug active.  
  
3.  Démarrez ReceiveLocations.exe.  
  
4.  Affichez les nouveaux port de réception et emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 L'exemple de script PowerShell suivant illustre les mêmes opérations que la version [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. Vérifiez que la stratégie d'exécution des scripts a été correctement configurée comme indiqué dans la section Conditions requises de cette rubrique.  
  
```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port" as an    ===#  
#=== example.                                                   ===#  
#===                                                            ===#  
#=== A new receive location will also be created and associated ===#  
#=== with the receive port.                                     ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateAndConfigureReceiveLocation()  
{  
   $myreceivePort = $catalog.AddNewReceivePort($false)  
  
   #=== Note that if you don’t set the name property for the receieve port, ===#  
   #=== it will create a new receive location and add it to the receive     ===#     
   #=== port.                                                               ===#  
  
   $myreceivePort.Name = "My Receive Port"  
  
   #=== Create a new receive location and add it to the receive port ===#  
   $myreceiveLocation = $myreceivePort.AddNewReceiveLocation()  
  
   foreach ($handler in $catalog.ReceiveHandlers)  
   {  
      if ($handler.TransportType.Name -eq "HTTP")  
      {  
         $myreceiveLocation.ReceiveHandler = $handler  
         break  
      }  
   }  
  
   #=== Associate a transport protocol and URI with the receive location. ===#   
   $myreceiveLocation.TransportType = $catalog.ProtocolTypes["HTTP"]  
   $myreceiveLocation.Address = "/home"  
  
   #=== Assign the first receive pipeline found to process the message. ===#  
   foreach ($pipeline in $catalog.Pipelines)  
   {  
      if ($pipeline.Type -eq [Microsoft.Biztalk.ExplorerOM.PipelineType] "Receive")  
      {  
         $myreceiveLocation.ReceivePipeline = $pipeline  
         break  
      }  
  
      #=== Enable the receive location. ===#  
      $myreceiveLocation.Enable = $true  
  
      #=== Optional Properties ===#  
      $myreceiveLocation.FragmentMessages = [Microsoft.BizTalk.ExplorerOM.Fragmentation] "Yes"  
      $myreceiveLocation.ServiceWindowEnabled = $false    
   }  
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes.                                      ===#  
    $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Delete the receive port named "My Receive Port"         ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteReceivePort  
{  
  $receivePort = $catalog.ReceivePorts["My Receive Port"]  
  
  if ($receivePort -ne $null)  
  {  
  
    #=== Enumerate the receive locations. ===#  
    foreach ($location in $receivePort.ReceiveLocations)  
    {  
        if (($location.Name -eq "Receive Location1") -and ($location.IsPrimary -eq $false))  
        {  
          $receivePort.RemoveReceiveLocation($location)  
        }  
    }  
  
    $catalog.RemoveReceivePort($receivePort)    
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  
  
#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports and their receive locations. ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceiveLocations  
{  
   #=== Enumerate the receive locations in each of the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  
  
      #=== Enumerate the receive locations. ===#  
      foreach ($location in $receivePort.ReceiveLocations)  
      {  
         Write-Host "`t$($location.Name)"  
      }  
   }  
  
   Write-host ""  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to delete the ===#  
#=== receive port.                                              ===#  
#==================================================================#  
  
$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
#=== Create the new receive port with its new receive location ===#  
CreateAndConfigureReceiveLocation  
Write-Host "`r`n`"My Receive Port`" created."  
  
#=== Enumerate each receive port along with its receive locations ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceiveLocations  
  
#=== Prompt before removing the new example receive port and location ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  
  
#=== Enumerate again to show the receive port and location was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceiveLocations  
  
```  
  
 Voici un exemple de sortie de l'exécution du script PowerShell montrant les port et emplacement de réception en cours de création et de suppression :  
  
```  
PS C:\> .\ReceiveLocations.ps1  
  
"My Receive Port" created.  
  
Enumerating all receive ports...  
  
BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  
  
ResendReceivePort  
        ResendReceiveLocation  
  
HelloWorldReceivePort  
        HelloWorldReceiveLocation  
  
CBRReceivePort  
        CBRReceiveLocation  
  
RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  
  
My Receive Port  
        Receive Location1  
  
Press <ENTER> to delete "My Receive Port"...  
  
Enumerating all receive ports to show "My Receive Port" was removed...  
  
BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  
  
ResendReceivePort  
        ResendReceiveLocation  
  
HelloWorldReceivePort  
        HelloWorldReceiveLocation  
  
CBRReceivePort  
        CBRReceiveLocation  
  
RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Emplacements de réception](../core/receive-locations.md)   
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
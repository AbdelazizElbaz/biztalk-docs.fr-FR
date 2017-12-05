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
ms.openlocfilehash: b5b1a6d6b651ea07430f67667a17029dfe162d4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receivelocations-biztalk-server-sample"></a><span data-ttu-id="83773-102">ReceiveLocations (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="83773-102">ReceiveLocations (BizTalk Server Sample)</span></span>
<span data-ttu-id="83773-103">L’exemple ReceiveLocations illustre comment créer des emplacements de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la **ExplorerOM** objets d’administration.</span><span class="sxs-lookup"><span data-stu-id="83773-103">The ReceiveLocations sample demonstrates how to create receive locations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by using the **ExplorerOM** administration objects.</span></span> <span data-ttu-id="83773-104">Pour plus d’informations sur les emplacements de réception en général, consultez [emplacements de réception](../core/receive-locations.md).</span><span class="sxs-lookup"><span data-stu-id="83773-104">For more information about receive locations in general, see [Receive Locations](../core/receive-locations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="83773-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="83773-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="83773-106">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="83773-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="83773-107">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="83773-107">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="83773-108">Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="83773-108">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="83773-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="83773-109">What This Sample Does</span></span>  
 <span data-ttu-id="83773-110">Cet exemple montre comment utiliser le **ExplorerOM** des classes d’administration pour créer et configurer des ports de réception et emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="83773-110">This sample demonstrates using the **ExplorerOM** administrative classes to create and configure receive ports and receive locations.</span></span> <span data-ttu-id="83773-111">Un exemple de script Windows PowerShell est également inclus dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="83773-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="83773-112">L'exemple effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="83773-112">The sample performs the following operations:</span></span>  
  
-   <span data-ttu-id="83773-113">création d'un port de réception nommé « My Receive Port » ;</span><span class="sxs-lookup"><span data-stu-id="83773-113">Create a new receive port named “My Receive Port”.</span></span>  
  
-   <span data-ttu-id="83773-114">création d'un emplacement de réception associé au nouveau port et configuré pour utiliser le protocole de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="83773-114">Create a new receive location associated with the new port and configured to use the HTTP transport protocol.</span></span>  
  
-   <span data-ttu-id="83773-115">Cet exemple contient également des procédures de suppression et d'énumération des ports et des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="83773-115">This sample also contains example procedures to delete and enumerate receive ports and locations.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="83773-116">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="83773-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="83773-117">Cet exemple se trouve dans l’emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="83773-117">This sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="83773-118">\<*Exemples de chemin d’accès* \> \Admin\ExplorerOM\ReceiveLocations</span><span class="sxs-lookup"><span data-stu-id="83773-118">\<*Samples Path*\> \Admin\ExplorerOM\ReceiveLocations</span></span>  
  
 <span data-ttu-id="83773-119">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="83773-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="83773-120">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="83773-120">File(s)</span></span>|<span data-ttu-id="83773-121"> Description</span><span class="sxs-lookup"><span data-stu-id="83773-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83773-122">ReceiveLocations.cs</span><span class="sxs-lookup"><span data-stu-id="83773-122">ReceiveLocations.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="83773-123">fichier source pour les opérations présentés dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="83773-123"> source file for the operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="83773-124">ReceiveLocations.sln et ReceiveLocations.csproj</span><span class="sxs-lookup"><span data-stu-id="83773-124">ReceiveLocations.sln and ReceiveLocations.csproj</span></span>|<span data-ttu-id="83773-125">Fichiers solution et projet de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="83773-125">Solution and project files for this sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="83773-126">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="83773-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="83773-127">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="83773-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="83773-128">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution ReceiveLocations.sln.</span><span class="sxs-lookup"><span data-stu-id="83773-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceiveLocations.sln.</span></span>  
  
2.  <span data-ttu-id="83773-129">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="83773-129">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="83773-130">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="83773-130">To run this sample</span></span>  
  
1.  <span data-ttu-id="83773-131">Ouvrez une invite de commandes avec des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83773-131">Open a command prompt with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges.</span></span>  
  
2.  <span data-ttu-id="83773-132">Remplacez par le \< *exemples*\>\Admin\ExplorerOM\ReceiveLocations\bin\debug active.</span><span class="sxs-lookup"><span data-stu-id="83773-132">Change to the \<*Samples*\>\Admin\ExplorerOM\ReceiveLocations\bin\debug directory.</span></span>  
  
3.  <span data-ttu-id="83773-133">Démarrez ReceiveLocations.exe.</span><span class="sxs-lookup"><span data-stu-id="83773-133">Run ReceiveLocations.exe.</span></span>  
  
4.  <span data-ttu-id="83773-134">Affichez les nouveaux port de réception et emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83773-134">View the new receive port and receive location with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="83773-135">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="83773-135">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="83773-136">L'exemple de script PowerShell suivant illustre les mêmes opérations que la version [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83773-136">The following PowerShell example script demonstrates the same operations as the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] version.</span></span> <span data-ttu-id="83773-137">Vérifiez que la stratégie d'exécution des scripts a été correctement configurée comme indiqué dans la section Conditions requises de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="83773-137">Make sure the script execution policy has been properly configured as mentioned in the requirements section of this topic.</span></span>  
  
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
  
 <span data-ttu-id="83773-138">Voici un exemple de sortie de l'exécution du script PowerShell montrant les port et emplacement de réception en cours de création et de suppression :</span><span class="sxs-lookup"><span data-stu-id="83773-138">Here is example output from the PowerShell script execution showing the receive port and location being created and deleted:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83773-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83773-139">See Also</span></span>  
 <span data-ttu-id="83773-140">[Emplacements de réception](../core/receive-locations.md) </span><span class="sxs-lookup"><span data-stu-id="83773-140">[Receive Locations](../core/receive-locations.md) </span></span>  
 [<span data-ttu-id="83773-141">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="83773-141">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
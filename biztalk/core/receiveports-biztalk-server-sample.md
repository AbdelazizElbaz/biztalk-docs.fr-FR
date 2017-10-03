---
title: ReceivePorts (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c403005d-5e0e-4015-b138-6318e03192af
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb14221ba11fe514ab076dd6bad8cc0aeb5b929e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receiveports-biztalk-server-sample"></a><span data-ttu-id="5b1da-102">ReceivePorts (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5b1da-102">ReceivePorts (BizTalk Server Sample)</span></span>
<span data-ttu-id="5b1da-103">L’exemple ReceivePorts illustre comment créer un nouveau port de réception à l’aide de la **ExplorerOM** classes d’administration.</span><span class="sxs-lookup"><span data-stu-id="5b1da-103">The ReceivePorts sample demonstrates how to create a new receive port by using the **ExplorerOM** administrative classes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b1da-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5b1da-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="5b1da-105">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5b1da-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="5b1da-106">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="5b1da-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="5b1da-107">Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="5b1da-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5b1da-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5b1da-108">What This Sample Does</span></span>  
 <span data-ttu-id="5b1da-109">Cet exemple montre comment utiliser le **BtsCatalogExplorer** et **ReceivePort** des classes à partir de la **Microsoft.BizTalk.ExplorerOM** espace de noms pour ajouter un nouveau port de réception pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b1da-109">This sample demonstrates using the **BtsCatalogExplorer** and **ReceivePort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to add a new receive port to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="5b1da-110">Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b1da-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="5b1da-111">Un exemple de script Windows PowerShell est également inclus dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5b1da-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="5b1da-112">Il illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b1da-112">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="5b1da-113">Connexion à la base de données de gestion BizTalk à l’aide de la **BtsCatalogExplorer** classe.</span><span class="sxs-lookup"><span data-stu-id="5b1da-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
-   <span data-ttu-id="5b1da-114">Ajout d’un nouveau port de réception à l’aide de la **AddNewReceivePort** (méthode).</span><span class="sxs-lookup"><span data-stu-id="5b1da-114">Adding a new receive port by using the **AddNewReceivePort** method.</span></span>  
  
-   <span data-ttu-id="5b1da-115">énumération des ports de réception ;</span><span class="sxs-lookup"><span data-stu-id="5b1da-115">Enumerating receive ports.</span></span>  
  
-   <span data-ttu-id="5b1da-116">suppression des ports de réception.</span><span class="sxs-lookup"><span data-stu-id="5b1da-116">Deleting receive ports.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5b1da-117">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5b1da-117">Where To Find This Sample</span></span>  
 <span data-ttu-id="5b1da-118">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="5b1da-118">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="5b1da-119">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\ReceivePorts</span><span class="sxs-lookup"><span data-stu-id="5b1da-119">\<*Samples Path*>\Admin\ExplorerOM\ReceivePorts</span></span>  
  
 <span data-ttu-id="5b1da-120">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5b1da-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5b1da-121">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5b1da-121">File(s)</span></span>|<span data-ttu-id="5b1da-122"> Description</span><span class="sxs-lookup"><span data-stu-id="5b1da-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b1da-123">ReceivePorts.cs</span><span class="sxs-lookup"><span data-stu-id="5b1da-123">ReceivePorts.cs</span></span>|<span data-ttu-id="5b1da-124">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5b1da-124">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="5b1da-125">ReceivePorts.sln et ReceivePorts.csproj</span><span class="sxs-lookup"><span data-stu-id="5b1da-125">ReceivePorts.sln and ReceivePorts.csproj</span></span>|<span data-ttu-id="5b1da-126">Fichier de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5b1da-126">Solution and project file for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="5b1da-127">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5b1da-127">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="5b1da-128">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="5b1da-128">To build this sample</span></span>  
  
1.  <span data-ttu-id="5b1da-129">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier ReceivePorts.sln de la solution.</span><span class="sxs-lookup"><span data-stu-id="5b1da-129">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceivePorts.sln.</span></span>  
  
2.  <span data-ttu-id="5b1da-130">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="5b1da-130">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="5b1da-131">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5b1da-131">To run this sample</span></span>  
  
1.  <span data-ttu-id="5b1da-132">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5b1da-132">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="5b1da-133">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\ReceivePorts\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="5b1da-133">\<*Samples Path*>\Admin\ExplorerOM\ReceivePorts\bin\Debug</span></span>  
  
2.  <span data-ttu-id="5b1da-134">Exécutez le fichier ReceivePorts.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1da-134">Run the file ReceivePorts.exe.</span></span> <span data-ttu-id="5b1da-135">Le nouveau port de réception doit avoir été créé et affiché dans l'énumération de port.</span><span class="sxs-lookup"><span data-stu-id="5b1da-135">The new receive port should be created and shown in the port enumeration.</span></span> <span data-ttu-id="5b1da-136">Le port de réception est immédiatement supprimé après l'énumération.</span><span class="sxs-lookup"><span data-stu-id="5b1da-136">After the enumeration the receive port is immediately removed.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="5b1da-137">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b1da-137">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="5b1da-138">L’exemple de script Windows PowerShell suivant peut être utilisé pour illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="5b1da-138">The following Windows PowerShell example script can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port".         ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateReceivePort()  
{   
  #=== Passing false here creates a one-way receive port opposed to a two-way ===#  
  $myreceivePort = $catalog.AddNewReceivePort($false)  
  
  $myreceivePort.Name = "My Receive Port"  
  $myreceivePort.Tracking = [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterReceivePipeline"  
  
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
    $catalog.RemoveReceivePort($receivePort)    
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  
  
#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports.                             ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceivePorts  
{  
   #=== Enumerate the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  
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
  "Exception encountered:`r`n"; $_; "`r`nDiscarding changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
#=== Create the new receive port ===#  
Write-Host "`r`nAttempting to create `"My Receive Port`"..."  
CreateReceivePort  
  
#=== Enumerate each receive port ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceivePorts  
  
#=== Prompt before removing the new example receive port ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  
  
#=== Enumerate again to show the receive port was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceivePorts  
  
```  
  
 <span data-ttu-id="5b1da-139">Voici un exemple d'exécution du script Windows PowerShell pour créer le port de réception :</span><span class="sxs-lookup"><span data-stu-id="5b1da-139">Here is an example of running the Windows PowerShell script to create the new receive port:</span></span>  
  
```  
PS C:\> .\receiveports.ps1  
  
Attempting to create "My Receive Port"...  
  
Enumerating all receive ports...  
  
BatchControlMessageRecvPort  
  
ResendReceivePort  
  
HelloWorldReceivePort  
  
CBRReceivePort  
  
RP_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
  
My Receive Port  
  
Press <ENTER> to delete "My Receive Port"...  
  
Enumerating all receive ports to show "My Receive Port" was removed...  
  
BatchControlMessageRecvPort  
  
ResendReceivePort  
  
HelloWorldReceivePort  
  
CBRReceivePort  
  
RP_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b1da-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b1da-140">See Also</span></span>  
 [<span data-ttu-id="5b1da-141">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5b1da-141">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
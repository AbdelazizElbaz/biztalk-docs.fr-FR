---
title: SendPorts (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b84f96a2-b749-4fe0-be15-e4dd13eff66f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f6bc29589f0546dda3841221fcce3ab91d704ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendports-biztalk-server-sample"></a><span data-ttu-id="8f153-102">SendPorts (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8f153-102">SendPorts (BizTalk Server Sample)</span></span>
<span data-ttu-id="8f153-103">L’exemple SendPorts illustre l’énumération et la gestion des ports d’envoi à l’aide de la **Microsoft.BizTalk.ExplorerOM** classes d’administration.</span><span class="sxs-lookup"><span data-stu-id="8f153-103">The SendPorts sample demonstrates how to enumerate and manage send ports by using the **Microsoft.BizTalk.ExplorerOM** administration classes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f153-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8f153-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="8f153-105">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8f153-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="8f153-106">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="8f153-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="8f153-107">Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="8f153-107">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="8f153-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8f153-108">What This Sample Does</span></span>  
 <span data-ttu-id="8f153-109">Cet exemple montre comment utiliser le **BtsCatalogExplorer** et **SendPort** classes à partir de la **Microsoft.BizTalk.ExplorerOM** espace de noms pour gérer les ports d’envoi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="8f153-109">This sample demonstrates using the **BtsCatalogExplorer** and **SendPort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="8f153-110">Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f153-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="8f153-111">Un exemple de script Windows PowerShell est également inclus dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8f153-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="8f153-112">Il illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f153-112">The sample demonstrates the following operations:</span></span>  
  
1.  <span data-ttu-id="8f153-113">Connexion à la base de données de gestion BizTalk à l’aide de la **BtsCatalogExplorer** classe.</span><span class="sxs-lookup"><span data-stu-id="8f153-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
2.  <span data-ttu-id="8f153-114">Création de deux nouveaux ports d’envoi nommé myStaticOnewaySendPort1 et myDynamicTwowaySendPort1.</span><span class="sxs-lookup"><span data-stu-id="8f153-114">Creating two new send ports named myStaticOnewaySendPort1 and myDynamicTwowaySendPort1.</span></span> <span data-ttu-id="8f153-115">myStaticOnewaySendPort1, comme son nom l’indique, est un port d’envoi unidirectionnel statique.</span><span class="sxs-lookup"><span data-stu-id="8f153-115">myStaticOnewaySendPort1, as its name implies, is a static one-way send port.</span></span>  <span data-ttu-id="8f153-116">Il est créé pour utiliser le transport HTTP avec un exemple destination URL http://sample1.</span><span class="sxs-lookup"><span data-stu-id="8f153-116">It is created to use the HTTP transport with an example destination URL http://sample1.</span></span> <span data-ttu-id="8f153-117">myDynamicTwowaySendPort1 est créé comme un port d’envoi dynamique bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="8f153-117">myDynamicTwowaySendPort1 is created as a dynamic two-way send port.</span></span>  
  
3.  <span data-ttu-id="8f153-118">énumération des ports d'envoi dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f153-118">Enumerating send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="8f153-119">Cet exemple d'énumération doit inclure les deux nouveaux ports d'envoi ;</span><span class="sxs-lookup"><span data-stu-id="8f153-119">This example enumeration should include the two new send ports.</span></span>  
  
4.  <span data-ttu-id="8f153-120">suppression des deux nouveaux ports ;</span><span class="sxs-lookup"><span data-stu-id="8f153-120">Deleting the two new send ports.</span></span>  
  
5.  <span data-ttu-id="8f153-121">configuration des nouveaux ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="8f153-121">Configuring the new send ports.</span></span> <span data-ttu-id="8f153-122">Les configurations illustrées par l'exemple sont appliquées à l'exemple de port d'envoi nommé myStaticOnewaySendPort1.</span><span class="sxs-lookup"><span data-stu-id="8f153-122">The configurations demonstrated by the sample are applied to the example send port named myStaticOnewaySendPort1.</span></span> <span data-ttu-id="8f153-123">Les configurations appliquées par l'exemple sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f153-123">The configurations applied by the sample include the following:</span></span>  
  
    -   <span data-ttu-id="8f153-124">L’activation de la **message de requête avant le traitement de port** option pour le suivi des corps de message.</span><span class="sxs-lookup"><span data-stu-id="8f153-124">Enabling the **Request message before port processing** option for tracking message bodies.</span></span>  
  
    -   <span data-ttu-id="8f153-125">L’activation de la **message de requête après le traitement de port** option pour le suivi des corps de message.</span><span class="sxs-lookup"><span data-stu-id="8f153-125">Enabling the **Request message after port processing** option for tracking message bodies.</span></span>  
  
    -   <span data-ttu-id="8f153-126">spécification d'un certificat de chiffrement utilisé par le port d'envoi sur les messages sortants ;</span><span class="sxs-lookup"><span data-stu-id="8f153-126">Specifying an encryption certificate for the send port to use on outgoing messages.</span></span>  
  
    -   <span data-ttu-id="8f153-127">spécification d'un filtre pour l'inscription par rapport à un ensemble de messages ;</span><span class="sxs-lookup"><span data-stu-id="8f153-127">Specifying a filter for enlistment against a set of messages.</span></span>  
  
    -   <span data-ttu-id="8f153-128">ajout d'un mappage pour transformer les messages ;</span><span class="sxs-lookup"><span data-stu-id="8f153-128">Adding a map to transform the messages.</span></span>  
  
6.  <span data-ttu-id="8f153-129">modification de l'état des deux nouveaux ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="8f153-129">Changing send port status on the two new send ports.</span></span>  <span data-ttu-id="8f153-130">L'exécution de l'exemple effectue les modifications d'état suivantes sur le port myStaticOnewaySendPort1 :</span><span class="sxs-lookup"><span data-stu-id="8f153-130">The execution of the sample will make the following status changes on the myStaticOnewaySendPort1:</span></span>  
  
    -   <span data-ttu-id="8f153-131">définition de l'état sur Démarré ;</span><span class="sxs-lookup"><span data-stu-id="8f153-131">Change the status to started.</span></span>  
  
    -   <span data-ttu-id="8f153-132">définition de l'état sur Arrêté ;</span><span class="sxs-lookup"><span data-stu-id="8f153-132">Change the status to stopped.</span></span>  
  
    -   <span data-ttu-id="8f153-133">définition de l'état sur Lié.</span><span class="sxs-lookup"><span data-stu-id="8f153-133">Change the status to bound.</span></span> <span data-ttu-id="8f153-134">L'état Lié est équivalent à l'état Désinscrit.</span><span class="sxs-lookup"><span data-stu-id="8f153-134">The bound status is the same as unenlisted.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="8f153-135">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="8f153-135">Where To Find This Sample</span></span>  
 <span data-ttu-id="8f153-136">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="8f153-136">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="8f153-137">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\SendPorts</span><span class="sxs-lookup"><span data-stu-id="8f153-137">\<*Samples Path*>\Admin\ExplorerOM\SendPorts</span></span>  
  
 <span data-ttu-id="8f153-138">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="8f153-138">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="8f153-139">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="8f153-139">File(s)</span></span>|<span data-ttu-id="8f153-140"> Description</span><span class="sxs-lookup"><span data-stu-id="8f153-140">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f153-141">SendPorts.cs</span><span class="sxs-lookup"><span data-stu-id="8f153-141">SendPorts.cs</span></span>|<span data-ttu-id="8f153-142">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8f153-142">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="8f153-143">SendPorts.sln, SendPorts.csproj, SendPorts.suo</span><span class="sxs-lookup"><span data-stu-id="8f153-143">SendPorts.sln, SendPorts.csproj, SendPorts.suo</span></span>|<span data-ttu-id="8f153-144">Fichiers de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="8f153-144">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="8f153-145">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8f153-145">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="8f153-146">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="8f153-146">To build this sample</span></span>  
  
1.  <span data-ttu-id="8f153-147">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution SendPorts.sln.</span><span class="sxs-lookup"><span data-stu-id="8f153-147">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendPorts.sln.</span></span>  
  
2.  <span data-ttu-id="8f153-148">Dans le menu principal, cliquez sur **générer**, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="8f153-148">On the main menu, click **Build**, and then click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="8f153-149">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8f153-149">To run this sample</span></span>  
  
1.  <span data-ttu-id="8f153-150">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="8f153-150">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="8f153-151">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\SendPorts\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="8f153-151">\<*Samples Path*>\Admin\ExplorerOM\SendPorts\bin\Debug</span></span>  
  
2.  <span data-ttu-id="8f153-152">Exécutez le fichier SendPorts.exe.</span><span class="sxs-lookup"><span data-stu-id="8f153-152">Run the file SendPorts.exe.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="8f153-153">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f153-153">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="8f153-154">Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="8f153-154">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
Function CreateSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #=== create a new static one-way send port using HTTP transport ===#  
  
    $myStaticOnewaySendPort = $Catalog.AddNewSendPort($false,$false)  
    $myStaticOnewaySendPort.Name = "myStaticOnewaySendPort1"  
    $myStaticOnewaySendPort.PrimaryTransport.TransportType = $catalog.ProtocolTypes["HTTP"]  
    $myStaticOnewaySendPort.PrimaryTransport.Address = "http://sample1"  
    $myStaticOnewaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== create a new dynamic two-way send port ===#  
  
    $myDynamicTwowaySendPort = $catalog.AddNewSendPort($true,$true)  
    $myDynamicTwowaySendPort.Name = "myDynamicTwowaySendPort1";  
    $myDynamicTwowaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"];  
    $myDynamicTwowaySendPort.ReceivePipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLReceive"];  
  
    #=== Persist new ports to BizTalk configuration database ===#  
  
    Write-Host Adding $myStaticOnewaySendPort.Name...  
    Write-Host Adding $myDynamicTwowaySendPort.Name...  
    $catalog.SaveChanges();  
    Write-Host "`r`nCreateSendPorts() completed."  
}  
  
Function DeleteSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #=== Delete this sample's new send ports by name ===#  
  
    $Catalog.RemoveSendPort($Catalog.SendPorts["myStaticOnewaySendPort1"])  
    $Catalog.RemoveSendPort($Catalog.SendPorts["myDynamicTwowaySendPort1"])  
  
    #=== Persist changes to BizTalk configuration database ===#  
  
    $catalog.SaveChanges();  
    Write-Host "DeleteSendPorts() completed."  
}  
  
Function EnumerateSendPorts($Catalog)  
{  
    #=== Display all send ports and their status info ===#  
  
    $catalog.SendPorts | format-table -Property Name, Status -autosize  
  
    Write-Host "EnumerateSendPorts`(`) completed."  
}  
  
Function ConfigureSendPort($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  
  
    #=== specify tracking settings for tracking ===#  
  
    Write-Host $sendport.Name: Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
    $sendport.Tracking = ([Microsoft.BizTalk.ExplorerOM.TrackingTypes] "BeforeSendPipeline" -bor   
                         [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterSendPipeline")  
  
    #=== specify an encryption certificate for outgoing messages ===#  
  
    Write-Host $sendport.Name: Adding a encryption certificate  
    foreach ($certificate in $catalog.Certificates)  
    {  
        if ($certificate.UsageType -eq [Microsoft.BizTalk.ExplorerOM.CertUsageType] "Encryption")  
        {  
            $sendport.EncryptionCert = $certificate  
        }  
    }  
  
    #=== specify filters for content-based routing ===#  
    Write-Host $sendport.Name: Adding a filter  
    $sendport.Filter = "<Filter><Group>" +  
                       "<Statement Property='SMTP.Subject' Operator='0' Value='Purchase Order'/>" +  
                       "<Statement Property='SMTP.From' Operator='0' Value='Customer'/>" +  
                       "</Group></Filter>"  
  
    #=== specify transform maps for document normalization ===#  
  
    foreach ($transform in $catalog.Transforms)  
    {  
        if (($transform.SourceSchema.FullName -ieq "myPO") -and (transform.TargetSchema.FullName -ieq "partnerPO"))  
        {  
            Write-Host $sendport.Name: Adding a transform  
            $sendport.OutboundTransforms.Add($transform)  
        }  
    }  
  
    #=== Persist all changes to BizTalk configuration database ===#  
  
    Write-Host $sendport.Name: Saving changes  
    $catalog.SaveChanges();  
    Write-Host "`r`nConfigureSendPort() completed."  
}  
  
Function ChangeSendPortStatus($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  
  
    #=== start the send port to begin processing messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Started"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
  
    #=== stop the send port to stop processing and suspend messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Stopped"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
  
    #=== unenlist the send port to stop processing and discard messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Bound"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)`(Unenlisted`)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
}  
  
#=== Main Script Body ===#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== Exercise the CreateSendPorts function to create the two new ports ===#  
  
Write-Host "`r`n========================="  
Write-Host "=== CreateSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
CreateSendPorts $Catalog  
  
#=== Enumerate all send ports to view the two new ports ===#  
  
Write-Host "`r`n============================"  
Write-Host "=== EnumerateSendPorts`(`) ==="  
Write-Host "============================`r`n"  
EnumerateSendPorts $Catalog  
  
#=== Add some configuration to the static send port ===#  
  
Write-Host "`r`n==========================="  
Write-Host "=== ConfigureSendPort`(`) ==="  
Write-Host "===========================`r`n"  
ConfigureSendPort $Catalog  
  
#=== Cycle through some status changes on the static send port ===#  
  
Write-Host "`r`n=============================="  
Write-Host "=== ChangeSendPortStatus`(`) ==="  
Write-Host "==============================`r`n"  
ChangeSendPortStatus $Catalog  
  
#=== Delete the two new ports ===#  
  
Write-Host "`r`n========================="  
Write-Host "=== DeleteSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
DeleteSendPorts $Catalog  
  
Write-Host  
```  
  
 <span data-ttu-id="8f153-155">Voici la sortie attendue de l'exécution de l'exemple de script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f153-155">Here is example expected output from running the Windows PowerShell script sample.</span></span>  
  
```  
PS C:\> & 'C:\SendPorts.ps1'  
  
=========================  
=== CreateSendPorts() ===  
=========================  
  
Adding myStaticOnewaySendPort1 ...  
Adding myDynamicTwowaySendPort1 ...  
  
CreateSendPorts() completed.  
  
============================  
=== EnumerateSendPorts() ===  
============================  
  
Name                      Status  
----                      ------  
ResendPort               Started  
HelloWorldSendPort       Started  
ToCustomerSendPort       Started  
CBRUSSendPort            Started  
CBRCANSendPort           Started  
SendportCANOrders          Bound  
myStaticOnewaySendPort1    Bound  
myDynamicTwowaySendPort1   Bound  
  
EnumerateSendPorts() completed.  
  
===========================  
=== ConfigureSendPort() ===  
===========================  
  
myStaticOnewaySendPort1 : Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
myStaticOnewaySendPort1 : Adding a encryption certificate  
myStaticOnewaySendPort1 : Adding a filter  
myStaticOnewaySendPort1 : Saving changes  
  
ConfigureSendPort() completed.  
  
==============================  
=== ChangeSendPortStatus() ===  
==============================  
  
Changing myStaticOnewaySendPort1 status to Started ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Stopped ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Bound (Unenlisted)...  
Complete.  
  
=========================  
=== DeleteSendPorts() ===  
=========================  
  
DeleteSendPorts() completed.  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f153-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f153-156">See Also</span></span>  
 [<span data-ttu-id="8f153-157">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8f153-157">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
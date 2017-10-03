---
title: CBR (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add16683-4090-4854-8d6e-923b58937e9d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8694e0525eae82c6df4e6187d6182fbfae3f43e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cbr-biztalk-server-sample"></a><span data-ttu-id="ae1d4-102">CBR (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ae1d4-102">CBR (BizTalk Server Sample)</span></span>
<span data-ttu-id="ae1d4-103">L’exemple de routage montre comment utiliser le **ExplorerOM** des objets d’administration pour ajouter et configurer de nouveaux ports d’envoi pour le routage basé sur le contenu des messages BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-103">The CBR sample demonstrates using the **ExplorerOM** administrative objects to add and configure new send ports for content-based routing of BizTalk messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ae1d4-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ae1d4-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="ae1d4-105">Cet exemple requiert que l’exemple CBRSample être déployé en exécutant le fichier setup.bat situé dans le \< *exemples de chemin*> \Messaging\CBRSample active.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-105">This sample requires that the CBRSample be deployed by running setup.bat located in the \<*Samples Path*>\Messaging\CBRSample directory.</span></span>  
  
-   <span data-ttu-id="ae1d4-106">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="ae1d4-107">L'exemple de script Windows PowerShell requiert que la stratégie d'exécution de Windows PowerShell autorise l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-107">The Windows PowerShell script example requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="ae1d4-108">Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="ae1d4-108">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ae1d4-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae1d4-109">What This Sample Does</span></span>  
 <span data-ttu-id="ae1d4-110">Cet exemple illustre l’utilisation des objets d’administration dans le **Microsoft.BizTalk.ExplorerOM** espace de noms pour ajouter deux nouveaux ports à l’exemple CBRApplication.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-110">This sample demonstrates using the administrative objects in the **Microsoft.BizTalk.ExplorerOM** namespace to add two new ports to the CBRApplication sample.</span></span> <span data-ttu-id="ae1d4-111">Ces nouveaux ports sont des exemples de ports pour CBRApplication.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-111">These new ports are example ports for CBRApplication.</span></span> <span data-ttu-id="ae1d4-112">Les ports sont configurés pour router les messages vers une adresse de service Web HTTP hypothétique à l'aide de l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-112">The ports are configured to route messages to a hypothetical HTTP Web service address by using the HTTP adapter.</span></span> <span data-ttu-id="ae1d4-113">L'exemple illustre les opérations suivantes utilisant les objets **ExplorerOM** :</span><span class="sxs-lookup"><span data-stu-id="ae1d4-113">The sample demonstrates the following operations using the **ExplorerOM** objects:</span></span>  
  
-   <span data-ttu-id="ae1d4-114">À l’aide de la **AddNewSendPort** méthode de la **Application** classe pour ajouter un port d’envoi nommé SendportUSOrders à CBRApplication.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-114">Using the **AddNewSendPort** method of the **Application** class to add a new send port called SendportUSOrders to CBRApplication.</span></span> <span data-ttu-id="ae1d4-115">Le port est configuré pour utiliser l'adaptateur HTTP pour le transport avec une adresse Web hypothétique.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-115">The port is configured to use the HTTP adapter for transport with a hypothetical Web address.</span></span>  
  
-   <span data-ttu-id="ae1d4-116">Ajout d’un filtre à SendportUSOrders, qui s’abonne aux messages dans CBRApplication avec la version américaine Valeur de Code de pays de 100.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-116">Adding a filter to SendportUSOrders that subscribes to messages in CBRApplication with the U.S. Country Code value of 100.</span></span>  
  
-   <span data-ttu-id="ae1d4-117">Ajout du mappage CBRApplication pour la transformation de messages U.S. aux mappages sortants pour SendportUSOrders.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-117">Adding the CBRApplication map for transforming U.S.-based messages to the outbound maps for SendportUSOrders.</span></span>  
  
-   <span data-ttu-id="ae1d4-118">Ajout d'un nouveau port nommé SendportCANOrders à CBRApplication et configuration de ce port pour utiliser l'adaptateur HTTP pour le transport avec une adresse Web hypothétique.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-118">Adding a new send port called SendportCANOrders to CBRApplication and configuring it to use the HTTP adapter for transport with a hypothetical Web address.</span></span>  
  
-   <span data-ttu-id="ae1d4-119">Ajout d'un filtre à SendportCANOrders, qui s'abonne aux messages dans CBRApplication avec la valeur de code de pays Canada 200.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-119">Adding a filter to SendportCANOrders that subscribes to messages in CBRApplication with the Canada Country Code value of 200.</span></span>  
  
-   <span data-ttu-id="ae1d4-120">Ajout du mappage CBRApplication pour la transformation de messages canadiens aux mappages sortants pour SendportCANOrders.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-120">Adding the CBRApplication map for transforming Canadian-based messages to the outbound maps for SendportCANOrders.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ae1d4-121">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae1d4-121">Where To Find This Sample</span></span>  
 <span data-ttu-id="ae1d4-122">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="ae1d4-122">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="ae1d4-123">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\CBR</span><span class="sxs-lookup"><span data-stu-id="ae1d4-123">\<*Samples Path*>\Admin\ExplorerOM\CBR</span></span>  
  
 <span data-ttu-id="ae1d4-124">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-124">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ae1d4-125">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="ae1d4-125">File(s)</span></span>|<span data-ttu-id="ae1d4-126"> Description</span><span class="sxs-lookup"><span data-stu-id="ae1d4-126">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae1d4-127">ContentBasedRouting.cs</span><span class="sxs-lookup"><span data-stu-id="ae1d4-127">ContentBasedRouting.cs</span></span>|<span data-ttu-id="ae1d4-128">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-128">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="ae1d4-129">CBR.sln, CBR.csproj, CBR.suo</span><span class="sxs-lookup"><span data-stu-id="ae1d4-129">CBR.sln, CBR.csproj, CBR.suo</span></span>|<span data-ttu-id="ae1d4-130">Fichiers de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-130">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="ae1d4-131">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae1d4-131">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="ae1d4-132">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae1d4-132">To build this sample</span></span>  
  
1.  <span data-ttu-id="ae1d4-133">Assurez-vous de que vous avez effectué les étapes de création, de déploiement et de configuration de CBRSample.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-133">Make sure you have completed the steps for building, deploying, and configuring the CBRSample.</span></span> <span data-ttu-id="ae1d4-134">Ces étapes sont décrites dans [CBRSample (exemple BizTalk Server)](../core/cbrsample-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ae1d4-134">Those steps are provided in [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="ae1d4-135">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution CBR.sln.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-135">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file CBR.sln.</span></span>  
  
3.  <span data-ttu-id="ae1d4-136">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-136">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ae1d4-137">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae1d4-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="ae1d4-138">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console et accédez à la **CBRApplication** nœud.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-138">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and navigate to the **CBRApplication** node.</span></span>  
  
2.  <span data-ttu-id="ae1d4-139">Développez le **CBRApplication** nœud pour vérifier que le **Ports d’envoi** nœud possède actuellement que les deux ports CBRUSSendPort et CBRCANSendPort.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-139">Expand the **CBRApplication** node to verify that the **Send Ports** node currently has only two ports listed as CBRUSSendPort and CBRCANSendPort.</span></span>  
  
3.  <span data-ttu-id="ae1d4-140">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ae1d4-140">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="ae1d4-141">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\CBR\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="ae1d4-141">\<*Samples Path*>\Admin\ExplorerOM\CBR\bin\Debug</span></span>  
  
4.  <span data-ttu-id="ae1d4-142">Exécutez le fichier CBR.exe.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-142">Run the file CBR.exe.</span></span>  
  
5.  <span data-ttu-id="ae1d4-143">Appuyez sur F5 dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour actualiser l’affichage sous le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-143">Press F5 in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to refresh the view under the **Send Ports** node.</span></span> <span data-ttu-id="ae1d4-144">Vous devez à présent voir les deux ports de nouveau ajoutés à CBRApplication par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-144">You should now see the two new ports added to CBRApplication by this sample.</span></span> <span data-ttu-id="ae1d4-145">Ils sont nommés SendportUSOrders et SendportCANOrders.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-145">They are called SendportUSOrders and SendportCANOrders.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="ae1d4-146">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae1d4-146">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="ae1d4-147">L'exemple de script Windows PowerShell suivant permet d'illustrer les mêmes fonctionnalités des classes **ExplorerOM** .</span><span class="sxs-lookup"><span data-stu-id="ae1d4-147">The following Windows PowerShell script can be used to demonstrate the same features of the **ExplorerOM** classes.</span></span> <span data-ttu-id="ae1d4-148">Toutefois, étant donné que la **ajouter** méthode pour le **SendPort.OutboundTranforms** collection est marquée comme Internal dans le **ExplorerOM** assembly il ne peut pas être appelée directement à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-148">However, because the **Add** method for the **SendPort.OutboundTranforms** collection is marked Internal in the **ExplorerOM** assembly it cannot be called directly from Windows PowerShell.</span></span> <span data-ttu-id="ae1d4-149">Ce script Windows PowerShell illustre l'utilisation du fournisseur BizTalk WMI à partir de Windows PowerShell pour ajouter le mappage de transformation sortant au nouveau port.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-149">This Windows PowerShell script demonstrates using the BizTalk WMI Provider from Windows PowerShell to add the outbound transform map to the new port.</span></span>  
  
```  
Function WMI_AddOutboundTransformToPort($transform,$strPortName)  
{  
    Write-Host "WMI Processing Transform...`r`nPortName `:"$strPortName  
    Write-Host "Transform `:"$transform.AssemblyQualifiedName  
  
    $WMIsendport = get-wmiobject MSBTS_SendPort -filter "Name=`"$strPortName`"" -namespace root\microsoftbiztalkserver  
    $WMIsendport.OutboundTransforms = $transform.AssemblyQualifiedName  
    [Void] $WMIsendport.Put()  
    [Void] $WMIsendport.Start()  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
$CBRApp = $Catalog.Applications["CBRApplication"]  
  
if ($CBRApp -eq $null)  
{  
    Write-Host "`r`nFailed to find `"CBRApplication`" deployed on this BizTalk server."  
    Write-Host "You must deploy the SDK\Samples\Messaging\CBRSample in order to test this script.`r`n"  
}  
else  
{  
    #=== Register a trap handler for any exceptions ===#  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #===================================#  
    #=== Create the U.S. Orders Port ===#  
    #===================================#  
  
    $USPort = $CBRApp.AddNewSendPort($false,$false)  
    $USPort.Name = "SendportUSOrders"  
    $USPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $USPort.PrimaryTransport.Address = "http://process_orders_US.asp"  
    $USPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== add the filter to subscribe to messages with U.S country code 100 ===#  
  
    $USPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='100'/>" +  
                     "</Group></Filter>"  
  
    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  
  
    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  
  
    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2USMap"] $USport.Name  
  
    #=====================================#  
    #=== Create the Canada Orders Port ===#  
    #=====================================#  
  
    $CanadaPort = $CBRApp.AddNewSendPort($false,$false)  
    $CanadaPort.Name = "SendportCANOrders"  
    $CanadaPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $CanadaPort.PrimaryTransport.Address = "http://process_orders_CAN.asp"  
    $CanadaPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== add the filter to subscribe to messages with U.S country code 100 ===#  
  
    $CanadaPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='200'/>" +  
                     "</Group></Filter>"  
  
    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  
  
    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  
  
    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2CANMap"] $CanadaPort.Name  
  
    Write-Host  
}  
```  
  
 <span data-ttu-id="ae1d4-150">Voici un exemple de résultat de l'exécution du script Windows PowerShell pour créer les deux nouveaux ports.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-150">Here is an example output from running the Windows PowerShell script to create the two new ports.</span></span> <span data-ttu-id="ae1d4-151">Les nouveaux ports peuvent également être vérifiés dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme mentionné ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ae1d4-151">The new ports can also be verified in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console as mentioned above.</span></span>  
  
```  
PS C:\> .\CBR.ps1  
  
Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportUSOrders  
Transform : CBRSample.CBRInput2USMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  
  
Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportCANOrders  
Transform : CBRSample.CBRInput2CANMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae1d4-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae1d4-152">See Also</span></span>  
 <span data-ttu-id="ae1d4-153">[Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="ae1d4-153">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="ae1d4-154">CBRSample (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ae1d4-154">CBRSample (BizTalk Server Sample)</span></span>](../core/cbrsample-biztalk-server-sample.md)
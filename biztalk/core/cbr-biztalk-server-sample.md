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
ms.openlocfilehash: 30811b4f0dba463d518bdd9cd8f6d227e0e79aac
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="cbr-biztalk-server-sample"></a>CBR (exemple BizTalk Server)
L’exemple de routage montre comment utiliser le **ExplorerOM** des objets d’administration pour ajouter et configurer de nouveaux ports d’envoi pour le routage basé sur le contenu des messages BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Cet exemple requiert que l’exemple CBRSample être déployé en exécutant le fichier setup.bat situé dans le \< *exemples de chemin*\>\Messaging\CBRSample active.  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   L'exemple de script Windows PowerShell requiert que la stratégie d'exécution de Windows PowerShell autorise l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre l’utilisation des objets d’administration dans le **Microsoft.BizTalk.ExplorerOM** espace de noms pour ajouter deux nouveaux ports à l’exemple CBRApplication. Ces nouveaux ports sont des exemples de ports pour CBRApplication. Les ports sont configurés pour router les messages vers une adresse de service Web HTTP hypothétique à l'aide de l'adaptateur HTTP. L'exemple illustre les opérations suivantes utilisant les objets **ExplorerOM** :  
  
-   À l’aide de la **AddNewSendPort** méthode de la **Application** classe pour ajouter un port d’envoi nommé SendportUSOrders à CBRApplication. Le port est configuré pour utiliser l'adaptateur HTTP pour le transport avec une adresse Web hypothétique.  
  
-   Ajout d’un filtre à SendportUSOrders, qui s’abonne aux messages dans CBRApplication avec la version américaine Valeur de Code de pays de 100.  
  
-   Ajout du mappage CBRApplication pour la transformation de messages U.S. aux mappages sortants pour SendportUSOrders.  
  
-   Ajout d'un nouveau port nommé SendportCANOrders à CBRApplication et configuration de ce port pour utiliser l'adaptateur HTTP pour le transport avec une adresse Web hypothétique.  
  
-   Ajout d'un filtre à SendportCANOrders, qui s'abonne aux messages dans CBRApplication avec la valeur de code de pays Canada 200.  
  
-   Ajout du mappage CBRApplication pour la transformation de messages canadiens aux mappages sortants pour SendportCANOrders.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\CBR  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|ContentBasedRouting.cs|Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.|  
|CBR.sln, CBR.csproj, CBR.suo|Fichiers de projet et de solution de l'exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Assurez-vous de que vous avez effectué les étapes de création, de déploiement et de configuration de CBRSample. Ces étapes sont décrites dans [CBRSample (exemple BizTalk Server)](../core/cbrsample-biztalk-server-sample.md).  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution CBR.sln.  
  
3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console et accédez à la **CBRApplication** nœud.  
  
2.  Développez le **CBRApplication** nœud pour vérifier que le **Ports d’envoi** nœud possède actuellement que les deux ports CBRUSSendPort et CBRCANSendPort.  
  
3.  Ouvrez une fenêtre de commande, puis accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\CBR\bin\Debug  
  
4.  Exécutez le fichier CBR.exe.  
  
5.  Appuyez sur F5 dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour actualiser l’affichage sous le **Ports d’envoi** nœud. Vous devez à présent voir les deux ports de nouveau ajoutés à CBRApplication par cet exemple. Ils sont nommés SendportUSOrders et SendportCANOrders.  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 L'exemple de script Windows PowerShell suivant permet d'illustrer les mêmes fonctionnalités des classes **ExplorerOM** . Toutefois, étant donné que la **ajouter** méthode pour le **SendPort.OutboundTranforms** collection est marquée comme Internal dans le **ExplorerOM** assembly il ne peut pas être appelée directement à partir de Windows PowerShell. Ce script Windows PowerShell illustre l'utilisation du fournisseur BizTalk WMI à partir de Windows PowerShell pour ajouter le mappage de transformation sortant au nouveau port.  
  
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
  
 Voici un exemple de résultat de l'exécution du script Windows PowerShell pour créer les deux nouveaux ports. Les nouveaux ports peuvent également être vérifiés dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme mentionné ci-dessus.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)   
 [CBRSample (exemple BizTalk Server)](../core/cbrsample-biztalk-server-sample.md)
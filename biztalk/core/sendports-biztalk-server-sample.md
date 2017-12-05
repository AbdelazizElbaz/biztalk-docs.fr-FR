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
ms.openlocfilehash: 0bd7c03e4cfa586a0dddd2579931bd5f30d293fa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sendports-biztalk-server-sample"></a>SendPorts (exemple BizTalk Server)
L’exemple SendPorts illustre l’énumération et la gestion des ports d’envoi à l’aide de la **Microsoft.BizTalk.ExplorerOM** classes d’administration.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment utiliser le **BtsCatalogExplorer** et **SendPort** classes à partir de la **Microsoft.BizTalk.ExplorerOM** espace de noms pour gérer les ports d’envoi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. Un exemple de script Windows PowerShell est également inclus dans cette rubrique. Il illustre les opérations suivantes :  
  
1.  Connexion à la base de données de gestion BizTalk à l’aide de la **BtsCatalogExplorer** classe.  
  
2.  Création de deux nouveaux ports d’envoi nommé myStaticOnewaySendPort1 et myDynamicTwowaySendPort1. myStaticOnewaySendPort1, comme son nom l’indique, est un port d’envoi unidirectionnel statique.  Il est créé pour utiliser le transport HTTP avec un exemple destination URL http://sample1. myDynamicTwowaySendPort1 est créé comme un port d’envoi dynamique bidirectionnel.  
  
3.  énumération des ports d'envoi dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet exemple d'énumération doit inclure les deux nouveaux ports d'envoi ;  
  
4.  suppression des deux nouveaux ports ;  
  
5.  configuration des nouveaux ports d'envoi. Les configurations illustrées par l'exemple sont appliquées à l'exemple de port d'envoi nommé myStaticOnewaySendPort1. Les configurations appliquées par l'exemple sont les suivantes :  
  
    -   L’activation de la **message de requête avant le traitement de port** option pour le suivi des corps de message.  
  
    -   L’activation de la **message de requête après le traitement de port** option pour le suivi des corps de message.  
  
    -   spécification d'un certificat de chiffrement utilisé par le port d'envoi sur les messages sortants ;  
  
    -   spécification d'un filtre pour l'inscription par rapport à un ensemble de messages ;  
  
    -   ajout d'un mappage pour transformer les messages ;  
  
6.  modification de l'état des deux nouveaux ports d'envoi.  L'exécution de l'exemple effectue les modifications d'état suivantes sur le port myStaticOnewaySendPort1 :  
  
    -   définition de l'état sur Démarré ;  
  
    -   définition de l'état sur Arrêté ;  
  
    -   définition de l'état sur Lié. L'état Lié est équivalent à l'état Désinscrit.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\SendPorts  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|SendPorts.cs|Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.|  
|SendPorts.sln, SendPorts.csproj, SendPorts.suo|Fichiers de projet et de solution de l'exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution SendPorts.sln.  
  
2.  Dans le menu principal, cliquez sur **générer**, puis cliquez sur **générer la Solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de commande, puis accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\SendPorts\bin\Debug  
  
2.  Exécutez le fichier SendPorts.exe.  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :  
  
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
  
 Voici la sortie attendue de l'exécution de l'exemple de script Windows PowerShell.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
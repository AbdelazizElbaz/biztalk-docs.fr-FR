---
title: BrowsingArtifacts (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b63c0833-3445-4361-a8eb-63837017edf8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32e29f945d9d20cd2ea998e0fa05eda6b52174ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browsingartifacts-biztalk-server-sample"></a>BrowsingArtifacts (exemple BizTalk Server)
L'exemple BrowsingArtifacts illustre l'énumération des attributs et artefacts BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   L'exemple de script Windows PowerShell requiert que la stratégie d'exécution de Windows PowerShell autorise l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment utiliser le **BtsCatalogExplorer** classe à partir de la **Microsoft.BizTalk.ExplorerOM** espace de noms pour énumérer les artefacts et leurs attributs de rapports. Les artefacts suivants sont inclus dans le rapport généré par cet exemple : Orchestrations, les Ports, les assemblys, les Parties et les transformations. L'exemple est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. Un exemple de script Windows PowerShell est également fourni dans cette rubrique.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\ExplorerOM\BrowsingArtifacts  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|BrowsingArtifacts.cs|Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.|  
|BrowsingArtifacts.sln, BrowsingArtifacts.csproj, BrowsingArtifacts.suo|Fichiers de projet et de solution de l'exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution BrowsingArtifacts.sln.  
  
2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de commande, puis accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Admin\ExplorerOM\BrowsingArtifacts\bin\Debug  
  
2.  Exécutez le fichier BrowsingArtifacts.exe.  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 Le script Windows PowerShell suivant peut être utilisé pour illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :  
  
```  
Function EnumOrchestrations($catalog)  
{  
    Write-Host `r`n======================  
    Write-Host ===  ORCHESTRATIONS  ===  
    Write-Host ======================`r`n   
  
    #=== Enumerating the assemblies and pulling orchestration information ===#  
  
    foreach($assembly in $catalog.Assemblies)  
    {  
        foreach($orch in $assembly.Orchestrations)  
        {  
            #=== We can’t report the host if it is not hosted or enlisted ===#  
            if ($orch.Status -ieq "Unenlisted")  
            {  
                Write-Host Name : $orch.Fullname`r`nHost : N/A`r`nStatus : $orch.Status  
            }  
            else  
            {  
                Write-Host Name : $orch.Fullname`r`nHost : $orch.Host.Name`r`nStatus : $orch.Status  
            }  
  
            #=== Reporting port types and operations ===#  
            foreach($port in $orch.Ports)  
            {  
                Write-Host "`tPort:"$port.PortType.FullName  
  
                foreach($portop in $port.PortType.Operations)  
                {  
                    Write-Host "`t`tOperation:"$portop.Name  
                }  
            }  
  
            #=== Reporting Used roles ===#  
            foreach($role in $orch.UsedRoles)  
            {  
                Write-Host "`tRole:"$role.Name"`("$role.ServiceLinkType"`)"  
  
                foreach($EnlistedParty in $role.EnlistedParties)  
                {  
                    Write-Host "`t`tParty:"$Enlistedparty.Party.Name  
                }  
            }  
  
            #=== Reporting implemented roles ===#  
            foreach($role in $orch.ImplementedRoles)  
            {  
                Write-Host "`tRole:"$role.Name"`("$role.ServiceLinkType"`)"  
            }  
  
            Write-Host  
        }  
    }  
}  
  
Function EnumOtherArtifacts($catalog)  
{  
    Write-Host `r`n======================  
    Write-Host "===   ASSEMBLIES   ==="  
    Write-Host ======================`r`n   
  
    foreach($assembly in $catalog.Assemblies)  
    {  
        Write-Host $assembly.Name  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===     HOSTS      ==="  
    Write-Host ======================`r`n   
  
    foreach($btshost in $catalog.Hosts)  
    {  
        Write-Host $btshost.Name"`($($btshost.Type)`)"  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===    PARTIES     ==="  
    Write-Host ======================`r`n   
  
    foreach($party in $catalog.Parties)  
    {  
        Write-Host $party.Name  
  
        foreach($sendport in $party.SendPorts)  
        {  
            Write-Host "`tSendPort:"$sendport.Name  
        }  
  
        foreach($alias in $party.Aliases)  
        {  
            Write-Host "`tAlias:"$alias.Name":"$alias.Qualifier"="$alias.Value  
        }  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===   TRANSFORMS   ==="  
    Write-Host ======================`r`n   
  
    foreach($transform in $catalog.Transforms)  
    {  
        Write-Host $transform.FullName":`r`n`t"$transform.SourceSchema.Fullname"==>"$transform.TargetSchema.Fullname`r`n  
    }  
}  
  
#=== Main Script Body ===#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== All reporting is performed in the following two functions ===#  
  
EnumOrchestrations $Catalog  
EnumOtherArtifacts $Catalog  
```  
  
 Voici un exemple d'exécution du script Windows PowerShell avec la sortie correspondante :  
  
```  
PS C:\> .\BrowsingArtifacts.ps1  
  
======================  
=== ORCHESTRATIONS ===  
======================  
  
Name : Microsoft.BizTalk.Edi.BatchSuspendOrchestration.BatchElementSuspendService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : Microsoft.BizTalk.Edi.BatchingOrchestration.BatchingService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : EAIOrchestrations.EAIProcess  
Host : N/A  
Status : Unenlisted  
        Port: EAIOrchestrations.ReceiveReqType  
                Operation: Operation_1  
        Port: EAIOrchestrations.SendDeclineType  
                Operation: Operation_1  
        Port: EAIOrchestrations.SendToERPType  
                Operation: Operation_1  
  
Name : B2BOrchestrations.B2BProcess  
Host : BizTalkServerApplication  
Status : Started  
        Port: B2BOrchestrations.ReceivePO_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.SendPOConfirmed_Type  
                Operation: Operation_1  
        Port: B2BSchemas.localhost.Process_.Process  
                Operation: ReceivePO  
        Port: B2BOrchestrations.ReceiveASN_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.ReceiveInvoice_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.PortType_PaymentVoucherArchive  
                Operation: Operation_1  
        Port: B2BSchemas.localhost1.Payment_Service_.Payment_Service  
                Operation: ProcessPayment  
        Port: B2BOrchestrations.SendPaymentAck_Type  
                Operation: Operation_1  
  
======================  
===   ASSEMBLIES   ===  
======================  
  
Microsoft.BizTalk.GlobalPropertySchemas  
Microsoft.BizTalk.DefaultPipelines  
Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties  
MQSeries  
Microsoft.BizTalk.Hws.HwsPromotedProperties  
Microsoft.BizTalk.Hws.HwsSchemas  
Microsoft.BizTalk.KwTpm.StsDefaultPipelines  
Microsoft.BizTalk.KwTpm.RoleLinkTypes  
mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
Microsoft.BizTalk.Edi.BaseArtifacts  
Microsoft.BizTalk.Edi.EdiPipelines  
Microsoft.BizTalk.Edi.BatchingOrchestration  
Microsoft.BizTalk.Edi.RoutingOrchestration  
Microsoft.BizTalk.Edi.EdiIntPipelines  
EAISchemas  
EAIOrchestrations  
B2BSchemas  
B2BOrchestrations  
WCFArtifacts  
FFDisassemblerWalkthrough  
BTSWhitespaceTest  
  
======================  
===     HOSTS      ===  
======================  
  
BizTalkServerApplication (InProcess)  
BizTalkServerIsolatedHost (Isolated)  
  
======================  
===    PARTIES     ===  
======================  
  
PartyB  
        Alias: Organization : OrganizationName = PartyB  
  
======================  
===   TRANSFORMS   ===  
======================  
  
EAISchemas.FFRequestDeniedMap :  
         EAISchemas.FlatFileSchema1 ==> EAISchemas.RequestDenied  
  
EAISchemas.RequestDeniedMap :  
         EAISchemas.Request ==> EAISchemas.RequestDenied  
  
B2BSchemas.InvoiceToPayment :  
         B2BSchemas.CommonInvoice ==> B2BSchemas.localhost1.Reference  
  
B2BSchemas.MapToCommonPO :  
         B2BSchemas.PO ==> B2BSchemas.localhost.Reference  
  
BizTalkArtifacts.ConcatMap :  
         BizTalkArtifacts.InputSchema ==> BizTalkArtifacts.OutputSchema  
  
FFDisassemblerWalkthrough.Map1 :  
         FFDisassemblerWalkthrough.Body ==> FFDisassemblerWalkthrough.Body  
  
BTSWhitespaceTest.Map1 :  
         FFDisassemblerWalkthrough.Body ==> BTSWhitespaceTest.Schema1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
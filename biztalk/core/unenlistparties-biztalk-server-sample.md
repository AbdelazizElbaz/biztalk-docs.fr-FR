---
title: UnenlistParties (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, parties
- parties, examples
- parties, unenlisting
- examples, administering
- administering, examples
ms.assetid: a751a0fc-ca94-4610-a8aa-db3a24159334
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34cbb94dff7211a157fc492c1157fa379236641e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="unenlistparties-biztalk-server-sample"></a>UnenlistParties (exemple BizTalk Server)
L'exemple UnenlistParties décrit la désinscription de tous les tiers associés à un assembly BizTalk Server déployé.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple, écrit en Visual C# à l'aide d'objets du modèle objet de l'Explorateur BizTalk, effectue les opérations suivantes :  
  
-   requête d'un assembly particulier ;  
  
-   récupération de tous les rôles associés à cet assembly ;  
  
-   désinscription de tous les tiers associés à de tels rôles ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\UnenlistParties\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs|Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui désinscrit tous les tiers pour un assembly particulier.|  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution UnenlistParties.sln.  
  
2.  Dans le **générer** menu, sélectionnez **générer la Solution**.  
  
### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\UnenlistParties\bin\Debug\  
  
2.  Exécutez le fichier UnenlistParties.exe, en passant l'un des deux arguments de ligne de commande suivants :  
  
    -   **\<** ***AssemblyName* \>** . Nom d'un assembly dont tous les tiers associés doivent être désinscrits. Si le nom de l'assembly contient des espaces, placez-le entre guillemets.  
  
    -   **/?.** Affiche l’aide.  
  
     Exemple :  
  
    ```  
    UnenlistParties "My BizTalk Assembly.dll"  
    ```  
  
     -OU-  
  
    ```  
    UnenlistParties /?  
    ```  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 Le fragment de script Windows Powershell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :  
  
```  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=====================================================#  
#=== If no assembly name is specified, just list   ===#  
#=== the assemblies, roles and partyies enlisted.  ===#  
#=====================================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`n===========================================================  
  Write-Host No assembly name provided for party unenlist operation.  
  Write-Host Listing Parties for each assembly on local BizTalk Server:  
  Write-Host ===========================================================`r`n  
  
  foreach ($assembly in $Catalog.Assemblies)  
  {  
    write-host $Assembly.Name`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
      write-host `t($role.name)  
  
      foreach($party in $role.EnlistedParties)  
      {  
        Write-Host `t`t($party.Party.Name)  
      }  
      write-host  
    }  
  }  
  
  write-host  
}  
  
#=====================================================#  
#=== If assembly name is specified, remove parties ===#  
#=== enlisted in all roles for the assembly.       ===#  
#=====================================================#  
  
else  
{  
  $Assembly = $Catalog.Assemblies[$args[0]]  
  
  if ($assembly -eq $null)  
  {  
    write-host Assembly named $args[0] not found.`r`n  
  }   
  
  else  
  {  
    write-host `r`nUnenlisting parties from all roles in ($Assembly.Name)`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
  
      $count = $role.EnlistedParties.count  
  
      for($c=0; $c -lt $count; $c++)  
      {  
        #==========================================================#  
        #=== Array index stays at zero because the collection   ===#  
        #=== changes after each item is removed.                ===#  
        #==========================================================#  
  
        $party = $role.EnlistedParties[0]  
  
        Write-Host Unenlisting ($party.Party.Name) from ($role.Name)...  
        $role.RemoveEnlistedParty($party)  
        Write-Host done.`r`n  
      }  
    }  
  
    write-Host Comitting changes...  
    $catalog.SaveChanges()  
    Write-Host done.`r`n  
  }  
}  
  
```  
  
 La sortie de script suivante a été générée à partir de tiers se désinscrivant de l'assembly Supplier qui fait partie de l'exemple PartyResolution. L’exemple PartyResolution se trouve dans le \< *exemples de chemin*\>\Admin\Orchestrations\PartyResolution active.  
  
```  
PS C:\> .\UnenlistParties.ps1 Supplier  
  
Unenlisting parties from all roles in Supplier  
  
Unenlisting ShipmentAgency1 from ShipmentRole ...  
done.  
  
Unenlisting ShipmentAgency2 from ShipmentRole ...  
done.  
  
Unenlisting BuyerAgency from Buyer ...  
done.  
  
Comitting changes...  
done.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
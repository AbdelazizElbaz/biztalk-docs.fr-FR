---
title: DeleteParty (exemple BizTalk Server) | Documents Microsoft
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
- deleting, parties
- examples, administering
- parties, deleting
- administering, examples
ms.assetid: 8161af7d-76ef-4df5-81c8-f0f5c81df9a8
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d07793400f0217ef2f3ddcc637265f186647a00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleteparty-biztalk-server-sample"></a>DeleteParty (exemple BizTalk Server)
L'exemple DeleteParty décrit la suppression d'un tiers spécifique.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
> [!NOTE]
>  Avant de pouvoir supprimer un tiers, vous devez d'abord en créer un. Pour faire cela consiste à exécuter la [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md) exemple.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple, écrit en Microsoft Visual C#, à l'aide d'objets du modèle objet de l'Explorateur BizTalk (ExplorerOM), effectue les opérations suivantes :  
  
-   requête d'un tiers spécifique ;  
  
-   suppression de ce tiers ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Cet exemple se trouve dans l’emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\ExplorerOM\DeleteParty\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, DeleteParty.csproj, DeleteParty.sln, DeleteParty.cs|Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui supprime un tiers spécifié.|  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution DeleteParty.sln.  
  
2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Admin\ExplorerOM\DeleteParty\bin\Debug\  
  
2.  Exécutez le fichier DeleteParty.exe, en passant l'un des deux arguments de ligne de commande suivants :  
  
    -   **\<**   
         ***Nom_tiers* >.** Nom du tiers à supprimer. Si le nom du tiers contient des espaces, placez-le entre guillemets.  
  
    -   **/?.** Affiche l’aide.  
  
     Exemple :  
  
    ```  
    DeleteParty "My Party #3"  
    ```  
  
     -OU-  
  
    ```  
    DeleteParty /?  
    ```  
  
## <a name="windows-powershell-script-example"></a>Exemple de Script Windows Powershell  
 Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :  
  
```  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=======================================#  
#=== If no party name is specified   ===#  
#=== just list the parties.          ===#  
#=======================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`nNo party name provided for delete operation.`r`n`r`nListing Parties on local Biztalk Server:  
  
  $Catalog.Parties | Format-List Name  
}  
  
#==========================================#  
#=== Delete the specified party by name ===#  
#==========================================#  
  
else  
{  
  $party = $Catalog.Parties[$args[0]]  
  Write-Host `r`nRemoving Party named `"($args[0])`"`r`n  
  $catalog.RemoveParty($party)  
  $catalog.SaveChanges()  
}  
```  
  
 L'exemple de script attend un nom de tiers unique pour le transmettre en tant qu'argument de ligne de commande.  Il recherche ce tiers à l'aide de son nom et tente de le supprimer.  Si aucun argument de ligne de commande ne lui est transmis, ce script répertorie tous les tiers du serveur BizTalk local. Voici un exemple de sortie du script :  
  
```  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party3  
  
Name : Party2  
  
PS C:\> .\DeletePart.ps1 Party3  
  
Removing Party named " Party3 "  
  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party2  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
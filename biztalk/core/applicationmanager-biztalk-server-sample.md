---
title: ApplicationManager (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51ebe7a8-a0ca-4d2a-bf40-ec6421ba5a95
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 374fc67f0a4b750aa1f797d57778f68347383736
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="applicationmanager-biztalk-server-sample"></a>ApplicationManager (exemple BizTalk Server)
L'exemple ApplicationManager montre comment démarrer et arrêter une application BizTalk à l'aide des objets d'administration.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.  
  
-   La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts. Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment utiliser le **BtsCatalogExplorer** et **Application** des classes à partir de la **Microsoft.BizTalk.ExplorerOM** pour démarrer et arrêter un espace de noms  Application BizTalk. Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. Un exemple de script Windows PowerShell est également inclus dans cette rubrique. Il illustre les opérations suivantes :  
  
-   Connexion à la base de données de gestion BizTalk à l’aide de la **BtsCatalogExplorer** classe.  
  
-   Recherche d’une instance d’application à partir de **BtsCatalogExplorer** basé sur le nom de l’application.  
  
-   soumission d'une commande de démarrage ou d'arrêt pour l'application.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\ApplicationManager  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Program.cs|Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.|  
|ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo|Fichiers de projet et de solution de l'exemple.|  
  
## <a name="building-and-running-this-sample"></a>Création et exécution de l'exemple  
  
#### <a name="to-build-this-sample"></a>Pour créer l'exemple  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution ApplicationManager.sln.  
  
2.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de commande, puis accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug  
  
2.  Exécutez le fichier ApplicationManager.exe en indiquant les deux arguments de ligne de commande suivants dans cet ordre :  
  
    -   **\<Démarrer &#124; arrêter\>**  premier argument est l’opération à effectuer sur l’application déployée.  
  
    -   **\<ApplicationName\>**  deuxième argument est le nom de l’application déployée.  
  
     Exemple :  
  
    ```  
    ApplicationManager.exe stop MyBizTalkApp  
    ```  
  
     L'exécution de l'exemple avec des paramètres de ligne de commande insuffisants affiche la syntaxe d'utilisation. Exemple :  
  
    ```  
    Usage:  
  
    ApplicationManager <start|stop> <Application Name>  
  
     Where:  
      <Application Name> = The name of the application that needs to be changed  
  
    Example: ApplicationManager start Application1  
    ```  
  
## <a name="windows-powershell-script-example"></a>Exemple de script Windows PowerShell  
 Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :  
  
```  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== Loop through applications in the catalog trying to find a name match ===#  
  
foreach($app in $Catalog.Applications)  
{  
    if ($($app.Name) -ieq $args[1])  
    {  
  
        #=== The first command-line argument should be "start" or "stop" ===#  
  
        if ($args[0] -ieq "start")  
        {  
            Write-Host `r`nIssuing start command to $app.Name...`r`n  
            $app.Start([Microsoft.BizTalk.ExplorerOM.ApplicationStartOption] "StartAll")  
            $Catalog.SaveChanges()  
        }  
  
        if ($args[0] -ieq "stop")  
        {  
            Write-Host `r`nIssuing stop command to $app.Name...`r`n  
            $app.Stop([Microsoft.BizTalk.ExplorerOM.ApplicationStopOption] "StopAll")  
            $Catalog.SaveChanges()  
        }  
  
    }  
}  
```  
  
 Le script attend les mêmes arguments de ligne de commande que l'exemple [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. Voici un exemple d'exécution du script Windows PowerShell pour démarrer une application BizTalk déployée :  
  
```  
PS C:\> .\ApplicationManager.ps1 start MyBizTalkApp  
  
Issuing start command to MyBizTalkApp ...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-ExplorerOM (dossier d’exemples BizTalk Server)](../core/admin-explorerom-biztalk-server-samples-folder.md)
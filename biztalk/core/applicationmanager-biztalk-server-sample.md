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
# <a name="applicationmanager-biztalk-server-sample"></a><span data-ttu-id="d47c7-102">ApplicationManager (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="d47c7-102">ApplicationManager (BizTalk Server Sample)</span></span>
<span data-ttu-id="d47c7-103">L'exemple ApplicationManager montre comment démarrer et arrêter une application BizTalk à l'aide des objets d'administration.</span><span class="sxs-lookup"><span data-stu-id="d47c7-103">The ApplicationManager sample demonstrates how to start or stop a  BizTalk application by using the administration objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d47c7-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d47c7-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="d47c7-105">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d47c7-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="d47c7-106">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="d47c7-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="d47c7-107">Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="d47c7-107">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="d47c7-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d47c7-108">What This Sample Does</span></span>  
 <span data-ttu-id="d47c7-109">Cet exemple montre comment utiliser le **BtsCatalogExplorer** et **Application** des classes à partir de la **Microsoft.BizTalk.ExplorerOM** pour démarrer et arrêter un espace de noms  Application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d47c7-109">This sample demonstrates using the **BtsCatalogExplorer** and **Application** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to start and stop a deployed  BizTalk application.</span></span> <span data-ttu-id="d47c7-110">Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d47c7-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="d47c7-111">Un exemple de script Windows PowerShell est également inclus dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d47c7-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="d47c7-112">Il illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d47c7-112">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="d47c7-113">Connexion à la base de données de gestion BizTalk à l’aide de la **BtsCatalogExplorer** classe.</span><span class="sxs-lookup"><span data-stu-id="d47c7-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
-   <span data-ttu-id="d47c7-114">Recherche d’une instance d’application à partir de **BtsCatalogExplorer** basé sur le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="d47c7-114">Finding an application instance from  **BtsCatalogExplorer** based on application name.</span></span>  
  
-   <span data-ttu-id="d47c7-115">soumission d'une commande de démarrage ou d'arrêt pour l'application.</span><span class="sxs-lookup"><span data-stu-id="d47c7-115">Submitting a start or stop command for the application.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="d47c7-116">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="d47c7-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="d47c7-117">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="d47c7-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="d47c7-118">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\ApplicationManager</span><span class="sxs-lookup"><span data-stu-id="d47c7-118">\<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager</span></span>  
  
 <span data-ttu-id="d47c7-119">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="d47c7-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="d47c7-120">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="d47c7-120">File(s)</span></span>|<span data-ttu-id="d47c7-121"> Description</span><span class="sxs-lookup"><span data-stu-id="d47c7-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d47c7-122">Program.cs</span><span class="sxs-lookup"><span data-stu-id="d47c7-122">Program.cs</span></span>|<span data-ttu-id="d47c7-123">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d47c7-123">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="d47c7-124">ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo</span><span class="sxs-lookup"><span data-stu-id="d47c7-124">ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo</span></span>|<span data-ttu-id="d47c7-125">Fichiers de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d47c7-125">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="d47c7-126">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d47c7-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="d47c7-127">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="d47c7-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="d47c7-128">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution ApplicationManager.sln.</span><span class="sxs-lookup"><span data-stu-id="d47c7-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ApplicationManager.sln.</span></span>  
  
2.  <span data-ttu-id="d47c7-129">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="d47c7-129">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="d47c7-130">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d47c7-130">To run this sample</span></span>  
  
1.  <span data-ttu-id="d47c7-131">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="d47c7-131">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="d47c7-132">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="d47c7-132">\<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug</span></span>  
  
2.  <span data-ttu-id="d47c7-133">Exécutez le fichier ApplicationManager.exe en indiquant les deux arguments de ligne de commande suivants dans cet ordre :</span><span class="sxs-lookup"><span data-stu-id="d47c7-133">Run the file ApplicationManager.exe providing the following two ordered command-line arguments:</span></span>  
  
    -   <span data-ttu-id="d47c7-134">**\<Démarrer &#124; arrêter\>**  premier argument est l’opération à effectuer sur l’application déployée.</span><span class="sxs-lookup"><span data-stu-id="d47c7-134">**\<start&#124;stop\>** First argument is the operation to be performed on the deployed application.</span></span>  
  
    -   <span data-ttu-id="d47c7-135">**\<ApplicationName\>**  deuxième argument est le nom de l’application déployée.</span><span class="sxs-lookup"><span data-stu-id="d47c7-135">**\<ApplicationName\>** Second argument is the name of the deployed application.</span></span>  
  
     <span data-ttu-id="d47c7-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d47c7-136">For example:</span></span>  
  
    ```  
    ApplicationManager.exe stop MyBizTalkApp  
    ```  
  
     <span data-ttu-id="d47c7-137">L'exécution de l'exemple avec des paramètres de ligne de commande insuffisants affiche la syntaxe d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="d47c7-137">Running the sample with insufficient command-line parameters displays the usage syntax.</span></span> <span data-ttu-id="d47c7-138">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d47c7-138">For example:</span></span>  
  
    ```  
    Usage:  
  
    ApplicationManager <start|stop> <Application Name>  
  
     Where:  
      <Application Name> = The name of the application that needs to be changed  
  
    Example: ApplicationManager start Application1  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="d47c7-139">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d47c7-139">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="d47c7-140">Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="d47c7-140">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
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
  
 <span data-ttu-id="d47c7-141">Le script attend les mêmes arguments de ligne de commande que l'exemple [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d47c7-141">The script expects the same command-line arguments as the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] sample.</span></span> <span data-ttu-id="d47c7-142">Voici un exemple d'exécution du script Windows PowerShell pour démarrer une application BizTalk déployée :</span><span class="sxs-lookup"><span data-stu-id="d47c7-142">Here is an example of running the Windows PowerShell script to start a deployed BizTalk application:</span></span>  
  
```  
PS C:\> .\ApplicationManager.ps1 start MyBizTalkApp  
  
Issuing start command to MyBizTalkApp ...  
```  
  
## <a name="see-also"></a><span data-ttu-id="d47c7-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d47c7-143">See Also</span></span>  
 [<span data-ttu-id="d47c7-144">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="d47c7-144">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
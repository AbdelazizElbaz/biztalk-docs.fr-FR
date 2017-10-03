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
# <a name="deleteparty-biztalk-server-sample"></a><span data-ttu-id="3bc50-102">DeleteParty (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="3bc50-102">DeleteParty (BizTalk Server Sample)</span></span>
<span data-ttu-id="3bc50-103">L'exemple DeleteParty décrit la suppression d'un tiers spécifique.</span><span class="sxs-lookup"><span data-stu-id="3bc50-103">The DeleteParty sample demonstrates how to delete a specified party.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3bc50-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="3bc50-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="3bc50-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="3bc50-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bc50-106">Avant de pouvoir supprimer un tiers, vous devez d'abord en créer un.</span><span class="sxs-lookup"><span data-stu-id="3bc50-106">Before you can delete a party, you must first create one.</span></span> <span data-ttu-id="3bc50-107">Pour faire cela consiste à exécuter la [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="3bc50-107">One way to do this is to run the [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md) sample.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3bc50-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3bc50-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="3bc50-109">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="3bc50-109">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="3bc50-110">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="3bc50-110">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="3bc50-111">Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="3bc50-111">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3bc50-112">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="3bc50-112">What This Sample Does</span></span>  
 <span data-ttu-id="3bc50-113">Cet exemple, écrit en Microsoft Visual C#, à l'aide d'objets du modèle objet de l'Explorateur BizTalk (ExplorerOM), effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bc50-113">This sample, written in Microsoft Visual C#, using objects from the BizTalk Explorer object model (ExplorerOM), performs the following operations:</span></span>  
  
-   <span data-ttu-id="3bc50-114">requête d'un tiers spécifique ;</span><span class="sxs-lookup"><span data-stu-id="3bc50-114">Query for a specified party.</span></span>  
  
-   <span data-ttu-id="3bc50-115">suppression de ce tiers ;</span><span class="sxs-lookup"><span data-stu-id="3bc50-115">Delete that party.</span></span>  
  
-   <span data-ttu-id="3bc50-116">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3bc50-116">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3bc50-117">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="3bc50-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="3bc50-118">Cet exemple se trouve dans l’emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="3bc50-118">This sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="3bc50-119">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\DeleteParty\\</span><span class="sxs-lookup"><span data-stu-id="3bc50-119">\<*Samples Path*>\Admin\ExplorerOM\DeleteParty\\</span></span>  
  
 <span data-ttu-id="3bc50-120">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="3bc50-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3bc50-121">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="3bc50-121">File(s)</span></span>|<span data-ttu-id="3bc50-122"> Description</span><span class="sxs-lookup"><span data-stu-id="3bc50-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bc50-123">App.ico, AssemblyInfo.cs, DeleteParty.csproj, DeleteParty.sln, DeleteParty.cs</span><span class="sxs-lookup"><span data-stu-id="3bc50-123">App.ico, AssemblyInfo.cs, DeleteParty.csproj, DeleteParty.sln, DeleteParty.cs</span></span>|<span data-ttu-id="3bc50-124">Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui supprime un tiers spécifié.</span><span class="sxs-lookup"><span data-stu-id="3bc50-124">Project, solution, and source files for building a Visual C# command-line application that removes a specified party.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="3bc50-125">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="3bc50-125">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="3bc50-126">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution DeleteParty.sln.</span><span class="sxs-lookup"><span data-stu-id="3bc50-126">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file DeleteParty.sln.</span></span>  
  
2.  <span data-ttu-id="3bc50-127">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="3bc50-127">On the **Build** menu, click **Build Solution**.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="3bc50-128">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3bc50-128">To run this sample</span></span>  
  
1.  <span data-ttu-id="3bc50-129">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="3bc50-129">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="3bc50-130">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\DeleteParty\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="3bc50-130">\<*Samples Path*>\Admin\ExplorerOM\DeleteParty\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="3bc50-131">Exécutez le fichier DeleteParty.exe, en passant l'un des deux arguments de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="3bc50-131">Run the file DeleteParty.exe, passing one of the two following command-line arguments:</span></span>  
  
    -   **\<**   
         <span data-ttu-id="3bc50-132">***Nom_tiers* >.**</span><span class="sxs-lookup"><span data-stu-id="3bc50-132">***PartyName* >.**</span></span> <span data-ttu-id="3bc50-133">Nom du tiers à supprimer.</span><span class="sxs-lookup"><span data-stu-id="3bc50-133">The name of a party to be deleted.</span></span> <span data-ttu-id="3bc50-134">Si le nom du tiers contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="3bc50-134">If the party name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="3bc50-135">**/?.**</span><span class="sxs-lookup"><span data-stu-id="3bc50-135">**/?.**</span></span> <span data-ttu-id="3bc50-136">Affiche l’aide.</span><span class="sxs-lookup"><span data-stu-id="3bc50-136">Displays help.</span></span>  
  
     <span data-ttu-id="3bc50-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3bc50-137">For example:</span></span>  
  
    ```  
    DeleteParty "My Party #3"  
    ```  
  
     <span data-ttu-id="3bc50-138">-OU-</span><span class="sxs-lookup"><span data-stu-id="3bc50-138">-OR-</span></span>  
  
    ```  
    DeleteParty /?  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="3bc50-139">Exemple de Script Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="3bc50-139">Windows Powershell Script example</span></span>  
 <span data-ttu-id="3bc50-140">Le fragment de script Windows PowerShell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="3bc50-140">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
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
  
 <span data-ttu-id="3bc50-141">L'exemple de script attend un nom de tiers unique pour le transmettre en tant qu'argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3bc50-141">The script example expects a single party name to be passed as a command line argument.</span></span>  <span data-ttu-id="3bc50-142">Il recherche ce tiers à l'aide de son nom et tente de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="3bc50-142">It looks for that party by name and attempts to delete it.</span></span>  <span data-ttu-id="3bc50-143">Si aucun argument de ligne de commande ne lui est transmis, ce script répertorie tous les tiers du serveur BizTalk local.</span><span class="sxs-lookup"><span data-stu-id="3bc50-143">The script will list all parties on the local Biztalk server if no commandline argument is passed to it.</span></span> <span data-ttu-id="3bc50-144">Voici un exemple de sortie du script :</span><span class="sxs-lookup"><span data-stu-id="3bc50-144">Here is example output from the script:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bc50-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bc50-145">See Also</span></span>  
 [<span data-ttu-id="3bc50-146">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="3bc50-146">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
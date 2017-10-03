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
ms.openlocfilehash: 2d328a1a95b7340520352b32b6d72e1579b9594a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unenlistparties-biztalk-server-sample"></a><span data-ttu-id="c77c7-102">UnenlistParties (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="c77c7-102">UnenlistParties (BizTalk Server Sample)</span></span>
<span data-ttu-id="c77c7-103">L'exemple UnenlistParties décrit la désinscription de tous les tiers associés à un assembly BizTalk Server déployé.</span><span class="sxs-lookup"><span data-stu-id="c77c7-103">The UnenlistParties sample demonstrates how to unenlist all of the parties associated with a deployed BizTalk Server assembly.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c77c7-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="c77c7-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="c77c7-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="c77c7-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c77c7-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c77c7-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="c77c7-107">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c77c7-107">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="c77c7-108">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="c77c7-108">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="c77c7-109">Pour plus d’informations, consultez : [examen de la stratégie d’exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="c77c7-109">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="c77c7-110">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="c77c7-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="c77c7-111">Cet exemple, écrit en Visual C# à l'aide d'objets du modèle objet de l'Explorateur BizTalk, effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c77c7-111">This sample, written in Visual C# using objects from the BizTalk Explorer object model, performs the following operations:</span></span>  
  
-   <span data-ttu-id="c77c7-112">requête d'un assembly particulier ;</span><span class="sxs-lookup"><span data-stu-id="c77c7-112">Query for a particular assembly.</span></span>  
  
-   <span data-ttu-id="c77c7-113">récupération de tous les rôles associés à cet assembly ;</span><span class="sxs-lookup"><span data-stu-id="c77c7-113">Retrieve all of the roles associated with that assembly.</span></span>  
  
-   <span data-ttu-id="c77c7-114">désinscription de tous les tiers associés à de tels rôles ;</span><span class="sxs-lookup"><span data-stu-id="c77c7-114">Unenlist all of the parties associated with each such role.</span></span>  
  
-   <span data-ttu-id="c77c7-115">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c77c7-115">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="c77c7-116">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="c77c7-116">Where to Find This Sample</span></span>  
 <span data-ttu-id="c77c7-117">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="c77c7-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="c77c7-118">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\UnenlistParties\\</span><span class="sxs-lookup"><span data-stu-id="c77c7-118">\<*Samples Path*>\Admin\ExplorerOM\UnenlistParties\\</span></span>  
  
 <span data-ttu-id="c77c7-119">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="c77c7-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="c77c7-120">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="c77c7-120">File(s)</span></span>|<span data-ttu-id="c77c7-121"> Description</span><span class="sxs-lookup"><span data-stu-id="c77c7-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c77c7-122">App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs</span><span class="sxs-lookup"><span data-stu-id="c77c7-122">App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs</span></span>|<span data-ttu-id="c77c7-123">Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui désinscrit tous les tiers pour un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="c77c7-123">Project, solution, and source files for building a Visual C# command-line application that unenlists all of the parties for a particular assembly.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="c77c7-124">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="c77c7-124">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="c77c7-125">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution UnenlistParties.sln.</span><span class="sxs-lookup"><span data-stu-id="c77c7-125">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file UnenlistParties.sln.</span></span>  
  
2.  <span data-ttu-id="c77c7-126">Dans le **générer** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="c77c7-126">In the **Build** menu, select **Build Solution**.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="c77c7-127">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c77c7-127">To run this sample</span></span>  
  
1.  <span data-ttu-id="c77c7-128">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="c77c7-128">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="c77c7-129">\<*Exemples de chemin d’accès*> \Admin\ExplorerOM\UnenlistParties\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="c77c7-129">\<*Samples Path*>\Admin\ExplorerOM\UnenlistParties\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="c77c7-130">Exécutez le fichier UnenlistParties.exe, en passant l'un des deux arguments de ligne de commande suivants :</span><span class="sxs-lookup"><span data-stu-id="c77c7-130">Run the file UnenlistParties.exe, passing one of the two following command-line arguments:</span></span>  
  
    -   **\<**   
         <span data-ttu-id="c77c7-131">***AssemblyName* >**.</span><span class="sxs-lookup"><span data-stu-id="c77c7-131">***AssemblyName* >**.</span></span> <span data-ttu-id="c77c7-132">Nom d'un assembly dont tous les tiers associés doivent être désinscrits.</span><span class="sxs-lookup"><span data-stu-id="c77c7-132">The name of an assembly from which all associated parties are to be unenlisted.</span></span> <span data-ttu-id="c77c7-133">Si le nom de l'assembly contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="c77c7-133">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="c77c7-134">**/?.**</span><span class="sxs-lookup"><span data-stu-id="c77c7-134">**/?.**</span></span> <span data-ttu-id="c77c7-135">Affiche l’aide.</span><span class="sxs-lookup"><span data-stu-id="c77c7-135">Displays help.</span></span>  
  
     <span data-ttu-id="c77c7-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c77c7-136">For example:</span></span>  
  
    ```  
    UnenlistParties "My BizTalk Assembly.dll"  
    ```  
  
     <span data-ttu-id="c77c7-137">-OU-</span><span class="sxs-lookup"><span data-stu-id="c77c7-137">-OR-</span></span>  
  
    ```  
    UnenlistParties /?  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="c77c7-138">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c77c7-138">Windows Powershell Script Example</span></span>  
 <span data-ttu-id="c77c7-139">Le fragment de script Windows Powershell suivant permet d’illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="c77c7-139">The following Windows Powershell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
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
  
 <span data-ttu-id="c77c7-140">La sortie de script suivante a été générée à partir de tiers se désinscrivant de l'assembly Supplier qui fait partie de l'exemple PartyResolution.</span><span class="sxs-lookup"><span data-stu-id="c77c7-140">The following script output was generated from unenlisting parties from the Supplier assembly which is part of the PartyResolution sample.</span></span> <span data-ttu-id="c77c7-141">L’exemple PartyResolution se trouve dans le \< *exemples de chemin*> \Admin\Orchestrations\PartyResolution active.</span><span class="sxs-lookup"><span data-stu-id="c77c7-141">The PartyResolution sample is located in the \<*Samples Path*>\Admin\Orchestrations\PartyResolution directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c77c7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c77c7-142">See Also</span></span>  
 [<span data-ttu-id="c77c7-143">Admin-ExplorerOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="c77c7-143">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)
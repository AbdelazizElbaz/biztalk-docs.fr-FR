---
title: PartnerManagement (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83e2a84f-ab25-4a7c-b8d7-0ba2dfa93095
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2ffc9e84e8c31ed1e1feb4c768498e817ad474c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="partnermanagement-biztalk-server-sample"></a><span data-ttu-id="8297e-102">PartnerManagement (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8297e-102">PartnerManagement (BizTalk Server Sample)</span></span>
<span data-ttu-id="8297e-103">L’exemple PartnerManagement illustre comment gérer des parties dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la **ExplorerOM** objets d’administration.</span><span class="sxs-lookup"><span data-stu-id="8297e-103">The PartnerManagement sample demonstrates how to manage parties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by using the **ExplorerOM** administration objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8297e-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8297e-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="8297e-105">Vous devez disposer des privilèges d'administrateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser les objets d'administration dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8297e-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="8297e-106">La stratégie d'exécution de Windows PowerShell doit autoriser l'exécution des scripts.</span><span class="sxs-lookup"><span data-stu-id="8297e-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="8297e-107">Pour plus d'informations, consultez la page [Examen de la stratégie d'exécution](http://go.microsoft.com/fwlink/?LinkId=128930).</span><span class="sxs-lookup"><span data-stu-id="8297e-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="8297e-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8297e-108">What This Sample Does</span></span>  
 <span data-ttu-id="8297e-109">Cet exemple illustre l’utilisation des classes d’administration à partir de la **Microsoft.BizTalk.ExplorerOM** espace de noms pour gérer les tiers.</span><span class="sxs-lookup"><span data-stu-id="8297e-109">This sample demonstrates using the administrative classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage parties.</span></span> <span data-ttu-id="8297e-110">Les tiers représentent les partenaires commerciaux ou les applications principales avec lesquels un processus d'entreprise peut interagir.</span><span class="sxs-lookup"><span data-stu-id="8297e-110">Parties represent trading partners or back-end applications with which a business process can interact.</span></span> <span data-ttu-id="8297e-111">Pour plus d’informations sur les parties en général, consultez la documentation de [Parties](../core/parties.md) ou [liens de rôle et les rôles de lien de Service](../core/role-links-and-service-link-roles.md).</span><span class="sxs-lookup"><span data-stu-id="8297e-111">For more information about parties in general, see the documentation for [Parties](../core/parties.md) or [Role Links and Service Link Roles](../core/role-links-and-service-link-roles.md).</span></span> <span data-ttu-id="8297e-112">Il est écrit dans Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8297e-112">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="8297e-113">Un exemple de script Windows PowerShell est également inclus dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8297e-113">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="8297e-114">Il illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8297e-114">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="8297e-115">Création d'un tiers avec un alias standard ou personnalisé et ajout de ports d'envois [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] existants à ce tiers.</span><span class="sxs-lookup"><span data-stu-id="8297e-115">Creating a new party with a custom or standard alias and adding existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send ports to the party.</span></span>  
  
-   <span data-ttu-id="8297e-116">Inscription du nouveau tiers avec un lien de rôle existant sur le serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8297e-116">Enlisting the new party with an existing role link on the BizTalk server.</span></span>  
  
-   <span data-ttu-id="8297e-117">Annulation de l'inscription du nouveau tiers.</span><span class="sxs-lookup"><span data-stu-id="8297e-117">Un-enlisting the new party.</span></span>  
  
-   <span data-ttu-id="8297e-118">Suppression du nouveau tiers.</span><span class="sxs-lookup"><span data-stu-id="8297e-118">Deleting the new party.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="8297e-119">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="8297e-119">Where To Find This Sample</span></span>  
 <span data-ttu-id="8297e-120">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="8297e-120">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="8297e-121">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\PartnerManagement</span><span class="sxs-lookup"><span data-stu-id="8297e-121">\<*Samples Path*\>\Admin\ExplorerOM\PartnerManagement</span></span>  
  
 <span data-ttu-id="8297e-122">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="8297e-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="8297e-123">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="8297e-123">File(s)</span></span>|<span data-ttu-id="8297e-124"> Description</span><span class="sxs-lookup"><span data-stu-id="8297e-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8297e-125">PartnerManagement.cs</span><span class="sxs-lookup"><span data-stu-id="8297e-125">PartnerManagement.cs</span></span>|<span data-ttu-id="8297e-126">Fichier source [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] pour les opérations montrées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8297e-126">[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="8297e-127">PartnerManagement.sln et PartnerManagement.csproj</span><span class="sxs-lookup"><span data-stu-id="8297e-127">PartnerManagement.sln and PartnerManagement.csproj</span></span>|<span data-ttu-id="8297e-128">Fichiers de projet et de solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="8297e-128">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="8297e-129">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8297e-129">Building and Running This Sample</span></span>  
 <span data-ttu-id="8297e-130">Avant de créer l'exemple, vous devez le personnaliser pour le serveur BizTalk en apportant quatre modifications au code.</span><span class="sxs-lookup"><span data-stu-id="8297e-130">Before you build the sample, you need to make four code modifications to customize the sample for the BizTalk server.</span></span> <span data-ttu-id="8297e-131">Cette opération est nécessaire car l'exemple utilise des noms arbitraires pour les ports d'envoi associés au tiers et un nom de rôle arbitraire pour l'inscription.</span><span class="sxs-lookup"><span data-stu-id="8297e-131">This is necessary because the sample uses arbitrary names for send ports associated with the party and an arbitrary role name for the enlistment.</span></span> <span data-ttu-id="8297e-132">C'est pourquoi, vous devez fournir des noms valides pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="8297e-132">Therefore you need to provide valid names to the sample.</span></span> <span data-ttu-id="8297e-133">Pour illustrer ce, cette rubrique décrit tout d’abord générer l’exemple PartyResolution à partir du répertoire suivant : \< *exemples de chemin*\>\Orchestrations\PartyResolution.</span><span class="sxs-lookup"><span data-stu-id="8297e-133">To demonstrate this sample, this topic describes first building the PartyResolution sample from the following directory: \<*Samples Path*\>\Orchestrations\PartyResolution.</span></span> <span data-ttu-id="8297e-134">Cette solution permet de s'assurer qu'un nom de rôle et des noms de ports d'envoi valides figurent sur le serveur BizTalk pour illustrer les procédures de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="8297e-134">This approach is used to make sure a valid role name and send port names are present on the BizTalk server to demonstrate the sample procedures.</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="8297e-135">Pour créer l'exemple</span><span class="sxs-lookup"><span data-stu-id="8297e-135">To build this sample</span></span>  
  
1.  <span data-ttu-id="8297e-136">Vous devez commencer par vérifier que l'exemple PartyResolution a été créé et initialisé de manière à utiliser un nom de rôle et des noms de ports d'envoi valides.</span><span class="sxs-lookup"><span data-stu-id="8297e-136">First make sure the PartyResolution sample has been built and initialized so that a valid role name and send port names can be used by the sample.</span></span> <span data-ttu-id="8297e-137">Cela est décrit dans la section « Création et initialisation de l’exemple » [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8297e-137">This is documented in the section entitled “Building and Initializing This Sample” in  [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="8297e-138">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution PartnerManagement.sln.</span><span class="sxs-lookup"><span data-stu-id="8297e-138">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file PartnerManagement.sln.</span></span>  
  
3.  <span data-ttu-id="8297e-139">Dans l'Explorateur de solutions, ouvrez le fichier source PartnerManagement.cs.</span><span class="sxs-lookup"><span data-stu-id="8297e-139">In Solution Explorer, open the source file PartnerManagement.cs.</span></span>  
  
4.  <span data-ttu-id="8297e-140">Faites défiler vers le bas dans la fonction nommée **CreateParty** et insérez les deux envoyer des exemples de noms à partir de la PartyResolution ou utilisent des noms valides à partir de l’environnement BizTalk server.</span><span class="sxs-lookup"><span data-stu-id="8297e-140">Scroll down into the function named **CreateParty** and insert the two send port names from the PartyResolution sample or use valid names from the BizTalk server environment.</span></span> <span data-ttu-id="8297e-141">L'exemple de code suivant illustre les modifications apportées à l'aide des ports d'envoi de l'exemple PartyResolution.</span><span class="sxs-lookup"><span data-stu-id="8297e-141">The following code example demonstrates the change using the send ports from the PartyResolution sample.</span></span>  
  
    ```  
    // Replacing arbitrary send port names with PartyResolution send port names ===  
  
    //            myParty.SendPorts.Add(catalog.SendPorts["NormalDelivery"]);  
    //            myParty.SendPorts.Add(catalog.SendPorts["ExpressDelivery"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency1"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency2"]);  
  
    ```  
  
5.  <span data-ttu-id="8297e-142">Faites défiler vers le bas dans la fonction nommée **EnlistParty** et modifiez la boucle foreach afin qu’elle recherche l’assembly Supplier pour un rôle nommé « ShipmentRole » à utiliser avec l’inscription.</span><span class="sxs-lookup"><span data-stu-id="8297e-142">Scroll down into the function named **EnlistParty** and change the foreach loop so that it searches the Supplier assembly for a role named “ShipmentRole” to use with the enlistment.</span></span> <span data-ttu-id="8297e-143">L'exemple de code suivant illustre les modifications à apporter pour utiliser ShipmentRole, à partir de l'exemple PartyResolution.</span><span class="sxs-lookup"><span data-stu-id="8297e-143">The following code example demonstrates the change to use the ShipmentRole from the PartyResolution sample.</span></span>  
  
    ```  
                // Search for the “Shipmentrole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
6.  <span data-ttu-id="8297e-144">Faites défiler vers le bas dans la fonction nommée **UnenlistParty** et modifiez la boucle foreach pour rechercher l’assembly Supplier pour le rôle ShipmentRole.</span><span class="sxs-lookup"><span data-stu-id="8297e-144">Scroll down into the function named **UnenlistParty** and change the foreach loop to search the Supplier assembly for the ShipmentRole.</span></span> <span data-ttu-id="8297e-145">L'exemple de code suivant illustre cette modification.</span><span class="sxs-lookup"><span data-stu-id="8297e-145">The following code example demonstrates this change.</span></span>  
  
    ```  
                // Search for the “ShipmentRole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
7.  <span data-ttu-id="8297e-146">Après la création et l'inscription du nouveau tiers avec le ShipmentRole, l'exemple est conçu pour annuler immédiatement l'inscription du tiers et supprimer celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8297e-146">After creating and enlisting the new party with the ShipmentRole, the sample is designed to immediately un-enlist the party and delete it.</span></span> <span data-ttu-id="8297e-147">Ajoutez la modification de code suivante à la procédure principale pour suspendre l'exécution et afficher l'inscription créée pour le nouveau tiers dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8297e-147">Add the following code change to the main procedure to pause execution and allow you to view the created enlistment for the new party in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       CreateParty();     
       EnlistParty();     
  
       Console.WriteLine("\nNew Party created and enlisted.\n\nPress <Enter> to unenlist and delete.\n");  
       Console.ReadLine();  
  
       UnenlistParty();   
       DeleteParty();  
    }  
  
    ```  
  
8.  <span data-ttu-id="8297e-148">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="8297e-148">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="8297e-149">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8297e-149">To run this sample</span></span>  
  
1.  <span data-ttu-id="8297e-150">Ouvrez une fenêtre de commande, puis accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="8297e-150">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="8297e-151">\<*Exemples de chemin d’accès*\>\Admin\ExplorerOM\PartnerManagement\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="8297e-151">\<*Samples Path*\>\Admin\ExplorerOM\PartnerManagement\bin\Debug</span></span>  
  
2.  <span data-ttu-id="8297e-152">Exécutez le fichier PartnerManagement.exe.</span><span class="sxs-lookup"><span data-stu-id="8297e-152">Run the file PartnerManagement.exe.</span></span>  
  
3.  <span data-ttu-id="8297e-153">Lorsque l’exemple affiche le message que le nouveau tiers est créé et inscrit, ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration et l’affichage du nouveau tiers nommé **FedEx** sous le **Parties** nœud.</span><span class="sxs-lookup"><span data-stu-id="8297e-153">When the sample displays the message that the new party is created and enlisted, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and view the new party named **FedEx** under the **Parties** node.</span></span>  
  
4.  <span data-ttu-id="8297e-154">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, parcourez l’arborescence pour le **ShipmentRole** sous **Applications\BizTalk Application 1\Role liens**.</span><span class="sxs-lookup"><span data-stu-id="8297e-154">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, navigate the tree view to the **ShipmentRole** under **Applications\BizTalk Application 1\Role Links**.</span></span> <span data-ttu-id="8297e-155">Double-cliquez sur **ShipmentRole** et notez **ShipmentAgency1** mappé à la **SupplierAdvice** opération et **ShipmentAgency2** mappé à la **SupplierOrder** opération dans l’inscription.</span><span class="sxs-lookup"><span data-stu-id="8297e-155">Double-click **ShipmentRole** and notice **ShipmentAgency1** mapped to the **SupplierAdvice** operation and **ShipmentAgency2** mapped to the **SupplierOrder** operation in the enlistment.</span></span>  
  
5.  <span data-ttu-id="8297e-156">Dans la fenêtre de commande, appuyez sur ENTRÉE pour autoriser l'exemple à annuler l'inscription et à supprimer le nouveau tiers.</span><span class="sxs-lookup"><span data-stu-id="8297e-156">In the command window, press ENTER to allow the sample to un-enlist and delete the new party.</span></span>  
  
6.  <span data-ttu-id="8297e-157">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, vérifiez que le tiers a été désinscrit à partir de la **ShipmentRole** et supprimées à partir de la **Parties** nœud.</span><span class="sxs-lookup"><span data-stu-id="8297e-157">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, verify the party was un-enlisted from the **ShipmentRole** and deleted from the **Parties** node.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="8297e-158">Exemple de script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8297e-158">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="8297e-159">L’exemple de script Windows PowerShell suivant peut être utilisé pour illustrer les mêmes fonctionnalités de la **ExplorerOM** classes :</span><span class="sxs-lookup"><span data-stu-id="8297e-159">The following Windows PowerShell script example can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#===============================================================#  
#===                                                         ===#  
#=== Create a new party named "FedEx" as an example.         ===#  
#===                                                         ===#  
#=== Two Shipment agency send ports from the PartyResolution ===#  
#=== sample will be added to the party.                      ===#  
#===                                                         ===#  
#===============================================================#  
Function CreateParty  
{  
  #=== Create a party =====================#  
  $myParty = $Catalog.AddNewParty()  
  $myParty.Name = "FedEx"  
  
  #=== create a standard alias ==========================#  
  $standardAlias = $myParty.AddNewAlias()  
  $standardAlias.Name = "D-U-N-S (Dun & Bradstreet)"  
  $standardAlias.Value = "Value1"  
  
  #=== Create a custom alias ==================#  
  $customAlias = $myParty.AddNewAlias()  
  $customAlias.Name = "Telephone"  
  $customAlias.Qualifier = "100"  
  $customAlias.Value = "4255550234"  
  
  #=== Add party send ports =====================================================#  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]  
  
  $sendport1 = $Catalog.SendPorts["SP_FilesToShipmentAgency1"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport1)  
  
  $sendport2 = $Catalog.SendPorts["SP_FilesToShipmentAgency2"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport2)  
  
  #=== Specify a signature certificate, make sure the certificate is available ===#  
  #=== in the AddressBook store of the Local Machine                           ===#  
  
  foreach ($certificate in $Catalog.Certificates)  
  {  
    if ($certificate.ShortName -eq "BR, Certisign Certificadora Digital Ltda., Certisign - Autoridade Certificadora - AC2")  
    {  
      $myParty.SignatureCert = $certificate  
    }  
  }  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Delete the party named "FedEx"                          ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteParty  
{  
  $Catalog.RemoveParty($Catalog.Parties["FedEx"])  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Enlist the "FedEx" party with the "ShipmentRole"        ===#  
#===                                                         ===#  
#===============================================================#  
Function EnlistParty  
{  
  $myParty = $Catalog.Parties["FedEx"]  
  
  #=== Get the "ShipmentRole" in the Supplier assembly.        ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Enlist the party under the shipper role ===#  
  $enlistedParty = $svcRole.AddNewEnlistedParty($myParty)  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]   
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierAdvice" ===#  
  #=== operation.                                              ===#  
  #=== Using the first send port added to the new party which  ===#  
  #=== is "SP_FilesToShipmentAgency1" at index 0 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[0].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,0)  
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierOrder"  ===#  
  #=== operation.                                              ===#  
  #=== Using the second send port added to the new party which ===#  
  #=== is "SP_FilesToShipmentAgency2" at index 1 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[1].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,1)  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Unenlist the "FedEx" party from the ShipmentRole        ===#  
#===                                                         ===#  
#===============================================================#  
Function UnenlistParty  
{  
  #=== Get the "ShipmentRole" from the Supplier assembly. ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Remove the "FedEx" party ===#  
  foreach ($enlistedparty in $svcRole.EnlistedParties)  
  {  
    if ($enlistedparty.Party.Name -eq "FedEx")  
    {  
      $svcRole.RemoveEnlistedParty($enlistedparty)  
      break  
    }  
  }  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== This sample expects the PartyResolution sample to be built and deployed  ===#  
#=== to the BizTalk Server.                                                   ===#  
  
write-host `r`nMake sure the "PartyResolution" sample application from the Orchestrations   
write-host sample directory is deployed and running.  
write-host By default it will be listed in the BizTalk Server Administration Console  
write-host with the application name: `"BizTalk.Application.1`"`r`n  
  
$SupplierAssembly = $Catalog.Assemblies["Supplier"]  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to unenlist,  ===#  
#=== and delete the party.                                      ===#  
#==================================================================#  
  
$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the party...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
CreateParty  
EnlistParty  
  
if ($Script:NoExceptionOccurred)  
{  
  Write-Host "`r`nExample Party `"FedEx`" should be created and enlisted with the `"ShipmentRole`".`r`n"  
  Write-Host You can view the results in the BizTalk Server Administration console.`r`n  
  Write-Host "Press <Enter> to unenlist and delete...`r`n"  
  Read-Host  
}  
  
UnenlistParty  
DeleteParty  
  
```  
  
 <span data-ttu-id="8297e-160">Voici un exemple de sortie de l'exécution de l'exemple de script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8297e-160">Here is example output from running the PowerShell example script.</span></span> <span data-ttu-id="8297e-161">Si l'exécution du script échoue, vérifiez que l'exécution de scripts PowerShell est activée en vous référant à la section relative aux conditions préalables dans la partie supérieure de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8297e-161">If the script fails to run, make sure PowerShell scripting is enabled according to the requirements note at the top of this topic.</span></span>  
  
```  
PS C:\> .\PartnerManagement.ps1  
  
Make sure the PartyResolution sample application from the Orchestrations  
sample directory is deployed and running.  
By default it will be listed in the BizTalk Server Administration Console  
with the application name: "BizTalk.Application.1"  
  
Example Party "FedEx" should be created and enlisted with the "ShipmentRole".  
  
You can view the results in the BizTalk Server Administration console.  
  
Press <Enter> to unenlist and delete...  
```  
  
## <a name="see-also"></a><span data-ttu-id="8297e-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8297e-162">See Also</span></span>  
 <span data-ttu-id="8297e-163">[Parties](../core/parties.md) </span><span class="sxs-lookup"><span data-stu-id="8297e-163">[Parties](../core/parties.md) </span></span>  
 <span data-ttu-id="8297e-164">[Liens de rôle et les rôles de lien de Service](../core/role-links-and-service-link-roles.md) </span><span class="sxs-lookup"><span data-stu-id="8297e-164">[Role Links and Service Link Roles](../core/role-links-and-service-link-roles.md) </span></span>  
 [<span data-ttu-id="8297e-165">Admin (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8297e-165">Admin (BizTalk Server Samples Folder)</span></span>](../core/admin-biztalk-server-samples-folder.md)
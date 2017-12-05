---
title: "Annuler le déploiement d’un adaptateur à l’aide de l’adaptateur LOB WCF SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f9a124-9e63-4451-af0e-ffee752fbeac
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1332e41593ede5f7075ec7f5ede1293d79d65594
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="undeploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="f2294-102">Annuler le déploiement d’un adaptateur à l’aide de l’adaptateur LOB WCF SDK</span><span class="sxs-lookup"><span data-stu-id="f2294-102">Undeploy an adapter using the WCF LOB adapter SDK</span></span>
<span data-ttu-id="f2294-103">Pour annuler le déploiement d’une carte à partir d’un ordinateur, l’utilisateur doit effectuer les deux tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2294-103">To undeploy an adapter from a computer, the user needs to perform the following two tasks:</span></span>  
  
1.  <span data-ttu-id="f2294-104">Désinstaller l’assembly d’adaptateur (et tous les assemblys dépendants) dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="f2294-104">Uninstall the adapter assembly (and any dependent assemblies) from the global assembly cache (GAC).</span></span>  
  
2.  <span data-ttu-id="f2294-105">Supprimer la liaison de l’adaptateur et d’un élément de liaison de l’adaptateur dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="f2294-105">Remove the adapter binding and adapter binding element in the machine.config file.</span></span>  
  
## <a name="uninstall-an-assembly-from-the-gac"></a><span data-ttu-id="f2294-106">Désinstaller un Assembly du GAC</span><span class="sxs-lookup"><span data-stu-id="f2294-106">Uninstall an Assembly from the GAC</span></span>  
  
#### <a name="use-the-windows-interface"></a><span data-ttu-id="f2294-107">Utiliser l’interface Windows</span><span class="sxs-lookup"><span data-stu-id="f2294-107">Use the Windows interface</span></span>  
  
1.  <span data-ttu-id="f2294-108">Ouvrez l’Explorateur Windows comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **l’Explorateur Windows**.</span><span class="sxs-lookup"><span data-stu-id="f2294-108">Open Windows Explorer as follows: Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="f2294-109">Recherchez dans le GAC, ce qui se trouve dans % systemdrive%\Windows\Assembly.</span><span class="sxs-lookup"><span data-stu-id="f2294-109">Browse to the GAC, which is located at %systemdrive%\Windows\Assembly.</span></span>  
  
3.  <span data-ttu-id="f2294-110">Sur chaque fichier d’assembly qui est inclus dans votre application, cliquez **désinstallation**, puis cliquez sur **Oui** pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="f2294-110">Right-click each assembly file that is included in your application, click **Uninstall**, and then click **Yes** to confirm.</span></span>  
  
#### <a name="use-the-command-line"></a><span data-ttu-id="f2294-111">Utilisez la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="f2294-111">Use the command line</span></span>  
  
1.  <span data-ttu-id="f2294-112">Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f2294-112">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="f2294-113">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f2294-113">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="f2294-114">**gacutil /u** \< *complet**nom de l’assembly*\></span><span class="sxs-lookup"><span data-stu-id="f2294-114">**gacutil /u** \<*fully qualified**assembly name*\></span></span>  
  
     <span data-ttu-id="f2294-115">Dans cette commande, le nom de l’assembly est le nom de l’assembly à désinstaller à partir du GAC.</span><span class="sxs-lookup"><span data-stu-id="f2294-115">In this command, the assembly name is the name of the assembly to uninstall from the GAC.</span></span>  
  
     <span data-ttu-id="f2294-116">L'exemple suivant supprime un assembly nommé hello.dll du GAC.</span><span class="sxs-lookup"><span data-stu-id="f2294-116">The following example removes an assembly named hello.dll from the GAC.</span></span>  
  
     `gacutil /u "MyAdapter,Version=1.0.0.0, Culture=neutral, PublicKeyToken=fafafafafafafafa"`
  
## <a name="remove-the-adapter-binding-from-the-machineconfig-file"></a><span data-ttu-id="f2294-117">Supprimer la liaison de l’adaptateur à partir du fichier Machine.config</span><span class="sxs-lookup"><span data-stu-id="f2294-117">Remove the Adapter Binding from the Machine.config File</span></span>  
 <span data-ttu-id="f2294-118">Vous pouvez manuellement modifier le fichier machine.config pour supprimer la liaison de la carte, ou utilisez l’éditeur de Configuration de Service.</span><span class="sxs-lookup"><span data-stu-id="f2294-118">You can manually edit the machine.config file to remove the adapter binding, or use the Service Configuration Editor.</span></span> <span data-ttu-id="f2294-119">Cette section répertorie les deux étapes.</span><span class="sxs-lookup"><span data-stu-id="f2294-119">This section lists both steps.</span></span> 
  
#### <a name="manually-edit-the-machineconfig-file"></a><span data-ttu-id="f2294-120">Modifier manuellement le fichier machine.config</span><span class="sxs-lookup"><span data-stu-id="f2294-120">Manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="f2294-121">Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="f2294-121">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="f2294-122">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **bloc-notes \<chemin d’installation de Windows\>\Microsoft.NET\Framework\\< version\>\CONFIG\machine.config**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2294-122">To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2294-123">Effectuez une sauvegarde du fichier machine.config avant d’apporter des modifications pour vous prémunir contre les erreurs de modification.</span><span class="sxs-lookup"><span data-stu-id="f2294-123">Make a backup of the machine.config file before you make changes to guard against editing mistakes.</span></span>  
  
2.  <span data-ttu-id="f2294-124">Mettre à jour le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="f2294-124">Update the machine.config file.</span></span> <span data-ttu-id="f2294-125">Recherchez l’élément de bindingExtensions pour la carte que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="f2294-125">Find the bindingExtensions element for the adapter you want to remove.</span></span> <span data-ttu-id="f2294-126">Basée sur les autres informations qui n’est présentes, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2294-126">Based on the other information that is present, do one of the following:</span></span>  
  
    -   <span data-ttu-id="f2294-127">S’il existe des autres bindingExtensions, supprimez uniquement votre extension de carte.</span><span class="sxs-lookup"><span data-stu-id="f2294-127">If there are other bindingExtensions, remove only your adapter extension.</span></span>  
  
    -   <span data-ttu-id="f2294-128">S’il n’y a aucune autres bindingExtensions, vous pouvez supprimer la section bindingExtensions (y compris votre extension de carte).</span><span class="sxs-lookup"><span data-stu-id="f2294-128">If there are no other bindingExtensions, you can remove the bindingExtensions section (including your adapter extension).</span></span>  
  
    -   <span data-ttu-id="f2294-129">S’il n’y a aucun autre bindingExtensions ou extensions, vous pouvez supprimer la section des extensions.</span><span class="sxs-lookup"><span data-stu-id="f2294-129">If there are no other bindingExtensions or extensions, you can remove the extensions section.</span></span>  
  
    -   <span data-ttu-id="f2294-130">Enfin, si system.serviceModel contient uniquement votre extension de carte, vous pouvez supprimer la section system.serviceModel entière.</span><span class="sxs-lookup"><span data-stu-id="f2294-130">Finally, if system.serviceModel contains only your adapter extension, you can remove the entire system.serviceModel section.</span></span>  
  
3.  <span data-ttu-id="f2294-131">Répétez l’étape 2 pour l’élément bindingElementExtensions.</span><span class="sxs-lookup"><span data-stu-id="f2294-131">Repeat step 2 for the bindingElementExtensions element.</span></span>  
  
4.  <span data-ttu-id="f2294-132">Fermez et enregistrez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="f2294-132">Close and save the machine.config file.</span></span>  
  
#### <a name="use-the-service-configuration-editor-do-change-the-machineconfig-file"></a><span data-ttu-id="f2294-133">Utilisez l’éditeur de Configuration de Service ne modifiez pas le fichier machine.config</span><span class="sxs-lookup"><span data-stu-id="f2294-133">Use the Service Configuration Editor do change the machine.config file</span></span>  
  
1.  <span data-ttu-id="f2294-134">Ouvrez l’éditeur de Configuration de Service.</span><span class="sxs-lookup"><span data-stu-id="f2294-134">Open Service Configuration Editor.</span></span> <span data-ttu-id="f2294-135">Consultez [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f2294-135">See [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) for more information.</span></span>
  
2.  <span data-ttu-id="f2294-136">Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds.</span><span class="sxs-lookup"><span data-stu-id="f2294-136">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="f2294-137">Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier et sélectionnez l’élément d’extensions de liaison.</span><span class="sxs-lookup"><span data-stu-id="f2294-137">Click the **Advanced** folder, click the **Extensions** folder, and then select the binding extensions element.</span></span>  
  
3.  <span data-ttu-id="f2294-138">Dans le volet détails de l’éditeur d’Extensions de liaison, cliquez sur l’extension de liaison que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="f2294-138">In the details pane of the Binding Extensions Editor, click the binding extension that you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="f2294-139">Dans l’illustration suivante, MyAdapterExtension est mis en surbrillance et est supprimée.</span><span class="sxs-lookup"><span data-stu-id="f2294-139">In the following figure, MyAdapterExtension is highlighted and will be deleted.</span></span>  
  
     <span data-ttu-id="f2294-140">![Éditeur de configuration de service avec ajout d’extension. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span><span class="sxs-lookup"><span data-stu-id="f2294-140">![Service configuration editor with added extension.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span></span>  
  
4.  <span data-ttu-id="f2294-141">Fermez l'éditeur de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="f2294-141">Close the Service Configuration Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2294-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2294-142">See Also</span></span>  
 [<span data-ttu-id="f2294-143">Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK</span><span class="sxs-lookup"><span data-stu-id="f2294-143">Deploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)
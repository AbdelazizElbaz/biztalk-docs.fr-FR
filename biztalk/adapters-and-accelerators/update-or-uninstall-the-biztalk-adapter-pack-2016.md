---
title: "Mettre à jour ou désinstaller le 2016 de pack d’adaptateur BizTalk | Documents Microsoft"
description: "Utilisez l’Assistant Installation ou msiexec pour modifier ou désinstaller 2016 BAP inclus dans BizTalk Server ; y compris de supprimer les liaisons et de supprimer les RFC personnalisés"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3d6c001-1005-4d7b-a143-eaa37b48f898
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb0dd0b9d778f878df9a06efdfc0f41754403690
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="update-or-uninstall-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="01065-103">Mettre à jour ou désinstaller le 2016 de pack d’adaptateur BizTalk</span><span class="sxs-lookup"><span data-stu-id="01065-103">Update or uninstall the BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="01065-104">Comment modifier ou désinstaller le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01065-104">How to change or uninstall the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>

<a name="BKMK_Modify_Adap"></a>
## <a name="change-or-update-the-installation"></a><span data-ttu-id="01065-105">Modifier ou mettre à jour de l’installation</span><span class="sxs-lookup"><span data-stu-id="01065-105">Change or update the installation</span></span>  
<span data-ttu-id="01065-106">Avant d’exécuter l’Assistant Installation pour modifier le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, assurez-vous que le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="01065-106">Before you run the setup wizard to modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] is installed.</span></span> 
  
 <span data-ttu-id="01065-107">Vous pouvez modifier l’installation en mode interactif (l’Assistant d’installation), ou en mode silencieux (la ligne de commande).</span><span class="sxs-lookup"><span data-stu-id="01065-107">You can modify the installation in interactive mode (the setup wizard), or in silent mode (the command line).</span></span>
  
### <a name="use-the-setup-wizard"></a><span data-ttu-id="01065-108">Utilisez l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="01065-108">Use the setup wizard</span></span>  
  
1.  <span data-ttu-id="01065-109">Connectez-vous avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="01065-109">Sign in with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="01065-110">Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.</span><span class="sxs-lookup"><span data-stu-id="01065-110">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
3.  <span data-ttu-id="01065-111">Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **modification**.</span><span class="sxs-lookup"><span data-stu-id="01065-111">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Change**.</span></span>  
  
4.  <span data-ttu-id="01065-112">Dans l’écran de bienvenue, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="01065-112">On the Welcome screen, select **Next**.</span></span>  
  
5.  <span data-ttu-id="01065-113">Dans **modifier, réparer ou supprimer l’installation**:</span><span class="sxs-lookup"><span data-stu-id="01065-113">In **Change, repair, or remove installation**:</span></span>  
  
    -   <span data-ttu-id="01065-114">Pour sélectionner les composants à installer, sélectionnez **modification** et accédez à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="01065-114">To select the components you want to install, select **Change** and go to Step 6.</span></span>  
  
    -   <span data-ttu-id="01065-115">Pour réparer les erreurs dans l’installation la plus récente, sélectionnez **réparer** et accédez à l’étape 7.</span><span class="sxs-lookup"><span data-stu-id="01065-115">To repair errors in the most recent installation, select **Repair** and go to Step 7.</span></span>  
  
    -   <span data-ttu-id="01065-116">Pour supprimer la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de l’ordinateur, sélectionnez **supprimer** et passez à l’étape 10.</span><span class="sxs-lookup"><span data-stu-id="01065-116">To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from the computer, select **Remove** and then go to Step 10.</span></span>  
  
6.  <span data-ttu-id="01065-117">Si vous avez choisi de modifier l’installation :</span><span class="sxs-lookup"><span data-stu-id="01065-117">If you chose to modify the installation:</span></span>  
  
    -   <span data-ttu-id="01065-118">Développez le **Microsoft BizTalk Adapter Pack** nœud de choisir d’installer les adaptateurs de base, les fournisseurs de données .NET Framework ou les deux.</span><span class="sxs-lookup"><span data-stu-id="01065-118">Expand the **Microsoft BizTalk Adapter Pack** node to choose to install the base adapters, the .NET Framework Data Providers, or both.</span></span>  
  
    -   <span data-ttu-id="01065-119">Développez le **Base cartes** nœud de choisir d’installer toutes les cartes ou des cartes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="01065-119">Expand the **Base Adapters** node to choose to install all the adapters or specific adapters.</span></span>  
  
    -   <span data-ttu-id="01065-120">Développez le **ADO fournisseurs** nœud de choisir d’installer tous les fournisseurs ou des fournisseurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="01065-120">Expand the **ADO Providers** node to choose to install all the providers or specific providers.</span></span>  
  
    -   <span data-ttu-id="01065-121">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="01065-121">Select **Next**.</span></span>  
  
    -   <span data-ttu-id="01065-122">Sélectionnez **modification**, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="01065-122">Select **Change**, and then select **Finish**.</span></span>  
  
7.  <span data-ttu-id="01065-123">Si vous avez choisi réparer l’installation, dans le **prêt à réparer Microsoft BizTalk Adapter Pack** boîte de dialogue, sélectionnez **réparer**.</span><span class="sxs-lookup"><span data-stu-id="01065-123">If you chose to repair the installation, in the **Ready to repair Microsoft BizTalk Adapter Pack** dialog box, select **Repair**.</span></span> <span data-ttu-id="01065-124">L’Assistant démarre la réparation de l’installation.</span><span class="sxs-lookup"><span data-stu-id="01065-124">The wizard starts repairing the installation.</span></span>  
  
8.  <span data-ttu-id="01065-125">Si nécessaire, modifiez vos préférences concernant le choix d’amélioration du produit, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="01065-125">If required, change your preferences regarding opting for CEIP, and then select **OK**.</span></span> 
  
9. <span data-ttu-id="01065-126">Sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="01065-126">Select **Finish**.</span></span>  
  
10. <span data-ttu-id="01065-127">Si vous avez choisi de supprimer les adaptateurs, dans le **prêt à supprimer de Microsoft BizTalk Adapter Pack** boîte de dialogue, sélectionnez **supprimer**, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="01065-127">If you chose to remove the adapters, in the **Ready to remove Microsoft BizTalk Adapter Pack** dialog box, select **Remove**, and then select **Finish**.</span></span>  
  
### <a name="use-msiexec-in-silent-mode"></a><span data-ttu-id="01065-128">Utiliser msiexec en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="01065-128">Use msiexec in silent mode</span></span>  
  
1.  <span data-ttu-id="01065-129">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="01065-129">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="01065-130">Exécutez une commande semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="01065-130">Run a command similar to the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01065-131">Pour modifier la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode sans assistance sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.</span><span class="sxs-lookup"><span data-stu-id="01065-131">To modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in a silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
    ```  
  
     <span data-ttu-id="01065-132">Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]et installe le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01065-132">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], and installs the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span>  
  
     <span data-ttu-id="01065-133">À l’aide des valeurs différentes pour le `REMOVE` et `ADDLOCAL` propriétés, vous pouvez ajouter ou supprimer des composants spécifiques.</span><span class="sxs-lookup"><span data-stu-id="01065-133">By using different values for the `REMOVE` and `ADDLOCAL` properties, you can add or remove specific components.</span></span> <span data-ttu-id="01065-134">Reportez-vous au tableau dans **installer en mode silencieux** à [BAP d’installation](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) pour plus d’informations sur les valeurs que vous pouvez utiliser pour ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="01065-134">Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for these properties.</span></span>  
  
     <span data-ttu-id="01065-135">Vous pourrez également effectuer une réparation en mode silencieux à l’aide de l’option /f dans le cadre de la commande msiexec.</span><span class="sxs-lookup"><span data-stu-id="01065-135">You can also do a silent repair by using the /f option as part of the msiexec command.</span></span> <span data-ttu-id="01065-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="01065-136">For example:</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn /f  
    ```  
  
     <span data-ttu-id="01065-137">Vous pouvez utiliser diverses combinaisons avec l’option /f.</span><span class="sxs-lookup"><span data-stu-id="01065-137">You can use various different combinations with the /f option.</span></span> <span data-ttu-id="01065-138">Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`.</span><span class="sxs-lookup"><span data-stu-id="01065-138">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="01065-139">Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span><span class="sxs-lookup"><span data-stu-id="01065-139">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="01065-140">Lors de la modification du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation en mode silencieux, vous ne pouvez pas modifier vos préférences pour vous inscrire ou de refuser le CEIP.</span><span class="sxs-lookup"><span data-stu-id="01065-140">While modifying the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP.</span></span> <span data-ttu-id="01065-141">Les préférences de que celle choisie lors de l’installation reste, même si vous définissez explicitement la CEIP_OPTIN à true ou false.</span><span class="sxs-lookup"><span data-stu-id="01065-141">The preferences you chose during the installation remains, even if you explicitly set the CEIP_OPTIN to true or false.</span></span>  

## <a name="uninstall-or-remove-the-biztalk-adapter-pack"></a><span data-ttu-id="01065-142">Désinstaller ou supprimer le Pack d’adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="01065-142">Uninstall or remove the BizTalk Adapter Pack</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01065-143">Si vous avez créé des tables dans la base de données SQL Server pour travailler avec la fonctionnalité tRFC de la [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], vous devez les supprimer manuellement avant de désinstaller le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01065-143">If you created tables in the SQL Server database to work with the tRFC feature of the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], you must manually remove them before uninstalling the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="01065-144">Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] d’installation copie un `SapAdapter-DbScript-Uninstall.sql` de fichiers en général au  *\<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]* .</span><span class="sxs-lookup"><span data-stu-id="01065-144">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copies a `SapAdapter-DbScript-Uninstall.sql` file typically at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]*.</span></span> <span data-ttu-id="01065-145">Exécuter ce fichier pour supprimer les tables que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="01065-145">Run this file to remove the tables you created.</span></span>  
  
<span data-ttu-id="01065-146">Effectuez les étapes suivantes pour supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] à partir de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01065-146">Complete the following steps to remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from your computer.</span></span> <span data-ttu-id="01065-147">Assurez-vous que vous avez le [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installé avant d’exécuter l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="01065-147">Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard.</span></span>  
  
 <span data-ttu-id="01065-148">Vous pouvez supprimer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode interactif (Assistant Installation), ou en mode silencieux (ligne de commande).</span><span class="sxs-lookup"><span data-stu-id="01065-148">You can remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode (setup wizard), or in silent mode (command line).</span></span>
  
### <a name="uninstall-using-the-setup-wizard"></a><span data-ttu-id="01065-149">Désinstallation à l’aide de l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="01065-149">Uninstall using the setup wizard</span></span>  
  
1.  <span data-ttu-id="01065-150">Dans **programmes et fonctionnalités**, sélectionnez **désinstaller un programme**.</span><span class="sxs-lookup"><span data-stu-id="01065-150">In **Programs and features**, select **Uninstall a program**.</span></span>  
  
2.  <span data-ttu-id="01065-151">Avec le bouton droit **Microsoft BizTalk Adapter Pack**, puis sélectionnez **désinstallation**.</span><span class="sxs-lookup"><span data-stu-id="01065-151">Right-click **Microsoft BizTalk Adapter Pack**, and then select **Uninstall**.</span></span>  
  
### <a name="uninstall-in-silent-mode"></a><span data-ttu-id="01065-152">Désinstaller en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="01065-152">Uninstall in silent mode</span></span>  
  
1.  <span data-ttu-id="01065-153">Ouvrez une invite de commandes et accédez au répertoire racine de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="01065-153">Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.</span></span>  
  
2.  <span data-ttu-id="01065-154">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="01065-154">Run the following command:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01065-155">Pour supprimer la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode silencieux sur une plateforme x64 64, les commandes suivantes, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi`.</span><span class="sxs-lookup"><span data-stu-id="01065-155">To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.</span></span>  
  
    ```  
    msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
    ```  
  
     <span data-ttu-id="01065-156">Cette commande supprime le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="01065-156">This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span>  
  
     <span data-ttu-id="01065-157">En fournissant des valeurs différentes pour le `REMOVE` propriété, vous pouvez supprimer des composants spécifiques à partir de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="01065-157">By providing different values for the `REMOVE` property, you can remove specific components from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="01065-158">Reportez-vous au tableau dans **installer en mode silencieux** à [BAP d’installation](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) pour plus d’informations sur les valeurs que vous pouvez utiliser pour cette propriété.</span><span class="sxs-lookup"><span data-stu-id="01065-158">Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for this property.</span></span>  
  
     <span data-ttu-id="01065-159">Pour supprimer complètement le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="01065-159">To completely remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], execute the following command:</span></span>  
  
    ```  
    msiexec /x AdaptersSetup.msi /qn  
    ```  
  
     <span data-ttu-id="01065-160">Pour plus d’informations sur le type de commande msiexec `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`.</span><span class="sxs-lookup"><span data-stu-id="01065-160">For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="01065-161">Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span><span class="sxs-lookup"><span data-stu-id="01065-161">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
  
## <a name="remove-the-bindings"></a><span data-ttu-id="01065-162">Supprimer les liaisons</span><span class="sxs-lookup"><span data-stu-id="01065-162">Remove the bindings</span></span>  
 <span data-ttu-id="01065-163">Effectuez ces étapes *uniquement* si l’Assistant installation ne parvient pas à supprimer les liaisons de l’adaptateur ou l’inscription du fournisseur de données .NET Framework à partir du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="01065-163">Complete these steps *only* if the setup wizard fails to remove the adapter bindings or .NET Framework Data Provider registration from the machine.config file.</span></span>  
  
1.  <span data-ttu-id="01065-164">Accédez au fichier machine.config sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01065-164">Go to the machine.config file on the computer.</span></span> <span data-ttu-id="01065-165">Par exemple, sur une plateforme 32 bits, le fichier machine.config est disponible sous  *\<lecteur système\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG*.</span><span class="sxs-lookup"><span data-stu-id="01065-165">For example, on a 32-bit platform, the machine.config is available under *\<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG*.</span></span>  
  
2.  <span data-ttu-id="01065-166">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="01065-166">Open the file using a text editor.</span></span>  
  
3.  <span data-ttu-id="01065-167">Supprimer l’inscription de la liaison de la carte :</span><span class="sxs-lookup"><span data-stu-id="01065-167">Remove the adapter binding registration:</span></span>  
  
    1.  <span data-ttu-id="01065-168">Recherchez le `system.serviceModel` élément et supprimer les éléments suivants figurant dans l’élément :</span><span class="sxs-lookup"><span data-stu-id="01065-168">Search for the `system.serviceModel` element, and remove the following from under the element:</span></span>  
  
        ```  
        <client>  
          <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
          <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
          <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
          <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
        </client>  
  
        ```  
  
    2.  <span data-ttu-id="01065-169">Recherchez le `bindingElementExtensions` élément sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="01065-169">Search for the `bindingElementExtensions` element under system.serviceModel\extensions.</span></span>  
  
    3.  <span data-ttu-id="01065-170">Supprimer les sections suivantes sous la `bindingElementExtensions` nœud, en fonction de la liaison d’adaptateur disponibles.</span><span class="sxs-lookup"><span data-stu-id="01065-170">Remove the following sections under the `bindingElementExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="01065-171">Vous devez supprimer toutes les liaisons si l’Assistant installation ne parvient pas à supprimer.</span><span class="sxs-lookup"><span data-stu-id="01065-171">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
         <span data-ttu-id="01065-172">Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-172">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-173">Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-173">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-174">Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-174">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-175">Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-175">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-176">Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-176">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  <span data-ttu-id="01065-177">Recherchez le `bindingExtensions` élément sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="01065-177">Search for the `bindingExtensions` element under system.serviceModel\extensions.</span></span>  
  
    5.  <span data-ttu-id="01065-178">Supprimer les sections suivantes sous la `bindingExtensions` nœud, en fonction de la liaison d’adaptateur disponibles.</span><span class="sxs-lookup"><span data-stu-id="01065-178">Remove the following sections under the `bindingExtensions` node, depending on the available adapter binding.</span></span> <span data-ttu-id="01065-179">Vous devez supprimer toutes les liaisons si l’Assistant installation ne parvient pas à supprimer.</span><span class="sxs-lookup"><span data-stu-id="01065-179">You must remove all the bindings if the setup wizard fails to remove any.</span></span>  
  
         <span data-ttu-id="01065-180">Pour [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-180">For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-181">Pour [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-181">For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-182">Pour [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-182">For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:</span></span>  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-183">Pour [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-183">For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-184">Pour [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-184">For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
4.  <span data-ttu-id="01065-185">Supprimer l’inscription du fournisseur de données .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="01065-185">Remove the .NET Framework Data Provider registration:</span></span>  
  
    -   <span data-ttu-id="01065-186">Recherchez le `DbProviderFactories` élément sous le nœud system.data.</span><span class="sxs-lookup"><span data-stu-id="01065-186">Search for the `DbProviderFactories` element under the system.data node.</span></span>  
  
    -   <span data-ttu-id="01065-187">Recherchez les fournisseurs de données .NET Framework qui sont toujours inscrits.</span><span class="sxs-lookup"><span data-stu-id="01065-187">Look for the .NET Framework Data Providers that are still registered.</span></span> <span data-ttu-id="01065-188">Supprimer les sections suivantes sous la `DbProviderFactories` nœud, selon les fournisseurs de données .NET Framework existant.</span><span class="sxs-lookup"><span data-stu-id="01065-188">Remove the following sections under the `DbProviderFactories` node, depending on the existing .NET Framework Data Providers.</span></span> <span data-ttu-id="01065-189">Vous devez supprimer tous les fournisseurs s’ils existent.</span><span class="sxs-lookup"><span data-stu-id="01065-189">You must remove all the providers if they exist.</span></span>  
  
         <span data-ttu-id="01065-190">Pour [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-190">For [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
            description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
         <span data-ttu-id="01065-191">Pour [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], supprimer :</span><span class="sxs-lookup"><span data-stu-id="01065-191">For [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], remove:</span></span>  
  
        ```  
        <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
            description=".NET Framework Data Provider for Siebel eBusiness Applications"  
            type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
5.  <span data-ttu-id="01065-192">Enregistrez et fermez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="01065-192">Save and close the machine.config file.</span></span>  
  
## <a name="remove-the-custom-rfcs"></a><span data-ttu-id="01065-193">Supprimer les RFC personnalisés</span><span class="sxs-lookup"><span data-stu-id="01065-193">Remove the custom RFCs</span></span>  
<span data-ttu-id="01065-194">Effectuez cette étape pour supprimer les RFC personnalisés que vous avez installé dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="01065-194">Complete this step to remove the custom RFCs that you installed in the SAP system.</span></span> <span data-ttu-id="01065-195">Consultez [installer ou supprimer les RFC personnalisés](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="01065-195">See [Install or remove custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  

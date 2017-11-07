---
title: "Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 376b4dcf-2d2c-4872-a394-67edc0c3d088
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72c83998bbe16899055c839a73795d456a132381
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="ac71e-102">Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK</span><span class="sxs-lookup"><span data-stu-id="ac71e-102">Deploy an adapter using the WCF LOB adapter SDK</span></span>
<span data-ttu-id="ac71e-103">Pour déployer un adaptateur, vous devez installer l’assembly de l’adaptateur dans le global assembly cache (GAC) et puis inscrire l’adaptateur dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ac71e-103">To deploy an adapter, you must install the adapter assembly into the global assembly cache (GAC), and then register the adapter in the machine.config file.</span></span>  
  
## <a name="install-the-adapter-assembly-into-the-gac"></a><span data-ttu-id="ac71e-104">Installer l’Assembly d’adaptateur dans le GAC</span><span class="sxs-lookup"><span data-stu-id="ac71e-104">Install the Adapter Assembly into the GAC</span></span>  
 <span data-ttu-id="ac71e-105">Avant l’utilisation d’un adaptateur à l’aide de Visual Studio le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] commande ou dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] fonctionnalité, vous devez installer l’assembly dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="ac71e-105">Before consuming an adapter in Visual Studio using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] command or in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] feature, you must install the assembly into the GAC.</span></span> <span data-ttu-id="ac71e-106">Seuls les assemblys qui sont dotés de nom fort peuvent être installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="ac71e-106">Only assemblies that are strong-named can be installed into the GAC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac71e-107">Pour effectuer cette procédure, vous devez être connecté avec un compte qui dispose des autorisations d’écriture sur le GAC.</span><span class="sxs-lookup"><span data-stu-id="ac71e-107">To complete this procedure, you must be logged on with an account that has Write permissions on the GAC.</span></span> <span data-ttu-id="ac71e-108">Le compte des administrateurs de l'ordinateur local dispose de ces autorisations.</span><span class="sxs-lookup"><span data-stu-id="ac71e-108">The Administrators account on the local computer has these permissions.</span></span>  
  
#### <a name="configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="ac71e-109">Configurer un fichier de clé de nom fort assembly</span><span class="sxs-lookup"><span data-stu-id="ac71e-109">Configure a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="ac71e-110">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], chargez le fichier de projet d’adaptateur qui requiert un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ac71e-110">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], load the adapter project file that needs a strong name.</span></span>  
  
2.  <span data-ttu-id="ac71e-111">Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ac71e-111">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
3.  <span data-ttu-id="ac71e-112">À l'invite de commandes, à partir du dossier dans lequel vous voulez stocker le fichier de clé, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ac71e-112">At the command prompt, from the folder where you want to store the key file, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="ac71e-113">**sn /k***nom_fichier* **.snk** </span><span class="sxs-lookup"><span data-stu-id="ac71e-113">**sn /k**  *file_name* **.snk**</span></span>  
  
     <span data-ttu-id="ac71e-114">Exemple : **sn /k EchoAdapter.snk**</span><span class="sxs-lookup"><span data-stu-id="ac71e-114">Example: **sn /k EchoAdapter.snk**</span></span>  
  
     <span data-ttu-id="ac71e-115">Un message de confirmation, **paire écrite dans la clé** \< *nom_fichier*>**.snk** `,` affiche sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ac71e-115">A confirmation message, **Key pair written to** \<*file_name*>**.snk**`,` displays on the command line.</span></span>  
  
4.  <span data-ttu-id="ac71e-116">Dans l’Explorateur de solutions Visual Studio, cliquez sur le projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-116">In Visual Studio Solution Explorer, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ac71e-117">Dans le volet gauche, développez **propriétés communes**, puis cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-117">In the left pane, expand **Common Properties**, and then click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="ac71e-118">Dans le volet droit, faites défiler vers le **nom fort** boîte.</span><span class="sxs-lookup"><span data-stu-id="ac71e-118">In the right pane, scroll to the **Strong name** box.</span></span>  
  
7.  <span data-ttu-id="ac71e-119">Dans le **nom fort** , cliquez sur le champ à côté **fichier de clé d’Assembly**, cliquez sur le bouton Parcourir (**...** ), puis accédez au fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="ac71e-119">In the **Strong name** box, click the field next to **Assembly Key File**, click the browse button (**…**), and then browse to the key file.</span></span>  
  
8.  <span data-ttu-id="ac71e-120">Cliquez sur le fichier de clé, cliquez sur **ouvrir**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-120">Click the key file, click **Open**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="ac71e-121">Dans le menu Visual Studio, cliquez sur **générer**, puis choisissez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-121">On the Visual Studio menu, click **Build**, and then choose **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac71e-122">Si votre assembly d’adaptateur dépend des autres assemblys, assurez-vous de ces assemblys référencés sont signés avec un nom fort ; Sinon, vous obtiendrez une erreur.</span><span class="sxs-lookup"><span data-stu-id="ac71e-122">If your adapter assembly depends on any other assemblies, ensure these referenced assemblies are signed with a strong name; otherwise you will get an error.</span></span>  
  
 <span data-ttu-id="ac71e-123">Si vous disposez de la source, vous pouvez le recompiler avec un nom fort comme indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="ac71e-123">If you have the source, you can recompile with a strong name as shown previously.</span></span> <span data-ttu-id="ac71e-124">Si l’assembly de référence appartient à un tiers, et vous ne pouvez pas vous assurer qu’il a un nom fort, vous pouvez démonter et puis réassembler l’assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ac71e-124">If the reference assembly belongs to a third-party and you cannot ensure that it will be given a strong name, you can disassemble and then reassemble the assembly with a strong name.</span></span>  
  
 <span data-ttu-id="ac71e-125">Votre assembly d’origine sera remplacé, par conséquent, si vous souhaitez conserver la version d’origine, veillez à effectuer une copie de sauvegarde avant de procéder aux étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ac71e-125">Your original assembly will be overwritten, so if you want to keep the original version, ensure you make a backup copy of it before proceeding with the following steps.</span></span>  
  
 <span data-ttu-id="ac71e-126">Utilisez le désassembleur de langage MSIL (Microsoft Intermediate) pour désassembler l’assembly :</span><span class="sxs-lookup"><span data-stu-id="ac71e-126">Use Microsoft Intermediate Language (MSIL) Disassembler to disassemble the assembly:</span></span>  
  
-   <span data-ttu-id="ac71e-127">ILDASM thirdparty.dll /out:thirdparty.il</span><span class="sxs-lookup"><span data-stu-id="ac71e-127">ILDASM thirdparty.dll /out:thirdparty.il</span></span>  
  
 <span data-ttu-id="ac71e-128">Utilisez l’assembleur MSIL pour réassembler l’assembly avec un nom fort :</span><span class="sxs-lookup"><span data-stu-id="ac71e-128">Use MSIL Assembler to reassemble the assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="ac71e-129">ILASM thirdparty.il /dll /key=strongkeyfile.snk</span><span class="sxs-lookup"><span data-stu-id="ac71e-129">ILASM thirdparty.il /dll /key=strongkeyfile.snk</span></span>  
  
#### <a name="install-an-assembly-in-the-gac"></a><span data-ttu-id="ac71e-130">Installer un assembly dans le GAC</span><span class="sxs-lookup"><span data-stu-id="ac71e-130">Install an assembly in the GAC</span></span>  
  
1.  <span data-ttu-id="ac71e-131">Vérifiez que votre adaptateur a été signé.</span><span class="sxs-lookup"><span data-stu-id="ac71e-131">Verify that your adapter has been signed.</span></span>  
  
2.  <span data-ttu-id="ac71e-132">Ouvrir un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ac71e-132">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
3.  <span data-ttu-id="ac71e-133">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ac71e-133">Type the following command:</span></span>  
  
     <span data-ttu-id="ac71e-134">**Gacutil.exe /if «\<**  *chemin d’accès du fichier d’assembly .dll* **> »**</span><span class="sxs-lookup"><span data-stu-id="ac71e-134">**gacutil.exe /if "\<** *path to the assembly .dll file* **>"**</span></span>  
  
4.  <span data-ttu-id="ac71e-135">Cette procédure installe l'assembly dans le GAC, en remplaçant tout autre assembly existant sous le même nom.</span><span class="sxs-lookup"><span data-stu-id="ac71e-135">This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.</span></span>  
  
## <a name="register-the-adapter-in-machineconfig"></a><span data-ttu-id="ac71e-136">Inscrire l’adaptateur dans Machine.config</span><span class="sxs-lookup"><span data-stu-id="ac71e-136">Register the Adapter in Machine.config</span></span>  
 <span data-ttu-id="ac71e-137">Un adaptateur développées à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est présenté comme une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="ac71e-137">An adapter developed using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is surfaced as a WCF binding.</span></span>  <span data-ttu-id="ac71e-138">Pour plus d’informations, consultez Microsoft.ServiceModel.Channels.Common.AdapterBinding.</span><span class="sxs-lookup"><span data-stu-id="ac71e-138">See Microsoft.ServiceModel.Channels.Common.AdapterBinding for more information.</span></span>  <span data-ttu-id="ac71e-139">La liaison de l’adaptateur est inscrit avec WCF à l’aide de \<bindingExtensions > section \<système. ServiceModel > et l’élément de liaison de transport de l’adaptateur est enregistré avec WCF à l’aide de \<bindingElementExtensions > section \<système. ServiceModel >.</span><span class="sxs-lookup"><span data-stu-id="ac71e-139">The adapter binding is registered with WCF using \<bindingExtensions> section within \<system.ServiceModel> and the adapter transport binding element is registered with WCF using \<bindingElementExtensions> section within \<system.ServiceModel>.</span></span>  
  
 <span data-ttu-id="ac71e-140">Vous pouvez modifier manuellement le fichier machine.config à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="ac71e-140">You can manually edit the machine.config file using a text editor.</span></span>  
  
#### <a name="manually-edit-the-machineconfig-file"></a><span data-ttu-id="ac71e-141">Modifier manuellement le fichier machine.config</span><span class="sxs-lookup"><span data-stu-id="ac71e-141">Manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="ac71e-142">Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="ac71e-142">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="ac71e-143">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad \<Windows le chemin d’installation > \Microsoft.NET\Framework\\< version\>\CONFIG\machine.config, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-143">To do this, click **Start**, click **Run**, type notepad \<Windows install path>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ac71e-144">Mettre à jour le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ac71e-144">Update the machine.config file.</span></span> <span data-ttu-id="ac71e-145">Si le fichier ne contient pas de section system.serviceModel, ajoutez la section suivante à la fin du fichier de configuration, mais avant la fermeture de balise racine.</span><span class="sxs-lookup"><span data-stu-id="ac71e-145">If the file does not contain a system.serviceModel section, add the following section at the end of the configuration file but before the closing root tag.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac71e-146">Remplacez « myAdapterBinding », version, culture et autres informations spécifiques à l’assembly avec les informations de votre carte.</span><span class="sxs-lookup"><span data-stu-id="ac71e-146">Replace "myAdapterBinding", version, culture and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    \<system.serviceModel>  
      <extensions>  
        <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
        </bindingExtensions>      <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
      </extensions>  
    \</system.serviceModel>  
    ```  
  
     - <span data-ttu-id="ac71e-147">- OU -</span><span class="sxs-lookup"><span data-stu-id="ac71e-147">OR -</span></span>  
  
     <span data-ttu-id="ac71e-148">Si le fichier machine.config contient une section system.serviceModel, déterminer quels éléments sont manquants et les ajouter, en remplaçant « MyAdapter » et autres informations avec les informations de votre carte.</span><span class="sxs-lookup"><span data-stu-id="ac71e-148">If your machine.config file contains a system.serviceModel section, determine which elements are missing and add them, replacing "MyAdapter" and other information with your adapter's information.</span></span>  
  
    ```  
    <extensions>  
      <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
      </bindingExtensions>  
          <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
    </extensions>  
    ```  
  
3.  <span data-ttu-id="ac71e-149">Fermez et enregistrez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ac71e-149">Close and save the machine.config file.</span></span>  
  
 <span data-ttu-id="ac71e-150">Vous pouvez également utiliser le [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour modifier le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="ac71e-150">You can also use the [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) to modify the machine.config file.</span></span>
  
#### <a name="edit-the-machineconfig-file-using-the-service-configuration-editor"></a><span data-ttu-id="ac71e-151">Modifier le fichier machine.config à l’aide de l’éditeur de Configuration de Service</span><span class="sxs-lookup"><span data-stu-id="ac71e-151">Edit the machine.config file using the Service Configuration Editor</span></span>  
  
1.  <span data-ttu-id="ac71e-152">Ouvrez le **éditeur de Configuration de Service**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-152">Open the **Service Configuration Editor**.</span></span> <span data-ttu-id="ac71e-153">Consultez [éditeur de Configuration de Service](https://msdn.microsoft.com/library/ms732009.aspx) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ac71e-153">See [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) for  more information.</span></span>
  
2.  <span data-ttu-id="ac71e-154">Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds.</span><span class="sxs-lookup"><span data-stu-id="ac71e-154">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="ac71e-155">Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier et sélectionnez l’élément d’extensions de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac71e-155">Click the **Advanced** folder, click the **Extensions** folder, and then select the binding extensions element.</span></span>  
  
     <span data-ttu-id="ac71e-156">![Éditeur de configuration de service. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")</span><span class="sxs-lookup"><span data-stu-id="ac71e-156">![Service configuration editor.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")</span></span>  
  
3.  <span data-ttu-id="ac71e-157">Créer une nouvelle extension de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac71e-157">Create a new binding extension.</span></span> <span data-ttu-id="ac71e-158">Cliquez sur le **nouveau** bouton pour ouvrir l’Extension **Éditeur des éléments de Configuration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ac71e-158">Click the **New** button to open the Extension **Configuration Element Editor** dialog box.</span></span> <span data-ttu-id="ac71e-159">Dans **nom de la Configuration**, entrez un nom unique pour les extensions, par exemple *MyAdapterExtension*.</span><span class="sxs-lookup"><span data-stu-id="ac71e-159">In **Configuration Name**, enter a unique name for the extensions, for example *MyAdapterExtension*.</span></span>  
  
     <span data-ttu-id="ac71e-160">![Éditeur de configuration d’élément d’extension](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")</span><span class="sxs-lookup"><span data-stu-id="ac71e-160">![Extension configuration element editor](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")</span></span>  
  
4.  <span data-ttu-id="ac71e-161">Cliquez sur le **Type** champ, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la **Explorateur de types d’Extension de liaison** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ac71e-161">Click the **Type** field, and then click the ellipsis button (**...**) to open the **Binding Extension Type Browser** dialog box.</span></span>  
  
5.  <span data-ttu-id="ac71e-162">Cliquez sur global assembly cache (GAC) pour répertorier les DLL dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="ac71e-162">Click the global assembly cache (GAC) icon to list the DLLs in the GAC.</span></span>  
  
6.  <span data-ttu-id="ac71e-163">Cliquez sur votre assembly d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ac71e-163">Click your adapter assembly.</span></span>  
  
     <span data-ttu-id="ac71e-164">![Explorateur de types d’extension de génération. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")</span><span class="sxs-lookup"><span data-stu-id="ac71e-164">![Building extension type browser.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")</span></span>  
  
7.  <span data-ttu-id="ac71e-165">Cliquez sur le **ouvrir** pour sélectionner l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ac71e-165">Click the **Open** button to select the assembly.</span></span>  
  
8.  <span data-ttu-id="ac71e-166">Dans le **Explorateur de types d’Extension de liaison** boîte de dialogue, cliquez sur le nom de type qui implémente l’élément de collection de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac71e-166">In the **Binding Extension Type Browser** dialog box, click the type name that implements the binding collection element.</span></span>  
  
     <span data-ttu-id="ac71e-167">![Explorateur de types d’extension de génération. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")</span><span class="sxs-lookup"><span data-stu-id="ac71e-167">![Building extension type browser.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")</span></span>  
  
9. <span data-ttu-id="ac71e-168">Cliquez sur le **ouvrir** pour sélectionner le type.</span><span class="sxs-lookup"><span data-stu-id="ac71e-168">Click the **Open** button to select the type.</span></span>  
  
10. <span data-ttu-id="ac71e-169">Cliquez sur **OK** pour fermer la **éditeur de Configuration d’élément d’Extension** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ac71e-169">Click **OK** to close the **Extension Configuration Element Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="ac71e-170">Dans le volet détails de la **Éditeur d’Extensions de liaison**, vérifiez que votre extension de liaison s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ac71e-170">In the details pane of the **Binding Extensions Editor**, verify that your binding extension appears.</span></span> <span data-ttu-id="ac71e-171">Dans l’illustration suivante, MyAdapterExtension est mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="ac71e-171">In the following figure, MyAdapterExtension is highlighted.</span></span>  
  
     <span data-ttu-id="ac71e-172">![Éditeur de configuration de service avec ajout d’extension. ] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span><span class="sxs-lookup"><span data-stu-id="ac71e-172">![Service configuration editor with added extension.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span></span>  
  
12. <span data-ttu-id="ac71e-173">Fermer le **éditeur de Configuration de Service**.</span><span class="sxs-lookup"><span data-stu-id="ac71e-173">Close the **Service Configuration Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac71e-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac71e-174">See Also</span></span>  
 [<span data-ttu-id="ac71e-175">Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK</span><span class="sxs-lookup"><span data-stu-id="ac71e-175">Deploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)
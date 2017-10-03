---
title: "Fonctoid personnalisé (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, customizing
- examples, functoids
- functoids, examples
- XML tools
- examples, XML tools
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5117bed6ea1116047052359eadcd11754e9f85d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-functoid-biztalk-server-sample"></a><span data-ttu-id="4ffb6-102">Fonctoid personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="4ffb6-102">Custom Functoid (BizTalk Server Sample)</span></span>
<span data-ttu-id="4ffb6-103">L'exemple de fonctoid personnalisé montre comment écrire un fonctoid personnalisé pour le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-103">The Custom Functoid sample demonstrates how to write a custom functoid for BizTalk Mapper.</span></span> <span data-ttu-id="4ffb6-104">Vous pouvez ajouter le fonctoid à la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ffb6-104">You can add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span> <span data-ttu-id="4ffb6-105">Le fonctoid est affiché dans la boîte à outils lorsque le Mappeur BizTalk est actif.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-105">The functoid will be displayed in the Toolbox when BizTalk Mapper is in focus.</span></span>  
  
 <span data-ttu-id="4ffb6-106">Un fonctoid personnalisé doit résider dans un assembly du Mappeur BizTalk pour être reconnu.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-106">A custom functoid should reside in a BizTalk Mapper assembly to recognize it.</span></span> <span data-ttu-id="4ffb6-107">Il peut être écrit dans n'importe quel langage compatible .NET, tel que C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-107">It can be written in any .NET-compliant language, such as C# or Visual Basic.</span></span>  
  
 <span data-ttu-id="4ffb6-108">Par ailleurs, un fonctoid personnalisé doit dériver de la classe `Microsoft.BizTalk.BaseFunctoids` et fournir l'implémentation pour certaines méthodes en les remplaçant.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-108">Also, a custom functoid must derive from the `Microsoft.BizTalk.BaseFunctoids` class, and it must provide implementation for some methods by overriding them.</span></span> <span data-ttu-id="4ffb6-109">(La classe `BaseFunctoid` est définie dans l'assembly Microsoft.BizTalk.BaseFunctoids.dll inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="4ffb6-109">(The `BaseFunctoid` class is defined in the Microsoft.BizTalk.BaseFunctoids.dll assembly included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="4ffb6-110">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-110">What This Sample Does</span></span>  
 <span data-ttu-id="4ffb6-111">L'exemple de fonctoid personnalisé implémente plusieurs fonctoids qui dérivent de la classe `BaseFunctoid` et remplacent plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-111">The Custom Functoid sample implements several functoids, each deriving from the `BaseFunctoid` class and overriding several methods.</span></span>  
  
 <span data-ttu-id="4ffb6-112">Vous pouvez exposer le code Inline d'un fonctoid personnalisé lors de son implémentation.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-112">When implementing a custom functoid, you can expose its code inline.</span></span> <span data-ttu-id="4ffb6-113">Le code Inline exécute le calcul pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-113">The inline code is what performs the computation for the functoid.</span></span> <span data-ttu-id="4ffb6-114">Le compilateur du Mappeur BizTalk extrait le code Inline d'un fonctoid et l'intègre dans le XSLT compilé lors de la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-114">The BizTalk Mapper compiler extracts inline code from a functoid and embeds it in the compiled XSLT when you build the project.</span></span>  
  
 <span data-ttu-id="4ffb6-115">Si votre fonctoid personnalisé n'expose aucun code Inline, le Mappeur BizTalk génère le XSLT qui appelle l'assembly dans lequel réside le fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-115">If your custom functoid does not expose any inline code, BizTalk Mapper generates XSLT that calls into the assembly where the custom functoid resides.</span></span> <span data-ttu-id="4ffb6-116">Dans ce cas, vous devez vérifier que l'assembly de votre fonctoid personnalisé est disponible dans le Global Assembly Cache (GAC) afin que le moteur XSLT puisse le trouver.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-116">In this case, you must be sure your custom functoid assembly is available in the global assembly cache (GAC) so the XSLT engine can find it.</span></span> <span data-ttu-id="4ffb6-117">Un fonctoid personnalisé doit avoir également un attribut de GUID unique.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-117">A custom functoid must also have a unique GUID attribute.</span></span> <span data-ttu-id="4ffb6-118">Le Mappeur BizTalk utilise le GUID pour identifier l'assembly à charger.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-118">BizTalk Mapper uses the GUID to identify which assembly to load.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ffb6-119">Si vous réutilisez l'exemple de code de fonctoid personnalisé pour implémenter vos propres fonctoids, veillez à utiliser un attribut de GUID unique.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-119">If you reuse the Custom Functoid sample code to implement your own functoid(s), you must be sure to change the GUID attribute to one that is unique.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="4ffb6-120">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="4ffb6-121">*\<Exemples de chemin d’accès >*\XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="4ffb6-121">*\<Samples Path>*\XmlTools\CustomFunctoid</span></span>  
  
 <span data-ttu-id="4ffb6-122">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="4ffb6-123">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="4ffb6-123">File(s)</span></span>|<span data-ttu-id="4ffb6-124"> Description</span><span class="sxs-lookup"><span data-stu-id="4ffb6-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ffb6-125">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="4ffb6-125">AssemblyInfo.cs</span></span>|<span data-ttu-id="4ffb6-126">Code source C# d'informations de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-126">Assembly information C# source code.</span></span>|  
|<span data-ttu-id="4ffb6-127">CBuildArray.bmp</span><span class="sxs-lookup"><span data-stu-id="4ffb6-127">CBuildArray.bmp</span></span>|<span data-ttu-id="4ffb6-128">Bitmap de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-128">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="4ffb6-129">CConcat.bmp</span><span class="sxs-lookup"><span data-stu-id="4ffb6-129">CConcat.bmp</span></span>|<span data-ttu-id="4ffb6-130">Bitmap de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-130">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="4ffb6-131">CExtractArray.bmp</span><span class="sxs-lookup"><span data-stu-id="4ffb6-131">CExtractArray.bmp</span></span>|<span data-ttu-id="4ffb6-132">Bitmap de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-132">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="4ffb6-133">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="4ffb6-133">Cleanup.bat</span></span>|<span data-ttu-id="4ffb6-134">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC), ainsi que pour supprimer le fichier CustomFunctoid.dll.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-134">Used to undeploy assemblies and remove them from the global assembly cache (GAC) and to delete CustomFunctoid.dll.</span></span>|  
|<span data-ttu-id="4ffb6-135">CLongestString.bmp</span><span class="sxs-lookup"><span data-stu-id="4ffb6-135">CLongestString.bmp</span></span>|<span data-ttu-id="4ffb6-136">Bitmap de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-136">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="4ffb6-137">CMultiply.bmp</span><span class="sxs-lookup"><span data-stu-id="4ffb6-137">CMultiply.bmp</span></span>|<span data-ttu-id="4ffb6-138">Bitmap de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-138">Toolbox bitmap.</span></span>|  
|<span data-ttu-id="4ffb6-139">CustomFunctoid.cs</span><span class="sxs-lookup"><span data-stu-id="4ffb6-139">CustomFunctoid.cs</span></span>|<span data-ttu-id="4ffb6-140">Code source C# du fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-140">Custom functoid C# source code.</span></span>|  
|<span data-ttu-id="4ffb6-141">CustomFunctoid.csproj</span><span class="sxs-lookup"><span data-stu-id="4ffb6-141">CustomFunctoid.csproj</span></span>|<span data-ttu-id="4ffb6-142">Projet C# du fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-142">Custom functoid C# project.</span></span>|  
|<span data-ttu-id="4ffb6-143">CustomFunctoid.sln</span><span class="sxs-lookup"><span data-stu-id="4ffb6-143">CustomFunctoid.sln</span></span>|<span data-ttu-id="4ffb6-144">Solution du fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-144">Custom functoid solution.</span></span>|  
|<span data-ttu-id="4ffb6-145">CustomFunctoidResources.resx</span><span class="sxs-lookup"><span data-stu-id="4ffb6-145">CustomFunctoidResources.resx</span></span>|<span data-ttu-id="4ffb6-146">Ressources du fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-146">Custom functoid resources.</span></span>|  
|<span data-ttu-id="4ffb6-147">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="4ffb6-147">Setup.bat</span></span>|<span data-ttu-id="4ffb6-148">Utilisé pour créer, déployer et démarrer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-148">Used to build, deploy, and start the sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="4ffb6-149">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-149">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="4ffb6-150">La procédure suivante permet de créer et d'initialiser l'exemple de fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-150">Use the following procedure to build and initialize the Custom Functoid sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="4ffb6-151">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-151">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="4ffb6-152">Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-152">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="4ffb6-153">\<*Exemples de chemin d’accès*> \XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="4ffb6-153">\<*Samples Path*>\XmlTools\CustomFunctoid</span></span>  
  
2.  <span data-ttu-id="4ffb6-154">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-154">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="4ffb6-155">création de l'exemple de projet ;</span><span class="sxs-lookup"><span data-stu-id="4ffb6-155">Builds the sample project.</span></span>  
  
    -   <span data-ttu-id="4ffb6-156">copie de l'assembly généré dans le répertoire Developer Tools\Mapper Extensions ;</span><span class="sxs-lookup"><span data-stu-id="4ffb6-156">Copies the generated assembly to the Developer Tools\Mapper Extensions directory.</span></span>  
  
    -   <span data-ttu-id="4ffb6-157">ajout de l'assembly généré au GAC.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-157">Adds the generated assembly to the GAC.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4ffb6-158">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-158">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="4ffb6-159">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="4ffb6-159">Running This Sample</span></span>  
 <span data-ttu-id="4ffb6-160">La procédure suivante permet d'exécuter l'exemple de fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-160">Use the following procedure to run the Custom Functoid sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="4ffb6-161">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-161">To run this sample</span></span>  
  
1.  <span data-ttu-id="4ffb6-162">À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **outils** , puis sélectionnez **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-162">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.</span></span>  
  
2.  <span data-ttu-id="4ffb6-163">Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, sélectionnez le **fonctoids du Mappeur BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-163">In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.</span></span>  
  
3.  <span data-ttu-id="4ffb6-164">Cliquez sur **réinitialiser**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-164">Click **Reset**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ffb6-165">Si votre fonctoid personnalisé n'expose aucun code Inline, vérifiez que son assembly est disponible dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-165">If your custom functoid does not expose any inline code, make sure its assembly is made available in the GAC.</span></span>  
  
4.  <span data-ttu-id="4ffb6-166">À partir de la **fichier** menu, sélectionnez **Exit** pour fermer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ffb6-166">From the **File** menu, select **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="4ffb6-167">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-167">Start **Visual Studio Command Prompt**.</span></span>  
  
6.  <span data-ttu-id="4ffb6-168">À l’invite de commandes, tapez **devenv /setup**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-168">At the command prompt, type **devenv /setup**.</span></span>  
  
7.  <span data-ttu-id="4ffb6-169">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-169">Start **Microsoft Visual Studio**.</span></span>  
  
     <span data-ttu-id="4ffb6-170">Personnalisé fonctoids (fonctoid concaténation personnalisé, chaîne la plus longue, Build tableau fonctoid et tableau fonctoid) s’affichent sur le **fonctoids de chaîne** onglet de la boîte à outils et le fonctoid Multiplication Cumulative apparaît sur le **Fonctoids cumulés** onglet.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-170">The custom functoids (Custom concatenate functoid, Longest String, Build array functoid, and Extract array functoid) appear on the **String Functoids** tab of the Toolbox, and the Cumulative Multiply functoid appears on the **Cumulative Functoids** tab.</span></span>  
  
## <a name="removing-this-sample"></a><span data-ttu-id="4ffb6-171">Suppression de cet exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-171">Removing This Sample</span></span>  
 <span data-ttu-id="4ffb6-172">La procédure suivante permet de supprimer l'exemple de fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-172">Use the following procedure to remove the Custom Functoid sample.</span></span>  
  
#### <a name="to-remove-this-sample"></a><span data-ttu-id="4ffb6-173">Pour supprimer cet exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-173">To remove this sample</span></span>  
  
1.  <span data-ttu-id="4ffb6-174">Supprimez les fonctoids de la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ffb6-174">Remove the functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="4ffb6-175">Si, après l'exécution de Cleanup.bat, les fonctoids personnalisés obsolètes apparaissent toujours dans la boîte à outils (ce qui peut tenir à une mise en cache interne dans Visual Studio), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-175">If after running Cleanup.bat, you still see the stale custom functoids in the toolbox (probably due to internal caching by Visual Studio), then follow the procedures below:</span></span>  
  
    1.  <span data-ttu-id="4ffb6-176">À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **outils** , puis sélectionnez **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-176">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="4ffb6-177">Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, sélectionnez le **fonctoids du Mappeur BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-177">In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.</span></span>  
  
    3.  <span data-ttu-id="4ffb6-178">Recherchez les fonctoids personnalisés (fonctoids personnalisés de concaténation, de chaîne la plus longue, de création de tableau, d'extraction de tableau et de multiplication cumulative) dans la liste.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-178">Find the custom functoids (Custom concatenate functoid, Longest String, Build array functoid, Extract array functoid, and Cumulative Multiply) in the list.</span></span> <span data-ttu-id="4ffb6-179">Cliquez sur la **case à cocher** à supprimer les fonctoids, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-179">Click the respective **check box** to remove the functoids, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4ffb6-180">Si le problème persiste, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-180">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="4ffb6-181">À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **boîte à outils** onglet lors de la modification d’un mappage pour afficher la Palette de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-181">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab while editing a map to bring up the Toolbox Palette.</span></span>  
  
    2.  <span data-ttu-id="4ffb6-182">Avec le bouton droit de la boîte à outils et sélectionnez **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-182">Right-click the tool box and select **Choose Items**.</span></span>  
  
    3.  <span data-ttu-id="4ffb6-183">Dans la boîte de dialogue Choisir des éléments, cliquez sur **réinitialiser**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-183">In the Choose Items dialog box, click **Reset**, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="4ffb6-184">Fermez toutes les instances de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ffb6-184">Close all instances of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
     <span data-ttu-id="4ffb6-185">Si le problème persiste, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-185">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="4ffb6-186">Démarrer **invite de commandes Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-186">Start **Visual Studio Command Prompt** as an administrator.</span></span>  
  
    2.  <span data-ttu-id="4ffb6-187">Fermez toutes les instances de Visual Studio en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-187">Close all the running instances of Visual Studio.</span></span>  
  
    3.  <span data-ttu-id="4ffb6-188">Exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-188">Give the following commands:</span></span>  
  
         `devenv /resetsettings`  
  
         `devenv /setup`  
  
    4.  <span data-ttu-id="4ffb6-189">Vous pouvez sélectionner manuellement les fonctoids indésirables dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-189">You can manually select the unwanted functoids from the toolbox.</span></span> <span data-ttu-id="4ffb6-190">Ensuite, cliquez avec le bouton droit sur le fonctoid, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-190">Then, right click the functoid, and click **Delete**.</span></span>  
  
     <span data-ttu-id="4ffb6-191">Si le problème persiste, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-191">If the above procedure does not work, follow the below procedure.</span></span>  
  
    1.  <span data-ttu-id="4ffb6-192">Dans un projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], cliquez sur l'onglet Boîte à outils lors de la modification d'un mappage pour afficher la palette de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-192">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the Toolbox tab while editing a map to bring up the Toolbox Palette.</span></span>  
  
    2.  <span data-ttu-id="4ffb6-193">Cliquez sur le **fonctoids cumulés** groupe.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-193">Click the **Cumulative Functoids** group.</span></span>  
  
    3.  <span data-ttu-id="4ffb6-194">Cliquez avec le bouton droit sur le fonctoid que vous souhaitez supprimer, puis choisissez **supprimer** ou appuyez sur la touche SUPPR.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-194">Right click the functoid you want to remove and then choose **Delete** or press the delete key.</span></span>  
  
    4.  <span data-ttu-id="4ffb6-195">Cliquez sur le **fonctoids de chaîne** groupe.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-195">Click the **String Functoids** group.</span></span>  
  
    5.  <span data-ttu-id="4ffb6-196">Cliquez avec le bouton droit sur le fonctoid que vous souhaitez supprimer, puis choisissez **supprimer** ou appuyez sur la touche SUPPR.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-196">Right click the functoid you want to remove and then choose **Delete** or press the delete key.</span></span>  
  
2.  <span data-ttu-id="4ffb6-197">Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-197">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="4ffb6-198">\<*Exemples de chemin d’accès*> \XmlTools\CustomFunctoid</span><span class="sxs-lookup"><span data-stu-id="4ffb6-198">\<*Samples Path*>\XmlTools\CustomFunctoid</span></span>  
  
3.  <span data-ttu-id="4ffb6-199">Exécutez le fichier Cleanup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ffb6-199">Run the file Cleanup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="4ffb6-200">suppression de l'assembly du répertoire Developer Tools\Mapper Extensions ;</span><span class="sxs-lookup"><span data-stu-id="4ffb6-200">Deletes the assembly from the Developer Tools\Mapper Extensions directory.</span></span>  
  
    -   <span data-ttu-id="4ffb6-201">suppression de l'assembly du GAC.</span><span class="sxs-lookup"><span data-stu-id="4ffb6-201">Removes the assembly from the GAC.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="4ffb6-202">Classes ou méthodes utilisées dans l'exemple</span><span class="sxs-lookup"><span data-stu-id="4ffb6-202">Classes or Methods Used in This Sample</span></span>  
 [<span data-ttu-id="4ffb6-203">Microsoft.BizTalk.BaseFunctoids.BaseFunctoid</span><span class="sxs-lookup"><span data-stu-id="4ffb6-203">Microsoft.BizTalk.BaseFunctoids.BaseFunctoid</span></span>](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="4ffb6-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ffb6-204">See Also</span></span>  
 <span data-ttu-id="4ffb6-205">[Utilisation de BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="4ffb6-205">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 [<span data-ttu-id="4ffb6-206">Outils XML (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="4ffb6-206">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)
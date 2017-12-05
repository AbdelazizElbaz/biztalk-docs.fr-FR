---
title: "Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28f798cc-da97-4332-a842-ba87ac7b13b8
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 955c526c39a1cbb376a0d83848554bdeb6cc15c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="adding-and-removing-custom-functoids-from-the-visual-studio-toolbox"></a><span data-ttu-id="1cc16-102">Ajout et suppression de fonctoids personnalisés dans la boîte à outils de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1cc16-102">Adding and Removing Custom Functoids from the Visual Studio Toolbox</span></span>
<span data-ttu-id="1cc16-103">Cette rubrique décrit l'ajout et la suppression des fonctoids personnalisés dans la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cc16-103">This topic describes how to add custom functoids to and remove custom functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
## <a name="adding-custom-functoids-to-visual-studio"></a><span data-ttu-id="1cc16-104">Ajout de fonctoids personnalisés à Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1cc16-104">Adding Custom Functoids to Visual Studio</span></span>  
 <span data-ttu-id="1cc16-105">Pour pouvoir utiliser des fonctoids personnalisés dans un mappage, vous devez les avoir préalablement ajoutés dans la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cc16-105">Custom functoids must be added to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox before they can be used in a map.</span></span> <span data-ttu-id="1cc16-106">La procédure suivante permet d'ajouter des fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1cc16-106">Use the following procedure to add custom functoids.</span></span>  
  
#### <a name="to-add-a-custom-functoid"></a><span data-ttu-id="1cc16-107">Pour ajouter un fonctoid personnalisé</span><span class="sxs-lookup"><span data-stu-id="1cc16-107">To add a custom functoid</span></span>  
  
1.  <span data-ttu-id="1cc16-108">Ajoutez le fonctoid à la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cc16-108">Add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
    1.  <span data-ttu-id="1cc16-109">À l'aide de l'Explorateur Windows, recherchez l'assembly qui implémente vos fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1cc16-109">Using Windows Explorer, find the assembly that implements your custom functoids.</span></span>  
  
    2.  <span data-ttu-id="1cc16-110">Copiez l’assembly dans le \< *dossier d’installation de BizTalk Server*\>**\Developer Tools\Mapper Extensions** active.</span><span class="sxs-lookup"><span data-stu-id="1cc16-110">Copy the assembly to the \<*BizTalk Server installation folder*\>**\Developer Tools\Mapper Extensions** directory.</span></span> <span data-ttu-id="1cc16-111">Le Mappeur BizTalk recherche les fonctoids personnalisés dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="1cc16-111">This is where BizTalk Mapper looks for custom functoids.</span></span>  
  
    3.  <span data-ttu-id="1cc16-112">À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-112">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    4.  <span data-ttu-id="1cc16-113">Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="1cc16-113">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
    5.  <span data-ttu-id="1cc16-114">Cliquez sur **réinitialiser**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-114">Click **Reset**, and then click **OK**.</span></span> <span data-ttu-id="1cc16-115">Ce processus peut prendre quelques instants.</span><span class="sxs-lookup"><span data-stu-id="1cc16-115">This process may take a few moments.</span></span>  
  
         <span data-ttu-id="1cc16-116">Vos fonctoids personnalisés doivent maintenant apparaître dans la boîte à outils sous les onglets correspondant à leur catégorie.</span><span class="sxs-lookup"><span data-stu-id="1cc16-116">Your custom functoids should now appear in the Toolbox under tabs matching their category.</span></span>  
  
     <span data-ttu-id="1cc16-117">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="1cc16-117">\- OR -</span></span>  
  
    1.  <span data-ttu-id="1cc16-118">À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-118">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="1cc16-119">Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="1cc16-119">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
    3.  <span data-ttu-id="1cc16-120">Cliquez sur **réinitialiser**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-120">Click **Reset**, and then click **OK**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="1cc16-121">Si votre fonctoid personnalisé n'expose aucun code Inline, vérifiez que son assembly est disponible dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1cc16-121">If your custom functoid does not expose any inline code, make sure its assembly is made available in the global assembly cache.</span></span>  
  
    4.  <span data-ttu-id="1cc16-122">Sur le **fichier** menu, cliquez sur **Exit** pour fermer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cc16-122">On the **File** menu, click **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    5.  <span data-ttu-id="1cc16-123">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-123">Start **Visual Studio Command Prompt**.</span></span>  
  
    6.  <span data-ttu-id="1cc16-124">À l’invite de commandes, tapez **devenv /setup**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-124">At the command prompt, type **devenv /setup**.</span></span>  
  
    7.  <span data-ttu-id="1cc16-125">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-125">Start **Microsoft Visual Studio**.</span></span>  
  
         <span data-ttu-id="1cc16-126">Le ou les fonctoids personnalisés doivent apparaître sous l'onglet approprié.</span><span class="sxs-lookup"><span data-stu-id="1cc16-126">The custom functoid(s) should appear in the appropriate tab.</span></span>  
  
2.  <span data-ttu-id="1cc16-127">Ajoutez l'assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1cc16-127">Add the assembly to the global assembly cache.</span></span> <span data-ttu-id="1cc16-128">Si votre assembly contient uniquement des fonctoids Inline, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="1cc16-128">If your assembly contains only inline functoids, then you can skip this step.</span></span>  
  
    1.  <span data-ttu-id="1cc16-129">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-129">Start **Visual Studio Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="1cc16-130">Placez-vous dans le dossier contenant votre assembly.</span><span class="sxs-lookup"><span data-stu-id="1cc16-130">Switch to the folder containing your assembly.</span></span>  
  
    3.  <span data-ttu-id="1cc16-131">À l’invite de commandes, tapez **gacutil /if < assembly_path >**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-131">At the command prompt, type **gacutil /if <assembly_path >**.</span></span> <span data-ttu-id="1cc16-132">Par exemple, si votre nom de l’assembly est FunctoidLibrary.dll, tapez **gacutil /if FunctoidLibrary.dll**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-132">For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary.dll**.</span></span>  
  
    4.  <span data-ttu-id="1cc16-133">Lorsque vous avez terminé, tapez **quitter**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-133">When you are finished, type **exit**.</span></span>  
  
## <a name="removing-custom-functoids-from-visual-studio"></a><span data-ttu-id="1cc16-134">Suppression de fonctoids personnalisés de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1cc16-134">Removing Custom Functoids from Visual Studio</span></span>  
 <span data-ttu-id="1cc16-135">La procédure suivante permet de supprimer des fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1cc16-135">Use the following procedure to remove custom functoids.</span></span>  
  
#### <a name="to-remove-a-custom-functoid"></a><span data-ttu-id="1cc16-136">Pour supprimer un fonctoid personnalisé</span><span class="sxs-lookup"><span data-stu-id="1cc16-136">To remove a custom functoid</span></span>  
  
1.  <span data-ttu-id="1cc16-137">Supprimez le fonctoid à partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="1cc16-137">Remove the functoid from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
    1.  <span data-ttu-id="1cc16-138">À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-138">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
    2.  <span data-ttu-id="1cc16-139">Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="1cc16-139">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
    3.  <span data-ttu-id="1cc16-140">Recherchez le fonctoid personnalisé dans la liste, sélectionnez le **supprimer** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-140">Find the custom functoid in the list, select the **Remove** check box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1cc16-141">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="1cc16-141">\- OR -</span></span>  
  
    1.  <span data-ttu-id="1cc16-142">Lors de la modification d’un mappage dans un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **boîte à outils** onglet pour afficher la palette de boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="1cc16-142">While editing a map in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab to bring up the Toolbox Palette.</span></span>  
  
    2.  <span data-ttu-id="1cc16-143">Cliquez sur le groupe de fonctoids contenant votre fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1cc16-143">Click the functoid group containing your custom functoid.</span></span>  
  
    3.  <span data-ttu-id="1cc16-144">Cliquez sur le fonctoid que vous souhaitez supprimer, puis cliquez sur **supprimer** ou appuyez sur la touche SUPPR.</span><span class="sxs-lookup"><span data-stu-id="1cc16-144">Right-click the functoid you want to remove, and then click **Delete** or press the delete key.</span></span>  
  
2.  <span data-ttu-id="1cc16-145">Supprimez l’assembly fonctoid à partir de la **Developer Tools\Mapper Extensions** active.</span><span class="sxs-lookup"><span data-stu-id="1cc16-145">Remove the functoid assembly from the **Developer Tools\Mapper Extensions** directory.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="1cc16-146">Si un assembly contient des fonctoids actifs, ne le supprimez pas.</span><span class="sxs-lookup"><span data-stu-id="1cc16-146">If an assembly contains active functoids, then do not remove it.</span></span> <span data-ttu-id="1cc16-147">Vous risqueriez de supprimer d'autres mappages.</span><span class="sxs-lookup"><span data-stu-id="1cc16-147">Doing so will break other maps.</span></span>  
  
    1.  <span data-ttu-id="1cc16-148">Démarrez l’Explorateur Windows et accédez à la **Developer Tools\Mapper Extensions** de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cc16-148">Start Windows Explorer and navigate to the **Developer Tools\Mapper Extensions** directory of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="1cc16-149">Avec le bouton droit de l’assembly contenant le fonctoid supprimé, puis cliquez sur **supprimer** pour supprimer le fichier.</span><span class="sxs-lookup"><span data-stu-id="1cc16-149">Right-click the assembly containing the removed functoid, and then click **Delete** to remove the file.</span></span>  
  
3.  <span data-ttu-id="1cc16-150">Supprimez l'assembly du fonctoid du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1cc16-150">Remove the functoid assembly from the global assembly cache.</span></span> <span data-ttu-id="1cc16-151">Si votre assembly contient uniquement des fonctoids Inline, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="1cc16-151">If your assembly contains only inline functoids, then you can skip this step.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="1cc16-152">Si un assembly contient des fonctoids actifs, ne le supprimez pas du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="1cc16-152">If an assembly contains active functoids, then do not remove it from the global assembly cache.</span></span> <span data-ttu-id="1cc16-153">Vous risqueriez de supprimer d'autres mappages.</span><span class="sxs-lookup"><span data-stu-id="1cc16-153">Doing so will break other maps.</span></span>  
  
    1.  <span data-ttu-id="1cc16-154">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-154">Start **Visual Studio Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="1cc16-155">À l’invite de commandes, tapez **gacutil /u < assembly_display_name >**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-155">At the command prompt, type **gacutil /u <assembly_display_name>**.</span></span> <span data-ttu-id="1cc16-156">Par exemple, si votre nom de l’assembly est FunctoidLibrary.dll, tapez **gacutil /if FunctoidLibrary**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-156">For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary**.</span></span>  
  
    3.  <span data-ttu-id="1cc16-157">Lorsque vous avez terminé, tapez **quitter**.</span><span class="sxs-lookup"><span data-stu-id="1cc16-157">When you are finished, type **exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc16-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cc16-158">See Also</span></span>  
 [<span data-ttu-id="1cc16-159">Développement de fonctoids personnalisés</span><span class="sxs-lookup"><span data-stu-id="1cc16-159">Developing Custom Functoids</span></span>](../core/developing-custom-functoids.md)
---
title: "Comment ajouter des fonctoids de script à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.functiod.script
ms.assetid: eb96814a-b3fb-48f6-a947-ab595a270faa
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e66e6ed25fd44b1e89fe5500346a7ad01d5d7ff0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-scripting-functoids-to-a-map"></a><span data-ttu-id="91250-102">Ajout de fonctoids Script à un mappage</span><span class="sxs-lookup"><span data-stu-id="91250-102">How to Add Scripting Functoids to a Map</span></span>
<span data-ttu-id="91250-103">Le **script** fonctoid permet d’utiliser le script personnalisé ou un code en cours d’exécution pour exécuter des fonctions non disponibles.</span><span class="sxs-lookup"><span data-stu-id="91250-103">The **Scripting** functoid enables you to use custom script or code at run time to perform functions otherwise not available.</span></span> <span data-ttu-id="91250-104">Par exemple, vous pouvez appeler un objet COM en cours d’exécution à l’aide de la **script** fonctoid et l’écriture de votre propre script personnalisé.</span><span class="sxs-lookup"><span data-stu-id="91250-104">For example, you can call a COM object at run time by using the **Scripting** functoid and writing your own custom script.</span></span>  
  
 <span data-ttu-id="91250-105">Pour obtenir des informations conceptuelles sur le **script** fonctoid, consultez [le fonctoid script](../core/scripting-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="91250-105">For conceptual information about the **Scripting** functoid, see [Scripting Functoid](../core/scripting-functoid.md).</span></span>  
  
### <a name="to-add-the-scripting-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="91250-106">Pour ajouter le fonctoid Script à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="91250-106">To add the Scripting functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="91250-107">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="91250-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="91250-108">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="91250-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="91250-109">Faites glisser le **script** fonctoid ![](../core/media/bts-tls-scripting.gif "bts_tls_scripting") à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="91250-109">Drag the **Scripting** functoid ![](../core/media/bts-tls-scripting.gif "bts_tls_scripting") from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-110">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="91250-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="91250-111">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="91250-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-112">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur emplacement relatif de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="91250-112">If you are constructing a map using more than one functoid together, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="91250-113">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="91250-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="91250-114">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="91250-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="91250-115">Sélectionnez le **script** fonctoid que vous venez d’ajouter à la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="91250-115">Select the **Scripting** functoid that you just added to the displayed grid page.</span></span>  
  
4.  <span data-ttu-id="91250-116">Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) associés à la **Script** propriété.</span><span class="sxs-lookup"><span data-stu-id="91250-116">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, click the ellipsis (**...**) button associated with the **Script** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-117">Ou bien, cliquez sur le fonctoid, puis cliquez sur **configurer le Script du fonctoid** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="91250-117">Alternatively, you can right-click the functoid, and then click **Configure Functoid Script** in the context menu.</span></span> <span data-ttu-id="91250-118">Le **configurer le fonctoid script** boîte de dialogue s’affiche avec le **Configuration du fonctoid Script** onglet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="91250-118">The **Configure Scripting Functoid** dialog box appears with the **Script Functoid Configuration** tab selected.</span></span>  
  
5.  <span data-ttu-id="91250-119">Dans le **configurer le fonctoid script** boîte de dialogue le **sélectionner le type de script** liste déroulante, sélectionnez le type de votre script.</span><span class="sxs-lookup"><span data-stu-id="91250-119">In the **Configure Scripting Functoid** dialog box, in the **Select script type** drop-down list, select the type of your script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-120">Selon votre sélection, différents sous-ensembles des autres champs de la boîte de dialogue seront activés et désactivés.</span><span class="sxs-lookup"><span data-stu-id="91250-120">Depending on your selection of script type, different subsets of the remaining dialog box fields will be enabled and disabled.</span></span>  
  
6.  <span data-ttu-id="91250-121">Si vous avez sélectionné **Assembly externe** comme type de script, utilisez la **Script de l’assembly**, **Script classe**, et **méthode de Script** liste déroulante listes, dans cet ordre, pour sélectionner l’assembly, la classe et la méthode, respectivement, à associer à ce **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="91250-121">If you selected **External Assembly** as the script type, use the **Script assembly**, **Script class**, and **Script method** drop-down lists, in that order, to select the assembly, class, and method, respectively, to associate with this **Scripting** functoid.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="91250-122">Le code contenu dans l’assembly externe doit être exempt de tout thread.</span><span class="sxs-lookup"><span data-stu-id="91250-122">The code in the external assembly must be thread-safe.</span></span> <span data-ttu-id="91250-123">Dans les situations de forte charge, il est possible d’exécuter plusieurs instances d’un mappage en même temps.</span><span class="sxs-lookup"><span data-stu-id="91250-123">Under stress conditions, multiple instances of a map may be running concurrently.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-124">Après avoir sélectionné un assembly, le **Script classe** liste de déroulante sera remplie avec les classes de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="91250-124">After you have selected an assembly, the **Script class** drop-down list will be populated with the classes in that assembly.</span></span> <span data-ttu-id="91250-125">De même, après avoir sélectionné une classe, le **méthode de Script** liste de déroulante sera remplie avec les méthodes de cette classe.</span><span class="sxs-lookup"><span data-stu-id="91250-125">Likewise, after you have selected a class, the **Script method** drop-down list will be populated with the methods in that class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-126">Le **script Inline** zone de texte est désactivée lorsque vous sélectionnez **Assembly externe** comme type de script.</span><span class="sxs-lookup"><span data-stu-id="91250-126">The **Inline script** text box is disabled when you select **External Assembly** as the script type.</span></span>  
  
     <span data-ttu-id="91250-127">Si vous avez sélectionné un élément autre que **Assembly externe** comme type de script (une des options inline), utilisez la **script Inline** zone de texte pour entrer votre script dans la langue sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="91250-127">If you selected something other than **External Assembly** as the script type (one of the inline choices), use the **Inline script** text box to enter your script in the language you selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-128">Les options de langage inline pour la **script** fonctoid incluent Visual C# .NET, JScript.NET, Visual Basic .NET, XSLT et le modèle d’appel XSLT.</span><span class="sxs-lookup"><span data-stu-id="91250-128">The inline language choices for the **Scripting** functoid include C# .NET, JScript.NET, Visual Basic .NET, XSLT, and XSLT Call Template.</span></span>  
  
     <span data-ttu-id="91250-129">La création de scripts à l'aide du langage C# n'autorise pas les instructions « using ».</span><span class="sxs-lookup"><span data-stu-id="91250-129">Scripting using C# does not allow "using" statements.</span></span> <span data-ttu-id="91250-130">Si le script doit utiliser des classes .Net spéciales, les assemblys correspondants et leurs dépendances doivent être ajoutés aux « Références » du projet BizTalk ; en outre, le code de script doit utiliser des noms complets.</span><span class="sxs-lookup"><span data-stu-id="91250-130">If the script needs to use any special .Net classes, then the corresponding assemblies and their dependent assemblies should be added to "References" in the BizTalk project, and the script code should use fully qualified names.</span></span> <span data-ttu-id="91250-131">Si vous écrivez un script pour effectuer une conversion en minuscules sensible à la culture, le fragment de code correspondant doit être écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="91250-131">If you write a script to perform culture-sensitive lowercase conversion, the corresponding code fragment should be written as below.</span></span> <span data-ttu-id="91250-132">Des restrictions similaires s'appliquent à tous les langages de création de scripts pris en charge.</span><span class="sxs-lookup"><span data-stu-id="91250-132">Similar limitations apply to all supported scripting languages.</span></span>  
  
    ```  
    string x = y.ToLower(System.Globalization.CultureInfo.CurrentCulture);  
    ```  
  
     <span data-ttu-id="91250-133">Pour utiliser les classes d'un assembly dans le script, assurez-vous d'ajouter l'assembly correspondant et ses dépendances aux « Références » du projet BizTalk contenant votre mappage.</span><span class="sxs-lookup"><span data-stu-id="91250-133">In the script, to use classes from any assembly, ensure you add the corresponding assembly and its dependent assemblies to “References” in the BizTalk project containing your map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-134">Vous pouvez créer votre script personnalisé directement dans le **script Inline** zone de texte, ou vous pouvez créer votre script ailleurs et le coller dans le **script Inline** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="91250-134">You can create your custom script directly in the **Inline script** text box, or you can create your script elsewhere, and paste it into the **Inline script** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91250-135">Le **Script de l’assembly**, **Script classe**, et **méthode de Script** listes déroulantes sont désactivées lorsque vous sélectionnez une des options inline (quelque chose que **Assembly externe**) comme type de script.</span><span class="sxs-lookup"><span data-stu-id="91250-135">The **Script assembly**, **Script class**, and **Script method** drop-down lists are disabled when you select one of the inline choices (something other than **External Assembly**) as the script type.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="91250-136">Si vous créez un script contenant plusieurs fonctions, la première fonction sera considérée comme fonction principale, tandis que les autres sont uniquement appelées dans l’exécution de la fonction principale.</span><span class="sxs-lookup"><span data-stu-id="91250-136">If you create a script containing multiple functions, the first function will be treated as the main or primary function; other functions are only called if they are called in the execution of the primary function.</span></span>  
  
     <span data-ttu-id="91250-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91250-137">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="91250-138">Si votre script ou la méthode associée d’un assembly externe requiert des paramètres d’entrée, créez le nombre et le type appropriés de liens d’entrée comme pour un fonctoid de base.</span><span class="sxs-lookup"><span data-stu-id="91250-138">If your script or the associated method in an external assembly requires input parameters, create the appropriate number and type of input links as you would for a basic functoid.</span></span>  
  
8.  <span data-ttu-id="91250-139">Dans la plupart des cas, votre **script** fonctoid produira une valeur de sortie utilisée pour remplir un champ du schéma de destination ou en tant qu’entrée à un autre fonctoid, à peu près la même façon que les fonctoids. procédez.</span><span class="sxs-lookup"><span data-stu-id="91250-139">In most circumstances, your **Scripting** functoid will produce an output value used to populate a field in the destination schema, or as input to another functoid, in much the same way that basic functoids do.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91250-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91250-140">See Also</span></span>  
 [<span data-ttu-id="91250-141">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="91250-141">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
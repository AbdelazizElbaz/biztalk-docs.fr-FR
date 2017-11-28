---
title: "Comment ajouter des fonctoids déclarer à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdd79a2-b70f-489b-8711-e00a50d8e2d8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 553daa0c6e97d09e8284d2369e801c5d2ff8beee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-assert-functoids-to-a-map"></a><span data-ttu-id="36403-102">Ajout de fonctoids Déclarer à un mappage</span><span class="sxs-lookup"><span data-stu-id="36403-102">How to Add Assert Functoids to a Map</span></span>
<span data-ttu-id="36403-103">Le **Assert** fonctoid permet de tester vos hypothèses sur les conditions de votre mappage.</span><span class="sxs-lookup"><span data-stu-id="36403-103">The **Assert** functoid enables you to test your assumptions about conditions in your map.</span></span> <span data-ttu-id="36403-104">Par exemple, si vous effectuez des calculs pour déterminer une remise supplémentaire sur les achats de produits, vous pouvez déclarer que la remise supplémentaire soit pas plus de 100 $ à l’aide d’un fonctoid logique (**supérieur à** ou  **Less than**).</span><span class="sxs-lookup"><span data-stu-id="36403-104">For example, if you perform some calculations to determine an additional discount on product purchases, you might assert that the additional discount be no more than $100 by using a logical functoid (**Greater Than** or **Less Than**).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36403-105">Le **Assert** fonctoid se déclenche uniquement dans les versions de développement ou lorsque le **générer des informations de débogage** dans les paramètres de génération de projet est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="36403-105">The **Assert** functoid only fires in development builds or when the **Generate Debugging Information** property in the project build settings is set to **True**.</span></span> <span data-ttu-id="36403-106">Lorsque votre application BizTalk est compilée pour le déploiement et la **générer des informations de débogage** est définie sur **False** (la valeur par défaut), déclarations sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="36403-106">When your BizTalk application is compiled for deployment and the **Generate Debugging Information** property is set to **False** (the default), assertions are ignored.</span></span>  
  
 <span data-ttu-id="36403-107">Pour obtenir des informations conceptuelles sur le **Assert** fonctoid, consultez [déclarer un fonctoid](../core/assert-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="36403-107">For conceptual information about the **Assert** functoid, see [Assert Functoid](../core/assert-functoid.md).</span></span>  
  
## <a name="add-the-assert-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="36403-108">Ajouter le fonctoid déclarer à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="36403-108">Add the Assert functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="36403-109">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="36403-109">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span> <span data-ttu-id="36403-110">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="36403-110">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="36403-111">Faites glisser le **Assert** fonctoid (![fonctoid déclarer](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="36403-111">Drag the **Assert** functoid (![Assert functoid](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36403-112">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="36403-112">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="36403-113">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="36403-113">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span> 
    >    
    >  <span data-ttu-id="36403-114">Si vous construisez un mappage impliquant plusieurs fonctoids, vous devez tenir compte de leur placement relatif de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="36403-114">If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="36403-115">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="36403-115">Functoids are executed from left to right.</span></span> <span data-ttu-id="36403-116">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="36403-116">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="36403-117">Le fonctoid doit posséder exactement trois paramètres d'entrée et génère un unique paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="36403-117">The functoid must have exactly three input parameters and it generates one output parameter.</span></span> <span data-ttu-id="36403-118">Pour établir le premier paramètre pour le **Assert** fonctoid, créez un lien d’entrée en faisant glisser la sortie à partir d’autres **logiques** fonctoid ou à partir d’un champ de variable booléen dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="36403-118">To establish the first parameter for the **Assert** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.</span></span>  
  
4.  <span data-ttu-id="36403-119">Pour établir le deuxième paramètre d’entrée pour le **Assert** fonctoid, créez un lien d’entrée en un nœud de champ du schéma source vers le **Assert** fonctoid, ou insérez une constante.</span><span class="sxs-lookup"><span data-stu-id="36403-119">To establish the second input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.</span></span>  
  
5.  <span data-ttu-id="36403-120">Pour établir le troisième paramètre d’entrée pour le **Assert** fonctoid, créez un lien d’entrée en un nœud de champ du schéma source vers le **Assert** fonctoid, ou insérez une constante.</span><span class="sxs-lookup"><span data-stu-id="36403-120">To establish the third input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.</span></span>  
  
6.  <span data-ttu-id="36403-121">Pour utiliser le paramètre de sortie à partir de la **Assert** fonctoid, créez un lien de sortie en faisant glisser le **Assert** fonctoid à un champ dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="36403-121">To use the output parameter from the **Assert** functoid, create an output link by dragging the **Assert** functoid to a field in the destination schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36403-122">Comme avec d’autres fonctoids, la sortie de la **Assert** fonctoid peut être utilisé comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="36403-122">As with other functoids, the output of the **Assert** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36403-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36403-123">See Also</span></span>  
-  <span data-ttu-id="36403-124">**Référence du fonctoid déclarer**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="36403-124">**Assert Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>   
-  [<span data-ttu-id="36403-125">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="36403-125">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
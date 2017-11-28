---
title: Comment personnaliser les couleurs et polices dans le Mappeur BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.options.colors
ms.assetid: 494e4d70-8159-4721-9378-85bfc3c3d6f2
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 724d9e3c118afc4ef0ca369be17b36f439c5885e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-customize-colors-and-font-in-biztalk-mapper"></a><span data-ttu-id="6f235-102">Personnalisation des couleurs et de la police dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="6f235-102">How to Customize Colors and Font in BizTalk Mapper</span></span>
<span data-ttu-id="6f235-103">Vous pouvez changer les couleurs associées aux différents types de liens et la couleur des objets sélectionnés dans la vue Grille.</span><span class="sxs-lookup"><span data-stu-id="6f235-103">You can change the colors associated with various types of links and the color of selected objects in the Grid view.</span></span> <span data-ttu-id="6f235-104">Vous pouvez également modifier la police utilisée pour afficher les nœuds d’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="6f235-104">You can also change the font used to display the schema tree nodes.</span></span> <span data-ttu-id="6f235-105">Cette rubrique contient des instructions détaillées sur ces changements.</span><span class="sxs-lookup"><span data-stu-id="6f235-105">This topic provides step-by-step instructions for making such changes.</span></span>  
  
 <span data-ttu-id="6f235-106">Vous pouvez également personnaliser les paramètres généraux du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6f235-106">You can also choose to customize the general settings for BizTalk Mapper.</span></span> <span data-ttu-id="6f235-107">Pour plus d’informations sur la façon de choisir les paramètres, consultez [comment personnaliser les paramètres généraux dans le Mappeur BizTalk](../core/how-to-customize-general-settings-in-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="6f235-107">For information on how to choose the settings, see [How to Customize General Settings in BizTalk Mapper](../core/how-to-customize-general-settings-in-biztalk-mapper.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f235-108">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6f235-108">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-change-the-colors-and-font-used-in-biztalk-mapper"></a><span data-ttu-id="6f235-109">Pour changer les couleurs et la police utilisées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="6f235-109">To change the colors and font used in BizTalk Mapper</span></span>  
  
1.  <span data-ttu-id="6f235-110">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le menu **Outils** , cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="6f235-110">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="6f235-111">Dans le **Options** boîte de dialogue, développez le **le Mappeur BizTalk** nœud, puis cliquez sur **couleurs et polices**.</span><span class="sxs-lookup"><span data-stu-id="6f235-111">In the **Options** dialog box, expand the **BizTalk Mapper** node, and then click **Colors & Fonts**.</span></span>  
  
     <span data-ttu-id="6f235-112">![Sélectionnez les polices et couleurs](../core/media/colorsfonts-options.gif "ColorsFonts_Options")</span><span class="sxs-lookup"><span data-stu-id="6f235-112">![Select colors and fonts](../core/media/colorsfonts-options.gif "ColorsFonts_Options")</span></span>  
  
3.  <span data-ttu-id="6f235-113">Changez les couleurs des différents types de liens, avertissements du compilateur, premier-plan et arrière-plan de la grille, à l’aide du sélecteur de couleur déroulant associé à chaque propriété de couleur.</span><span class="sxs-lookup"><span data-stu-id="6f235-113">Change the colors for the various types of links, compiler warnings, grid foreground, and grid background by using the drop-down color picker associated with each color property.</span></span>  
  
     <span data-ttu-id="6f235-114">Les choix de couleurs suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="6f235-114">The following color choices are available:</span></span>  
  
    -   <span data-ttu-id="6f235-115">**Liens de nœud enfant.**</span><span class="sxs-lookup"><span data-stu-id="6f235-115">**Child Node Links.**</span></span> <span data-ttu-id="6f235-116">couleur utilisée pour indiquer les liens des enfants du parent réduit.</span><span class="sxs-lookup"><span data-stu-id="6f235-116">The color used for drawing links of collapsed parent’s children.</span></span>  
  
    -   <span data-ttu-id="6f235-117">**Erreurs du compilateur.**</span><span class="sxs-lookup"><span data-stu-id="6f235-117">**Compiler Errors.**</span></span> <span data-ttu-id="6f235-118">couleur utilisée pour indiquer une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="6f235-118">The color used for drawing the compiler error.</span></span>  
  
    -   <span data-ttu-id="6f235-119">**Liaisons du compilateur.**</span><span class="sxs-lookup"><span data-stu-id="6f235-119">**Compiler Links.**</span></span> <span data-ttu-id="6f235-120">couleur des liens du compilateur qui constituent les liens des directives du compilateur.</span><span class="sxs-lookup"><span data-stu-id="6f235-120">The color of compiler links, which are the compiler directive links.</span></span> <span data-ttu-id="6f235-121">Ces liens sont créés automatiquement lorsqu'un lien est défini à partir d'un champ de l'arborescence des schémas sources vers un champ de l'arborescence des schémas de destination.</span><span class="sxs-lookup"><span data-stu-id="6f235-121">They are links that are automatically created when a link is set from a field in the source schema tree to a field in the destination schema tree.</span></span>  
  
    -   <span data-ttu-id="6f235-122">**Liaisons estompées.**</span><span class="sxs-lookup"><span data-stu-id="6f235-122">**Dimmed Links.**</span></span> <span data-ttu-id="6f235-123">couleur utilisée pour indiquer les liaisons qui ne sont pas sélectionnées ou mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="6f235-123">The color used to draw links that are not selected or highlighted.</span></span>  
  
    -   <span data-ttu-id="6f235-124">**Liaisons souples.**</span><span class="sxs-lookup"><span data-stu-id="6f235-124">**Elastic Links.**</span></span> <span data-ttu-id="6f235-125">couleur des liens souples qui constituent des liens simples pouvant être déplacés de l'arborescence du schéma source vers celle du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6f235-125">The color of elastic links, which are simple value-copy links that are dragged from the source schema tree to the destination schema tree.</span></span> <span data-ttu-id="6f235-126">Une fois le lien créé, sa couleur est remplacée par celle des liens fixes.</span><span class="sxs-lookup"><span data-stu-id="6f235-126">After the link is made, the color of the link changes to the color for fixed links.</span></span>  
  
    -   <span data-ttu-id="6f235-127">**Liaisons générales :**</span><span class="sxs-lookup"><span data-stu-id="6f235-127">**General Links.**</span></span> <span data-ttu-id="6f235-128">couleur utilisée pour indiquer les liaisons ayant les deux extrémités dans la vue, lorsque rien n'est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6f235-128">The color used to draw links that have both the ends in the view, when nothing is selected.</span></span>  
  
    -   <span data-ttu-id="6f235-129">**Arrière-plan de la grille.**</span><span class="sxs-lookup"><span data-stu-id="6f235-129">**Grid Background.**</span></span> <span data-ttu-id="6f235-130">couleur de l'arrière-plan des pages de grille.</span><span class="sxs-lookup"><span data-stu-id="6f235-130">The color of the background in grid pages.</span></span>  
  
    -   <span data-ttu-id="6f235-131">**Lignes de la grille.**</span><span class="sxs-lookup"><span data-stu-id="6f235-131">**Grid Lines.**</span></span> <span data-ttu-id="6f235-132">couleur utilisée pour indiquer les lignes de la grille.</span><span class="sxs-lookup"><span data-stu-id="6f235-132">The color used for drawing the grid lines.</span></span>  
  
    -   <span data-ttu-id="6f235-133">**Liaisons mises en surbrillance.**</span><span class="sxs-lookup"><span data-stu-id="6f235-133">**Highlighted Links.**</span></span> <span data-ttu-id="6f235-134">couleur utilisée pour mettre des liens en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="6f235-134">The color used for highlighting links.</span></span>  
  
    -   <span data-ttu-id="6f235-135">**Correspondance indicatives :**</span><span class="sxs-lookup"><span data-stu-id="6f235-135">**Indicative Match Links.**</span></span> <span data-ttu-id="6f235-136">couleur utilisée pour indiquer les correspondances indicatives.</span><span class="sxs-lookup"><span data-stu-id="6f235-136">The color used to draw indicative matches.</span></span>  
  
    -   <span data-ttu-id="6f235-137">**Liaisons partiellement hors étendue.**</span><span class="sxs-lookup"><span data-stu-id="6f235-137">**Partially Out of Scope Links.**</span></span> <span data-ttu-id="6f235-138">couleur utilisée pour indiquer les liaisons ayant une seule extrémité dans la vue.</span><span class="sxs-lookup"><span data-stu-id="6f235-138">The color used to draw links that have only one end in view.</span></span>  
  
    -   <span data-ttu-id="6f235-139">**Couleur de police du nœud de schéma.**</span><span class="sxs-lookup"><span data-stu-id="6f235-139">**Schema Node Font Color.**</span></span> <span data-ttu-id="6f235-140">couleur utilisée pour les nœuds d'arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="6f235-140">The color used for schema tree nodes.</span></span>  
  
    -   <span data-ttu-id="6f235-141">**Résultats de la recherche.**</span><span class="sxs-lookup"><span data-stu-id="6f235-141">**Search Results.**</span></span> <span data-ttu-id="6f235-142">couleur utilisée pour indiquer les correspondances dans l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="6f235-142">The color used for drawing search matches on the schema tree.</span></span>  
  
    -   <span data-ttu-id="6f235-143">**Objets de grille sélectionnée.**</span><span class="sxs-lookup"><span data-stu-id="6f235-143">**Selected Grid Objects.**</span></span> <span data-ttu-id="6f235-144">couleur utilisée pour indiquer la sélection dans la surface de la grille.</span><span class="sxs-lookup"><span data-stu-id="6f235-144">The color used for drawing the selection in the grid surface.</span></span>  
  
    -   <span data-ttu-id="6f235-145">**Liaisons totalement hors étendue.**</span><span class="sxs-lookup"><span data-stu-id="6f235-145">**Totally Out of Scope Links.**</span></span> <span data-ttu-id="6f235-146">couleur utilisée pour indiquer les liaisons ayant les deux extrémités hors de la vue.</span><span class="sxs-lookup"><span data-stu-id="6f235-146">The color used to draw links that have both ends out of the view.</span></span>  
  
4.  <span data-ttu-id="6f235-147">Cliquez sur le bouton de sélection (**...** ) situé à l’extrémité droite de la **police du nœud de schéma** zone de valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="6f235-147">Click the ellipsis (**…**) button located at the right end of the **Schema node font** property value box.</span></span>  
  
5.  <span data-ttu-id="6f235-148">Dans le **police** boîte de dialogue, de modifier la police utilisée dans les vues dans la fenêtre d’édition principale.</span><span class="sxs-lookup"><span data-stu-id="6f235-148">In the **Font** dialog box, change the font used in the views in the main editing window.</span></span>  
  
6.  <span data-ttu-id="6f235-149">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f235-149">Click **OK**.</span></span> <span data-ttu-id="6f235-150">Les paramètres choisis sont appliqués.</span><span class="sxs-lookup"><span data-stu-id="6f235-150">The settings are applied as chosen.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6f235-151">Si vous ne souhaitez pas utiliser les paramètres personnalisés, cliquez sur **paramètres par défaut** dans les **Options** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f235-151">If you do not want to use the customized settings, click **Restore Defaults** in the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f235-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f235-152">See Also</span></span>  
 [<span data-ttu-id="6f235-153">À l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="6f235-153">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)
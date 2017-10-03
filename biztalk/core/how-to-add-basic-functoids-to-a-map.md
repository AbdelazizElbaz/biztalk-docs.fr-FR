---
title: "Ajout de fonctoids de base à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a81fb73-cccf-4f74-af92-39e4af13e255
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23a6748a5ce128ef13ce012412e36570e4e01eba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-basic-functoids-to-a-map"></a><span data-ttu-id="dd445-102">Ajout d'un fonctoid de base à un mappage</span><span class="sxs-lookup"><span data-stu-id="dd445-102">How to Add Basic Functoids to a Map</span></span>
<span data-ttu-id="dd445-103">De nombreux fonctoids sont très simples à utiliser.</span><span class="sxs-lookup"><span data-stu-id="dd445-103">Many functoids are very simple to use.</span></span> <span data-ttu-id="dd445-104">Ils sont désignés ici des fonctoids de base pour les différencier des fonctoids dans la **avancé** catégorie.</span><span class="sxs-lookup"><span data-stu-id="dd445-104">These are referred to here as basic functoids to distinguish them from the functoids in the **Advanced** category.</span></span> <span data-ttu-id="dd445-105">Les fonctoids de base regroupent les catégories restantes de fonctoids, telles que Conversion, Cumulé, Base de données, Date et heure, Logique, Mathématique, Scientifique et Chaîne.</span><span class="sxs-lookup"><span data-stu-id="dd445-105">Basic functoids comprise the remaining categories of functoids such as Conversion, Cumulative, Database, Date and Time, Logical, Mathematical, Scientific, and String.</span></span>  
  
 <span data-ttu-id="dd445-106">En général, les fonctoids de base utilisent des types simples tels que des nombres ou des chaînes pour leurs liens d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="dd445-106">Basic functoids, in general, have simple types, such as numbers and strings, as their input and output links.</span></span>  
  
 <span data-ttu-id="dd445-107">Pour utiliser un fonctoid de base, il faut l'ajouter à une page de grille, créer des liens d'entrée vers ce fonctoid à partir de la gauche et créer vers la droite un lien de sortie à partir de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="dd445-107">Using a basic functoid involves adding it to a grid page, creating input links to the functoid, coming from the left, and creating output link from the functoid, leaving to the right.</span></span> <span data-ttu-id="dd445-108">Cette rubrique contient des instructions détaillées concernant ce type d'opérations.</span><span class="sxs-lookup"><span data-stu-id="dd445-108">This topic provides step-by-step instructions for these operations.</span></span>  
  
## <a name="add-a-basic-functoid-to-a-map"></a><span data-ttu-id="dd445-109">Ajouter un fonctoid de base à un mappage</span><span class="sxs-lookup"><span data-stu-id="dd445-109">Add a basic functoid to a map</span></span>  
  
1.  <span data-ttu-id="dd445-110">Avec la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] active, cliquez sur l'onglet approprié pour sélectionner la catégorie du fonctoid que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="dd445-110">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the appropriate tab to select the category of the functoid you want to use.</span></span>  
  
     <span data-ttu-id="dd445-111">La liste des fonctoids disponibles dans la catégorie choisie s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dd445-111">The list of available functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="dd445-112">Faites glisser le fonctoid que vous souhaitez utiliser de la boîte à outils vers l'emplacement approprié d'une page de grille.</span><span class="sxs-lookup"><span data-stu-id="dd445-112">Drag the functoid you want to use from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-113">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="dd445-113">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="dd445-114">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="dd445-114">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-115">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="dd445-115">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="dd445-116">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="dd445-116">Functoids are executed from left to right.</span></span> <span data-ttu-id="dd445-117">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="dd445-117">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
## <a name="create-input-links-to-a-basic-functoid"></a><span data-ttu-id="dd445-118">Créer des liens d’entrée vers un fonctoid de base</span><span class="sxs-lookup"><span data-stu-id="dd445-118">Create input links to a basic functoid</span></span>  
  
1.  <span data-ttu-id="dd445-119">Faites glisser un nœud d'enregistrement ou de champ du schéma source vers le fonctoid de base de la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="dd445-119">Drag a record or field node from the source schema to the basic functoid in the displayed grid page.</span></span>  
  
     <span data-ttu-id="dd445-120">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-120">**- Or -**</span></span>  
  
     <span data-ttu-id="dd445-121">Dans la page de grille qui s'affiche, faites glisser un autre fonctoid, situé plus à gauche, vers le fonctoid de base avec lequel vous souhaitez établir un lien d'entrée.</span><span class="sxs-lookup"><span data-stu-id="dd445-121">In the displayed grid page, drag another functoid, which is located farther to the left, to the basic functoid to which you want to create an input link.</span></span>  
  
     <span data-ttu-id="dd445-122">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-122">**- Or -**</span></span>  
  
     <span data-ttu-id="dd445-123">Faites glisser le fonctoid de base de la page de grille affichée vers un nœud d'enregistrement ou de champ du schéma source.</span><span class="sxs-lookup"><span data-stu-id="dd445-123">Drag the basic functoid in the displayed grid page to a record or field node in the source schema.</span></span>  
  
     <span data-ttu-id="dd445-124">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-124">**- Or -**</span></span>  
  
     <span data-ttu-id="dd445-125">Dans la page de grille qui s'affiche, faites glisser le fonctoid de base avec lequel vous souhaitez établir un lien d'entrée vers un autre fonctoid, situé plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="dd445-125">In the displayed grid page, drag the basic functoid to which you want to create an input link to another functoid that is located farther to the left.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-126">Contrairement au point de terminaison fixe du lien, le point de terminaison mobile du lien prend, pendant l'opération de glisser-déposer, la forme d'une croix pour cibler plus précisément le deuxième point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dd445-126">While dragging, the moving endpoint of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint.</span></span> <span data-ttu-id="dd445-127">Si vous pointez le point de terminaison mobile du lien sur un objet qui n'est pas un deuxième point de terminaison approprié pour le lien (ce qui peut arriver en cas d'incompatibilité de types de données), la croix se transforme en une icône constituée d'un cercle barré d'un trait diagonal.</span><span class="sxs-lookup"><span data-stu-id="dd445-127">If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.</span></span>  
  
2.  <span data-ttu-id="dd445-128">Répétez l'étape 1 le nombre de fois nécessaire pour établir l'ensemble des liens d'entrée (mais peut-être pas l'ensemble des paramètres d'entrée) vers le fonctoid de base.</span><span class="sxs-lookup"><span data-stu-id="dd445-128">Repeat step 1 as necessary to establish the complete set of input links (though perhaps not the entire set of input parameters) to the basic functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-129">Quelques fonctoids ne requièrent aucun lien d'entrée.</span><span class="sxs-lookup"><span data-stu-id="dd445-129">There are a few functoids that do not require any input links.</span></span> <span data-ttu-id="dd445-130">Par exemple, le **Date**, **temps**, et **Date et heure** fonctoids dans le **Date et heure** catégorie de fonctoid Indiquez la date actuelle, heure, ou la date et heure, respectivement, à laquelle un message d’instance est en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="dd445-130">For example, the **Date**, **Time**, and **Date and Time** functoids in the **Date and Time** functoid category provide the current date, time, or date and time, respectively, at which an instance message is being processed.</span></span> <span data-ttu-id="dd445-131">Ils ne nécessitent donc aucun paramètre d'entrée à partir du schéma source.</span><span class="sxs-lookup"><span data-stu-id="dd445-131">Thus, they do not require any input parameters from the source schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-132">L’ordre des paramètres d’entrée de nombreux fonctoids est important, comme indiqué dans la rubrique de référence de fonctoids correspondante (voir **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]).</span><span class="sxs-lookup"><span data-stu-id="dd445-132">The order of input parameters to many functoids is significant, as indicated in the corresponding functoid reference topic (see **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]).</span></span> <span data-ttu-id="dd445-133">L'ordre dans lequel vous créez des liens détermine l'ordre des paramètres d'entrée du fonctoid.</span><span class="sxs-lookup"><span data-stu-id="dd445-133">The order in which you create links sets the order of input parameters to the functoid.</span></span> <span data-ttu-id="dd445-134">Pour plus d’informations sur les propriétés des fonctoids et en spécifiant l’ordre des paramètres d’entrée du fonctoid, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dd445-134">For more information about functoid properties and specifying the order of functoid input parameters, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span> <span data-ttu-id="dd445-135">Pour plus d’informations sur la façon de configurer les paramètres d’entrée d’un fonctoid, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dd445-135">For information about how to configure the input parameters of a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-136">Avant de commencer à établir des liens, assurez-vous que les fonctoids ou que le nœud de schéma source que vous souhaitez lier sont visibles dans la page de grille ou la fenêtre de schéma source affichée.</span><span class="sxs-lookup"><span data-stu-id="dd445-136">Ensure the functoids or source schema node you want to link are visible in the displayed grid page or source schema window before you begin linking.</span></span>  
  
## <a name="create-the-output-link-from-a-basic-functoid"></a><span data-ttu-id="dd445-137">Créer le lien de sortie à partir d’un fonctoid de base</span><span class="sxs-lookup"><span data-stu-id="dd445-137">Create the output link from a basic functoid</span></span>  
  
1.  <span data-ttu-id="dd445-138">Faites glisser un nœud d'enregistrement ou de champ du schéma de destination vers le fonctoid de base dans la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="dd445-138">Drag a record or field node from the destination schema to the basic functoid in the displayed grid page.</span></span>  
  
     <span data-ttu-id="dd445-139">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-139">**- Or -**</span></span>  
  
     <span data-ttu-id="dd445-140">Dans la page de grille affichée, faites glisser un autre fonctoid, situé à droite, vers le fonctoid de base avec lequel vous souhaitez établir le lien de sortie.</span><span class="sxs-lookup"><span data-stu-id="dd445-140">In the displayed grid page, drag another functoid, which is located farther to the right, to the basic functoid to which you want to create the output link.</span></span>  
  
     <span data-ttu-id="dd445-141">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-141">**- Or -**</span></span>  
  
     <span data-ttu-id="dd445-142">Faites glisser le fonctoid de base de la page de grille affichée vers un nœud d'enregistrement ou de champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="dd445-142">Drag the basic functoid in the displayed grid page to a record or field node in the destination schema.</span></span>  
  
     <span data-ttu-id="dd445-143">**- Ou -**</span><span class="sxs-lookup"><span data-stu-id="dd445-143">**- Or -**</span></span>  
  
2.  <span data-ttu-id="dd445-144">Dans la page de grille affichée, faites glisser le fonctoid de base avec lequel vous souhaitez établir un lien de sortie vers un autre fonctoid, situé à sa droite.</span><span class="sxs-lookup"><span data-stu-id="dd445-144">In the displayed grid page, drag the basic functoid to which you want to create the output link to another functoid that is located farther to the right.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-145">Avant de commencer l'opération de connexion, assurez-vous que les fonctoids et que le nœud de schéma source que vous souhaitez lier sont déjà visibles respectivement dans la page de grille affichée et la fenêtre de schéma source.</span><span class="sxs-lookup"><span data-stu-id="dd445-145">Ensure the functoids and source schema node that you want to link are already visible in the displayed grid page and source schema window, respectively, before you begin the linking operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-146">La connexion de fonctoids tente toujours de désactiver les liens inappropriés, notamment les liens dont les types de données source et cible ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="dd445-146">Functoid linking always attempts to disallow inappropriate linking, such as links where source and target data types do not match.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd445-147">Contrairement au point de terminaison fixe, le point de terminaison mobile du lien, pendant l'opération de glisser-déposer, prend la forme d'une croix pour cibler plus précisément le deuxième point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dd445-147">While dragging, the moving end point of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint.</span></span> <span data-ttu-id="dd445-148">Si vous pointez le point de terminaison mobile du lien sur un objet qui n'est pas un deuxième point de terminaison approprié pour le lien (ce qui peut arriver en cas d'incompatibilité de types de données), la croix se transforme en une icône constituée d'un cercle barré d'un trait diagonal.</span><span class="sxs-lookup"><span data-stu-id="dd445-148">If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd445-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd445-149">See Also</span></span>  
<span data-ttu-id="dd445-150">**Référence du fonctoid**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="dd445-150">**Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
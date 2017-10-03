---
title: "Ajout de fonctoids itération à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eaea929-e352-447d-b119-bd69b6b24e6c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2df7cda082a9a85e54e1dce427d73ea15d8f920
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-iteration-functoids-to-a-map"></a><span data-ttu-id="3510e-102">Ajout de fonctoids Itération à un mappage</span><span class="sxs-lookup"><span data-stu-id="3510e-102">How to Add Iteration Functoids to a Map</span></span>
<span data-ttu-id="3510e-103">Le **itération** fonctoid sorties commençant à 1 pour le premier enregistrement, 2 pour le deuxième enregistrement de la structure de l’index de l’enregistrement actif dans une boucle et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="3510e-103">The **Iteration** functoid outputs the index of the current record in a looping structure, beginning at 1 for the first record, 2 for the second record, and so on.</span></span>  
  
 <span data-ttu-id="3510e-104">Pour obtenir des informations conceptuelles sur le **itération** fonctoid, consultez [fonctoid itération](../core/iteration-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="3510e-104">For conceptual information about the **Iteration** functoid, see [Iteration Functoid](../core/iteration-functoid.md).</span></span>  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="3510e-105">Pour ajouter le fonctoid Index à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="3510e-105">To add the Index functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="3510e-106">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="3510e-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="3510e-107">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="3510e-107">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="3510e-108">Faites glisser le **Index** fonctoid (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="3510e-108">Drag the **Index** functoid (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3510e-109">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="3510e-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="3510e-110">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="3510e-110">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3510e-111">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="3510e-111">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="3510e-112">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="3510e-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="3510e-113">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="3510e-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="3510e-114">Pour établir le paramètre d’entrée d’enregistrement en boucle pour le **itération** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement de boucle du schéma source vers le **itération** fonctoid, ou en faisant glisser le  **Itération** fonctoid vers un enregistrement de boucle dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="3510e-114">To establish the looping record input parameter for the **Iteration** functoid, create an input link by dragging a looping record from the source schema to the **Iteration** functoid, or by dragging the **Iteration** functoid to a looping record in the source schema.</span></span>  
  
4.  <span data-ttu-id="3510e-115">Pour utiliser le paramètre de sortie à partir de la **itération** fonctoid, créez un lien de sortie en faisant glisser le **itération** fonctoid à un champ du schéma de destination, ou en faisant glisser un champ dans le schéma de destination le **itération** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="3510e-115">To use the output parameter from the **Iteration** functoid, create an output link by dragging the **Iteration** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Iteration** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3510e-116">Le type de données du champ correspondant dans le schéma de destination doit être numérique ou convertible en numérique afin qu’il corresponde au type de données de sortie de la **itération** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="3510e-116">The data type of the relevant field in the destination schema must be numeric or convertible to numeric so that it matches the output data type of the **Iteration** functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3510e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3510e-117">See Also</span></span>  
 [<span data-ttu-id="3510e-118">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="3510e-118">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
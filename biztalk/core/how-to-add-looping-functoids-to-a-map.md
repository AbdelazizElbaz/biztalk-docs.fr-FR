---
title: "Comment ajouter des fonctoids bouclage à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa380b4a92de685ad8dc19c27a98f6578d12dc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-looping-functoids-to-a-map"></a><span data-ttu-id="66247-102">Ajout de fonctoids Bouclage à un mappage</span><span class="sxs-lookup"><span data-stu-id="66247-102">How to Add Looping Functoids to a Map</span></span>

## <a name="overview"></a><span data-ttu-id="66247-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="66247-103">Overview</span></span>
<span data-ttu-id="66247-104">Le **bouclage** fonctoid combine plusieurs enregistrements ou champs du schéma source en un enregistrement unique dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="66247-104">The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.</span></span>  
  
 <span data-ttu-id="66247-105">Pour obtenir des informations conceptuelles sur le **bouclage** fonctoid, consultez [fonctoid Bouclage](../core/looping-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="66247-105">For conceptual information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).</span></span>  
  
 <span data-ttu-id="66247-106">Sous certaines conditions, certains fonctoids peuvent ne pas fonctionner comme prévu lorsqu’ils sont utilisés dans un mappage avec un **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66247-106">Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid.</span></span> <span data-ttu-id="66247-107">Si un tel fonctoid remplit les conditions suivantes, il ne produit pas les résultats attendus :</span><span class="sxs-lookup"><span data-stu-id="66247-107">If such a functoid meets the following conditions, it does not produce the expected results:</span></span>  
  
-   <span data-ttu-id="66247-108">Plusieurs liens d'entrée sont associés au fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66247-108">The functoid has more than one input link.</span></span>  
  
-   <span data-ttu-id="66247-109">Deux ou plusieurs des liens d’entrée de fonctoid sont liés aux champs enfants des enregistrements d’entrée pour le **bouclage** fonctoid, où les champs enfants ne sont pas frères.</span><span class="sxs-lookup"><span data-stu-id="66247-109">Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.</span></span>  
  
-   <span data-ttu-id="66247-110">Le fonctoid possède un lien de sortie qui est lié à un champ enfant de l’enregistrement de la sortie de la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66247-110">The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.</span></span>  
  
## <a name="add-the-looping-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="66247-111">Ajouter le fonctoid Bouclage à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="66247-111">Add the Looping functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="66247-112">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="66247-112">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="66247-113">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="66247-113">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="66247-114">Faites glisser le **bouclage** fonctoid à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="66247-114">Drag the **Looping** functoid from the Toolbox to the appropriate location on a grid page.</span></span>  
  
     ![](../core/media/bts-tls-looping.gif "bts_tls_looping")  
<span data-ttu-id="66247-115">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="66247-115">Looping functoid</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="66247-116">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="66247-116">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="66247-117">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="66247-117">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
    > 
    >  <span data-ttu-id="66247-118">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="66247-118">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="66247-119">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="66247-119">Functoids are executed from left to right.</span></span> <span data-ttu-id="66247-120">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="66247-120">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="66247-121">Pour établir les paramètres d’entrée pour le **bouclage** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement ou champ du schéma source vers le **bouclage** fonctoid, ou en faisant glisser le **bouclage**  fonctoid vers un enregistrement ou un champ du schéma source.</span><span class="sxs-lookup"><span data-stu-id="66247-121">To establish the input parameters for the **Looping** functoid, create an input link by dragging a record or field from the source schema to the **Looping** functoid, or dragging the **Looping** functoid to a record or field in the source schema.</span></span> <span data-ttu-id="66247-122">Répétez que nécessaire pour inclure tous les enregistrements d’entrée pertinents à la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66247-122">Repeat as required to include all of the relevant input records or fields to the **Looping** functoid.</span></span>  
  
4.  <span data-ttu-id="66247-123">Pour utiliser le paramètre de sortie à partir de la **bouclage** fonctoid, créez un lien de sortie en faisant glisser le **bouclage** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en faisant glisser un enregistrement ou un champ dans le schéma de destination pour le **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66247-123">To use the output parameter from the **Looping** functoid, create an output link by dragging the **Looping** functoid to a record or field in the destination schema, or by dragging a record or field in the destination schema to the **Looping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="66247-124">Contrairement à beaucoup d’autres fonctoids, la sortie de la **bouclage** fonctoid ne peut être lié à un élément du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="66247-124">Unlike many other functoids, the output of the **Looping** functoid can only be linked to an element of the destination schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66247-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66247-125">See Also</span></span>  
-  [<span data-ttu-id="66247-126">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="66247-126">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)   
-  <span data-ttu-id="66247-127">**Référence du fonctoid de bouclage**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="66247-127">**Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
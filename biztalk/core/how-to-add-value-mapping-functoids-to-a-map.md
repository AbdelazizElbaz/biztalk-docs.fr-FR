---
title: "Comment ajouter des fonctoids de mappage à un mappage de valeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc70067a-67a1-4a0e-95e5-b0cb327d2cee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e463489332c3a1d2887dab5f7bd734fdd20af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-value-mapping-functoids-to-a-map"></a><span data-ttu-id="e8b52-102">Ajout de fonctoids de mappage des valeurs à un mappage</span><span class="sxs-lookup"><span data-stu-id="e8b52-102">How to Add Value Mapping Functoids to a Map</span></span>
<span data-ttu-id="e8b52-103">Le **mappage** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="e8b52-103">The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="e8b52-104">Un fonctoid sert souvent à modifier les attributs d'un champ en attributs d'un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="e8b52-104">A common use of the functoid is to change the attributes of a field into the attributes of a record.</span></span>  
  
 <span data-ttu-id="e8b52-105">Pour obtenir des informations conceptuelles sur le **mappage** fonctoid, consultez [fonctoid Mappage des valeurs](../core/value-mapping-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="e8b52-105">For conceptual information about the **Value Mapping** functoid, see [Value Mapping Functoid](../core/value-mapping-functoid.md).</span></span>  
  
### <a name="to-add-the-value-mapping-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="e8b52-106">Pour ajouter le fonctoid Mappage des valeurs à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="e8b52-106">To add the Value Mapping functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="e8b52-107">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="e8b52-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="e8b52-108">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="e8b52-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="e8b52-109">Faites glisser le **mappage** fonctoid (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="e8b52-109">Drag the **Value Mapping** functoid (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8b52-110">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="e8b52-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="e8b52-111">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="e8b52-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8b52-112">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="e8b52-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="e8b52-113">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="e8b52-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="e8b52-114">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="e8b52-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="e8b52-115">Pour établir le premier paramètre d’entrée pour le **mappage des valeurs** fonctoid, créer un lien d’entrée en faisant glisser le **mappage** fonctoid à un nœud enregistrement ou de champ dans le schéma source ou à un autre fonctoid pour de gauche, qui possède un type de données booléen et qui produira une valeur d’entrée « true » ou « false ».</span><span class="sxs-lookup"><span data-stu-id="e8b52-115">To establish the first input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or to another functoid to its left, that has a Boolean data type and that will produce an input value of "true" or "false".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8b52-116">Vous pouvez également faire glisser dans la direction opposée, en faisant glisser la source de la valeur booléenne à la **mappage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e8b52-116">You can also drag in the opposite direction, dragging the source of the Boolean value to the **Value Mapping** functoid.</span></span>  
  
4.  <span data-ttu-id="e8b52-117">Pour établir le deuxième paramètre d’entrée pour le **mappage des valeurs** fonctoid, créer un lien d’entrée en faisant glisser le **mappage** fonctoid vers un nœud enregistrement ou de champ du schéma source, ou en faisant glisser un enregistrement ou nœud de champ dans le schéma source vers le **mappage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e8b52-117">To establish the second input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or by dragging a record or field node in the source schema to the **Value Mapping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8b52-118">La deuxième entrée de paramètre à la **mappage** fonctoid peut également être à partir de la sortie d’un autre fonctoid situé à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="e8b52-118">The second input parameter to the **Value Mapping** functoid can also be from the output of another functoid to its left.</span></span> <span data-ttu-id="e8b52-119">Créez les liens qui représentent ces sources d'entrée en faisant glisser un des fonctoids appropriés vers l'autre fonctoid approprié.</span><span class="sxs-lookup"><span data-stu-id="e8b52-119">Create the links that represent such sources of input by dragging one of the relevant functoids to the other relevant functoid.</span></span>  
  
5.  <span data-ttu-id="e8b52-120">Pour utiliser le paramètre de sortie à partir de la **mappage des valeurs** fonctoid, créez un lien de sortie en faisant glisser le **mappage des valeurs** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en faisant glisser un champ d’enregistrement le schéma de destination le **mappage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e8b52-120">To use the output parameter from the **Value Mapping** functoid, create an output link by dragging the **Value Mapping** functoid to a record or field in the destination schema, or by dragging a record field in the destination schema to the **Value Mapping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8b52-121">Comme avec d’autres fonctoids, la sortie de la **mappage** fonctoid peut servir d’entrée à un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e8b52-121">As with other functoids, the output of the **Value Mapping** functoid can serve as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b52-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8b52-122">See Also</span></span>  
 [<span data-ttu-id="e8b52-123">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="e8b52-123">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
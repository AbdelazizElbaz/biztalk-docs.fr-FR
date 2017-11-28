---
title: "Comment ajouter le mappage de fonctoids (mise à plat) à une carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a447c3-58d0-42ab-a5c4-417ee7800a6b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5fe3f7b55a5bd5ef532bf2727c60bad2a621c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-value-mapping-flattening-functoids-to-a-map"></a><span data-ttu-id="0c997-102">Ajout de fonctoids de mappage des valeurs (mise à plat) à un mappage</span><span class="sxs-lookup"><span data-stu-id="0c997-102">How to Add Value Mapping (Flattening) Functoids to a Map</span></span>
<span data-ttu-id="0c997-103">Le **Value Mapping (Flattening)** fonctoid vous permet d’aplatir une partie d’un message d’instance d’entrée en convertissant plusieurs enregistrements en un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="0c997-103">The **Value Mapping (Flattening)** functoid enables you to flatten a portion of an input instance message by converting multiple records into a single record.</span></span> <span data-ttu-id="0c997-104">Il s’agit d’une opération courante dans la conversion des catalogues Microsoft Commerce Server.</span><span class="sxs-lookup"><span data-stu-id="0c997-104">This is a common operation in converting Microsoft Commerce Server catalogs.</span></span>  
  
 <span data-ttu-id="0c997-105">Pour obtenir des informations conceptuelles sur le **Value Mapping (Flattening)** fonctoid, consultez [fonctoid Mappage des valeurs (mise à plat)](../core/value-mapping-flattening-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="0c997-105">For conceptual information about the **Value Mapping (Flattening)** functoid, see [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
### <a name="to-add-the-value-mapping-flattening-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="0c997-106">Pour ajouter le fonctoid Mappage des valeurs (mise à plat) à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="0c997-106">To add the Value Mapping (Flattening) functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="0c997-107">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="0c997-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="0c997-108">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="0c997-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="0c997-109">Faites glisser le **Value Mapping (Flattening)** fonctoid (![](../core/media/bts-tls-valmapflat.gif "bts_tls_valmapflat")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="0c997-109">Drag the **Value Mapping (Flattening)** functoid (![](../core/media/bts-tls-valmapflat.gif "bts_tls_valmapflat")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c997-110">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="0c997-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="0c997-111">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="0c997-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c997-112">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="0c997-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="0c997-113">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="0c997-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="0c997-114">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="0c997-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="0c997-115">Pour établir le premier paramètre d’entrée pour le **Value Mapping (Flattening)** fonctoid, créez un lien d’entrée en faisant glisser le **Value Mapping (Flattening)** fonctoid à un nœud enregistrement ou de champ dans la source schéma, ou un autre fonctoid situé à sa gauche, qui a un type de données booléen et qui produira une valeur d’entrée « true » ou « false ».</span><span class="sxs-lookup"><span data-stu-id="0c997-115">To establish the first input parameter for the **Value Mapping (Flattening)** functoid, create an input link by dragging the **Value Mapping (Flattening)** functoid to a record or field node in the source schema, or to another functoid to its left, that has a Boolean data type and that will produce an input value of "true" or "false."</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c997-116">Vous pouvez également faire glisser dans la direction opposée, en faisant glisser la source de la valeur booléenne à la **Value Mapping (Flattening)** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0c997-116">You can also drag in the opposite direction, dragging the source of the Boolean value to the **Value Mapping (Flattening)** functoid.</span></span>  
  
4.  <span data-ttu-id="0c997-117">Pour établir le deuxième paramètre d’entrée pour le **Value Mapping (Flattening)** fonctoid, créez un lien d’entrée en faisant glisser le **Value Mapping (Flattening)** fonctoid à un nœud enregistrement ou de champ dans la source schéma, ou en faisant glisser un nœud enregistrement ou de champ dans le schéma source vers le **Value Mapping (Flattening)** fonctoid, ou insérez une constante.</span><span class="sxs-lookup"><span data-stu-id="0c997-117">To establish the second input parameter for the **Value Mapping (Flattening)** functoid, create an input link by dragging the **Value Mapping (Flattening)** functoid to a record or field node in the source schema, or by dragging a record or field node in the source schema to the **Value Mapping (Flattening)** functoid, or insert a constant.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c997-118">La deuxième entrée de paramètre à la **Value Mapping (Flattening)** fonctoid peut également être à partir de la sortie d’un autre fonctoid situé à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="0c997-118">The second input parameter to the **Value Mapping (Flattening)** functoid can also be from the output of another functoid to its left.</span></span> <span data-ttu-id="0c997-119">Créez les liens le représentent ces sources d’entrée en faisant glisser un des fonctoids appropriés pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0c997-119">Create the links the represent such sources of input by dragging one of the relevant functoids to the other relevant functoid.</span></span>  
  
5.  <span data-ttu-id="0c997-120">Pour utiliser le paramètre de sortie à partir de la **Value Mapping (Flattening)** fonctoid, créez un lien de sortie en faisant glisser le **Value Mapping (Flattening)** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en en faisant glisser un champ d’enregistrement du schéma de destination pour le **Value Mapping (Flattening)** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0c997-120">To use the output parameter from the **Value Mapping (Flattening)** functoid, create an output link by dragging the **Value Mapping (Flattening)** functoid to a record or field in the destination schema, or by dragging a record field in the destination schema to the **Value Mapping (Flattening)** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c997-121">Comme avec d’autres fonctoids, la sortie de la **Value Mapping (Flattening)** fonctoid peut être utilisé comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0c997-121">As with other functoids, the output of the **Value Mapping (Flattening)** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c997-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c997-122">See Also</span></span>  
 [<span data-ttu-id="0c997-123">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="0c997-123">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
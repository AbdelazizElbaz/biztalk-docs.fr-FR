---
title: "Ajout de fonctoids valeur Nil à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e193ed-fe5c-4b12-aab8-ff2d81fd45e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cc7d8b0035161b4a2126ace021072ffcd1d17e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-nil-value-functoids-to-a-map"></a><span data-ttu-id="2acc2-102">Ajout de fonctoids Valeur nil à un mappage</span><span class="sxs-lookup"><span data-stu-id="2acc2-102">How to Add Nil Value Functoids to a Map</span></span>
<span data-ttu-id="2acc2-103">Le **valeur Nil** fonctoid définit la valeur du nœud de destination à **Nil**.</span><span class="sxs-lookup"><span data-stu-id="2acc2-103">The **Nil Value** functoid sets the value of the destination node to **Nil**.</span></span>  
  
 <span data-ttu-id="2acc2-104">Pour obtenir des informations conceptuelles sur le **valeur Nil** fonctoid, consultez [fonctoid valeur Nil](../core/nil-value-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="2acc2-104">For conceptual information about the **Nil Value** functoid, see [Nil Value Functoid](../core/nil-value-functoid.md).</span></span>  
  
## <a name="add-the-nil-value-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="2acc2-105">Ajouter le fonctoid valeur Nil à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="2acc2-105">Add the Nil Value functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="2acc2-106">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="2acc2-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span> <span data-ttu-id="2acc2-107">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="2acc2-107">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="2acc2-108">Faites glisser le **valeur Nil** fonctoid (![fonctoid valeur Nil](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="2acc2-108">Drag the **Nil Value** functoid (![Nil Value functoid](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2acc2-109">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="2acc2-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="2acc2-110">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="2acc2-110">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
    >
    >  <span data-ttu-id="2acc2-111">Si vous construisez un mappage impliquant plusieurs fonctoids, vous devez tenir compte de leur placement relatif de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="2acc2-111">If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="2acc2-112">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="2acc2-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="2acc2-113">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="2acc2-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="2acc2-114">Le **valeur Nil** fonctoid peut avoir zéro à un seul des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2acc2-114">The **Nil Value** functoid can have zero to one input parameters.</span></span> <span data-ttu-id="2acc2-115">S’il n’existe aucun paramètre d’entrée pour ce fonctoid, le nœud cible a la valeur **Nil**.</span><span class="sxs-lookup"><span data-stu-id="2acc2-115">If there is no input parameter for this functoid, the target node is set to **Nil**.</span></span> <span data-ttu-id="2acc2-116">Pour définir le paramètre d’entrée pour le **valeur Nil** fonctoid, créez un lien d’entrée en faisant glisser la sortie à partir d’autres **logiques** fonctoid ou à partir d’un champ de variable booléen dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2acc2-116">To establish the input parameter for the **Nil Value** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.</span></span>  
  
4.  <span data-ttu-id="2acc2-117">Pour utiliser le paramètre de sortie à partir de la **valeur Nil** fonctoid, créez un lien de sortie en faisant glisser le **valeur Nil** fonctoid vers un enregistrement ou un champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="2acc2-117">To use the output parameter from the **Nil Value** functoid, create an output link by dragging the **Nil Value** functoid to a record or field in the destination schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2acc2-118">Comme avec d’autres fonctoids, la sortie de la **valeur Nil** fonctoid peut être utilisé comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="2acc2-118">As with other functoids, the output of the **Nil Value** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acc2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2acc2-119">See Also</span></span>  
-  <span data-ttu-id="2acc2-120">**Référence du fonctoid Valeur nil**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="2acc2-120">**Nil Value Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>   
-  [<span data-ttu-id="2acc2-121">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="2acc2-121">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
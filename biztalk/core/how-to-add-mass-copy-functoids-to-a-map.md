---
title: "Ajout de fonctoids copie de masse à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cff63fc-8f34-4bd0-8501-a8401bde6349
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cee6f2c53bbd3b3dbabe55f0160309532d0ebf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-mass-copy-functoids-to-a-map"></a><span data-ttu-id="7293d-102">Ajout de fonctoids Copie de masse à un mappage</span><span class="sxs-lookup"><span data-stu-id="7293d-102">How to Add Mass Copy Functoids to a Map</span></span>
<span data-ttu-id="7293d-103">Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments.</span><span class="sxs-lookup"><span data-stu-id="7293d-103">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="7293d-104">Ces éléments sont, par essence, des caractères génériques fournis par le langage de définition du schéma XML pour remplacer des structures ou ensembles d'attributs non connus.</span><span class="sxs-lookup"><span data-stu-id="7293d-104">These elements are, in essence, wildcards provided in the XML Schema definition language to match unknown structures or sets of attributes.</span></span>  
  
 <span data-ttu-id="7293d-105">Pour obtenir des informations conceptuelles sur le **copie de masse** fonctoid, consultez [fonctoid copie de masse](../core/mass-copy-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="7293d-105">For conceptual information about the **Mass Copy** functoid, see [Mass Copy Functoid](../core/mass-copy-functoid.md).</span></span>  
  
### <a name="to-add-the-mass-copy-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="7293d-106">Pour ajouter le fonctoid Copie de masse à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="7293d-106">To add the Mass Copy functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="7293d-107">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="7293d-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="7293d-108">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="7293d-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="7293d-109">Faites glisser le **copie de masse** fonctoid (![](../core/media/advmasscopy.gif "advmasscopy")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="7293d-109">Drag the **Mass Copy** functoid (![](../core/media/advmasscopy.gif "advmasscopy")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7293d-110">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="7293d-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="7293d-111">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.</span><span class="sxs-lookup"><span data-stu-id="7293d-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7293d-112">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="7293d-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="7293d-113">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="7293d-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="7293d-114">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="7293d-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="7293d-115">Pour définir le paramètre d’entrée pour le **copie de masse** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement du schéma source vers le **copie de masse** fonctoid, ou en faisant glisser le **copie de masse** fonctoid vers un enregistrement dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="7293d-115">To establish the input parameter for the **Mass Copy** functoid, create an input link by dragging a record from the source schema to the **Mass Copy** functoid, or dragging the **Mass Copy** functoid to a record in the source schema.</span></span>  
  
4.  <span data-ttu-id="7293d-116">Pour utiliser le paramètre de sortie à partir de la **copie de masse** fonctoid, créez un lien de sortie en faisant glisser le **copie de masse** fonctoid vers un enregistrement dans le schéma de destination, ou en faisant glisser un enregistrement dans le schéma de destination le **copie de masse** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="7293d-116">To use the output parameter from the **Mass Copy** functoid, create an output link by dragging the **Mass Copy** functoid to a record in the destination schema, or by dragging a record in the destination schema to the **Mass Copy** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7293d-117">Contrairement à d’autres fonctoids, vous ne pouvez pas utiliser la sortie de la **copie de masse** fonctoid comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="7293d-117">Unlike other functoids, you cannot use the output of the **Mass Copy** functoid as input to another functoid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7293d-118">Vous pouvez insérer et configurer le **copie de masse** fonctoid en liant deux enregistrements directement.</span><span class="sxs-lookup"><span data-stu-id="7293d-118">You can insert and configure the **Mass Copy** functoid by linking two records directly.</span></span> <span data-ttu-id="7293d-119">Pour plus d’informations, consultez la section « pour lier à l’aide d’un fonctoid copie de masse » dans [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).</span><span class="sxs-lookup"><span data-stu-id="7293d-119">For more information, see the section “To link using a mass copy functoid” in [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7293d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7293d-120">See Also</span></span>  
 [<span data-ttu-id="7293d-121">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="7293d-121">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
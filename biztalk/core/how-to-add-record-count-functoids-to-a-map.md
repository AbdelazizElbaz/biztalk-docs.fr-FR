---
title: "Ajout de fonctoids nombre d’enregistrements à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fbfd2a0-fac5-49f1-bcbb-873c287cd278
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd315a637b3efd069361dfa2d780cff179559da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-record-count-functoids-to-a-map"></a><span data-ttu-id="6f1cb-102">Ajout de fonctoids Nombre d'enregistrements à un mappage</span><span class="sxs-lookup"><span data-stu-id="6f1cb-102">How to Add Record Count Functoids to a Map</span></span>
<span data-ttu-id="6f1cb-103">Le **nombre d’enregistrements** fonctoid vous permet de générer le nombre d’occurrences d’un enregistrement dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-103">The **Record Count** functoid enables you to generate a count of the number of times a record occurs in an instance message.</span></span>  
  
 <span data-ttu-id="6f1cb-104">Pour obtenir des informations conceptuelles sur le **nombre d’enregistrements** fonctoid, consultez [Functoid nombre d’enregistrements](../core/record-count-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="6f1cb-104">For conceptual information about the **Record Count** functoid, see [Record Count Functoid](../core/record-count-functoid.md).</span></span>  
  
### <a name="to-add-the-record-count-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="6f1cb-105">Pour ajouter le fonctoid Nombre d’enregistrements à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="6f1cb-105">To add the Record Count functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="6f1cb-106">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="6f1cb-107">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-107">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="6f1cb-108">Faites glisser le **nombre d’enregistrements** fonctoid (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-108">Drag the **Record Count** functoid (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f1cb-109">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="6f1cb-110">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette autre page.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-110">If you want to put the functoid onto a different grid page, you need to display the other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f1cb-111">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-111">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="6f1cb-112">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="6f1cb-113">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="6f1cb-114">Pour définir le paramètre d’entrée pour le **nombre d’enregistrements** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement de boucle du schéma source vers le **nombre d’enregistrements** fonctoid, ou en faisant glisser le  **Nombre d’enregistrements** fonctoid vers un enregistrement de boucle dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-114">To establish the input parameter for the **Record Count** functoid, create an input link by dragging a looping record from the source schema to the **Record Count** functoid, or dragging the **Record Count** functoid to a looping record in the source schema.</span></span>  
  
4.  <span data-ttu-id="6f1cb-115">Pour utiliser le paramètre de sortie à partir de la **nombre d’enregistrements** fonctoid, créez un lien de sortie en faisant glisser le **nombre d’enregistrements** fonctoid vers un champ du schéma de destination, ou en faisant glisser un champ dans la destination schéma pour le **nombre d’enregistrements** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-115">To use the output parameter from the **Record Count** functoid, create an output link by dragging the **Record Count** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Record Count** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f1cb-116">Comme avec d’autres fonctoids, la sortie de la **nombre d’enregistrements** fonctoid peut être utilisé comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="6f1cb-116">As with other functoids, the output of the **Record Count** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1cb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f1cb-117">See Also</span></span>  
 [<span data-ttu-id="6f1cb-118">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="6f1cb-118">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
---
title: "Ajout de fonctoids Index à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfccfcc-c333-422f-b40b-13ca4152e588
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6695f7830dcc35fbb0100c012cff10fa207f1ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-index-functoids-to-a-map"></a><span data-ttu-id="e145d-102">Ajout de fonctoids Index à un mappage</span><span class="sxs-lookup"><span data-stu-id="e145d-102">How to Add Index Functoids to a Map</span></span>
<span data-ttu-id="e145d-103">Le **Index** fonctoid vous permet de sélectionner des informations à partir d’un enregistrement spécifique dans une série d’enregistrements de boucle.</span><span class="sxs-lookup"><span data-stu-id="e145d-103">The **Index** functoid enables you to select information from a specific record in a series of looping records.</span></span> <span data-ttu-id="e145d-104">Chaque **Index** fonctoid sélectionne des informations à partir d’un champ unique.</span><span class="sxs-lookup"><span data-stu-id="e145d-104">Each **Index** functoid selects information from a single field.</span></span>  
  
 <span data-ttu-id="e145d-105">Pour obtenir des informations conceptuelles sur le **Index** fonctoid, consultez [fonctoid Index](../core/index-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="e145d-105">For conceptual information about the **Index** functoid, see [Index Functoid](../core/index-functoid.md).</span></span>  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="e145d-106">Pour ajouter le fonctoid Index à un mappage et le configurer</span><span class="sxs-lookup"><span data-stu-id="e145d-106">To add the Index functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="e145d-107">Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.</span><span class="sxs-lookup"><span data-stu-id="e145d-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="e145d-108">La liste de fonctoids de la catégorie choisie s'affiche.</span><span class="sxs-lookup"><span data-stu-id="e145d-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="e145d-109">Faites glisser le **Index** fonctoid (![](../core/media/bts-tls-index.gif "bts_tls_index")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="e145d-109">Drag the **Index** functoid (![](../core/media/bts-tls-index.gif "bts_tls_index")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e145d-110">Le fonctoid sera placé sur la page de grille affichée.</span><span class="sxs-lookup"><span data-stu-id="e145d-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="e145d-111">Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette autre page.</span><span class="sxs-lookup"><span data-stu-id="e145d-111">If you want to put the functoid onto a different grid page, you need to display the other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e145d-112">Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur emplacement relatif de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="e145d-112">If you are constructing a map using more than one functoid together, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="e145d-113">Les fonctoids sont exécutés de la gauche vers la droite.</span><span class="sxs-lookup"><span data-stu-id="e145d-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="e145d-114">La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.</span><span class="sxs-lookup"><span data-stu-id="e145d-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="e145d-115">Pour définir le paramètre d’entrée de champ pour le **Index** fonctoid, créez un lien d’entrée en faisant glisser un champ d’un enregistrement de boucle du schéma source vers le **Index** fonctoid, ou en faisant glisser le **Index** fonctoid à un champ d’enregistrement de boucle dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="e145d-115">To establish the field input parameter for the **Index** functoid, create an input link by dragging a field within a looping record from the source schema to the **Index** functoid, or dragging the **Index** functoid to a field within the looping record in the source schema.</span></span>  
  
4.  <span data-ttu-id="e145d-116">Pour établir au moins un paramètre d’entrée d’index pour la **Index** fonctoid, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e145d-116">To establish at least one index input parameter for the **Index** functoid, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="e145d-117">Avec la **Index** fonctoid sélectionné, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e145d-117">With the **Index** functoid selected, click the ellipsis (**...**) button associated with the **Input Parameters** property in the **Properties** window.</span></span>  
  
    2.  <span data-ttu-id="e145d-118">Dans le **configurer le fonctoid Index** boîte de dialogue, cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") bouton.</span><span class="sxs-lookup"><span data-stu-id="e145d-118">In the **Configure Index Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button.</span></span>  
  
    3.  <span data-ttu-id="e145d-119">Dans la zone d'édition, tapez le paramètre d'entrée de l'index sous forme de valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="e145d-119">In the edit box, type the index input parameter as a numeric value.</span></span> <span data-ttu-id="e145d-120">Répétez l’opération si les valeurs d’index supplémentaires sont nécessaires, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e145d-120">Repeat as necessary if additional index values are required, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e145d-121">Pour utiliser le paramètre de sortie à partir de la **Index** fonctoid, créez un lien de sortie en faisant glisser le **Index** fonctoid vers un champ du schéma de destination, ou en faisant glisser un champ du schéma de destination pour le  **Index** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e145d-121">To use the output parameter from the **Index** functoid, create an output link by dragging the **Index** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Index** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e145d-122">Comme avec d’autres fonctoids, la sortie de la **Index** fonctoid peut être utilisé comme entrée d’un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="e145d-122">As with other functoids, the output of the **Index** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e145d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e145d-123">See Also</span></span>  
 [<span data-ttu-id="e145d-124">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="e145d-124">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)
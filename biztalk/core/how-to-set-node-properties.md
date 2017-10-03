---
title: "Comment définir les propriétés d’un nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0c79eac-d9ba-45e2-a6e9-770b2bcb2067
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dc0f13814808a69c4c4b9c3976e9047acde5b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-node-properties"></a><span data-ttu-id="99b12-102">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="99b12-102">How to Set Node Properties</span></span>
<span data-ttu-id="99b12-103">Après avoir inséré un nœud dans un schéma BizTalk, vous devrez souvent modifier ses propriétés par rapport à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="99b12-103">After inserting a node into a BizTalk schema, you will often need to change the properties of that node from their default values.</span></span> <span data-ttu-id="99b12-104">Chaque type de nœud possède un ensemble distinct de propriétés. Dans chacun de ces ensembles, les paramètres d'une propriété peuvent affecter la disponibilité des autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="99b12-104">Each type of node has a distinct set of properties, and within one of those sets, the settings of one property can affect the availability of other properties.</span></span> <span data-ttu-id="99b12-105">Par exemple, avant de définir la **Default Wrap Character** propriété de la **schéma** nœud, vous devez définir le **Default Wrap Character Type** propriété soit **Caractère** ou **hexadécimal**, ce qui permet l’établissement le format dans lequel vous avez l’intention de représenter la propriété précédente.</span><span class="sxs-lookup"><span data-stu-id="99b12-105">For example, before setting the **Default Wrap Character** property of the **Schema** node, you must set the **Default Wrap Character Type** property to either **Character** or **Hexadecimal**, thereby establishing the format in which you intend to represent the former property.</span></span> <span data-ttu-id="99b12-106">En outre, ces propriétés n’est disponible, ni l’ensemble de **analyser** catégorie de propriété à laquelle ils appartiennent, sauf si **Extension de fichier plat** est activé à l’aide de la **l’éditeur de schéma Extensions** propriété.</span><span class="sxs-lookup"><span data-stu-id="99b12-106">Further, neither of these properties is available, nor is the entire **Parse** property category to which they belong, unless **Flat File Extension** is enabled by using the **Schema Editor Extensions** property.</span></span>  

 <span data-ttu-id="99b12-107">Les propriétés de nœud sont nombreuses et peuvent être complexes, comme l'est le langage XSD (XML Schema Definition) qu'elles prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="99b12-107">Node properties are extensive and can be complex, as is the XML Schema definition (XSD) language that they support.</span></span> <span data-ttu-id="99b12-108">Cette rubrique se borne à décrire brièvement les étapes générales nécessaires à l'examen et à la définition de propriétés de nœud.</span><span class="sxs-lookup"><span data-stu-id="99b12-108">This topic only briefly describes the general steps involved in examining and setting node properties.</span></span> <span data-ttu-id="99b12-109">Pour plus d’informations sur ces propriétés, y compris, par exemple, pour plus d’informations sur leur valeur par défaut et les valeurs autorisées, consultez la **référence du schéma de propriété**.</span><span class="sxs-lookup"><span data-stu-id="99b12-109">For detailed information about these properties, including, for example, information about their default and allowed values, see the **Schema Property Reference**.</span></span> <span data-ttu-id="99b12-110">Pour encore plus d’informations sur les concepts XSD et les éléments qui sous-tendent la plupart de ces propriétés, reportez-vous directement aux informations sur les [XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="99b12-110">For even more detailed information about the XSD concepts and elements that underlie most of these node properties, refer directly to information about [XSD on the Web](../core/xsd-resources-on-the-web.md).</span></span>  

<span data-ttu-id="99b12-111">Plus d’informations sur ces propriétés et la référence du schéma de propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="99b12-111">More info on these properties, and the schema property reference [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

  
## <a name="examine-a-node-property-value"></a><span data-ttu-id="99b12-112">Examiner une valeur de propriété de nœud</span><span class="sxs-lookup"><span data-stu-id="99b12-112">Examine a node property value</span></span>  
  
1.  <span data-ttu-id="99b12-113">Dans l'Éditeur BizTalk, ouvrez le schéma qui contient la propriété que vous voulez examiner et sélectionnez le nœud qui contient cette propriété.</span><span class="sxs-lookup"><span data-stu-id="99b12-113">In BizTalk Editor, open the schema that contains the property you want to examine, and then select the node that contains that property.</span></span>  
  
2.  <span data-ttu-id="99b12-114">Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99b12-114">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
3.  <span data-ttu-id="99b12-115">Si nécessaire, faites défiler la fenêtre Propriétés pour rechercher la propriété qui vous intéresse et notez sa valeur.</span><span class="sxs-lookup"><span data-stu-id="99b12-115">If necessary, scroll the Properties window to find the property of interest, and note its value.</span></span>  
  
     <span data-ttu-id="99b12-116">Les boutons du haut de la fenêtre Propriétés permettent de modifier le mode de tri des propriétés : alphabétique dans chacune de leurs catégories ou alphabétique sans tenir compte (ou sans affichage) de leurs catégories.</span><span class="sxs-lookup"><span data-stu-id="99b12-116">You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.</span></span>  
  
## <a name="set-a-node-property-value"></a><span data-ttu-id="99b12-117">Valeur de propriété de nœud</span><span class="sxs-lookup"><span data-stu-id="99b12-117">Set a node property value</span></span>  
  
1.  <span data-ttu-id="99b12-118">Dans l'Éditeur BizTalk, ouvrez le schéma qui contient la propriété que vous voulez définir et sélectionnez le nœud qui contient cette propriété.</span><span class="sxs-lookup"><span data-stu-id="99b12-118">In BizTalk Editor, open the schema that contains the property you want to set, and then select the node that contains that property.</span></span>  
  
2.  <span data-ttu-id="99b12-119">Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99b12-119">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
3.  <span data-ttu-id="99b12-120">Si nécessaire, faites défiler la fenêtre Propriétés pour rechercher la propriété qui vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="99b12-120">If necessary, scroll the Properties window to find the property of interest.</span></span>  
  
     <span data-ttu-id="99b12-121">Les boutons du haut de la fenêtre Propriétés permettent de modifier le mode de tri des propriétés : alphabétique dans chacune de leurs catégories ou alphabétique sans tenir compte (ou sans affichage) de leurs catégories.</span><span class="sxs-lookup"><span data-stu-id="99b12-121">You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.</span></span>  
  
4.  <span data-ttu-id="99b12-122">Définissez la valeur de la propriété dans le champ de valeur situé à droite du nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="99b12-122">Set the value of the property in the value field, which is to the right of the property name.</span></span> <span data-ttu-id="99b12-123">Selon le type de cette dernière, vous pouvez taper une valeur ou en choisir une dans la liste déroulante qui s'affiche lorsque le champ de valeur est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="99b12-123">Depending on the type of the property, you might type a value or choose a value from the drop-down list that is displayed when the value field is selected.</span></span> <span data-ttu-id="99b12-124">Certaines propriétés permettent de procéder d'une manière ou d'une autre.</span><span class="sxs-lookup"><span data-stu-id="99b12-124">Some properties allow either operation.</span></span> <span data-ttu-id="99b12-125">Certaines propriétés affichent les points de suspension (**...** ) bouton cliquer pour ouvrir une boîte de dialogue dans laquelle des valeurs, telles que des collections plus compliquées peut être définie.</span><span class="sxs-lookup"><span data-stu-id="99b12-125">Some properties display an ellipsis (**...**) button that when clicked opens a dialog box in which more complicated values, such as collections, can be set.</span></span>  
  
5.  <span data-ttu-id="99b12-126">Si vous avez tapé une nouvelle valeur pour la propriété, terminez en appuyant sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="99b12-126">If you have typed a new value for the property, finish by pressing ENTER.</span></span>  
  
##  <a name="clear-a-node-property-value"></a><span data-ttu-id="99b12-127">Effacer une valeur de propriété de nœud</span><span class="sxs-lookup"><span data-stu-id="99b12-127">Clear a node property value</span></span>  
  
1.  <span data-ttu-id="99b12-128">Sélectionnez le nœud contenant la propriété qui vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="99b12-128">Select the node that contains the property of interest.</span></span>  
  
2.  <span data-ttu-id="99b12-129">Dans la fenêtre Propriétés, double-cliquez sur la valeur de propriété que vous souhaitez effacer, avec le bouton droit de la valeur de propriété, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="99b12-129">In the Properties window, double-click the property value that you want to clear, right-click the property value, and then click **Delete**.</span></span>  
  
## <a name="restore-a-node-property-to-its-default-value"></a><span data-ttu-id="99b12-130">Restauration d’une propriété de nœud à sa valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="99b12-130">Restore a node property to its default value</span></span>  
  
1.  <span data-ttu-id="99b12-131">Sélectionnez le nœud contenant la propriété qui vous intéresse.</span><span class="sxs-lookup"><span data-stu-id="99b12-131">Select the node that contains the property of interest.</span></span>  
  
2.  <span data-ttu-id="99b12-132">Dans la fenêtre Propriétés, cliquez sur le nom de propriété que vous souhaitez rétablir la valeur par défaut, puis cliquez sur **réinitialiser**.</span><span class="sxs-lookup"><span data-stu-id="99b12-132">In the Properties window, right-click the property name that you want to reset to its default value, and then click **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b12-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99b12-133">See Also</span></span>  
 [<span data-ttu-id="99b12-134">Utilisation des nœuds existants</span><span class="sxs-lookup"><span data-stu-id="99b12-134">Working with Existing Nodes</span></span>](../core/working-with-existing-nodes.md)
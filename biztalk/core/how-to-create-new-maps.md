---
title: "Comment créer de nouveaux mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 910d79782f4332ae1d706e12a8c5dda8c399a41b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-new-maps"></a><span data-ttu-id="6f1aa-102">Comment créer de nouveaux mappages</span><span class="sxs-lookup"><span data-stu-id="6f1aa-102">How to Create New Maps</span></span>

## <a name="overview"></a><span data-ttu-id="6f1aa-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="6f1aa-103">Overview</span></span>
<span data-ttu-id="6f1aa-104">Pour construire un mappage BizTalk, vous devez suivre trois étapes détaillées :</span><span class="sxs-lookup"><span data-stu-id="6f1aa-104">To build a new BizTalk map, there are three high-level steps to perform:</span></span>  
  
1.  <span data-ttu-id="6f1aa-105">Créer le nouveau mappage au sein d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-105">Create the new map within a BizTalk project.</span></span>  
  
2.  <span data-ttu-id="6f1aa-106">Ajoutez les schémas source et de destination à la carte.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-106">Add the source and destination schemas to the map.</span></span>  
  
3.  <span data-ttu-id="6f1aa-107">Établir l’ensemble de liens et, le cas échéant, les fonctoids intermédiaires spécifiant la façon dont le schéma source est mappé au schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-107">Build the set of links and, perhaps, intermediate functoids specifying how the source schema maps to the destination schema.</span></span>  
  
 <span data-ttu-id="6f1aa-108">Dans le contexte actuel, les deux premières étapes correspondent à la « création » du mappage.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-108">In the current context, the first two of these three steps is considered "creating" the map.</span></span> <span data-ttu-id="6f1aa-109">La troisième étape correspond à la « construction » du mappage.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-109">The third step is considered "building" the map.</span></span> <span data-ttu-id="6f1aa-110">Pour obtenir des instructions détaillées sur la plupart des tâches liées au processus de construction du mappage, consultez [à l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="6f1aa-110">For step-by-step instructions on many of the tasks related to the process of building the map, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).</span></span>  
  
## <a name="create-a-new-map"></a><span data-ttu-id="6f1aa-111">Créer un nouveau mappage</span><span class="sxs-lookup"><span data-stu-id="6f1aa-111">Create a new map</span></span> 
  
1.  <span data-ttu-id="6f1aa-112">Cliquez sur un projet BizTalk dans l’Explorateur de solutions, sélectionnez **ajouter**, puis sélectionnez **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-112">Right-click a BizTalk project in Solution Explorer, select **Add**, and then select **New Item**.</span></span>  
  
2.  <span data-ttu-id="6f1aa-113">Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** zone, sélectionnez **carte**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-113">In the **Add New Item** dialog box, in the **Templates** area, select **Map**.</span></span>  
  
3.  <span data-ttu-id="6f1aa-114">Sélectionnez le texte dans le **nom** zone, tapez un nom pour le mappage, puis sélectionnez **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-114">Select the text in the **Name** box, type a name for the map, and then select **Add**.</span></span>  
  
     <span data-ttu-id="6f1aa-115">Le Mappeur BizTalk s'ouvre dans la fenêtre d'édition Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], et présente trois volets distincts, côte à côte.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-115">BizTalk Mapper opens in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window, showing three distinct panes, side-by-side.</span></span> <span data-ttu-id="6f1aa-116">De gauche à droite, ces volets affichent le schéma source, la grille (qui peut comporter plusieurs pages) et le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-116">From left to right, these panes show the source schema, the grid (which may have multiple pages), and the destination schema.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6f1aa-117">Vous ne pouvez pas utiliser les noms suivants pour les mappages : « XmlContent », « SourceSchemas », « TargetSchemas » ou « Et ».</span><span class="sxs-lookup"><span data-stu-id="6f1aa-117">You cannot use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent".</span></span> <span data-ttu-id="6f1aa-118">Ces noms ne peuvent pas être utilisés, car la compilation dans un assembly .NET engendre des restrictions de nom résultant du code C# généré.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-118">These names cannot be used because compilation into a .NET assembly produces naming restrictions as the result of generated C# code.</span></span>  
  
4.  <span data-ttu-id="6f1aa-119">Dans le Mappeur BizTalk, dans le volet gauche, sélectionnez **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-119">In BizTalk Mapper, in the left pane, select **Open Source Schema**.</span></span>  
  
5.  <span data-ttu-id="6f1aa-120">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud, sélectionnez le schéma source approprié, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-120">In the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the appropriate source schema, and then select **OK**.</span></span>  

    > [!TIP] 
    > <span data-ttu-id="6f1aa-121">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre du sélecteur de Type pour afficher le nom complet de votre schéma.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-121">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize the Type Picker window to see the full name of your schema.</span></span>
  
     <span data-ttu-id="6f1aa-122">Si une seule une racine unique existe dans le schéma source ou un nœud racine a été établi pour le schéma à l’aide la **référence de racine** propriété de la **schéma** nœud, le schéma source s’ouvre dans le volet gauche et que vous procéder à l’étape 7.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-122">If only a single root exists in the source schema, or a root node has been established for the schema using the **Root Reference** property of the **Schema** node, the source schema opens in the left pane, and you can proceed to step 7.</span></span>  
  
6.  <span data-ttu-id="6f1aa-123">Si le schéma source a plusieurs nœuds racine et qu’aucun nœud racine n’a été établie pour le schéma source à l’aide du **schéma** du nœud **référence de racine** propriété, dans le **nœud racine pour la Source Schéma** boîte de dialogue, sélectionnez le nœud racine approprié, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-123">If the source schema has multiple root nodes, and no root node has been established for the source schema using the **Schema** node's **Root Reference** property, in the **Root Node for Source Schema** dialog box, select the appropriate root node, and select **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6f1aa-124">Si vous choisissez un nœud racine d’un schéma dans le Mappeur BizTalk et que vous modifiez ensuite la **référence de racine** la propriété dans le schéma, la prochaine fois que vous ouvrez le schéma dans le Mappeur BizTalk, le nœud racine pas à jour pour la nouvelle référence racine configurée dans l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-124">If you choose a root node for a schema in BizTalk Mapper and then later change the **Root Reference** property in the schema, the next time you open the schema in BizTalk Mapper, the root node will not update to the new root reference configured in BizTalk Editor.</span></span>  
  
7.  <span data-ttu-id="6f1aa-125">Dans le Mappeur BizTalk, dans le volet droit, sélectionnez **ouvrir le schéma de Destination**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-125">In BizTalk Mapper, in the right pane, select **Open Destination Schema**.</span></span>  
  
8.  <span data-ttu-id="6f1aa-126">Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schéma** nœud dans l’arborescence, si nécessaire, sélectionnez le schéma de destination approprié, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-126">In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the tree, if necessary, select the appropriate destination schema, and then select **OK**.</span></span>  
  
     <span data-ttu-id="6f1aa-127">Si seule une racine unique existe dans le schéma de destination, ou un nœud racine a été établi pour le schéma de destination à l’aide de la **référence de racine** propriété de la **schéma** ouvre de nœud, le schéma de destination dans le volet droit, et vous ne devrez pas effectuer l’étape 9.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-127">If only a single root exists in the destination schema, or a root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, the destination schema opens in the right pane, and you will not need to perform step 9.</span></span>  
  
9. <span data-ttu-id="6f1aa-128">Si le schéma de destination comporte plusieurs nœuds racine et qu’aucun nœud racine n’a été établie pour le schéma de destination à l’aide de la **référence de racine** propriété de la **schéma** nœud, dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez le nœud racine approprié, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-128">If the destination schema has multiple root nodes, and no root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, in the **Root Node for Target Schema** dialog box, select the appropriate root node, and select **OK**.</span></span>  
  
     <span data-ttu-id="6f1aa-129">Le schéma de destination s’ouvre dans le volet de droite.</span><span class="sxs-lookup"><span data-stu-id="6f1aa-129">The destination schema opens in the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1aa-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f1aa-130">See Also</span></span>  
 [<span data-ttu-id="6f1aa-131">La gestion des mappages dans des projets</span><span class="sxs-lookup"><span data-stu-id="6f1aa-131">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)
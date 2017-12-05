---
title: "Comment gérer des liens existants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0db213b9-df84-4ebd-a59f-7691774d5031
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cdc505f98f61dd7259c8893b526ff094128df42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-existing-links"></a><span data-ttu-id="e49b1-102">Gestion des liens existants</span><span class="sxs-lookup"><span data-stu-id="e49b1-102">How to Manage Existing Links</span></span>
<span data-ttu-id="e49b1-103">Il peut arriver que vous ayez besoin de modifier la source ou la destination d’un lien, de nommer ou de renommer un lien ou encore de supprimer un lien.</span><span class="sxs-lookup"><span data-stu-id="e49b1-103">Sometimes you may need to change the source or destination of a link, name or rename a link, or delete a link.</span></span> <span data-ttu-id="e49b1-104">Cette rubrique contient des instructions détaillées concernant la réalisation de ces types d'opérations.</span><span class="sxs-lookup"><span data-stu-id="e49b1-104">This topic provides step-by-step instructions for performing these types of link operations.</span></span>  
  
### <a name="to-change-the-source-or-destination-of-a-link"></a><span data-ttu-id="e49b1-105">Pour modifier la source ou la destination d’un lien</span><span class="sxs-lookup"><span data-stu-id="e49b1-105">To change the source or destination of a link</span></span>  
  
1.  <span data-ttu-id="e49b1-106">Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="e49b1-106">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="e49b1-107">Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="e49b1-107">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="e49b1-108">Faites glisser un des deux points de terminaison vers le nouveau nœud de schéma ou le fonctoid auquel vous voulez le connecter.</span><span class="sxs-lookup"><span data-stu-id="e49b1-108">Drag either endpoint of the link to the new schema node or functoid to which you want it to connect it.</span></span>  
  
     <span data-ttu-id="e49b1-109">Tandis que vous faites glisser le point de terminaison, le curseur prend la forme d'une croix.</span><span class="sxs-lookup"><span data-stu-id="e49b1-109">As you drag an endpoint, the cursor becomes a crosshair.</span></span> <span data-ttu-id="e49b1-110">Si vous le pointez sur un nœud de schéma ou un fonctoid (ou tout autre objet) qui ne peut pas accepter le lien, le curseur prend la forme d'un cercle barré.</span><span class="sxs-lookup"><span data-stu-id="e49b1-110">If you point to a schema node or functoid (or other object) which cannot accept the link, the cursor becomes a circle with a line through it.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e49b1-111">Si plusieurs liens d’entrée sont connectés à un fonctoid et que vous redirigiez un ou plusieurs de ces liens d'entrée vers d'autres nœuds du schéma source ou vers d'autres fonctoids, il se peut que l'ordre des paramètres d'entrée dans le fonctoid d'origine ne soit pas conservé.</span><span class="sxs-lookup"><span data-stu-id="e49b1-111">If you have two or more input links connected to a functoid and you redirect one or more of those input links to other nodes in the source schema or to other functoids, the order of the input parameters to the original functoid may not be preserved.</span></span> <span data-ttu-id="e49b1-112">Utilisez le **configurer \<fonctoid\> fonctoid** boîte de dialogue pour vérifier l’ordre des paramètres d’entrée et les réorganiser si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e49b1-112">Use the **Configure \<Functoid\> Functoid** dialog box to review the resulting order of the input parameters and to reorder them if necessary.</span></span> <span data-ttu-id="e49b1-113">Pour plus d’informations sur la réorganisation des paramètres d’entrée d’un fonctoid, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e49b1-113">For more information about reordering the input parameters of a functoid, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span>  
  
### <a name="to-setedit-the-label-of-a-link"></a><span data-ttu-id="e49b1-114">Pour définir/modifier l'étiquette d'un lien</span><span class="sxs-lookup"><span data-stu-id="e49b1-114">To set/edit the label of a link</span></span>  
  
1.  <span data-ttu-id="e49b1-115">Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="e49b1-115">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="e49b1-116">Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="e49b1-116">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="e49b1-117">Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, fournissez un nom (nouveau) pour la liaison à l’aide de la **étiquette** propriété.</span><span class="sxs-lookup"><span data-stu-id="e49b1-117">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a (new) name for the link using the **Label** property.</span></span>  
  
### <a name="to-delete-a-link"></a><span data-ttu-id="e49b1-118">Pour supprimer un lien</span><span class="sxs-lookup"><span data-stu-id="e49b1-118">To delete a link</span></span>  
  
1.  <span data-ttu-id="e49b1-119">Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="e49b1-119">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="e49b1-120">Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="e49b1-120">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="e49b1-121">Sur le **modifier** menu, cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="e49b1-121">On the **Edit** menu, click **Delete**.</span></span>  
  
     <span data-ttu-id="e49b1-122">Vous pouvez également appuyer sur la touche SUPPR ou cliquez sur le lien et cliquez sur **supprimer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="e49b1-122">You can also press the DELETE key or right-click the link and click **Delete** on the shortcut menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e49b1-123">Il est possible de sélectionner plusieurs liens et/ou fonctoids afin de les supprimer simultanément.</span><span class="sxs-lookup"><span data-stu-id="e49b1-123">You can bulk-select multiple link(s) and/or functoid(s) and then delete them in one operation.</span></span> <span data-ttu-id="e49b1-124">Vous pourrez ensuite annuler et rétablir cette opération.</span><span class="sxs-lookup"><span data-stu-id="e49b1-124">You can undo or redo the bulk deletion of link(s) and/or functoid(s).</span></span> <span data-ttu-id="e49b1-125">Pour plus d’informations sur Annuler et rétablir des opérations, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e49b1-125">For more information about undo and redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49b1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e49b1-126">See Also</span></span>  
 [<span data-ttu-id="e49b1-127">Utilisation de liens pour spécifier des mappages d’enregistrements et de champs</span><span class="sxs-lookup"><span data-stu-id="e49b1-127">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)
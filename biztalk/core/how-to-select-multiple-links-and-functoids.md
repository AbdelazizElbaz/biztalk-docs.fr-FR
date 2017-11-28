---
title: "Comment sélectionner plusieurs liens et fonctoids | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9ae50cb-c212-48f3-9dfb-74df282645c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8885fe33d0c3a2dc081fbca66a398003c3e21913
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-multiple-links-and-functoids"></a><span data-ttu-id="126f6-102">Sélection de plusieurs liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="126f6-102">How to Select Multiple Links and Functoids</span></span>
<span data-ttu-id="126f6-103">Pour exécuter une opération similaire sur un groupe de fonctoids et/ou liens dans un mappage, vous pouvez en sélectionner l'intégralité.</span><span class="sxs-lookup"><span data-stu-id="126f6-103">When you want to perform a similar operation on a group of functoids and/or links in a map, you can select that group of functoids and/or links all at the same time.</span></span> <span data-ttu-id="126f6-104">Cette rubrique fournit les informations vous permettant d'effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="126f6-104">This topic provides information about how to perform this operation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="126f6-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="126f6-105">Prerequisites</span></span>  
 <span data-ttu-id="126f6-106">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="126f6-106">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="why-do-you-need-to-bulk-select-linksfunctoids"></a><span data-ttu-id="126f6-107">Pourquoi est-il nécessaire d'utiliser la sélection multiple de fonctoids et/ou de liens ?</span><span class="sxs-lookup"><span data-stu-id="126f6-107">Why do you need to bulk-select links/functoids?</span></span>  
 <span data-ttu-id="126f6-108">Vous pouvez sélectionner plusieurs fonctoids et/ou liens pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="126f6-108">You can bulk-select links and/or functoids to do any of the following:</span></span>  
  
-   <span data-ttu-id="126f6-109">Copier, couper et coller la sélection dans la même page de grille ou dans une autre page de grille dans le même mappage.</span><span class="sxs-lookup"><span data-stu-id="126f6-109">Copy/cut and paste the selection in the same grid page or another grid page in the same map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="126f6-110">Pour plus d’informations sur la façon de copier, couper et collage de liens et fonctoids, consultez [comment copier, couper et collez les liens et fonctoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="126f6-110">For information on how to copy, cut, and paste links and functoids, see [How to Copy, Cut, and Paste Links and Functoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span></span>  
  
-   <span data-ttu-id="126f6-111">Déplacer la sélection entre plusieurs pages de grille</span><span class="sxs-lookup"><span data-stu-id="126f6-111">Move the selection between grid pages</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="126f6-112">Pour plus d’informations sur la façon de déplacer une relation à partir d’une page de grille vers un autre, consultez [comment déplacer une relation entre les Pages de grille](../core/how-to-move-a-relationship-between-grid-pages.md).</span><span class="sxs-lookup"><span data-stu-id="126f6-112">For information on how to move a relationship from one grid page to another, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
-   <span data-ttu-id="126f6-113">Modifier les propriétés communes aux fonctoids et liens dans la sélection</span><span class="sxs-lookup"><span data-stu-id="126f6-113">Edit the common properties of functoids and links in the selection</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="126f6-114">Pour plus d’informations sur la définition des commentaires et des étiquettes pour les liens et fonctoids, consultez [l’étiquette à un lien](../core/how-to-label-a-link.md) ou [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="126f6-114">For information on how to set comments and labels for functoids and links, see [How to Label a Link](../core/how-to-label-a-link.md) or [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
-   <span data-ttu-id="126f6-115">Supression de plusieurs lien(s) et/ou fonctoid(s) en une seule étape</span><span class="sxs-lookup"><span data-stu-id="126f6-115">Deleting multiple link(s) and/or functoid(s) in one step</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="126f6-116">Pour plus d’informations sur la suppression de fonctoids, consultez [comment supprimer des fonctoids](../core/how-to-delete-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="126f6-116">For information on how to delete functoids, see [How to Delete Functoids](../core/how-to-delete-functoids.md).</span></span>  
  
## <a name="to-select-multiple-links-and-functoids"></a><span data-ttu-id="126f6-117">Pour sélectionner plusieurs liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="126f6-117">To select multiple links and functoids</span></span>  
 <span data-ttu-id="126f6-118">Vous pouvez sélectionner plusieurs fonctoids et/ou liens comme suit :</span><span class="sxs-lookup"><span data-stu-id="126f6-118">You can bulk-select functoids and/or links in any of the following ways:</span></span>  
  
-   <span data-ttu-id="126f6-119">Cliquez sur le lien ou le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="126f6-119">Click the link or the functoid.</span></span> <span data-ttu-id="126f6-120">Maintenez la touche CTRL enfoncée, puis cliquez sur les liens et/ou fonctoids que vous souhaitez sélectionner.</span><span class="sxs-lookup"><span data-stu-id="126f6-120">Hold down the CTRL key, and then click the other links and/or functoids you want to select.</span></span>  
  
     <span data-ttu-id="126f6-121">La figure suivante affiche en surbrillance les liens et fonctoids sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="126f6-121">The following figure shows the selected functoids and links highlighted.</span></span>  
  
     <span data-ttu-id="126f6-122">![En bloc en sélectionnant les liens et fonctoids](../core/media/bulkselect-functois-links.gif "BulkSelect_Functois & liens")</span><span class="sxs-lookup"><span data-stu-id="126f6-122">![Bulk selecting functoids and links](../core/media/bulkselect-functois-links.gif "BulkSelect_Functois&Links")</span></span>  
  
-   <span data-ttu-id="126f6-123">Faites glisser la souris sur la surface du mappage.</span><span class="sxs-lookup"><span data-stu-id="126f6-123">Drag the mouse on the map surface.</span></span> <span data-ttu-id="126f6-124">Les fonctoids situés sous le rectangle de sélection sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="126f6-124">The functoids under the selection rectangle are highlighted.</span></span>  
  
     <span data-ttu-id="126f6-125">![Sélection d’un rectangle de fonctoids](../core/media/bulkselect-selectionrectangle.gif "BulkSelect_SelectionRectangle")</span><span class="sxs-lookup"><span data-stu-id="126f6-125">![Rectangle selection of functoids](../core/media/bulkselect-selectionrectangle.gif "BulkSelect_SelectionRectangle")</span></span>  
  
-   <span data-ttu-id="126f6-126">Vous pouvez utiliser une combinaison d'opérations de glisser et de CTRL+clic.</span><span class="sxs-lookup"><span data-stu-id="126f6-126">You can use a combination of dragging and CTRL-click.</span></span> <span data-ttu-id="126f6-127">Faites glisser la souris sur la surface du mappage, puis sélectionnez les fonctoids et/ou liens dans cette plage.</span><span class="sxs-lookup"><span data-stu-id="126f6-127">Drag the mouse on the map surface and select the functoids and/or links in that range.</span></span> <span data-ttu-id="126f6-128">Maintenez la touche CTRL enfoncée, puis cliquez sur les liens et/ou fonctoids situés en dehors de la sélection.</span><span class="sxs-lookup"><span data-stu-id="126f6-128">Hold down the CTRL key, and then click the functoids and/or links outside the selection range.</span></span>  
  
## <a name="to-select-all-links-and-functoids-on-the-grid-page"></a><span data-ttu-id="126f6-129">Pour sélectionner tous les liens et fonctoids sur la page de grille</span><span class="sxs-lookup"><span data-stu-id="126f6-129">To select all links and functoids on the grid page</span></span>  
 <span data-ttu-id="126f6-130">Vous pouvez sélectionner tous les fonctoids et liens sur la page de grille du mappeur en utilisant l'une des procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="126f6-130">You can select all the functoids and links on the Mapper grid page in any of the following ways:</span></span>  
  
-   <span data-ttu-id="126f6-131">Avec le bouton droit n’importe où sur la page de grille et cliquez sur **sélectionner tout**.</span><span class="sxs-lookup"><span data-stu-id="126f6-131">Right-click anywhere on the grid page and click **Select All**.</span></span>  
  
-   <span data-ttu-id="126f6-132">Cliquez n'importe où sur la page de grille puis appuyez sur les touches CTRL+A du clavier.</span><span class="sxs-lookup"><span data-stu-id="126f6-132">Click anywhere on the grid page and click press CTRL+A from the keyboard.</span></span>  
  
-   <span data-ttu-id="126f6-133">Cliquez n'importe où sur la page de grille.</span><span class="sxs-lookup"><span data-stu-id="126f6-133">Click anywhere on the grid page.</span></span> <span data-ttu-id="126f6-134">Dans le menu Visual Studio, cliquez sur **modifier**, puis cliquez sur **sélectionner tout**.</span><span class="sxs-lookup"><span data-stu-id="126f6-134">From the Visual Studio menu, click **Edit**, and then click **Select All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126f6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="126f6-135">See Also</span></span>  
 [<span data-ttu-id="126f6-136">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="126f6-136">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)
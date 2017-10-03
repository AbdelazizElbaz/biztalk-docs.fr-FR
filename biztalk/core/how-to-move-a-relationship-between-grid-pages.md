---
title: "Comment déplacer une relation entre les Pages de grille | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.movetopage
ms.assetid: 185add4d-c876-44b6-b6e0-71c15a9b7c26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5737adcb9159568bfea7c7cdde9dff8015b19706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-relationship-between-grid-pages"></a><span data-ttu-id="0f047-102">Déplacement d'une relation entre les pages de grille</span><span class="sxs-lookup"><span data-stu-id="0f047-102">How to Move a Relationship Between Grid Pages</span></span>
<span data-ttu-id="0f047-103">Les grands mappages incluent plusieurs ensembles de fonctoids et liens, ce qui peut rendre difficile l'identification des liens connectant plusieurs fonctoids.</span><span class="sxs-lookup"><span data-stu-id="0f047-103">Large maps include many sets of functoids and links, which can make it difficult for you to identify the links joining multiple functoids.</span></span> <span data-ttu-id="0f047-104">En pareil cas, vous pouvez déplacer un ensemble similaire de fonctoids et liens vers une autre page de grille pour rendre le mappage plus lisible.</span><span class="sxs-lookup"><span data-stu-id="0f047-104">In such a scenario, you might want to move a similar set of functoids and links to a different grid page to make the map more readable.</span></span> <span data-ttu-id="0f047-105">Cette rubrique contient des instructions détaillées pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="0f047-105">This topic provides step-by-step instructions to perform the operation.</span></span>  
  
 <span data-ttu-id="0f047-106">Vous pouvez déplacer une relation d'une page de grille vers une autre, dans le même mappage uniquement, d'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f047-106">You can move a relationship from one grid page to another, in the same map only, in one of the following ways:</span></span>  
  
-   <span data-ttu-id="0f047-107">À l’aide de la **déplacer vers la Page** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="0f047-107">Using the **Move to Page** dialog box</span></span>  
  
-   <span data-ttu-id="0f047-108">en effectuant un glisser-déplacer du ou des fonctoids sélectionnés dans le ruban (et des liens associés).</span><span class="sxs-lookup"><span data-stu-id="0f047-108">Using the drag-and-drop of the ribbon-selected functoid(s) (and links)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f047-109">Vous pouvez déplacer un ou plusieurs fonctoids et leurs liens.</span><span class="sxs-lookup"><span data-stu-id="0f047-109">You can move one or more functoids and their links.</span></span> <span data-ttu-id="0f047-110">Lorsque vous déplacez une relation, les étiquettes, commentaires et valeurs constantes (ainsi que les espaces réservés appropriés) associés à cette relation sont conservés.</span><span class="sxs-lookup"><span data-stu-id="0f047-110">When you move a relationship, the labels, comments, and the constant values (along with the correct place holders) associated with that relationship are retained.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f047-111">Vous ne pouvez pas glisser-déplacer les seuls liens vers une autre page de grille.</span><span class="sxs-lookup"><span data-stu-id="0f047-111">You cannot drag-and-drop only links to another grid page.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0f047-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0f047-112">Prerequisites</span></span>  
 <span data-ttu-id="0f047-113">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0f047-113">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-move-a-relationship-using-move-to-page-dialog-box"></a><span data-ttu-id="0f047-114">Pour déplacer une relation à l'aide de la boîte de dialogue Déplacer vers la page</span><span class="sxs-lookup"><span data-stu-id="0f047-114">To move a relationship using Move To Page dialog box</span></span>  
  
1.  <span data-ttu-id="0f047-115">Dans le mappage, sélectionnez la page de grille depuis laquelle vous voulez déplacer une relation.</span><span class="sxs-lookup"><span data-stu-id="0f047-115">On the map, select the grid page from which you want to move a relationship.</span></span>  
  
2.  <span data-ttu-id="0f047-116">Cliquez sur un fonctoid ou un lien dans la relation que vous souhaitez déplacer, puis cliquez sur **déplacer vers la Page**.</span><span class="sxs-lookup"><span data-stu-id="0f047-116">Right-click a functoid or a link in the relationship you want to move and then click **Move to Page**.</span></span> <span data-ttu-id="0f047-117">Un message vous informe que tous les éléments de mappage sélectionnés seront déplacés avec les liens et fonctoids qui leur sont associés.</span><span class="sxs-lookup"><span data-stu-id="0f047-117">A message saying that all the selected map items(s), along with related links and functoids, will be moved is displayed.</span></span> <span data-ttu-id="0f047-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f047-118">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f047-119">Pour désactiver la boîte de message, dans le menu Visual Studio, accédez à **outils**, cliquez sur **Options**, cliquez sur **le Mappeur BizTalk**, cliquez sur **général**, et désactivez la **pour atteindre la page** option.</span><span class="sxs-lookup"><span data-stu-id="0f047-119">To disable the message popup, in the Visual Studio menu, go to **Tools**, click **Options**, click **BizTalk Mapper**, click **General**, and then uncheck the **Move to page** option.</span></span> <span data-ttu-id="0f047-120">Pour plus d’informations sur les options générales, consultez [comment personnaliser les paramètres généraux dans le Mappeur BizTalk](../core/how-to-customize-general-settings-in-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="0f047-120">For more information about general options, see [How to Customize General Settings in BizTalk Mapper](../core/how-to-customize-general-settings-in-biztalk-mapper.md).</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="0f047-121">Vous pouvez également appuyer sur CTRL + M, CTRL + M pour ouvrir la **déplacer vers la Page** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0f047-121">Alternatively, you can press CTRL+M, CTRL+M to open the **Move to Page** dialog box.</span></span> <span data-ttu-id="0f047-122">Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="0f047-122">For a list of Mapper shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="0f047-123">![Déplacer la relation sélectionnée vers une nouvelle page](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")</span><span class="sxs-lookup"><span data-stu-id="0f047-123">![Moving selected relationship to a new page](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")</span></span>  
  
3.  <span data-ttu-id="0f047-124">Dans le **déplacer vers la Page** boîte de dialogue, sélectionnez la page de grille cible à laquelle vous souhaitez déplacer la relation, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f047-124">In the **Move to Page** dialog box, select the target grid page to which you want to move the relationship, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f047-125">Vous pouvez également créer une nouvelle page en sélectionnant  **\*(ajouter la nouvelle page)**, puis en cliquant sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f047-125">You can also create a new page by selecting **\*(add new page)**, and then clicking **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f047-126">Vous pouvez également appuyer sur les touches CTRL+M, CTRL+A pour ajouter une page de grille à un mappage.</span><span class="sxs-lookup"><span data-stu-id="0f047-126">Alternatively, you can press CTRL+M, CTRL+A to add a new grid page in a map.</span></span> <span data-ttu-id="0f047-127">Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="0f047-127">For a list of Mapper shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="0f047-128">![En sélectionnant la page de grille cible](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")</span><span class="sxs-lookup"><span data-stu-id="0f047-128">![Selecting the target grid page](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")</span></span>  
  
     <span data-ttu-id="0f047-129">Le fonctoid/lien sélectionné (avec les fonctoids et liens associés) est déplacé vers la nouvelle page de grille.</span><span class="sxs-lookup"><span data-stu-id="0f047-129">The selected functoid/link, along with the related functoids and links, is moved to the new grid page.</span></span> <span data-ttu-id="0f047-130">La figure ci-dessous illustre la relation sélectionnée (qui était en page 3) déplacée vers la page 1.</span><span class="sxs-lookup"><span data-stu-id="0f047-130">The figure below shows the selected relationship (which was in Page 3) moved to Page 1.</span></span>  
  
     <span data-ttu-id="0f047-131">![Relation sélectionnée est déplacée vers une nouvelle page](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")</span><span class="sxs-lookup"><span data-stu-id="0f047-131">![Selected relationship is moved to a new page](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")</span></span>  
  
### <a name="to-move-a-relationship-using-drag-and-drop"></a><span data-ttu-id="0f047-132">Pour déplacer une relation à l'aide de la fonction glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="0f047-132">To move a relationship using drag-and-drop</span></span>  
  
1.  <span data-ttu-id="0f047-133">Dans le mappage, sélectionnez la page de grille depuis laquelle vous voulez déplacer une relation.</span><span class="sxs-lookup"><span data-stu-id="0f047-133">On the map, select the grid page from which you want to move a relationship.</span></span>  
  
2.  <span data-ttu-id="0f047-134">Sélectionnez le ou les fonctoids (et liens) à déplacer vers une autre page de grille.</span><span class="sxs-lookup"><span data-stu-id="0f047-134">Select the functoid(s) (and link(s)) you want to move to another grid page.</span></span> <span data-ttu-id="0f047-135">Cette action sélectionne de manière récursive les liens connectés aux fonctoids dans la sélection.</span><span class="sxs-lookup"><span data-stu-id="0f047-135">This recursively selects all links that connect to the functoids in the selection.</span></span>  
  
3.  <span data-ttu-id="0f047-136">Faites glisser la sélection vers la page (sous l'onglet de page) dans laquelle vous voulez déplacer la relation.</span><span class="sxs-lookup"><span data-stu-id="0f047-136">Drag the selection to the page (on the page tab) where you want to move the relationship.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="0f047-137">Ne relâchez pas le bouton de la souris tant que vous n'avez pas exécuté l'étape 4.</span><span class="sxs-lookup"><span data-stu-id="0f047-137">Do not release the mouse till you perform step 4.</span></span>  
  
4.  <span data-ttu-id="0f047-138">Une fois la page de grille cible activée (dans la figure ci-dessus, la Page 1 est activée), déposez la sélection dans une cellule vide de la page de grille.</span><span class="sxs-lookup"><span data-stu-id="0f047-138">When the target grid page comes into focus (in the above figure, Page 1 is in focus), drop the selection on an empty cell on the grid page.</span></span> <span data-ttu-id="0f047-139">La relation sélectionnée est déplacée vers la nouvelle page de grille.</span><span class="sxs-lookup"><span data-stu-id="0f047-139">The selected relationship is moved to the new grid page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f047-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f047-140">See Also</span></span>  
 [<span data-ttu-id="0f047-141">Utilisation des Pages de grille</span><span class="sxs-lookup"><span data-stu-id="0f047-141">Working with Grid Pages</span></span>](../core/working-with-grid-pages.md)
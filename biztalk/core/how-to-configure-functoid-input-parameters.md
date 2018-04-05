---
title: Comment configurer les paramètres d’entrée du fonctoid | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bts10.mapper.functoid.inputs
ms.assetid: 2c8f773a-932c-423d-b3fe-724265304b0a
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab04111835e7732aa8384e1d701a15ae8d268378
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-functoid-input-parameters"></a><span data-ttu-id="a48de-102">Configuration des paramètres d’entrée de fonctoid</span><span class="sxs-lookup"><span data-stu-id="a48de-102">How to Configure Functoid Input Parameters</span></span>
<span data-ttu-id="a48de-103">La configuration des paramètres d'entrée des fonctoids de votre mappage est un des aspects les plus importants (et les plus sujets aux erreurs) de l'utilisation des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="a48de-103">Properly configuring the input parameters to the functoids in your map is one of the most important, and potentially error-prone, aspects of using functoids.</span></span> <span data-ttu-id="a48de-104">Vous pouvez configurer ces paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="a48de-104">You can configure the functoid input parameters as follows:</span></span>  
  
-   <span data-ttu-id="a48de-105">Créer des liens d’entrée visibles par les nœuds de schéma qui se connecte et les fonctoids correspondants (glisser-déplacer la souris à partir d’un nœud de schéma pour le fonctoid).</span><span class="sxs-lookup"><span data-stu-id="a48de-105">Create visible input links by connecting schema nodes and respective functoids (drag-and-drop the mouse from schema node to the functoid).</span></span>  
  
-   <span data-ttu-id="a48de-106">Modifier directement la liste des paramètres d’entrée à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a48de-106">Directly edit the list of input parameters using the **Configure \<Functoid\> Functoid** dialog box.</span></span>  
  
 <span data-ttu-id="a48de-107">Cette rubrique fournit des instructions étape par étape pour configurer les paramètres d'entrée d'un fonctoid à l'aide de ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="a48de-107">This topic provides step-by-step instructions for configuring the input parameters for a functoid using these methods.</span></span>  
  
 <span data-ttu-id="a48de-108">L'opération de glisser-déposer utilisée pour définir les paramètres d'entrée de fonctoid constitue une méthode pratique pour spécifier les paramètres d'entrée comportant des spécifications XPath dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="a48de-108">The dragging method of establishing functoid input parameters provides a convenient way to specify input parameters that involve XPath specifications into the source schema.</span></span> <span data-ttu-id="a48de-109">Pour plus d’informations sur la création d’un schéma de paramètres d’entrée de fonctoid et de nœud, consultez [comment ajouter des fonctoids à un mappage](../core/how-to-add-basic-functoids-to-a-map.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-109">For information on creating a schema node and functoid input parameters, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md).</span></span> <span data-ttu-id="a48de-110">Toutefois, le **configurer \<fonctoid\> fonctoid** boîte de dialogue est le mécanisme par excellence pour afficher tous les paramètres d’entrée d’un fonctoid, pour créer et modifier tous les paramètres constants et pour réorganiser l’ordre des paramètres d’entrée lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a48de-110">However, the **Configure \<Functoid\> Functoid** dialog box is the definitive mechanism for viewing all the input parameters to a functoid, for creating and modifying any constant parameters, and for re-arranging the order of the input parameters when necessary.</span></span>  
  
 <span data-ttu-id="a48de-111">Lorsque vous configurez les paramètres d'entrée d'un fonctoid directement sur la page de grille (en dessinant des lignes, via une opération de glisser-déposer à l'aide de la souris, en partant du nœud du schéma et en reliant celui-ci au fonctoid) et si le nombre d'entrées atteint sa limite, le pointeur change d'état pour indiquer que l'action est impossible.</span><span class="sxs-lookup"><span data-stu-id="a48de-111">When you configure the input parameters for a functoid directly on the grid page (by drawing lines, using the mouse drag-and-drop, from the source schema node and linking it to the functoid), if the number of inputs reaches maximum, the cursor changes to a NO state.</span></span> <span data-ttu-id="a48de-112">La barre d'état affiche également le motif.</span><span class="sxs-lookup"><span data-stu-id="a48de-112">Also, the status bar displays the reason.</span></span> <span data-ttu-id="a48de-113">La figure ci-dessous illustre un fonctoid qui accepte un seul lien d'entrée.</span><span class="sxs-lookup"><span data-stu-id="a48de-113">The figure below shows a functoid which accepts only one input link.</span></span>  
  
 <span data-ttu-id="a48de-114">![AUCUN état de configuration du paramètre d’entrée du fonctoid](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")</span><span class="sxs-lookup"><span data-stu-id="a48de-114">![NO state for configuring functoid input parameter](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")</span></span>  
  
 <span data-ttu-id="a48de-115">Vous pouvez configurer les fonctoids de script et bouclage de Table à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a48de-115">You can configure the Scripting and Table Looping functoids using the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="a48de-116">Pour plus d’informations sur la façon de configurer les fonctoids, consultez [comment configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md) et [la configuration de bouclage de Table et de fonctoids Extracteur de Table](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-116">For information about how to configure the functoids, see [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md) and [How to Configure the Table Looping and Table Extractor Functoids](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a48de-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a48de-117">Prerequisites</span></span>  
 <span data-ttu-id="a48de-118">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a48de-118">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="what-is-an-input-parameter"></a><span data-ttu-id="a48de-119">Qu'est ce qu'un paramètre d'entrée ?</span><span class="sxs-lookup"><span data-stu-id="a48de-119">What is an input parameter?</span></span>  
 <span data-ttu-id="a48de-120">Un paramètre d'entrée peut prendre n'importe laquelle des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a48de-120">An input parameter can be any of the following:</span></span>  
  
-   <span data-ttu-id="a48de-121">un lien partant du nœud du schéma source et se dirigeant vers un fonctoid ;</span><span class="sxs-lookup"><span data-stu-id="a48de-121">A link from source schema node to a functoid</span></span>  
  
-   <span data-ttu-id="a48de-122">un lien partant d'un fonctoid et se dirigeant vers un autre fonctoid valide ;</span><span class="sxs-lookup"><span data-stu-id="a48de-122">A link from functoid to another valid functoid</span></span>  
  
-   <span data-ttu-id="a48de-123">une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="a48de-123">A constant value</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a48de-124">Il existe quelques fonctoids, tels que **Date**, **temps**, **Date et heure**, et **Nil**, ne requièrent aucun paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a48de-124">There are a few functoids, such as **Date**, **Time**, **Date and Time**, and **Nil**, which do not need any input parameters.</span></span>  
  
 <span data-ttu-id="a48de-125">La figure ci-dessous illustre un fonctoid (l'élément mis en surbrillance en rouge) qui dispose de deux paramètres d'entrée (Input[0] et Input[1]) et d'un paramètre constant (Input[2]).</span><span class="sxs-lookup"><span data-stu-id="a48de-125">The figure below displays a functoid (highlighted in red) with two input parameters (Input[0] and Input[1]) and a constant parameter (Input[2]).</span></span>  
  
 <span data-ttu-id="a48de-126">![Afficher les paramètres d’entrée d’un fonctoid](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")</span><span class="sxs-lookup"><span data-stu-id="a48de-126">![Displaying the input parameters to a functoid](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")</span></span>  
  
## <a name="to-open-the-configure-functoid-functoid-dialog-box"></a><span data-ttu-id="a48de-127">Pour ouvrir la page Configurer \<fonctoid\> boîte de dialogue fonctoid</span><span class="sxs-lookup"><span data-stu-id="a48de-127">To open the Configure \<Functoid\> Functoid dialog box</span></span>  
 <span data-ttu-id="a48de-128">Vous pouvez ouvrir le **configurer \<fonctoid\> fonctoid** boîte de dialogue de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="a48de-128">You can open the **Configure \<Functoid\> Functoid** dialog box in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a48de-129">Dans la page de grille correspondante, cliquez sur le fonctoid, puis cliquez sur **configurer les entrées de fonctoid**.</span><span class="sxs-lookup"><span data-stu-id="a48de-129">In the relevant grid page, right-click the functoid, and then click **Configure Functoid Inputs**.</span></span>  
  
-   <span data-ttu-id="a48de-130">Double-cliquez sur le fonctoid pour lequel vous souhaitez configurer les paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="a48de-130">Double-click the functoid for which you want to configure the input parameters.</span></span>  
  
-   <span data-ttu-id="a48de-131">Sélectionnez le fonctoid, puis cliquez sur le bouton de sélection (**...** ) dans Visual Studio **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="a48de-131">Select the functoid and then click the ellipses (**…**) in the Visual Studio’s **Properties** window.</span></span>  
  
-   <span data-ttu-id="a48de-132">Sélectionnez le fonctoid, puis appuyez sur la touche Entrée du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-132">Select the functoid and then press ENTER from the keyboard.</span></span>  
  
-   <span data-ttu-id="a48de-133">Sélectionnez le fonctoid, puis appuyez sur les touches CTRL+M, CTRL+I du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-133">Select the functoid and then press CTRL+M, CTRL+I from the keyboard.</span></span> <span data-ttu-id="a48de-134">Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-134">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
### <a name="to-insert-constant-input-parameters"></a><span data-ttu-id="a48de-135">Pour insérer des paramètres d'entrée constants</span><span class="sxs-lookup"><span data-stu-id="a48de-135">To insert constant input parameters</span></span>  
  
1.  <span data-ttu-id="a48de-136">Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, sélectionnez le **les entrées de fonctoid** onglet.</span><span class="sxs-lookup"><span data-stu-id="a48de-136">In the **Configure \<Functoid\> Functoid** dialog box, select the **Functoid Inputs** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-137">Le **les entrées de fonctoid** onglet est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="a48de-137">The **Functoid Inputs** tab is selected by default.</span></span>  
  
2.  <span data-ttu-id="a48de-138">Cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") bouton.</span><span class="sxs-lookup"><span data-stu-id="a48de-138">Click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button.</span></span> <span data-ttu-id="a48de-139">Une nouvelle ligne est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="a48de-139">A new row is added.</span></span>  
  
3.  <span data-ttu-id="a48de-140">La valeur du nouveau paramètre d’entrée, puis tapez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48de-140">Type the value for the new input parameter, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-141">Si le bouton d'ajout n'est pas activé, le fonctoid n'accepte ou n'exige aucun paramètre d'entrée, ou celui-ci a atteint le nombre maximal d'entrées autorisées.</span><span class="sxs-lookup"><span data-stu-id="a48de-141">If the add button is not enabled, the functoid does not accept or require input parameters, or may already have the maximum number of allowed inputs.</span></span>  
  
### <a name="to-edit-existing-constant-input-parameters"></a><span data-ttu-id="a48de-142">Pour modifier des paramètres d'entrée constants</span><span class="sxs-lookup"><span data-stu-id="a48de-142">To edit existing constant input parameters</span></span>  
  
1.  <span data-ttu-id="a48de-143">Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur la constante existante d’entrée de paramètre que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="a48de-143">In the **Configure \<Functoid\> Functoid** dialog box, click the existing constant input parameter that you want to edit.</span></span> <span data-ttu-id="a48de-144">La valeur actuelle est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="a48de-144">The current value is selected.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a48de-145">Vous pouvez uniquement modifier les paramètres d'entrées constantes.</span><span class="sxs-lookup"><span data-stu-id="a48de-145">You can edit the parameters of constant inputs only.</span></span> <span data-ttu-id="a48de-146">Il est impossible de modifier les paramètres d'entrée de tout autre type.</span><span class="sxs-lookup"><span data-stu-id="a48de-146">Input parameters of all other types cannot be edited.</span></span> <span data-ttu-id="a48de-147">Vous ne pouvez que les réorganiser ou les supprimer.</span><span class="sxs-lookup"><span data-stu-id="a48de-147">They can only be rearranged or deleted.</span></span>  
  
2.  <span data-ttu-id="a48de-148">Cliquez sur le ![modification des paramètres d’entrée constants](../core/media/edit-input-parameters.gif "Edit_input_parameters") bouton.</span><span class="sxs-lookup"><span data-stu-id="a48de-148">Click the ![Editing constant input parameters](../core/media/edit-input-parameters.gif "Edit_input_parameters") button.</span></span> <span data-ttu-id="a48de-149">Apportez les modifications appropriées à la valeur constante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48de-149">Make the appropriate changes to the constant value, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a48de-150">Vous pouvez également double-cliquer sur le paramètre d'entrée constant pour le modifier ou appuyer sur la touche F2 du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-150">Alternatively, you can double-click the constant input parameter to edit it, or press F2 from the keyboard.</span></span>  
  
## <a name="to-select-multiple-input-parameters"></a><span data-ttu-id="a48de-151">Sélection de plusieurs paramètres d'entrée</span><span class="sxs-lookup"><span data-stu-id="a48de-151">To select multiple input parameters</span></span>  
 <span data-ttu-id="a48de-152">Pour sélectionner plusieurs paramètres d'entrée, maintenez la touche CTRL enfoncée et cliquez sur les lignes souhaitées, puis effectuez l'une des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="a48de-152">You can select multiple input parameters by holding down the CTRL key and clicking the desired rows, and then perform any of the following operations.</span></span> <span data-ttu-id="a48de-153">Appuyez sur les touches CTRL+A du clavier pour sélectionner toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="a48de-153">You can press CTRL+A from the keyboard to select all the rows.</span></span>  
  
-   <span data-ttu-id="a48de-154">Déplacez la sélection vers le haut/bas.</span><span class="sxs-lookup"><span data-stu-id="a48de-154">Move the selection up/down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-155">Si la sélection comprend la ligne supérieure ou la ligne inférieure, vous ne pouvez pas déplacer la sélection vers le haut/bas respectivement.</span><span class="sxs-lookup"><span data-stu-id="a48de-155">If the bulk selection includes either the top-most or the bottom-most row among the other rows, you cannot move the selection up/down respectively.</span></span>  
  
-   <span data-ttu-id="a48de-156">Réorganisez la sélection.</span><span class="sxs-lookup"><span data-stu-id="a48de-156">Rearrange the selection.</span></span>  
  
-   <span data-ttu-id="a48de-157">Supprimez la sélection.</span><span class="sxs-lookup"><span data-stu-id="a48de-157">Delete the selection.</span></span>  
  
### <a name="to-change-the-order-of-existing-input-parameters"></a><span data-ttu-id="a48de-158">Pour modifier l’ordre des paramètres d’entrée existants</span><span class="sxs-lookup"><span data-stu-id="a48de-158">To change the order of existing input parameters</span></span>  
  
1.  <span data-ttu-id="a48de-159">Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur existant d’entrée de paramètre que vous souhaitez déplacer vers un autre emplacement dans la liste des paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a48de-159">In the **Configure \<Functoid\> Functoid** dialog box, click the existing input parameter that you want to move to a different position in the ordered list of input parameters.</span></span>  
  
2.  <span data-ttu-id="a48de-160">Cliquez sur le ![déplacer vers le haut dans la liste](../core/media/move-up-button.gif "Move_up_button") bouton pour déplacer le paramètre vers le haut dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a48de-160">Click the ![Move up in the list](../core/media/move-up-button.gif "Move_up_button") button to move the parameter up in the parameter list.</span></span> <span data-ttu-id="a48de-161">Répétez l'opération jusqu'à ce que le paramètre d'entrée sélectionné se trouve à la position souhaitée.</span><span class="sxs-lookup"><span data-stu-id="a48de-161">Repeat as necessary until the selected input parameter is in the desired position.</span></span> <span data-ttu-id="a48de-162">Vous pouvez également appuyer sur la flèche HAUT du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-162">Alternatively, you can press the UP ARROW key from the keyboard.</span></span> <span data-ttu-id="a48de-163">Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-163">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="a48de-164">-OU-</span><span class="sxs-lookup"><span data-stu-id="a48de-164">-OR-</span></span>  
  
     <span data-ttu-id="a48de-165">Cliquez sur le ![déplacement vers le bas dans une liste](../core/media/move-down-button.gif "Move_down_button") bouton Déplacer le paramètre vers le bas dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a48de-165">Click the ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") button to move the parameter down in the parameter list.</span></span> <span data-ttu-id="a48de-166">Répétez l'opération jusqu'à ce que le paramètre d'entrée sélectionné se trouve à la position souhaitée.</span><span class="sxs-lookup"><span data-stu-id="a48de-166">Repeat as necessary until the selected input parameter is in the desired position.</span></span> <span data-ttu-id="a48de-167">Vous pouvez également appuyer sur la flèche BAS du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-167">Alternatively, you can press the DOWN ARROW key from the keyboard.</span></span> <span data-ttu-id="a48de-168">Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-168">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a48de-169">Vous pouvez réorganiser la séquence des entrées uniquement dans les **configurer \<fonctoid\> fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a48de-169">You can rearrange the sequence of inputs only from the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="a48de-170">Si vous sélectionnez la ligne supérieure ou inférieure, la ![déplacer vers le haut dans la liste](../core/media/move-up-button.gif "Move_up_button") ou ![déplacement vers le bas dans une liste](../core/media/move-down-button.gif "Move_down_button")boutons sont désactivées, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a48de-170">If you select the top-most or bottom-most row, the ![Move up in the list](../core/media/move-up-button.gif "Move_up_button") or ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") buttons would be disabled, respectively.</span></span>  
  
### <a name="to-delete-an-input-parameter-by-deleting-the-input-link"></a><span data-ttu-id="a48de-171">Pour supprimer un paramètre d’entrée en supprimant le lien d’entrée</span><span class="sxs-lookup"><span data-stu-id="a48de-171">To delete an input parameter by deleting the input link</span></span>  
  
1.  <span data-ttu-id="a48de-172">Dans la page de grille correspondante, cliquez sur le lien d'entrée correspondant au paramètre d'entrée que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="a48de-172">In the relevant grid page, click the input link corresponding to the input parameter you want to delete.</span></span>  
  
2.  <span data-ttu-id="a48de-173">Sur le **modifier** menu, cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="a48de-173">On the **Edit** menu, click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-174">Ou bien, vous pouvez appuyer sur la touche SUPPR, ou cliquez sur le lien dans la page de grille correspondante, puis cliquez sur **supprimer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a48de-174">Alternatively, you can press the DELETE key, or right-click the link in the relevant grid page, and click **Delete** from the shortcut menu.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a48de-175">Le lien d'entrée est supprimé sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="a48de-175">The input link is deleted silently.</span></span> <span data-ttu-id="a48de-176">Il est toujours possible d'annuler la suppression si vous n'êtes pas sûr de vouloir réellement le faire.</span><span class="sxs-lookup"><span data-stu-id="a48de-176">You can always undo delete if you are not sure about it.</span></span> <span data-ttu-id="a48de-177">Pour plus d’informations sur les opérations d’annulation/de rétablissement, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-177">For more information about undo/redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
### <a name="to-delete-existing-input-parameters-within-the-configure-functoid-functoid-dialog-box"></a><span data-ttu-id="a48de-178">Pour supprimer des paramètres d’entrée existants dans la page Configurer \<fonctoid\> boîte de dialogue fonctoid</span><span class="sxs-lookup"><span data-stu-id="a48de-178">To delete existing input parameters within the Configure \<Functoid\> Functoid dialog box</span></span>  
  
1.  <span data-ttu-id="a48de-179">Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur existant d’entrée de paramètre que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="a48de-179">In the **Configure \<Functoid\> Functoid** dialog box, click the existing input parameter that you want to delete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-180">Vous pouvez supprimer n’importe quel paramètre d'entrée de cette façon, même ceux correspondant à un lien d'entrée.</span><span class="sxs-lookup"><span data-stu-id="a48de-180">You can delete any input parameter using this technique, even those that correspond to an input link.</span></span>  
  
2.  <span data-ttu-id="a48de-181">Cliquez sur le ![suppression de la sélection](../core/media/delete-button.gif "Delete_button") bouton.</span><span class="sxs-lookup"><span data-stu-id="a48de-181">Click the ![Deleting the selection](../core/media/delete-button.gif "Delete_button") button.</span></span> <span data-ttu-id="a48de-182">Le paramètre d'entrée existant sélectionné est supprimé de la liste des paramètres.</span><span class="sxs-lookup"><span data-stu-id="a48de-182">The selected existing input parameter is deleted from the parameter list.</span></span> <span data-ttu-id="a48de-183">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48de-183">Click **OK**.</span></span>  
  
     <span data-ttu-id="a48de-184">Vous pouvez également sélectionner la ligne à supprimer, puis appuyer sur la touche SUPPR du clavier.</span><span class="sxs-lookup"><span data-stu-id="a48de-184">Alternatively, you can select the row you want to delete, and press the DELETE key from the keyboard.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a48de-185">Le paramètre d'entrée est supprimé sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="a48de-185">The input parameter is deleted silently.</span></span> <span data-ttu-id="a48de-186">Il est toujours possible d'annuler la suppression si vous n'êtes pas sûr de vouloir réellement le faire.</span><span class="sxs-lookup"><span data-stu-id="a48de-186">You can always undo delete if you are not sure about it.</span></span> <span data-ttu-id="a48de-187">Pour plus d’informations sur les opérations d’annulation/de rétablissement, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-187">For more information about undo/redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a48de-188">Le bouton de suppression n'est pas activé tant qu'il n'existe pas de paramètres d'entrée dans la liste des paramètres.</span><span class="sxs-lookup"><span data-stu-id="a48de-188">The delete button is not enabled when there are no input parameters in the parameter list.</span></span>  
  
## <a name="to-set-labels-and-comments-for-functoids"></a><span data-ttu-id="a48de-189">Pour définir des étiquettes et des commentaires pour les fonctoids</span><span class="sxs-lookup"><span data-stu-id="a48de-189">To set labels and comments for functoids</span></span>  
 <span data-ttu-id="a48de-190">Vous pouvez définir des étiquettes et des commentaires à l’aide des fonctoids le **configurer \<fonctoid\> fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a48de-190">You can set labels and comments for functoids using the **Configure \<Functoid\> Functoid** dialog box.</span></span>  
  
1.  <span data-ttu-id="a48de-191">Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur le **étiquette et commentaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="a48de-191">In the **Configure \<Functoid\> Functoid** dialog box, click the **Label and Comments** tab.</span></span>  
  
2.  <span data-ttu-id="a48de-192">Type de la **étiquette** et **commentaires**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a48de-192">Type the **Label** and **Comments**, and then click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a48de-193">Pour plus d’informations sur l’étiquette et commentaires aux fonctoids et/ou liens, consultez [l’étiquette à un lien](../core/how-to-label-a-link.md) et [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="a48de-193">For more information about how to label and comment functoids and/or links, see [How to Label a Link](../core/how-to-label-a-link.md) and [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48de-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a48de-194">See Also</span></span>  
 [<span data-ttu-id="a48de-195">Modification des propriétés et paramètres d’entrée de fonctoid</span><span class="sxs-lookup"><span data-stu-id="a48de-195">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)
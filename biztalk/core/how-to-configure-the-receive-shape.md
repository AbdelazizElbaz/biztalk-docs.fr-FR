---
title: "Comment configurer la forme réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filter expressions, Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], about Receive shape
- configuring [Orchestration Designer], Receive shapes
- Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], filter expressions
ms.assetid: 15aadee4-fa05-4edd-a191-e4d191c1ea22
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3868384641e4c5fa03c82c7ec4ba18e3ee9fb1b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-receive-shape"></a><span data-ttu-id="c3e7c-102">Configuration de la forme Réception</span><span class="sxs-lookup"><span data-stu-id="c3e7c-102">How to Configure the Receive Shape</span></span>
![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")  
<span data-ttu-id="c3e7c-103">Forme Réception</span><span class="sxs-lookup"><span data-stu-id="c3e7c-103">Receive shape</span></span>  
  
 <span data-ttu-id="c3e7c-104">A **réception** forme peut être utilisée pour démarrer une orchestration.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-104">A **Receive** shape can be used to start an orchestration.</span></span> <span data-ttu-id="c3e7c-105">Si vous définissez la **activer** propriété **True**, le moteur d’exécution testerez un message entrant pour voir s’il s’agit du type approprié et, si un filtre a été appliqué, si l’expression de filtre est satisfaite.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-105">If you set the **Activate** property to **True**, the runtime engine will test an incoming message to see whether it is of the right type and, if a filter has been applied, whether the filter expression is satisfied.</span></span> <span data-ttu-id="c3e7c-106">Si les critères pour la réception du message, le moteur d’exécution crée et exécute une nouvelle instance de l’orchestration et le **réception** forme reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-106">If the criteria for receipt of the message are met, the runtime engine creates and runs a new orchestration instance, and the **Receive** shape receives the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3e7c-107">Si le **activer** propriété d’une forme réception est définie sur True, le **réception** doit être la première action dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-107">If the **Activate** property of a Receive shape is set to True, the **Receive** must be the first action in the orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3e7c-108">Si le **activer** est définie sur False sur tous les **réception** formes, l’orchestration doit être appelée par une autre orchestration pour pouvoir pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-108">If the **Activate** property is set to False on all **Receive** shapes, your orchestration must be called by another orchestration in order to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3e7c-109">Si vous placez un **réception** forme à l’intérieur d’une étendue avec le **activer** propriété la valeur **True**, puis ajoutez une variable de classe .NET à votre orchestration sans modifier le la variable **utiliser le constructeur par défaut** propriété **False**, la réception avec activation instruction sera hors de portée dans le code généré de XLANG/S, mais continue à l’aire de conception afficher comme étant à l’intérieur de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-109">If you put a **Receive** shape inside a scope with the **Activate** property set to **True**, and then add a .NET Class variable to your orchestration without changing the variable's **Use Default Constructor** property to **False**, the activate receive statement will be outside of the scope in the generated XLANG/S code, but the design surface will continue to show it as being inside the scope.</span></span>  
  
 <span data-ttu-id="c3e7c-110">Chaque orchestration doit avoir au moins un **réception** mettre en forme avec la **activer** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-110">Each orchestration must have at least one **Receive** shape with the **Activate** property set to **True**.</span></span>  
  
 <span data-ttu-id="c3e7c-111">Si vous vous attendez à recevoir une réponse indirecte ou asynchrone à un message précédemment envoyé (sans passer par un port de requête-réponse), vous devez mettre le message en corrélation avec l'instance d'orchestration en cours d'exécution, afin que la réponse puisse être dirigée vers l'instance appropriée.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-111">If you expect to receive an indirect or asynchronous response (not on a request-response port) to a message that you have previously sent, you need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance.</span></span> <span data-ttu-id="c3e7c-112">Vous pouvez appliquer à la forme Envoi un ensemble de corrélations initial, si vous prévoyez d'effectuer une corrélation ultérieure des valeurs du message entrant, ou un ensemble de corrélations ultérieur pour une corrélation utilisant un ensemble de corrélations précédemment initialisé.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-112">You can apply an initializing correlation set to the Receive shape if you plan to do subsequent correlation on values in the incoming message, or a following correlation set for correlating using a previously initialized correlation set.</span></span> <span data-ttu-id="c3e7c-113">Pour plus d’informations, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="c3e7c-113">For more information, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).</span></span>  
  
### <a name="to-configure-a-receive-shape"></a><span data-ttu-id="c3e7c-114">Pour configurer une forme Réception</span><span class="sxs-lookup"><span data-stu-id="c3e7c-114">To configure a Receive shape</span></span>  
  
1.  <span data-ttu-id="c3e7c-115">Définissez un message et une opération de port.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-115">Set a message and a port operation.</span></span>  
  
    1.  <span data-ttu-id="c3e7c-116">Dans la fenêtre Vue Orchestration, vérifiez que votre orchestration comporte à la fois un message et une opération de port définis pour le type de message reçu.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-116">In the Orchestration View window, verify that your orchestration has both a message and a port operation defined for the message type being received.</span></span>  
  
         <span data-ttu-id="c3e7c-117">Dans la fenêtre Propriétés, sélectionnez le message à recevoir dans le **Message** liste de propriétés de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-117">In the Properties window, select the message to receive from the **Message** property drop-down list.</span></span>  
  
    2.  <span data-ttu-id="c3e7c-118">Dans la fenêtre Propriétés, sélectionnez l’opération de port pour recevoir le message à partir de la **opération** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-118">In the Properties window, select the port operation to receive the message from the **Operation** drop-down list.</span></span>  
  
         <span data-ttu-id="c3e7c-119">— Ou :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-119">—Or—</span></span>  
  
         <span data-ttu-id="c3e7c-120">Faites glisser le connecteur de réception à partir de la **réception** forme pour le socket de port qui recevra le message.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-120">Drag the receive connector from the **Receive** shape to the port socket that will receive the message.</span></span>  
  
2.  <span data-ttu-id="c3e7c-121">Spécifier que le **réception** forme activera l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-121">Specify that the **Receive** shape will activate the orchestration.</span></span>  
  
3.  <span data-ttu-id="c3e7c-122">Dans la fenêtre Propriétés, définissez la propriété Activer sur True.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-122">In the Properties window, set the Activate property to True.</span></span>  
  
    1.  <span data-ttu-id="c3e7c-123">Dans la fenêtre Propriétés, cliquez sur le **points de suspension** (**...** ) bouton de la propriété Expression de filtre créer un filtre pour limiter les messages que ce **réception** forme accepte.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-123">In the Properties window, click the **Ellipsis** (**...**) button for the Filter Expression property to create a filter to restrict the messages that this **Receive** shape accepts.</span></span>  
  
         <span data-ttu-id="c3e7c-124">— Ou :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-124">—Or—</span></span>  
  
         <span data-ttu-id="c3e7c-125">Cliquez sur le **réception** mettre en forme, puis cliquez sur **modifier l’Expression de filtre**.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-125">Right-click the **Receive** shape and then click **Edit Filter Expression**.</span></span>  
  
    2.  <span data-ttu-id="c3e7c-126">Le **Expression de filtre** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-126">The **Filter Expression** dialog box appears.</span></span> <span data-ttu-id="c3e7c-127">Utilisez cette boîte de dialogue pour créer une ou plusieurs expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-127">Use this dialog box to create one or more filter expressions.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c3e7c-128">Un type de message doit être défini et affecté à la **réception** mettre en forme avant de pouvoir appliquer un filtre à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-128">A message type must be defined and assigned to the **Receive** shape before you can apply a filter to it.</span></span>  
  
4.  <span data-ttu-id="c3e7c-129">Spécifier les ensembles de corrélations pour limiter les messages le **réception** forme accepte.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-129">Specify correlation sets to restrict the messages the **Receive** shape accepts.</span></span>  
  
    -   <span data-ttu-id="c3e7c-130">Pour chaque ensemble de corrélations que vous souhaitez suivre, vérifiez une corrélation défini dans la liste déroulante sur le **ensembles de corrélations suivants** propriété.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-130">For each correlation set you want to follow, check a correlation set from the drop-down on the **Following Correlation Sets** property.</span></span>  
  
    -   <span data-ttu-id="c3e7c-131">Pour chaque correspondance de jeu que vous souhaitez initialiser, vérifiez une corrélation défini dans la liste déroulante sur le **l’initialisation des ensembles de corrélations** propriété.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-131">For each correlation set that you want to initialize, check a correlation set from the drop-down on the **Initializing Correlation Sets** property.</span></span>  
  
## <a name="filter-expression-grid-control"></a><span data-ttu-id="c3e7c-132">Contrôle de grille Expression de filtre</span><span class="sxs-lookup"><span data-stu-id="c3e7c-132">Filter Expression grid control</span></span>  
 <span data-ttu-id="c3e7c-133">Créez une expression de filtre à l'aide de ce contrôle de grille pour définir les prédicats composant l'expression.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-133">You build a filter expression by using this grid control to define the predicates that make up the expression.</span></span> <span data-ttu-id="c3e7c-134">Vous pouvez ajouter, modifier et supprimer des prédicats dans les cellules de la grille.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-134">You can add, edit, and delete predicates from the cells of the grid.</span></span> <span data-ttu-id="c3e7c-135">Ce contrôle de grille comporte quatre colonnes : propriété, opérateur, valeur et groupement.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-135">This grid control has four columns: Property, Operator, Value, and Grouping.</span></span>  
  
-   <span data-ttu-id="c3e7c-136">**Propriété.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-136">**Property.**</span></span> <span data-ttu-id="c3e7c-137">Vous pouvez entrer une référence de propriété ou en sélectionner une dans la liste déroulante de la cellule.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-137">You can type a property reference, or select one from the cell's drop-down list.</span></span> <span data-ttu-id="c3e7c-138">La liste comprend des propriétés de message entrant.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-138">The list contains properties on the incoming message.</span></span>  
  
-   <span data-ttu-id="c3e7c-139">**Opérateur.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-139">**Operator.**</span></span> <span data-ttu-id="c3e7c-140">Vous pouvez entrer valeur dans cette cellule ou sélectionner un opérateur dans la liste déroulante de la cellule.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-140">You can type in this cell, or select an operator from the drop-down list.</span></span> <span data-ttu-id="c3e7c-141">Les sélections possibles sont :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-141">Possible selections are:</span></span>  
  
    |<span data-ttu-id="c3e7c-142">Opérande</span><span class="sxs-lookup"><span data-stu-id="c3e7c-142">Operand</span></span>|<span data-ttu-id="c3e7c-143">Signification</span><span class="sxs-lookup"><span data-stu-id="c3e7c-143">Meaning</span></span>|  
    |-------------|-------------|  
    |==|<span data-ttu-id="c3e7c-144">Est égal à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-144">Is equal to</span></span>|  
    |<span data-ttu-id="c3e7c-145">!=</span><span class="sxs-lookup"><span data-stu-id="c3e7c-145">!=</span></span>|<span data-ttu-id="c3e7c-146">n'est pas égal à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-146">Is not equal to</span></span>|  
    |<|<span data-ttu-id="c3e7c-147">Est inférieur à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-147">Is less than</span></span>|  
    |\<=|<span data-ttu-id="c3e7c-148">Est inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-148">Is less than or equal to</span></span>|  
    |>|<span data-ttu-id="c3e7c-149">Est supérieur à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-149">Is greater than</span></span>|  
    |>=|<span data-ttu-id="c3e7c-150">Est supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="c3e7c-150">Is greater than or equal to</span></span>|  
    |<span data-ttu-id="c3e7c-151">Exists</span><span class="sxs-lookup"><span data-stu-id="c3e7c-151">Exists</span></span>|<span data-ttu-id="c3e7c-152">Exists</span><span class="sxs-lookup"><span data-stu-id="c3e7c-152">Exists</span></span>|  
  
-   <span data-ttu-id="c3e7c-153">**Valeur.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-153">**Value.**</span></span> <span data-ttu-id="c3e7c-154">Cellules de la **valeur** colonne peut contenir n’importe quelle constante que vous tapez dans : un littéral de chaîne, un littéral entier, ou null.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-154">Cells in the **Value** column can hold any constant that you type in: a string-literal, an integer-literal, or null.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3e7c-155">Si la propriété sélectionnée est du type chaîne, la valeur doit être encadrée par des guillemets.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-155">If the property selected is of type string, the value needs to be in quotes.</span></span> <span data-ttu-id="c3e7c-156">Par exemple, SMTP.From = "MyServer".</span><span class="sxs-lookup"><span data-stu-id="c3e7c-156">For example, SMTP.From = "MyServer".</span></span>  
  
-   <span data-ttu-id="c3e7c-157">**Regroupement.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-157">**Grouping.**</span></span> <span data-ttu-id="c3e7c-158">Utiliser cette colonne pour contrôler les groupes de prédicats.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-158">Use this column to control predicate grouping.</span></span> <span data-ttu-id="c3e7c-159">Les expressions de filtre sont toujours exprimées dans le formulaire de normale disjonctive (FND) afin de regroupement peut être déterminé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-159">Filter expressions are always expressed in Disjunctive Normal Form (DNF) so grouping can be determined automatically.</span></span> <span data-ttu-id="c3e7c-160">AND indique que le prédicat doit être regroupé avec le prédicat suivant, tandis que OR indique que le prédicat est séparé du prédicat de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-160">AND means the predicate is to be grouped with the predicate following it, while OR means the predicate is separate from the predicate in the next row.</span></span> <span data-ttu-id="c3e7c-161">Des parenthèses grises à gauche du contrôle de grille apparaissent lorsque les prédicats sont regroupés ensemble.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-161">Gray brackets to the left of the grid control appear when predicates are grouped together.</span></span> <span data-ttu-id="c3e7c-162">Il est impossible d'imbriquer des groupes de prédicats.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-162">Predicate groups cannot be nested.</span></span> <span data-ttu-id="c3e7c-163">Si vous n'entrez pas de valeur dans cette cellule, la valeur par défaut est AND.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-163">If you do not specify a value in this cell, the value of the cell defaults to AND.</span></span>  
  
 <span data-ttu-id="c3e7c-164">Par exemple, vous pouvez créer l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-164">For example, you might create an expression like the following:</span></span>  
  
 `MSMQ.MsgID = 1`  
  
 <span data-ttu-id="c3e7c-165">Avec ce filtre, le groupe de ports d'envoi s'abonnera uniquement aux messages ayant un ID de message MSMQ correspondant à 1.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-165">With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.</span></span>  
  
 <span data-ttu-id="c3e7c-166">Vous pouvez créer des expressions supplémentaires et leur définir une relation AND ou OR avec d'autres expressions, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-166">You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:</span></span>  
  
 `MSMQ.MsgID = 1 OR`  
  
 `SMTP.From = "MyServer"`  
  
 <span data-ttu-id="c3e7c-167">Dans ce cas, le groupe de ports d'envoi s'abonnera à tous les messages ayant un ID de message MSMQ de 1 ou qui proviennent du serveur SMTP nommé MyServer.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-167">In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.</span></span>  
  
## <a name="hint-label"></a><span data-ttu-id="c3e7c-168">Étiquette d'indication</span><span class="sxs-lookup"><span data-stu-id="c3e7c-168">Hint label</span></span>  
 <span data-ttu-id="c3e7c-169">Ce champ constitue une aide pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-169">This field provides user guidance.</span></span> <span data-ttu-id="c3e7c-170">Le texte de l'étiquette change en fonction de la colonne contenant la cellule active.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-170">The label text changes depending on which column contains the active cell.</span></span> <span data-ttu-id="c3e7c-171">Le texte affiche le nom de la colonne suivi par une indication, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3e7c-171">The text displays the column name followed by guidance text as follows:</span></span>  
  
-   <span data-ttu-id="c3e7c-172">**Propriété.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-172">**Property.**</span></span> <span data-ttu-id="c3e7c-173">Veuillez sélectionner une propriété pour le message entrant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-173">Please select a property on the incoming message from the list.</span></span>  
  
-   <span data-ttu-id="c3e7c-174">**Opérateur.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-174">**Operator.**</span></span> <span data-ttu-id="c3e7c-175">Sélectionnez un opérateur afin de comparer la Propriété avec la Valeur.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-175">Select an operator to compare the Property with the Value.</span></span>  
  
-   <span data-ttu-id="c3e7c-176">**Valeur.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-176">**Value.**</span></span> <span data-ttu-id="c3e7c-177">Sélectionnez une propriété de message dans la liste, ou tapez une valeur littérale.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-177">Select a message property from the list, or type in a literal value.</span></span>  
  
-   <span data-ttu-id="c3e7c-178">**Regroupement.**</span><span class="sxs-lookup"><span data-stu-id="c3e7c-178">**Grouping.**</span></span> <span data-ttu-id="c3e7c-179">Spécifiez la manière dont cette lignée doit être regroupée avec la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-179">Specify how this row is to be grouped with the next row.</span></span> <span data-ttu-id="c3e7c-180">"AND" entraîne la liaison des lignes, "OR" les sépare.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-180">'AND' will join the rows, and 'OR' will separate them.</span></span>  
  
## <a name="move-up-button"></a><span data-ttu-id="c3e7c-181">Bouton Monter </span><span class="sxs-lookup"><span data-stu-id="c3e7c-181">Move Up button</span></span>  
 <span data-ttu-id="c3e7c-182">Cliquez sur ce bouton pour déplacer la ligne sélectionnée vers le haut.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-182">Click this to move a selected row up.</span></span> <span data-ttu-id="c3e7c-183">(Commencez par sélectionner une ligne en cliquant sur le *flèche droite* (**>)** bouton sur le côté gauche du contrôle de grille.)</span><span class="sxs-lookup"><span data-stu-id="c3e7c-183">(First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)</span></span>  
  
## <a name="move-down-button"></a><span data-ttu-id="c3e7c-184">Bouton Descendre </span><span class="sxs-lookup"><span data-stu-id="c3e7c-184">Move Down button</span></span>  
 <span data-ttu-id="c3e7c-185">Cliquez sur ce bouton pour déplacer la ligne sélectionnée vers le bas.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-185">Click this to move a selected row down.</span></span> <span data-ttu-id="c3e7c-186">(Commencez par sélectionner une ligne en cliquant sur le *flèche droite* (**>)** bouton sur le côté gauche du contrôle de grille.)</span><span class="sxs-lookup"><span data-stu-id="c3e7c-186">(First select a row by clicking the *right arrow* (**>)** button at the left side of the grid control.)</span></span>  
  
## <a name="filter-expression-created-field"></a><span data-ttu-id="c3e7c-187">Champ Expression de filtre créée</span><span class="sxs-lookup"><span data-stu-id="c3e7c-187">Filter Expression Created field</span></span>  
 <span data-ttu-id="c3e7c-188">Cette zone de texte en lecteur seule contient l'expression telle que vous l'avez créée.</span><span class="sxs-lookup"><span data-stu-id="c3e7c-188">This read-only text box shows the expression as you are building it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3e7c-189">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c3e7c-189">In This Section</span></span>  
 [<span data-ttu-id="c3e7c-190">Utilisation des filtres avec la forme d’un Message de réception</span><span class="sxs-lookup"><span data-stu-id="c3e7c-190">Using Filters With the Receive Message Shape</span></span>](../core/using-filters-with-the-receive-message-shape.md)
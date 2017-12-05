---
title: "Définition d’une règle d’entreprise pour une Orchestration de processus de privé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, policies
- vocabularies, saving
- private processes, orchestrations
- business rules, private processes
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- policies, deploying
- vocabularies, creating
- orchestrations, private-process orchestrations
- private processes, customizing
- policies, publishing
- business rules, Set elements
- creating, policies
- customizing private processes
- Set elements
- business rules, orchestrations
- publishing, vocabularies
- vocabularies, publishing
- creating, rules
- business rules, Get elements
- policies, saving
- publishing, policies
- Get elements
- orchestrations, business rules
- rules
- private processes, business rules
- policies, creating
ms.assetid: 5d2b0257-1b15-482b-a562-798b808e9a2d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dd0ebb22bcf6253604e4e8bf7fd858deb776b0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="defining-a-business-rule-for-a-private-process-orchestration"></a><span data-ttu-id="8ab06-102">Définition d’une règle d’entreprise pour une Orchestration de processus de privé</span><span class="sxs-lookup"><span data-stu-id="8ab06-102">Defining a Business Rule for a Private Process Orchestration</span></span>
<span data-ttu-id="8ab06-103">Vous pouvez définir une règle d’entreprise pour une utilisation dans un processus privé d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="8ab06-103">You can define a business rule for use in an acknowledgement private process.</span></span> <span data-ttu-id="8ab06-104">Vous pouvez ainsi modifier la règle d’entreprise dynamiquement sans arrêter l’orchestration de processus privé.</span><span class="sxs-lookup"><span data-stu-id="8ab06-104">This lets you to modify the business rule dynamically without stopping the private-process orchestration.</span></span> <span data-ttu-id="8ab06-105">Ce processus utilise le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] moteur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8ab06-105">This process uses the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Business Rule Engine.</span></span> <span data-ttu-id="8ab06-106">Ce processus implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8ab06-106">This process involves the following steps:</span></span>  
  
1.  <span data-ttu-id="8ab06-107">Ajout d’un vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="8ab06-107">Adding a new vocabulary.</span></span> <span data-ttu-id="8ab06-108">Cela implique la définition de valeur de constante d’au moins un vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="8ab06-108">This involves defining at least one vocabulary constant value.</span></span> <span data-ttu-id="8ab06-109">Cela définit un seuil de la règle d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8ab06-109">This sets a business-rule threshold.</span></span> <span data-ttu-id="8ab06-110">Il implique également la définition de document XML `Get` et `Set` éléments.</span><span class="sxs-lookup"><span data-stu-id="8ab06-110">It also involves defining XML document `Get` and `Set` elements.</span></span> <span data-ttu-id="8ab06-111">Ceci établit la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] utilise le seuil.</span><span class="sxs-lookup"><span data-stu-id="8ab06-111">This establishes how [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] uses the threshold.</span></span>  
  
2.  <span data-ttu-id="8ab06-112">Ajout d’une nouvelle stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ab06-112">Adding a new policy.</span></span> <span data-ttu-id="8ab06-113">Cela implique la création d’une stratégie, création d’un ensemble de règles, puis l’enregistrement, publication et déploiement de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ab06-113">This involves creating a policy, creating a set of rules, and then saving, publishing, and deploying the policy.</span></span>  
  
3.  <span data-ttu-id="8ab06-114">Appel de la règle d’entreprise à partir de l’orchestration de processus privé.</span><span class="sxs-lookup"><span data-stu-id="8ab06-114">Calling the business rule from the private-process orchestration.</span></span> <span data-ttu-id="8ab06-115">Cela implique l’ajout d’un **appeler règles** forme à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8ab06-115">This involves adding a **Call Rules** shape to the orchestration.</span></span>  
  
 <span data-ttu-id="8ab06-116">Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK comprend un exemple [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stratégie commerciale, samplebtarnpolicy.xml, dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4.</span><span class="sxs-lookup"><span data-stu-id="8ab06-116">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a sample [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] business policy, samplebtarnpolicy.xml, in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4.</span></span> <span data-ttu-id="8ab06-117">Pour plus d’informations, consultez [stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).</span><span class="sxs-lookup"><span data-stu-id="8ab06-117">For more information, see [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).</span></span>  
  
 <span data-ttu-id="8ab06-118">L’orchestration PIP3A4PrivateResponder.odx est un exemple d’orchestration de processus privé qui montre comment implémenter un processus PIP (Partner Interface)-processus privé de répondeur spécifiques incorporant une règle d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8ab06-118">PIP3A4PrivateResponder.odx orchestration is a sample private-process orchestration that demonstrates how to implement a Partner Interface Process (PIP)-specific responder private process incorporating a business rule.</span></span> <span data-ttu-id="8ab06-119">Pour plus d’informations sur cet exemple, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span><span class="sxs-lookup"><span data-stu-id="8ab06-119">For more information about this sample, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
 <span data-ttu-id="8ab06-120">Pour plus d’informations sur les vocabulaires et des stratégies, consultez la rubrique « Développement avec des règles d’entreprise » dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8ab06-120">For more information about vocabularies and policies, see the "Developing with Business Rules" topic in BizTalk Server.</span></span>  
  
### <a name="to-add-a-new-vocabulary"></a><span data-ttu-id="8ab06-121">Pour ajouter un nouveau vocabulaire</span><span class="sxs-lookup"><span data-stu-id="8ab06-121">To add a new vocabulary</span></span>  
  
1.  <span data-ttu-id="8ab06-122">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-122">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="8ab06-123">Si le **ouvrir le magasin de règles** boîte de dialogue s’ouvre, sélectionnez le **moteur de règles BizTalk** base de données que vous configurez sur le serveur actuel, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-123">If the **Open Rule Store** dialog box opens, select the **BizTalk Rule Engine** database that you set up on the current server, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8ab06-124">Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Éditeur des règles d’entreprise, dans le volet Explorateur de faits, cliquez sur **vocabulaires**, puis cliquez sur **ajouter un nouveau vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-124">In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Business Rule Composer, in the Facts Explorer pane, right-click **Vocabularies**, and then click **Add New Vocabulary**.</span></span>  
  
4.  <span data-ttu-id="8ab06-125">Dans le volet des propriétés (partie inférieure gauche), définissez la **nom** nom à la propriété de vocabulaire approprié, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-125">In the Property pane (lower left), set the **Name** property to the name of the appropriate vocabulary, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="8ab06-126">Développez le dossier de vocabulaire que vous venez de créer, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-126">Expand the vocabulary folder you just created, right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.</span></span>  
  
6.  <span data-ttu-id="8ab06-127">Dans la page **Assistant Définition de vocabulaire** , sélectionnez **Valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-127">On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="8ab06-128">Sur le **valeur constante, plage de valeurs ou ensemble de valeurs** page, dans le **nom de la définition** , tapez le nom de la valeur de constante de vocabulaire approprié, tel que **quantité maximale autorisée** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-128">On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition Name** box, type the name of the appropriate vocabulary constant value, such as **Maximum Quantity Allowed**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="8ab06-129">Sur le **définir une valeur constante** page, dans le **champ de valeur** zone, tapez le seuil, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-129">On the **Define a Constant Value** page, in the **Value Field** box, type the threshold, and then click **Finish**.</span></span>  
  
### <a name="to-define-get-and-set-elements"></a><span data-ttu-id="8ab06-130">Pour définir les obtenir et définir les éléments</span><span class="sxs-lookup"><span data-stu-id="8ab06-130">To define Get and Set elements</span></span>  
  
1.  <span data-ttu-id="8ab06-131">Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de faits, sous le dossier du vocabulaire créé dans « pour ajouter une nouvelle procédure vocabulaire », cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-131">In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder created in the "To add a new vocabulary procedure", right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="8ab06-132">Sur le **Assistant Définition de vocabulaire** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-132">On the **Vocabulary Definition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="8ab06-133">Sur le **Document élément ou attribut XML** page, dans la zone de texte Nom de la définition, tapez un nom pour un **obtenir** élément.</span><span class="sxs-lookup"><span data-stu-id="8ab06-133">On the **XML Document Element or Attribute** page, in the Definition Name text box, type a name for a **Get** element.</span></span>  
  
4.  <span data-ttu-id="8ab06-134">Cliquez sur **Parcourir**, accédez à l’emplacement du schéma que vous souhaitez utiliser, sélectionnez le fichier de schéma, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-134">Click **Browse**, move to the location of the schema that you want to use, select the schema file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="8ab06-135">Si le **sélectionner un nœud racine** s’ouvre, sélectionnez le nœud racine à rechercher.</span><span class="sxs-lookup"><span data-stu-id="8ab06-135">If the **Select Root Node** page opens, select the root node to browse.</span></span>  
  
6.  <span data-ttu-id="8ab06-136">Sur le **sélectionnez une liaison** page, de passer au champ pour lequel vous souhaitez définir le seuil, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-136">On the **Select Binding** page, move to the field for which you want to define the threshold, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8ab06-137">Dans le **Type de Document** , tapez le nom du document.</span><span class="sxs-lookup"><span data-stu-id="8ab06-137">In the **Document Type** box, type the name of the document.</span></span>  
  
8.  <span data-ttu-id="8ab06-138">Dans le **Type d’opération** section, sélectionnez **effectuer une opération « Get »**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-138">In the **Operation Type** section, select **Perform “Get” operation**.</span></span>  
  
9. <span data-ttu-id="8ab06-139">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-139">Click **Finish**.</span></span>  
  
10. <span data-ttu-id="8ab06-140">Répétez ces étapes pour définir une ou plusieurs `Set` opérations, sélectionnez **effectuer une opération « Set »** pour le **Type d’opération**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-140">Repeat these steps to define one or more `Set` operations, select **Perform “Set” operation** for the **Operation Type**.</span></span>  
  
### <a name="to-save-and-publish-the-vocabulary"></a><span data-ttu-id="8ab06-141">Pour enregistrer et publier le vocabulaire</span><span class="sxs-lookup"><span data-stu-id="8ab06-141">To save and publish the vocabulary</span></span>  
  
1.  <span data-ttu-id="8ab06-142">Dans l’éditeur des règles d’entreprise, dans le volet de l’Explorateur de faits, sous le dossier du vocabulaire que vous avez créé, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-142">In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="8ab06-143">Dans le volet Explorateur de faits, sous le dossier 3A4PurchaseOrderVocabulary, avec le bouton droit **Version 1.0**, puis sélectionnez **publier**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-143">In the Facts Explorer pane, under the 3A4PurchaseOrderVocabulary folder, right-click **Version 1.0**, and then select **Publish**.</span></span>  
  
### <a name="to-add-a-new-policy-and-rules"></a><span data-ttu-id="8ab06-144">Pour ajouter une nouvelle stratégie et les règles</span><span class="sxs-lookup"><span data-stu-id="8ab06-144">To add a new policy and rules</span></span>  
  
1.  <span data-ttu-id="8ab06-145">Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-145">In Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
2.  <span data-ttu-id="8ab06-146">Cliquez sur **Policy1**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-146">Click **Policy1**.</span></span>  
  
3.  <span data-ttu-id="8ab06-147">Dans le volet Propriétés, définissez la **nom** propriété le nom de la stratégie appropriée.</span><span class="sxs-lookup"><span data-stu-id="8ab06-147">In the Property pane, set the **Name** property to the appropriate policy name.</span></span>  
  
4.  <span data-ttu-id="8ab06-148">Dans le volet Explorateur de stratégies, sous le dossier pour la nouvelle stratégie, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-148">In the Policy Explorer pane, under the folder for the new policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span>  
  
5.  <span data-ttu-id="8ab06-149">Cliquez sur **règle1**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-149">Click **Rule1**.</span></span>  
  
6.  <span data-ttu-id="8ab06-150">Dans le volet Propriétés, définissez la **nom** propriété le nom de la règle votre choix, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-150">In the Property pane, set the **Name** property to the rule name you want, and then press **Enter**.</span></span>  
  
7.  <span data-ttu-id="8ab06-151">Dans l’éditeur des règles, sous la **IF** volet, avec le bouton droit **Conditions**, puis sélectionnez une condition logique, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8ab06-151">In the Rule Composer, under the **IF** pane, right-click **Conditions**, and then select a logical condition, if appropriate.</span></span>  
  
8.  <span data-ttu-id="8ab06-152">Dans le volet Explorateur de faits, sous **vocabulaires**, développez **prédicats**, développez **Version 1.0 - publiée**, sélectionnez le prédicat voulu, faites-le glisser vers l’éditeur, puis déposez-le sur **Conditions** ou l’opérateur logique.</span><span class="sxs-lookup"><span data-stu-id="8ab06-152">In the Facts Explorer pane, under **Vocabularies**, expand **Predicates**, expand **Version 1.0 - Published**, select the predicate you want, drag it to the composer surface, and then drop it on **Conditions** or the logical operator.</span></span>  
  
9. <span data-ttu-id="8ab06-153">Dans le volet Explorateur de faits, sous le dossier vocabulaires, développez successivement le vocabulaire que vous avez créé, **Version 1.0 - publiée**, sélectionnez un `Get` ou `Set` élément, faites-le glisser vers l’éditeur et déposez-le sur **argument1**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-153">In the Facts Explorer pane, under the Vocabularies folder, expand the vocabulary that you created, expand **Version 1.0 - Published**, select a `Get` or `Set` element, drag it to the composer surface, and drop it on **argument1**.</span></span>  
  
10. <span data-ttu-id="8ab06-154">Sous le dossier du vocabulaire, sélectionnez un `Get` ou `Set` élément, faites-le glisser vers l’éditeur et déposez-le sur **argument2**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-154">Under the vocabulary folder, select a `Get` or `Set` element, drag it to the composer surface and drop it on **argument2**.</span></span>  
  
11. <span data-ttu-id="8ab06-155">Sous le dossier du vocabulaire, sélectionnez un `Set` élément, faites-le glisser vers l’éditeur et déposez-le dans la **Actions** zone dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="8ab06-155">Under the vocabulary folder, select a `Set` element, drag it to the composer surface, and drop it in the **Actions** box in the THEN pane.</span></span>  
  
12. <span data-ttu-id="8ab06-156">Si une variable est associée à la `Set` élément, cliquez sur la variable, apportez les modifications appropriées, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-156">If a variable is associated with the `Set` element, click the variable, make changes as appropriate, and then press **Enter**.</span></span> <span data-ttu-id="8ab06-157">Le cas échéant, répétez avec d’autres `Set` éléments.</span><span class="sxs-lookup"><span data-stu-id="8ab06-157">If appropriate, repeat with other `Set` elements.</span></span>  
  
### <a name="to-save-publish-and-deploy-the-policy"></a><span data-ttu-id="8ab06-158">Pour enregistrer, publier et déployer la stratégie</span><span class="sxs-lookup"><span data-stu-id="8ab06-158">To save, publish, and deploy the policy</span></span>  
  
1.  <span data-ttu-id="8ab06-159">Lorsque vous avez terminé de définir les règles, dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-159">When you have finished defining the rules, in Business Rule Composer, in the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="8ab06-160">Dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-160">In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
3.  <span data-ttu-id="8ab06-161">Dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-161">In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Deploy**.</span></span>  
  
### <a name="to-call-the-business-rule-from-the-orchestration"></a><span data-ttu-id="8ab06-162">Pour appeler la règle d’entreprise à partir de l’orchestration</span><span class="sxs-lookup"><span data-stu-id="8ab06-162">To call the business rule from the orchestration</span></span>  
  
1.  <span data-ttu-id="8ab06-163">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-163">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="8ab06-164">Sur le **fichier** menu, pointez sur Ouvrir, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-164">On the **File** menu, point to Open, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="8ab06-165">Recherchez la solution qui contient l’orchestration que vous devez appeler à partir de la règle d’entreprise, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-165">Locate the solution that contains the orchestration that you must call the business rule from, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="8ab06-166">Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-166">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
5.  <span data-ttu-id="8ab06-167">Développez **Variables**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-167">Expand **Variables**.</span></span> <span data-ttu-id="8ab06-168">Assurez-vous que la liste de variables d’orchestration contient une variable qui correspond à chaque paramètre dans la stratégie d’entreprise que vous appelez à partir de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8ab06-168">Make sure that the orchestration variable list contains a variable that corresponds to each parameter in the business policy that you call from the orchestration.</span></span> <span data-ttu-id="8ab06-169">Assurez-vous que la variable a le même type que le paramètre de stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ab06-169">Make sure that the variable has the same type as the policy parameter.</span></span> <span data-ttu-id="8ab06-170">Si la liste ne contient pas une variable d’orchestration pour chaque paramètre de stratégie, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-170">If the list does not contain an orchestration variable for each policy parameter, right-click **Variables**, and then click **New Variable**.</span></span> <span data-ttu-id="8ab06-171">Dans Vue Orchestration, tapez un nom de variable, puis, dans la fenêtre Propriétés, entrez le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8ab06-171">In Orchestration View, type a variable name, and then in the Properties window, enter the type of the parameter.</span></span>  
  
6.  <span data-ttu-id="8ab06-172">À partir de la **boîte à outils**, faites glisser un **appeler règles** forme sur l’aire de conception d’orchestration et déposez-le sous le **réception** forme.</span><span class="sxs-lookup"><span data-stu-id="8ab06-172">From the **Toolbox**, drag a **Call Rules** shape to the orchestration design surface, and then drop it under the **Receive** shape.</span></span>  
  
7.  <span data-ttu-id="8ab06-173">Double-cliquez sur le **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="8ab06-173">Double-click the **Call Rules** shape.</span></span>  
  
8.  <span data-ttu-id="8ab06-174">Dans le **sélectionnez la stratégie commerciale que vous souhaitez appeler** , sélectionnez la stratégie d’entreprise à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="8ab06-174">In the **Select the business policy you wish to call** box, select the business policy from the drop-down list.</span></span>  
  
9. <span data-ttu-id="8ab06-175">Pour le premier paramètre, pour **nom de paramètre**, sélectionnez un nom dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="8ab06-175">For the first parameter shown, for **Parameter Name**, select a name from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ab06-176">BTARN remplit la **paramètre de stratégie** liste avec tous les paramètres dans la stratégie d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8ab06-176">BTARN populates the **Policy Parameter** list with all the parameters in the business policy.</span></span> <span data-ttu-id="8ab06-177">Pour chaque paramètre dans la liste, BTARN entre une valeur dans **Type de paramètre** à partir de la stratégie d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8ab06-177">For each parameter in the list, BTARN enters a value in **Parameter Type** from the business policy.</span></span> <span data-ttu-id="8ab06-178">Dans la liste déroulante associée **nom de paramètre**, BTARN entre les noms de toutes les variables à partir de la liste des variables de l’orchestration qui a le même type que les paramètres de stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ab06-178">In the drop-down list associated with **Parameter Name**, BTARN enters the names of all variables from the orchestration's variable list that has the same type as the policy parameters.</span></span> <span data-ttu-id="8ab06-179">En sélectionnant une variable d’orchestration, vous associez cette variable avec le paramètre de stratégie.</span><span class="sxs-lookup"><span data-stu-id="8ab06-179">By selecting an orchestration variable, you are associating that variable with the policy parameter.</span></span> <span data-ttu-id="8ab06-180">Vous pouvez afficher les variables d’orchestration dans Vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="8ab06-180">You can view the orchestration variables in Orchestration View.</span></span>  
  
10. <span data-ttu-id="8ab06-181">Répétez l’étape 9 pour tous les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="8ab06-181">Repeat step 9 for all other parameters.</span></span>  
  
11. <span data-ttu-id="8ab06-182">Dans la fenêtre de conception de l’Orchestration, entrez toutes les formes supplémentaires requis pour le traitement de la stratégie d’entreprise, y compris l’ajout un **décision** sous la forme la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="8ab06-182">In the Orchestration Design window, enter all the additional shapes required for the processing associated with the business policy, including adding a **Decision** shape under the **Call Rules** shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ab06-183">Pour obtenir un exemple montrant comment utiliser un **appeler règles** forme dans une orchestration, reportez-vous à l’orchestration PIP3A4PrivateResponder.odx incluse dans le SDK de BTARN.</span><span class="sxs-lookup"><span data-stu-id="8ab06-183">For an example of how to use a **Call Rules** shape in an orchestration, see the PIP3A4PrivateResponder.odx orchestration included in the BTARN SDK.</span></span> <span data-ttu-id="8ab06-184">Il se trouve à \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span><span class="sxs-lookup"><span data-stu-id="8ab06-184">It is located at \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span></span> <span data-ttu-id="8ab06-185">Pour plus d’informations, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span><span class="sxs-lookup"><span data-stu-id="8ab06-185">For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
12. <span data-ttu-id="8ab06-186">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ab06-186">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab06-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab06-187">See Also</span></span>  
 <span data-ttu-id="8ab06-188">[Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span><span class="sxs-lookup"><span data-stu-id="8ab06-188">[Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span></span>  
 <span data-ttu-id="8ab06-189">[Stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span><span class="sxs-lookup"><span data-stu-id="8ab06-189">[Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span></span>  
 [<span data-ttu-id="8ab06-190">Orchestration de répondeur privé 3A4 avec une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="8ab06-190">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)
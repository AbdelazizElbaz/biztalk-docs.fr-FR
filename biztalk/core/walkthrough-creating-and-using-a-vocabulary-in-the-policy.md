---
title: "Procédure pas à pas : Création et utilisation de vocabulaire dans la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c306a6e-3384-4f43-9c75-c5407cd9aed2
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fb64a0548fefb816e1975e4c858934fc3dceb7c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-creating-and-using-a-vocabulary-in-the-policy"></a><span data-ttu-id="b833f-102">Procédure pas à pas : Création et utilisation de vocabulaire dans la stratégie</span><span class="sxs-lookup"><span data-stu-id="b833f-102">Walkthrough: Creating and Using a Vocabulary in the Policy</span></span>
<span data-ttu-id="b833f-103">Cette procédure pas à pas fournit des procédures pas à pas pour créer un vocabulaire et à son utilisation dans les **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="b833f-103">This walkthrough provides step-by-step procedures for creating a vocabulary and using the vocabulary in the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b833f-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b833f-104">Prerequisites</span></span>  
 <span data-ttu-id="b833f-105">Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b833f-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before performing this walkthrough.</span></span> <span data-ttu-id="b833f-106">En outre, nous vous conseillons de suivre toutes les procédures pas à pas précédant celle-ci dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="b833f-106">However, we recommend that you complete all the walkthroughs that are listed before this walkthrough in the documentation.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="b833f-107">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="b833f-107">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="b833f-108">Cette procédure pas à pas regroupe trois procédures, comme indiqué dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b833f-108">This walkthrough contains three procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="b833f-109">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="b833f-109">Procedure title</span></span>|<span data-ttu-id="b833f-110">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="b833f-110">Procedure descritpion</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="b833f-111">Pour créer le vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="b833f-111">To create the POVocabulary vocabulary</span></span>|<span data-ttu-id="b833f-112">Fournit des instructions détaillées pour la création de la **POVocabulary** vocabulaire avec trois définitions : quantité requise, nombre maximal d’éléments autorisés et état de la demande.</span><span class="sxs-lookup"><span data-stu-id="b833f-112">Provides step-by-step instructions for creating the **POVocabulary** vocabulary with three definitions: Requested Quantity, Maximum Number of Items Allowed, and Request Status.</span></span>|  
|<span data-ttu-id="b833f-113">Pour utiliser le vocabulaire POVocabulary dans la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="b833f-113">To use the POVocabulary in the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="b833f-114">Fournit des instructions détaillées pour la création d’une nouvelle version de la **ProcessPurchaseOrder** à l’aide de la stratégie **POVocabulary**.</span><span class="sxs-lookup"><span data-stu-id="b833f-114">Provides step-by-step instructions for creating a new version of the **ProcessPurchaseOrder** policy using **POVocabulary**.</span></span>|  
|<span data-ttu-id="b833f-115">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="b833f-115">To test the solution</span></span>|<span data-ttu-id="b833f-116">Fournit des instructions pas à pas pour le test de la solution.</span><span class="sxs-lookup"><span data-stu-id="b833f-116">Provides step-by-step instructions for testing the solution.</span></span>|  
  
### <a name="to-create-the-povocabulary-vocabulary"></a><span data-ttu-id="b833f-117">Pour créer le vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="b833f-117">To create the POVocabulary vocabulary</span></span>  
  
1.  <span data-ttu-id="b833f-118">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="b833f-118">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="b833f-119">Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="b833f-119">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b833f-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b833f-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="b833f-121">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="b833f-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="b833f-122">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="b833f-122">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
3.  <span data-ttu-id="b833f-123">Avec le bouton droit **vocabulaires**, cliquez sur **ajouter un nouveau vocabulaire**, puis tapez **POVocabulary** comme nom pour le vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="b833f-123">Right-click **Vocabularies**, click **Add New Vocabulary**, and then type **POVocabulary** as the name for the vocabulary.</span></span>  
  
4.  <span data-ttu-id="b833f-124">Si vous n’avez pas modifié le nom du vocabulaire en POVocabulary à l’étape 3, modifiez le nom du vocabulaire pour **POVocabulary**dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="b833f-124">If you did not change the name of the vocabulary to POVocabulary in step 3, change the name of the vocabulary to **POVocabulary**in the Properties window.</span></span>  
  
5.  <span data-ttu-id="b833f-125">Avec le bouton droit **Version 1.0 (non enregistrée)** dans **POVocabulary**, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="b833f-125">Right-click **Version 1.0(not saved)** in **POVocabulary**, and then click **Add New Definition**.</span></span>  
  
6.  <span data-ttu-id="b833f-126">Dans l’Assistant Définition de vocabulaire, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b833f-126">In the Vocabulary Definition Wizard, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="b833f-127">Pour le **nom de la définition**, type **quantité requise**.</span><span class="sxs-lookup"><span data-stu-id="b833f-127">For the **Definition name**, type **Requested Quantity**.</span></span>  
  
8.  <span data-ttu-id="b833f-128">Cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** vous avez créé dans [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md).</span><span class="sxs-lookup"><span data-stu-id="b833f-128">Click **Browse**, and select the **PO.xsd** file you created in [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md).</span></span>  
  
9. <span data-ttu-id="b833f-129">Dans le **sélectionnez une liaison** boîte de dialogue, développez **PurchaseOrder**, développez **élément**, puis double-cliquez sur **quantité**.</span><span class="sxs-lookup"><span data-stu-id="b833f-129">In the **Select Binding** dialog box, expand **PurchaseOrder**, expand **Item**, and then double-click **Quantity**.</span></span>  
  
10. <span data-ttu-id="b833f-130">Assurez-vous que le **type de document** a la valeur **RuleTest.PO**.</span><span class="sxs-lookup"><span data-stu-id="b833f-130">Make sure that the **document type** is set to **RuleTest.PO**.</span></span> <span data-ttu-id="b833f-131">Si elle n’est pas le cas, modifiez le type de document à RuleTest.PO.</span><span class="sxs-lookup"><span data-stu-id="b833f-131">If it is not, change the document type to RuleTest.PO.</span></span> <span data-ttu-id="b833f-132">Cette étape est très importante.</span><span class="sxs-lookup"><span data-stu-id="b833f-132">This step is very important.</span></span>  
  
     <span data-ttu-id="b833f-133">![BRE &#45; Procédure pas à pas &#45; ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")</span><span class="sxs-lookup"><span data-stu-id="b833f-133">![BRE&#45;Walkthrough&#45;ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")</span></span>  
  
11. <span data-ttu-id="b833f-134">Spécifiez le **sélectionner une opération** dans les **sélectionner une opération** groupe en tant que **effectuer une opération Get**.</span><span class="sxs-lookup"><span data-stu-id="b833f-134">Specify the **select operation** in the **Select operation** group as **Perform Get Operation**.</span></span>  
  
     <span data-ttu-id="b833f-135">![BRE &#45; Procédure pas à pas &#45; SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")</span><span class="sxs-lookup"><span data-stu-id="b833f-135">![BRE&#45;Walkthrough&#45;SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")</span></span>  
  
12. <span data-ttu-id="b833f-136">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-136">Click **Finish**.</span></span>  
  
13. <span data-ttu-id="b833f-137">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="b833f-137">Right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
14. <span data-ttu-id="b833f-138">Sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b833f-138">Select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
15. <span data-ttu-id="b833f-139">Pour le **nom de la définition**, type **état de la demande**.</span><span class="sxs-lookup"><span data-stu-id="b833f-139">For the **Definition name**, type **Request Status**.</span></span>  
  
16. <span data-ttu-id="b833f-140">Cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** fichier.</span><span class="sxs-lookup"><span data-stu-id="b833f-140">Click **Browse**, and select the **PO.xsd** file.</span></span>  
  
17. <span data-ttu-id="b833f-141">Dans le **sélectionnez une liaison** boîte de dialogue, développez **PurchaseOrder**, puis double-cliquez sur **état**.</span><span class="sxs-lookup"><span data-stu-id="b833f-141">In the **Select Binding** dialog box, expand **PurchaseOrder**, and then double-click **Status**.</span></span>  
  
18. <span data-ttu-id="b833f-142">Modifier la **type de document** à **RuleTest.PO**.</span><span class="sxs-lookup"><span data-stu-id="b833f-142">Change the **document type** to **RuleTest.PO**.</span></span> <span data-ttu-id="b833f-143">Cette étape est très importante.</span><span class="sxs-lookup"><span data-stu-id="b833f-143">This step is very important.</span></span>  
  
19. <span data-ttu-id="b833f-144">Assurez-vous que le **opération exécuter Set** option est sélectionnée, puis cliquez sur **suivant.**</span><span class="sxs-lookup"><span data-stu-id="b833f-144">Make sure that the  **Perform Set operation** option is selected, and then click **Next.**</span></span>  
  
20. <span data-ttu-id="b833f-145">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-145">Click **Finish**.</span></span>  
  
21. <span data-ttu-id="b833f-146">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="b833f-146">Right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
22. <span data-ttu-id="b833f-147">Assurez-vous que **valeur constante, plage de valeurs ou ensemble de valeurs** est sélectionné, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b833f-147">Make sure that **Constant Value, Range of Values, or Set of Values** is selected, and then click **Next**.</span></span>  
  
23. <span data-ttu-id="b833f-148">Pour le **nom de la définition**, type **nombre maximal d’éléments autorisés**.</span><span class="sxs-lookup"><span data-stu-id="b833f-148">For the **Definition name**, type **Maximum Number of Items Allowed**.</span></span>  
  
24. <span data-ttu-id="b833f-149">Assurez-vous que **type de définition de valeur de constante** est sélectionné, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b833f-149">Make sure that **Constant Value definition type** is selected, and then click **Next**.</span></span>  
  
25. <span data-ttu-id="b833f-150">Type **500** pour la valeur, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-150">Type **500** for the value, and then click **Finish**.</span></span>  
  
26. <span data-ttu-id="b833f-151">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-151">Right-click **Version 1.0(not saved)**, and then click **Save**.</span></span>  
  
27. <span data-ttu-id="b833f-152">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="b833f-152">Right-click **Version 1.0(not saved)**, and then click **Publish**.</span></span>  
  
### <a name="to-use-the-povocabulary-in-the-processpurchaseorder-policy"></a><span data-ttu-id="b833f-153">Pour utiliser le vocabulaire POVocabulary dans la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="b833f-153">To use the POVocabulary in the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="b833f-154">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **copier**.</span><span class="sxs-lookup"><span data-stu-id="b833f-154">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="b833f-155">Avec le bouton droit **ProcessPurchaseOrder** puis cliquez sur **coller une Version de stratégie**.</span><span class="sxs-lookup"><span data-stu-id="b833f-155">Right-click **ProcessPurchaseOrder** and then click **Paste Policy Version**.</span></span>  
  
3.  <span data-ttu-id="b833f-156">Cliquez sur **ApprovalRule** dans **Version 1.1 (non enregistrée)**.</span><span class="sxs-lookup"><span data-stu-id="b833f-156">Click **ApprovalRule** in **Version 1.1(not saved)**.</span></span>  
  
4.  <span data-ttu-id="b833f-157">Dans la fenêtre Explorateur de faits, développez **vocabulaires**, développez **POVocabulary**, développez **Version 1.0**, puis faites glisser **quantité requise**vers le volet IF pour remplacer l’argument de la partie gauche du prédicat LessThanOrEqual.</span><span class="sxs-lookup"><span data-stu-id="b833f-157">In the Facts Explorer window, expand **Vocabularies**, expand **POVocabulary**, expand **Version 1.0**, and then drag **Requested Quantity** to the IF pane to replace the left hand side (LHS) argument of the LessThanOrEqual predicate.</span></span>  
  
     <span data-ttu-id="b833f-158">![BRE &#45; Procédure pas à pas &#45; DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")</span><span class="sxs-lookup"><span data-stu-id="b833f-158">![BRE&#45;Walkthrough&#45;DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")</span></span>  
  
     <span data-ttu-id="b833f-159">![BRE &#45; Procédure pas à pas &#45; ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")</span><span class="sxs-lookup"><span data-stu-id="b833f-159">![BRE&#45;Walkthrough&#45;ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")</span></span>  
  
5.  <span data-ttu-id="b833f-160">Faites glisser **nombre maximal d’éléments autorisés** pour remplacer l’argument côté (RHS) de droite de la condition (**500**).</span><span class="sxs-lookup"><span data-stu-id="b833f-160">Drag **Maximum Number of Items Allowed** to replace the right hand side (RHS) argument of the condition (**500**).</span></span>  
  
6.  <span data-ttu-id="b833f-161">Sélectionnez l’action existante dans le volet THEN, avec le bouton droit, puis cliquez sur **supprimer l’action**.</span><span class="sxs-lookup"><span data-stu-id="b833f-161">Select the existing action in the THEN pane, right-click, and then click **Delete action**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b833f-162">Vous pouvez également appuyer sur la touche SUPPR pour supprimer l'action après l'avoir sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="b833f-162">You can also press DELETE after selecting the action to delete the action.</span></span>  
  
7.  <span data-ttu-id="b833f-163">Faites glisser **état de la demande** à la **puis** volet.</span><span class="sxs-lookup"><span data-stu-id="b833f-163">Drag **Request Status** to the **THEN** pane.</span></span>  
  
8.  <span data-ttu-id="b833f-164">Cliquez sur  **\<une chaîne vide\>**  , puis tapez **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="b833f-164">Click **\<empty string\>** and then type **Approved**.</span></span>  
  
9. <span data-ttu-id="b833f-165">Avec le bouton droit **Version 1.1 (non enregistrée)** dans la fenêtre Explorateur de stratégies, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-165">Right-click **Version 1.1(not saved)** in the Policy Explorer window, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="b833f-166">Avec le bouton droit **Version 1.1 (non enregistrée)** dans la fenêtre Explorateur de stratégies, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="b833f-166">Right-click **Version 1.1(not saved)** in the Policy Explorer window, and then click **Publish**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="b833f-167">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="b833f-167">To test the solution</span></span>  
  
1.  <span data-ttu-id="b833f-168">Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0 déployée**, puis cliquez sur **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="b833f-168">In Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0 - Deployed**, and then click **Undeploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b833f-169">Cette étape est facultative car l'orchestration récupère toujours la dernière version déployée de la stratégie, soit 1.1, une fois l'étape 2 accomplie.</span><span class="sxs-lookup"><span data-stu-id="b833f-169">This step is optional because the orchestration always picks the latest deployed version of the policy, which is 1.1 after you perform step 2.</span></span>  
  
2.  <span data-ttu-id="b833f-170">Avec le bouton droit **Version 1.1 publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="b833f-170">Right-click **Version 1.1- Published**, and then click **Deploy**.</span></span>  
  
3.  <span data-ttu-id="b833f-171">Attendez environ **60** secondes.</span><span class="sxs-lookup"><span data-stu-id="b833f-171">Wait for approximately **60** seconds.</span></span> <span data-ttu-id="b833f-172">Toutes les 60 secondes, le service de mise à jour du moteur des règles recherche dans sa mémoire cache les mises à jour d'une stratégie mise en cache.</span><span class="sxs-lookup"><span data-stu-id="b833f-172">The rule engine update service refreshes its cache every 60 seconds if there are any updates to a policy that it caches.</span></span> <span data-ttu-id="b833f-173">L'accomplissement de l'étape 1 n'entre pas en compte ; l'orchestration récupère toujours la dernière version déployée de la stratégie, soit 1.1.</span><span class="sxs-lookup"><span data-stu-id="b833f-173">It does not matter whether you perform step 1—the orchestration picks up the latest deployed version of the policy, which is 1.1</span></span>  
  
4.  <span data-ttu-id="b833f-174">Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.</span><span class="sxs-lookup"><span data-stu-id="b833f-174">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
5.  <span data-ttu-id="b833f-175">Copie le **SamplePO.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="b833f-175">Copy the **SamplePO.xml** file from C:\BRE-Walkthroughs directory to C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
6.  <span data-ttu-id="b833f-176">Un fichier de sortie doit s'afficher pour l'orchestration dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output.</span><span class="sxs-lookup"><span data-stu-id="b833f-176">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="b833f-177">Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="b833f-177">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
7.  <span data-ttu-id="b833f-178">Répétez les étapes 5 et 6 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**XYZ**).</span><span class="sxs-lookup"><span data-stu-id="b833f-178">Repeat steps 5 and 6 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**XYZ**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b833f-179">La valeur de la **état** reste la même (XYZ), car le moteur de règles n’exécute pas l’action dans le **ApprovalRule** règle, car la condition est évaluée à `false`.</span><span class="sxs-lookup"><span data-stu-id="b833f-179">The value of the **Status** field remains the same (XYZ) because the rule engine does not execute the action in the **ApprovalRule** rule because the condition evaluated to `false`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="b833f-180">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b833f-180">Comments</span></span>  
  
-   <span data-ttu-id="b833f-181">Une fois le vocabulaire enregistré, celui-ci reste modifiable.</span><span class="sxs-lookup"><span data-stu-id="b833f-181">After you save the vocabulary, you can still modify it.</span></span> <span data-ttu-id="b833f-182">Ce n'est pas le cas du vocabulaire publié.</span><span class="sxs-lookup"><span data-stu-id="b833f-182">After you publish the vocabulary, you cannot modify it.</span></span>  
  
-   <span data-ttu-id="b833f-183">Si vous avez besoin de modifier, d'ajouter ou de supprimer une définition, créez une nouvelle version du vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="b833f-183">If you need to modify a definition, add a new definition, or delete a definition, you should create a new version of the vocabulary.</span></span>  
  
-   <span data-ttu-id="b833f-184">Seuls les vocabulaires publiés peuvent être utilisés dans les stratégies.</span><span class="sxs-lookup"><span data-stu-id="b833f-184">Only published vocabularies can be used in policies.</span></span>  
  
-   <span data-ttu-id="b833f-185">Dans la procédure « pour créer le vocabulaire POVocabulary », vous avez modifié le type de document à **RuleTest.PO**.</span><span class="sxs-lookup"><span data-stu-id="b833f-185">In the "To create the POVocabulary vocabulary" procedure, you changed the document type to **RuleTest.PO**.</span></span> <span data-ttu-id="b833f-186">Pour afficher les résultats de cette modification, dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **PO.xsd**.</span><span class="sxs-lookup"><span data-stu-id="b833f-186">To see the results of this change, in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, click **PO.xsd**.</span></span> <span data-ttu-id="b833f-187">Dans la fenêtre Propriétés, notez que **RuleTest** est le nom de l’espace de noms et **PO** est le nom de la **Type**.</span><span class="sxs-lookup"><span data-stu-id="b833f-187">In the Properties window, note that **RuleTest** is the name of the namespace, and **PO** is the name of the **Type**.</span></span>  
  
-   <span data-ttu-id="b833f-188">Dans cette procédure, vous avez utilisé un document XML unique en tant que fait de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="b833f-188">In this walkthrough, you used only an XML document as a fact to the policy.</span></span> <span data-ttu-id="b833f-189">Lorsque vous créez des stratégies, vous pouvez également utiliser des faits .NET et des faits de base de données.</span><span class="sxs-lookup"><span data-stu-id="b833f-189">You can also use .NET facts and database facts when you create policies</span></span>  
  
-   <span data-ttu-id="b833f-190">Lorsque vous sélectionnez **effectuer une opération « Set »** sur la deuxième page de l’Assistant Définition de vocabulaire, vous pouvez spécifier un **format de chaîne complet** sur la page qui suit.</span><span class="sxs-lookup"><span data-stu-id="b833f-190">When you select **Perform "Set" operation** on the second page of the Vocabulary Definition Wizard, you can specify a **Display format string** on the page that follows.</span></span> <span data-ttu-id="b833f-191">Par exemple, vous pourriez modifier le format de chaîne complet **{0} de l’état de la demande** à **demander l’état est : {0}** avant de cliquer sur **Terminer** à l’étape 20 de la « créer procédure de vocabulaire ».</span><span class="sxs-lookup"><span data-stu-id="b833f-191">For example, you could change the display format string from **Request Status {0}** to **Request status is: {0}** before clicking **Finish** in the step 20 of the "create vocabulary" procedure.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b833f-192">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b833f-192">Next Steps</span></span>  
 <span data-ttu-id="b833f-193">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas, ce qui vous donne des instructions pour ajouter une nouvelle règle à la **ProcessPurchaseOrder**stratégie.</span><span class="sxs-lookup"><span data-stu-id="b833f-193">Now that you have completed this walkthrough, perform the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough, which gives you step-by-step instructions for adding a new rule to the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b833f-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b833f-194">See Also</span></span>  
 <span data-ttu-id="b833f-195">[Vocabulaires](../core/vocabularies.md) </span><span class="sxs-lookup"><span data-stu-id="b833f-195">[Vocabularies](../core/vocabularies.md) </span></span>  
 <span data-ttu-id="b833f-196">[Le développement des vocabulaires](../core/how-to-develop-vocabularies.md) </span><span class="sxs-lookup"><span data-stu-id="b833f-196">[How to Develop Vocabularies](../core/how-to-develop-vocabularies.md) </span></span>  
 <span data-ttu-id="b833f-197">[Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="b833f-197">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 [<span data-ttu-id="b833f-198">Agenda et priorité</span><span class="sxs-lookup"><span data-stu-id="b833f-198">Agenda and Priority</span></span>](../core/agenda-and-priority.md)
---
title: "Procédure pas à pas : Modification de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd74440-2a45-4a1a-8e36-98796e1e1392
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7292d541adaf0ae2242d1c504f1a845dde66f5dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-modifying-the-policy"></a><span data-ttu-id="76f0e-102">Procédure pas à pas : Modification de la stratégie</span><span class="sxs-lookup"><span data-stu-id="76f0e-102">Walkthrough: Modifying the Policy</span></span>
<span data-ttu-id="76f0e-103">Cette procédure pas à pas fournit des instructions détaillées pour la création d’une nouvelle version de la **POVocabulary**, création d’une nouvelle version de la **ProcessPurchaseOrder** stratégie et à l’aide de la dernière version de la **POVocabulary** dans la nouvelle version de la **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="76f0e-103">This walkthrough provides step-by-step instructions for creating a new version of the **POVocabulary**, creating a new version of the **ProcessPurchaseOrder** policy, and using the latest version of the **POVocabulary** in the new version of the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76f0e-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="76f0e-104">Prerequisites</span></span>  
 <span data-ttu-id="76f0e-105">Vous devez effectuer la [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="76f0e-105">You must complete the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="76f0e-106">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="76f0e-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="76f0e-107">Cette procédure pas à pas regroupe trois procédures, comme indiqué dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="76f0e-107">This walkthrough contains three procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="76f0e-108">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="76f0e-108">Procedure title</span></span>|<span data-ttu-id="76f0e-109">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="76f0e-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="76f0e-110">Pour modifier le vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="76f0e-110">To modify the POVocabulary vocabulary</span></span>|<span data-ttu-id="76f0e-111">Fournit des instructions détaillées pour la création d’une nouvelle version de vocabulaire pour modifier la valeur de **nombre maximal d’éléments autorisés** de **500** à **1000**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-111">Provides step-by-step instructions for creating a new vocabulary version to modify the value of **Maximum number of items allowed** from **500** to **1000**.</span></span>|  
|<span data-ttu-id="76f0e-112">Pour modifier la stratégie ProcessPurchaseOrder afin d'utiliser le vocabulaire mis à jour</span><span class="sxs-lookup"><span data-stu-id="76f0e-112">To modify the ProcessPurchaseOrder policy to use the updated vocabulary</span></span>|<span data-ttu-id="76f0e-113">Fournit des instructions détaillées pour la création d’une nouvelle version de la **ProcessPurchaseOrder** stratégie à utiliser la nouvelle version de **POVocabulary**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-113">Provides step-by-step instructions for creating a new version of the **ProcessPurchaseOrder** policy to use the new version of **POVocabulary**.</span></span>|  
|<span data-ttu-id="76f0e-114">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="76f0e-114">To test the solution</span></span>|<span data-ttu-id="76f0e-115">Fournit des instructions détaillées sur le test de la solution et la vérification de l'application de la nouvelle stratégie.</span><span class="sxs-lookup"><span data-stu-id="76f0e-115">Provides step-by-step instructions for testing the solution and verifying that the new policy is in effect.</span></span>|  
  
### <a name="to-modify-the-povocabulary-vocabulary"></a><span data-ttu-id="76f0e-116">Pour modifier le vocabulaire POVocabulary</span><span class="sxs-lookup"><span data-stu-id="76f0e-116">To modify the POVocabulary vocabulary</span></span>  
  
1.  <span data-ttu-id="76f0e-117">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-117">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="76f0e-118">Si vous avez Éditeur des règles d’entreprise déjà ouvrir, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.</span><span class="sxs-lookup"><span data-stu-id="76f0e-118">If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76f0e-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="76f0e-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="76f0e-120">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-120">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="76f0e-121">Dans la fenêtre Explorateur de faits, développez **vocabulaires**, puis développez **POVocabulary**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-121">In the Facts Explorer window, expand **Vocabularies**, and then expand **POVocabulary**.</span></span>  
  
3.  <span data-ttu-id="76f0e-122">Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-122">Right-click **Version 1.0 - Published**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="76f0e-123">Avec le bouton droit **POVocabulary**, puis cliquez sur **coller une Version de vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-123">Right-click **POVocabulary**, and then click **Paste Vocabulary Version**.</span></span>  
  
5.  <span data-ttu-id="76f0e-124">Double-cliquez sur **nombre maximal d’éléments autorisés** dans **Version 1.1 (non enregistrée)** pour démarrer l’Assistant Définition de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="76f0e-124">Double-click **Maximum Number of Items Allowed** in **Version 1.1 (not saved)** to start the Vocabulary Definition Wizard.</span></span>  
  
6.  <span data-ttu-id="76f0e-125">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-125">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="76f0e-126">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-126">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="76f0e-127">Remplacez la valeur de **500** à **1000**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-127">Change the value from **500** to **1000**.</span></span>  
  
9. <span data-ttu-id="76f0e-128">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-128">Click **Finish**.</span></span>  
  
10. <span data-ttu-id="76f0e-129">Avec le bouton droit **Version 1.1 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-129">Right-click **Version 1.1 (not saved)**, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="76f0e-130">Avec le bouton droit **Version 1.1**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-130">Right-click **Version 1.1**, and then click **Publish**.</span></span>  
  
### <a name="to-modify-the-processpurchaseorder-policy-to-use-the-updated-vocabulary"></a><span data-ttu-id="76f0e-131">Pour modifier la stratégie ProcessPurchaseOrder afin d'utiliser le vocabulaire mis à jour</span><span class="sxs-lookup"><span data-stu-id="76f0e-131">To modify the ProcessPurchaseOrder policy to use the updated vocabulary</span></span>  
  
1.  <span data-ttu-id="76f0e-132">Dans l’Explorateur de stratégies, développez **stratégies**, puis développez **ProcessPurchaseOrder**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-132">In Policy Explorer, expand **Policies**, and then expand **ProcessPurchaseOrder**.</span></span>  
  
2.  <span data-ttu-id="76f0e-133">Avec le bouton droit **Version 1.2**, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-133">Right-click **Version 1.2**, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="76f0e-134">Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **PastePolicyVersion**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-134">Right-click **ProcessPurchaseOrder**, and then click **PastePolicyVersion**.</span></span>  
  
4.  <span data-ttu-id="76f0e-135">Cliquez sur **ApprovalRule** dans **Version 1.3 (non enregistrée)**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-135">Click **ApprovalRule** in **Version 1.3 (not saved)**.</span></span>  
  
5.  <span data-ttu-id="76f0e-136">Dans l’Explorateur de faits, développez **vocabulaires**, développez **POVocabulary**, puis développez **Version 1.1 publiée**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-136">In Facts Explorer, expand **Vocabularies**, expand **POVocabulary**, and then expand **Version 1.1 - Published**.</span></span>  
  
6.  <span data-ttu-id="76f0e-137">Faites glisser **nombre maximal d’éléments autorisés** dans **Version 1.1 publiée** remplacer **nombre maximal d’éléments autorisés** de la version 1.0, dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="76f0e-137">Drag **Maximum Number of Items Allowed** in **Version 1.1 - Published** to replace **Maximum Number of Items Allowed** of version 1.0 in the IF pane.</span></span>  
  
7.  <span data-ttu-id="76f0e-138">Répétez les étapes 4 à 6 avec **DeniedRule**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-138">Repeat steps 4-6 with **DeniedRule**.</span></span>  
  
8.  <span data-ttu-id="76f0e-139">Avec le bouton droit **Version 1.3 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-139">Right-click **Version 1.3 (not saved)**, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="76f0e-140">Avec le bouton droit **Version 1.3**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-140">Right-click **Version 1.3**, and then click **Publish**.</span></span>  
  
10. <span data-ttu-id="76f0e-141">Avec le bouton droit **Version 1.3**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-141">Right-click **Version 1.3**, and then click **Deploy**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="76f0e-142">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="76f0e-142">To test the solution</span></span>  
  
1.  <span data-ttu-id="76f0e-143">Cliquez sur **Démarrer**, ouvrez **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-143">Click **Start**, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="76f0e-144">Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="76f0e-144">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="76f0e-145">Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-145">Right-click **RuleTestApp**, and then click **Start**.</span></span> <span data-ttu-id="76f0e-146">Si **Démarrer** est désactivée, l’application est déjà en cours d’exécution et vous pouvez ignorer l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="76f0e-146">If **Start** is disabled, the application is already running and you can ignore the next step.</span></span>  
  
3.  <span data-ttu-id="76f0e-147">Cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-147">Click **Start**.</span></span>  
  
4.  <span data-ttu-id="76f0e-148">Copie le **SamplePO2.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="76f0e-148">Copy the **SamplePO2.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
5.  <span data-ttu-id="76f0e-149">Un fichier de sortie doit s'afficher dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output.</span><span class="sxs-lookup"><span data-stu-id="76f0e-149">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory.</span></span> <span data-ttu-id="76f0e-150">Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="76f0e-150">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76f0e-151">La valeur de la **quantité** champ dans SamplePO2.xml est 700.</span><span class="sxs-lookup"><span data-stu-id="76f0e-151">The value of the **Quantity** field in SamplePO2.xml is 700.</span></span> <span data-ttu-id="76f0e-152">La version 1.3 de la **ProcessPurchaseOrder** stratégie compare cette valeur à 1 000 au lieu de comparer avec 500 comme le faisait la version 1.2.</span><span class="sxs-lookup"><span data-stu-id="76f0e-152">Version 1.3 of the **ProcessPurchaseOrder** policy compares this value with 1000 instead of comparing it with 500 as version 1.2 did.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="76f0e-153">Commentaires</span><span class="sxs-lookup"><span data-stu-id="76f0e-153">Comments</span></span>  
  
-   <span data-ttu-id="76f0e-154">Une stratégie publiée n'est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="76f0e-154">A published policy cannot be modified.</span></span> <span data-ttu-id="76f0e-155">Vous devez créer une nouvelle version de la stratégie pour pouvoir la modifier.</span><span class="sxs-lookup"><span data-stu-id="76f0e-155">You must create a new version of the policy to modify it.</span></span> <span data-ttu-id="76f0e-156">De même, un vocabulaire publié n'est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="76f0e-156">Similarly, a published vocabulary cannot be modified.</span></span> <span data-ttu-id="76f0e-157">Vous devez créer une nouvelle version du vocabulaire pour pouvoir le modifier.</span><span class="sxs-lookup"><span data-stu-id="76f0e-157">You must create a new version of the vocabulary to modify it.</span></span>  
  
-   <span data-ttu-id="76f0e-158">L’orchestration d’appel d’une stratégie à l’aide de la **appeler règles** forme utilise la dernière version déployée de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="76f0e-158">The orchestration invoking a policy by using the **Call Rules** shape uses the latest deployed version of the policy.</span></span> <span data-ttu-id="76f0e-159">Par exemple, si vous disposez des versions 1.0, 1.1, 1.2 et 1.3 de la stratégie déployée, l'orchestration utilise la version 1.3.</span><span class="sxs-lookup"><span data-stu-id="76f0e-159">For example, if you have versions 1.0, 1.1, 1.2, and 1.3 of the policy deployed, the orchestration uses version 1.3.</span></span> <span data-ttu-id="76f0e-160">Si celle-ci n'est pas déployée et que la version 1.2 l'est, l'orchestration utilise la version 1.2.</span><span class="sxs-lookup"><span data-stu-id="76f0e-160">If version 1.3 is not deployed and version 1.2 is deployed, the orchestration uses version 1.2.</span></span> <span data-ttu-id="76f0e-161">Par conséquent, si vous souhaitez utiliser la version 1.2, il vous suffit d'annuler le déploiement de la version 1.3, et de vous assurer que la version 1.2 est déployée.</span><span class="sxs-lookup"><span data-stu-id="76f0e-161">Therefore if you want to switch back to using version 1.2, you just need to undeploy version 1.3, and make sure that version 1.2 is deployed.</span></span>  
  
-   <span data-ttu-id="76f0e-162">Pour utiliser une version spécifique d’une stratégie à partir d’une orchestration, vous devez utiliser un **Expression** mettre en forme et appeler le moteur de règles pour la stratégie d’exécution par programme à l’aide de la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="76f0e-162">To use a specific version of a policy from an orchestration, you should use an **Expression** shape and invoke the rule engine to execute the policy programmatically by using the **Policy.Execute** method.</span></span>  
  
-   <span data-ttu-id="76f0e-163">Notez que la version 1.3 de la stratégie utilise les définitions de vocabulaire des versions 1.0 et 1.1 de POVocabulary.</span><span class="sxs-lookup"><span data-stu-id="76f0e-163">Note that version 1.3 of the policy uses the vocabulary definitions from both version 1.0 and version 1.1 of the POVocabulary vocabulary.</span></span> <span data-ttu-id="76f0e-164">Si vous exportez la version 1.3 de la stratégie vers un fichier XML, et l'importez afin de créer la stratégie sur un autre ordinateur, le processus d'importation recherche les deux versions du vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="76f0e-164">If you export version 1.3 of the policy to an XML file, and import it to create the policy on a different computer, the import process looks for both versions of the vocabulary.</span></span> <span data-ttu-id="76f0e-165">Vous devez donc exporter les versions 1.0 et 1.1 du vocabulaire et les importer avant d'importer la version 1.3 de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="76f0e-165">Therefore you need to export both version 1.0 and version 1.1 of the vocabulary and import them before importing version 1.3 of the policy.</span></span>  
  
-   <span data-ttu-id="76f0e-166">Après avoir déployé une version plus récente de la stratégie, vous devez patienter environ 60 secondes avant de tester la solution.</span><span class="sxs-lookup"><span data-stu-id="76f0e-166">After you deploy a newer version of the policy, you should wait approximately 60 seconds before testing the solution.</span></span> <span data-ttu-id="76f0e-167">Le service de mise à jour du moteur des règles recherche les mises à jour d'une stratégie toutes les 60 secondes (1 minute) par défaut.</span><span class="sxs-lookup"><span data-stu-id="76f0e-167">The rule engine update service looks for any updates to a policy every 60 seconds (1 minute) by default.</span></span> <span data-ttu-id="76f0e-168">En cas de mises à jour, il actualise le cache avec les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="76f0e-168">If there are updates, it refreshes the cache with the updated information.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="76f0e-169">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="76f0e-169">Next Steps</span></span>  
  
-   <span data-ttu-id="76f0e-170">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : exécution de la stratégie de suivi](../core/walkthrough-tracking-policy-execution.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour le suivi des détails de la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="76f0e-170">Now that you have completed this walkthrough, perform the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough, which gives you step-by-step instructions for tracking policy execution details.</span></span>
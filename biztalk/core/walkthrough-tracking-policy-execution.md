---
title: "Procédure pas à pas : Suivi d’exécution de la stratégie dans BizTalk Server | Documents Microsoft"
description: "Didacticiel pour activer le suivi et afficher les détails de suivi de la stratégie dans BizTalk Server"
ms.custom: 
ms.date: 04/05/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef88eae7-f0f8-4f3f-85d0-3961a47395b6
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f1baca3a561702546ca2fae10b1c567042cd387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-tracking-policy-execution"></a><span data-ttu-id="161c4-103">Procédure pas à pas : Exécution de la stratégie de suivi</span><span class="sxs-lookup"><span data-stu-id="161c4-103">Walkthrough: Tracking Policy Execution</span></span>
<span data-ttu-id="161c4-104">Procédures pas à pas pour activer le suivi de la **ProcessPurchaseOrder** stratégie et pour afficher les informations de suivi après l’exécution de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="161c4-104">Step-by-step procedures for enabling tracking for the **ProcessPurchaseOrder** policy, and for viewing the tracking information after the policy is executed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="161c4-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="161c4-105">Prerequisites</span></span>  
<span data-ttu-id="161c4-106">Terminer la [procédure pas à pas : modification de la stratégie](../core/walkthrough-modifying-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="161c4-106">Complete the [Walkthrough: Modifying the Policy](../core/walkthrough-modifying-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="enable-tracking-for-the-processpurchaseorder-policy"></a><span data-ttu-id="161c4-107">Activer le suivi de la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="161c4-107">Enable tracking for the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="161c4-108">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="161c4-108">Open **BizTalk Server Administration**.</span></span> <span data-ttu-id="161c4-109">Si elle est déjà ouverte, appuyez sur F5 pour actualiser.</span><span class="sxs-lookup"><span data-stu-id="161c4-109">If it's already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="161c4-110">Développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **RuleTestApp**.</span><span class="sxs-lookup"><span data-stu-id="161c4-110">Expand **Console Root**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="161c4-111">Avec le bouton droit **stratégies**, sélectionnez **ajouter**, puis sélectionnez **stratégie**.</span><span class="sxs-lookup"><span data-stu-id="161c4-111">Right-click **Policies**, select **Add**, and then select **Policy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="161c4-112">Pour activer le suivi d'une stratégie, vous devez ajouter cette stratégie à une application BizTalk par l'intermédiaire de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="161c4-112">To enable tracking for a policy, you must add the policy to a BizTalk application by using the BizTalk Server Administration console.</span></span>  
  
4.  <span data-ttu-id="161c4-113">Dans le **ajouter des stratégies** boîte de dialogue, développez **ProcessPurchaseOrder**, puis sélectionnez Version **1.3**.</span><span class="sxs-lookup"><span data-stu-id="161c4-113">In the **Add Policies** dialog box, expand **ProcessPurchaseOrder**, and select Version **1.3**.</span></span>  
  
5.  <span data-ttu-id="161c4-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="161c4-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="161c4-115">Si vous ne voyez pas **ProcessPurchaseOrder** dans la liste, sélectionnez F5 pour actualiser l’affichage.</span><span class="sxs-lookup"><span data-stu-id="161c4-115">If you don't see **ProcessPurchaseOrder** in the list, select F5 to refresh the view.</span></span>
  
7.  <span data-ttu-id="161c4-116">Avec le bouton droit **ProcessPurchaseOrder**, puis sélectionnez **de suivi.**</span><span class="sxs-lookup"><span data-stu-id="161c4-116">Right-click **ProcessPurchaseOrder**, and then select **Tracking.**</span></span>  
  
8.  <span data-ttu-id="161c4-117">Dans le **Options de suivi de stratégie** boîte de dialogue, sélectionnez les cases à cocher pour **activité des faits**, **d’évaluation de Condition**, **dedéclenchementsderègles**, et **mises à jour de l’Agenda**.</span><span class="sxs-lookup"><span data-stu-id="161c4-117">In the **Policy Tracking Options** dialog box, select all the check boxes for **Fact activity**, **Condition evaluation**, **Rule firings**, and **Agenda updates**.</span></span>  
  
9. <span data-ttu-id="161c4-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="161c4-118">Click **OK**.</span></span>  
  
## <a name="test-the-solution-and-view-the-tracking-information"></a><span data-ttu-id="161c4-119">Tester la solution et afficher les informations de suivi</span><span class="sxs-lookup"><span data-stu-id="161c4-119">Test the solution and view the tracking information</span></span>  
  
1.  <span data-ttu-id="161c4-120">Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et modifiez la valeur de la **état** au champ **XYZ**.</span><span class="sxs-lookup"><span data-stu-id="161c4-120">Open **SamplePO.xml** and **SamplePO2.xml** in notepad, and change the value of the **Status** field to **XYZ**.</span></span>  
  
2.  <span data-ttu-id="161c4-121">Copie **SamplePO.xml** que vous avez créé dans [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) dans le répertoire d’entrée pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="161c4-121">Copy **SamplePO.xml** that you created in [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) to the input directory for the orchestration.</span></span>  
  
3.  <span data-ttu-id="161c4-122">Vous devez voir un fichier de sortie dans le répertoire de sortie de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="161c4-122">You should see an output file in the output directory for the orchestration.</span></span> <span data-ttu-id="161c4-123">Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="161c4-123">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
4.  <span data-ttu-id="161c4-124">Dans **Administration de BizTalk Server**, accédez à la **vue d’ensemble du groupe** page, cliquez sur le **Hub du groupe** onglet, puis cliquez sur **Instances de Service suivies**.</span><span class="sxs-lookup"><span data-stu-id="161c4-124">In **BizTalk Server Administration**, go to the **Group Overview** page, click on the **Group Hub** tab, and then click on **Tracked Service Instances**.</span></span>  
  
5.  <span data-ttu-id="161c4-125">Cliquez sur le nom de l’Orchestration (RuleTest.Orchestration_1), puis cliquez sur **flux Message**.</span><span class="sxs-lookup"><span data-stu-id="161c4-125">Right-click the name of the Orchestration (RuleTest.Orchestration_1), and then click **Message Flow**.</span></span>  
  
6.  <span data-ttu-id="161c4-126">Cliquez sur **suivez ce lien pour afficher les détails de l’exécution de stratégie pour cette instance d’orchestration**.</span><span class="sxs-lookup"><span data-stu-id="161c4-126">Click **Follow this link to view the Policy execution details for this orchestration instance**.</span></span> <span data-ttu-id="161c4-127">Vérifiez que vous consultez la fenêtre qui ressemble à la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="161c4-127">Make sure you see the window that looks like the following figure:</span></span>  
  
     <span data-ttu-id="161c4-128">![BRE &#45; Procédure pas à pas &#45; FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")</span><span class="sxs-lookup"><span data-stu-id="161c4-128">![BRE&#45;Walkthrough&#45;FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")</span></span>  
  
7. <span data-ttu-id="161c4-129">Cliquez sur l’heure ou **ProcessPurchaseOrder1.3** à l’écran suivant apparaît.</span><span class="sxs-lookup"><span data-stu-id="161c4-129">Click the time or **ProcessPurchaseOrder1.3** to see the following screen.</span></span> <span data-ttu-id="161c4-130">Dans cet écran, vous pouvez voir le service (orchestration) qui a demandé l'exécution de la stratégie, l'ID de l'orchestration, ainsi que l'heure d'exécution et l'ID de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="161c4-130">In this screen, you can see the service (orchestration) that requested the policy execution, the ID of the orchestration, the time at which the policy was executed, and the ID of the policy.</span></span>  
  
     <span data-ttu-id="161c4-131">![BRE &#45; Procédure pas à pas &#45; PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")</span><span class="sxs-lookup"><span data-stu-id="161c4-131">![BRE&#45;Walkthrough&#45;PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")</span></span>  
  
8. <span data-ttu-id="161c4-132">Cliquez sur **activité des faits** pour accéder aux faits (données) qui ont été déclarés dans la règle de travail du moteur mémoire et les faits qui ont été retirés de la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="161c4-132">Click **Fact Activity** to see the facts (data) that were asserted into the rule engine's working memory and the facts that were retracted from the rule engine's working memory.</span></span>  
  
     <span data-ttu-id="161c4-133">![BRE &#45; Procédure pas à pas &#45; FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")</span><span class="sxs-lookup"><span data-stu-id="161c4-133">![BRE&#45;Walkthrough&#45;FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")</span></span>  
  
9. <span data-ttu-id="161c4-134">Sur le **fichier** menu, cliquez sur **naviguer précédent**.</span><span class="sxs-lookup"><span data-stu-id="161c4-134">On the **File** menu, click **Navigate back**.</span></span>  
  
10. <span data-ttu-id="161c4-135">Cliquez sur **Conditions évaluées**.</span><span class="sxs-lookup"><span data-stu-id="161c4-135">Click **Conditions that Evaluated**.</span></span> <span data-ttu-id="161c4-136">Vous consultez les détails sur les conditions qui ont été évaluées.</span><span class="sxs-lookup"><span data-stu-id="161c4-136">You see the details about the conditions that were evaluated.</span></span> <span data-ttu-id="161c4-137">Dans ce cas, la stratégie comporte deux règles et chaque règle possède une condition.</span><span class="sxs-lookup"><span data-stu-id="161c4-137">In this case, there are two rules in the policy, and each policy has a condition.</span></span> <span data-ttu-id="161c4-138">Vous pouvez voir que les deux conditions ont été évaluées ; une évaluation à `true`, et l’autre évalués à `false`.</span><span class="sxs-lookup"><span data-stu-id="161c4-138">You can see that two conditions were evaluated; one evaluated to `true`, and the other one evaluated to `false`.</span></span>  
  
     <span data-ttu-id="161c4-139">![BRE &#45; Procédure pas à pas &#45; ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")</span><span class="sxs-lookup"><span data-stu-id="161c4-139">![BRE&#45;Walkthrough&#45;ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")</span></span>  
  
11. <span data-ttu-id="161c4-140">Sur le **fichier** menu, cliquez sur **naviguer précédent**.</span><span class="sxs-lookup"><span data-stu-id="161c4-140">On the **File** menu, click **Navigate back**.</span></span>  
  
12. <span data-ttu-id="161c4-141">Cliquez sur **mises à jour de l’Agenda**.</span><span class="sxs-lookup"><span data-stu-id="161c4-141">Click **Agenda Updates**.</span></span> <span data-ttu-id="161c4-142">Vous pouvez voir que seule la règle ApprovalRule est ajoutée à l'agenda.</span><span class="sxs-lookup"><span data-stu-id="161c4-142">You can see that only the ApprovalRule is added to the agenda.</span></span> <span data-ttu-id="161c4-143">La règle DeniedRule n'est pas ajoutée à l'agenda car sa condition est évaluée sur `false`.</span><span class="sxs-lookup"><span data-stu-id="161c4-143">The DeniedRule is not added to the agenda because its condition evaluates to `false`.</span></span>  
  
     <span data-ttu-id="161c4-144">![BRE &#45; Procédure pas à pas &#45; Agenda](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")</span><span class="sxs-lookup"><span data-stu-id="161c4-144">![BRE&#45;Walkthrough&#45;Agenda](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")</span></span>  
  
13. <span data-ttu-id="161c4-145">Cliquez sur **ApprovalRule** pour afficher la définition de la règle ApprovalRule.</span><span class="sxs-lookup"><span data-stu-id="161c4-145">Click **ApprovalRule** to see the definition of the ApprovalRule.</span></span>  
  
14. <span data-ttu-id="161c4-146">Sur le **fichier** menu, cliquez sur **naviguer précédent**.</span><span class="sxs-lookup"><span data-stu-id="161c4-146">On the **File** menu, click **Navigate back**.</span></span>  
  
15. <span data-ttu-id="161c4-147">Sur **fichier** menu, cliquez sur **naviguer arrière** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="161c4-147">On **File** menu, click **Navigate back** again.</span></span>  
  
16. <span data-ttu-id="161c4-148">Cliquez sur **règles déclenchées**.</span><span class="sxs-lookup"><span data-stu-id="161c4-148">Click **Rules that fired**.</span></span> <span data-ttu-id="161c4-149">Vous voyez que seule la règle ApprovalRule a été déclenchée (les actions de la règle ApprovalRule ont été exécutées).</span><span class="sxs-lookup"><span data-stu-id="161c4-149">You can see that only ApprovalRule was fired (actions for the ApprovalRule were executed).</span></span>  
  
17. <span data-ttu-id="161c4-150">Sur le **fichier** menu, cliquez sur **naviguer précédent**.</span><span class="sxs-lookup"><span data-stu-id="161c4-150">On the **File** menu, click **Navigate back**.</span></span>  
  
18. <span data-ttu-id="161c4-151">Cliquez sur **les règles non déclenchées**.</span><span class="sxs-lookup"><span data-stu-id="161c4-151">Click **Rules that did not fire**.</span></span> <span data-ttu-id="161c4-152">La règle DeniedRule n'a pas été déclenchée car elle ne figurait pas dans l'agenda.</span><span class="sxs-lookup"><span data-stu-id="161c4-152">You can see that DeniedRule was not fired because it was not in the agenda.</span></span>  
  
19. <span data-ttu-id="161c4-153">Répétez les étapes 1-18 avec **SamplePO2.xml**.</span><span class="sxs-lookup"><span data-stu-id="161c4-153">Repeat steps 1-18 with **SamplePO2.xml**.</span></span>  
  
## <a name="key-details"></a><span data-ttu-id="161c4-154">Détails de la clé</span><span class="sxs-lookup"><span data-stu-id="161c4-154">Key details</span></span>  
  
-   <span data-ttu-id="161c4-155">Les informations de suivi de la stratégie sont similaires aux informations de suivi disponibles dans l'Éditeur des règles d'entreprise lorsque vous testez une stratégie.</span><span class="sxs-lookup"><span data-stu-id="161c4-155">The policy tracking information is very similar to the tracking information you see in Business Rule Composer when you test a policy.</span></span>  
  
-   <span data-ttu-id="161c4-156">Bien que le nom de l'orchestration soit RuleTest.odx, il apparaît sous la forme Orchestration_1, car le nom du type de l'orchestration est défini sur Orchestration_1 même si le nom est changé.</span><span class="sxs-lookup"><span data-stu-id="161c4-156">Although the orchestration name is RuleTest.odx, you see the name of the orchestration as Orchestration_1, because the Type Name for the orchestration is set to Orchestration_1 even though the Name is changed.</span></span> <span data-ttu-id="161c4-157">Le suivi affiche le nom de l’orchestration dans le format \<Namespace >.\< Tapez le nom >.</span><span class="sxs-lookup"><span data-stu-id="161c4-157">Tracking is showing you the orchestration name in the format \<Namespace>.\<Type Name>.</span></span>  
  
-   <span data-ttu-id="161c4-158">Si vous supprimez une stratégie d'une application BizTalk par le biais de la console Administration de BizTalk Server, cette stratégie est non seulement supprimée de l'application mais également de la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="161c4-158">If you delete a policy from a BizTalk application by using the BizTalk Server Administration console, the tool deletes the policy not only from the application, but also from the rule engine database.</span></span> <span data-ttu-id="161c4-159">Elle n'apparaît donc plus dans l'Éditeur des règles d'entreprise (appuyez sur F5 pour actualiser l'affichage).</span><span class="sxs-lookup"><span data-stu-id="161c4-159">You will no longer see the policy in Business Rule Composer (press F5 to refresh).</span></span> <span data-ttu-id="161c4-160">Vous devez donc faire très attention lorsque vous supprimez une stratégie d'une application.</span><span class="sxs-lookup"><span data-stu-id="161c4-160">Therefore, you should be careful when deleting a policy from an application.</span></span>  
  
-   <span data-ttu-id="161c4-161">Lorsque vous arrêtez RuleTestApp et sélectionnez le **arrêt complet** , la stratégie ProcessPurchaseOrder (version 1.3) est automatiquement annulée.</span><span class="sxs-lookup"><span data-stu-id="161c4-161">When you stop the RuleTestApp and select the **Full Stop** option, the ProcessPurchaseOrder policy (version 1.3) is automatically undeployed.</span></span>  
  
-   <span data-ttu-id="161c4-162">Si une stratégie est utilisée par plusieurs applications, créez une application séparée pour cette stratégie, puis créez des références vers celle-ci à partir des applications clientes.</span><span class="sxs-lookup"><span data-stu-id="161c4-162">If a policy is used by multiple applications, create a separate application for the policy and then create references to it from the client applications.</span></span> <span data-ttu-id="161c4-163">Si vous ajoutez la stratégie à toutes les applications clientes, lorsque vous arrêtez l'une de ces applications, le déploiement de la stratégie est annulé et les autres applications clientes ne peuvent plus l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="161c4-163">If you add the policy to all the client applications, when you stop one of the client applications, the policy is undeployed, and the other client applications can no longer use the policy.</span></span> <span data-ttu-id="161c4-164">Il est donc conseillé de créer une application séparée pour les stratégies partagées par deux applications ou plus.</span><span class="sxs-lookup"><span data-stu-id="161c4-164">Therefore it is a good practice to create a separate application for a policy that is shared across two or more applications.</span></span>  
  
-   <span data-ttu-id="161c4-165">Lorsque vous démarrez RuleTestApp, la stratégie ProcessPurchaseOrder (version 1.3) est automatiquement déployée.</span><span class="sxs-lookup"><span data-stu-id="161c4-165">When you start the RuleTestApp, the ProcessPurchaseOrder policy (version 1.3) is automatically deployed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="161c4-166">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="161c4-166">Next Steps</span></span>  
 <span data-ttu-id="161c4-167">Maintenant que vous avez terminé cette procédure pas à pas, accédez à la [procédure pas à pas : déploiement de la stratégie](../core/walkthrough-deploying-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour déployer des stratégies.</span><span class="sxs-lookup"><span data-stu-id="161c4-167">Now that you have completed this walkthrough, go to the [Walkthrough: Deploying the Policy](../core/walkthrough-deploying-the-policy.md) walkthrough, which gives you step-by-step instructions for deploying policies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161c4-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="161c4-168">See Also</span></span>  
 <span data-ttu-id="161c4-169">[Comment configurer le suivi d’une stratégie](../core/how-to-configure-tracking-for-a-policy.md) </span><span class="sxs-lookup"><span data-stu-id="161c4-169">[How to Configure Tracking for a Policy](../core/how-to-configure-tracking-for-a-policy.md) </span></span>  
 [<span data-ttu-id="161c4-170">Gestion des stratégies</span><span class="sxs-lookup"><span data-stu-id="161c4-170">Managing Policies</span></span>](../core/managing-policies.md)
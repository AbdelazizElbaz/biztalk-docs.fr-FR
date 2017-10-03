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
# <a name="walkthrough-tracking-policy-execution"></a>Procédure pas à pas : Exécution de la stratégie de suivi
Procédures pas à pas pour activer le suivi de la **ProcessPurchaseOrder** stratégie et pour afficher les informations de suivi après l’exécution de la stratégie.  
  
## <a name="prerequisites"></a>Conditions préalables  
Terminer la [procédure pas à pas : modification de la stratégie](../core/walkthrough-modifying-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.  
  
## <a name="enable-tracking-for-the-processpurchaseorder-policy"></a>Activer le suivi de la stratégie ProcessPurchaseOrder  
  
1.  Ouvrez **Administration de BizTalk Server.** Si elle est déjà ouverte, appuyez sur F5 pour actualiser.  
  
2.  Développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **RuleTestApp**.  
  
3.  Avec le bouton droit **stratégies**, sélectionnez **ajouter**, puis sélectionnez **stratégie**.  
  
    > [!NOTE]
    >  Pour activer le suivi d'une stratégie, vous devez ajouter cette stratégie à une application BizTalk par l'intermédiaire de la console Administration de BizTalk Server.  
  
4.  Dans le **ajouter des stratégies** boîte de dialogue, développez **ProcessPurchaseOrder**, puis sélectionnez Version **1.3**.  
  
5.  Cliquez sur **OK**.  
  
6.  Si vous ne voyez pas **ProcessPurchaseOrder** dans la liste, sélectionnez F5 pour actualiser l’affichage.
  
7.  Avec le bouton droit **ProcessPurchaseOrder**, puis sélectionnez **de suivi.**  
  
8.  Dans le **Options de suivi de stratégie** boîte de dialogue, sélectionnez les cases à cocher pour **activité des faits**, **d’évaluation de Condition**, **dedéclenchementsderègles**, et **mises à jour de l’Agenda**.  
  
9. Cliquez sur **OK**.  
  
## <a name="test-the-solution-and-view-the-tracking-information"></a>Tester la solution et afficher les informations de suivi  
  
1.  Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et modifiez la valeur de la **état** au champ **XYZ**.  
  
2.  Copie **SamplePO.xml** que vous avez créé dans [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) dans le répertoire d’entrée pour l’orchestration.  
  
3.  Vous devez voir un fichier de sortie dans le répertoire de sortie de l'orchestration. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
4.  Dans **Administration de BizTalk Server**, accédez à la **vue d’ensemble du groupe** page, cliquez sur le **Hub du groupe** onglet, puis cliquez sur **Instances de Service suivies**.  
  
5.  Cliquez sur le nom de l’Orchestration (RuleTest.Orchestration_1), puis cliquez sur **flux Message**.  
  
6.  Cliquez sur **suivez ce lien pour afficher les détails de l’exécution de stratégie pour cette instance d’orchestration**. Vérifiez que vous consultez la fenêtre qui ressemble à la figure suivante :  
  
     ![BRE &#45; Procédure pas à pas &#45; FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")  
  
7. Cliquez sur l’heure ou **ProcessPurchaseOrder1.3** à l’écran suivant apparaît. Dans cet écran, vous pouvez voir le service (orchestration) qui a demandé l'exécution de la stratégie, l'ID de l'orchestration, ainsi que l'heure d'exécution et l'ID de la stratégie.  
  
     ![BRE &#45; Procédure pas à pas &#45; PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")  
  
8. Cliquez sur **activité des faits** pour accéder aux faits (données) qui ont été déclarés dans la règle de travail du moteur mémoire et les faits qui ont été retirés de la mémoire de travail du moteur de règles.  
  
     ![BRE &#45; Procédure pas à pas &#45; FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")  
  
9. Sur le **fichier** menu, cliquez sur **naviguer précédent**.  
  
10. Cliquez sur **Conditions évaluées**. Vous consultez les détails sur les conditions qui ont été évaluées. Dans ce cas, la stratégie comporte deux règles et chaque règle possède une condition. Vous pouvez voir que les deux conditions ont été évaluées ; une évaluation à `true`, et l’autre évalués à `false`.  
  
     ![BRE &#45; Procédure pas à pas &#45; ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")  
  
11. Sur le **fichier** menu, cliquez sur **naviguer précédent**.  
  
12. Cliquez sur **mises à jour de l’Agenda**. Vous pouvez voir que seule la règle ApprovalRule est ajoutée à l'agenda. La règle DeniedRule n'est pas ajoutée à l'agenda car sa condition est évaluée sur `false`.  
  
     ![BRE &#45; Procédure pas à pas &#45; Agenda](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")  
  
13. Cliquez sur **ApprovalRule** pour afficher la définition de la règle ApprovalRule.  
  
14. Sur le **fichier** menu, cliquez sur **naviguer précédent**.  
  
15. Sur **fichier** menu, cliquez sur **naviguer arrière** à nouveau.  
  
16. Cliquez sur **règles déclenchées**. Vous voyez que seule la règle ApprovalRule a été déclenchée (les actions de la règle ApprovalRule ont été exécutées).  
  
17. Sur le **fichier** menu, cliquez sur **naviguer précédent**.  
  
18. Cliquez sur **les règles non déclenchées**. La règle DeniedRule n'a pas été déclenchée car elle ne figurait pas dans l'agenda.  
  
19. Répétez les étapes 1-18 avec **SamplePO2.xml**.  
  
## <a name="key-details"></a>Détails de la clé  
  
-   Les informations de suivi de la stratégie sont similaires aux informations de suivi disponibles dans l'Éditeur des règles d'entreprise lorsque vous testez une stratégie.  
  
-   Bien que le nom de l'orchestration soit RuleTest.odx, il apparaît sous la forme Orchestration_1, car le nom du type de l'orchestration est défini sur Orchestration_1 même si le nom est changé. Le suivi affiche le nom de l’orchestration dans le format \<Namespace >.\< Tapez le nom >.  
  
-   Si vous supprimez une stratégie d'une application BizTalk par le biais de la console Administration de BizTalk Server, cette stratégie est non seulement supprimée de l'application mais également de la base de données du moteur de règles. Elle n'apparaît donc plus dans l'Éditeur des règles d'entreprise (appuyez sur F5 pour actualiser l'affichage). Vous devez donc faire très attention lorsque vous supprimez une stratégie d'une application.  
  
-   Lorsque vous arrêtez RuleTestApp et sélectionnez le **arrêt complet** , la stratégie ProcessPurchaseOrder (version 1.3) est automatiquement annulée.  
  
-   Si une stratégie est utilisée par plusieurs applications, créez une application séparée pour cette stratégie, puis créez des références vers celle-ci à partir des applications clientes. Si vous ajoutez la stratégie à toutes les applications clientes, lorsque vous arrêtez l'une de ces applications, le déploiement de la stratégie est annulé et les autres applications clientes ne peuvent plus l'utiliser. Il est donc conseillé de créer une application séparée pour les stratégies partagées par deux applications ou plus.  
  
-   Lorsque vous démarrez RuleTestApp, la stratégie ProcessPurchaseOrder (version 1.3) est automatiquement déployée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, accédez à la [procédure pas à pas : déploiement de la stratégie](../core/walkthrough-deploying-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour déployer des stratégies.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le suivi d’une stratégie](../core/how-to-configure-tracking-for-a-policy.md)   
 [Gestion des stratégies](../core/managing-policies.md)
---
title: "Procédure pas à pas : Ajout d’une règle à la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2a682c0-a5d7-4550-924d-be9fa29b84d2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b08fc197c16f04f3eb738468421db340060b9613
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-adding-a-rule-to-the-policy"></a>Procédure pas à pas : Ajout d’une règle à la stratégie
Cette procédure pas à pas fournit des instructions détaillées pour l’ajout d’une règle nommée **DeniedRule** à la **ProcessPurchaseOrder** stratégie.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : création et utilisation d’un vocabulaire dans la stratégie](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure pas à pas regroupe trois procédures, comme indiqué dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour ajouter la règle DeniedRule à la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour l’ajout d’une nouvelle règle nommée **DeniedRule** à la **ProcessPurchaseOrder** stratégie. Le **DeniedRule** règle définit la valeur de la **état** au champ **refusé** si la valeur de la **quantité** est supérieure à 500.|  
|Pour procéder à des tests à l'aide de l'Éditeur des règles d'entreprise|Fournit des instructions détaillées pour tester le **ProcessPurchaseOrder** stratégie à l’aide de l’éditeur des règles d’entreprise.|  
|Pour tester la solution|Fournit des instructions pas à pas pour le test de la solution.|  
  
### <a name="to-add-deniedrule-to-the-processpurchaseorder-policy"></a>Pour ajouter la règle DeniedRule à la stratégie ProcessPurchaseOrder  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.1**, puis cliquez sur **copier**.  
  
3.  Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **coller une Version de stratégie**.  
  
4.  Avec le bouton droit **Version 1.2 (non enregistrée)**, cliquez sur **ajouter une nouvelle règle**, puis modifiez le nom de la règle à **DeniedRule**.  
  
5.  Si vous avez oublié de modifier le nom de la règle à **DeniedRule** à l’étape 4, cliquez sur **Rule1**et remplacez le nom par **DeniedRule** dans la fenêtre Propriétés.  
  
6.  Dans le volet IF, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **supérieur à**.  
  
7.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.  
  
8.  Développez **vocabulaires**, développez **POVocabulary**, développez **Version 1.0 - publiée**, puis faites glisser **quantité de la demande** à **argument1** dans le volet IF.  
  
9. Faites glisser **nombre maximal d’éléments autorisés** à **argument2** dans le volet IF.  
  
10. Faites glisser **état de la demande** vers le volet THEN.  
  
11. Cliquez sur  **\<une chaîne vide\>**  , puis tapez **refusé**.  
  
12. Avec le bouton droit **Version 1.2 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
13. Avec le bouton droit **Version 1.2**, puis cliquez sur **publier**.  
  
14. Avec le bouton droit **Version 1.2**, puis cliquez sur **déployer**.  
  
### <a name="to-test-with-business-rule-composer"></a>Pour procéder à des tests à l'aide de l'Éditeur des règles d'entreprise  
  
1.  Ouvrez les fichiers SamplePO.xml et SamplePO2.xml dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.2**, puis cliquez sur **tester la stratégie**.  
  
3.  Sous le **XmlDocument** nœud, sélectionnez **RuleTest.PO**, puis cliquez sur **ajouter une Instance**.  
  
4.  Sélectionnez **SamplePO.xml**, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **Test**.  
  
6.  Examinez le **mise à jour de l’Agenda** section de la sortie et notez que seule **ApprovalRule** est ajouté à l’agenda. C'est par conséquent la seule qui se déclenche (les actions associées à la règle sont exécutées).  
  
7.  Ouvrir **SamplePO.xml** dans le bloc-notes et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
8.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.2**, puis cliquez sur **tester la stratégie.**  
  
9. Sélectionnez **SamplePO.xml**, cliquez sur **supprimer l’instance**, puis cliquez sur **ajouter une Instance**.  
  
10. Sélectionnez **SamplePO2.xml**, puis cliquez sur **ouvrir**.  
  
11. Cliquez sur **Test**.  
  
12. Examinez le **mise à jour de l’Agenda** section de la sortie et notez que seule **DeniedRule** est ajouté à l’agenda. C'est par conséquent la seule qui se déclenche.  
  
13. Ouvrez **SamplePO2.xml** dans le bloc-notes et notez que la valeur de la **état** champ est **refusé**.  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.  
  
2.  Copie le **SamplePO.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.  
  
3.  Un fichier de sortie doit s'afficher pour l'orchestration dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
4.  Répétez les étapes 2 et 3 avec **SamplePO2.xml**et notez que la valeur de la **état** champ est défini sur **refusé** dans le document de sortie. Cela prouve que l’orchestration à l’aide de la version 1.2 de la **ProcessPurchaseOrder** stratégie. L’orchestration utilise la dernière version déployée de la **ProcessPurchaseOrder** stratégie, qui est **1.2**. Il n'est pas nécessaire d'annuler le déploiement de la version 1.1 de la stratégie pour utiliser la version 1.2. Cependant, vous devez patienter environ 60 secondes avant de tester la solution. Pour plus d'informations, voir la section Commentaires.  
  
## <a name="comments"></a>Commentaires  
  
-   Une stratégie peut comporter une ou plusieurs règles d'entreprise. Il n'y a pas de limite logique au nombre de règles dans une stratégie.  
  
-   Le moteur de règles utilise un algorithme évaluation de condition-résolution des conflits-exécution d'action. Dans le **évaluation de Condition** étape, le moteur de règles évalue les conditions de toutes les règles. Les règles dont les conditions sont True deviennent candidates à l'exécution. Dans le **la résolution des conflits** à l’étape, les règles candidates sont ajoutées à l’agenda dans l’ordre de la priorité de la règle. Dans le **exécution d’Action** à l’étape, les actions dans les règles candidates sont exécutées. Si des règles candidates ont la même priorité, il n'y a pas d'ordre déterministe dans lequel les actions de ces règles sont exécutées. Considérez qu'elles sont exécutées en parallèle.  
  
-   Dans ce scénario, pour tout exemple de fichier donné, une seule de ces règles est déclenchée. Vérifiez que vous remplacez la valeur de la **état** champ avant d’exécuter un test.  
  
-   Après avoir déployé une nouvelle version de la stratégie, vous devez patienter environ 60 secondes avant de d'exécuter le test. Le service de mise à jour du moteur des règles interroge régulièrement la base de données du moteur de règles (toutes les 60 secondes par défaut) afin de rechercher les stratégies nouvellement déployées. Il met l'objet de stratégie à jour dans la mémoire à l'aide des informations sur la dernière version déployée de la stratégie provenant de la base de données du moteur de règles.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : modification de la stratégie](../core/walkthrough-modifying-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour la modification de la stratégie d’approuver les bons de commande avec la valeur de **quantité** inférieure ou égale à 1 000 (au lieu de 500).  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md)   
 [Agenda et priorité](../core/agenda-and-priority.md)
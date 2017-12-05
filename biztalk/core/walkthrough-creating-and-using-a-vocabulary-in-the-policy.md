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
# <a name="walkthrough-creating-and-using-a-vocabulary-in-the-policy"></a>Procédure pas à pas : Création et utilisation de vocabulaire dans la stratégie
Cette procédure pas à pas fournit des procédures pas à pas pour créer un vocabulaire et à son utilisation dans les **ProcessPurchaseOrder** stratégie.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas. En outre, nous vous conseillons de suivre toutes les procédures pas à pas précédant celle-ci dans la documentation.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure pas à pas regroupe trois procédures, comme indiqué dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour créer le vocabulaire POVocabulary|Fournit des instructions détaillées pour la création de la **POVocabulary** vocabulaire avec trois définitions : quantité requise, nombre maximal d’éléments autorisés et état de la demande.|  
|Pour utiliser le vocabulaire POVocabulary dans la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour la création d’une nouvelle version de la **ProcessPurchaseOrder** à l’aide de la stratégie **POVocabulary**.|  
|Pour tester la solution|Fournit des instructions pas à pas pour le test de la solution.|  
  
### <a name="to-create-the-povocabulary-vocabulary"></a>Pour créer le vocabulaire POVocabulary  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.  
  
3.  Avec le bouton droit **vocabulaires**, cliquez sur **ajouter un nouveau vocabulaire**, puis tapez **POVocabulary** comme nom pour le vocabulaire.  
  
4.  Si vous n’avez pas modifié le nom du vocabulaire en POVocabulary à l’étape 3, modifiez le nom du vocabulaire pour **POVocabulary**dans la fenêtre Propriétés.  
  
5.  Avec le bouton droit **Version 1.0 (non enregistrée)** dans **POVocabulary**, puis cliquez sur **ajouter une nouvelle définition**.  
  
6.  Dans l’Assistant Définition de vocabulaire, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
7.  Pour le **nom de la définition**, type **quantité requise**.  
  
8.  Cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** vous avez créé dans [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md).  
  
9. Dans le **sélectionnez une liaison** boîte de dialogue, développez **PurchaseOrder**, développez **élément**, puis double-cliquez sur **quantité**.  
  
10. Assurez-vous que le **type de document** a la valeur **RuleTest.PO**. Si elle n’est pas le cas, modifiez le type de document à RuleTest.PO. Cette étape est très importante.  
  
     ![BRE &#45; Procédure pas à pas &#45; ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")  
  
11. Spécifiez le **sélectionner une opération** dans les **sélectionner une opération** groupe en tant que **effectuer une opération Get**.  
  
     ![BRE &#45; Procédure pas à pas &#45; SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")  
  
12. Cliquez sur **Terminer**.  
  
13. Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.  
  
14. Sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
15. Pour le **nom de la définition**, type **état de la demande**.  
  
16. Cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** fichier.  
  
17. Dans le **sélectionnez une liaison** boîte de dialogue, développez **PurchaseOrder**, puis double-cliquez sur **état**.  
  
18. Modifier la **type de document** à **RuleTest.PO**. Cette étape est très importante.  
  
19. Assurez-vous que le **opération exécuter Set** option est sélectionnée, puis cliquez sur **suivant.**  
  
20. Cliquez sur **Terminer**.  
  
21. Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.  
  
22. Assurez-vous que **valeur constante, plage de valeurs ou ensemble de valeurs** est sélectionné, puis cliquez sur **suivant**.  
  
23. Pour le **nom de la définition**, type **nombre maximal d’éléments autorisés**.  
  
24. Assurez-vous que **type de définition de valeur de constante** est sélectionné, puis cliquez sur **suivant**.  
  
25. Type **500** pour la valeur, puis cliquez sur **Terminer**.  
  
26. Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
27. Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.  
  
### <a name="to-use-the-povocabulary-in-the-processpurchaseorder-policy"></a>Pour utiliser le vocabulaire POVocabulary dans la stratégie ProcessPurchaseOrder  
  
1.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **copier**.  
  
2.  Avec le bouton droit **ProcessPurchaseOrder** puis cliquez sur **coller une Version de stratégie**.  
  
3.  Cliquez sur **ApprovalRule** dans **Version 1.1 (non enregistrée)**.  
  
4.  Dans la fenêtre Explorateur de faits, développez **vocabulaires**, développez **POVocabulary**, développez **Version 1.0**, puis faites glisser **quantité requise**vers le volet IF pour remplacer l’argument de la partie gauche du prédicat LessThanOrEqual.  
  
     ![BRE &#45; Procédure pas à pas &#45; DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")  
  
     ![BRE &#45; Procédure pas à pas &#45; ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")  
  
5.  Faites glisser **nombre maximal d’éléments autorisés** pour remplacer l’argument côté (RHS) de droite de la condition (**500**).  
  
6.  Sélectionnez l’action existante dans le volet THEN, avec le bouton droit, puis cliquez sur **supprimer l’action**.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur la touche SUPPR pour supprimer l'action après l'avoir sélectionnée.  
  
7.  Faites glisser **état de la demande** à la **puis** volet.  
  
8.  Cliquez sur  **\<une chaîne vide\>**  , puis tapez **approuvé**.  
  
9. Avec le bouton droit **Version 1.1 (non enregistrée)** dans la fenêtre Explorateur de stratégies, puis cliquez sur **enregistrer**.  
  
10. Avec le bouton droit **Version 1.1 (non enregistrée)** dans la fenêtre Explorateur de stratégies, puis cliquez sur **publier**.  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0 déployée**, puis cliquez sur **annuler le déploiement**.  
  
    > [!NOTE]
    >  Cette étape est facultative car l'orchestration récupère toujours la dernière version déployée de la stratégie, soit 1.1, une fois l'étape 2 accomplie.  
  
2.  Avec le bouton droit **Version 1.1 publiée**, puis cliquez sur **déployer**.  
  
3.  Attendez environ **60** secondes. Toutes les 60 secondes, le service de mise à jour du moteur des règles recherche dans sa mémoire cache les mises à jour d'une stratégie mise en cache. L'accomplissement de l'étape 1 n'entre pas en compte ; l'orchestration récupère toujours la dernière version déployée de la stratégie, soit 1.1.  
  
4.  Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.  
  
5.  Copie le **SamplePO.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.  
  
6.  Un fichier de sortie doit s'afficher pour l'orchestration dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
7.  Répétez les étapes 5 et 6 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**XYZ**).  
  
    > [!NOTE]
    >  La valeur de la **état** reste la même (XYZ), car le moteur de règles n’exécute pas l’action dans le **ApprovalRule** règle, car la condition est évaluée à `false`.  
  
## <a name="comments"></a>Commentaires  
  
-   Une fois le vocabulaire enregistré, celui-ci reste modifiable. Ce n'est pas le cas du vocabulaire publié.  
  
-   Si vous avez besoin de modifier, d'ajouter ou de supprimer une définition, créez une nouvelle version du vocabulaire.  
  
-   Seuls les vocabulaires publiés peuvent être utilisés dans les stratégies.  
  
-   Dans la procédure « pour créer le vocabulaire POVocabulary », vous avez modifié le type de document à **RuleTest.PO**. Pour afficher les résultats de cette modification, dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **PO.xsd**. Dans la fenêtre Propriétés, notez que **RuleTest** est le nom de l’espace de noms et **PO** est le nom de la **Type**.  
  
-   Dans cette procédure, vous avez utilisé un document XML unique en tant que fait de la stratégie. Lorsque vous créez des stratégies, vous pouvez également utiliser des faits .NET et des faits de base de données.  
  
-   Lorsque vous sélectionnez **effectuer une opération « Set »** sur la deuxième page de l’Assistant Définition de vocabulaire, vous pouvez spécifier un **format de chaîne complet** sur la page qui suit. Par exemple, vous pourriez modifier le format de chaîne complet **{0} de l’état de la demande** à **demander l’état est : {0}** avant de cliquer sur **Terminer** à l’étape 20 de la « créer procédure de vocabulaire ».  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas, ce qui vous donne des instructions pour ajouter une nouvelle règle à la **ProcessPurchaseOrder**stratégie.  
  
## <a name="see-also"></a>Voir aussi  
 [Vocabulaires](../core/vocabularies.md)   
 [Le développement des vocabulaires](../core/how-to-develop-vocabularies.md)   
 [Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md)   
 [Agenda et priorité](../core/agenda-and-priority.md)
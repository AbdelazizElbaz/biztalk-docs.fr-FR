---
title: 'Procédure pas à pas : Appel de la stratégie à partir d’une Orchestration | Documents Microsoft'
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb2d2974-8a36-4d36-905c-799e4236ef99
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36de942d34a4235b689b464192a460451e7c921a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="walkthrough-invoking-the-policy-from-an-orchestration"></a>Procédure pas à pas : Appel de la stratégie à partir d’une Orchestration
Vous pouvez appeler une stratégie à partir d'une orchestration à l'aide de l'une des méthodes suivantes :  
  
-   À l’aide de la **appeler règles** forme  
  
-   À l’aide de la **Expression** mettre en forme et l’appelant de façon programmée le moteur de règles pour exécuter la stratégie (**Policy.Execute** méthode)  
  
 À l’aide de la **appeler règles** forme est la façon la plus courante et recommandée pour appeler une stratégie à partir d’une orchestration. Cette procédure pas à pas fournit des instructions détaillées pour l’utilisation de la **appeler règles** forme pour appeler le **ProcessPurchaseOrder** stratégie.  
  
## <a name="prerequisites"></a>Configuration requise  
 Vous devez effectuer la [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de sept autres procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour créer un projet BizTalk avec un schéma et une orchestration|Fournit des instructions détaillées pour la création d’un schéma et une orchestration qui appelle le **ProcessPurchaseOrder** stratégie.|  
|Pour créer des variables de message|Fournit des instructions détaillées pour la création des variables de message utilisées dans l'orchestration.|  
|Pour configurer des formes|Fournit des instructions détaillées pour la configuration de formes dans l'orchestration.|  
|Pour créer des ports|Fournit des instructions détaillées pour la création de ports dans l'orchestration.|  
|Pour connecter des ports aux formes|Fournit des instructions détaillées pour la connexion de ports aux formes.|  
|Pour créer et déployer la solution|Fournit des instructions détaillées pour la création et le déploiement de la solution.|  
|Pour tester la solution|Fournit des instructions pas à pas pour le test de la solution.|  
  
### <a name="to-create-a-biztalk-project-with-a-schema-and-an-orchestration"></a>Pour créer un projet BizTalk avec un schéma et une orchestration  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **projets BizTalk**.|  
    |**Modèles**|Cliquez sur **vide le projet BizTalk Server**.|  
    |**Nom**|Type **RuleTest**.|  
    |**Emplacement**|Spécifiez **C:\BRE-Walkthroughs**.|  
    |**Nom de solution**|Type **RuleTestSol**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
  
4.  Cliquez sur **OK**. Le **RuleTest** projet doit s’afficher dans l’Explorateur de solutions. Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **RuleTest**, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
6.  Parcourir et d’ajouter le **PO.xsd** fichier de schéma que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas. Visual Studio effectue une copie de la **PO.xsd** de fichier et l’ajoute au projet.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **RuleTest**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
8.  Dans le **ajouter un nouvel élément** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **fichiers d’Orchestration**.|  
    |**Modèles**|Cliquez sur **Orchestration BizTalk**.|  
    |**Nom**|Type **RuleTest.odx**.|  
  
9. Cliquez sur **Ajouter**.  
  
10. Avec le bouton droit **déposez une forme à partir de la boîte à outils ici**, pointez sur **insérer une forme**, puis cliquez sur **réception**.  
  
11. Dans la fenêtre Propriétés, remplacez le nom de la **réception** à mettre en forme **ReceivePO**et définissez la valeur de la **activer** propriété `true`.  
  
12. Dans la boîte à outils, sur le **Orchestrations BizTalk** onglet, faites glisser le **appeler règles** forme sur une ligne de connexion sous la **réception** forme.  
  
13. Dans la fenêtre Propriétés, remplacez le nom de la **appeler règles** à mettre en forme **CallProcessPOPolicy**.  
  
14. Avec le bouton ci-dessous le **appeler règles** mettre en forme, pointez sur **insérer une forme**, puis cliquez sur **envoyer**.  
  
15. Dans la fenêtre Propriétés, remplacez le nom de la **envoyer** à mettre en forme **SendPO**. L'orchestration doit présenter l'aspect suivant :  
  
     ![BRE&#45;Walkthrough&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")  
  
### <a name="to-create-message-variables"></a>Pour créer des variables de message  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**. Si vous ne voyez pas la fenêtre Vue Orchestration, cliquez sur le **vue** menu, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**. Normalement, la fenêtre Vue Orchestration correspond à l'onglet situé à côté de celui de la fenêtre Explorateur de solutions. Par défaut, le nouveau message nommé **Message_1**.  
  
     ![BRE&#45;Walkthrough&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")  
  
2.  Dans la fenêtre Vue Orchestration, cliquez sur **Message_1**.  
  
3.  Dans la fenêtre Propriétés, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Identificateur**|Type **POInst**, puis appuyez sur ENTRÉE.|  
    |**Type de message**|Dans la liste déroulante, développez **schémas**, puis sélectionnez **RuleTest.PO**.|  
  
     ![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")  
  
### <a name="to-configure-shapes"></a>Pour configurer des formes  
  
1.  Sélectionnez le **réception** forme dans le Concepteur d’Orchestration.  
  
2.  Dans la fenêtre Propriétés, sélectionnez **POInst** pour le **Message** propriété.  
  
3.  Double-cliquez sur le **appeler règles** forme dans le Concepteur d’Orchestration.  
  
4.  Dans le **configuration de la stratégie appeler règles** boîte de dialogue, sélectionnez **ProcessPurchaseOrder** pour la stratégie.  
  
5.  Cliquez sur Suivant pour **\***ci-dessous **nom de paramètre**, puis sélectionnez **POInst** en tant que paramètre à la stratégie.  
  
     ![BRE&#45;Walkthrough&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")  
  
6.  Cliquez sur **OK**.  
  
7.  Sélectionnez le **envoyer** forme de l’orchestration.  
  
8.  Dans la fenêtre Propriétés, définissez la valeur de la **Type de Message** propriété **POInst**.  
  
### <a name="to-create-ports"></a>Pour créer des ports  
  
1.  Créez deux dossiers, **entrée** et **sortie**, dans le dossier C:\BRE-Walkthroughs\RuleTestSol.  
  
2.  Avec le bouton droit de la surface du port de gauche de l’orchestration, puis cliquez sur **nouveau Port configuré**.  
  
3.  Cliquez sur **Suivant**. Type **ReceivePOPrt** pour le nom du port.  
  
4.  Cliquez sur **suivant** à deux reprises.  
  
5.  Sélectionnez **spécifier maintenant** pour le **liaison de port**.  
  
6.  Spécifiez **fichier** pour le **transport**, puis tapez le nom du répertoire d’entrée en tant que **C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml** en même temps que le masque de fichier (**\*.xml**) pour l’URI.  
  
7.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
8.  Avec le bouton droit de la surface du port de droite de l’orchestration, puis cliquez sur **nouveau Port configuré**.  
  
9. Cliquez sur **Suivant**. Type **SendPOPort** pour le nom du port.  
  
10. Cliquez sur **suivant** à deux reprises.  
  
11. Modifier la **direction de communication du Port** à **toujours envoyer les messages sur ce port**.  
  
12. Sélectionnez **spécifier maintenant** pour le **liaison de port**.  
  
13. Spécifiez **fichier** pour le **transport**, puis tapez le nom du répertoire de sortie en tant que **C:\BRE-Walkthroughs\RuleTestSol\Output**et %MessageID%.xml en tant que le fichier de sortie nom.  
  
14. Cliquez sur **Suivant**, puis sur **Terminer**.  
  
### <a name="to-connect-ports-with-the-shapes"></a>Pour connecter des ports aux formes  
  
1.  Connecter le **ReceivePOPrt** port pour le **ReceivePO** forme. (dans la surface du port, faites glisser la flèche à droite du port ReceivePort vers la boîte de la forme ReceivePO).  
  
     ![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")  
  
2.  Connecter le **SendPO** à mettre en forme le **SendPOPrt** port.  
  
     ![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")  
  
### <a name="to-build-and-deploy-the-solution"></a>Pour créer et déployer la solution  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur le **RuleTest** de projet, puis cliquez sur **propriétés**.  
  
3.  Dans le Concepteur de projet (dans le volet central), cliquez sur **signature**.  
  
4.  Dans l’onglet signature, cochez **signer l’assembly** case à cocher ; Dans la liste déroulante **choisir un fichier de clé de nom fort**, cliquez sur **nouveau**; Dans le **nom de fichier de clé** , entrez Test de la règle ; Dans le **mot de passe** champ (facultatif), définir le mot de passe, puis cliquez sur **OK**.  
  
5.  Dans le Concepteur de projets, cliquez sur **déploiement** pour basculer vers l’onglet déploiement.  
  
6.  Spécifiez **RuleTestApp** comme nom d’application.  
  
     ![BRE&#45;Walkthrough&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur le **RuleTest** de projet, puis cliquez sur **générer**.  
  
9. Cliquez sur le **RuleTest** de projet, puis cliquez sur **déployer**.  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **publier**.  
  
2.  Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
3.  Dans le **Démarrer** menu, ouvrir **Administration de BizTalk Server**. Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.  
  
4.  Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
5.  Avec le bouton droit **RuleTestApp**, puis cliquez sur **configurer**.  
  
6.  Cliquez sur **Orchestration_1**et spécifiez **BizTalkServerApplication** en tant que l’ordinateur hôte.  
  
     ![BRE&#45;Walkthrough&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")  
  
7.  Cliquez sur **OK**.  
  
8.  Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**.  
  
9. Dans le **démarrer l’Application 'RuleTestApp'** boîte de dialogue, cliquez sur **Démarrer**, puis attendez que l’application est démarrée avec succès.  
  
10. Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.  
  
11. Copie le **SamplePO.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.  
  
12. Un fichier de sortie doit s'afficher pour l'orchestration dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
13. Répétez les étapes 11 et 12 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**xyz**).  
  
## <a name="comments"></a>Commentaires  
  
-   Dans cette procédure pas à pas, pour ajouter une forme à l'orchestration, vous n'avez pas utilisé celles de la Boîte à outils. Vous avez en effet cliqué avec le bouton droit de votre souris pour sélectionner la forme à insérer.  
  
-   La configuration de la **appeler règles** forme examine la toute dernière version enregistrée lors de la détermination des types utilisés. Lors de l'exécution, la dernière version déployée sera utilisée.  
  
-   Si vous envisagez d’utiliser une version autre que la dernière version déployée de la stratégie, vous devez utiliser un **Expression** mettre en forme et appeler le moteur de règles par programme pour exécuter la stratégie de cette version. Pour plus d’informations, consultez [comment exécuter les stratégies](../core/how-to-execute-policies.md).  
  
-   Le **appeler règles** forme reconstruit le message, comme si vous utilisez un **construire un Message** forme, ce qui peut entraîner des propriétés de contexte du message soit perdu.  
  
-   Une stratégie ne peut plus être modifiée une fois publiée.  
  
-   Les applications clientes ne peuvent accéder qu'aux stratégies déployées. Si une application cliente appelle une stratégie qui n’est pas déployée, le moteur de règles génère une **RuleEngineDeploymentNotDeployedException** exception. Le message d'erreur détaillé s'affiche dans le journal des événements de l'application.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : création et utilisation d’un vocabulaire dans la stratégie](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour créer un vocabulaire et à son utilisation dans les **ProcessPurchaseOrder** stratégie.  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md)   
 [Agenda et priorité](../core/agenda-and-priority.md)   
 [Appel des règles d’entreprise dans les orchestrations](../core/invoking-business-rules-in-orchestrations.md)
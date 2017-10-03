---
title: "Procédure pas à pas : Test de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53ed915d-0f3a-48ea-bfd5-a1f89b9b689c
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a6f879111a28d5cbf9b2a75c7b3f3b3b865fb38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-testing-the-policy"></a>Procédure pas à pas : Test de la stratégie
Cette procédure pas à pas fournit des procédures pas à pas pour tester la stratégie que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour créer les fichiers de test|Fournit des instructions détaillées pour créer deux exemples XML des fichiers, avec la valeur du champ Quantity 400 (\<= 500) et l’autre avec la valeur du champ Quantity 700 (> 500).|  
|Pour tester la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour le test de la stratégie à l'aide de l'Éditeur des règles d'entreprise.|  
  
### <a name="to-create-the-test-files"></a>Pour créer les fichiers de test  
  
1.  Sur le **Démarrer** menu, ouvrir **bloc-notes**.  
  
2.  Copiez le texte XML suivant dans le Bloc-notes :  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>400</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>    
    ```  
  
3.  Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.  
  
4.  Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.  
  
5.  Accédez au répertoire **C:\BRE-Walkthroughs**.  
  
6.  Type **SamplePO.xml** pour **nom de fichier**, puis cliquez sur **enregistrer**.  
  
7.  Dans le menu **Fichier** , cliquez sur **Nouveau**.  
  
8.  Copiez le texte XML suivant dans le Bloc-notes :  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>700</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>   
    ```  
  
9. Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.  
  
10. Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.  
  
11. Accédez au répertoire **C:\BRE-Walkthroughs**.  
  
12. Type **SamplePO2.xml** pour **nom de fichier**, puis cliquez sur **enregistrer**.  
  
13. Fermez le Bloc-notes.  
  
### <a name="to-test-the-processpurchaseorder-policy"></a>Pour tester la stratégie ProcessPurchaseOrder  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez Éditeur des règles d’entreprise déjà ouvert, appuyez sur F5 pour actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie**.  
  
3.  Dans le **XmlDocument** nœud, sélectionnez **RuleTest.PO**, puis cliquez sur **ajouter une Instance**.  
  
     ![Éditeur des règles d’entreprise &#45; TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")  
  
4.  Sélectionnez le **SamplePO.xml** de fichiers que vous avez créé précédemment, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **Test**.  
  
6.  Consultez les résultats dans la fenêtre Sortie. Pour une explication de cette sortie, reportez-vous à la section ci-après « Analyse des résultats du premier test (samplepo.xml) ».  
  
7.  Ouvrir **SamplePO.xml** dans le bloc-notes et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
8.  Avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie**.  
  
9. Sélectionnez **SamplePO.xml**, cliquez sur **supprimer l’instance**, puis cliquez sur **ajouter une Instance**.  
  
10. Sélectionnez le **SamplePO2.xml** de fichiers que vous avez créé précédemment, puis cliquez sur **ouvrir**.  
  
11. Cliquez sur **Test**. Pour une explication de cette sortie, reportez-vous à la section ci-après « Analyse des résultats du second test (samplepo2.xml) ».  
  
12. Ouvrez le **SamplePO2.xml** dans le bloc-notes et notez que la valeur de la **état** champ est toujours **XYZ**.  
  
## <a name="analysis-of-the-output-from-the-first-test-samplepoxml"></a>Analyse des résultats du premier test (samplepo.xml)  
  
> [!NOTE]
>  Les résultats apparaissent en caractères gras, suivis de l'explication.  
  
 **TRACE du moteur de règles pour le groupe de règles : ProcessPurchaseOrder 8/31/2006 1:33:10 PM**  
  
 La trace du moteur de règles pour l’exécution de la stratégie de **ProcessPurchaseOrder** a démarré à 8/31/2006 1:33:10 PM.  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : Assert**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder**  
  
 **Identificateur de l’Instance de l’objet : 14626574**  
  
 Lorsque vous cliquez sur **Test**, les événements suivants se produisent :  
  
1.  L’éditeur des règles d’entreprise crée un **RuleEngine.Policy** objet, qui à son tour crée une nouvelle instance de moteur de règles ou acquiert une instance du moteur de règles à partir du cache du moteur de règle.  
  
2.  L’éditeur des règles d’entreprise crée un **TypedXmlDocument** objet basé sur le fichier SamplePO.xml.  
  
3.  L’éditeur des règles d’entreprise appelle la **Policy.Execute** méthode avec la **TypedXmlDocument** objet en tant que paramètre.  
  
4.  Le **Policy.Execute** méthode déclare (ajoute) le **TypedXmlDocument** objet en tant que fait dans la mémoire de travail du moteur de règles.  
  
5.  Le moteur de règles utilise le **TypedXmlDocument** en tant que fait l’objet et exécute le **ProcessPurchaseOrder** stratégie.  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : Assert**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder**  
  
 **Identificateur de l’Instance de l’objet : 64530307**  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : Assert**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder/Item**  
  
 **Identificateur de l’Instance de l’objet : 43901854**  
  
1.  Le moteur de règles détermine quels enfant **TypedXmlDocument** pour créer les objets en fonction des sélecteurs XPath définis dans les règles. Lorsque vous créez des règles dans l’éditeur des règles d’entreprise, la valeur du sélecteur XPath par défaut est le nœud situé au-dessus du nœud sélectionné dans le **schémas XML** onglet dans l’Explorateur de faits. La valeur du champ XPath est par défaut définie sur le nœud sélectionné, par rapport à son nœud parent. Toutefois, si le nœud sélectionné possède des nœuds enfants, seule une liaison de sélecteur XPath est créée afin de pointer sur le nœud sélectionné, et aucune liaison de champ XPath n'est créée.  
  
2.  Le tableau suivant montre le sélecteur et XPath Field des valeurs de liaison pour les champs utilisés dans les **ProcessPurchaseOrder** stratégie. (La stratégie ne comporte qu'une seule règle, la règle ApprovalRule.)  
  
|Nom du champ|Sélecteur XPath|Champ XPath|Sélecteur XPath (forme simplifiée)|Champ XPath<br /><br /> (forme simplifiée)|  
|----------------|--------------------|-----------------|----------------------------------------|-----------------------------------------|  
|Quantité|/ * [local-name () = 'PurchaseOrder' et namespace-uri() = 'http://EAISolution.PurchaseOrder'] /\*[local-name () = 'Item' et namespace-uri() ='']|*[local-name()='Quantity' and namespace-uri()='']|/PurchaseOrder/Item|Quantité|  
|État|/*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']|*[local-name()='Status' and namespace-uri()='']|/PurchaseOrder|État|  
  
#### <a name="to-view-the-xpath-selector-and-xpath-field-bindings-for-the-quantity-and-status-fields"></a>Pour afficher les liaisons du sélecteur et du champ Xpath pour les champs Quantity et Status  
  
1.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, puis développez **Version 1.0**.  
  
2.  Cliquez sur **ApprovalRule**.  
  
3.  Dans le volet IF sur la droite, cliquez sur **PO : / PurchaseOrder/Item/Quantity**.  
  
4.  Vérifiez que vous voyez la valeur affichée dans le tableau précédent pour le **sélecteur XPath** et **XPath Field** liaisons dans la fenêtre Propriétés.  
  
5.  Répétez les étapes 3 et 4 pour le **PO : / PurchaseOrder/Status** champ.  
  
 Le moteur de règles crée un enfant **TypedXmlDocument** objet d’origine **TypedXmlDocument** vous avez soumis pour chaque sélecteur XPath. Étant donné que deux sélecteurs XPath distincts sont utilisés dans la stratégie (**/PurchaseOrder/Item** pour le **quantité** champ et **/PurchaseOrder** pour la  **État** champ), le moteur de règles crée deux enfants **TypedXmlDocument** objets et les déclare dans la mémoire de travail du moteur de règles.  
  
> [!NOTE]
>  Pour afficher la trace de sortie à nouveau, cliquez sur **Version 1.0** dans la fenêtre Explorateur de stratégies.  
  
 **TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Expression de test : TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**  
  
 **Valeur de l’opérande gauche : 400**  
  
 **Valeur de l’opérande droite : 500**  
  
 **Résultat de test : True**  
  
 **METTRE À JOUR DE AGENDA 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : ajouter**  
  
 **Nom de règle : ApprovalRule**  
  
 **Critères de résolution de conflit : 0**  
  
 Le moteur de règles utilise un algorithme en trois étapes (évaluation de condition, résolution des conflits, exécution des actions) pour exécuter les stratégies. Dans l'étape d'évaluation de condition, le moteur de règles évalue les conditions dans toutes les règles de la stratégie et ajoute les règles dont les conditions donnent le résultat `true` dans l'agenda. Dans cet exemple simple, la **ProcessPurchaseOrder** stratégie comporte une seule règle, **ApprovalRule**. Par conséquent, le moteur de règles évalue la condition, **quantité < = 500**, dans le **ApprovalRule** à l’aide de la valeur de la **quantité** champ dans le document XML soumis, qui est **400**. Le résultat ci-dessus vous montre les valeurs de l'opérande gauche, de l'opérande droit et le résultat du test.  
  
 Dans la deuxième étape, celle des critères de résolution des conflits, les règles dont les conditions ont pour résultat `true` sont ajoutées à l'agenda dans l'ordre correspondant à leur priorité. Dans ce scénario, le moteur de règles ajoute la **ApprovalRule** à l’agenda, car la condition pour le **ApprovalRule** évalués à `true`. Les critères de résolution de conflits indiquée dans la sortie ci-dessus est uniquement la priorité de la règle (**ApprovalRule**). Si vous cliquez sur le **ApprovalRule** nœud dans la fenêtre de l’Explorateur de stratégies, vous pouvez voir la valeur de la **priorité** propriété sur la règle dans la fenêtre de propriétés en tant que **0**, qui est le valeur par défaut d’une règle. Si votre stratégie comporte plusieurs règles et que vous voulez que les actions de l'une ne soient exécutées qu'après les actions de l'autre, vous devez établir un ordre de priorité en conséquence. Plus le nombre est élevé, plus la priorité est haute.  
  
 **RÈGLE DÉCLENCHÉE 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Nom de règle : ApprovalRule**  
  
 **Critères de résolution de conflit : 0**  
  
 Dans la dernière étape, l'étape d'exécution des actions, le moteur de règles commence à exécuter les actions de la règle. Il existe une action dans le **ApprovalRule**, qui définit la valeur de la **état** champ dans le document XML soumis à **approuvé**.  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : retrait**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder**  
  
 **Identificateur de l’Instance de l’objet : 14626574**  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : retrait**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder/Item**  
  
 **Identificateur de l’Instance de l’objet : 43901854**  
  
 **ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**  
  
 **Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Opération : retrait**  
  
 **Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder**  
  
 **Identificateur d’Instance objet :** 64530307  
  
 Tous les faits soumis (**PurchaseOrder**) à la règle de moteur et les faits enfants créés par le moteur de règles en fonction des sélecteurs XPath (**\PurchaseOrder** et **\PurchaseOrder\Item**) sont retirés (supprimés) à partir de la mémoire de travail du moteur de règles.  
  
## <a name="analysis-of-the-output-from-the-second-test-samplepo2xml"></a>Analyse des résultats du second test (samplepo2.xml)  
 **TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 9/5/2006 5:24:42 PM**  
  
 **Identificateur de l’Instance du moteur de règles : b749d2fd-a883-4c2f-9974-5cf688010622**  
  
 **Nom du groupe de règles : ProcessPurchaseOrder**  
  
 **Expression de test : TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**  
  
 **Valeur de l’opérande gauche : 700**  
  
 **Valeur de l’opérande droite : 500**  
  
 **Résultat de test :** False  
  
 Le moteur de règles évalue la condition (**quantité < = 500**) dans le **ApprovalRule** à l’aide de la commande isolés **élément** objet. Vous pouvez voir que valeur de l’opérande gauche est la valeur de la **quantité** élément dans le document XML, **700**. Le résultat de test est `false` car **700 < = 500**, de sorte que la règle n’est pas ajoutée à l’agenda du moteur de règles. L'agenda ne comporte aucune règle. Par conséquent, il y a aucune action à exécuter et la valeur de la **état** champ reste **XYZ**.  
  
## <a name="comments"></a>Commentaires  
  
-   Il est recommandé de tester les stratégies avant de les appliquer dans les applications clientes, telles que les applications BizTalk.  
  
-   Lorsque vous testez une stratégie qui utilise les faits de base de données avec le **DataConnection** de liaison dans l’éditeur des règles d’entreprise, un **DataConnection** objet est automatiquement créé pour vous. Toutefois, lorsque vous appelez la même stratégie à partir d’une orchestration à l’aide de la **appeler règles** mettre en forme, non **DataConnection** objet est passé automatiquement à la stratégie. Vous devez créer un **DataConnection** de l’objet dans l’orchestration et passez-le en tant que paramètre ou créez un extracteur de faits qui déclare le **DataConnection** de l’objet, puis configurez la stratégie à utiliser l’extracteur de faits.  
  
-   Pour tester une stratégie qui utilise un fait .NET, vous devez créer un composant créateur de faits et spécifiez dans le **sélectionner des faits** boîte de dialogue. Pour plus d’informations sur la création de créateurs de faits, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md). Vous pouvez effectuer la même chose lorsque la stratégie utilise les faits de base de données (**TypedDataConnection** ou **TypedDataTable** ou **TypedDataRow**) ou des faits XML ( **TypedXmlDocument**).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : appel de la stratégie à partir d’une Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour l’appel de la **ProcessPurchaseOrder**  stratégie à partir d’une orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Sortie de Trace de Test de stratégie](../core/policy-test-trace-output.md)   
 [Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md)   
 [Agenda et priorité](../core/agenda-and-priority.md)
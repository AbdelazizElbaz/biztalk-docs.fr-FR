---
title: "Procédure pas à pas : Création d’une stratégie commerciale Simple | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02d35735-dce2-4ee2-965e-dae307a125b0
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1eb4f21cf9311399ef6092b95fa818547679a240
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-creating-a-simple-business-policy"></a>Procédure pas à pas : Création d’une stratégie commerciale Simple
Cette procédure pas à pas fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour créer une stratégie commerciale simple intitulée **ProcessPurchaseOrder** contenant une règle nommée **ApprovedRule**. Le **ApprovedRule** règle attend l’utilisateur d’envoyer un document XML en tant que fait et définit la valeur de la **état** champ dans le document à **approuvé** si la valeur de la  **Quantité** champ est inférieure ou égale à **500**.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez connaître les bases de l'infrastructure des règles d'entreprise pour effectuer cette procédure. Si vous ne connaissez pas l’infrastructure des règles d’entreprise, nous vous recommandons de lire la présentation de l’architecture de l’infrastructure de règles d’entreprise à [moteur des règles d’entreprise](../core/business-rules-engine.md) avant d’effectuer cette procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour créer le fichier du schéma de bon de commande|Fournit des instructions détaillées pour la création du schéma pour le document qui le **ProcessPurchaseOrder** stratégie utilise.|  
|Pour créer la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour la création de la **ProcessPurchaseOrder** stratégie à l’aide de l’éditeur des règles d’entreprise.|  
  
### <a name="to-create-the-po-schema-file"></a>Pour créer le fichier du schéma de bon de commande  
  
1.  Sur le **Démarrer** menu, ouvrir **bloc-notes**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Fichier**.  
  
3.  Copiez le texte XML suivant dans l'éditeur :  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://EAISolution.PurchaseOrder" targetNamespace="http://EAISolution.PurchaseOrder" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="PurchaseOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="Header">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="ReqID" type="xs:string" />  
                  <xs:element name="Date" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Item">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Description" type="xs:string" />  
                  <xs:element name="Quantity" type="xs:int" />  
                  <xs:element name="UnitPrice" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Status" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
4.  Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.  
  
5.  Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.  
  
6.  Type **PO.xsd** dans les **nom de fichier** texte, changez le répertoire à **C:\BRE-Walkthroughs**, modifiez la valeur de **codage** à  **Unicode** puis cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Créer le répertoire **BRE-Walkthroughs** sous **C:\\**  s’il n’existe pas, puis cliquez sur **enregistrer**.  
  
7.  Fermez le Bloc-notes.  
  
### <a name="to-create-the-processpurchaseorder-business-policy"></a>Pour créer la stratégie d’entreprise ProcessPurchaseOrder  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
    > [!NOTE]
    >  L’éditeur des règles d’entreprise affiche la **ouvrir le magasin de règles** boîte de dialogue lorsqu’il est ouvert pour la première fois sur un ordinateur. Si vous voyez le **ouvrir le magasin de règles** boîte de dialogue, cliquez sur **OK** après avoir vérifié le nom du serveur SQL et le nom de la base de données.  
  
2.  Dans la fenêtre Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.  
  
3.  Modifier le nom de la stratégie, **Policy1**à **ProcessPurchaseOrder** et appuyez sur ENTRÉE. Vous pouvez également modifier le nom de la stratégie dans le **propriétés** fenêtre.  
  
4.  Avec le bouton droit **Version 1.0**, puis cliquez sur **AddNewRule**.  
  
5.  Modifier le nom de la règle **Rule1** à **ApprovalRule** et appuyez sur entrée**.** Vous pouvez également modifier le nom de la règle dans le **propriétés** fenêtre.  
  
6.  Dans la fenêtre Explorateur de faits, cliquez sur le **schémas XML** onglet.  
  
7.  Avec le bouton droit **schémas**, cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** fichier que vous avez créé précédemment.  
  
8.  Dans la fenêtre Propriétés, modifiez la valeur de la **Type de Document** propriété à partir de **PO** à **RuleTest.PO**.  
  
    > [!NOTE]
    >  Vous allez créer un projet BizTalk nommé **RuleTest** plus loin dans le [procédure pas à pas : appel de la stratégie à partir d’une Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) procédure pas à pas. Dans ce guide, vous allez ajouter le **PO.xsd** de fichiers au projet, créez une orchestration qui appelle le **ProcessPurchaseOrder** stratégie, puis testez la stratégie. Pour tester la stratégie à partir de l’orchestration, vous devez vous assurer que vous modifiez le **Type de Document** propriété  **\<nom du projet\>.\< SchemaName\>**, qui est **RuleTest.PO** dans ce cas.  
  
     ![BRE &#45; Procédure pas à pas &#45; ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")  
  
9. Dans la fenêtre Explorateur de faits, développez **PurchaseOrder**, puis développez **élément**.  
  
10. Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **LessThanEqual**.  
  
     ![Éditeur des règles d’entreprise &#45; Inférieur ou égal](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")  
  
11. Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.  
  
     ![Éditeur des règles d’entreprise &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")  
  
     ![Éditeur des règles d’entreprise &#45; UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")  
  
12. Dans le volet IF, cliquez sur **argument2**, type `500`, puis appuyez sur ENTRÉE.  
  
13. Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits pour le volet THEN en bas à droite de l’éditeur des règles d’entreprise.  
  
     ![Éditeur des règles d’entreprise &#45; DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")  
  
14. Dans le volet THEN, cliquez sur  **\<entrer une valeur\>**  , puis tapez **approuvé**.  
  
15. Dans la fenêtre Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
## <a name="comments"></a>Commentaires  
  
-   Une stratégie peut comporter une ou plusieurs règles d'entreprise. Vous allez ajouter une autre règle, **DeniedRule**, dans le [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas.  
  
-   Vous pouvez modifier la stratégie afin d'ajouter d'autres règles, modifier les conditions et changer les actions lorsque l'état de la stratégie est Enregistré.  
  
-   Vous pouvez classer par priorité d’exécution des règles en spécifiant le **priorité** propriété des règles dans l’éditeur des règles d’entreprise. Par exemple, si vous cliquez sur le **ApprovedRule** nœud dans la fenêtre de l’Explorateur de stratégies, vous pouvez voir les **priorité** propriété dans la fenêtre Propriétés. Plus le nombre est élevé, plus la priorité de la règle l'est également.  
  
-   Vous avez la possibilité d'utiliser un schéma XML, une base de données ou un assembly .NET comme source de données de la stratégie. Dans cette procédure, vous avez utilisé un schéma XML comme source de données. Vous devez envoyer une instance du document XML du schéma en tant que fait au moteur de règles pour que la stratégie soit exécutée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour tester le **ProcessPurchaseOrder** stratégie vous créé dans cette procédure pas à pas.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des règles d’entreprise](../core/about-business-rules.md)
---
title: "Étape 2 : Créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75d34c48-0f2a-42e4-a60b-e04bcf2404e1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bd1eaac434f4fc6bda55f6ab290740147d91997
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-an-application-definition-file-for-siebel-business-component-operations"></a>Étape 2 : Créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** le catalogue de données métiers expose et incorpore des données à partir d’applications de métier (LOB) dans des portails. Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.  
  
 L’outil Business Data Catalog Definition Editor vous permet de vous permet de créer un fichier de définition d’application pour le catalogue de données métiers. Cet outil génère automatiquement le code XML pour le fichier de définition. Par conséquent, vous n’avez pas à créer manuellement le fichier dans un document XML éditeur.  
  
 L’objectif de l’application Microsoft Office SharePoint Server que vous créez est d’effectuer une opération de requête sur le composant de gestion de compte pour récupérer une liste d’enregistrements. Pour ce faire, vous devez effectuer un ensemble de tâches dans Business Data Catalog Definition Editor. Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer de l’éditeur de définition de catalogue de données métier installé avec le SDK de Microsoft Office SharePoint Server 2007. Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).  
  
-   Doit avoir publié le service WCF, comme décrit dans [étape 1 : publier les opérations de composant d’entreprise Siebel comme Service WCF](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).  
  
## <a name="creating-an-application-definition-file"></a>Création d’un fichier de définition d’Application  
 Cette section fournit des instructions pas à pas pour créer un fichier de définition d’application pour le service WCF.  
  
### <a name="connect-to-the-wcf-service-and-create-entities"></a>Se connecter au Service WCF et créer des entités  
 Vous devez vous connecter au service WCF pour extraire la Description langage WSDL (Web Services) pour le service. À partir de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes. Ces méthodes peuvent être utilisées pour créer des entités. Pour cet exemple, vous devez créer une entité de l’opération de requête sur le composant de gestion de compte.  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>Pour vous connecter au service WCF et créer des entités  
  
1.  Démarrez l’éditeur de définition de catalogue de données métier. Sur le **Démarrer** menu, cliquez sur **Microsoft Business Data Catalog Definition Editor**.  
  
2.  Dans l’outil, cliquez sur **ajouter un système LOB**.  
  
3.  Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.  
  
4.  Dans la zone URL, tapez l’URL pour le service WCF. L’URL doit être au format suivant :  
  
    ```  
    https://<computer_name>/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
    ```  
  
     WHERE, BusinessObjects_Account_Account_Operation.svc est le fichier de service pour le contrat Siebel.  
  
     L’URL que vous devez taper est disponible lorsque vous testez si le service WCF est publié avec succès, comme décrit dans [étape 1 : publier les opérations de composant d’entreprise Siebel comme Service WCF](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).  
  
5.  Cliquez sur **Se connecter**.  
  
6.  Cliquez sur le **ajouter une méthode Web** onglet pour consulter les opérations que vous avez sélectionné dans l’Assistant développement d’adaptateurs WCF. Vous verrez la **requête** (méthode).  
  
     ![Ajouter des méthodes web à l’application BDC](../../adapters-and-accelerators/adapter-siebel/media/f9505cd3-67e3-4f99-b189-d010322a3137.gif "f9505cd3-67e3-4f99-b189-d010322a3137")  
  
7.  Faites glisser le **requête** méthode l’aire de conception, puis cliquez sur **OK**.  
  
8.  Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte. Dans cet exemple, tapez `Siebel_Account`, puis cliquez sur **OK**. Une entité, **Entity0**, est créé dans Business Data Catalog Definition Editor.  
  
    > [!IMPORTANT]
    >  L’outil Business Data Catalog Definition Editor ne gère pas les types de données énumérés. Par conséquent, l’outil Business Data Catalog Definition Editor importe les champs jusqu'à ce qu’il rencontre un type de données énumérés et ignore les champs restants. L’outil Business Data Catalog Definition Editor fournit également une erreur. Vous pouvez ignorer cette erreur et continuer en cliquant sur OK. Vous pouvez ajouter manuellement les champs requis dans le fichier de définition d’application à un stade ultérieur.  
  
9. Modifier les noms d’entité d’utiliser des noms plus conviviaux. Pour cet exemple, remplacez **Entity0** à **compte**.  
  
    1.  Développez le **Siebel_Account** nœud, puis développez le **entités** nœud.  
  
    2.  Sélectionnez le **Entity0** nœud.  
  
    3.  Dans le volet Propriétés, tapez **compte** dans les **nom** champ.  
  
         ![Renommer l’entité](../../adapters-and-accelerators/adapter-siebel/media/44eda1de-b348-4421-9c51-0355b51f4a90.gif "44eda1de-b348-4421-9c51-0355b51f4a90")  
  
### <a name="specify-user-name-and-password-headers-for-methods"></a>Spécifiez le nom d’utilisateur et les en-têtes de mot de passe pour les méthodes  
 Lorsque vous créez un service WCF pour les opérations de composant d’entreprise sélectionnée dans le système Siebel, vous avez spécifié les en-têtes nom et mot de passe utilisateur en tant que partie de la configuration de comportement de point de terminaison ([étape 1 : publier les opérations de composant d’entreprise Siebel comme un Service WCF](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)). Vous devez spécifier les mêmes valeurs pour les propriétés de la méthode.  
  
##### <a name="to-specify-user-name-and-password-headers-for-the-query-method"></a>Pour spécifier les en-têtes de nom et mot de passe utilisateur pour la méthode de requête  
  
1.  Dans le volet objets de métadonnées, développez le **compte** nœud, puis développez le **méthodes** nœud.  
  
2.  Cliquez sur le **requête** nœud, dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** champ.  
  
3.  Dans la boîte de dialogue Éditeur de collections PropertyView, cliquez sur **ajouter**, puis, dans le volet Propriétés, tapez `HttpHeaderUserName` pour le **nom** champ. De même, tapez `MyUserHeader` pour le **PropertyValue** champ. Sélectionnez **System.String** pour le **Type** champ.  
  
     ![Ajouter une propriété](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")  
  
4.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**, puis, dans le volet Propriétés, tapez `HttpHeaderPassword` pour le **nom** champ. De même, tapez `MyPassHeader` pour le **PropertyValue** champ. Sélectionnez **System.String** pour le **Type** champ.  
  
5.  Cliquez sur **OK**.  
  
### <a name="set-up-single-sign-on-for-connecting-to-a-siebel-system"></a>Valeur de l’authentification unique pour la connexion à un système Siebel  
 Une fois que vous avez terminé d’exécuter toutes les procédures dans cette rubrique, vous avez créé une définition d’application XML qui peut être importé dans une application SharePoint. À partir de l’application, vous appellerez les opérations de composant d’entreprise Siebel (exposées en tant que méthodes Web) pour récupérer les données pertinentes à partir du système Siebel. Pour ce faire, vous devez créer un mappage entre un utilisateur dans le système Siebel et de l’utilisateur dans l’application SharePoint. Vous créez ce mappage dans le site Web Administration centrale de SharePoint après avoir importé la définition d’application XML.  
  
 Toutefois, pour créer le mappage, vous devez définir une propriété **SecondarySsoApplicationId** dans Business Data Catalog Definition Editor.  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a>Pour définir la propriété SecondarySsoApplicationId  
  
1.  Dans le volet objets de métadonnées, développez le **Siebel_Account** nœud, puis développez le **Instances** nœud.  
  
2.  Cliquez sur **Siebel_Account_Instance** dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** champ.  
  
3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**, puis, dans le volet Propriétés, tapez **SecondarySsoApplicationId** pour le **nom** champ. De même, tapez **SiebelSSO** pour le **PropertyValue** champ. Sélectionnez **System.String** pour le **Type** champ.  
  
     ![Ajouter la propriété SSO](../../adapters-and-accelerators/adapter-siebel/media/59ce70eb-498f-406b-965d-c273c2d6ed14.gif "59ce70eb-498f-406b-965d-c273c2d6ed14")  
  
4.  Cliquez sur **OK**.  
  
### <a name="requirement-perform-a-query-operation-on-the-account-business-component"></a>Condition : Effectuer une opération de requête sur le composant de gestion de compte  
 La première exigence de cet exemple consiste à créer une définition d’application qui peut être utilisée pour effectuer une opération de requête sur le composant de gestion de compte. Pour cela, vous devez effectuer l’ensemble suivant de tâches :  
  
-   Dans la méthode de requête, créer un filtre et le mapper au paramètre sur lequel l’opération de requête est effectuée. Pour le composant de gestion de compte, vous allez effectuer une requête à l’aide de la **SearchExpr** paramètre. Par conséquent, vous allez mapper le filtre à la **SearchExpr** paramètre.  
  
-   Créez une instance de méthode Finder pour la méthode de requête. Une méthode de recherche récupère une liste d’enregistrements en fonction d’un filtre.  
  
##### <a name="to-create-a-filter-and-map-it-to-the-searchexpr-parameter"></a>Pour créer un filtre et la mapper au paramètre SearchExpr  
  
1.  Créer un filtre pour la méthode de requête.  
  
    1.  Dans le volet objets de métadonnées, développez le **compte** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez la méthode de requête, cliquez sur **filtres**, puis cliquez sur **ajouter un filtre**.  
  
         ![Ajouter un filtre à une méthode](../../adapters-and-accelerators/adapter-siebel/media/9cf7ccfd-6da0-44b7-b522-df327a74e7a2.gif "9cf7ccfd-6da0-44b7-b522-df327a74e7a2")  
  
    3.  Dans le volet Propriétés, tapez `SearchExpression` pour le **nom** champ.  
  
    4.  Pour le **FilterType** propriété, sélectionnez **est égal à**.  
  
         ![Spécifiez un nom de filtre et un type](../../adapters-and-accelerators/adapter-siebel/media/9faa18e1-4d27-4ee4-960a-458f978812a7.gif "9faa18e1-4d27-4ee4-960a-458f978812a7")  
  
2.  Mapper le filtre à la **SearchExpr** paramètre dans la méthode de requête.  
  
    1.  Dans le volet objets de métadonnées, développez le **compte** nœud, puis développez le **méthodes** nœud.  
  
    2.  La méthode de requête, puis le **paramètres** nœud.  
  
    3.  Développez le **AccountQueryInputRecord** nœud, puis développez la seconde **AccountQueryInputRecord** nœud.  
  
    4.  Cliquez sur le **SearchExpr** nœud dans le volet Propriétés, sélectionnez **SearchExpression** à partir de la **FilterDescriptor**liste.  
  
         ![Mapper un paramètre à un filtre](../../adapters-and-accelerators/adapter-siebel/media/199c8ba7-d0e8-4fb4-9d73-9cf548512498.gif "199c8ba7-d0e8-4fb4-9d73-9cf548512498")  
  
        > [!IMPORTANT]
        >  Le **AccountQueryInputRecord** contient également un **ChampsRequête** nœud, qui à son tour contient un **élément** nœud. Vous devez supprimer la **élément** nœud, sinon l’opération de requête sur le composant de gestion de compte peuvent ne pas donne les résultats souhaités. Pour supprimer la **élément** nœud, cliquez sur le nœud et sélectionnez **supprimer**.  
  
##### <a name="to-create-a-finder-method-instance-for-query-method"></a>Pour créer une instance de méthode Finder pour la méthode de requête  
  
1.  Dans le volet objets de métadonnées, développez le **compte** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **requête** nœud, avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajouter une instance de méthode Finder](../../adapters-and-accelerators/adapter-siebel/media/c90e7784-4fb7-4eb5-baf5-efbefba4bb1f.gif "c90e7784-4fb7-4eb5-baf5-efbefba4bb1f")  
  
3.  Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour le **Type d’Instance de méthode**.  
  
4.  Cliquez sur **retourner** de **TypeDescriptor de retour** section.  
  
     ![Ajouter une instance de méthode Finder](../../adapters-and-accelerators/adapter-siebel/media/e8343988-d7c1-4b04-85b0-ca7d07097490.gif "e8343988-d7c1-4b04-85b0-ca7d07097490")  
  
5.  Cliquez sur **OK**.  
  
6.  Dans le volet Propriétés, tapez `QueryAccount` pour le **nom** champ.  
  
     ![Spécifiez un nom pour l’instance de méthode](../../adapters-and-accelerators/adapter-siebel/media/401223f3-806f-4010-8646-d5ac0c0e9f67.gif "401223f3-806f-4010-8646-d5ac0c0e9f67")  
  
### <a name="remove-the-parameters-of-systemnullable-type"></a>Supprimez les paramètres de Type de System.Nullable  
 Les paramètres de retournés de fonction de requête peuvent contenir des paramètres de type de System.Nullable. En raison de la présence de ces paramètres dans la définition d’application, vous pouvez obtenir une erreur lors de la présentation des données Siebel sur un portail SharePoint. Par conséquent, vous devez supprimer les paramètres du type de System.Nullable à partir de la définition d’application.  
  
 En outre, pour chaque paramètre de type de System.Nullable, l’éditeur de définition de catalogue de données métier crée un autre paramètre de type de System.Boolean et ajoute « Specified » au nom du paramètre. Par exemple, le paramètre AccountRole est de type de System.Nullable. Par conséquent, l’éditeur de définition de catalogue de données métier ajoute un paramètre AccountRoleSpecified à la liste de paramètres. Vous devez supprimer ces paramètres.  
  
> [!NOTE]
>  Vous pouvez voir le paramètre de type en sélectionnant le paramètre dans Business Data Catalog Definition Editor et en examinant la valeur de la **TypeName** propriété dans le volet Propriétés.  
  
> [!NOTE]
>  Vous pouvez ignorer cette étape si l’application ne contient pas tous les paramètres de type de System.Nullable.  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type-for-the-query-method"></a>Pour supprimer les paramètres de type System.Nullable pour la méthode de requête  
  
1.  Dans le volet objets de métadonnées, développez le **compte** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **requête** nœud, puis développez le **paramètres** nœud.  
  
3.  Développez le **retourner** nœud, puis développez la seconde **retourner** nœud.  
  
4.  Cliquez sur le paramètre que vous souhaitez supprimer, puis sélectionnez **supprimer**.  
  
5.  Dans la boîte de dialogue, cliquez sur **OK**.  
  
### <a name="export-the-application-definition-to-a-file"></a>Exporter la définition d’Application dans un fichier  
 Vous venez de créer une définition d’application qui contient les métadonnées de l’instance du système Siebel. Vous devez exporter cette définition dans un fichier XML, qui peut être importé dans Microsoft Office SharePoint Server.  
  
##### <a name="to-export-the-application-definition-to-a-file"></a>Pour exporter la définition d’application dans un fichier  
  
1.  Cliquez sur le **Siebel_Account** nœud dans le volet objets de métadonnées, puis cliquez sur **exporter**.  
  
2.  Enregistrez le fichier sous Siebel_Account.xml.  
  
### <a name="modify-the-application-definition-file-to-include-specific-parameters"></a>Modifier le fichier de définition d’Application pour inclure des paramètres spécifiques  
 Comme mentionné plus haut dans cette rubrique, l’outil Business Data Catalog Definition Editor ne gère pas les types de données énumérés. L’outil Business Data Catalog Definition Editor importe les champs jusqu'à ce qu’il rencontre un type de données énumérés et ignore les champs restants. Par conséquent, certains champs que vous souhaitez dans votre application peuvent être omis. Vous pouvez modifier manuellement le fichier de définition d’application pour inclure ces champs.  
  
> [!NOTE]
>  Vous devez vous assurer que les paramètres que vous ajoutez sont présents dans le fichier .cs généré par l’Assistant de développement de services de l’adaptateur WCF dans [étape 1 : publier les opérations de composant d’entreprise Siebel comme Service WCF](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).  
  
 Dans ce fichier de définition d’application, vous ajouter ou supprimer des paramètres de retournés pour la **QueryAccount** (méthode).  
  
##### <a name="to-modify-the-application-definition-file"></a>Pour modifier le fichier de définition d’application  
  
1.  Ouvrez le fichier de définition d’application, Siebel_Account.xml, à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou un autre éditeur.  
  
2.  Modifier le fichier de définition d’application pour remplacer les paramètres pour le **QueryAccount** (méthode).  
  
    1.  Dans le fichier de définition d’application, recherchez les éléments suivants :  
  
        ```  
        <TypeDescriptor TypeName="BDC.AccountQueryRecord,Siebel_Account" Name="Item">  
        ```  
  
    2.  Dans le `<TypeDescriptors>` de balise, remplacer la `<TypeDescriptor>` éléments avec les éléments suivants :  
  
        ```  
  
        <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Id" />  
        <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Country" />  
        <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Name" />  
        <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Location" />  
        ```  
  
    3.  Enregistrez et fermez le fichier.  
  
    > [!TIP]
    >  Vous pouvez importer le fichier de définition d’application mis à jour dans l’outil Business Data Catalog Definition Editor pour afficher les champs qui vient d’être ajoutés. Toutefois, avant l’importation, vous devrez supprimer l’application « Siebel_Account » existante à partir de l’outil Éditeur de définition de catalogue de données métier.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous devez maintenant créer une application SharePoint pour récupérer des données à partir d’un système Siebel. Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) pour obtenir des instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)
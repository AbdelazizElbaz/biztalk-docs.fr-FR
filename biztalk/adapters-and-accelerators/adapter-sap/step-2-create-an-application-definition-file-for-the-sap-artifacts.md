---
title: "Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application definition file, creating a
- Business Data Catalog Definition Editor
- Business Data Catalog
ms.assetid: d254b00e-dbeb-4167-ad57-6f0aa2e7a563
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d334b885b1135fb429655200090671a2a750ec0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-an-application-definition-file-for-the-sap-artifacts"></a>Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** la fonctionnalité de catalogue de données métiers dans Microsoft SharePoint Server expose et incorpore des données à partir d’applications de métier (LOB) dans des portails. Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.  
  
 L’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, vous permet de créer un fichier de définition d’application pour le catalogue de données métiers. Cet outil génère automatiquement un fichier XML pour le fichier de définition, vous n’avez pas besoin de créer manuellement le fichier dans un document XML éditeur.  
  
 L’objectif de l’application Microsoft Office SharePoint Server que vous créez est de :  
  
-   Rechercher un client dans le système SAP basé sur un nom de client.  
  
-   Sélectionnez un client dans la liste des clients d’extraction et de récupérer les détails pour le client.  
  
-   Sélectionnez un client dans la liste des clients d’extraction et de récupérer les commandes client pour le client.  
  
 Pour chacune de ces exigences, vous devez effectuer un ensemble de tâches dans l’outil Éditeur de définition de catalogue de données métier. Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Assurez-vous que vous disposez de l’éditeur de définition de catalogue de données métier installé avec le SDK de Microsoft Office SharePoint Server 2007. Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).  
  
-   Publier le service WCF, comme décrit dans [étape 1 : publier les artefacts SAP comme un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).  
  
## <a name="creating-an-application-definition-file"></a>Création d’un fichier de définition d’Application  
 Cette rubrique fournit des instructions pas à pas pour créer un fichier de définition d’application pour le service WCF.  
  
### <a name="connect-to-the-wcf-lob-service-and-create-entities"></a>Se connecter au Service WCF LOB et créer des entités  
 Vous devez vous connecter au service WCF pour extraire la Description langage WSDL (Web Services) pour le service. À partir de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes. Ces méthodes peuvent être utilisées pour créer des entités. Pour cet exemple, deux entités sont créées, chacune pour les client et les commandes client.  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>Pour vous connecter au service WCF et de créer des entités  
  
1.  Démarrez l’éditeur de définition de catalogue de données métier. Sur le **Démarrer** menu, cliquez sur **Microsoft Business Data Catalog Definition Editor**.  
  
2.  Dans la barre d’outils, cliquez sur **ajouter un système LOB**.  
  
3.  Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.  
  
4.  Dans le **URL** zone, tapez l’URL pour le service WCF. L’URL doit être au format suivant :  
  
    ```  
    https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
    ```  
  
     où Rfc.svc est le fichier créé pour le contrat de Rfc.  
  
     L’URL est disponible lorsque vous testez si le service WCF est publié avec succès, comme décrit dans la rubrique [étape 1 : publier les artefacts SAP comme un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).  
  
5.  Cliquez sur **Se connecter**.  
  
6.  Pour afficher les opérations que vous avez sélectionné dans l’Assistant développement d’adaptateurs WCF, cliquez sur le **ajouter une méthode Web** onglet. Vous verrez les méthodes suivantes :  
  
    -   SD_RFC_CUSTOMER_GET  
  
    -   BAPI_SALESORDER_GETLIST  
  
         ![Ajouter des méthodes web à l’application BDC](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")  
  
     Faites glisser les méthodes à l’aire de conception. Assurez-vous que vous faites glisser les deux opérations pour les différentes entités.  
  
     ![Créer des entités pour les méthodes web](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte. Pour cet exemple, appeler **Customer_Order**, puis cliquez sur **OK**.  
  
9. Dans l’entreprise Data Catalog Definition Editor, les deux entités sont répertoriées comme **Entity0** et **Entity1**. Donnez des noms conviviaux ces entités. Renommer l’entité pour SD_RFC_CUSTOMER_GET à **client**et renommer l’entité pour BAPI_SALESORDER_GETLIST à **SalesOrder**. Procédez comme suit pour renommer les entités :  
  
    1.  Développez le **Customer_Order** nœud, puis développez le **entités** nœud.  
  
    2.  Sélectionnez le **Entity0** nœud.  
  
    3.  Dans le volet Propriétés, tapez **client** dans les **nom** boîte.  
  
         ![Renommer l’entité](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")  
  
    4.  Sélectionnez le **Entity1** nœud.  
  
    5.  Dans le volet Propriétés, tapez **SalesOrder** dans les **nom** boîte.  
  
### <a name="specify-user-name-and-password-headers-for-the-methods"></a>Spécifiez le nom d’utilisateur et les en-têtes de mot de passe pour les méthodes  
 Lorsque vous créez un service WCF pour les documents RFC sélectionnés dans le système SAP, vous avez spécifié les en-têtes nom et mot de passe utilisateur en tant que partie de la configuration de comportement de point de terminaison. Consultez [étape 1 : publier les artefacts SAP sous la forme d’un Service WCF](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md). Vous devez spécifier les mêmes valeurs pour les propriétés de la méthode.  
  
##### <a name="to-specify-user-name-and-password-headers"></a>Pour spécifier les en-têtes de nom et mot de passe utilisateur  
  
1.  Ajoutez les en-têtes de nom et mot de passe utilisateur pour la méthode SD_RFC_CUSTOMER_GET.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
    2.  Cliquez sur le nœud SD_RFC_CUSTOMER_GET et dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** boîte.  
  
    3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte. De même, tapez **MyUserHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
         ![Ajouter une propriété](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")  
  
    4.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte. De même, tapez **MyPassHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
    5.  Cliquez sur **OK**.  
  
2.  Ajoutez les en-têtes de nom et mot de passe utilisateur pour la méthode BAPI_SALESORDER_GETLIST.  
  
    1.  Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.  
  
    2.  Cliquez sur le nœud BAPI_SALESORDER_GETLIST et dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **propriétés** boîte.  
  
    3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte. De même, tapez **MyUserHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
    4.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte. De même, tapez **MyPassHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
    5.  Cliquez sur **OK**.  
  
### <a name="set-up-single-sign-on-for-connecting-to-the-sap-system"></a>Valeur de l’authentification unique pour la connexion au système SAP  
 Une fois que vous avez terminé d’exécuter toutes les procédures dans cette rubrique, vous avez créé un fichier de définition d’application qui peut être importé dans une application SharePoint. À partir de l’application, vous appelez les méthodes SAP pour récupérer les données pertinentes à partir du système SAP. Pour ce faire, vous devez créer un mappage entre un utilisateur dans le système SAP et de l’utilisateur dans l’application SharePoint. Vous créez ce mappage dans la console d’Administration centrale de SharePoint après avoir importé le fichier de définition d’application.  
  
 Toutefois, pour créer le mappage, vous devez définir une propriété **SecondarySsoApplicationId** dans Business Data Catalog Definition Editor.  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a>Pour définir la propriété SecondarySsoApplicationId  
  
1.  Dans le volet objets de métadonnées, développez le **Customer_Order** nœud, puis développez le **Instances** nœud.  
  
2.  Cliquez sur **Customer_Order_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.  
  
3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** pour le **nom** boîte. De même, tapez **SAPSSO** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
     ![Ajouter la propriété SSO](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")  
  
4.  Cliquez sur **OK**.  
  
### <a name="requirement-1-search-for-customers-based-on-customer-name"></a>Condition 1 : Recherche pour les clients basés sur le nom du client  
 Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des clients basés sur le nom du client, vous devez effectuer l’ensemble suivant de tâches.  
  
-   Dans la méthode SD_RFC_CUSTOMER_GET, créer un filtre et le mapper au paramètre qui stocke le nom du client.  
  
-   Créer un **recherche** instance de méthode pour la méthode SD_RFC_CUSTOMER_GET. A **recherche** méthode récupère une liste d’enregistrements en fonction d’un filtre.  
  
##### <a name="to-create-a-filter-and-map-it-to-the-customer-name-parameter"></a>Pour créer un filtre et la mapper au paramètre de nom de client  
  
1.  Créer un filtre.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez la méthode SD_RFC_CUSTOMER_GET, avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.  
  
         ![Ajouter un filtre à une méthode](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")  
  
    3.  Dans le volet Propriétés, tapez **CustomerName** dans les **nom** boîte.  
  
         ![Spécifiez un nom pour le filtre](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")  
  
    4.  Pour le **FilterType** propriété, sélectionnez **WildcardFilter**.  
  
2.  Mapper le filtre à la **nom1** paramètre dans la méthode SD_RFC_CUSTOMER_GET.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
    2.  La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.  
  
    3.  Développez le **nom1** nœud, puis cliquez sur le deuxième **nom1** nœud. Le **nom1** paramètre contient le nom du client.  
  
    4.  Dans le volet Propriétés, sélectionnez **CustomerName** à partir de la **FilterDescriptor** liste.  
  
         ![Mapper le filtre à un paramètre de méthode](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")  
  
##### <a name="to-create-a-finder-method-instance-for-the-sdrfccustomerget-method"></a>Pour créer une instance de méthode Finder pour la méthode SD_RFC_CUSTOMER_GET  
  
1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **SD_RFC_CUSTOMER_GET** nœud, avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")  
  
3.  Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**. Sélectionnez **CUSTOMER_T** pour **TypeDescriptor de retour**.  
  
     ![Ajouter une instance de méthode Finder](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **GetCustomerByName_Instance** dans les **nom** boîte.  
  
     ![Spécifiez un nom pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")  
  
### <a name="requirement-2-retrieve-details-for-a-specific-customer-from-the-list-of-customers"></a>Condition 2 : Récupération des détails pour un client spécifique à partir de la liste des clients  
 Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des clients basés sur le nom du client, vous devez effectuer l’ensemble suivant de tâches.  
  
-   Dans la méthode SD_RFC_CUSTOMER_GET, créer un identificateur et le mapper au paramètre qui stocke le numéro de client.  
  
-   Créer un **recherche spécifique** instance de méthode pour la méthode SD_RFC_CUSTOMER_GET. A **recherche spécifique** méthode trouve un enregistrement spécifique en fonction d’un identificateur.  
  
##### <a name="to-create-an-identifier-and-map-it-to-the-customer-number-parameter"></a>Pour créer un identificateur et la mapper vers le paramètre numéro de client  
  
1.  Créer un identificateur pour le **client** entité.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud.  
  
    2.  Cliquez sur le **identificateurs** nœud et sélectionnez **ajouter un identificateur**.  
  
         ![Ajouter un identificateur à une méthode](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")  
  
    3.  Dans le volet Propriétés, tapez **CustomerID** dans les **nom** boîte.  
  
    4.  Sélectionnez **System.String** pour le **Type** boîte.  
  
         ![Spécifiez un nom pour l’identificateur](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")  
  
2.  Mapper l’identificateur pour le paramètre de clé pour la méthode SD_RFC_CUSTOMER_GET.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
    2.  La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.  
  
    3.  Développez le **KUNNR** paramètre, puis cliquez sur le deuxième **KUNNR** nœud.  
  
    4.  Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.  
  
         ![Mapper l’identificateur à un paramètre](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")  
  
3.  Définir une association entre les paramètres d’entrée et de retournés.  
  
    1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis développez le **méthodes** nœud.  
  
    2.  La méthode SD_RFC_CUSTOMER_GET, puis le **paramètres** nœud.  
  
    3.  Développez le **CUSTOMER_T** nœud, puis le deuxième **CUSTOMER_T** nœud, puis le **élément** nœud, puis cliquez sur le **KUNNR** nœud.  
  
    4.  Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.  
  
##### <a name="to-create-a-specific-finder-method-instance-for-the-sdrfccustomerget-method"></a>Pour créer une instance de méthode Finder spécifique pour la méthode SD_RFC_CUSTOMER_GET  
  
1.  Dans le volet objets de métadonnées, développez le **client** nœud, puis le **méthodes** nœud.  
  
2.  Développez le **SD_RFC_CUSTOMER_GET** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")  
  
3.  Dans la fenêtre Créer une Instance de méthode, sélectionnez **recherche spécifique** pour **Type d’Instance de méthode**. De même, sélectionnez **CUSTOMER_T** pour **TypeDescriptor de retour**.  
  
     ![Ajouter une Instance de méthode Finder spécifique](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **GetCustomerByNumber_Instance** pour le **nom** boîte.  
  
     ![Spécifiez un nom pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")  
  
### <a name="requirement-3-retrieve-sales-order-details-for-a-specific-customer-from-the-list-of-customers"></a>Condition 3 : Récupérer les détails des commandes client pour un client spécifique à partir de la liste des clients  
 Pour créer un fichier de définition d’application qui peut être utilisé pour récupérer les détails des commandes client pour un client spécifique, vous devez effectuer l’ensemble suivant de tâches.  
  
-   Configurer une association entre la **client** et **SalesOrder** entités.  
  
-   Créer un **Association** méthode pour la méthode BAPI_SALESORDER_GETLIST.  
  
##### <a name="to-create-an-association-between-the-customer-and-salesorder-entities"></a>Pour créer une association entre les entités Customer et SalesOrder  
  
1.  Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.  
  
2.  La méthode BAPI_SALESORDER_GETLIST, puis le **paramètres** nœud.  
  
3.  Développez le **CUSTOMER_NUMBER** nœud, puis cliquez sur le deuxième **CUSTOMER_NUMBER** nœud.  
  
4.  Dans le volet Propriétés, sélectionnez **CustomerID [Customer]** à partir de la **identificateur** liste.  
  
     ![Créer une association entre les deux entités](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")  
  
##### <a name="to-create-an-association-method-instance-for-the-bapisalesordergetlist-method"></a>Pour créer une instance de méthode d’Association pour la méthode BAPI_SALESORDER_GETLIST  
  
1.  Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **BAPI_SALESORDER_GETLIST** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajoutez une Instance de méthode Association](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")  
  
3.  Dans la fenêtre Créer une Instance de méthode, sélectionnez **Association** pour **Type d’Instance de méthode**.  
  
4.  Dans le **entités sources** liste, sélectionnez **client**.  
  
5.  Dans le **TypeDescriptor de retour** liste, sélectionnez **SALES_ORDERS**...  
  
     ![Créer une Instance de méthode Association](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le volet Propriétés, tapez **SalesOrderForCustomer_Instance** pour le **nom** boîte.  
  
     ![Spécifiez un nom pour la méthode d’Association](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")  
  
### <a name="remove-parameters-of-systemnullable-type"></a>Supprimer les paramètres de Type de System.Nullable  
 Lors de la création du **Association** instance de méthode pour la méthode BAPI_SALESORDER_GETLIST, vous avez sélectionné le type de retour en tant que SALES_ORDERS. Si vous développez le paramètre SALES_ORDER, vous remarquerez que certains paramètres sont de type de System.Nullable. Vous pouvez voir le paramètre de type en sélectionnant le paramètre dans Business Data Catalog Definition Editor et en examinant la valeur de la **TypeName** propriété.  
  
 Pour ces paramètres, l’éditeur de définition de catalogue de données métier crée un autre paramètre portant le même nom mais avec un suffixe « Spécifié ». Par exemple, examinez les paramètres *ITM_NUMBER* et *ITM_NUMBERSpecified*. Microsoft Office SharePoint Server ne prend pas en charge System.Nullable paramètres. Par conséquent, lorsque vous essayez d’enregistrements qui contiennent le type de paramètre System.Nullable, elle lève une exception. Par conséquent, vous devez supprimer les paramètres (avec et sans le suffixe « Spécifié » et portant le même nom) à partir de Business Data Catalog Definition Editor  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type"></a>Pour supprimer les paramètres du type de System.Nullable  
  
1.  Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **BAPI_SALESORDER_GETLIST** nœud, puis développez le **paramètres** nœud.  
  
3.  Développez **SALES_ORDERS**, développez la seconde **SALES_ORDERS**, puis développez **élément**.  
  
4.  Cliquez sur le paramètre qui contient le suffixe « Specified » dans le nom, puis sélectionnez **supprimer**.  
  
5.  Le paramètre qui porte le même nom que le paramètre que vous avez supprimé, sans le suffixe d’avec le bouton droit, puis sélectionnez **supprimer**. En règle générale, ce paramètre est juste avant le paramètre qui a le suffixe « Spécifié ».  
  
### <a name="set-default-parameters"></a>Définir les paramètres par défaut  
 Le BAPI_SALESORDER_GETLIST accepte deux paramètres. Un de ces paramètres, TRANSACTION_GROUP, est le paramètre par défaut. Par conséquent, vous devez définir la valeur par défaut pour ce paramètre.  
  
##### <a name="to-set-the-default-value-for-transactiongroup"></a>Pour définir la valeur par défaut pour TRANSACTION_GROUP  
  
1.  Dans le volet objets de métadonnées, développez le **SalesOrder** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **BAPI_SALESORDER_GETLIST** nœud, puis développez le **Instances** nœud.  
  
3.  Sélectionnez le **SalesOrderForCustomer_Instance** (méthode) de l’instance et dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **DefaultValues** boîte.  
  
4.  Dans la fenêtre d’édition, développez **TRANSACTION_GROUP** nœud et pour le **TRANSACTION_GROUP** , spécifiez la valeur par défaut 0.  
  
     ![Spécifiez une valeur par défaut pour l’instance de méthode](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")  
  
5.  Cliquez sur **Fermer**.  
  
### <a name="export-the-application-definition-to-a-file"></a>Exporter la définition d’Application dans un fichier  
 Vous venez de créer une définition d’application qui contient les métadonnées de l’instance du système SAP. Vous devez exporter cette définition dans un fichier XML, qui peut être importé dans Microsoft Office SharePoint Server.  
  
##### <a name="to-export-the-application-definition-to-a-file"></a>Pour exporter la définition d’application dans un fichier  
  
1.  Dans le volet objets de métadonnées, cliquez sur le **Customer_Order** nœud, puis cliquez sur **exporter**.  
  
2.  Enregistrez le fichier sous Customer_Order.xml.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous devez maintenant créer une application SharePoint pour récupérer des données à partir d’un système SAP. Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) pour obtenir des instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)
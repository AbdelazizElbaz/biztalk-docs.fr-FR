---
title: "Étape 2 : Créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2665afde-0337-4795-ab4c-6223d39fdf9c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed4340893d351d8406212b585e6216de19c634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-an-application-definition-file-for-the-oracle-e-business-suite-artifacts"></a>Étape 2 : Créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** la fonctionnalité de catalogue de données métiers dans Microsoft SharePoint Server expose et incorpore des données à partir d’applications de métier (LOB) dans des portails. Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.  
  
 L’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, vous permet de créer un fichier de définition d’application pour le catalogue de données métiers. Cet outil génère automatiquement un fichier XML pour le fichier de définition, vous n’avez pas besoin de créer manuellement le fichier dans un document XML éditeur.  
  
 L’objectif de l’application Microsoft Office SharePoint Server que vous créez est de :  
  
-   Requête pour un employé dans la table d’interface MS_SAMPLE_EMPLOYEE à l’aide d’un composant WebPart de liste de données Business basée sur un nom d’employé.  
  
-   Effectuer une recherche en texte intégral à partir de Microsoft Office SharePoint Server sur la table d’interface MS_SAMPLE_EMPLOYEE.  
  
 Pour chacune de ces exigences, vous devez effectuer un ensemble de tâches dans l’outil Éditeur de définition de catalogue de données métier. Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Assurez-vous que vous disposez de l’éditeur de définition de catalogue de données métier installé avec le SDK de Microsoft Office SharePoint Server 2007. Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).  
  
-   Publier le service WCF, comme décrit dans [étape 1 : utiliser l’adaptateur Oracle E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).  
  

  
##  <a name="Connect"></a>Se connecter au Service WCF LOB et créer une entité  
 Vous devez vous connecter au service WCF pour extraire la Description langage WSDL (Web Services) pour le service. À partir de WSDL, l’éditeur de définition de catalogue de données métier extrait les méthodes. Ces méthodes peuvent être utilisées pour créer des entités. Pour ce didacticiel, une entité est créée.  
  
#### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>Pour vous connecter au service WCF et de créer des entités  
  
1.  Démarrez l’éditeur de définition de catalogue de données métier. Sur le **Démarrer** menu, cliquez sur **Microsoft Business Data Catalog Definition Editor**.  
  
2.  Dans la barre d’outils, cliquez sur **ajouter un système LOB**.  
  
3.  Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.  
  
4.  Dans le **URL** zone, tapez l’URL pour le service WCF. Pour ce didacticiel, l’URL sera :  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc  
    ```  
  
     L’URL est disponible lorsque vous testez si le service WCF est publié avec succès, comme décrit dans [étape 1 : utiliser l’adaptateur Oracle E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).  
  
5.  Cliquez sur **Se connecter**.  
  
6.  Pour afficher les opérations que vous avez sélectionné dans l’Assistant développement d’adaptateurs WCF, cliquez sur le **ajouter une méthode Web** onglet. Vous verrez la méthode suivante : **sélectionnez**.  
  
7.  Faites glisser le **sélectionnez** méthodes à l’aire de conception. Lorsque vous faites glisser la méthode à l’aire de conception, une entité est créée, et la méthode devient partie intégrante de cette entité.  
  
     ![Ajouter la méthode Select à l’aire de conception](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")  
  
8.  Cliquez sur **OK**.  
  
9. Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte. Pour cet exemple, appeler **MS_SAMPLE_EMPLOYEE**, puis cliquez sur **OK**.  
  
10. Dans l’entreprise Data Catalog Definition Editor, l’entité nouvellement créée est répertoriée en tant que **Entity0**. Renommez l’entité **employé**. Procédez comme suit pour renommer l’entité :  
  
    1.  Développez le **MS_SAMPLE_EMPLOYEE** nœud, puis développez le **entités** nœud.  
  
    2.  Sélectionnez le **Entity0** nœud.  
  
    3.  Dans le volet Propriétés, tapez **employé** dans les **nom** boîte.  
  
         ![Renommer l’entité](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")  
  
##  <a name="Headers"></a>Spécifiez le nom d’utilisateur et les en-têtes de mot de passe pour les méthodes  
 Lorsque vous créez un service WCF pour l’opération Select sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite, vous avez spécifié des en-têtes nom et mot de passe d’utilisateur dans le cadre de la configuration de comportement de point de terminaison dans [étape 1 : utiliser le Oracle Adaptateur de E-Business pour créer et publier un Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md). Vous devez spécifier les mêmes valeurs pour la propriété de la méthode Select.  
  
#### <a name="to-specify-user-name-and-password-headers-for-the-select-method"></a>Pour spécifier les en-têtes de nom et mot de passe utilisateur pour la méthode Select  
  
1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
2.  Cliquez sur le **sélectionnez** nœud, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.  
  
3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderUserName** pour le **nom** boîte. Type **MyUserHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
4.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **HttpHeaderPassword** pour le **nom** boîte. De même, tapez **MyPasswordHeader** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
     ![Ajouter une propriété](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")  
  
5.  Cliquez sur **OK**.  
  
##  <a name="Scenario1"></a>Scénario 1 : Les requêtes pour les employés à l’aide d’un composant WebPart de liste de données métier  
 Pour créer un fichier de définition d’application qui peut être utilisé pour rechercher des employés à partir d’un composant WebPart de liste de données métier et basé sur le nom de l’employé, vous devez effectuer l’ensemble suivant de tâches.  
  
1.  Dans le **sélectionnez** (méthode), créer un filtre et mappez-le à le **filtre** paramètre.  
  
2.  Créer un **recherche** instance de méthode pour le **sélectionnez** (méthode). A **recherche** méthode récupère une liste d’enregistrements en fonction d’un filtre.  
  
#### <a name="to-create-a-filter-and-map-it-to-the-filter-parameter"></a>Pour créer un filtre et la mapper au paramètre de filtre  
  
1.  Créer un filtre.  
  
    1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez le **sélectionnez** (méthode), avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.  
  
         ![Ajouter un filtre à la méthode SELECT](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")  
  
    3.  Dans le volet Propriétés, pour le **FilterType** propriété, sélectionnez **est égal à**.  
  
    4.  Dans le volet Propriétés, tapez **EmployeeName** dans les **nom** boîte.  
  
         ![Spécifiez les propriétés de filtre](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")  
  
2.  Mapper le filtre à la **filtre** paramètre dans le **sélectionnez** (méthode).  
  
    1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.  
  
    3.  Développez le **filtre** nœud, puis cliquez sur le deuxième **filtre** nœud.  
  
    4.  Dans le volet Propriétés, sélectionnez **EmployeeName** à partir de la **FilterDescriptor** liste.  
  
         ![Mapper le filtre au paramètre de méthode Select](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")  
  
#### <a name="to-create-a-finder-method-instance-for-the-select-method"></a>Pour créer une instance de méthode Finder pour la méthode Select  
  
1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode**.  
  
     ![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**. Sélectionnez **retourner** pour **TypeDescriptor de retour**.  
  
     ![Créer une instance de méthode Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **Finder_Instance** dans les **nom** boîte.  
  
     ![Spécifiez un nom pour l’instance de méthode Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")  
  
##  <a name="Scenario2"></a>Scénario 2 : Recherche de texte intégral sur la Table d’Interface MS_SAMPLE_EMPLOYEE à partir de Microsoft Office SharePoint Server  
 Pour créer un fichier de définition d’application qui peut être utilisé pour effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE à partir de Microsoft Office SharePoint Server, vous devez effectuer l’ensemble suivant de tâches.  
  
-   Dans le **sélectionnez** (méthode), créer un identificateur et le mapper au paramètre filtre et la valeur de retour qui stocke le nom de l’employé.  
  
-   Créer un **recherche spécifique** instance de méthode pour le **sélectionnez**. Le **recherche spécifique** méthode trouve un enregistrement spécifique en fonction de l’identificateur, autrement dit, un nom d’employé.  
  
-   Créer une instance de méthode énumérateur d’ID.  
  
#### <a name="to-create-an-identifier-and-map-it-to-the-filter-parameter-and-employee-name-return-value"></a>Pour créer un identificateur et mapper pour le nom du paramètre et employé filtre valeur de retour  
  
1.  Créer un identificateur pour le **employé** entité.  
  
    1.  Dans le volet objets de métadonnées, développez le **employé** nœud.  
  
    2.  Cliquez sur le **identificateurs** nœud et sélectionnez **ajouter un identificateur**.  
  
         ![Créer un identificateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")  
  
    3.  Dans le volet Propriétés, tapez **EmployeeName** dans les **nom** boîte.  
  
    4.  Sélectionnez **System.String** pour le **Type** boîte.  
  
         ![Spécifiez les propriétés de l’identificateur](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")  
  
2.  Mapper l’identificateur pour le paramètre de filtre pour le **sélectionnez** (méthode).  
  
    1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.  
  
    3.  Développez le **filtre** paramètre, puis cliquez sur le deuxième **filtre** nœud.  
  
    4.  Dans le volet Propriétés, sélectionnez **EmployeeName [Employee]** à partir de la **identificateur** liste.  
  
         ![Définition d’identificateur pour le paramètre FILTER](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")  
  
3.  Mapper l’identificateur à la valeur de retour du nom employé.  
  
    1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
    2.  Développez le **sélectionnez** (méthode), puis développez le **paramètres** nœud.  
  
    3.  Développez le **retourner** nœud, puis le deuxième **retourner** nœud, puis le **élément** nœud, puis cliquez sur le **nom** nœud.  
  
    4.  Dans le volet Propriétés, sélectionnez **EmployeeName [Employee]** à partir de la **identificateur** liste.  
  
#### <a name="to-create-a-specific-finder-method-instance-for-the-select-method"></a>Pour créer une instance de méthode Finder spécifique pour la méthode Select  
  
1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis le **méthodes** nœud.  
  
2.  Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  Dans la fenêtre Créer une Instance de méthode, sélectionnez **recherche spécifique** pour **Type d’Instance de méthode**. Sélectionnez **retourner** pour **TypeDescriptor de retour**.  
  
     ![Ajouter une instance de méthode Finder spécifique](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **SpeciFinder_Instance** pour le **nom** boîte.  
  
#### <a name="to-create-an-id-enumerator-method-instance-for-the-select-method"></a>Pour créer une instance de méthode énumérateur d’Id pour la méthode Select  
  
1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis le **méthodes** nœud.  
  
2.  Développez le **sélectionnez** nœud, avec le bouton droit **Instances**, puis sélectionnez **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
     ![Ajouter une instance de méthode](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  Dans la fenêtre Créer une Instance de méthode, sélectionnez **énumérateur d’Id** pour **Type d’Instance de méthode**. Sélectionnez **retourner** pour **TypeDescriptor de retour**.  
  
     ![Créer une instance de méthode énumérateur d’Id](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **IDEnumerator_Instance** pour le **nom** boîte.  
  
##  <a name="Defaults"></a>Définir les paramètres par défaut pour les Instances (méthode)  
 La méthode Select vous oblige à spécifier les noms de colonnes. Par conséquent, vous devez spécifier une valeur par défaut pour le **les noms de colonne** paramètre pour les instances de méthode Finder, recherche spécifique et que l’énumérateur d’Id a été créé précédemment. En outre, vous devez également spécifier une valeur par défaut pour le **filtre** paramètre pour l’instance de méthode énumérateur d’Id.  
  
#### <a name="to-set-the-default-parameters-for-the-method-instances"></a>Pour définir les paramètres par défaut pour les instances (méthode)  
  
1.  Dans le volet objets de métadonnées, développez le **employé** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **sélectionnez** nœud, puis développez le **paramètres** nœud.  
  
3.  Développez le **les noms de colonne** nœud, puis sélectionnez le **les noms de colonne** paramètre.  
  
4.  Dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **DefaultValues** boîte.  
  
5.  Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **ajouter**, dans le volet des propriétés, cliquez sur **Finder_Instance** dans le  **SelectMethodInstance** liste.  
  
     ![En spécifiant la valeur par défaut pour l’instance Finder](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")  
  
6.  Type `*` dans les **valeur** boîte.  
  
7.  De même, répétez les étapes 5 et 6 pour ajouter des valeurs par défaut pour le **SpecificFinder_Instance** et **IDEnumerator_Instance** instances de méthode.  
  
8.  Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **OK**.  
  
9. Ensuite, ajoutez une valeur par défaut pour le **filtre** paramètre pour le **IDEnumerator_Instance** instance de méthode. Développez le **filtre** nœud, puis sélectionnez le **filtre** paramètre.  
  
10. Dans le volet Propriétés, cliquez sur le bouton de sélection (...) contre le **DefaultValues** boîte.  
  
11. Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **ajouter**, dans le volet des propriétés, cliquez sur **IDEnumerator_Instance** dans le  **SelectMethodInstance** liste.  
  
12. Type `%` dans les **valeur** boîte.  
  
     ![Valeurs par défaut pour l’instance de l’énumérateur d’Id](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")  
  
13. Dans le **l’éditeur de collections DefaultValueView** boîte de dialogue, cliquez sur **OK**.  
  
##  <a name="SSO"></a>Valeur de l’authentification unique pour la connexion à Oracle E-Business Suite  
 Une fois que vous avez terminé d’exécuter toutes les procédures dans cette rubrique, vous avez créé un fichier de définition d’application qui peut être importé dans une application SharePoint. À partir de l’application, vous appelez les méthodes pour récupérer les données pertinentes à partir d’Oracle E-Business Suite. Pour ce faire, vous devez créer un mappage entre un utilisateur dans Oracle E-Business Suite et de l’utilisateur dans l’application SharePoint. Vous créez ce mappage dans la console d’Administration centrale de SharePoint après avoir importé le fichier de définition d’application.  
  
 Toutefois, pour créer le mappage, vous devez définir une propriété **SecondarySsoApplicationId** dans Business Data Catalog Definition Editor.  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a>Pour définir la propriété SecondarySsoApplicationId  
  
1.  Dans le volet objets de métadonnées, développez le **MS_SAMPLE_EMPLOYEE** nœud, puis développez le **Instances** nœud.  
  
2.  Cliquez sur **MS_SAMPLE_EMPLOYEE_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection (...) par rapport à la **propriétés** boîte.  
  
3.  Dans le **l’éditeur de collections PropertyView** boîte de dialogue, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** pour le **nom** boîte. De même, tapez **OracleSSO** pour le **PropertyValue** boîte. Sélectionnez **System.String** pour le **Type** boîte.  
  
     ![Ajouter la propriété SSO](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")  
  
4.  Cliquez sur **OK**.  
  
##  <a name="Export"></a>Exporter la définition d’Application dans un fichier  
 Vous venez de créer une définition d’application qui contient les métadonnées de l’instance Oracle E-Business Suite. Vous devez exporter cette définition dans un fichier XML, qui peut être importé dans Microsoft Office SharePoint Server.  
  
#### <a name="to-export-the-application-definition-to-a-file"></a>Pour exporter la définition d’application dans un fichier  
  
1.  Dans le volet objets de métadonnées, cliquez sur le **MS_SAMPLE_EMPLOYEE** nœud, puis cliquez sur **exporter**.  
  
2.  Enregistrez le fichier sous Employee.xml.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous devez maintenant créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite. Pour obtenir des instructions, consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un Site SharePoint](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)
---
title: "Étape 3 : Créer un fichier de définition d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 843fafdb-571e-4da4-ad04-7dc7f23e03ac
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce22a63e8267c36c1306974caa0faa5f9aa6be4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-an-application-definition-file"></a>Étape 3 : Créer un fichier de définition d’Application
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 15 minutes  
  
 La fonctionnalité de catalogue de données métiers dans Microsoft Office SharePoint Server expose et incorpore des données dans les applications line-of-business (LOB) dans des portails. Pour intégrer ces données dans votre site portail, vous devez générer un fichier de définition d’application Microsoft Office SharePoint Server peut consommer.  
  
 Dans cette étape, vous utilisez l’outil Business Data Catalog Definition Editor, disponible avec le SDK Microsoft Office SharePoint Server 2007, pour créer un fichier de définition d’application pour le catalogue de données métiers. Ce fichier de définition décrit la méthode EchoGreetings de l’adaptateur d’écho et servira dans les étapes suivantes pour activer SharePoint pour communiquer avec la carte.  
  
 L’objectif de l’application Microsoft Office SharePoint Server que vous créez doit vous permettent d’appeler la méthode EchoGreetings de l’adaptateur d’écho et de retourner la réponse à l’aide d’un composant WebPart SharePoint.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 2 : déployer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md). Vous devez également avoir accès à la Business Data Catalog Definition Editor, qui est installé dans le cadre de la SDK Microsoft Office SharePoint Server 2007. Vous pouvez télécharger le Kit de développement logiciel à partir de [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).  
  
## <a name="creating-an-application-definition-file"></a>Création d’un fichier de définition d’Application  
 Cette rubrique fournit des instructions pas à pas pour créer un fichier de définition d’application pour la connexion du catalogue de données métiers SharePoint avec l’adaptateur WCF hébergé dans IIS.  
  
#### <a name="to-connect-to-the-wcf-adapter-service-and-create-entities"></a>Pour vous connecter au service de l’adaptateur WCF et créer des entités  
  
1.  À partir de la **menu Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Microsoft Business Data Catalog Definition Editor**.  
  
2.  Dans la barre d’outils, cliquez sur **ajouter un système LOB**.  
  
3.  Dans la fenêtre Ajouter un système LOB, cliquez sur **se connecter au service Web**.  
  
4.  Dans le **URL** zone, tapez l’URL pour le service WCF. L’URL doit être au format suivant :`https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`  
  
5.  Cliquez sur **Se connecter**.  
  
6.  Pour afficher les opérations disponibles, cliquez sur le **ajouter une méthode Web** onglet. Vous devez voir la méthode EchoGreetings. Faites glisser la méthode à l’aire de conception.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **Entrez un nom pour le système LOB** boîte de dialogue, tapez un nom dans la **nom du système LOB** boîte. Par exemple, entrez **EchoWSLOB**, puis cliquez sur **OK**.  
  
9. Développez le **EchoWSLob** nœud, puis développez le **entités** nœud. Sélectionnez **Entity0** et dans le type du volet Propriétés **EchoGreetings** comme valeur pour le **nom** propriété.  
  
     ![Nom de l’entité](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")  
  
## <a name="specify-user-name-and-password-headers-for-the-method"></a>Spécifiez le nom d’utilisateur et mot de passe en-têtes pour la méthode  
 Lors de l’appel d’un adaptateur WCF, vous devrez fournir les informations d’identification d’utilisateur qui seront transmises au système métier. Dans [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md), vous avez configuré l’adaptateur Echo pour exiger que les informations de nom et mot de passe utilisateur fourni dans les champs MyUserHeader et MyPassHeader. Vous devez maintenant utiliser les mêmes noms de champ pour ce fichier de définition d’application.  
  
#### <a name="to-specify-user-name-and-password-headers"></a>Pour spécifier les en-têtes de nom et mot de passe utilisateur  
  
1.  Dans le volet objets de métadonnées, développez le **EchoGreetings** nœud, puis développez le **méthodes** nœud.  
  
2.  Cliquez sur le **EchoGreetings** nœud et, dans le volet Propriétés, cliquez sur le bouton de sélection **(...)**  situé dans le **propriétés** champ.  
  
3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le **nom** champ du volet Propriétés, type **HttpHeaderUserName**.  
  
     ![Spécifiez les champs d’en-tête de nom d’utilisateur](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")  
  
4.  Dans le **PropertyValue**, tapez **MyUserHeader**.  
  
5.  Cliquez sur **ajouter**et dans le type de volet propriété **HttpHeaderPassword** pour le champ nom, puis tapez **MyPassHeader** pour la **PropertyValue**champ.  
  
6.  Cliquez sur **OK**.  
  
## <a name="set-up-single-sign-on-for-connecting-to-the-echo-adapter"></a>Définir des Single Sign-On pour la connexion à l’adaptateur d’écho  
 SharePoint utilise les informations à partir de l’authentification unique pour remplir le MyUserHeader et MyPassHeader avec des valeurs de l’authentification. Pour lier ce fichier de définition d’application pour l’authentification unique, vous devez fournir un SecondarySsoApplicationId.  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a>Pour définir la propriété SecondarySsoApplicationId  
  
1.  Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **Instances** nœud.  
  
2.  Cliquez sur **EchoWSLOB_Instance**, dans le volet Propriétés, cliquez sur le bouton de sélection **(...)** situé dans le **propriétés** champ.  
  
3.  Dans la fenêtre Éditeur de collections PropertyView, cliquez sur **ajouter**et dans le volet Propriétés, tapez **SecondarySsoApplicationId** dans les **nom** champ.  
  
4.  Dans le **PropertyValue** , tapez **EchoSSO**.  
  
     ![Définir SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")  
  
5.  Cliquez sur **OK**.  
  
## <a name="create-input-filters-and-default-values"></a>Créer des filtres d’entrée et les valeurs par défaut  
 Le fichier de définition d’application doit être en mesure d’accepter l’entrée d’utilisateur qui peut être passée à un service Web. Pour ce faire, vous devez effectuer l’ensemble suivant de tâches :  
  
#### <a name="to-create-a-filter-and-map-it-to-the-greeting-parameter"></a>Pour créer un filtre et la mapper au paramètre de message d’accueil  
  
1.  Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **EchoGreetings** (méthode), avec le bouton droit **filtres**, puis cliquez sur **ajouter un filtre**.  
  
3.  Dans le volet Propriétés, tapez **salutation** dans les **nom** champ.  
  
     ![Définir le nom du filtre](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")  
  
4.  Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud  
  
5.  Développez le **EchoGreetings** (méthode), puis développez le **paramètres** nœud.  
  
6.  Développez le **salutation** nœud, puis développez la seconde **salutation** nœud.  
  
7.  Cliquez sur le **greetingText** nœud, puis dans le volet Propriétés, sélectionnez **salutation** à partir de la **FilterDescriptor** liste.  
  
#### <a name="to-create-a-finder-method-instance-for-the-echogreetings-method"></a>Pour créer une instance de méthode Finder pour la méthode EchoGreetings  
  
1.  Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **EchoGreetings** (méthode), avec le bouton droit **Instances**, puis cliquez sur **ajouter une Instance de méthode** pour ouvrir la fenêtre Créer une Instance de méthode.  
  
3.  Dans la fenêtre Créer une Instance de méthode, cliquez sur **recherche** pour **Type d’Instance de méthode**, puis sélectionnez **retourner** pour **TypeDescriptor de retour**.  
  
     ![Créer l’Instance de méthode](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet Propriétés, tapez **EchoGreetings_Instance** dans les **nom** champ.  
  
#### <a name="to-set-default-parameters"></a>Pour définir les paramètres par défaut  
  
1.  Dans le volet objets de métadonnées, développez le **EchoWSLOB** nœud, puis développez le **méthodes** nœud.  
  
2.  Développez le **EchoGreetings** (méthode), puis développez le **Instances** nœud.  
  
3.  Sélectionnez le **EchoGreetings_Instance** méthode d’instance et dans le volet Propriétés, cliquez sur le bouton de sélection (...) dans le **DefaultValues** champ.  
  
4.  Dans la fenêtre d’édition, développez le **salutation** nœud, puis développez la seconde **salutation** nœud. Développez le **nom** nœud, jusqu'à ce que l’arborescence est entièrement affiché.  
  
5.  Dans la fenêtre d’édition, définissez les valeurs de champ comme suit :  
  
    |Définition de|Sur|  
    |--------------|-------------|  
    |**id**|Une valeur GUID, par exemple 27829ed4-583a - 40c 4-ad87-fb8cdd9dc98d.|  
    |**sentDateTime**|La date et l’heure, par exemple 15/05/08 9 h 12|  
    |**Prénom**|Première|  
    |**middleName**|Milieu|  
    |**lastName**|Dernière|  
  
     ![Paramètres par défaut](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")  
  
6.  Cliquez sur **Fermer**.  
  
### <a name="to-export-the-application-definition-file"></a>Pour exporter le fichier de définition d’application  
  
1.  Dans le volet objets de métadonnées, cliquez sur le **EchoWSLOB** nœud, puis cliquez sur **exporter**.  
  
2.  Enregistrez le fichier sous EchoWS.xml.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous avez utilisé l’outil Business Data Catalog Definition Editor pour créer un fichier de définition d’application qui peut être importé dans Microsoft Office SharePoint Server 2007 pour activer la connectivité avec votre adaptateur est hébergé dans IIS.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous devez maintenant créer une application SharePoint basée sur le fichier de définition d’application créé à cette étape. Consultez [étape 4 : créer une Application Sharepoint pour accéder à la carte](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md) pour obtenir des instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)
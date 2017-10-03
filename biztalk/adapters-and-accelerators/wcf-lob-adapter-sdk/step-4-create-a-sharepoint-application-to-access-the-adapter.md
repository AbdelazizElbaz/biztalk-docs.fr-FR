---
title: "Étape 4 : Créer une Application Sharepoint pour accéder à l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d8c398-370a-4c62-961d-0eab6066ad5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3360bbdf5ae5a6a8dde9851c544342ea6a6bc1cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-sharepoint-application-to-access-the-adapter"></a>Étape 4 : Créer une Application Sharepoint pour accéder à la carte
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 15 minutes  
  
 Dans cette étape vous prenez le fichier de définition d’application que vous avez créé à l’aide de l’outil Éditeur de définition de catalogue de données métier et l’importer dans Microsoft Office SharePoint Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous avez devez créé un fichier d’application comme décrit dans [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).  
  
-   Le service Microsoft Single Sign-On doit être en cours d’exécution.  
  
## <a name="how-to-create-a-sharepoint-application"></a>Comment créer une Application SharePoint  
 Création d’une application SharePoint implique les étapes suivantes :  
  
-   Créer une application Single Sign-On (SSO) dans SharePoint.  
  
-   Créer un fournisseur de Services partagés et importez le fichier de définition d’application.  
  
-   Créer une page Web et ajouter des composants WebPart.  
  
 Cette rubrique montre comment effectuer ces étapes.  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>Création d’une Application de l’authentification unique dans SharePoint  
 Pour passer les informations d’identification de l’utilisateur à l’adaptateur d’écho à partir d’une application SharePoint, vous devez configurer une application SSO qui mappe à un compte d’utilisateur ou un groupe.  
  
#### <a name="manage-server-settings-for-single-sign-on"></a>Gérer les paramètres de serveur pour l’authentification unique  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
3.  Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres de l’authentification unique sur**.  
  
4.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **paramètres du serveur** , cliquez sur **gérer les paramètres de serveur**.  
  
5.  Assurez-vous que les informations de cette page sont correctes pour votre installation de l’authentification unique. Pour plus d’informations sur ces opérations, consultez « Configurer l’authentification unique (Office SharePoint Server) » à [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
#### <a name="manage-settings-for-enterprise-application-definitions"></a>Gérer les paramètres des définitions d’application d’entreprise  
  
1.  Dans l’Administration centrale de SharePoint, dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
2.  Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres pour l’authentification unique sur**.  
  
3.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer les paramètres pour les définitions d’application d’entreprise**.  
  
4.  Dans la page Gérer les définitions d’Application d’entreprise, cliquez sur **un nouvel élément**.  
  
5.  Sur la créer Enterprise définitions Page Application, définissez la **nom d’affichage** au champ **EchoSSO**, puis définissez le **nom de l’Application** au champ  **EchoSSO**. Cette valeur doit correspondre à SecondarySsoApplicationId que vous avez spécifié dans [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).  
  
6.  Dans le **adresse de messagerie du Contact** champ, entrez votre adresse de messagerie, puis cliquez sur **OK**.  
  
#### <a name="manage-account-information-for-enterprise-application-definitions"></a>Gérer les informations de compte pour les définitions d’application d’entreprise  
  
1.  Dans l’Administration centrale de SharePoint, dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
2.  Sur la page opérations, dans le **Section de Configuration de sécurité**, cliquez sur **gérer les paramètres de l’authentification unique sur**.  
  
3.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer informations de compte pour entreprise définitions d’application**.  
  
4.  Sur les informations de compte gérer pour une définition d’Application d’entreprise, sélectionnez **EchoSSO** à partir de la **définition d’application d’entreprise** liste.  
  
5.  Dans le **nom de compte de groupe** , tapez le groupe Windows qui permet de sécuriser cette définition d’application. Par exemple, **les utilisateurs du domaine source\Administrateurs du domaine**.  
  
6.  Cliquez sur **Définir**.  
  
7.  Dans la page des informations de compte EchoSSO, dans le **nom d’utilisateur** le type de champ **testuser**, puis, dans le **mot de passe** le type de champ **testpassword**.  
  
8.  Cliquez sur **OK**, puis cliquez sur **fait**.  
  
## <a name="creating-a-shared-services-provider-and-importing-the-application-definition-file"></a>Création d’un fournisseur de Services partagés et l’importation du fichier de définition d’application  
 Un fournisseur de Services partagés (SSP) est un regroupement logique des services partagés et leurs ressources de prise en charge. Vous pouvez créer un fournisseur de services partagés à l’aide de la Console d’Administration centrale de SharePoint. Cet exemple fonctionne dans n’importe quel fournisseur. Pour plus d’informations sur la création d’un fournisseur de services partagés, consultez « Vue d’ensemble : créer et configurer des fournisseurs de Services partagés » à [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).  
  
### <a name="to-import-the-application-definition-file"></a>Pour importer le fichier de définition d’application  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans le **catalogue de données métiers** , cliquez sur **importer la définition d’application**.  
  
4.  Dans la page de définition d’Application importation, cliquez sur **Parcourir**, puis sélectionnez le fichier EchoWS.xml.  
  
5.  Cliquez sur **importation**, puis cliquez sur **OK**.  
  
## <a name="creating-web-parts"></a>Création de composants WebPart  
 Vous devez maintenant créer des composants WebPart de votre site SharePoint pour utiliser l’instance de la méthode créée dans l’éditeur de définition du catalogue de données métier. Composants WebPart est des composants réutilisables qui peuvent contenir tout type d’informations sur le Web, y compris analytiques, de collaboration et informations de base de données.  
  
#### <a name="to-create-a-web-part-page"></a>Pour créer une page Web  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur dans lequel vous avez importé le fichier de définition d’application.  
  
3.  Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
     ![Créer des Actions de Site](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")  
  
4.  Sur le **créer** page, dans le **Pages Web** , cliquez sur **Page WebPart**.  
  
5.  Dans la page Nouveau composant WebPart, dans le **nom** , tapez **EchoPart**, puis sélectionnez **pleine Page, Vertical** à partir de la **a choisi un modèle de disposition**liste.  
  
6.  Cliquez sur **Créer**.  
  
#### <a name="to-add-a-business-data-web-part"></a>Pour ajouter un composant WebPart données métier  
  
1.  Cliquez sur **Ajouter un composant WebPart**.  
  
2.  Dans le **ajouter des WebParts** boîte de dialogue, sélectionnez **liste de données métiers**, puis cliquez sur **ajouter**.  
  
     ![Liste de données métiers](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")  
  
3.  Cliquez sur **ouvrir le volet d’outils**.  
  
4.  Le volet d’outils liste de données métiers s’ouvre dans le volet droit. Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Sélectionnez le Type](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")  
  
5.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **EchoWSLob_Instance** application, puis sur **OK**.  
  
6.  Dans le volet d’outils liste de données d’entreprise, cliquez sur **OK**.  
  
7.  Vous sont présentées avec un champ qui vous permet d’entrer une valeur de message d’accueil à passer à la méthode EchoGreetings. Entrez des données dans le champ de message d’accueil, cliquez sur **récupérer les données**. Il appelle la méthode EchoGreetings de l’adaptateur d’écho hébergé dans IIS et retourne une réponse.  
  
     ![Liste EchoGreetings](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")  
  
    > [!NOTE]
    >  La colonne de nom ne contient-elle pas les informations d’utilisateur, mais affiche uniquement les BDC. Nom. Cela se produit, car le catalogue de données métiers attend seulement une structure de l’enregistrement simple et n’affiche pas la structure complexe représentée par le champ nom.  
  
8.  Cliquez sur **quitter le Mode édition** à partir de l’angle supérieur de la page.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous avez utilisé l’Administration centrale de SharePoint 3.0 pour importer une définition d’application et créer des composants WebPart qui utilisent cette définition d’appeler l’opération EchoGreetings de l’adaptateur de l’écho.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ce didacticiel est terminé. Pour plus d’informations à l’aide du catalogue de données métiers, consultez « Catalogue de données métiers » à [http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)
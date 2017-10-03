---
title: "Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86bde531-2daf-452b-b3e6-5481d66f72e7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94537b57a731e5d71459518fcbb0a528b6240d19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel"></a>Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de Siebel
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 15 minutes.  
  
 **Objectif :** vous devez maintenant mettre le fichier de définition d’application vous avez créé à l’aide de l’éditeur de définition de catalogue de données métier et importez-le dans Office SharePoint Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous avez devez créé un fichier de définition d’application, comme décrit dans [étape 2 : créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).  
  
-   Le service Microsoft Single Sign-on doit être en cours d’exécution.  
  
## <a name="how-to-create-a-sharepoint-application"></a>Comment créer une Application SharePoint  
 Création d’une application SharePoint implique les étapes suivantes :  
  
-   Créer une application d’authentification unique (SSO) dans SharePoint  
  
-   Créer un fournisseur de Services partagés (SSP)  
  
-   Importez le fichier de définition d’application  
  
-   Créer une page Web et ajouter des WebParts  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>Création d’une Application de l’authentification unique dans SharePoint  
 Pour accéder aux données dans un système Siebel à partir d’une application SharePoint, vous devez configurer une application SSO qui mappe un utilisateur SharePoint à un utilisateur Siebel. Création d’une application de l’authentification unique dans SharePoint implique les étapes suivantes :  
  
1.  **Gérer les paramètres du serveur pour l’authentification unique sur**. Dans cette étape, vous spécifiez un compte d’utilisateur qui peut gérer et configurer le service d’authentification unique. Vous pouvez le faire à partir de la page Gérer les paramètres de serveur. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Configure Single Sign-On pour Office SharePoint Server 2007 » au [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
2.  **Gérer les paramètres des définitions d’application d’entreprise**. Dans cette étape, vous configurez les paramètres de la définition d’application d’entreprise. Vous pouvez le faire à partir de la gérer les paramètres de page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint.  
  
    1.  Dans l’Administration centrale, dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
    2.  Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres de l’authentification unique sur**.  
  
    3.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer les paramètres des définitions d’application d’entreprise**.  
  
    4.  Dans la page Gérer les définitions d’Application d’entreprise, indiquez des valeurs pour le **nom d’affichage**, **nom de l’Application**et le **adresse de messagerie du Contact** champs.  
  
        > [!IMPORTANT]
        >  Pour le **nom de l’Application** champ, veillez à spécifier le même nom de l’application SSO que vous avez spécifié pour le **SecondarySsoApplicationId** variable lors de la création du fichier de définition de l’application, en tant que décrit dans [étape 2 : créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).  
  
    5.  Conservez les autres champs par défaut, puis cliquez sur **OK**.  
  
3.  **Gérer les informations de compte pour les définitions d’application d’entreprise**. Dans cette étape, vous activez les utilisateurs ou groupes de se connecter à une application d’entreprise à partir de SharePoint. Pour l’essentiel, cette étape vous mappez un utilisateur ou un groupe à un utilisateur dans le système métier. Vous spécifiez également les informations d’identification pour se connecter au système métier. Vous pouvez le faire à partir de gérer les informations de compte pour la page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Gérer les informations de compte pour une définition d’application d’entreprise » à [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
## <a name="creating-a-shared-services-provider"></a>Création d’un fournisseur de Services partagés  
 Un fournisseur de services partagés est un regroupement logique des services partagés et leurs ressources de prise en charge. Vous pouvez créer un fournisseur de services partagés à l’aide de la console d’Administration centrale de SharePoint.  
  
 Vous devez définir un site Web lors de la création d’un fournisseur SSP. Rappelez-vous que le numéro de port et l’adresse de site que vous créez. Vous allez importer la définition d’application de catalogue de données métiers pour ce site.  
  
 Pour plus d’informations sur la création d’un fournisseur de services partagés, consultez « Vue d’ensemble : créer et configurer des fournisseurs de Services partagés » à [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).  
  
## <a name="importing-the-application-definition-file"></a>L’importation du fichier de définition d’Application  
 Vous devez maintenant importer le fichier de définition d’application dans le SSP.  
  
#### <a name="to-import-the-application-definition-file"></a>Pour importer le fichier de définition d’application  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans le **catalogue de données métiers** , cliquez sur **importer la définition d’application**.  
  
4.  Dans la page Application importer la définition qui s’ouvre, cliquez sur Parcourir pour Siebel_Account.xml, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **Importer**.  
  
6.  Cliquez sur **OK**.  
  
 Après avoir importé l’application, vous pouvez voir votre application en accédant à la **afficher les Applications** lien. Cliquez sur le nom de l’application pour afficher les entités dans l’application.  
  
## <a name="creating-web-parts"></a>Création de composants WebPart  
 Vous devez maintenant créer des composants WebPart de votre site SharePoint pour afficher et gérer les données d’entreprise qui seront extraites à partir du système Siebel. Composants WebPart est des composants réutilisables qui peuvent contenir tout type d’informations sur le Web, y compris analytiques, de collaboration et informations de base de données.  
  
 Dans ce didacticiel, les composants WebPart sont créés pour la méthode d’instance qui ont été créés dans Business Data Catalog Definition Editor. Office SharePoint Server fournit différents types de composants WebPart pour une utilisation spécifique. Pour l’instance de méthode Finder, nous utiliserons le **liste de données métiers** WebPart. Ce composant WebPart vous permet de spécifier une expression de recherche pour effectuer une requête sur le composant de gestion de compte. Pour ce didacticiel, nous appelons cela la **requête comptes** WebPart.  
  
 Cette section fournit des instructions pour créer ces composants WebPart. Pour plus d’informations sur la création de composants WebPart, consultez le document Microsoft Office SharePoint Server 2007 (« Personnaliser les listes de données professionnelles, composants WebPart et sites ») à [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).  
  
 Les composants WebPart sera ajoutés à une même page WebPart. Vous devez créer une page Web avant d’ajouter les composants WebPart. Pour ce didacticiel, la page de composant WebPart est appelée **compte Siebel**.  
  
### <a name="creating-a-web-part-page"></a>Création d’une Page de composants WebPart  
 Cette section fournit des instructions pour créer une page WebPart.  
  
##### <a name="to-create-a-web-part-page"></a>Pour créer une page de composants WebPart  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans la page Administration de Services partagés, à partir de l’angle supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
     ![Menu pour créer un composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4.  Dans la page Créer, sous la **Pages Web** , cliquez sur **Page WebPart**.  
  
5.  Dans la page Nouveau composant WebPart, procédez comme suit :  
  
    1.  Dans le **nom** champ, spécifiez un nom pour la page. Pour ce didacticiel, spécifiez le nom de `Siebel Account`.  
  
    2.  Sélectionnez le **remplacer si le fichier existe déjà** case à cocher, si vous souhaitez remplacer les anciennes pages portant le même nom que la page que vous créez.  
  
    3.  Dans le **disposition** section, à partir de la **choisir un modèle de disposition** , sélectionnez une disposition de la page de composant WebPart. Pour ce didacticiel, sélectionnez **pleine Page, Vertical**.  
  
    4.  Dans **l’emplacement de sauvegarde** section, dans le **bibliothèque de documents** liste, sélectionnez **modèles de formulaire**.  
  
    5.  Cliquez sur **Créer**. La figure suivante illustre une page WebPart après sa création uniquement.  
  
         ![Page composant WebPart vide](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")  
  
     Vous devez maintenant ajouter les différents composants WebPart à cette page.  
  
### <a name="adding-a-business-data-list-web-part"></a>Ajout d’un composant WebPart de liste de données métier  
 Vous devez à présent ajouter un composant WebPart de liste de données métier à la page de composant WebPart. À l’aide de ce composant WebPart, vous interroge le composant de gestion de compte à l’aide d’une expression de recherche. Ce composant WebPart correspond à l’instance de méthode Finder (QueryAccount) que vous avez créé dans Business Data Catalog Definition Editor.  
  
##### <a name="to-add-a-business-data-list-web-part"></a>Pour ajouter un composant WebPart de liste de données métier  
  
1.  Dans le **compte Siebel** page, dans le **en-tête** , cliquez sur **ajouter un composant WebPart**.  
  
2.  Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **liste de données métiers** case à cocher, puis cliquez sur **ajouter**.  
  
     ![Options de création d’un composant WebPart de données business](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  Dans nouvellement ajoutée Business données WebPart liste, cliquez sur le **ouvrir le volet d’outils** lien.  
  
     ![Ouvrez le volet d’outils pour le composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  Le volet d’outils liste de données métiers s’ouvre dans le volet droit. Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Volet d’outils liste de données métiers](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")  
  
5.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **Siebel_Account_Instance** application, puis sur **OK**.  
  
     ![Sélectionnez l’instance d’application](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")  
  
6.  Développez le **apparence** nœud, puis, dans le **titre** Indiquez un titre pour le composant WebPart. Pour ce composant WebPart, spécifiez **liste des comptes**.  
  
7.  Dans le volet d’outils liste de données d’entreprise, cliquez sur **appliquer**, puis cliquez sur **OK**. Le composant WebPart de liste de données Business ressemble maintenant à ceci :  
  
     ![Composant WebPart de liste de données de l’entreprise](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")  
  
    > [!NOTE]
    >  Vous pouvez également modifier l’ordre dans lequel les colonnes de paramètre. Vous pouvez le faire en cliquant sur le **modifier la vue** lien vers la droite du composant WebPart.  
  
8.  Cliquez sur **quitter le Mode édition** à partir de l’angle supérieur droit de la page.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester l’application SharePoint en extrayant des données à partir d’un système Siebel. Consultez [étape 4 : tester votre Application SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)
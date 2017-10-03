---
title: "Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO application, creating an
- Business Data Catalog Definition Editor
- application definition file, importing
- Web Part
- SSP
- Web Part page, creating a
- Shared Services Provider, creating a
ms.assetid: 7158caec-9dc0-477c-9db3-179e634e5196
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 879a4b48da7645471e53db357f7c0a6260117f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-sap"></a>Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de SAP
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** vous devez maintenant prendre le fichier de définition d’application que vous avez créé à l’aide de l’outil Éditeur de définition de catalogue de données métier et l’importer dans Microsoft Office SharePoint Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous avez devez créé un fichier de définition d’application comme décrit dans [étape 2 : créer un fichier de définition d’Application pour les artefacts SAP](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md).  
  
-   Le service Microsoft Single Sign-on doit être en cours d’exécution.  
  
## <a name="how-to-create-a-sharepoint-application"></a>Comment créer une Application SharePoint  
 Création d’une application SharePoint implique les étapes suivantes :  
  
-   Créer une application d’authentification unique (SSO) dans SharePoint  
  
-   Créer un fournisseur de Services partagés  
  
-   Importez le fichier de définition d’application  
  
-   Créer une page Web et ajouter des WebParts  
  
 Cette rubrique montre comment effectuer ces étapes.  
  
## <a name="creating-an-sso-application-in-sharepoint"></a>Création d’une Application de l’authentification unique dans SharePoint  
 Pour accéder aux données dans un système SAP à partir d’une application SharePoint, vous devez configurer une application SSO qui mappe un utilisateur SharePoint à un utilisateur SAP. Création d’une application de l’authentification unique dans SharePoint implique les étapes suivantes :  
  
1.  **Gérer les paramètres du serveur pour l’authentification unique sur**. Dans cette étape, vous spécifiez un compte d’utilisateur qui peut gérer et configurer le service d’authentification unique. Vous pouvez le faire sur la page Gérer les paramètres de serveur. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Configure Single Sign-On pour Office SharePoint Server 2007 » au [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
2.  **Gérer les paramètres des définitions d’application d’entreprise**. Dans cette étape, vous configurez les paramètres de la définition d’application d’entreprise. Vous pouvez le faire à partir de la gérer les paramètres de page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint.  
  
    1.  Dans l’Administration centrale, dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
    2.  Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres de l’authentification unique sur**.  
  
    3.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer les paramètres des définitions d’application d’entreprise**.  
  
    4.  Dans la page Gérer les définitions d’Application d’entreprise, indiquez des valeurs pour le **nom d’affichage**, **nom de l’Application**et le **adresse de messagerie du Contact** champs.  
  
        > [!IMPORTANT]
        >  Pour le **nom de l’Application** champ, veillez à spécifier le même nom de l’application SSO que vous avez spécifié pour le **SecondarySsoApplicationId** variable lors de la création du fichier de définition de l’application, en tant que décrit dans [étape 2 : créer un fichier de définition d’Application pour les artefacts SAP](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md).  
  
    5.  Conservez les autres champs par défaut, puis cliquez sur **OK**.  
  
3.  **Gérer les informations de compte pour les définitions d’application d’entreprise**. Dans cette étape, vous activez les utilisateurs ou groupes de se connecter à une application d’entreprise à partir de SharePoint. Pour l’essentiel, cette étape vous mappez un utilisateur ou un groupe à un utilisateur dans le système métier. Vous spécifiez également les informations d’identification pour se connecter au système métier. Vous pouvez le faire gérer les informations de compte pour la page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Gérer les informations de compte pour une définition d’application d’entreprise » à [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
## <a name="creating-a-shared-services-provider"></a>Création d’un fournisseur de Services partagés  
 Un fournisseur de services partagés est un regroupement logique des services partagés et leurs ressources de prise en charge. Vous pouvez créer un fournisseur de services partagés à l’aide de la console d’Administration centrale de SharePoint.  
  
 Vous devez définir un site Web lors de la création d’un fournisseur SSP. Rappelez-vous que le numéro de port et l’adresse du site que vous créez. Vous allez importer la définition d’application de catalogue de données métiers pour ce site.  
  
 Pour plus d’informations sur la création d’un fournisseur de services partagés, consultez « Vue d’ensemble : créer et configurer des fournisseurs de Services partagés » à [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).  
  
## <a name="importing-the-application-definition-file"></a>L’importation du fichier de définition d’Application  
 Vous devez maintenant importer le fichier de définition d’application dans le SSP.  
  
#### <a name="to-import-the-application-definition-file"></a>Pour importer le fichier de définition d’application  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans le **catalogue de données métiers** , cliquez sur **importer la définition d’application**.  
  
4.  Dans la page Application importer la définition qui s’ouvre, cliquez sur Parcourir pour Customer_Orders.xml, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **Importer**.  
  
6.  Cliquez sur **OK**.  
  
     Après avoir importé l’application, vous pouvez afficher votre application en accédant à la **afficher les Applications** lien. Cliquez sur le nom de l’application pour afficher les entités dans l’application.  
  
## <a name="creating-web-parts"></a>Création de composants WebPart  
 Vous devez maintenant créer des composants WebPart de votre site SharePoint pour afficher et gérer les données d’entreprise qui seront extraites à partir du système SAP. Composants WebPart est des composants réutilisables qui peuvent contenir tout type d’informations sur le Web, y compris analytiques, de collaboration et informations de base de données.  
  
 Dans ce didacticiel, les composants WebPart sont créés pour la méthode d’instance qui ont été créés dans Business Data Catalog Definition Editor. Office SharePoint Server fournit différents types de composants WebPart pour une utilisation spécifique. Les composants WebPart suivantes sont utilisées ici :  
  
-   **Liste de données métiers** WebPart pour le **recherche** instance de méthode. Ce composant WebPart vous permet de spécifier une expression de recherche pour récupérer une liste de clients à partir du système SAP. Pour ce didacticiel, cela s’appelle le composant WebPart recherche clients.  
  
-   **Élément de données métiers** WebPart pour le **recherche spécifique** instance de méthode. Ce composant WebPart affiche les détails pour un client spécifique que vous sélectionnez dans le composant WebPart recherche clients. Ce composant WebPart est mappé sur le composant WebPart client de recherche.  Pour ce didacticiel, il s’agit de la partie Web des détails client.  
  
-   **Liste liée aux données métier** WebPart pour le **Association** instance de méthode. Ce composant WebPart répertorie les commandes pour un client spécifique que vous sélectionnez dans le composant WebPart recherche clients. Ce composant WebPart est associé avec le composant WebPart client de recherche.  Pour ce didacticiel, cela s’appelle le composant WebPart de détails de commande Sales.  
  
 Cette section fournit des instructions pour créer ces composants WebPart et créer des associations entre eux. Pour plus d’informations sur la création de composants WebPart, consultez « Personnaliser les listes de données professionnelles, composants WebPart et sites » à [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).  
  
 Les composants WebPart sera ajoutés à une même page WebPart. Vous devez créer une page Web avant d’ajouter les composants WebPart. Pour ce didacticiel, cette page de composant WebPart est appelée Customer_SalesOrders.  
  
### <a name="creating-a-web-part-page"></a>Création d’une Page de composants WebPart  
 Cette section fournit des instructions pour créer une page WebPart.  
  
##### <a name="to-create-a-web-part-page"></a>Pour créer une page Web  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
     ![Menu pour créer un composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4.  Dans la page Créer, dans le **Pages Web** , cliquez sur **Page WebPart**.  
  
5.  Dans la page Nouveau composant WebPart, procédez comme suit :  
  
    1.  Dans le **nom** , tapez un nom pour la page. Pour ce didacticiel, tapez le nom en tant que **Customer_SalesOrders**.  
  
    2.  Sélectionnez le **remplacer si le fichier existe déjà** case à cocher, si vous souhaitez remplacer les anciennes pages avec le même nom que la nouvelle page que vous créez.  
  
    3.  Dans le **disposition** section, à partir de la **choisir un modèle de disposition** , sélectionnez une disposition de la page de composant WebPart. Pour ce didacticiel, sélectionnez **en-tête, colonne de gauche, corps**.  
  
    4.  Dans le **enregistrer l’emplacement** section, dans le **bibliothèque de documents** , cliquez sur **modèles de formulaire**.  
  
    5.  Cliquez sur **Créer**. La figure suivante illustre une page WebPart après sa création uniquement.  
  
         ![Page composant WebPart vide](../../adapters-and-accelerators/adapter-sap/media/6aa68c43-59df-47c4-95a6-453f7c668025.gif "6aa68c43-59df-47c4-95a6-453f7c668025")  
  
    6.  Vous devez maintenant ajouter les différents composants WebPart à cette page.  
  
### <a name="adding-a-business-data-list-web-part"></a>Ajout d’un composant WebPart de liste de données métier  
 Vous devez à présent ajouter un composant WebPart de liste de données métier à la page de composant WebPart. À l’aide de ce composant WebPart vous récupère une liste de clients à partir du système SAP qui correspond à une expression de recherche. Ce composant WebPart correspond à la **recherche** instance de méthode (*GetCustomerByName_Instance*) que vous avez créé dans Business Data Catalog Definition Editor.  
  
##### <a name="to-add-a-business-data-list-web-part"></a>Pour ajouter un composant WebPart de liste de données métier  
  
1.  Dans la page Customer_SalesOrders, dans le **en-tête** , cliquez sur **ajouter un composant WebPart**.  
  
2.  Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **liste de données métiers** case à cocher, puis cliquez sur **ajouter**.  
  
     ![Options de création d’un composant WebPart de données business](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  Dans nouvellement ajoutée Business données WebPart liste, cliquez sur le **ouvrir le volet d’outils** lien.  
  
     ![Ouvrez le volet d’outils pour le composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  Le volet d’outils liste de données métiers s’ouvre dans le volet droit. Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Volet d’outils liste de données métiers](../../adapters-and-accelerators/adapter-sap/media/580c58bf-bfc7-4d48-8c62-8ca4eee4ab48.gif "580c58bf-bfc7-4d48-8c62-8ca4eee4ab48")  
  
5.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **Customer_Order_Instance** application, puis sur **OK**.  
  
     ![Sélectionnez l’instance d’application](../../adapters-and-accelerators/adapter-sap/media/79967c27-9c76-4394-89bc-38c63649bdda.gif "79967c27-9c76-4394-89bc-38c63649bdda")  
  
6.  Développez le **apparence** nœud, puis, dans le **titre** , tapez un titre pour le composant WebPart. Pour ce composant WebPart, tapez **liste de clients**.  
  
7.  Dans le volet d’outils liste de données d’entreprise, cliquez sur **appliquer**, puis cliquez sur **OK**. Le composant WebPart de liste de données Business ressemble maintenant à ceci :  
  
     ![Composant WebPart de liste de données de l’entreprise](../../adapters-and-accelerators/adapter-sap/media/185fb3f3-98b0-4efe-960d-91312912ad7d.gif "185fb3f3-98b0-4efe-960d-91312912ad7d")  
  
8.  Le composant WebPart répertorie les champs qui sont retournés par l’exécution de la RFC SD_RFC_CUSTOMER_GET. Vous pouvez supprimer les champs que vous ne souhaitez pas afficher sur le portail SharePoint. Pour supprimer les champs, cliquez sur le **modifier la vue** lien dans le coin supérieur droit du composant WebPart.  
  
9. Dans la page Modifier la vue, dans la section de colonnes, désactivez les cases à cocher sur les colonnes que vous ne souhaitez pas afficher.  
  
     ![Afficher des colonnes spécifiques dans SharePoint](../../adapters-and-accelerators/adapter-sap/media/24213b67-aafe-4534-91a7-06bde7bcbf7c.gif "24213b67-aafe-4534-91a7-06bde7bcbf7c")  
  
10. Cliquez sur **OK**.  
  
### <a name="adding-a-business-data-item-web-part"></a>Ajout d’un composant WebPart élément de données métier  
 Vous devez à présent ajouter un composant WebPart élément de données métier à la page de composant WebPart. Ce composant WebPart vous connectera également à la partie Web liste données métier que vous venez de créer. En procédant ainsi, vous serez en mesure de voir les détails pour un client que vous sélectionnez dans le composant WebPart de liste de données Business. Ce composant WebPart correspond à la **recherche spécifique** instance de méthode (*GetCustomerByNumber_Instance*) que vous avez créé dans Business Data Catalog Definition Editor.  
  
##### <a name="to-add-a-business-data-item-web-part"></a>Pour ajouter un composant WebPart élément de données métier  
  
1.  Dans la page Customer_SalesOrders, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **modifier la Page**.  
  
2.  Dans la page Customer_SalesOrders, dans le **colonne gauche** , cliquez sur **ajouter un composant WebPart**.  
  
3.  Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **élément de données métiers** case à cocher, puis cliquez sur **ajouter**.  
  
4.  Dans le nouvellement ajoutée Business données élément WebPart, cliquez sur le **ouvrir le volet d’outils** lien.  
  
5.  Le volet d’outils élément de données d’entreprise s’ouvre dans le volet droit. Dans le **élément de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Volet d’outils élément de données métiers](../../adapters-and-accelerators/adapter-sap/media/29322df5-4ce3-4c1f-a658-39a355dfe2aa.gif "29322df5-4ce3-4c1f-a658-39a355dfe2aa")  
  
6.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **Customer_Order_Instance** application, puis sur **OK**.  
  
7.  Dans le **vue** liste, sélectionnez **par défaut**.  
  
8.  Laissez le **élément** liste vide.  
  
    > [!NOTE]
    >  Pour le **élément** champ, vous devez spécifier un nom de client ou le numéro de client pour lequel vous souhaitez afficher les détails. Qui sert de paramètre d’entrée pour ce composant WebPart. Étant donné que vous allez récupérer le paramètre d’entrée en vous connectant au composant WebPart liste de données métier, vous ne devez pas spécifier explicitement un élément.  
  
9. Dans le **champs** , cliquez sur **choisir** pour sélectionner les champs que vous souhaitez afficher sur la page.  
  
10. Développez le **apparence** nœud, puis, dans le **titre** Indiquez un titre pour le composant WebPart. Pour ce composant WebPart, spécifiez **détails pour un client spécifique**.  
  
11. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
12. Connecter la composant WebPart à la **liste de clients** WebPart. Pour cela :  
  
    1.  Cliquez sur **modifier** vers le coin supérieur droit du composant WebPart.  
  
    2.  Dans le menu contextuel, pointez sur **connexions**, pointez sur **obtenir l’élément de**, puis cliquez sur **liste de clients**.  
  
         ![Connecter deux composants WebPart](../../adapters-and-accelerators/adapter-sap/media/505aead7-f498-448f-a7cb-55d0a121f91f.gif "505aead7-f498-448f-a7cb-55d0a121f91f")  
  
### <a name="adding-a-business-data-related-list-web-part"></a>Ajout de données d’une entreprise liés WebPart de liste  
 Vous devez à présent ajouter une entreprise données connexes WebPart de liste à la page de composant WebPart. Ce composant WebPart vous connectera également à l’entreprise données WebPart liste vous avez créé précédemment. En procédant ainsi, vous serez en mesure d’afficher les commandes client pour un client que vous sélectionnez dans le composant WebPart de liste de données Business. Ce composant WebPart correspond à la **Association** instance de méthode (*SalesOrderForCustomer_Instance*) vous avez créé dans Business Data Catalog Definition Editor.  
  
##### <a name="to-add-a-business-data-related-list-web-part"></a>Pour ajouter des données d’entreprise relatives au composant WebPart liste  
  
1.  Dans la page Customer_SalesOrders, dans le **corps** , cliquez sur **ajouter un composant WebPart**.  
  
2.  Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **liste liée aux données métier** case à cocher, puis cliquez sur **ajouter**.  
  
3.  Dans nouvellement ajoutée Business données connexes WebPart liste, cliquez sur le **ouvrir le volet d’outils** lien.  
  
4.  Le volet d’outils de liste liée aux données métier s’ouvre dans le volet droit. Dans le **liste liée aux données métier** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Données d’entreprise liés liste](../../adapters-and-accelerators/adapter-sap/media/1914e12d-27f0-4ecb-9605-3177183a2d44.gif "1914e12d-27f0-4ecb-9605-3177183a2d44")  
  
5.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **Customer_Order_Instance** application, puis sur **OK**. Le **relation** liste remplie avec le nom de la **Association** instance de méthode (*SalesOrderForCustomer_Instance*).  
  
6.  Développez le **apparence** nœud, puis, dans le **titre** , tapez un titre pour le composant WebPart. Pour ce composant WebPart, tapez **Sales Order pour un client spécifique**.  
  
7.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
8.  Le composant WebPart répertorie les champs qui sont retournés par l’exécution de la RFC BAPI_SALESORDER_GETLIST. Vous pouvez supprimer les champs que vous ne souhaitez pas afficher sur le portail SharePoint. Pour supprimer les champs, cliquez sur le **modifier la vue** lien dans le coin supérieur droit du composant WebPart.  
  
9. Dans la page Modifier la vue, dans le **colonnes** section, désactivez les zones de texte sur les colonnes que vous ne souhaitez pas afficher.  
  
10. Cliquez sur **OK**.  
  
11. Connecter la composant WebPart à la **liste de clients** WebPart. Pour cela :  
  
    1.  Cliquez sur **modifier** vers le coin supérieur droit de la **Sales Order pour un client spécifique** WebPart.  
  
    2.  Dans le menu contextuel, pointez sur **connexions**, pointez sur **obtenir un élément connexe de**, puis cliquez sur **liste de clients**.  
  
12. Cliquez sur **quitter le Mode édition** à partir de l’angle supérieur droit de la page.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester l’application SharePoint en récupérant des données à partir d’un système SAP. Consultez [étape 4 : tester votre Application SharePoint](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)
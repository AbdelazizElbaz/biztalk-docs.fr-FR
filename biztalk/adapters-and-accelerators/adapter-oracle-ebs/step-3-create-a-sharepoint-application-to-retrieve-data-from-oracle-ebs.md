---
title: "Étape 3 : Créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaa16011-9284-4ccf-8132-9c1e14cc6aa7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe9d6fc34fa039bb4b3861deb35fb51524180ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-e-business-suite"></a>Étape 3 : Créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** vous devez importer le fichier de définition d’application dans Microsoft Office SharePoint Server et configurer une application pour récupérer des données à partir d’Oracle E-Business Suite.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous avez devez créé un fichier de définition d’application comme décrit dans [étape 2 : créer un fichier de définition d’Application pour Oracle E-Business Suite artefacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).  
  
-   Le service Microsoft Single Sign-on doit être en cours d’exécution.  
  
 
  
##  <a name="SSO"></a>Création d’une Application de l’authentification unique dans SharePoint  
 Pour accéder aux données dans Oracle E-Business Suite à partir d’une application SharePoint, vous devez configurer une application SSO qui mappe un utilisateur SharePoint à un utilisateur d’Oracle E-Business Suite. Création d’une application de l’authentification unique dans SharePoint implique les étapes suivantes :  
  
1.  **Gérer les paramètres du serveur pour l’authentification unique sur**. Dans cette étape, vous spécifiez un compte d’utilisateur qui peut gérer et configurer le service d’authentification unique. Vous pouvez le faire sur la page Gérer les paramètres de serveur. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Configure Single Sign-On pour Office SharePoint Server 2007 » au [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
2.  **Gérer les paramètres des définitions d’application d’entreprise**. Dans cette étape, vous configurez les paramètres de la définition d’application d’entreprise. Vous pouvez le faire à partir de la gérer les paramètres de page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint.  
  
    1.  Dans l’Administration centrale, dans la barre de navigation supérieure, cliquez sur **Operations**.  
  
    2.  Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres de l’authentification unique sur**.  
  
    3.  Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer les paramètres des définitions d’application d’entreprise**.  
  
    4.  Dans la page Gérer les définitions d’Application d’entreprise, indiquez des valeurs pour le **nom d’affichage**, **nom de l’Application**et le **adresse de messagerie du Contact** champs.  
  
        > [!IMPORTANT]
        >  Pour le **nom de l’Application** champ, veillez à spécifier le même nom de l’application SSO que vous avez spécifié pour le **SecondarySsoApplicationId** variable lors de la création du fichier de définition de l’application, en tant que décrit dans [étape 2 : créer un fichier de définition d’Application pour Oracle E-Business Suite artefacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).  
  
    5.  Conservez les autres champs par défaut, puis cliquez sur **OK**.  
  
3.  **Gérer les informations de compte pour les définitions d’application d’entreprise**. Dans cette étape, vous activez les utilisateurs ou groupes de se connecter à une application d’entreprise à partir de SharePoint. Pour l’essentiel, cette étape vous mappez un utilisateur ou un groupe à un utilisateur dans le système métier. Vous spécifiez également les informations d’identification pour se connecter au système métier. Vous pouvez le faire gérer les informations de compte pour la page de définitions d’Application d’entreprise. Cette option est disponible à partir de la console d’Administration centrale de SharePoint. Pour plus d’informations sur cette étape, reportez-vous à la section « Gérer les informations de compte pour une définition d’application d’entreprise » à [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).  
  
##  <a name="SSP"></a>Création d’un fournisseur de Services partagés  
 Un fournisseur de services partagés est un regroupement logique des services partagés et leurs ressources de prise en charge. Vous pouvez créer un fournisseur de services partagés à l’aide de la console d’Administration centrale de SharePoint.  
  
 Vous devez définir un site Web lors de la création d’un fournisseur SSP. Rappelez-vous que le numéro de port et l’adresse du site que vous créez. Vous allez importer la définition d’application de catalogue de données métiers pour ce site.  
  
 Pour plus d’informations sur la création d’un fournisseur de services partagés, consultez « Vue d’ensemble : créer et configurer des fournisseurs de Services partagés » à [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).  
  
##  <a name="Import"></a>L’importation du fichier de définition d’Application  
 Vous devez maintenant importer le fichier de définition d’application dans le SSP.  
  
#### <a name="to-import-the-application-definition-file"></a>Pour importer le fichier de définition d’application  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans le **catalogue de données métiers** , cliquez sur **importer la définition d’application**.  
  
4.  Sur la page Application importer la définition qui s’ouvre, cliquez sur Parcourir pour Employee.xml, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **Importer**.  
  
6.  Une fois le fichier de définition d’application est importé avec succès, cliquez sur **OK**.  
  
     L’application créée à la suite de l’importation du fichier de définition d’application, MS_SAMPLE_EMPLOYEE, s’affiche.  
  
     ![L’application dans SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/media/b0695720-0113-49dc-8eb6-c685aceada6c.gif "b0695720-0113-49dc-8eb6-c685aceada6c")  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant, vous êtes prêt à créer des composants WebPart pour créer un site SharePoint pour afficher et rechercher les données d’entreprise qui seront extraites à partir d’Oracle E-Business Suite. Nous allons créer r :  
  
-   Entreprise données WebPart de liste pour afficher les enregistrements d’employés à partir de la table d’interface MS_SAMPLE_EMPLOYEE. Consultez [scénario 1 : afficher des données à l’aide de WebPart de liste de données entreprise](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).  
  
-   Rechercher un composant WebPart zone pour effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE. Consultez [scénario 2 : recherche à l’aide du composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un Site SharePoint](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)
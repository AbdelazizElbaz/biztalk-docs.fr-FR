---
title: "Étape 4 : Tester votre SharePoint Application1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7ded5a5-88d5-40aa-814b-70bc0a7dcfa3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b8be51df02bd9796b41201c0495758c281e8f14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application"></a>Étape 4 : Tester votre Application SharePoint
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** une fois que vous avez ajouté des composants WebPart dans le site SharePoint et créé une application, vous devez tester l’application en récupérant des données à partir du système SAP. Cette rubrique fournit des instructions sur l’utilisation de l’application pour récupérer les données à partir du système SAP.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Il convient que vous avez créé la page Web qui contient les composants WebPart approprié pour récupérer des données d’entreprise. Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md).  
  
### <a name="to-test-the-sharepoint-application"></a>Pour tester l’application SharePoint  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.  
  
3.  Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**. Dans le volet droit, cliquez sur **modèles de formulaire**.  
  
4.  Dans le **catégorie de formulaire** , cliquez sur **Customer_SalesOrders**. Vous avez spécifié ce nom lorsque vous avez créé la page de composant WebPart. L’illustration suivante montre la page de composant WebPart que vous avez créé.  
  
     ![Page composant WebPart terminée](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")  
  
5.  Rechercher des clients basés sur une chaîne de recherche. Par exemple, rechercher des clients avec des noms commençant par « John E ». Pour cela :  
  
    1.  Dans la liste de clients, à partir de la première liste, cliquez sur **CustomerName**.  
  
    2.  Dans la deuxième liste, cliquez sur **commence par**.  
  
    3.  Dans la zone de texte, tapez **John E**.  
  
    4.  Cliquez sur le **récupérer les données** lier ou appuyez sur ENTRÉE. L’illustration suivante montre les enregistrements récupérés à partir du système SAP qui répondent aux critères de recherche.  
  
         ![Rechercher les résultats à partir du système SAP](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")  
  
6.  Vous pouvez maintenant voir les détails d’un client dans la liste et les commandes client associés aux clients, le cas échéant. Pour ce faire, cliquez sur la case d’option par rapport à un numéro de client. La page est actualisée pour présenter les détails et les commandes pour un client spécifique dans les composants WebPart respectifs.  
  
     ![Données SAP présentées sur SharePoint](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")  
  
     Si les détails des clients et la commande client associée sont affichent correctement, vous avez terminé le didacticiel. Si aucun ou des données incorrectes s’affiche, vérifiez soigneusement votre travail pour vous assurer que vous avez effectué toutes les tâches correctement.  
  
## <a name="summary"></a>Résumé  
 Dans ce didacticiel, vous avez créé un service WCF pour les artefacts SAP que vous souhaitez accéder à partir d’un portail SharePoint. Vous avez créé également une définition d’application pour les artefacts SAP qui est importée dans un portail SharePoint pour créer des composants WebPart pour présenter des données à partir d’un système SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)
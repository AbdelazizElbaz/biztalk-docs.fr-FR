---
title: "Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3831814-8b70-4352-b22f-cebd08750ef5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1add974ca3ad0b80b7838b120920f4de47f1650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-display-data-using-business-data-list-web-part"></a>Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données métiers
Nous allons utiliser la **liste de données métiers** WebPart pour le **recherche** instance de méthode. Ce composant WebPart vous permet de spécifier une expression de recherche pour récupérer une liste d’employés à partir d’Oracle E-Business Suite. Pour ce didacticiel, cela s’appelle le composant WebPart Affichage employés. Cette section fournit des instructions sur la création de ce composant WebPart. Pour plus d’informations sur la création de composants WebPart, consultez « Personnaliser les listes de données professionnelles, composants WebPart et sites » à [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).  
  
 Vous devez créer une page Web avant d’ajouter les composants WebPart.  
  
## <a name="creating-a-web-part-page"></a>Création d’une Page de composants WebPart  
 Cette section fournit des instructions pour créer une page WebPart.  
  
###  <a name="WebPart"></a>Pour créer une page Web  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.  
  
3.  Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
     ![Menu pour créer un composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")  
  
4.  Dans la page Créer, dans le **Pages Web** , cliquez sur **Page WebPart**.  
  
5.  Dans la page Nouveau composant WebPart, procédez comme suit :  
  
    1.  Dans le **nom** , tapez un nom pour la page. Pour ce didacticiel, tapez le nom en tant que **MS_SAMPLE_EMPLOYEE**.  
  
    2.  Sélectionnez le **remplacer si le fichier existe déjà** case à cocher, si vous souhaitez remplacer les anciennes pages avec le même nom que la nouvelle page que vous créez.  
  
    3.  Dans le **disposition** section, à partir de la **choisir un modèle de disposition** , sélectionnez une disposition de la page de composant WebPart. Pour ce didacticiel, sélectionnez **pleine Page, Vertical**.  
  
    4.  Dans le **enregistrer l’emplacement** section, dans le **bibliothèque de documents** , cliquez sur **modèles de formulaire**.  
  
    5.  Cliquez sur **Créer**. L’illustration suivante montre la page de composant WebPart après sa création.  
  
         ![La nouvelle page WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")  
  
    6.  Vous devez maintenant ajouter les composants WebPart à cette page.  
  
## <a name="adding-a-business-data-list-web-part"></a>Ajout d’un composant WebPart de liste de données métier  
 Vous devez à présent ajouter un composant WebPart de liste de données métier à la page de composant WebPart. À l’aide de ce composant WebPart vous récupère une liste d’enregistrements d’employés à partir de la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite qui correspond à une expression de recherche. Ce composant WebPart correspond à la **recherche** instance de méthode (*Finder_Instance*) que vous avez créé dans Business Data Catalog Definition Editor.  
  
#### <a name="to-add-a-business-data-list-web-part"></a>Pour ajouter un composant WebPart de liste de données métier  
  
1.  Dans la page MS_SAMPLE_EMPLOYEE, cliquez sur **ajouter un composant WebPart**.  
  
2.  Dans le **ajouter des WebParts** boîte de dialogue le **données d’entreprise** section, sélectionnez le **liste de données métiers** case à cocher, puis cliquez sur **ajouter**.  
  
     ![Options de création d’un composant WebPart de données business](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")  
  
3.  Dans nouvellement ajoutée Business données WebPart liste, cliquez sur le **ouvrir le volet d’outils** lien.  
  
     ![Ouvrez le volet d’outils pour le composant WebPart](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")  
  
4.  Le volet d’outils liste de données métiers s’ouvre dans le volet droit. Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.  
  
     ![Volet d’outils liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")  
  
5.  Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **MS_SAMPLE_EMPLOYEE_Instance** application, puis sur **OK**.  
  
     ![Sélectionnez l’instance d’application](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")  
  
6.  Développez le **apparence** nœud, puis, dans le **titre** , tapez un titre pour le composant WebPart. Pour ce composant WebPart, tapez **liste d’employés**.  
  
7.  Dans le volet d’outils liste de données d’entreprise, cliquez sur **appliquer**, puis cliquez sur **OK**. Le composant WebPart de liste de données Business ressemble maintenant à ceci :  
  
     ![Composant WebPart de liste de données de l’entreprise](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")  
  
8.  Le composant WebPart répertorie les champs qui sont retournés par l’exécution de l’opération Select sur la table d’interface MS_SAMPLE_EMPLOYEE.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)   
 [Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)
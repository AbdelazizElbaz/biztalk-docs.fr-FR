---
title: "Étape 4 : Tester votre application SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a859044e-a28e-477e-a20b-f9bb3c9f7405
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 427235d27e4e783111ccdb60f799c228737cd008
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application"></a>Étape 4 : Tester votre application SharePoint
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** une fois que vous avez ajouté des composants WebPart dans le site SharePoint et créé une application, vous devez tester l’application en récupérant des données à partir d’Oracle E-Business Suite. Cette rubrique fournit des instructions sur l’utilisation de l’application pour récupérer les données à partir d’Oracle E-Business Suite.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Il convient que vous avez créé la page Web qui contient les composants WebPart approprié pour récupérer des données d’entreprise. Consultez [étape 3 : créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).  
  
### <a name="scenario-1-to-test-the-sharepoint-application-created-using-business-data-list-web-part"></a>Scénario 1 : Pour tester l’application SharePoint créé à l’aide de la WebPart de liste de données métier  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.  
  
3.  Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**. Dans le volet droit, cliquez sur **modèles de formulaire**.  
  
4.  Dans le **catégorie de formulaire** , cliquez sur **MS_SAMPLE_EMPLOYEE**. Vous avez spécifié ce nom lorsque vous avez créé la page de composant WebPart dans [scénario 1 : afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).  
  
5.  Rechercher des employés basés sur une chaîne de recherche. Par exemple, pour rechercher tous les employés, tapez  **%**  dans la zone de texte, puis cliquez sur **récupérer les données**. L’illustration suivante montre les enregistrements récupérés à partir d’Oracle E-Business Suite :  
  
     ![Résultat de la recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/bdc-result.gif "BDC_Result")  
  
6.  Vous pouvez également rechercher pour un employé spécifique en entrant leur nom ou le nom de famille :  
  
    -   Pour rechercher à l’aide du nom, tapez les premières lettres d’un nom d’employé suivi par le  **%**  symbole pour retourner les enregistrements de tous les employés correspondant aux critères de recherche.  
  
    -   Pour rechercher à l’aide du nom, tapez  **%**  suivi par nom d’employé.  
  
    > [!NOTE]
    >  La chaîne de recherche respecte la casse.  
  
     ![Recherche par prénom d’un employé](../../adapters-and-accelerators/adapter-oracle-ebs/media/b5044c4d-31ec-46d8-b02c-3b26bfe8178e.gif "b5044c4d-31ec-46d8-b02c-3b26bfe8178e")  
  
### <a name="scenario-2-to-test-the-sharepoint-application-created-to-perform-a-full-text-search"></a>Scénario 2 : Pour tester l’application SharePoint créé pour effectuer une recherche en texte intégral  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.  
  
3.  Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**. Dans le volet droit, cliquez sur **modèles de formulaire**.  
  
4.  Dans le **catégorie de formulaire** , cliquez sur **MS_SAMPLE_EMPLOYEE_Search**. Vous avez spécifié ce nom lorsque vous avez créé la page de composant WebPart dans [scénario 2 : effectuer une recherche à l’aide du composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md) dans [scénario 2 : effectuer une recherche à l’aide du composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md).  
  
5.  La page MS_SAMPLE_EMPLOYEE_Search affiche la zone de recherche dans laquelle vous pouvez effectuer une recherche en texte intégral sur la table EMPLOYEE de MS_SAMPLE. Par exemple, si vous souhaitez rechercher tous les employés qui vivent à New York, tapez `New York` dans la zone de recherche, appuyez sur ENTRÉE.  
  
     ![Spécifiez un paramètre de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/34-search-result.gif "34_Search_Result")  
  
6.  Une page s’affiche avec les résultats de recherche. Chaque enregistrement correspondant s’affiche sous forme de lien dans la page de résultats.  
  
     ![Résultats de la recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/05cc6fdc-8c9f-4312-8579-ef1753d02c63.gif "05cc6fdc-8c9f-4312-8579-ef1753d02c63")  
  
7.  Cliquez sur un lien dans le résultat de recherche pour afficher l’enregistrement d’employé respectif.  
  
     ![Enregistrement d’employé détaillé](../../adapters-and-accelerators/adapter-oracle-ebs/media/36-search-result2.gif "36_Search_Result2")  
  
## <a name="summary"></a>Résumé  
 Dans ce didacticiel, vous avez créé un service WCF pour les artefacts d’Oracle E-Business Suite que vous souhaitez accéder à partir d’un portail SharePoint. Vous avez créé également une définition d’application pour les artefacts d’Oracle E-Business Suite est importée dans un portail SharePoint pour créer des composants WebPart pour présenter et rechercher des données dans Oracle E-Business Suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](../../adapters-and-accelerators/adapter-oracle-ebs/tutorial-present-data-from-oracle-e-business-suite-on-a-sharepoint-site.md)
---
title: "Étape 4 : Votre SharePoint Application de Test avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1392fa-fdc1-42be-b4dc-75a55d8fa400
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cebcafcdf768686ed3f7382a0838db5062d96b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application-with-the-siebel-adapter"></a>Étape 4 : Tester votre Application SharePoint avec l’adaptateur Siebel
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 5 minutes.  
  
 **Objectif :** une fois que vous avez ajouté des composants WebPart dans le site SharePoint et créé une application, vous devez tester l’application en récupérant des données à partir du système Siebel. Cette section fournit des instructions sur l’utilisation de l’application pour récupérer les données à partir du système Siebel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Il convient que vous avez créé la page de composant WebPart contenant les composants WebPart approprié pour récupérer des données d’entreprise. Consultez [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md).  
  
### <a name="to-test-the-sharepoint-application"></a>Pour tester l’application SharePoint  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom du fournisseur sous lequel vous avez créé l’application.  
  
3.  Dans le volet gauche, cliquez sur **afficher tout le contenu du Site**. Dans le volet droit, cliquez sur **modèles de formulaire**.  
  
4.  Dans le **catégorie de formulaire** , cliquez sur **compte Siebel**. Vous avez spécifié ce nom lors de la création de la page de composant WebPart. L’illustration suivante montre la page de composant WebPart que vous avez créé.  
  
     ![Page composant WebPart terminée](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")  
  
5.  Le composant de gestion de compte selon une chaîne de recherche de la requête. Par exemple, spécifiez l’expression de recherche `[Name] LIKE ‘W*’`. Pour cela :  
  
    1.  Dans le **liste des comptes** section, dans la première liste, sélectionnez **SearchExpression**, puis sélectionnez **est égal à**.  
  
    2.  Dans le champ de texte, tapez `[Name] LIKE ‘W*’`.  
  
    3.  Cliquez sur **récupérer les données** lier, ou appuyez sur ENTRÉE. L’illustration suivante montre les enregistrements récupérés à partir du système Siebel qui répondent aux critères de recherche.  
  
         ![Rechercher les résultats à partir du système Siebel](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)
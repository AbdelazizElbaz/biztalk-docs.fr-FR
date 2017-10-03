---
title: "Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a233772f-7577-4ac5-b55a-cb1ba2f464c7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03e536df00499e8965632a3952eb3ae50e3f83df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2--search-using-the-search-box-web-part"></a>Scénario 2 : Effectuer une recherche avec le composant WebPart zone de recherche
Nous configurerons les paramètres de recherche dans Microsoft Office SharePoint Server pour configurer une application de recherche à l’aide de laquelle vous pouvez effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite. Une version ultérieure, nous allons ajouter une zone WebPart de recherche à d’où vous pouvez effectuer la recherche.  
  
 
  
##  <a name="Define"></a>Définir la Source de contenu  
 Cette section présente sur la définition d’une source de contenu à partir de sur lequel Microsoft Office SharePoint Server peut analyser les données. Cela implique le mappage du contenu à l’énumérateur d’Id instance de méthode créé dans [étape 2 : créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).  
  
#### <a name="to-define-a-content-source"></a>Pour définir une source de contenu  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.  
  
3.  Sur la page d’accueil, dans le **recherche** , cliquez sur **paramètres de recherche**.  
  
4.  Dans la page Configurer les paramètres de recherche, dans le volet gauche sous **analyse**, cliquez sur **compte d’accès au contenu par défaut** pour spécifier un compte à utiliser en tant que le compte par défaut lors de l’analyse de contenu.  
  
5.  Dans la page compte d’accès au contenu par défaut, spécifiez les informations d’identification utilisateur et mot de passe, puis cliquez sur **OK**. Vous revenez à la page d’Administration de la recherche.  
  
6.  Dans le volet gauche sous **analyse**, cliquez sur **Sources de contenu**.  
  
7.  Dans la page Gérer les Sources de contenu, cliquez sur **nouvelle Source de contenu**.  
  
8.  Dans la page Gérer les Sources de contenu, cliquez sur **nouvelle Source de contenu**.  
  
9. Dans la page Source de contenu à ajouter :  
  
    1.  Type `MS_SAMPLE_EMPLOYEE` dans les **nom** boîte.  
  
    2.  Dans le **le Type de Source de contenu** zone, cliquez sur **données d’entreprise**.  
  
    3.  Dans le **Applications** zone, cliquez sur **analyse des applications sélectionnées**, puis sélectionnez le **MS_SAMPLE_EMPLOYEE_Instance** case à cocher.  
  
    4.  Dans le **démarrer l’analyse complète** zone, sélectionnez le **démarrer une analyse complète de cette source de contenu** case à cocher, puis cliquez sur **OK**.  
  
         ![Ajouter une source de contenu](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")  
  
10. Vous revenez à la page Gérer les Sources de contenu avec la nouvelle source de contenu ajoutée. La source de contenu analyse les données de la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite. Attendez que l’analyse est terminée.  
  
11. Dans le volet gauche sous **analyse**, cliquez sur **journal d’analyse**, puis vérifiez le fichier journal pour vous assurer que l’analyse a réussi.  
  
##  <a name="Scope"></a>Définir une étendue pour le contenu analysé  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.  
  
3.  Sur la page d’accueil, dans le **recherche** , cliquez sur **paramètres de recherche**.  
  
4.  Dans la page Configurer les paramètres de recherche, dans le volet gauche sous **interroge et résultats**, cliquez sur **étendues** pour définir une étendue de l’analyse de données.  
  
5.  Dans la page Afficher les étendues, cliquez sur **nouvelle étendue**.  
  
6.  Dans la page Créer une étendue, tapez `MS_SAMPLE_EMPLOYEE_Search` dans les **titre** zone, puis cliquez sur **OK**.  
  
     ![Créer une étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")  
  
7.  Vous revenez à la page Afficher les étendues avec la nouvelle étendue ajoutée. Dans le **état de mise à jour** colonne pour l’étendue nouvellement ajoutée, cliquez sur le **ajouter des règles** lien.  
  
8.  Dans la page Ajouter une règle d’étendue :  
  
    1.  Dans le **Type de règle d’étendue** zone, cliquez sur **Source de contenu**.  
  
    2.  Dans le **Source du contenu** , cliquez sur **MS_SAMPLE_EMPLOYEE**, puis cliquez sur **OK**.  
  
         ![Ajouter une règle d’étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")  
  
9. Vous revenez à la page Afficher les étendues à la règle ajoutée pour l’étendue. Dans le volet gauche, cliquez sur **Administration de la recherche**.  
  
10. Dans la page Administration de la recherche, recherchez le **étendues nécessitant une mise à jour** de ligne, puis cliquez sur le **démarrer la mise à jour maintenant** lien.  
  
 Le **état de mise à jour de l’étendue** ligne affiche l’état de la mise à jour de l’étendue. Attendez que la mise à jour est terminée. Une fois la mise à jour est terminée, l’étendue est prête à être utilisée.  
  
##  <a name="AddScope"></a>Ajout de l’étendue à la liste déroulante de recherche  
 Après avoir créé l’étendue de recherche, vous devez ajouter l’étendue à la liste déroulante de recherche dans Microsoft Office SharePoint Server afin qu’il peut être utilisé.  
  
#### <a name="to-add-the-scope-to-the-search-dropdown"></a>Pour ajouter l’étendue à la liste déroulante de recherche  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) dans lequel vous souhaitez configurer l’application de recherche.  
  
3.  Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **paramètres du Site**.  
  
4.  Dans la page Paramètres du Site, dans le **Administration de Collection de sites** , cliquez sur **zones de recherche**.  
  
5.  Dans la page Afficher les étendues, cliquez sur le **liste déroulante de recherche** lien.  
  
     ![Afficher les étendues](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")  
  
6.  Dans la page Modifier le groupe affichage étendue :  
  
    1.  Dans le **étendues** zone, sélectionnez le **MS_SAMPLE_EMPLOYEE_Search** case à cocher.  
  
    2.  Dans le **étendue par défaut** zone, cliquez sur **MS_SAMPLE_EMPLOYEE_Search** dans les **étendue par défaut** liste, puis cliquez sur **OK**.  
  
         ![Page Modifier le groupe affichage étendue](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")  
  
7.  Vous revenez à la page Afficher les étendues avec l’étendue MS_SAMPLE_EMPLOYEE_Search ajouté dans le groupe d’affichage de liste déroulante de recherche.  
  
##  <a name="SearchWebPart"></a>Ajouter le composant WebPart zone de recherche  
 Pour permettre aux utilisateurs d’effectuer une recherche en texte intégral sur la table d’interface MS_SAMPLE_EMPLOYEE dans Oracle E-Business Suite, vous devez maintenant créer une page de composants WebPart et ajouter un composant WebPart zone de recherche à celui-ci.  
  
#### <a name="to-add-the-search-box-web-part"></a>Pour ajouter le composant WebPart zone de recherche  
  
1.  Créer une page WebPart appelée **MS_SAMPLE_EMPLOYEE_Search**. Pour connaître les étapes de création d’une page Web, voir [scénario 1 : afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md) dans [scénario 1 : afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).  
  
2.  Dans la page MS_SAMPLE_EMPLOYEE_Search, cliquez sur **ajouter un composant WebPart**.  
  
3.  Dans le **ajouter des WebParts** boîte de dialogue le **recherche** section, sélectionnez le **zone de recherche** case à cocher, puis cliquez sur **ajouter**.  
  
     ![Ajouter le composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")  
  
4.  Le composant WebPart zone recherche est ajouté à la page MS_SAMPLE_EMPLOYEE_Search.  
  
     ![Composant WebPart zone de recherche](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer une application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
 [Scénario 1 : Afficher des données à l’aide du composant WebPart liste de données métiers](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)
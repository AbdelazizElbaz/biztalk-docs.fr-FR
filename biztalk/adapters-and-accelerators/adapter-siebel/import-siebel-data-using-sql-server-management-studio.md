---
title: "Importer des données Siebel à l’aide de SQL Server Management Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio, importing data by using
- how to, import data by using SQL Server Management Studio
ms.assetid: 67da7f7b-37ea-4a31-89ef-a9f6974ff976
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a17d3061721006c9e98517a7bf2bf7ab11d7052d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-siebel-data-using-sql-server-management-studio"></a>Importer des données Siebel à l’aide de SQL Server Management Studio
Cette section fournit des informations sur l’utilisation de SQL Server Management Studio pour importer des données à partir d’un système Siebel dans une base de données SQL Server. Il fournit également des instructions sur la façon de créer et exécuter un package SSIS pour importer ces données.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :  
  
-   Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] est installé sur l’ordinateur.  
  
-   SQL Server Business Intelligence Development Studio est installé sur l’ordinateur.  
  
## <a name="importing-data-by-using-sql-server-management-studio"></a>L’importation de données à l’aide de SQL Server Management Studio  
 Procédez comme suit pour importer des données à partir d’à l’aide du système Siebel [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SQL Server Management Studio.  
  
#### <a name="to-import-data-by-using-sql-server-management-studio"></a>Pour importer des données à l’aide de SQL Server Management Studio  
  
1.  Démarrez SQL Server Management Studio.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez les valeurs pour se connecter à une base de données SQL Server, puis cliquez sur **connexion**. Microsoft SQL Server Management Studio s’ouvre.  
  
3.  Dans l’Explorateur d’objets, développez le nom SQL Server, **bases de données**et avec le bouton droit de la base de données dans lequel vous exporterez les tables à partir du système Siebel. Dans le menu contextuel, pointez sur **tâches**, puis cliquez sur **importer des données**. Cela démarre le SQL Server Assistant Importation et exportation.  
  
4.  Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.  
  
5.  Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** la liste déroulante, sélectionnez **fournisseur de données .NET Framework pour Siebel eBusiness Applications**. Spécifier des valeurs pour les propriétés de connexion différentes pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] chaîne de connexion. Pour plus d’informations sur les propriétés de chaîne de connexion, consultez [les propriétés de fournisseur de données pour la chaîne de connexion Siebel](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).  
  
     Cliquez sur **Suivant**.  
  
6.  Dans le **choisir une Destination** boîte de dialogue :  
  
    1.  À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.  
  
    2.  À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de SQL Server.  
  
    3.  Sélectionnez un mode d'authentification.  
  
    4.  À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table Siebel.  
  
    5.  Cliquez sur **Suivant**.  
  
7.  Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** option.  
  
8.  Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).  
  
     Cliquez sur le **analyser** bouton pour valider la requête, cliquez sur **OK** dans la boîte de dialogue contextuelle, puis cliquez sur **suivant**.  
  
9. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination. La source est la requête que vous avez spécifié pour récupérer des données à partir de Siebel. La destination est la table qui sera créée dans la base de données SQL Server.  
  
10. L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table. Toutefois, vous pouvez modifier les mappages en fonction de vos besoins. Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.  
  
     ![Mappages de colonnes entre les tables Siebel et SQL](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")  
  
11. Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :  
  
    -   Modifier les noms de colonnes dans la table de destination.  
  
    -   Ignorer certaines colonnes de la table de destination.  
  
    -   Modifier le type de données pour les champs dans la table de destination.  
  
    -   Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.  
  
         Lorsque vous avez terminé, cliquez sur **OK**.  
  
12. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.  
  
13. Dans le **enregistrer et exécuter le Package** boîte de dialogue :  
  
    -   Sélectionnez le **exécuter immédiatement** case à cocher pour exécuter la requête.  
  
    -   Sélectionnez le **enregistrer le Package SSIS** case à cocher pour enregistrer la requête sous forme de package et de l’exécuter ultérieurement. Si vous avez choisi d’enregistrer le package, vous devez également spécifier si vous souhaitez enregistrer le package dans SQL Server ou le système de fichiers.  
  
    -   À partir de la **au niveau de protection du Package** liste déroulante, sélectionnez une protection au niveau du package et spécifiez les informations d’identification si nécessaire.  
  
    -   Cliquez sur **Suivant**.  
  
     Si vous avez choisi d’enregistrer le package, passez à l’étape suivante. Sinon, passez à l’étape 15.  
  
14. Dans le **enregistrer le Package SSIS** boîte de dialogue, spécifiez les éléments suivants :  
  
    -   Le nom du package  
  
    -   La description du package  
  
    -   Si vous choisissez d’enregistrer le package sur un serveur SQL Server, sélectionnez un serveur SQL Server à partir de la **nom du serveur** liste déroulante.  
  
    -   Si vous choisissez d’enregistrer le package sur le système de fichiers, spécifiez le nom et l’emplacement du fichier dans le **nom de fichier** zone de texte.  
  
         Lorsque vous avez terminé, cliquez sur **Suivant**.  
  
15. Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant s’effectuer, puis cliquez sur **Terminer**.  
  
16. Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de Siebel dans une table de base de données SQL Server. L’état de chaque tâche s’affiche dans l’Assistant.  
  
17. Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**. Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.  
  
## <a name="running-the-ssis-package"></a>L’exécution du Package SSIS  
 Si vous avez choisi d’enregistrer le package SSIS, vous pouvez exécuter pour récupérer les informations les plus récentes à partir du système Siebel. Cette section fournit des informations sur la façon d’exécuter le package si vous avez choisi à l’enregistrer dans le système de fichiers.  
  
#### <a name="to-run-the-package-from-windows-explorer"></a>Pour exécuter le package à partir de l’Explorateur Windows  
  
1.  À partir de **l’Explorateur Windows**, accédez à l’emplacement où vous avez enregistré le package et double-cliquez sur le package.  
  
2.  Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Exécuter**. Le **progression de l’exécution du Package** boîte de dialogue affiche la progression des tâches différentes.  
  
3.  Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.  
  
4.  Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Fermer**.  
  
 Pour plus d’informations sur l’exécution de packages, consultez « Exécution de Packages » à [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972). Pour les autres informations relatives aux packages SSIS, consultez « Package procédures rubriques (SSIS) » à [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).  
  
## <a name="verifying-the-results"></a>Vérification des résultats  
 Après l’exécution du package, vous devez vérifier les résultats en accédant à la base de données SQL Server à laquelle les données Siebel sont importées. L’exécution du package doit avoir créé une table dans la base de données de destination. Cette table doit être remplie avec les valeurs de la table Siebel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données pour Siebel avec SSIS](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)
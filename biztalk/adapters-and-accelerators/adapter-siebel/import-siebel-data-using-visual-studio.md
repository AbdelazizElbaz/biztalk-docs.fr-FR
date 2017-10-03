---
title: "Importer des données Siebel à l’aide de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- Data Provider for Siebel, importing Siebel data by using Visual Studio
ms.assetid: 33701361-eca2-4795-a5e0-78162a98e9ba
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0671459b39462422768e42e18bf16336a469f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-siebel-data-using-visual-studio"></a>Importer des données Siebel à l’aide de Visual Studio
Cette section fournit des informations sur l’utilisation de Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour importer des données à partir d’un système Siebel dans une base de données SQL Server. Il fournit également des instructions sur la façon de créer et exécuter un package SSIS pour importer ces données.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :  
  
-   Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] est installé sur l’ordinateur.  
  
-   Microsoft [!INCLUDE[vs2010](../../includes/vs2010-md.md)] est installé sur l’ordinateur.  
  
## <a name="importing-data-by-using-visual-studio"></a>L’importation de données à l’aide de Visual Studio  
 Procédez comme suit pour importer des données à l’aide de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
#### <a name="to-import-data-by-using-visual-studio"></a>Pour importer des données à l’aide de Visual Studio  
  
1.  Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créez un projet de Service d’intégration.  
  
2.  À partir de la **projet** menu, sélectionnez **SSIS Assistant Importation et exportation**. Cela démarre le SQL Server Assistant Importation et exportation.  
  
3.  Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.  
  
4.  Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour Siebel eBusiness Applications**. Spécifier des valeurs pour les propriétés de connexion différentes pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] chaîne de connexion. Pour plus d’informations sur les propriétés de chaîne de connexion, consultez [les propriétés de fournisseur de données pour la chaîne de connexion Siebel](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).  
  
     Cliquez sur **Suivant**.  
  
5.  Dans le **choisir une Destination** boîte de dialogue :  
  
    1.  À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.  
  
    2.  À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de SQL Server.  
  
    3.  Sélectionnez un mode d'authentification.  
  
    4.  À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table Siebel.  
  
    5.  Cliquez sur **Suivant**.  
  
6.  Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** option.  
  
7.  Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).  
  
8.  Pour valider la requête, cliquez sur le **analyser** et sur **OK** dans la boîte de dialogue contextuelle, puis cliquez sur **suivant**.  
  
9. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination. La source est la requête que vous avez spécifié pour récupérer des données à partir de Siebel. La destination sera la table qui sera créée dans la base de données SQL Server.  
  
10. L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table. Toutefois, vous pouvez modifier les mappages en fonction de vos besoins. Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.  
  
11. Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :  
  
    -   Modifier les noms de colonnes dans la table de destination.  
  
    -   Ignorer certaines colonnes de la table de destination.  
  
    -   Modifier le type de données pour les champs dans la table de destination.  
  
    -   Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.  
  
    -   Cliquez sur **OK**.  
  
     ![Mappages de colonnes entre les tables Siebel et SQL](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")  
  
12. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.  
  
13. Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant s’effectuer, puis cliquez sur **Terminer**.  
  
14. Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de Siebel dans une table de base de données SQL Server. L’état de chaque tâche s’affiche dans l’Assistant.  
  
15. Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**. Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.  
  
16. L’Assistant ajoute un package SSIS à votre projet de Service d’intégration. Enregistrez le projet de Service d’intégration.  
  
## <a name="running-the-ssis-package"></a>L’exécution du Package SSIS  
 Une fois que le package est créé dans un projet de Service d’intégration, vous pouvez l’exécuter pour importer des données à partir d’un système Siebel dans une base de données SQL Server. Procédez comme suit pour importer des données Siebel à l’exécution du package.  
  
#### <a name="to-run-the-package-from-visual-studio"></a>Pour exécuter le package à partir de Visual Studio  
  
1.  Accédez au package SSIS dans l’Explorateur de solutions.  
  
2.  Cliquez sur le nom du package, puis **exécuter le Package**.  
  
 Pour plus d’informations sur l’exécution de packages, consultez « Exécution de Packages » à [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972). Pour les autres informations relatives aux packages SSIS, consultez « Package procédures rubriques (SSIS) » à [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).  
  
## <a name="verifying-the-results"></a>Vérification des résultats  
 Après l’exécution du package, vous devez vérifier les résultats en vous connectant à SQL Server et en accédant à la base de données à laquelle les données Siebel sont importées. L’exécution du package doit avoir créé une table dans la base de données de destination. Cette table doit être remplie avec les valeurs de la table Siebel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données pour Siebel avec SSIS](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)
---
title: "Importer des données SAP à l’aide de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- importing SAP data, using Visual Studio
- Visual Studio, importing SAP data
ms.assetid: 70cce089-232d-4ab9-81bd-6b0d6f0097d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1295f763815872bacedf2262f7c022d6813bd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-visual-studio"></a>Importer des données SAP à l’aide de Visual Studio
Cette section fournit des informations sur la façon d’utiliser Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour importer des données à partir d’un système SAP dans une base de données SQL Server. Cette section fournit des instructions sur la création d’un package SSIS que vous pouvez exécuter pour importer des données. Cette section fournit également des informations sur la façon d’exécuter le package SSIS.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]est installé sur l’ordinateur.  
  
-   [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]est installé sur l’ordinateur.  
  
### <a name="to-import-data-using-visual-studio"></a>Pour importer des données à l’aide de Visual Studio  
  
1.  Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créez un projet de Service d’intégration.  
  
2.  À partir de la **projet** menu, sélectionnez **SSIS Assistant Importation et exportation**. Cela démarre le **SQL Server Assistant Importation et exportation**.  
  
3.  Lire les informations sur l’écran d’accueil et cliquez sur **suivant**.  
  
4.  Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour mySAP Business Suite**. La boîte de dialogue répertorie les paramètres de connexion pour se connecter à un système SAP. Une chaîne de connexion par défaut pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert :  
  
    -   Les paramètres de connexion pour un type de connexion. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les types de connexion A, B et D. Pour vous connecter à un système SAP, vous devez fournir les paramètres de connexion pour les *un* de ces types de connexion. Par exemple, pour le type de connexion A, vous devez fournir le nom de l’hôte d’application serveur et le numéro du système.  
  
    -   Les informations de connexion pour se connecter à un système SAP, telles que le nom d’utilisateur et mot de passe.  
  
     Pour plus d’informations sur la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [en savoir plus sur le fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
     Dans le **choisir une Source de données** boîte de dialogue, spécifiez :  
  
    -   Les paramètres de connexion pour n’importe quel type d’une seule connexion.  
  
    -   Les informations de connexion pour se connecter à un système SAP.  
  
    -   Si vous voulez activer le débogage de l’interface utilisateur graphique SAP.  
  
    -   Si vous souhaitez utiliser le suivi du Kit de développement logiciel RFC.  
  
     Cliquez sur **Suivant**.  
  
5.  Dans le **choisir une Destination** boîte de dialogue :  
  
    1.  À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.  
  
    2.  À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de serveur SQL.  
  
    3.  Sélectionnez un mode d'authentification.  
  
    4.  À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table SAP.  
  
    5.  Cliquez sur **Suivant**.  
  
6.  Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** , puis cliquez sur **suivant**.  
  
7.  Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).  
  
     Cliquez sur le **analyser** pour valider la requête et cliquez sur **OK** dans la boîte de dialogue contextuelle. Cliquez sur **Suivant**.  
  
8.  Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination. La source est la requête que vous avez spécifié pour récupérer des données à partir de SAP. La destination est la table qui sera créée dans la base de données SQL Server.  
  
9. L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table. Toutefois, vous pouvez modifier les mappages en fonction de vos besoins. Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.  
  
     ![Mappages de colonnes entre les tables SAP et SQL](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")  
  
10. Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :  
  
    -   Modifier les noms de colonnes dans la table de destination.  
  
    -   Ignorer certaines colonnes de la table de destination.  
  
    -   Modifier le type de données pour les champs dans la table de destination.  
  
    -   Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.  
  
    -   Cliquez sur **OK**.  
  
11. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.  
  
12. Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant effectuer, puis cliquez sur **Terminer**.  
  
13. Dans le **exécution de l’opération** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de SAP dans une table de base de données SQL Server. L’état de chaque tâche s’affiche dans l’Assistant.  
  
14. Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**. Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.  
  
15. L’Assistant ajoute un package SSIS à votre projet de Service d’intégration. Enregistrez le projet de Service d’intégration.  
  
## <a name="running-the-ssis-package"></a>L’exécution du Package SSIS  
 Une fois que le package est créé dans un projet de Service d’intégration, vous pouvez l’exécuter pour importer des données à partir d’un système SAP dans une base de données SQL Server. Procédez comme suit pour importer des données SAP à l’exécution du package.  
  
#### <a name="to-run-the-package-from-visual-studio"></a>Pour exécuter le package à partir de Visual Studio  
  
1.  Accédez au package SSIS dans l’Explorateur de solutions.  
  
2.  Cliquez sur le nom du package et sélectionnez **exécuter le Package**.  
  
 Pour plus d’informations sur l’exécution de packages, consultez [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972). Pour toutes les informations relatives aux packages SSIS, consultez [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).  
  
## <a name="verifying-the-results"></a>Vérification des résultats  
 Après l’exécution du package, vous devez vérifier les résultats en vous connectant à SQL Server et en accédant à la base de données à laquelle les données SAP sont importées. L’exécution du package doit avoir créé une table de base de données de destination et remplie avec les valeurs de la table SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données pour SAP avec SSIS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)
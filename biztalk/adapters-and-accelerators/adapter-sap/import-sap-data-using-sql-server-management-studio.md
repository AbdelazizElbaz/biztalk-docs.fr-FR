---
title: "Importer des données SAP à l’aide de SQL Server Management Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- SQL Server Management Studio, importing data
ms.assetid: c8151c6d-4b33-40fe-9b83-9bed27df9a99
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28981d2130e82a094e470de1e2b6904382be56b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-sql-server-management-studio"></a>Importer des données SAP à l’aide de SQL Server Management Studio
Cette section fournit des informations sur l’utilisation de SQL Server Management Studio pour importer des données à partir d’un système SAP dans une base de données SQL Server. Cette section fournit des instructions sur la création d’un package SSIS que vous pouvez exécuter pour importer des données. Cette section fournit également des informations sur la façon d’exécuter le package SSIS.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]est installé sur l’ordinateur.  
  
-   SQL Server Business Intelligence Development Studio est installé sur l’ordinateur.  
  
### <a name="to-import-data-using-sql-server-management-studio"></a>Pour importer des données à l’aide de SQL Server Management Studio  
  
1.  Démarrez SQL Server Management Studio.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez les valeurs pour vous connecter à une base de données SQL Server et cliquez sur **connexion**. Le **Microsoft SQL Server Management Studio** s’ouvre.  
  
3.  Dans le **l’Explorateur d’objets**, développez le nom SQL Server, **bases de données**et avec le bouton droit de la base de données dans lequel vous exporterez les tables à partir du système SAP. Dans le menu contextuel, pointez sur **tâches**, puis cliquez sur **importer des données**. Cela démarre le **SQL Server Assistant Importation et exportation**.  
  
4.  Lire les informations sur l’écran d’accueil et cliquez sur **suivant**.  
  
5.  Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour mySAP Business Suite**. La boîte de dialogue répertorie les paramètres de connexion pour se connecter à un système SAP. Une chaîne de connexion par défaut pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert :  
  
    -   Les paramètres de connexion pour un type de connexion. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les types de connexion A, B et D. Pour vous connecter à un système SAP, vous devez fournir les paramètres de connexion pour les *un* de ces types de connexion. Par exemple, pour le type de connexion A, vous devez fournir le nom de l’hôte d’application serveur et le numéro du système.  
  
    -   Les informations de connexion pour se connecter à un système SAP, telles que le nom d’utilisateur et mot de passe.  
  
     Pour plus d’informations sur la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [en savoir plus sur le fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
     Dans le **choisir une Source de données** boîte de dialogue, spécifiez :  
  
    -   Les paramètres de connexion pour n’importe quel type d’une seule connexion.  
  
    -   Les informations de connexion pour se connecter à un système SAP.  
  
    -   Si vous voulez activer le débogage de l’interface utilisateur graphique SAP.  
  
    -   Si vous souhaitez utiliser le suivi du Kit de développement logiciel RFC.  
  
     Cliquez sur **Suivant**.  
  
6.  Dans le **choisir une Destination** boîte de dialogue :  
  
    1.  À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.  
  
    2.  À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de serveur SQL.  
  
    3.  Sélectionnez un mode d'authentification.  
  
    4.  À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table SAP.  
  
    5.  Cliquez sur **Suivant**.  
  
7.  Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** , puis cliquez sur **suivant**.  
  
8.  Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server. Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une SAP instruction sélectionnez](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).  
  
     Cliquez sur le **analyser** pour valider la requête et cliquez sur **OK** dans la boîte de dialogue contextuelle. Cliquez sur **Suivant**.  
  
9. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination. La source est la requête que vous avez spécifié pour récupérer des données à partir de SAP. La destination est la table qui sera créée dans la base de données SQL Server.  
  
10. L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table. Toutefois, vous pouvez modifier les mappages en fonction de vos besoins. Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.  
  
     ![Mappages de colonnes entre les tables SAP et SQL](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")  
  
11. Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :  
  
    -   Modifier les noms de colonnes dans la table de destination.  
  
    -   Ignorer certaines colonnes de la table de destination.  
  
    -   Modifier le type de données pour les champs dans la table de destination.  
  
    -   Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.  
  
    -   Cliquez sur **OK**.  
  
12. Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.  
  
13. Dans le **enregistrer et exécuter le Package** boîte de dialogue  
  
    -   Sélectionnez le **exécuter immédiatement** case à cocher pour exécuter la requête.  
  
    -   Sélectionnez le **enregistrer le Package SSIS** case à cocher pour enregistrer la requête sous forme de package et de l’exécuter ultérieurement. Si vous avez choisi d’enregistrer le package, vous devez également spécifier si vous souhaitez enregistrer le package dans SQL Server ou le système de fichiers.  
  
    -   À partir de la **au niveau de protection du Package** liste déroulante, sélectionnez une protection au niveau du package et spécifiez les informations d’identification si nécessaire.  
  
    -   Cliquez sur **Suivant**.  
  
     Si vous avez choisi d’enregistrer le package, passez à l’étape suivante. Sinon, passez à l’étape 15.  
  
14. Dans le **enregistrer le Package SSIS** boîte de dialogue, spécifiez :  
  
    -   Nom du package  
  
    -   Description du package  
  
    -   Si vous choisissez d’enregistrer le package sur un serveur SQL server, sélectionnez un serveur SQL Server à partir de la **nom du serveur** liste déroulante.  
  
    -   Si vous choisissez d’enregistrer le package sur le système de fichiers, spécifiez le nom et l’emplacement du fichier dans le **nom de fichier** zone de texte.  
  
    -   Cliquez sur **Suivant**.  
  
15. Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant effectuer, puis cliquez sur **Terminer**.  
  
16. Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de SAP dans une table de base de données SQL Server. L’état de chaque tâche s’affiche dans l’Assistant.  
  
17. Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**. Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.  
  
## <a name="running-the-ssis-package"></a>L’exécution du Package SSIS  
 Si vous avez choisi d’enregistrer le package SSIS, vous pouvez exécuter pour récupérer les informations les plus récentes à partir du système SAP. Cette section fournit des informations sur la façon d’exécuter le package si vous avez choisi à l’enregistrer dans le système de fichiers.  
  
#### <a name="to-run-the-package-from-windows-explorer"></a>Pour exécuter le package à partir de l’Explorateur Windows  
  
1.  À partir de la **l’Explorateur Windows**, accédez à l’emplacement où vous avez enregistré le package et double-cliquez sur le package.  
  
2.  Sur le **utilitaire** boîte de dialogue, cliquez sur **Execute**.  
  
3.  Le **progression de l’exécution du Package** boîte de dialogue affiche la progression des tâches différentes.  
  
4.  Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.  
  
5.  Sur le **utilitaire** boîte de dialogue, cliquez sur **fermer**.  
  
 Pour plus d’informations sur l’exécution de packages, consultez [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972). Pour toutes les informations relatives aux packages SSIS, consultez [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).  
  
## <a name="verifying-the-results"></a>Vérification des résultats  
 Après l’exécution du package, vous devez vérifier les résultats en accédant à la base de données SQL Server à laquelle les données SAP sont importées. L’exécution du package doit avoir créé une table de base de données de destination et remplie avec les valeurs de la table SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du fournisseur de données pour SAP avec SSIS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)
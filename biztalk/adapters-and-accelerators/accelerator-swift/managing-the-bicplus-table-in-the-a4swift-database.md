---
title: "La gestion de la Table dans la base de données A4SWIFT Bicplus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), Bicplus table
- A4SWIFT database, Bicplus table
- Bicplus table
ms.assetid: a255cdea-5ed4-4481-97f1-8425877a76d6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a58396a9dd6627f2913da8e3845a99b17cf7698
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="managing-the-bicplus-table-in-the-a4swift-database"></a>La gestion de la Table Bicplus dans la base de données A4SWIFT
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]utilise une table d’entrées BIC pour effectuer la validation BIC. Cette table peut être la table de Bicplus dans les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données ou une table dans une base de données personnalisée.  
  
 Pour gérer cette table, vous devez le remplir avec les valeurs BIC de SWIFT. Si vous utilisez une base de données personnalisée, vous devez également exporter des vues SQL dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données dans la base de données personnalisé.  
  
## <a name="importing-bic-data-from-the-swift-bicplus-database"></a>L’importation des données BIC à partir de la base de données SWIFT Bicplus  
 Vous devez remplir la table des entrées BIC (la valeur par défaut ou la table personnalisée) avec les valeurs BIC de SWIFT. Les données de code SWIFT BIC seront disponibles dans un [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul ou dans une base de données Oracle qui est mis à jour tous les mois. Pour plus d’informations sur les données de code SWIFT BIC, accédez à [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  
  
 Si vous utilisez une base de données personnalisée, vous devez exporter des données BIC à partir de la base de données SWIFT Bicplus dans la base de données personnalisé. Il le faut  
  
 Vous pouvez importer des données depuis le code BIC [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul fournie par SWIFT dans la table Bicplus le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] de base de données, car elles sont compatibles. Si vous importez les données à partir de la feuille de calcul SWIFT non -[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] de base de données, assurez-vous que les champs et les colonnes de votre base de données, notamment la colonne BIC, sont compatibles avec la feuille de calcul SWIFT.  
  
 L’opération d’importation ne supprime pas les codes BIC non publiés lorsqu’il met à jour la table de destination avec les codes publiées dans la table SWIFT.  
  
 Les modifications apportées à la table Bicplus de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données sont enregistrées dans le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] fichier journal.  
  
#### <a name="to-import-bic-data-from-the-swift-bicplus-database"></a>Pour importer des données BIC à partir de la base de données SWIFT Bicplus  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointer vers la version inistalled de SQL Server, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la connexion de la boîte de dialogue, cliquez sur **connexion**.  
  
3.  Dans la fenêtre de Microsoft SQL Server Management Studio, développez le nœud de votre serveur, puis **bases de données**.  
  
4.  Avec le bouton droit **A4SWIFT**, pointez sur **tâches**, puis cliquez sur **importer des données**.  
  
5.  Sur l’importation de SQL Server et de la page d’accueil Assistant Exportation, cliquez sur **suivant**.  
  
6.  Sur le **choisir une Source de données** page, si vous importez des données BIC depuis le Bicplus SWIFT [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul, sélectionnez **Microsoft Excel** dans les **Source de données** zone de texte. Accédez à l’emplacement de la feuille de calcul et sélectionnez le nom de fichier de la feuille de calcul dans le **chemin d’accès du fichier Excel** zone de texte. Cliquez sur **Suivant**.  
  
     Si l’importation de données BIC à partir de la base de données Oracle, sélectionnez **le pilote Microsoft ODBC pour Oracle** dans les **Source de données** zone de texte. Entrez le serveur avec la base de données Oracle et le nom d’utilisateur et le mot de passe requis pour se connecter à ce serveur, puis cliquez sur **suivant**.  
  
7.  Sur le **choisir une Destination** page, vérifiez que **fournisseur Microsoft OLE DB pour SQL Server** est entré dans le **Destination** zone de texte et que **utilisation L’authentification Windows** est sélectionnée. Si vous remplissez la table Bicplus dans les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] de base de données, vérifiez que **A4SWIFT** est entré dans le **base de données** zone de texte. Si vous utilisez une base de données personnalisée, entrez le nom de cette base de données dans le **base de données** zone de texte. Cliquez sur **Suivant**.  
  
8.  Sur le **sélectionnez copie de la Table ou requête** page, vérifiez que **copier les données d’une ou plusieurs tables ou vues** est sélectionnée. Si vous avez besoin d’utiliser une requête pour spécifier les données, sélectionnez **écrire une requête pour spécifier les données à transférer**. Cliquez sur **Suivant**.  
  
9. Sur le **sélectionner des Tables Source et vues** , cliquez sur **Bicplus** dans les **Source** colonne, sélectionnez **Bicplus** dans le  **Destination** colonne, puis cliquez sur **suivant**.  
  
10. Sur le **enregistrer et exécuter le Package** page, entrez les informations de planification appropriée, puis cliquez sur **suivant**.  
  
11. Sur le **terminer l’Assistant** , examinez le résumé, puis cliquez sur **Terminer**.  
  
## <a name="importing-sql-views-from-the-a4swift-database-into-a-custom-database"></a>L’importation des vues SQL à partir de la base de données A4SWIFT dans une base de données personnalisé  
 Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] programme d’installation installe les deux vues SQL dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données. Une vue est de huit caractères BICs et l’autre est de 11 caractères BICs.  
  
 Si vous utilisez une base de données personnalisée au lieu du [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données, vous devez l’importation de ces vues SQL dans la base de données personnalisé. Pour faire en exécutant le script CreateBICViews.sql dans l’Analyseur de requêtes. Ce script se trouve dans \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT/Scripts.  
  
#### <a name="to-import-sql-views-from-the-a4swift-database-into-a-custom-database"></a>Pour importer des vues SQL à partir de la base de données A4SWIFT dans une base de données personnalisée  
  
1.  Dans l’Explorateur Windows, accédez à \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\Scripts. Double-cliquez sur **CreateBICViews.sql**.  
  
2.  Dans la connexion de la boîte de dialogue, cliquez sur **connexion**.  
  
3.  Dans la fenêtre de Microsoft SQL Server Management Studio, sélectionnez **A4SWIFT** dans la zone de texte de base de données.  
  
4.  Dans le volet de requête, si vous stockez les BICs dans une table qui est nommée autre que « Bicplus », recherchez **dbo. Bicplus** dans la vue **dbo. Bic11**et remplacez-le par le nom de la table appropriée. Faire de même pour la vue **dbo. Bic8**.  
  
5.  Si vous stockez dans une colonne autre que « BIC » nommé BICs, recherchez **BIC** dans les **sélectionnez**, **où**, et **ORDER BY** clauses, et Remplacez-le par le nom de colonne approprié.  
  
6.  Cliquez sur **Exécuter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Activation de la validation des codes BIC](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)
---
title: "Restauration de la base de données Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, restoring databases
- databases, restoring
ms.assetid: 291178c1-826e-49e0-a1d2-cbffee749659
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f77c242fe6477baac53b6a3e1b2fda545a7e4365
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-the-contoso-database"></a>Restauration de la base de données Contoso
Dans cette étape, vous utilisez SQL Server Management Studio pour exécuter un script SQL pour restaurer la base de données Contoso et les procédures stockées associées. Vous également remplir les tables de base de données avec les données préliminaires.  
  
### <a name="to-restore-the-contoso-database"></a>Pour restaurer la base de données Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la connexion de la boîte de dialogue, dans le **SQL Server** , cliquez sur **connexion**.  
  
    > [!NOTE]
    >  Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le volet de requête, copiez et collez le script SQL suivant dans la fenêtre de requête :  
  
    ```  
    CREATE DATABASE Contoso  
    GO  
    USE Contoso  
    GO  
    CREATE TABLE Products (  
    [ProductID] [varchar] (255) NOT NULL ,  
    [Name] [varchar] (255) NOT NULL ,  
    [Description] [varchar] (800) NULL ,  
    [Price] [money] NULL ,  
    [NumberAvailable] [int] NOT NULL   
    ) ON [PRIMARY]  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901234', 'ADM Line Card','',200.65,820 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901235','Analog Line Card','',165.24,769 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901236', 'Mapper/MUX','',150.54,948)  
    GO  
    CREATE TABLE StatusCodes (  
    [statusID] [int] NOT NULL ,  
    [statusCode] [nvarchar] (50) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    CREATE PROCEDURE GetInventoryForProductID  
    @ProductID varchar(255),  
    @NumberAvailable INT OUTPUT,  
    @Price MONEY OUTPUT  
    AS  
    SET NOCOUNT ON  
    SELECT @NumberAvailable = NumberAvailable,  
     @Price = Price  
    FROM Products  
    WHERE  ProductID = @ProductID  
    RETURN(0)  
    GO  
    CREATE PROCEDURE SP_GetInventoryForProductID  
    @ProductID varchar(255)  
    AS  
    SET NOCOUNT ON  
    SELECT *  
    FROM Products  
    WHERE ProductID = @ProductID  
    for xml auto  
    RETURN(0)  
    ```  
  
5.  Cliquez sur **Exécuter**.  
  
### <a name="to-set-permissions-on-the-contoso-database"></a>Pour définir les autorisations sur la base de données Contoso  
  
1.  Dans l’Explorateur d’objets de Microsoft SQL Server Management Studio, développez **bases de données**, développez le **Contoso** de base de données, puis développez **sécurité**. Cliquez avec le bouton droit sur **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.  
  
2.  L’utilisateur de base de données - nouvelle boîte de dialogue pour **nom de connexion**, cliquez sur le bouton de sélection.  
  
3.  Dans la boîte de dialogue Sélectionner la connexion, cliquez sur **Parcourir**.  
  
4.  Dans la boîte de dialogue objets rechercher, sélectionnez **utilisateurs d’applications BizTalk**, puis cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Sélectionner la connexion, cliquez sur **OK**.  
  
6.  L’utilisateur de base de données - nouvelle boîte de dialogue, dans le **l’appartenance au rôle de base de données** volet, sélectionnez **db_datareader** et **db_datawriter**. Pour **nom d’utilisateur**, entrez **utilisateurs d’applications BizTalk**. Cliquez sur **OK**.  
  
7.  Répétez les étapes 1 à 6 pour **utilisateurs d’hôtes BizTalk isolés**, en sélectionnant **db_datareader** et **db_datawriter** pour **l’appartenance au rôledebasededonnées**et en entrant **utilisateurs d’hôtes BizTalk isolés** pour **nom d’utilisateur**.  
  
8.  Répétez les étapes 1 à 6 pour **administrateurs de BizTalk Server**, en sélectionnant **db_owner** pour **l’appartenance au rôle de base de données**et en entrant **BizTalk Server Les administrateurs** pour **nom d’utilisateur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération et l’activation de certificats](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)
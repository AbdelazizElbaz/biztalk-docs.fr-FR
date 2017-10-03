---
title: "Étape 4 (sur site) : Créer la Table SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e253ac-8707-484f-8461-f098cc7ec7d8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6a6934a98ccd101003519486388b09504b5f0ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-on-premises-create-the-sql-server-table"></a>Étape 4 (sur site) : Créer la Table SQL Server
Dans le cadre du scénario d’entreprise, le message X12 message de commande envoyé par Contoso à Northwind doit être inséré dans un **SalesOrder** de table, si la quantité commandée est supérieure à 100. Cette rubrique fournit des instructions sur la façon de créer le **SalesOrder** table au sein d’une instance de base de données SQL Server qui est hébergée localement.  
  
### <a name="to-create-the-salesorder-table"></a>Pour créer la table SalesOrder  
  
1.  Ouvrez SQL Server Management Studio et exécutez la requête suivante sur la base de données dans laquelle vous souhaitez créer la table.  
  
2.  Exécutez la requête suivante pour créer le **SalesOrder** table :  
  
    ```  
    CREATE TABLE [dbo].[SalesOrder] (  
        [SalesOrderID] int IDENTITY(1,1) NOT NULL,  
        [PartNum] int  NOT NULL,  
        [DateRequested] datetime  NULL,  
        [CompanyCode] varchar(3)  NOT NULL,  
        [Qty] int  NOT NULL,  
        [UnitAskPrice] float  NULL,  
        [ShipDate] datetime  NOT NULL,  
        [SellToAddress] varchar(255)  NULL,  
        [BillToAddress] varchar(255)  NOT NULL,  
        [PartnerContact] varchar(128)  NULL,  
        [CustomerComments] varchar(500)  NULL,  
        [RFQStatuesId] smallint  NULL  
    );  
    GO  
    ```  
  
3.  Vérifiez que la table est créée dans la base de données cible.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)
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
# <a name="step-4-on-premises-create-the-sql-server-table"></a><span data-ttu-id="9f544-102">Étape 4 (sur site) : Créer la Table SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f544-102">Step 4 (On Premises): Create the SQL Server Table</span></span>
<span data-ttu-id="9f544-103">Dans le cadre du scénario d’entreprise, le message X12 message de commande envoyé par Contoso à Northwind doit être inséré dans un **SalesOrder** de table, si la quantité commandée est supérieure à 100.</span><span class="sxs-lookup"><span data-stu-id="9f544-103">As part of the business scenario, the message X12 sales order message sent by Contoso to Northwind must finally be inserted in a **SalesOrder** table, if the quantity ordered is greater than 100.</span></span> <span data-ttu-id="9f544-104">Cette rubrique fournit des instructions sur la façon de créer le **SalesOrder** table au sein d’une instance de base de données SQL Server qui est hébergée localement.</span><span class="sxs-lookup"><span data-stu-id="9f544-104">This topic provides instructions on how to create the **SalesOrder** table within a SQL Server database instance that is housed on-premises.</span></span>  
  
### <a name="to-create-the-salesorder-table"></a><span data-ttu-id="9f544-105">Pour créer la table SalesOrder</span><span class="sxs-lookup"><span data-stu-id="9f544-105">To create the SalesOrder table</span></span>  
  
1.  <span data-ttu-id="9f544-106">Ouvrez SQL Server Management Studio et exécutez la requête suivante sur la base de données dans laquelle vous souhaitez créer la table.</span><span class="sxs-lookup"><span data-stu-id="9f544-106">Open SQL Server Management Studio and run the following query against the database where you want to create the table.</span></span>  
  
2.  <span data-ttu-id="9f544-107">Exécutez la requête suivante pour créer le **SalesOrder** table :</span><span class="sxs-lookup"><span data-stu-id="9f544-107">Run the following query to create the **SalesOrder** table:</span></span>  
  
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
  
3.  <span data-ttu-id="9f544-108">Vérifiez que la table est créée dans la base de données cible.</span><span class="sxs-lookup"><span data-stu-id="9f544-108">Verify that the table is created in the target database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f544-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f544-109">See Also</span></span>  
 [<span data-ttu-id="9f544-110">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="9f544-110">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)
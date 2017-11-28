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
# <a name="restoring-the-contoso-database"></a><span data-ttu-id="110dd-102">Restauration de la base de données Contoso</span><span class="sxs-lookup"><span data-stu-id="110dd-102">Restoring the Contoso Database</span></span>
<span data-ttu-id="110dd-103">Dans cette étape, vous utilisez SQL Server Management Studio pour exécuter un script SQL pour restaurer la base de données Contoso et les procédures stockées associées.</span><span class="sxs-lookup"><span data-stu-id="110dd-103">In this step, you use SQL Server Management Studio to run a SQL script to restore the Contoso database and its associated stored procedures.</span></span> <span data-ttu-id="110dd-104">Vous également remplir les tables de base de données avec les données préliminaires.</span><span class="sxs-lookup"><span data-stu-id="110dd-104">You also populate the database tables with preliminary data.</span></span>  
  
### <a name="to-restore-the-contoso-database"></a><span data-ttu-id="110dd-105">Pour restaurer la base de données Contoso</span><span class="sxs-lookup"><span data-stu-id="110dd-105">To restore the Contoso database</span></span>  
  
1.  <span data-ttu-id="110dd-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="110dd-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="110dd-107">Dans la connexion de la boîte de dialogue, dans le **SQL Server** , cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="110dd-107">In the Connect to Server dialog box, in the **SQL Server** box, click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="110dd-108">Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="110dd-108">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="110dd-109">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="110dd-109">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="110dd-110">Dans le volet de requête, copiez et collez le script SQL suivant dans la fenêtre de requête :</span><span class="sxs-lookup"><span data-stu-id="110dd-110">In the Query pane, copy and paste the following SQL script into the Query window:</span></span>  
  
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
  
5.  <span data-ttu-id="110dd-111">Cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="110dd-111">Click **Execute**.</span></span>  
  
### <a name="to-set-permissions-on-the-contoso-database"></a><span data-ttu-id="110dd-112">Pour définir les autorisations sur la base de données Contoso</span><span class="sxs-lookup"><span data-stu-id="110dd-112">To set permissions on the Contoso database</span></span>  
  
1.  <span data-ttu-id="110dd-113">Dans l’Explorateur d’objets de Microsoft SQL Server Management Studio, développez **bases de données**, développez le **Contoso** de base de données, puis développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="110dd-113">In the Object Explorer of the Microsoft SQL Server Management Studio, expand **Databases**, expand the **Contoso** database, and then expand **Security**.</span></span> <span data-ttu-id="110dd-114">Cliquez avec le bouton droit sur **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="110dd-114">Right-click **Users**, and then click **New User**.</span></span>  
  
2.  <span data-ttu-id="110dd-115">L’utilisateur de base de données - nouvelle boîte de dialogue pour **nom de connexion**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="110dd-115">In the Database User - New dialog box, for **Login name**, click the ellipsis.</span></span>  
  
3.  <span data-ttu-id="110dd-116">Dans la boîte de dialogue Sélectionner la connexion, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="110dd-116">In the Select Login dialog box, click **Browse**.</span></span>  
  
4.  <span data-ttu-id="110dd-117">Dans la boîte de dialogue objets rechercher, sélectionnez **utilisateurs d’applications BizTalk**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="110dd-117">In the Browse for Objects dialog box, select **BizTalk Application Users**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="110dd-118">Dans la boîte de dialogue Sélectionner la connexion, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="110dd-118">In the Select Login dialog box, click **OK**.</span></span>  
  
6.  <span data-ttu-id="110dd-119">L’utilisateur de base de données - nouvelle boîte de dialogue, dans le **l’appartenance au rôle de base de données** volet, sélectionnez **db_datareader** et **db_datawriter**.</span><span class="sxs-lookup"><span data-stu-id="110dd-119">In the Database User - New dialog box, in the **Database role membership** pane, select **db_datareader** and **db_datawriter**.</span></span> <span data-ttu-id="110dd-120">Pour **nom d’utilisateur**, entrez **utilisateurs d’applications BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="110dd-120">For **User name**, enter **BizTalk Application Users**.</span></span> <span data-ttu-id="110dd-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="110dd-121">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="110dd-122">Répétez les étapes 1 à 6 pour **utilisateurs d’hôtes BizTalk isolés**, en sélectionnant **db_datareader** et **db_datawriter** pour **l’appartenance au rôledebasededonnées**et en entrant **utilisateurs d’hôtes BizTalk isolés** pour **nom d’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="110dd-122">Repeat steps 1 through 6 for **BizTalk Isolated Host Users**, selecting **db_datareader** and **db_datawriter** for **Database role membership**, and entering **BizTalk Isolated Host Users** for **User name**.</span></span>  
  
8.  <span data-ttu-id="110dd-123">Répétez les étapes 1 à 6 pour **administrateurs de BizTalk Server**, en sélectionnant **db_owner** pour **l’appartenance au rôle de base de données**et en entrant **BizTalk Server Les administrateurs** pour **nom d’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="110dd-123">Repeat steps 1 through 6 for **BizTalk Server Administrators**, selecting **db_owner** for **Database role membership**, and entering **BizTalk Server Administrators** for **User name**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110dd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="110dd-124">See Also</span></span>  
 [<span data-ttu-id="110dd-125">Génération et l’activation de certificats</span><span class="sxs-lookup"><span data-stu-id="110dd-125">Generating and Enabling Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)
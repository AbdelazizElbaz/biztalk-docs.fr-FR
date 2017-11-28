---
title: "Comment copier des Messages suivis dans la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, copying between servers
- MessageBox database, Tracking database
- Tracking database, linking servers
- MessageBox database, copying messages
- linking, servers
- Tracking database, archiving
- archiving [Tracking database], linking servers
- Tracking database, MessageBox database
- Tracking database, copying messages
- archiving [Tracking database], MessageBox database
- MessageBox database, linking servers
- MessageBox database, archiving
ms.assetid: 369e972a-efbe-4ad5-a68f-aa3bbfb9ad54
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23aaa8e3bea3405d51a18da1778d420550ad4584
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-tracked-messages-into-the-biztalk-tracking-database"></a><span data-ttu-id="0b6b5-102">Copie des messages suivis dans la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="0b6b5-102">How to Copy Tracked Messages into the BizTalk Tracking Database</span></span>
<span data-ttu-id="0b6b5-103">Les processus d'archivage et de purge pouvant utiliser ou modifier des bases de données présentes sur différents serveurs SQL Server, vous devez configurer des serveurs liés entre les instances de SQL Server concernées.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-103">The archiving and purging process potentially accesses and/or updates databases in different SQL servers, so you must set up linked servers between the involved SQL Server instances.</span></span> <span data-ttu-id="0b6b5-104">Vous pouvez copier directement les messages suivis à partir du serveur MessageBox (BizTalkMsgBoxDb) vers votre base de données des suivis BizTalk (BizTalkDTADb) par l'intermédiaire d'un serveur lié.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-104">You can directly copy tracked messages from the BizTalk MessageBox (BizTalkMsgBoxDb) database server to your BizTalk Tracking (BizTalkDTADb) database using a linked server.</span></span> <span data-ttu-id="0b6b5-105">Vous devez configurer des serveurs liés entre :</span><span class="sxs-lookup"><span data-stu-id="0b6b5-105">You must set up linked servers between:</span></span>  
  
-   <span data-ttu-id="0b6b5-106">chacune de vos bases de données MessageBox BizTalk (BizTalkMsgBoxDb) et la base de données des suivis BizTalk (BizTalkDTADb) ;</span><span class="sxs-lookup"><span data-stu-id="0b6b5-106">Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
-   <span data-ttu-id="0b6b5-107">la base de données des suivis BizTalk (BizTalkDTADb) et le serveur de validation pour la validation de l'archivage.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-107">The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.</span></span>  
  
-   <span data-ttu-id="0b6b5-108">Les comptes de service de l'Agent SQL Server sur l'ordinateur qui héberge la base de données MessageBox BizTalk (BizTalkMsgBoxDb) doivent disposer des autorisations db_datareader et db_datawriter pour la base de données des suivis BizTalk (BizTalkDTADb) qui réside sur le serveur lié.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-108">The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b6b5-109">Dans SQL Server Agent, vérifiez que la tâche de copie est exécutée sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-109">In SQL Server Agent, verify that the copy job runs without errors.</span></span> <span data-ttu-id="0b6b5-110">En cas d'erreurs, le transfert des données dans la base de données des suivis risque d'échouer.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-110">Otherwise, errors might prevent data from being moved to the tracking database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b6b5-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0b6b5-111">Prerequisites</span></span>  
 <span data-ttu-id="0b6b5-112">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-112">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-copy-tracked-messages-into-the-biztalk-tracking-database-sql-server-2008"></a><span data-ttu-id="0b6b5-113">Pour copier des messages suivis dans la base de données des suivis BizTalk (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="0b6b5-113">To copy tracked messages into the BizTalk Tracking database (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="0b6b5-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-114">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="0b6b5-115">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL server approprié.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-115">In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL server.</span></span>  
  
3.  <span data-ttu-id="0b6b5-116">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-116">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="0b6b5-117">Dans le volet détails, cliquez sur **TrackedMessages_Copy_BizTalkMsgBoxDb**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-117">In the details pane, right-click **TrackedMessages_Copy_BizTalkMsgBoxDb**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="0b6b5-118">Dans le **propriétés du travail - TrackedMessages_Copy_BizTalkMsgBoxDb** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-118">In the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="0b6b5-119">Sous **liste des étapes du travail**, cliquez sur **purger**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-119">Under **Job step list**, click **Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="0b6b5-120">Dans le **commande** zone, modifiez le serveur de suivi et les paramètres de noms de base de données approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-120">In the **Command** box, edit the tracking server and database names parameters as appropriate, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="0b6b5-121">Sur le **propriétés du travail - TrackedMessages_Copy_BizTalkMsgBoxDb** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-121">On the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **General**,select the **Enabled** check box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0b6b5-122">Les messages seront copiés de la base de données MessageBox  BizTalk  (BizTalkMsgBoxDb) vers la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="0b6b5-122">The messages will be copied from the BizTalk MessageBox (BizTalkMsgBoxDb) to the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b6b5-123">Si vous ajoutez une nouvelle base de données MessageBox, vous devez effectuer à nouveau cette procédure pour cette dernière.</span><span class="sxs-lookup"><span data-stu-id="0b6b5-123">If you add a new MessageBox database, you will need to perform this procedure again for the new MessageBox database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6b5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b6b5-124">See Also</span></span>  
 [<span data-ttu-id="0b6b5-125">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="0b6b5-125">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)
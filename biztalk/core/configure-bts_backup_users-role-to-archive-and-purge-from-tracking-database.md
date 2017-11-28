---
title: "Comment configurer le rôle BTS_BACKUP_USERS pour l’archivage et la purge des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, BTS_BACKUP_USERS role
- Tracking database, purging
- BTS_BACKUP_USERS role
- DTA Purge and Archive job
- archiving [Tracking database], BTS_BACKUP_USERS role
- archiving [Tracking database], DTA Purge and Archive job
- Tracking database, BTS_BACKUP_USERS role
- Tracking database, archiving
- purging, DTA Purge and Archive job
ms.assetid: c27aad2a-5788-4236-b5eb-ca730bf79851
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fb083f3755259ab2176541213d1637ce872c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="ef8cb-102">Configuration du rôle BTS_BACKUP_USERS pour l'archivage et la purge des données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="ef8cb-102">How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="ef8cb-103">Le travail de purge et d'archivage de la base de données des suivis (BizTAlkDTADb) s'exécute normalement en utilisant les informations d'identification de l'utilisateur du compte de service SQL Server Agent connecté.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-103">The DTA Purge and Archive (BizTAlkDTADb) job normally runs using the credentials of the logged-on SQL Server Agent service account user.</span></span> <span data-ttu-id="ef8cb-104">Pour renforcer la sécurité, vous pouvez toutefois le configurer afin qu'il s'exécute en utilisant les informations d'identification d'un compte membre du rôle BTS_BACKUP_USERS.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-104">For added security, however, you can configure the DTA Purge and Archive (BizTalkDTADb) job to run using the credentials of an account which is a member of the BTS_BACKUP_USERS role.</span></span> <span data-ttu-id="ef8cb-105">Cela permet d'exécuter les travaux SQL Server Agent sous des comptes disposant d'autorisations essentielles et évite de devoir octroyer des privilèges plus importants.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-105">This helps to prevent elevation of privileges by running SQL Server Agent jobs under accounts with essential permissions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef8cb-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ef8cb-106">Prerequisites</span></span>  
 <span data-ttu-id="ef8cb-107">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-107">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="ef8cb-108">Pour configurer le rôle BTS_BACKUP_USERS pour l'archivage et la purge des données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="ef8cb-108">To configure the BTS_BACKUP_USERS role for archiving and purging data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="ef8cb-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-109">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="ef8cb-110">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server approprié.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-110">In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
3.  <span data-ttu-id="ef8cb-111">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **BizTalkDTADb**, double-cliquez sur **sécurité**, double-cliquez sur **rôles**, et puis double-cliquez sur **des rôles de base de données**.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-111">In **Microsoft SQL Server Management Studio**, double-click **BizTalkDTADb**, double-click **Security**, double-click **Roles**, and then double-click **Database Roles**.</span></span>  
  
4.  <span data-ttu-id="ef8cb-112">Dans le **détails de l’Explorateur d’objets** volet, double-cliquez sur **BTS_BACKUP_USERS**.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-112">In the **Object Explorer Details** pane, double-click **BTS_BACKUP_USERS**.</span></span>  
  
5.  <span data-ttu-id="ef8cb-113">Dans le **propriétés du rôle de base de données – BTS_BACKUP_USERS** boîte de dialogue **membres de ce rôle**, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-113">In the **Database Role Properties – BTS_BACKUP_USERS** dialog box, under **Members of this role**, click **Add**.</span></span>  
  
6.  <span data-ttu-id="ef8cb-114">Dans le **sélectionner un utilisateur de base de données ou rôle** boîte de dialogue, entrez un compte d’utilisateur avec les informations d’identification du Service SQL Server Agent, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef8cb-114">In the **Select Database User or Role** dialog box, enter a user account with SQL Server Agent Service credentials, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8cb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef8cb-115">See Also</span></span>  
 [<span data-ttu-id="ef8cb-116">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="ef8cb-116">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)
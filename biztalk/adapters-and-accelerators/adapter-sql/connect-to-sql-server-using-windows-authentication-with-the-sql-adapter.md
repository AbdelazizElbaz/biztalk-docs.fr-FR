---
title: "Se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45c54b2a-e056-496f-9f10-f19b6a3ca1a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db7d0cbe07155d09085091d995b524b3058c0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-using-windows-authentication-with-the-sql-adapter"></a><span data-ttu-id="4585b-102">Se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="4585b-102">Connect to SQL Server using Windows Authentication with the SQL adapter</span></span>
<span data-ttu-id="4585b-103">Le [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4585b-103">The [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] enables adapter clients to use Windows Authentication to establish a connection with SQL Server.</span></span> <span data-ttu-id="4585b-104">Pour utiliser l’authentification Windows, les clients de l’adaptateur doivent entrer un nom d’utilisateur vide et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4585b-104">To use Windows Authentication, adapter clients must enter an empty user name and password.</span></span> 

<span data-ttu-id="4585b-105">Pour vous connecter à SQL Server à l’aide de l’authentification Windows dans Visual Studio, consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).</span><span class="sxs-lookup"><span data-stu-id="4585b-105">To connect to SQL Server using Windows Authentication within Visual Studio, see [Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).</span></span>  
  
 <span data-ttu-id="4585b-106">Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à SQL Server, activez l’authentification Windows pour l’utilisateur sur l’ordinateur exécutant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4585b-106">To enable adapter clients to use Windows Authentication to connect to SQL Server, enable Windows Authentication for the user on the computer running SQL Server.</span></span>  

> [!TIP]
> <span data-ttu-id="4585b-107">Si SQL Server Management Studio n’est pas installé sur votre serveur SQL Server, vous pouvez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)et l’installer.</span><span class="sxs-lookup"><span data-stu-id="4585b-107">If SQL Server Management Studio is not installed on your SQL Server, you can [Download SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms), and install it.</span></span> 
 
## <a name="add-the-user-in-sql-server"></a><span data-ttu-id="4585b-108">Ajoutez l’utilisateur dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="4585b-108">Add the user in SQL Server</span></span>  
  
1.  <span data-ttu-id="4585b-109">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="4585b-109">Open SQL Server Management Studio.</span></span> <span data-ttu-id="4585b-110">Dans **se connecter au serveur**, sélectionnez **moteur de base de données**, entrez votre SQL **nom du serveur**, puis entrez les informations d’identification d’administrateur pour se connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="4585b-110">In **Connect to Server**, select **Database Engine**, enter your SQL **Server name**, and enter administrator credentials to connect to the server.</span></span>  

    <span data-ttu-id="4585b-111">Sélectionnez **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="4585b-111">Select **Connect**.</span></span>
  
2.  <span data-ttu-id="4585b-112">Dans **l’Explorateur d’objets**, développez le serveur SQL Server, **sécurité**, avec le bouton droit **connexions**, puis sélectionnez **nouvelle connexion**.</span><span class="sxs-lookup"><span data-stu-id="4585b-112">In **Object Explorer**, expand the SQL Server, expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
3.  <span data-ttu-id="4585b-113">Pour le **nom de connexion**, entrez le nom d’utilisateur Windows dans le `domain\username` format.</span><span class="sxs-lookup"><span data-stu-id="4585b-113">For the **Login name**, enter the Windows user name in the `domain\username` format.</span></span>  

    > [!NOTE]
    >* <span data-ttu-id="4585b-114">Lorsque vous utilisez cet adaptateur avec BizTalk, le nom de connexion que vous entrez, est l’identité du compte de l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="4585b-114">When using this adapter with BizTalk, then the login name you enter, is the identity of the host instance account.</span></span>  
    >
    >* <span data-ttu-id="4585b-115">Lorsque vous utilisez cet adaptateur dans le code .NET, le nom de connexion que vous entrez, est l’identité de ce processus.</span><span class="sxs-lookup"><span data-stu-id="4585b-115">When using this adapter in .NET code, then the login name you enter, is the identity for that process.</span></span>
  
4.  <span data-ttu-id="4585b-116">Sélectionnez **mappage de l’utilisateur** (volet gauche).</span><span class="sxs-lookup"><span data-stu-id="4585b-116">Select **User Mapping** (left pane).</span></span> <span data-ttu-id="4585b-117">Sélectionnez une base de données à associer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4585b-117">Select a database to associate with the user.</span></span> <span data-ttu-id="4585b-118">Un utilisateur BizTalk doit être associé à des bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="4585b-118">A typical BizTalk user should be associated with the following databases:</span></span> 

* <span data-ttu-id="4585b-119">BizTalkDTADb</span><span class="sxs-lookup"><span data-stu-id="4585b-119">BizTalkDTADb</span></span>
* <span data-ttu-id="4585b-120">BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="4585b-120">BizTalkMgmtDb</span></span>
* <span data-ttu-id="4585b-121">BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="4585b-121">BizTalkMsgBoxDb</span></span>
* <span data-ttu-id="4585b-122">BTAHL7</span><span class="sxs-lookup"><span data-stu-id="4585b-122">BTAHL7</span></span>
* <span data-ttu-id="4585b-123">SSODB</span><span class="sxs-lookup"><span data-stu-id="4585b-123">SSODB</span></span>

5. <span data-ttu-id="4585b-124">Dans le **appartenance au rôle de la base de données** boîte, sélectionnez **db_owner** pour toutes les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4585b-124">In the **Database role membership for** box, select **db_owner** for all the BizTalk databases.</span></span>  

    > [!NOTE]
    > <span data-ttu-id="4585b-125">[Rôles de serveur et base de données dans SQL Server](https://msdn.microsoft.com/library/bb669065.aspx) fournit de bonnes informations sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="4585b-125">[Server and Database Roles in SQL Server](https://msdn.microsoft.com/library/bb669065.aspx) provides good info on the roles.</span></span> 
  
6.  <span data-ttu-id="4585b-126">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="4585b-126">Select **OK** to save your changes.</span></span>
  
 <span data-ttu-id="4585b-127">Une fois que vous avez ajouté l’utilisateur, l’utilisateur peut se connecter et s’authentifier auprès de SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], l’enregistrement avec un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4585b-127">After you have added the user, the user can connect and authenticate to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], logging in with a blank username and password.</span></span>  



## <a name="see-also"></a><span data-ttu-id="4585b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4585b-128">See Also</span></span>  
 [<span data-ttu-id="4585b-129">Créer une connexion à SQL Server</span><span class="sxs-lookup"><span data-stu-id="4585b-129">Create a connection to SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)
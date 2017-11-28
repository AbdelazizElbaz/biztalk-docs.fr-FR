---
title: Comment sauvegarder et restaurer les connexions SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 847c3a3d-0d97-415b-893e-4ba173085bae
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54fa6a51a27f82add8a96c613e36f5ed7ce88e87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-server-logins"></a><span data-ttu-id="c2a95-102">Sauvegarde et restauration des comptes de connexion SQL Server</span><span class="sxs-lookup"><span data-stu-id="c2a95-102">How to Back Up and Restore SQL Server Logins</span></span>
<span data-ttu-id="c2a95-103">Sauvegarder et restaurer les connexions SQL Server associés à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c2a95-103">Back up and restore SQL Server logins associated with BizTalk Server.</span></span>  
  
## <a name="biztalk-server-sql-server-security-logins"></a><span data-ttu-id="c2a95-104">Comptes de connexion de sécurité SQL Server de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c2a95-104">BizTalk Server SQL Server Security Logins</span></span>  
 <span data-ttu-id="c2a95-105">Les comptes de connexion de sécurité SQL Server répertoriés ci-dessous sont associés à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c2a95-105">The SQL Server security logins listed below are associated with BizTalk Server.</span></span> <span data-ttu-id="c2a95-106">D'autres comptes de connexion peuvent être associés aux applications BizTalk Server que vous avez créées.</span><span class="sxs-lookup"><span data-stu-id="c2a95-106">You may have additional logins associated with the BizTalk Server applications you have created.</span></span> <span data-ttu-id="c2a95-107">Vous devez sauvegarder les comptes de connexion et les restaurer lors du déplacement des bases de données BizTalk Server vers un nouveau serveur ou une nouvelle instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c2a95-107">You need to back up the logins and restore them when moving the BizTalk Server databases to a new server or new instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="c2a95-108">Utilisateurs d'applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="c2a95-108">BizTalk Application Users</span></span>  
  
-   <span data-ttu-id="c2a95-109">Utilisateurs d'hôtes BizTalk isolés</span><span class="sxs-lookup"><span data-stu-id="c2a95-109">BizTalk Isolated Host Users</span></span>  
  
-   <span data-ttu-id="c2a95-110">Administrateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c2a95-110">BizTalk Server Administrators</span></span>  
  
-   <span data-ttu-id="c2a95-111">Opérateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c2a95-111">BizTalk Server Operators</span></span>  
  
-   <span data-ttu-id="c2a95-112">Administrateurs SSO</span><span class="sxs-lookup"><span data-stu-id="c2a95-112">SSO Administrators</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="c2a95-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c2a95-113">Prerequisites</span></span>  
<span data-ttu-id="c2a95-114">Vous devez être un membre de la **administrateurs** rôle de sécurité sur le serveur SQL où vous sauvegardez et restaurez les connexions.</span><span class="sxs-lookup"><span data-stu-id="c2a95-114">You must be a member of the **Administrators** security role on the SQL Server where you backup and restore the logins.</span></span>  
  
## <a name="back-up-a-login-using-a-script"></a><span data-ttu-id="c2a95-115">Sauvegarder un compte de connexion à l’aide d’un script</span><span class="sxs-lookup"><span data-stu-id="c2a95-115">Back up a login using a script</span></span>  
  
1.  <span data-ttu-id="c2a95-116">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="c2a95-116">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c2a95-117">Développez **sécurité**, développez la liste des **connexions**.</span><span class="sxs-lookup"><span data-stu-id="c2a95-117">Expand **Security**, and expand the list of **Logins**.</span></span>  
  
3.  <span data-ttu-id="c2a95-118">Avec le bouton droit de la connexion que vous souhaitez créer un script de sauvegarde, puis **Script de la connexion en tant que**.</span><span class="sxs-lookup"><span data-stu-id="c2a95-118">Right-click the login you want to create a backup script for, and then select **Script Login as**.</span></span>  
  
4.  <span data-ttu-id="c2a95-119">Sélectionnez **CREATE To**, puis sélectionnez une des **nouvelle fenêtre d’éditeur de requête**, **fichier**, ou **Presse-papiers** pour sélectionner une destination pour le script.</span><span class="sxs-lookup"><span data-stu-id="c2a95-119">Select **CREATE To**, and then select one of **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script.</span></span> <span data-ttu-id="c2a95-120">En règle générale, la destination est un fichier avec un **.sql** extension.</span><span class="sxs-lookup"><span data-stu-id="c2a95-120">Typically, the destination is a file with a **.sql** extension.</span></span>  
  
5.  <span data-ttu-id="c2a95-121">Répétez cette procédure depuis l'étape 3 pour chaque compte de connexion pour lequel créer un script.</span><span class="sxs-lookup"><span data-stu-id="c2a95-121">Repeat this procedure from Step 3 for each login you want to script.</span></span> <span data-ttu-id="c2a95-122">Consultez la liste des comptes de connexion liés à BizTalk Server pour identifier ceux pour lesquels créer un script.</span><span class="sxs-lookup"><span data-stu-id="c2a95-122">Refer to the list of BizTalk Server related logins to determine which logins you need to script.</span></span>  
  
## <a name="restore-a-login-from-a-script"></a><span data-ttu-id="c2a95-123">Restaurer un compte de connexion à partir d’un script</span><span class="sxs-lookup"><span data-stu-id="c2a95-123">Restore a login from a script</span></span>  
  
1.  <span data-ttu-id="c2a95-124">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="c2a95-124">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c2a95-125">Sur le **fichier** menu, **ouvrir** le fichier qui contient la connexion sous forme de script.</span><span class="sxs-lookup"><span data-stu-id="c2a95-125">On the **File** menu, **Open** the file containing the scripted login.</span></span>  
  
3.  <span data-ttu-id="c2a95-126">Exécutez le script pour créer le compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2a95-126">Execute the script to create the login.</span></span>
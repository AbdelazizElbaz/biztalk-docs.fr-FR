---
title: "Comment gérer le groupe d’administrateurs BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Administrators group, user accounts
- BizTalk Administrators group
- user accounts, BizTalk Administrators group
- Windows Management Instrumentation (WMI), administering
- BizTalk Administrators group, privileges
- security, BizTalk Administrators group
- Administration Console [BizTalk Server], security
- Administration Console [BizTalk Server], administering
- BizTalk Administrators group, about BizTalk Administrators group
ms.assetid: 60ea689b-0b93-4fcc-b49c-6436e7be473f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe92c9c43ccef242d8c14b5f1aa48e0b1a8d852
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-biztalk-server-administrators-group"></a><span data-ttu-id="bfc26-102">Gestion des groupes Administrateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bfc26-102">How to Manage the BizTalk Server Administrators Group</span></span>
<span data-ttu-id="bfc26-103">Le groupe Administrateurs BizTalk Server dispose des privilèges minimaux requis pour exécuter les tâches d'administration.</span><span class="sxs-lookup"><span data-stu-id="bfc26-103">The BizTalk Server Administrators group has the fewest privileges necessary to perform administrative tasks.</span></span> <span data-ttu-id="bfc26-104">Vous pouvez ajouter des utilisateurs au groupe Administrateurs BizTalk Server pour leur permettre d'effectuer des tâches d'administration à l'aide de la console Administration de BizTalk Server ou du fournisseur WMI.</span><span class="sxs-lookup"><span data-stu-id="bfc26-104">You add users to the BizTalk Server Administrators group so that they can perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider.</span></span> <span data-ttu-id="bfc26-105">Vous pouvez également supprimer des utilisateurs du groupe Administrateurs BizTalk Server lorsque ceux-ci n'ont plus besoin d'effectuer des tâches d'administration à l'aide de la console Administration de BizTalk Server ou du fournisseur WMI.</span><span class="sxs-lookup"><span data-stu-id="bfc26-105">You also remove users from the BizTalk Server Administrators group when they no longer need to perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bfc26-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bfc26-106">Prerequisites</span></span>  
 <span data-ttu-id="bfc26-107">Vous devez être membre du groupe Administrateurs ou Administrateurs de domaine pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="bfc26-107">You must be a member of the Administrators or Domain Admins group to perform this procedure.</span></span>  
  
### <a name="to-add-users-to-the-local-biztalk-server-administrators-group"></a><span data-ttu-id="bfc26-108">Pour ajouter des utilisateurs au groupe Administrateurs BizTalk Server local</span><span class="sxs-lookup"><span data-stu-id="bfc26-108">To add users to the local BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="bfc26-109">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-109">Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="bfc26-110">Développez **Outils système**, développez **utilisateurs et groupes locaux**, puis cliquez sur le **groupes** dossier.</span><span class="sxs-lookup"><span data-stu-id="bfc26-110">Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder.</span></span> <span data-ttu-id="bfc26-111">Le contenu du dossier apparaît dans le volet Détails.</span><span class="sxs-lookup"><span data-stu-id="bfc26-111">The folder contents appear in the details pane.</span></span>  
  
3.  <span data-ttu-id="bfc26-112">Dans le volet détails, cliquez sur **administrateurs de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-112">In the details pane, click **BizTalk Server Administrators**.</span></span>  
  
4.  <span data-ttu-id="bfc26-113">Sur le **Action** menu, pointez sur **toutes les tâches**, puis cliquez sur **ajouter au groupe**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-113">On the **Action** menu, point to **All Tasks**, and then click **Add to Group**.</span></span>  
  
5.  <span data-ttu-id="bfc26-114">Dans le **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-114">In the **BizTalk Server Administrators Properties** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="bfc26-115">Dans le **Regarder dans** , sélectionnez le nom de votre ordinateur ou de domaine.</span><span class="sxs-lookup"><span data-stu-id="bfc26-115">In the **Look in** list, select your domain or computer name.</span></span>  
  
7.  <span data-ttu-id="bfc26-116">Dans la liste qui contient les utilisateurs et les ordinateurs associés au domaine ou l’ordinateur que vous avez sélectionné à l’étape 6, sélectionnez le compte d’utilisateur à ajouter, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-116">In the list that contains the users and computers associated with the domain or computer you selected in step 6, select the user account to add, click **Add**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="bfc26-117">Cliquez sur **OK** pour fermer la **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bfc26-117">Click **OK** to close the **BizTalk Server Administrators Properties** dialog box.</span></span>  
  
### <a name="to-remove-users-from-local-the-biztalk-server-administrators-group"></a><span data-ttu-id="bfc26-118">Pour supprimer des utilisateurs du groupe Administrateurs BizTalk Server local</span><span class="sxs-lookup"><span data-stu-id="bfc26-118">To remove users from local the BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="bfc26-119">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-119">Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="bfc26-120">Développez **Outils système**, développez **utilisateurs et groupes locaux**, puis cliquez sur le **groupes** dossier.</span><span class="sxs-lookup"><span data-stu-id="bfc26-120">Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder.</span></span> <span data-ttu-id="bfc26-121">Le contenu du dossier apparaît dans le volet Détails.</span><span class="sxs-lookup"><span data-stu-id="bfc26-121">The folder contents appear in the details pane.</span></span>  
  
3.  <span data-ttu-id="bfc26-122">Dans le volet détails, cliquez sur **administrateurs de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-122">In the details pane, click **BizTalk Server Administrators**.</span></span>  
  
4.  <span data-ttu-id="bfc26-123">Sur le **Action** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-123">On the **Action** menu, click **Properties**.</span></span>  
  
5.  <span data-ttu-id="bfc26-124">Dans le **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue, sélectionnez le compte d’utilisateur à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-124">In the **BizTalk Server Administrators Properties** dialog box, select the user account you want to remove, and then click **Remove**.</span></span>  
  
6.  <span data-ttu-id="bfc26-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-125">Click **OK**.</span></span>  
  
### <a name="to-add-users-to-the-domain-biztalk-server-administrators-group"></a><span data-ttu-id="bfc26-126">Pour ajouter des utilisateurs au groupe Administrateurs BizTalk Server du domaine</span><span class="sxs-lookup"><span data-stu-id="bfc26-126">To add users to the domain BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="bfc26-127">Ouvrez une session sur le contrôleur de domaine dans lequel les bases de données SQL Server sont regroupées à l'aide du compte Administrateurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="bfc26-127">Log on to the domain controller where the SQL Server databases are joined by using the Domain Admins account.</span></span>  
  
2.  <span data-ttu-id="bfc26-128">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers** à Démarrer le **Active Directory Users and Computers** console.</span><span class="sxs-lookup"><span data-stu-id="bfc26-128">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.</span></span>  
  
    1.  <span data-ttu-id="bfc26-129">Dans l'arborescence de la console, cliquez sur le dossier contenant le groupe Administrateurs BizTalk Server auquel ajouter un membre.</span><span class="sxs-lookup"><span data-stu-id="bfc26-129">In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.</span></span>  
  
    2.  <span data-ttu-id="bfc26-130">Dans le volet de détails, cliquez sur le groupe d’administrateurs BizTalk Server, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-130">In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="bfc26-131">Sur le **membres** , cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-131">On the **Members** tab, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="bfc26-132">Dans **Entrez les noms des objets à sélectionner**, tapez le nom de l’utilisateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-132">In **Enter the object names to select**, type the name of the user, and then click **OK**.</span></span>  
  
### <a name="to-remove-users-from-the-domain-biztalk-server-administrators-group"></a><span data-ttu-id="bfc26-133">Pour supprimer des utilisateurs du groupe Administrateurs BizTalk Server du domaine</span><span class="sxs-lookup"><span data-stu-id="bfc26-133">To remove users from the domain BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="bfc26-134">Ouvrez une session sur le contrôleur de domaine dans lequel les bases de données SQL sont regroupées à l'aide du compte Administrateurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="bfc26-134">Log on to the domain controller where SQL databases are joined using the Domain Admins account.</span></span>  
  
2.  <span data-ttu-id="bfc26-135">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers** à Démarrer le **Active Directory Users and Computers** console.</span><span class="sxs-lookup"><span data-stu-id="bfc26-135">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.</span></span>  
  
    1.  <span data-ttu-id="bfc26-136">Dans l'arborescence de la console, cliquez sur le dossier contenant le groupe Administrateurs BizTalk Server auquel ajouter un membre.</span><span class="sxs-lookup"><span data-stu-id="bfc26-136">In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.</span></span>  
  
    2.  <span data-ttu-id="bfc26-137">Dans le volet de détails, cliquez sur le groupe d’administrateurs BizTalk Server, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-137">In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="bfc26-138">Sur le **membres** , cliquez sur le membre que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-138">On the **Members** tab, click the member you want to remove, and then click **Remove**.</span></span>  
  
    4.  <span data-ttu-id="bfc26-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfc26-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc26-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfc26-140">See Also</span></span>  
 <span data-ttu-id="bfc26-141">[Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="bfc26-141">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 <span data-ttu-id="bfc26-142">[Gestion des hôtes et des comptes de Service](../core/managing-hosts-and-service-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="bfc26-142">[Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md) </span></span>  
 <span data-ttu-id="bfc26-143">[Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="bfc26-143">[Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md) </span></span>  
 <span data-ttu-id="bfc26-144">[Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="bfc26-144">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="bfc26-145">La gestion des comptes d’utilisateurs et groupes Windows</span><span class="sxs-lookup"><span data-stu-id="bfc26-145">Managing Windows Groups and User Accounts</span></span>](../core/managing-windows-groups-and-user-accounts.md)
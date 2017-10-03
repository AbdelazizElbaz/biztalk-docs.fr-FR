---
title: "Meilleures pratiques pour sécuriser les adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, security
- best practices, adapters
- adapters, permissions
- security, adapters
- permissions, adapters
- best practices, security
- adapters, best practices
ms.assetid: 004e1a01-b316-4eee-967f-5a806431de2b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86abbba06e851b9b289b29cd7fbbf01b3af292a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-securing-adapters"></a><span data-ttu-id="18a68-102">Méthodes conseillées pour sécuriser les adaptateurs</span><span class="sxs-lookup"><span data-stu-id="18a68-102">Best Practices for Securing Adapters</span></span>
<span data-ttu-id="18a68-103">Cette rubrique fournit une liste des meilleures pratiques pour la sécurité des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="18a68-103">This topic provides a list of best practices for adapter security.</span></span>  
  
 <span data-ttu-id="18a68-104">**N’installez pas les adaptateurs non approuvés sur votre ordinateur ; utiliser uniquement certifiés partenaires.**</span><span class="sxs-lookup"><span data-stu-id="18a68-104">**Do not install untrusted adapters on your computer; use only certified adapter development partners.**</span></span>  
  
 <span data-ttu-id="18a68-105">**Ne stockez pas les données sensibles dans le schéma de l’adaptateur par défaut.**</span><span class="sxs-lookup"><span data-stu-id="18a68-105">**Do not store sensitive customer data in the default adapter schema.**</span></span>  
  
 <span data-ttu-id="18a68-106">Vous devez configurer le nom d'utilisateur et le mot de passe uniquement après avoir déployé un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="18a68-106">You should configure the user name and password information only after you deploy an adapter.</span></span> <span data-ttu-id="18a68-107">Cela garantit que les informations sont bien stockées dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="18a68-107">This ensures that the information gets stored in the SSO database.</span></span> <span data-ttu-id="18a68-108">Pour plus d’informations sur la base de données SSO, consultez [à l’aide de l’authentification unique](../core/using-sso.md).</span><span class="sxs-lookup"><span data-stu-id="18a68-108">For more information about the SSO database, see [Using SSO](../core/using-sso.md).</span></span>  
  
 <span data-ttu-id="18a68-109">**Accordez les autorisations suivantes sur les dossiers partagés qui sont utilisées pour récupérer et supprimer des fichiers à l’aide des adaptateurs File et EDI (le dossier de réception et le dossier d’envoi) :**</span><span class="sxs-lookup"><span data-stu-id="18a68-109">**Grant the following permissions on the shared folders (the Receive folder and Send folder) that are used to pick up and drop files using the File and EDI adapters:**</span></span>  
  
-   <span data-ttu-id="18a68-110">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="18a68-110">**Receive  folder**</span></span>  
  
     <span data-ttu-id="18a68-111">Le dossier de réception de l'adaptateur FILE peut être configuré sur l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="18a68-111">The receive folder for the File adapter is configurable on the receive location.</span></span> <span data-ttu-id="18a68-112">Le dossier de réception de l'adaptateur EDI peut être configuré sur le gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="18a68-112">The receive folder for the EDI adapter is configurable on the receive handler.</span></span> <span data-ttu-id="18a68-113">Le compte de service de l'hôte BizTalk qui récupère le fichier doit disposer des autorisations suivantes au niveau du système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="18a68-113">The service account for the BizTalk Host that picks up the file should have the following permissions at the file-system level:</span></span>  
  
    -   <span data-ttu-id="18a68-114">Lister le dossier/Lire les données</span><span class="sxs-lookup"><span data-stu-id="18a68-114">List Folder / Read Data</span></span>  
  
    -   <span data-ttu-id="18a68-115">Supprimer le sous-dossier et les fichiers</span><span class="sxs-lookup"><span data-stu-id="18a68-115">Delete SubFolder and Files</span></span>  
  
     <span data-ttu-id="18a68-116">Si le dossier de réception se trouve sur un partage réseau, les autorisations suivantes doivent être octroyées au niveau du partage de fichiers :</span><span class="sxs-lookup"><span data-stu-id="18a68-116">If the receive folder is on a network share, the following permissions must be granted at the file-share level:</span></span>  
  
    -   <span data-ttu-id="18a68-117">Le compte de service de l'hôte BizTalk qui récupère le fichier doit disposer des autorisations de contrôle total.</span><span class="sxs-lookup"><span data-stu-id="18a68-117">The service account for the BizTalk Host that picks up the file must have Full Control permissions.</span></span>  
  
    -   <span data-ttu-id="18a68-118">Les administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent disposer des autorisations de contrôle total pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="18a68-118">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrators must have Full Control permissions for troubleshooting.</span></span>  
  
    -   <span data-ttu-id="18a68-119">L'utilisateur ou les programmes externes qui déposent des fichiers à cet emplacement doivent disposer des autorisations en écriture.</span><span class="sxs-lookup"><span data-stu-id="18a68-119">The external user or programs that drop files to this location must have Write permissions.</span></span>  
  
-   <span data-ttu-id="18a68-120">**Dossier d’envoi**</span><span class="sxs-lookup"><span data-stu-id="18a68-120">**Send folder**</span></span>  
  
     <span data-ttu-id="18a68-121">Le dossier d'envoi des adaptateurs FILE et EDI peut être configuré sur le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="18a68-121">The send folder for the File and EDI adapters are configurable on the send port.</span></span>  
  
    -   <span data-ttu-id="18a68-122">Le compte de service du ou des hôtes BizTalk qui déposent des fichiers à cet emplacement doivent disposer des autorisations en écriture.</span><span class="sxs-lookup"><span data-stu-id="18a68-122">The service account for the BizTalk Host or Hosts that drop files here must have Write permissions.</span></span>  
  
    -   <span data-ttu-id="18a68-123">Les administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent disposer des autorisations de contrôle total.</span><span class="sxs-lookup"><span data-stu-id="18a68-123">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrators must have Full Control permissions.</span></span>  
  
    -   <span data-ttu-id="18a68-124">L'utilisateur ou le programme externe qui récupère les fichiers doit disposer des autorisations en lecture.</span><span class="sxs-lookup"><span data-stu-id="18a68-124">The external user or program that picks up files must have Read permissions.</span></span>  
  
 <span data-ttu-id="18a68-125">**Ajoutez le compte d’utilisateur sous lequel le service EDI est exécuté au rôle SQL BTS_HOST_USERS.**</span><span class="sxs-lookup"><span data-stu-id="18a68-125">**Add the user account under which the EDI service is running to the BTS_HOST_USERS SQL role.**</span></span>  
  
 <span data-ttu-id="18a68-126">Cette opération permet d'obtenir l'accès au modèle objet de l'Explorateur BizTalk sans autorisations administratives.</span><span class="sxs-lookup"><span data-stu-id="18a68-126">This is required so that you can obtain BizTalk Explorer Object Management (OM) Access without administrative permissions.</span></span> <span data-ttu-id="18a68-127">Pour ce faire, ajoutez les utilisateurs du sous-système EDI au rôle BTS_HOST_USERS dans la base de données de gestion BizTalk (BizTalkMgmtDb).</span><span class="sxs-lookup"><span data-stu-id="18a68-127">To do this, add "EDI Subsystem Users" to the BTS_HOST_USERS role in the BizTalk Management database, BizTalkMgmtDb.</span></span>  
  
 <span data-ttu-id="18a68-128">Pour ajouter les utilisateurs du sous-système EDI au rôle BTS_HOST_USERS sous SQL Server 2005, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="18a68-128">To add "EDI Subsystem Users" to the BTS_HOST_USERS role on SQL Server 2005, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="18a68-129">Lancez SQL Server Management Studio à partir de **Démarrer, programmes, Microsoft SQL Server 2008**.</span><span class="sxs-lookup"><span data-stu-id="18a68-129">Launch SQL Server Management Studio from **Start, Programs, Microsoft SQL Server 2008**.</span></span>  
  
2.  <span data-ttu-id="18a68-130">Connectez-vous au serveur SQL qui héberge votre base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="18a68-130">Connect to the SQL Server that houses your BizTalk Management database.</span></span>  
  
3.  <span data-ttu-id="18a68-131">Développez ce serveur dans l'Explorateur d'objets.</span><span class="sxs-lookup"><span data-stu-id="18a68-131">Expand this server in the Object Explorer.</span></span>  
  
4.  <span data-ttu-id="18a68-132">Développez **bases de données**, puis développez la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="18a68-132">Expand **Databases**, and then expand the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="18a68-133">Développez **sécurité**, développez **rôles**, puis cliquez sur pour sélectionner **des rôles de base de données**</span><span class="sxs-lookup"><span data-stu-id="18a68-133">Expand **Security**, expand **Roles**, and then click to select **Database Roles**</span></span>  
  
6.  <span data-ttu-id="18a68-134">Dans le volet de détails, cliquez sur le rôle BTS_HOST_USERS, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="18a68-134">In the details pane, right-click the BTS_HOST_USERS role, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="18a68-135">Dans la boîte de dialogue BTS_HOST_USERS, cliquez sur **ajouter**, cliquez sur **Parcourir**et puis activez la case en regard du groupe utilisateurs du sous-système EDI pour l’ajouter.</span><span class="sxs-lookup"><span data-stu-id="18a68-135">In the BTS_HOST_USERS dialog box, click **Add**, click **Browse**, and then check the box next to the EDI Subsystem Users group to add it.</span></span>  
  
     <span data-ttu-id="18a68-136">Si le groupe Utilisateurs du sous-système EDI ne figure pas dans la liste des utilisateurs à ajouter, vous devez l'ajouter en tant que nouvel utilisateur à la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="18a68-136">If the EDI Subsystem Users group is not available in the list of users to add, you must add the EDI Subsystem Users group as a new database user to the BizTalk Management database.</span></span> <span data-ttu-id="18a68-137">Pour ce faire, procédez comme suit dans SQL Server Management Studio :</span><span class="sxs-lookup"><span data-stu-id="18a68-137">To add the EDI Subsystem Users group as a new database user, complete the following steps in SQL Server Management Studio:</span></span>  
  
    1.  <span data-ttu-id="18a68-138">Développez la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="18a68-138">Expand the BizTalk Management database.</span></span>  
  
    2.  <span data-ttu-id="18a68-139">Développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="18a68-139">Expand **Security**.</span></span>  
  
    3.  <span data-ttu-id="18a68-140">Avec le bouton droit **utilisateurs** et cliquez sur **nouvel utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="18a68-140">Right-click **Users** and click **New User**.</span></span>  
  
    4.  <span data-ttu-id="18a68-141">Cliquez sur le bouton de sélection (...) en regard de la zone de texte **nom de connexion** pour afficher les **sélectionner la connexion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="18a68-141">Click the ellipses (…) button next to the text box for **Login name** to display the **Select Login** dialog box.</span></span>  
  
    5.  <span data-ttu-id="18a68-142">Cliquez sur le bouton Parcourir, entrez le **utilisateurs du sous-système EDI** de groupe, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="18a68-142">Click the Browse button, enter the **EDI Subsystem Users** group, and then click **OK.**</span></span> <span data-ttu-id="18a68-143">Si vous êtes invité au **plusieurs objets trouvés** boîte de dialogue, sélectionnez le **utilisateurs du sous-système EDI** connexion et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="18a68-143">If prompted with the **Multiple Objects Found** dialog box, select the **EDI Subsystem Users** login and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="18a68-144">Sur le **nouvel utilisateur de base de données** boîte de dialogue Entrez **utilisateurs du sous-système EDI** pour le **nom d’utilisateur** zone de texte et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="18a68-144">On the **Database User - New** dialog box enter **EDI Subsystem Users** for the **User name** textbox and click **OK**.</span></span>  
  
 <span data-ttu-id="18a68-145">**Ajoutez le compte d’utilisateur sous lequel le service BizTalk est en cours d’exécution au groupe utilisateurs du sous-système EDI.**</span><span class="sxs-lookup"><span data-stu-id="18a68-145">**Add the user account under which the BizTalk service is running to the EDI Subsystem Users group.**</span></span>  
  
 <span data-ttu-id="18a68-146">Pour ce faire, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="18a68-146">Follow these steps to add the user account for the BizTalk service to the EDI Subsystem Users group.</span></span>  
  
-   <span data-ttu-id="18a68-147">**Si BizTalk Server est configuré pour utiliser des groupes de domaine :**</span><span class="sxs-lookup"><span data-stu-id="18a68-147">**If BizTalk Server is configured to use domain groups:**</span></span>  
  
    1.  <span data-ttu-id="18a68-148">Ouvrez une session sur un ordinateur Windows Server dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="18a68-148">Logon to a Windows Server computer in the domain.</span></span>  
  
    2.  <span data-ttu-id="18a68-149">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers**.</span><span class="sxs-lookup"><span data-stu-id="18a68-149">Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="18a68-150">Vous devez disposer des autorisations de niveau domaine approprié pour modifier les objets dans le **Active Directory Users and Computers** interface.</span><span class="sxs-lookup"><span data-stu-id="18a68-150">You must have appropriate domain level permissions to modify objects in the **Active Directory Users and Computers** interface.</span></span>  
  
    3.  <span data-ttu-id="18a68-151">Cliquez pour développer le conteneur de domaine, puis cliquez pour développer le **utilisateurs** conteneur.</span><span class="sxs-lookup"><span data-stu-id="18a68-151">Click to expand the domain container and click to expand the **Users** container.</span></span>  
  
    4.  <span data-ttu-id="18a68-152">Double-cliquez sur le **utilisateurs du sous-système EDI** groupe pour afficher les propriétés pour ce groupe.</span><span class="sxs-lookup"><span data-stu-id="18a68-152">Double click the **EDI Subsystem Users** group to display the properties for this group.</span></span>  
  
    5.  <span data-ttu-id="18a68-153">Cliquez sur le **membres** onglet de la **utilisateurs du sous-système EDI** boîte de dialogue groupe.</span><span class="sxs-lookup"><span data-stu-id="18a68-153">Click the **Members** tab of the **EDI Subsystem Users** group dialog.</span></span>  
  
    6.  <span data-ttu-id="18a68-154">Cliquez sur le **ajouter** pour ajouter le compte d’utilisateur pour le BizTalk Service à ce groupe.</span><span class="sxs-lookup"><span data-stu-id="18a68-154">Click the **Add** button to add the user account for the BizTalk Service to this group.</span></span>  
  
    7.  <span data-ttu-id="18a68-155">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="18a68-155">Click **OK**.</span></span>  
  
-   <span data-ttu-id="18a68-156">**Si BizTalk Server est configuré pour utiliser des groupes locaux :**</span><span class="sxs-lookup"><span data-stu-id="18a68-156">**If BizTalk Server is configured to use local groups:**</span></span>  
  
    1.  <span data-ttu-id="18a68-157">Ouvrez une session sur le serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="18a68-157">Logon to the BizTalk Server.</span></span>  
  
    2.  <span data-ttu-id="18a68-158">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="18a68-158">Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
    3.  <span data-ttu-id="18a68-159">Cliquez pour développer **Outils système**, cliquez pour développer **utilisateurs et groupes locaux**et développez **groupes**.</span><span class="sxs-lookup"><span data-stu-id="18a68-159">Click to expand **System Tools**, click to expand **Local Users and Groups**, and click to expand **Groups**.</span></span>  
  
    4.  <span data-ttu-id="18a68-160">Double-cliquez sur le **utilisateurs du sous-système EDI** groupe pour afficher les propriétés pour ce groupe.</span><span class="sxs-lookup"><span data-stu-id="18a68-160">Double click the **EDI Subsystem Users** group to display the properties for this group.</span></span>  
  
    5.  <span data-ttu-id="18a68-161">Cliquez sur le **ajouter** pour ajouter le compte d’utilisateur pour le service BizTalk à ce groupe.</span><span class="sxs-lookup"><span data-stu-id="18a68-161">Click the **Add** button to add the user account for the BizTalk service to this group.</span></span>  
  
    6.  <span data-ttu-id="18a68-162">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="18a68-162">Click **OK**.</span></span>
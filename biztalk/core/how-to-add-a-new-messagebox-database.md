---
title: "Comment ajouter une nouvelle base de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, MessageBox database
- MessageBox database, adding
- managing [MessageBox database], adding
ms.assetid: 98d850dc-fe3e-43dd-8b5d-9b8c23c006ae
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cab4fd370aab2d85519b3fd52e0dadcd9583275e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-new-messagebox-database"></a><span data-ttu-id="56d0b-102">Ajout d'une nouvelle base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="56d0b-102">How to Add a New MessageBox Database</span></span>
<span data-ttu-id="56d0b-103">Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour ajouter une nouvelle base de données MessageBox à votre déploiement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="56d0b-103">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console to add a new MessageBox database to your BizTalk Server deployment.</span></span> <span data-ttu-id="56d0b-104">Les bases de données MessageBox sont à la base de l'équilibrage de la charge des opérations entre les serveurs de traitement coopératif.</span><span class="sxs-lookup"><span data-stu-id="56d0b-104">MessageBox databases are the basis for load-balancing work items across servers that do cooperative processing.</span></span> <span data-ttu-id="56d0b-105">Pour accroître le nombre de messages pouvant être traités par votre système, vous pouvez ajouter des bases de données MessageBox supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="56d0b-105">To increase the number of messages that your system can process, you may need to add additional MessageBox databases.</span></span>  
  
 <span data-ttu-id="56d0b-106">Vous ne pouvez pas créer une base de données MessageBox et, en même temps, avoir des orchestrations, des ports d'envoi ou des groupes de ports d'envoi inscrits.</span><span class="sxs-lookup"><span data-stu-id="56d0b-106">You cannot create a new MessageBox database and have enlisted orchestrations, send ports, or send port groups at the same time.</span></span> <span data-ttu-id="56d0b-107">Les orchestrations, ports d'envoi ou groupes de ports d'envoi inscrits accèdent à des données que BizTalk Server doit copier dans la nouvelle base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-107">Enlisted orchestrations, send ports, or send port groups access data that BizTalk Server must copy to the new MessageBox database.</span></span> <span data-ttu-id="56d0b-108">Tant que ces données font l'objet d'un accès, BizTalk Server ne peut pas les copier dans la nouvelle base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-108">While this data is being accessed, BizTalk Server cannot copy it into the new MessageBox database.</span></span>  
  
 <span data-ttu-id="56d0b-109">Vous pouvez désigner des bases de données locales et distantes comme bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-109">You can designate both local and remote databases as MessageBox databases.</span></span> <span data-ttu-id="56d0b-110">Pour plus d’informations sur les bases de données BizTalk Server, consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="56d0b-110">For information about BizTalk Server databases, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56d0b-111">L'Agent SQL Server doit s'exécuter sur tous les serveurs SQL Server auxquels vous voulez ajouter une nouvelle base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-111">SQL Server Agent must be running on all of the SQL servers to which you want to add a new MessageBox database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56d0b-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="56d0b-112">Prerequisites</span></span>  
 <span data-ttu-id="56d0b-113">Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="56d0b-113">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="56d0b-114">Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :</span><span class="sxs-lookup"><span data-stu-id="56d0b-114">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="56d0b-115">Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="56d0b-115">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="56d0b-116">être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.</span><span class="sxs-lookup"><span data-stu-id="56d0b-116">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
### <a name="to-add-a-new-messagebox-database"></a><span data-ttu-id="56d0b-117">Pour ajouter une nouvelle base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="56d0b-117">To add a new MessageBox database</span></span>  
  
1.  <span data-ttu-id="56d0b-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="56d0b-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="56d0b-119">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, puis cliquez sur **paramètres de plateforme**.</span><span class="sxs-lookup"><span data-stu-id="56d0b-119">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then click **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="56d0b-120">Avec le bouton droit **boîtes de Message**, cliquez sur **nouveau**, puis cliquez sur **boîte de Message**.</span><span class="sxs-lookup"><span data-stu-id="56d0b-120">Right-click **Message Boxes**, click **New**, and then click **Message Box**.</span></span>  
  
4.  <span data-ttu-id="56d0b-121">Dans le **propriétés de MessageBox** boîte de dialogue, procédez comme suit, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="56d0b-121">In the **Message Box Properties** dialog box, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="56d0b-122">Utiliser</span><span class="sxs-lookup"><span data-stu-id="56d0b-122">Use this</span></span>|<span data-ttu-id="56d0b-123">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="56d0b-123">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="56d0b-124">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="56d0b-124">**SQL Server**</span></span>|<span data-ttu-id="56d0b-125">Afficher le nom du serveur SQL Server hébergeant la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-125">Displays the name of the SQL server that hosts the MessageBox database.</span></span>|  
    |<span data-ttu-id="56d0b-126">**Base de données**</span><span class="sxs-lookup"><span data-stu-id="56d0b-126">**Database**</span></span>|<span data-ttu-id="56d0b-127">Afficher le nom de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="56d0b-127">Displays the name of the MessageBox database.</span></span>|  
    |<span data-ttu-id="56d0b-128">**Boîte de message d’abonnement principal**</span><span class="sxs-lookup"><span data-stu-id="56d0b-128">**Master subscription message box**</span></span>|<span data-ttu-id="56d0b-129">Indiquer si la base de données MessageBox sélectionnée est la base principale.</span><span class="sxs-lookup"><span data-stu-id="56d0b-129">Indicates whether the selected MessageBox database is the master.</span></span> <span data-ttu-id="56d0b-130">Si la base de données MessageBox active est la base principale, cette case à cocher est activée et indisponible.</span><span class="sxs-lookup"><span data-stu-id="56d0b-130">If the current MessageBox database is the master, this check box is selected and unavailable.</span></span> <span data-ttu-id="56d0b-131">Par défaut, la première base de données MessageBox créée quand vous exécutez l'Assistant Configuration est la base de données principale.</span><span class="sxs-lookup"><span data-stu-id="56d0b-131">The first MessageBox database created when you run the Configuration Wizard is the master by default.</span></span>|  
    |<span data-ttu-id="56d0b-132">**Désactiver la publication des nouveaux messages**</span><span class="sxs-lookup"><span data-stu-id="56d0b-132">**Disable new message publication**</span></span>|<span data-ttu-id="56d0b-133">Activer cette case à cocher pour indiquer que cette base de données MessageBox ne doit pas recevoir de messages d'activation.</span><span class="sxs-lookup"><span data-stu-id="56d0b-133">Select this check box to specify that you do not want this MessageBox database to receive activation messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56d0b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56d0b-134">See Also</span></span>  
 <span data-ttu-id="56d0b-135">[Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="56d0b-135">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="56d0b-136">[Comment désactiver la Publication des nouveaux messages](../core/how-to-disable-new-message-publication.md) </span><span class="sxs-lookup"><span data-stu-id="56d0b-136">[How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md) </span></span>  
 <span data-ttu-id="56d0b-137">[Comment supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="56d0b-137">[How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md) </span></span>  
 <span data-ttu-id="56d0b-138">[Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="56d0b-138">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="56d0b-139">La base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="56d0b-139">The MessageBox Database</span></span>](../core/the-messagebox-database.md)
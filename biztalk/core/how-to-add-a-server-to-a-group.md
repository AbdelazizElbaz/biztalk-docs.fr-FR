---
title: "Comment ajouter un serveur à un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- adding, servers
- managing [groups], adding servers
- servers, groups
- managing [servers], adding to groups
ms.assetid: 6eca1eeb-1a56-4470-b3bc-c64865cf6270
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db5c7b760167f3e17d3ea82bf1023884b65e725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-server-to-a-group"></a><span data-ttu-id="04146-102">Ajout d'un serveur à un groupe</span><span class="sxs-lookup"><span data-stu-id="04146-102">How to Add a Server to a Group</span></span>
<span data-ttu-id="04146-103">La configuration de BizTalk Server permet d'ajouter un serveur à un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="04146-103">You can use BizTalk Server Configuration to add a server to a BizTalk group.</span></span> <span data-ttu-id="04146-104">Cette opération permet d'étendre le déploiement de l'environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="04146-104">You add additional servers to a BizTalk group to scale out your BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="04146-105">Un serveur peut uniquement être associé à un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="04146-105">A server can only be associated with one BizTalk group.</span></span> <span data-ttu-id="04146-106">Si un serveur appartient déjà à un autre groupe, vous devez le supprimer de son groupe actuel avant de l'ajouter à un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="04146-106">If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.</span></span> <span data-ttu-id="04146-107">Pour plus d’informations sur la suppression d’un serveur à partir d’un groupe BizTalk, consultez [comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md).</span><span class="sxs-lookup"><span data-stu-id="04146-107">For information about removing a server from a BizTalk group, see [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04146-108">Il n'y a pas d'interaction entre les groupes BizTalk associés à différents serveurs dans un environnement BizTalk Server, excepté dans le cadre d'échanges de message.</span><span class="sxs-lookup"><span data-stu-id="04146-108">BizTalk groups associated with different servers in a BizTalk Server environment do not interact except to exchange messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04146-109">Le composant d'exécution de BizTalk Server doit être installé sur l'ordinateur que vous voulez ajouter au groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="04146-109">The BizTalk Server runtime must be installed on the computer you want to add to the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="04146-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="04146-110">Prerequisites</span></span>  
 <span data-ttu-id="04146-111">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs de l'authentification unique et du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="04146-111">To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-add-a-server-to-a-biztalk-group"></a><span data-ttu-id="04146-112">Pour ajouter un serveur à un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="04146-112">To add a server to a BizTalk group</span></span>  
  
1.  <span data-ttu-id="04146-113">Sur l’ordinateur que vous souhaitez ajouter à un groupe BizTalk Server pour, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="04146-113">On the computer that you want to add to a BizTalk Server group to, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="04146-114">Dans **Configuration de Microsoft BizTalk Server**, sélectionnez **configuration personnalisée**.</span><span class="sxs-lookup"><span data-stu-id="04146-114">In **Microsoft BizTalk Server Configuration**, select **Custom configuration**.</span></span>  
  
3.  <span data-ttu-id="04146-115">Dans **nom du serveur de base de données**, tapez le nom du serveur SQL pour le groupe BizTalk auquel associer le serveur.</span><span class="sxs-lookup"><span data-stu-id="04146-115">In **Database server name**, type the name of the SQL Server for the BizTalk Group the server is joining.</span></span>  
  
4.  <span data-ttu-id="04146-116">Dans **informations d’identification du Service**, tapez le nom d’utilisateur et un mot de passe que les services utilisera, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="04146-116">In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="04146-117">Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **Enterprise SSO**.</span><span class="sxs-lookup"><span data-stu-id="04146-117">In the navigation tree on the left side of the screen, click **Enterprise SSO**.</span></span>  
  
6.  <span data-ttu-id="04146-118">Sur le **Enterprise Single Sign-On** , cliquez sur **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="04146-118">On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.</span></span>  
  
     <span data-ttu-id="04146-119">Assurez-vous que le nom du serveur et le nom de la base de données pointent vers le serveur de base de données de l'authentification unique principal du groupe BizTalk Server auquel associer le serveur.</span><span class="sxs-lookup"><span data-stu-id="04146-119">Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group the server is joining.</span></span>  
  
7.  <span data-ttu-id="04146-120">Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **groupe**.</span><span class="sxs-lookup"><span data-stu-id="04146-120">In the navigation tree on the left side of the screen, click **Group**.</span></span>  
  
8.  <span data-ttu-id="04146-121">Sur le **groupe** , cliquez sur **joindre un groupe BizTalk existant**.</span><span class="sxs-lookup"><span data-stu-id="04146-121">On the **Group** page, click **Join an existing BizTalk Group**.</span></span>  
  
     <span data-ttu-id="04146-122">Assurez-vous que le nom du serveur et le nom de la base de données pointent vers les bases de données du groupe BizTalk Server auquel associer le serveur.</span><span class="sxs-lookup"><span data-stu-id="04146-122">Ensure that the server name and database name point to the databases for the BizTalk Server group the server is joining.</span></span>  
  
9. <span data-ttu-id="04146-123">Dans la barre de menus, cliquez sur **appliquer la Configuration** pour configurer Enterprise Single Sign-On et que le groupe sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="04146-123">On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04146-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04146-124">See Also</span></span>  
 <span data-ttu-id="04146-125">[Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span><span class="sxs-lookup"><span data-stu-id="04146-125">[Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span></span>  
 <span data-ttu-id="04146-126">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="04146-126">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="04146-127">[Groupes BizTalk](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="04146-127">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="04146-128">[Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="04146-128">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 <span data-ttu-id="04146-129">[Comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="04146-129">[How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md) </span></span>  
 <span data-ttu-id="04146-130">[Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="04146-130">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 [<span data-ttu-id="04146-131">Gestion des serveurs</span><span class="sxs-lookup"><span data-stu-id="04146-131">Managing Servers</span></span>](../core/managing-servers.md)
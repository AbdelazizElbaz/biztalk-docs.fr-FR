---
title: "Comment déplacer un serveur à partir d’un groupe vers un autre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- groups, moving
- managing [groups], moving servers
- servers, moving
- managing [servers], moving
- servers, groups
ms.assetid: 3f789a62-f597-426b-9cea-74c1fe22b694
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c9e5dfdf266d2205283afa7cd9804c31fc93ff3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-server-from-one-group-to-another"></a><span data-ttu-id="7e65e-102">Transfert d'un serveur d'un groupe à un autre</span><span class="sxs-lookup"><span data-stu-id="7e65e-102">How to Move a Server from One Group to Another</span></span>
<span data-ttu-id="7e65e-103">Un serveur ne peut être associé qu'à un seul groupe BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7e65e-103">A server can only be associated with one BizTalk Server group.</span></span> <span data-ttu-id="7e65e-104">Pour déplacer un serveur d'un groupe à un autre, vous devez d'abord supprimer le serveur du groupe d'origine en annulant sa configuration, puis l'ajouter au nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="7e65e-104">To move a server from one group to another, you must first remove the server from the original group by unconfiguring it, and then add the server to the new group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7e65e-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7e65e-105">Prerequisites</span></span>  
 <span data-ttu-id="7e65e-106">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs de l'authentification unique et du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="7e65e-106">To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-move-a-server-from-one-biztalk-group-to-another"></a><span data-ttu-id="7e65e-107">Pour déplacer un serveur d'un groupe BizTalk à un autre</span><span class="sxs-lookup"><span data-stu-id="7e65e-107">To move a server from one BizTalk group to another</span></span>  
  
1.  <span data-ttu-id="7e65e-108">Sur l’ordinateur que vous souhaitez déplacer le groupe BizTalk vers un autre, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **deConfigurationdeBizTalkServer**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-108">On the computer that you want to move from the BizTalk group to another, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="7e65e-109">Dans la barre de menus, cliquez sur **annuler la configuration des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-109">On the menu bar, click **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="7e65e-110">Dans le **annuler la configuration des fonctionnalités** boîte de dialogue, sélectionnez **Enterprise SSO**, sélectionnez **groupe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-110">In the **Unconfigure Features** dialog box, select **Enterprise SSO**, select **Group**, and then click **OK**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="7e65e-111">L'annulation de la configuration d'un groupe annule également la configuration de tous les composants dépendants déjà configurés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7e65e-111">Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.</span></span>  
  
4.  <span data-ttu-id="7e65e-112">Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-112">Click **Yes**.</span></span>  
  
5.  <span data-ttu-id="7e65e-113">Dans le **Configuration de Microsoft BizTalk Server** fenêtre, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-113">In the **Microsoft BizTalk Server Configuration** window, click **Next**.</span></span>  
  
     <span data-ttu-id="7e65e-114">La configuration de l'authentification unique de l'entreprise, du groupe et de leurs composants dépendants est annulée.</span><span class="sxs-lookup"><span data-stu-id="7e65e-114">Enterprise SSO, the Group, and their dependent features are unconfigured.</span></span>  
  
6.  <span data-ttu-id="7e65e-115">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-115">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="7e65e-116">Dans le **Configuration de Microsoft BizTalk Server** fenêtre, sélectionnez **configuration personnalisée**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-116">In the **Microsoft BizTalk Server Configuration** window, select **Custom configuration**.</span></span>  
  
8.  <span data-ttu-id="7e65e-117">Dans **nom du serveur de base de données**, tapez le nom du serveur SQL pour le groupe BizTalk sur lequel vous déplacez le serveur.</span><span class="sxs-lookup"><span data-stu-id="7e65e-117">In **Database server name**, type the name of the SQL server for the BizTalk Group where you are moving the server.</span></span>  
  
9. <span data-ttu-id="7e65e-118">Dans **informations d’identification du Service**, tapez le nom d’utilisateur et un mot de passe que les services utilisera, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-118">In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="7e65e-119">Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **Enterprise SSO**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-119">In the navigation tree on the left side of the screen, click **Enterprise SSO**.</span></span>  
  
11. <span data-ttu-id="7e65e-120">Sur le **Enterprise Single Sign-On** , cliquez sur **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-120">On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.</span></span>  
  
     <span data-ttu-id="7e65e-121">Assurez-vous que le nom du serveur et le nom de la base de données pointent vers le serveur de base de données de l'authentification unique principal du groupe BizTalk Server sur lequel vous déplacez le serveur.</span><span class="sxs-lookup"><span data-stu-id="7e65e-121">Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group where you are moving the server.</span></span>  
  
12. <span data-ttu-id="7e65e-122">Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **groupe**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-122">In the navigation tree on the left side of the screen, click **Group**.</span></span>  
  
13. <span data-ttu-id="7e65e-123">Sur le **groupe** , cliquez sur **joindre un groupe BizTalk existant**.</span><span class="sxs-lookup"><span data-stu-id="7e65e-123">On the **Group** page, click **Join an existing BizTalk Group**.</span></span>  
  
     <span data-ttu-id="7e65e-124">Assurez-vous que le nom du serveur et le nom de la base de données pointent vers les bases de données du groupe BizTalk Server sur lequel vous déplacez le serveur.</span><span class="sxs-lookup"><span data-stu-id="7e65e-124">Ensure that the server name and database name point to the databases for the BizTalk Server group where you are moving the server.</span></span>  
  
14. <span data-ttu-id="7e65e-125">Dans la barre de menus, cliquez sur **appliquer la Configuration** pour configurer Enterprise Single Sign-On et que le groupe sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7e65e-125">On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e65e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e65e-126">See Also</span></span>  
 <span data-ttu-id="7e65e-127">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-127">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="7e65e-128">[Groupes BizTalk](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-128">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="7e65e-129">[Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-129">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="7e65e-130">[Comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-130">[How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md) </span></span>  
 <span data-ttu-id="7e65e-131">[Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-131">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 <span data-ttu-id="7e65e-132">[Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-132">[Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span></span>  
 <span data-ttu-id="7e65e-133">[L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="7e65e-133">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 [<span data-ttu-id="7e65e-134">Gestion des serveurs</span><span class="sxs-lookup"><span data-stu-id="7e65e-134">Managing Servers</span></span>](../core/managing-servers.md)
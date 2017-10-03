---
title: "Désactiver la Publication des nouveaux messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9099ecaa-31ed-4880-a0f6-8dbfaf783f7a
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 478cf89ac4677d60e9a5b5a855998e0b0e5120c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disable-new-message-publication"></a><span data-ttu-id="86220-102">Désactiver la Publication des nouveaux messages</span><span class="sxs-lookup"><span data-stu-id="86220-102">Disable New Message Publication</span></span>

## <a name="overview"></a><span data-ttu-id="86220-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="86220-103">Overview</span></span>
<span data-ttu-id="86220-104">Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) pour désactiver la publication des nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="86220-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or Windows Management Instrumentation (WMI) to disable new message publication.</span></span> <span data-ttu-id="86220-105">Cette désactivation dans la base de données MessageBox permet d'arrêter la réception de nouveaux messages par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="86220-105">You disable new message publication in the MessageBox database to stop the receipt of new messages by the MessageBox database.</span></span> <span data-ttu-id="86220-106">Dans certains environnements BizTalk Server, la désactivation de la publication des nouveaux messages pour la base de données principale MessageBox permet d'améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="86220-106">In some BizTalk Server environments, you can improve performance if you disable new message publication for the master MessageBox database.</span></span> <span data-ttu-id="86220-107">Cette désactivation n'affecte pas les messages existants de la base de données MessageBox ni les instances de service en cours.</span><span class="sxs-lookup"><span data-stu-id="86220-107">Disabling new message publication does not affect existing messages in the MessageBox database or service instances that are in progress.</span></span>  
  
 <span data-ttu-id="86220-108">Pour plus d’informations sur l’utilisation de WMI pour désactiver la publication des nouveaux messages, consultez le **propriété MSBTS_MsgBoxSetting.DisableNewMessagePublication (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="86220-108">For information about using WMI to disable new message publication, see the **MSBTS_MsgBoxSetting.DisableNewMessagePublication Property (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="86220-109">Pour pouvoir supprimer une base de données MessageBox, vous devez désactiver la publication des nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="86220-109">You must disable the publication of new messages before you delete a MessageBox database.</span></span> <span data-ttu-id="86220-110">Pour plus d’informations sur la suppression d’une base de données MessageBox, consultez [comment supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md).</span><span class="sxs-lookup"><span data-stu-id="86220-110">For information about deleting a MessageBox database, see [How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="86220-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="86220-111">Prerequisites</span></span>  
 <span data-ttu-id="86220-112">Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="86220-112">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="86220-113">Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :</span><span class="sxs-lookup"><span data-stu-id="86220-113">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="86220-114">Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="86220-114">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="86220-115">être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.</span><span class="sxs-lookup"><span data-stu-id="86220-115">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
## <a name="disable-steps"></a><span data-ttu-id="86220-116">Désactiver des étapes</span><span class="sxs-lookup"><span data-stu-id="86220-116">Disable steps</span></span>
  
1.  <span data-ttu-id="86220-117">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="86220-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="86220-118">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **boîtes de Message**.</span><span class="sxs-lookup"><span data-stu-id="86220-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.</span></span>  
  
3.  <span data-ttu-id="86220-119">Dans le volet de détails, cliquez sur la base de données MessageBox que vous voulez désactiver, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="86220-119">In the details pane, right-click the MessageBox database you want to disable, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="86220-120">Dans le **propriétés de MessageBox** boîte de dialogue, sélectionnez le **désactiver la publication des nouveaux messages** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="86220-120">In the **Message Box Properties** dialog box, select the **Disable new message publication** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86220-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86220-121">See Also</span></span>  
 <span data-ttu-id="86220-122">[Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="86220-122">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="86220-123">[Ajouter une nouvelle base de données MessageBox](../core/how-to-add-a-new-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="86220-123">[Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md) </span></span>  
 <span data-ttu-id="86220-124">[Supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="86220-124">[Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md) </span></span>  
 [<span data-ttu-id="86220-125">La base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="86220-125">The MessageBox Database</span></span>](../core/the-messagebox-database.md)
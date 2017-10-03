---
title: "Service de créer des comptes pour les nouveaux ordinateurs hôtes et les Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager, service accounts
- Windows groups, service accounts
- Configuration Manager
- service accounts, Windows groups
- hosts, service accounts
- service accounts, hosts
- service accounts, Configuration Manager
- service accounts, creating
- creating, service accounts
ms.assetid: cef97f4a-8db1-41b6-9614-608c2fbf59a9
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3626f4349fa1e2cc9f739cf0375ab73e3adc7ae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-service-accounts-for-new-hosts-and-host-instances"></a><span data-ttu-id="9a6df-102">Création des comptes de service pour les nouveaux hôtes et instances d'hôte</span><span class="sxs-lookup"><span data-stu-id="9a6df-102">How to Create Service Accounts for New Hosts and Host Instances</span></span>
<span data-ttu-id="9a6df-103">Le Gestionnaire de configuration configure les groupes Windows et les comptes d'utilisateur nécessaires lors de l'installation et de la configuration de BizTalk Server sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9a6df-103">The Configuration Manager configures the necessary Windows groups and user accounts when you install and configure BizTalk Server on a single computer.</span></span>  
  
 <span data-ttu-id="9a6df-104">Vous devez créer manuellement les groupes Windows et les comptes d'utilisateur, puis ajouter ces derniers aux groupes Windows dans un environnement de domaine avant d'exécuter le Gestionnaire de configuration.</span><span class="sxs-lookup"><span data-stu-id="9a6df-104">You must manually create Windows groups and user accounts, and add the user accounts to the Windows groups in a domain environment before running the Configuration Manager.</span></span> <span data-ttu-id="9a6df-105">Pour plus d’informations, consultez [groupes de domaine](../core/domain-groups.md).</span><span class="sxs-lookup"><span data-stu-id="9a6df-105">For more information, see [Domain Groups](../core/domain-groups.md).</span></span>  
  
 <span data-ttu-id="9a6df-106">Vous devez effectuer la procédure suivante avant de créer un hôte ou une instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="9a6df-106">You must perform the following procedure before creating a new host or host instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9a6df-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9a6df-107">Prerequisites</span></span>  
 <span data-ttu-id="9a6df-108">Pour effectuer cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs ou Administrateurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="9a6df-108">You must be logged on as a member of Administrators or Domain Admins group to perform this procedure.</span></span>  
  
### <a name="to-create-service-accounts-for-new-hosts-or-host-instances"></a><span data-ttu-id="9a6df-109">Pour créer des comptes de service pour les nouveaux hôtes ou instances d'hôte</span><span class="sxs-lookup"><span data-stu-id="9a6df-109">To create service accounts for new hosts or host instances</span></span>  
  
1.  <span data-ttu-id="9a6df-110">Créez un groupe d'hôtes Windows pour l'hôte que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="9a6df-110">Create a host Windows group for the new host that you will create.</span></span> <span data-ttu-id="9a6df-111">Pour plus d’informations sur la création d’un nouvel hôte, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md).</span><span class="sxs-lookup"><span data-stu-id="9a6df-111">For more information about creating a new host, see [How to Create a New Host](../core/how-to-create-a-new-host.md).</span></span>  
  
2.  <span data-ttu-id="9a6df-112">Créez des comptes de service pour chaque instance d'hôte qui sera ajoutée au nouvel hôte.</span><span class="sxs-lookup"><span data-stu-id="9a6df-112">Create service accounts for each host instance that will be added to the new host.</span></span> <span data-ttu-id="9a6df-113">Pour plus d’informations sur la création d’une instance d’hôte, consultez [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="9a6df-113">For more information about creating a new host instance, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
3.  <span data-ttu-id="9a6df-114">Ajoutez les comptes de service au groupe Windows de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="9a6df-114">Add the service accounts to the host Windows group as needed.</span></span> <span data-ttu-id="9a6df-115">Pour plus d’informations sur les groupes Windows auxquels vous devez ajouter le compte de service, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="9a6df-115">For information about the Windows groups to which you must add the service account, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
4.  <span data-ttu-id="9a6df-116">Utilisez le groupe Windows et le compte de service lors de la création de l'hôte et des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="9a6df-116">Use the Windows group and service account when creating the host and host instances.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a6df-117">Ne spécifiez pas \< *nom de l’ordinateur*> \ en tant que le préfixe dans une configuration d’ordinateur unique avec des groupes locaux.</span><span class="sxs-lookup"><span data-stu-id="9a6df-117">Do not specify \<*computer name*>\ as the prefix in a single computer setup with local groups.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a6df-118">Si vous utilisez un groupe de domaine, vous devez spécifier \< *nom de domaine NetBIOS*> \ en tant que le préfixe du nom d’hôte groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="9a6df-118">If you are using a Domain group, you must specify \<*Domain NetBIOS Name*>\ as the prefix for the host Windows Group name.</span></span> <span data-ttu-id="9a6df-119">Par exemple, CONTOSO\btssvc.</span><span class="sxs-lookup"><span data-stu-id="9a6df-119">For example, CONTOSO\btssvc.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6df-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a6df-120">See Also</span></span>  
 <span data-ttu-id="9a6df-121">[Gestion des hôtes et des comptes de Service](../core/managing-hosts-and-service-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="9a6df-121">[Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md) </span></span>  
 <span data-ttu-id="9a6df-122">[Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="9a6df-122">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 <span data-ttu-id="9a6df-123">[Comment gérer le groupe d’administrateurs BizTalk Server](../core/how-to-manage-the-biztalk-server-administrators-group.md) </span><span class="sxs-lookup"><span data-stu-id="9a6df-123">[How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md) </span></span>  
 [<span data-ttu-id="9a6df-124">Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows</span><span class="sxs-lookup"><span data-stu-id="9a6df-124">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)
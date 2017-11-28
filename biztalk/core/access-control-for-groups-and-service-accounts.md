---
title: "Contrôle d’accès pour les groupes et comptes de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access control, service accounts
- user accounts, default accounts
- service accounts, security
- user accounts, unsupported
- access control, groups
- service accounts, access control
- groups, access control
- groups, security
ms.assetid: 411a7bfa-6675-4d09-9e37-83e2941df3c6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67bc5799d88c0dca876df463eb37d4af65ec84d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-for-groups-and-service-accounts"></a><span data-ttu-id="28032-102">Contrôle d’accès pour les groupes et comptes de Service</span><span class="sxs-lookup"><span data-stu-id="28032-102">Access Control for Groups and Service Accounts</span></span>
<span data-ttu-id="28032-103">Chaque instance de l'hôte BizTalk est exécutée sous un compte de service créé par un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="28032-103">Each BizTalk Host instance runs under a user-created service account.</span></span> <span data-ttu-id="28032-104">Vous devez indiquer les comptes de service et leur mot de passe au moment de la création de l'instance de l'hôte sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28032-104">You must provide the service accounts and their passwords at the time you create the host instance on a computer.</span></span> <span data-ttu-id="28032-105">BizTalk Server vérifie ensuite que les comptes disposent des droits d'utilisateur minimaux requis dont ils ont besoin pour effectuer leurs tâches en ajoutant chacun de ces comptes de service à un groupe Windows de domaine ou local qui, à son tour, l'ajoute au rôle de base de données SQL Server spécifique à l'hôte.</span><span class="sxs-lookup"><span data-stu-id="28032-105">BizTalk Server then ensures that the accounts have the minimum user rights needed to do their jobs by adding each of these service accounts to a local or domain Windows group that, in turn, it adds to the SQL Server Database role specific to that host.</span></span>  
  
 <span data-ttu-id="28032-106">Cette approche offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="28032-106">This approach offers the following benefits:</span></span>  
  
-   <span data-ttu-id="28032-107">Vous pouvez attribuer un compte de service distinct à chaque instance de l'hôte, ce qui permet de modifier les mots de passe de ces instances d'hôte sans avoir à mettre les serveurs hors ligne.</span><span class="sxs-lookup"><span data-stu-id="28032-107">You can give each host instance a distinct service account, making it possible to change the passwords for each host instance without having to take servers offline.</span></span> <span data-ttu-id="28032-108">Vous pouvez ainsi effectuer des mises à jour propagées de mots de passe sans interrompre le service.</span><span class="sxs-lookup"><span data-stu-id="28032-108">You can perform rolling password updates without interrupting service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28032-109">Il est impossible d'utiliser le même compte de service pour les hôtes approuvés par authentification et pour les hôtes qui ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="28032-109">You cannot use the same service account for hosts that are authentication trusted and hosts that are not authentication trusted.</span></span>  
  
-   <span data-ttu-id="28032-110">Si vous octroyez à une ressource des droits d'utilisateur au groupe de domaine ou au groupe local au niveau de Microsoft SQL Server™, vous pouvez ajouter et retirer des comptes de service sans avoir à modifier les droits d'utilisateurs octroyés dans SQL Server, ce qui permet ainsi de réduire la charge de gestion et le coût total de possession.</span><span class="sxs-lookup"><span data-stu-id="28032-110">If you grant resource user rights to the local or domain group at the Microsoft SQL Server™ level, you can add and subtract service accounts without having to change the user rights granted in SQL Server, thus reducing your management burden and total cost of ownership.</span></span>  
  
 <span data-ttu-id="28032-111">Pour garantir que les comptes de service disposent des droits d'utilisateur minimaux dont ils ont besoin pour effectuer leurs tâches, les rôles de base de données SQL Server que BizTalk crée pour les comptes de service ne sont pas identiques dans toutes les bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="28032-111">To ensure that the service accounts have the minimum user rights they need to do their jobs, the SQL Server Database roles that BizTalk Server creates for the service accounts are not identical on all the BizTalk Server databases.</span></span> <span data-ttu-id="28032-112">Pour les bases de données de gestion et des suivis, tous les comptes de service ont besoin d'accéder aux mêmes objets SQL Server : BizTalk Server a donc créé un rôle de base de données SQL Server unique intitulé BTS_Host_User.</span><span class="sxs-lookup"><span data-stu-id="28032-112">For the Management and Tracking databases, all of the host instance service accounts need access to the same SQL Server objects, so BizTalk Server created a single SQL Server Database role named BTS_Host_User.</span></span> <span data-ttu-id="28032-113">BizTalk ajoute tous les groupes Windows créés pour les hôtes BizTalk à ce rôle de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28032-113">BizTalk adds all the Windows groups created for BizTalk hosts to this SQL Server Database role.</span></span>  
  
 <span data-ttu-id="28032-114">Pour la base de données MessageBox, chaque hôte dispose de ressources dédiées à l'hôte.</span><span class="sxs-lookup"><span data-stu-id="28032-114">For the MessageBox database, each host has some resources dedicated to that host.</span></span> <span data-ttu-id="28032-115">BizTalk Server crée un rôle de base de données SQL Server par hôte, appelé BTS_\<*nom d’hôte*> _User, et ajoute le groupe Windows pour chaque hôte à son rôle respectif de la base de données SQL Server afin de bloquer l’accès d’un ordinateur hôte ressources par un autre hôte.</span><span class="sxs-lookup"><span data-stu-id="28032-115">BizTalk Server creates a SQL Server Database role per host, named BTS_\<*hostname*>_User, and adds the Windows group for each host to its respective SQL Server Database role in order to block access of one host resources by another host.</span></span>  
  
## <a name="accounts-not-supported-by-biztalk-server"></a><span data-ttu-id="28032-116">Comptes non pris en charge par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="28032-116">Accounts not supported by BizTalk Server</span></span>  
 <span data-ttu-id="28032-117">BizTalk Server ne prend pas en charge l'utilisation des comptes Windows suivants :</span><span class="sxs-lookup"><span data-stu-id="28032-117">BizTalk Server does not support using any of the following built-in Windows accounts:</span></span>  
  
-   <span data-ttu-id="28032-118">NT_AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="28032-118">NT_AUTHORITY\NetworkService</span></span>  
  
-   <span data-ttu-id="28032-119">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="28032-119">LocalSystem</span></span>  
  
-   <span data-ttu-id="28032-120">NT_AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="28032-120">NT_AUTHORITY\LocalService</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28032-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28032-121">See Also</span></span>  
 <span data-ttu-id="28032-122">[Contrôle d’accès pour les rôles d’administration](../core/access-control-for-administrative-roles.md) </span><span class="sxs-lookup"><span data-stu-id="28032-122">[Access Control for Administrative Roles](../core/access-control-for-administrative-roles.md) </span></span>  
 <span data-ttu-id="28032-123">[Autorisations de sécurité minimales](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="28032-123">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 <span data-ttu-id="28032-124">[Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="28032-124">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="28032-125">Contrôle d’accès et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="28032-125">Access Control and Data Security</span></span>](../core/access-control-and-data-security.md)
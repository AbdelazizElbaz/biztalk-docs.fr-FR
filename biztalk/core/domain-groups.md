---
title: Groupes de domaine | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: domain groups
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fc5cc05718aa6d9e0ca89bc48467052fb916a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="domain-groups"></a><span data-ttu-id="09368-102">Groupes de domaine</span><span class="sxs-lookup"><span data-stu-id="09368-102">Domain Groups</span></span>
<span data-ttu-id="09368-103">BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="09368-103">BizTalk Server supports domain group and user accounts in both single and multiple computer configurations.</span></span> <span data-ttu-id="09368-104">Pour les configurations multiserveurs, vous devez respecter les prérequis répertoriés dans cette section et dans la rubrique « Considérations relatives aux environnements multiserveurs » (Considerations for Multiserver Environments) du guide d'installation.</span><span class="sxs-lookup"><span data-stu-id="09368-104">For multiple computer configurations, you must observe the requirements provided in this section and in the Considerations for Multiserver Environments in the Installation Guide.</span></span> <span data-ttu-id="09368-105">Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span><span class="sxs-lookup"><span data-stu-id="09368-105">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span>  
  
-   <span data-ttu-id="09368-106">Si vous utilisez des groupes de domaine pour configurer BizTalk Server, vous devez créer manuellement les groupes avant de configurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="09368-106">If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server.</span></span> <span data-ttu-id="09368-107">Le Gestionnaire de configuration ne peut pas créer de groupes de domaine.</span><span class="sxs-lookup"><span data-stu-id="09368-107">The Configuration Manager cannot create domain groups.</span></span>  
  
-   <span data-ttu-id="09368-108">Après avoir créé des groupes de domaine ou des comptes d’utilisateur, ajoutez les comptes d’utilisateur aux groupes appropriés en fonction des affiliations de groupe dans [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="09368-108">After creating domain groups and/or user accounts, add user accounts to the proper groups according to the group affiliations in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="09368-109">Utilisez  **\<nom_domaine >\\< nom d’utilisateur\>**  lors de la spécification des informations de compte de domaine dans le Gestionnaire de Configuration.</span><span class="sxs-lookup"><span data-stu-id="09368-109">Use **\<DomainName>\\<UserName\>** when specifying domain account information in the Configuration Manager.</span></span>  
  
-   <span data-ttu-id="09368-110">BizTalk Server nécessite des comptes de domaine pour tous les scénarios de mise en cluster.</span><span class="sxs-lookup"><span data-stu-id="09368-110">BizTalk Server requires domain accounts for all clustering scenarios.</span></span> <span data-ttu-id="09368-111">Vous ne pouvez pas utiliser de comptes locaux avec un serveur SQL ou SSO (serveur de secret principal) mis en cluster.</span><span class="sxs-lookup"><span data-stu-id="09368-111">You cannot use local accounts with clustered SQL Server or clustered SSO Server (master secret server).</span></span>  
  
-   <span data-ttu-id="09368-112">L’administrateur de l’installation et la configuration de BizTalk Server doit être membre des groupes suivants : administrateurs de SSO (uniquement lors de la configuration du serveur de secret principal) ; Administrateurs locaux ; rôle sysadmin SQL Server ; Administrateurs OLAP.</span><span class="sxs-lookup"><span data-stu-id="09368-112">The administrator installing and configuring BizTalk Server must be a member of the following groups: SSO Administrators (only when configuring the master secret server); local Administrators; sysadmin SQL Server role; OLAP Administrators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09368-113">Vous pouvez créer le groupe de domaine automatiquement si vous en spécifiez un lors de la configuration pour les administrateurs SSO et les administrateurs d'applications associées à authentification unique, et si vous possédez les autorisations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="09368-113">You can create the domain group automatically if you specify a domain group during configuration for the SSO Administrators and SSO Affiliate Administrators, and you have sufficient privileges.</span></span> <span data-ttu-id="09368-114">Si vous ne disposez pas d'autorisations suffisantes, assurez-vous que ces groupes existent déjà.</span><span class="sxs-lookup"><span data-stu-id="09368-114">If you do not have sufficient privileges, ensure that these groups already exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09368-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09368-115">See Also</span></span>  
 <span data-ttu-id="09368-116">[Groupes locaux](../core/local-groups.md) </span><span class="sxs-lookup"><span data-stu-id="09368-116">[Local Groups](../core/local-groups.md) </span></span>  
 <span data-ttu-id="09368-117">[Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="09368-117">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 [<span data-ttu-id="09368-118">Groupes et comptes d’utilisateur Windows dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09368-118">Windows Groups and User Accounts in BizTalk Server</span></span>](../core/windows-groups-and-user-accounts-in-biztalk-server.md)
---
title: Groupes de domaine | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42833e24ee4b0ad8f78a8f60139d66ceb41a5f8f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="domain-groups-in-biztalk"></a><span data-ttu-id="f1f65-102">Groupes de domaine dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f1f65-102">Domain Groups in BIzTalk</span></span>
<span data-ttu-id="f1f65-103">BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1f65-103">BizTalk Server supports domain group and user accounts in both single and multiple computer configurations.</span></span> <span data-ttu-id="f1f65-104">Pour les configurations multiserveurs, vous devez respecter les prérequis répertoriés dans cette section et dans la rubrique « Considérations relatives aux environnements multiserveurs » (Considerations for Multiserver Environments) du guide d'installation.</span><span class="sxs-lookup"><span data-stu-id="f1f65-104">For multiple computer configurations, you must observe the requirements provided in this section and in the Considerations for Multiserver Environments in the Installation Guide.</span></span> <span data-ttu-id="f1f65-105">Pour plus d’informations, consultez la [vue d’ensemble de l’installation](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="f1f65-105">For more information, see the [installation overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f1f65-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="f1f65-106">Before you begin</span></span>
-   <span data-ttu-id="f1f65-107">Si vous utilisez des groupes de domaine pour configurer BizTalk Server, vous devez créer manuellement les groupes avant de configurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f1f65-107">If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server.</span></span> <span data-ttu-id="f1f65-108">Le Gestionnaire de configuration ne peut pas créer de groupes de domaine.</span><span class="sxs-lookup"><span data-stu-id="f1f65-108">The Configuration Manager cannot create domain groups.</span></span>  
  
-   <span data-ttu-id="f1f65-109">Après avoir créé des groupes de domaine ou des comptes d’utilisateur, ajoutez les comptes d’utilisateur aux groupes appropriés en fonction des affiliations de groupe dans [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f1f65-109">After creating domain groups and/or user accounts, add user accounts to the proper groups according to the group affiliations in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f1f65-110">Utilisez  **\<nom_domaine >\\< nom d’utilisateur\>**  lors de la spécification des informations de compte de domaine dans le Gestionnaire de Configuration.</span><span class="sxs-lookup"><span data-stu-id="f1f65-110">Use **\<DomainName>\\<UserName\>** when specifying domain account information in the Configuration Manager.</span></span>  
  
-   <span data-ttu-id="f1f65-111">BizTalk Server nécessite des comptes de domaine pour tous les scénarios de mise en cluster.</span><span class="sxs-lookup"><span data-stu-id="f1f65-111">BizTalk Server requires domain accounts for all clustering scenarios.</span></span> <span data-ttu-id="f1f65-112">Vous ne pouvez pas utiliser de comptes locaux avec un serveur SQL ou SSO (serveur de secret principal) mis en cluster.</span><span class="sxs-lookup"><span data-stu-id="f1f65-112">You cannot use local accounts with clustered SQL Server or clustered SSO Server (master secret server).</span></span>  
  
-   <span data-ttu-id="f1f65-113">L’administrateur de l’installation et la configuration de BizTalk Server doit être membre des groupes suivants : administrateurs de SSO (uniquement lors de la configuration du serveur de secret principal) ; Administrateurs locaux ; rôle sysadmin SQL Server ; Administrateurs OLAP.</span><span class="sxs-lookup"><span data-stu-id="f1f65-113">The administrator installing and configuring BizTalk Server must be a member of the following groups: SSO Administrators (only when configuring the master secret server); local Administrators; sysadmin SQL Server role; OLAP Administrators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1f65-114">Vous pouvez créer le groupe de domaine automatiquement si vous en spécifiez un lors de la configuration pour les administrateurs SSO et les administrateurs d'applications associées à authentification unique, et si vous possédez les autorisations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="f1f65-114">You can create the domain group automatically if you specify a domain group during configuration for the SSO Administrators and SSO Affiliate Administrators, and you have sufficient privileges.</span></span> <span data-ttu-id="f1f65-115">Si vous ne disposez pas d'autorisations suffisantes, assurez-vous que ces groupes existent déjà.</span><span class="sxs-lookup"><span data-stu-id="f1f65-115">If you do not have sufficient privileges, ensure that these groups already exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f65-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1f65-116">See Also</span></span>  
 <span data-ttu-id="f1f65-117">[Groupes locaux](../core/local-groups.md) </span><span class="sxs-lookup"><span data-stu-id="f1f65-117">[Local Groups](../core/local-groups.md) </span></span>  
 <span data-ttu-id="f1f65-118">[Vue d’ensemble de l’installation](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md) </span><span class="sxs-lookup"><span data-stu-id="f1f65-118">[Installation Overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md) </span></span>  
 [<span data-ttu-id="f1f65-119">Groupes et comptes d’utilisateur Windows dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f1f65-119">Windows Groups and User Accounts in BizTalk Server</span></span>](../core/windows-groups-and-user-accounts-in-biztalk-server.md)
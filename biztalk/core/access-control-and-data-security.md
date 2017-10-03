---
title: "Contrôle d’accès et sécurité des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access control, BizTalk Server Operator role
- databases, SQL roles
- access control, about access control
- BizTalk Server Administrator role
- databases, access control
- access control
- access control, BizTalk Server Administrator role
- access control, SQL roles
- user accounts, access control
- BizTalk Server Operator role
ms.assetid: f04fd4a3-0f8c-4170-934a-9cc77edd7f34
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11cb00eabf6110de78e2d194e0a25bfac6a3b6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-and-data-security"></a><span data-ttu-id="8c835-102">Contrôle d’accès et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="8c835-102">Access Control and Data Security</span></span>
<span data-ttu-id="8c835-103">BizTalk Server restreint l'accès à ses processus et bases de données en attribuant des droits d'utilisateur minimaux. Vous pouvez ainsi sécuriser certaines données stratégiques du système à l'aide de fonctionnalités de Microsoft Windows Server.</span><span class="sxs-lookup"><span data-stu-id="8c835-103">BizTalk Server limits access to its processes and databases by using minimum user rights; you can help secure important data in the system by using features from Microsoft Windows Server.</span></span> <span data-ttu-id="8c835-104">Pour des raisons de sécurité, les administrateurs de BizTalk Server et les hôtes BizTalk ne doivent pas disposer de plus de droits d'utilisateur qu'il n'en faut pour exécuter leur travail.</span><span class="sxs-lookup"><span data-stu-id="8c835-104">For security reasons, BizTalk Server Administrators and BizTalk Hosts should not have more user rights than necessary to perform their jobs.</span></span>  
  
 <span data-ttu-id="8c835-105">BizTalk contrôle l'accès administratif aux données à l'aide des rôles SQL, par l'intermédiaire d'outils et directement dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="8c835-105">BizTalk controls Administrative access to data using SQL roles, thereby controlling access to data both via tools and directly via the database.</span></span> <span data-ttu-id="8c835-106">Le contrôle de l'accès des hôtes BizTalk aux données s'effectue à l'aide des groupes d'utilisateurs d'hôtes et des comptes.</span><span class="sxs-lookup"><span data-stu-id="8c835-106">BizTalk Host access to data is controlled using Host User groups and accounts.</span></span>  
  
 <span data-ttu-id="8c835-107">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il existe deux rôles d’administration : l’administrateur du serveur BizTalk et l’opérateur de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8c835-107">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator.</span></span> <span data-ttu-id="8c835-108">Chaque fois que vous créez une base de données BizTalk Server dans le cadre d'une installation ou via la console Administration de BizTalk Server, BizTalk Server crée automatiquement des rôles SQL pour ces deux rôles d'administration dans cette base de données.</span><span class="sxs-lookup"><span data-stu-id="8c835-108">Anytime you create a BizTalk Server database through installation or the BizTalk Server Administration Console, BizTalk Server automatically creates SQL roles for both these administrative roles in that database.</span></span> <span data-ttu-id="8c835-109">BizTalk Server attribue à chaque rôle et à tout compte de connexion SQL Server qui lui est associé les droits d'utilisateur minimaux sur les objets SQL Server (tables, vues, procédures stockées, etc.) dont les administrateurs ont besoin pour effectuer des tâches administratives sur cette base de données.</span><span class="sxs-lookup"><span data-stu-id="8c835-109">BizTalk Server grants each role, and any SQL Server login assigned to the role, the minimum user rights needed by administrators on the SQL Server objects (tables, views, stored procedures, etc) to perform administrative tasks on that database.</span></span>  
  
 <span data-ttu-id="8c835-110">Le rôle administrateur de BizTalk Server dispose de privilèges élevés lui donnant accès à des données de configuration et de suivi.</span><span class="sxs-lookup"><span data-stu-id="8c835-110">The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data.</span></span> <span data-ttu-id="8c835-111">Le rôle opérateur de BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.</span><span class="sxs-lookup"><span data-stu-id="8c835-111">The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions.</span></span> <span data-ttu-id="8c835-112">Ce deuxième rôle peut visualiser l'état du service et le flux de message, démarrer ou arrêter des applications et terminer et rétablir des instances de service. Il ne permet pas de modifier la configuration ou d'afficher les propriétés de message ou le contenu.</span><span class="sxs-lookup"><span data-stu-id="8c835-112">This latter role can view service state and message flow and can start or stop applications and terminate and resume service instances, but cannot change configuration or view message properties and content.</span></span>  
  
 <span data-ttu-id="8c835-113">De même, BizTalk Server crée, dans chaque base de données, un rôle SQL pour le groupe d'utilisateurs pour chaque hôte, et attribue à ce rôle les droits d'utilisateur minimaux nécessaires pour que le groupe d'utilisateurs puisse effectuer des tâches pour cet hôte.</span><span class="sxs-lookup"><span data-stu-id="8c835-113">Similarly, BizTalk Server creates in each database a SQL role for the user group for each host, and grants this role the minimum user rights it needs for the user group to perform tasks for that host.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c835-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8c835-114">In This Section</span></span>  
  
-   [<span data-ttu-id="8c835-115">Groupes et comptes d’utilisateur Windows dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8c835-115">Windows Groups and User Accounts in BizTalk Server</span></span>](../core/windows-groups-and-user-accounts-in-biztalk-server.md)  
  
-   [<span data-ttu-id="8c835-116">Contrôle d’accès pour les groupes et comptes de Service</span><span class="sxs-lookup"><span data-stu-id="8c835-116">Access Control for Groups and Service Accounts</span></span>](../core/access-control-for-groups-and-service-accounts.md)  
  
-   [<span data-ttu-id="8c835-117">Contrôle d’accès pour les rôles d’administration</span><span class="sxs-lookup"><span data-stu-id="8c835-117">Access Control for Administrative Roles</span></span>](../core/access-control-for-administrative-roles.md)  
  
-   [<span data-ttu-id="8c835-118">Contrôle d’accès aux informations de l’entreprise</span><span class="sxs-lookup"><span data-stu-id="8c835-118">Access Control to Business Information</span></span>](../core/access-control-to-business-information.md)  
  
-   [<span data-ttu-id="8c835-119">Droits d’utilisateur de sécurité minimales</span><span class="sxs-lookup"><span data-stu-id="8c835-119">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)
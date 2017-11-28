---
title: "Considérations de sécurité pour le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, administrator accounts
- user accounts, BAM
- administrator accounts, BAM portal
- BAM portal, user accounts
- security, BAM portal
ms.assetid: 5c8e6034-dfb8-4dba-b040-0c19504abdb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b0f5220eba5b66daf41dffc7ab74f93df8bb509
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-the-bam-portal"></a><span data-ttu-id="f9630-102">Considérations de sécurité relatives au portail BAM</span><span class="sxs-lookup"><span data-stu-id="f9630-102">Security Considerations for the BAM Portal</span></span>
<span data-ttu-id="f9630-103">Selon le principe des privilèges les plus faibles, les comptes utilisateurs doivent disposer d'autorisations limitées leur permettant uniquement d'effectuer des tâches routinières dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="f9630-103">Using the principle of least privilege, user accounts should have restrictive permissions to perform routine tasks in the BAM portal.</span></span> <span data-ttu-id="f9630-104">Gardez à l'esprit les points suivants lorsque vous configurez les comptes utilisateurs pour permettre au composant BAM de trouver un compromis entre le niveau de sécurité nécessaire et les autorisations d'accès aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f9630-104">Keep the following points in mind as you set up your user accounts for BAM to balance security with appropriate access for users.</span></span>  
  
## <a name="user-accounts"></a><span data-ttu-id="f9630-105">Comptes d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f9630-105">User accounts</span></span>  
 <span data-ttu-id="f9630-106">Comptes d’utilisateur avec les autorisations minimales ne sont pas en mesure d’utiliser le navigationfeature distribuée de portail BAM.</span><span class="sxs-lookup"><span data-stu-id="f9630-106">User accounts with minimum permissions are not able to use the BAM portal distributed navigationfeature.</span></span> <span data-ttu-id="f9630-107">Pour pouvoir l'utiliser, ces comptes doivent disposer des autorisations leur permettant d'accéder aux services Web, depuis un ordinateur distant ou local.</span><span class="sxs-lookup"><span data-stu-id="f9630-107">To be able to use this feature, these accounts must have sufficient permissions to allow access to the Web services on the remote computer as well as on the local computer.</span></span>  
  
 <span data-ttu-id="f9630-108">Les comptes utilisateur ayant accès aux services Web BAM doivent disposer des autorisations d'accès à toutes les bases de données référencées et doivent y être membres du rôle BAM_ManagementWS.</span><span class="sxs-lookup"><span data-stu-id="f9630-108">User accounts for the BAM Web services must have permissions to access all referenced databases and must be a member of the BAM_ManagementWS role in the referenced databases.</span></span>  
  
 <span data-ttu-id="f9630-109">Selon le type d'utilisateur mentionné, tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f9630-109">For the following user types, you should be aware of these considerations:</span></span>  
  
-   <span data-ttu-id="f9630-110">Utilisateurs de domaine : ils doivent disposer d'autorisations d'accès sur des ordinateurs distants hébergeant des bases de données d'importation principales accessibles.</span><span class="sxs-lookup"><span data-stu-id="f9630-110">Domain Users, must have access permissions on remote computers that host Primary Import databases that are being accessed.</span></span>  
  
-   <span data-ttu-id="f9630-111">Utilisateurs auxquels un rôle d'utilisateur local a été attribué : ils ne peuvent pas utiliser la fonctionnalité de navigation distribuée.</span><span class="sxs-lookup"><span data-stu-id="f9630-111">Users who are assigned Local User role, cannot use distributed navigation.</span></span>  
  
## <a name="administrator-accounts"></a><span data-ttu-id="f9630-112">Comptes d'administrateur</span><span class="sxs-lookup"><span data-stu-id="f9630-112">Administrator accounts</span></span>  
 <span data-ttu-id="f9630-113">Les administrateurs doivent être membres des groupes securityadmin ou sysadmin pour accorder des autorisations d'accès aux utilisateurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="f9630-113">Administrators must be members of the securityadmin or sysadmin groups to grant permissions to domain users.</span></span>  
  
 <span data-ttu-id="f9630-114">Pour pouvoir exécuter l'utilitaire de gestion de l'analyse BAM, vous devez être défini en tant qu'opérateur de base de données au moins pour les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="f9630-114">To run the BAM Management utility, you must be at least a database operator for the BAM databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9630-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9630-115">See Also</span></span>  
 [<span data-ttu-id="f9630-116">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="f9630-116">BAM Portal</span></span>](../core/bam-portal.md)
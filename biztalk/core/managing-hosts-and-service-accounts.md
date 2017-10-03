---
title: "La gestion des ordinateurs hôtes et les comptes de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, managing
- managing [user accounts]
- service accounts, security
- managing [hosts], security
- security, hosts
- managing [Windows groups]
- hosts, security
- security, service accounts
- Windows groups, managing
- user accounts, managing
ms.assetid: 25797571-f1f9-42a4-8fff-5b03076bbe36
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0099e683fba7c5f4e2400ad2f9ce005928b0a2aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-hosts-and-service-accounts"></a><span data-ttu-id="7d57c-102">Gestion des hôtes et des comptes de service</span><span class="sxs-lookup"><span data-stu-id="7d57c-102">Managing Hosts and Service Accounts</span></span>
<span data-ttu-id="7d57c-103">Après avoir configuré BizTalk Server, vous devez gérer les groupes et les comptes d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="7d57c-103">After you configure BizTalk Server, you must manage Windows groups and user accounts.</span></span> <span data-ttu-id="7d57c-104">Cette section fournit des informations sur la gestion de ces comptes pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7d57c-104">This section provides information about how to manage these accounts for BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d57c-105">Pour une installation multiserveur de BizTalk Server, vous devez utiliser un groupe global de domaine.</span><span class="sxs-lookup"><span data-stu-id="7d57c-105">For a multiserver installation of BizTalk Server you must use a Domain Global group.</span></span> <span data-ttu-id="7d57c-106">Pour une installation monoserveur de BizTalk Server, vous pouvez utiliser soit un groupe global de domaine soit un groupe local.</span><span class="sxs-lookup"><span data-stu-id="7d57c-106">For a single server installation of BizTalk Server you can use either a Domain Global group or a local group.</span></span>  
  
 <span data-ttu-id="7d57c-107">Vous devez être un administrateur Windows pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d57c-107">You must be a Windows administrator to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="7d57c-108">créer un groupe d'hôtes Windows ;</span><span class="sxs-lookup"><span data-stu-id="7d57c-108">Create a host Windows group</span></span>  
  
-   <span data-ttu-id="7d57c-109">créer des comptes de service pour chaque instance d'hôte ;</span><span class="sxs-lookup"><span data-stu-id="7d57c-109">Create service accounts for each host instance</span></span>  
  
-   <span data-ttu-id="7d57c-110">ajouter les comptes de service au groupe d'hôtes Windows ;</span><span class="sxs-lookup"><span data-stu-id="7d57c-110">Add the service accounts to the host Windows group</span></span>  
  
-   <span data-ttu-id="7d57c-111">modifier le groupe Windows associé à l'hôte.</span><span class="sxs-lookup"><span data-stu-id="7d57c-111">Modify the Windows group associated with the host</span></span>  
  
 <span data-ttu-id="7d57c-112">Pour une liste complète et une description des groupes et leurs comptes d’utilisateur associés dans BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="7d57c-112">For a complete list and description of the groups and their affiliated user accounts in the BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="7d57c-113">Pour plus d’informations des droits de l’utilisateur de sécurité minimales pour les tâches administratives, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).</span><span class="sxs-lookup"><span data-stu-id="7d57c-113">For more information the minimum security user rights for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d57c-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7d57c-114">In This Section</span></span>  
  
-   [<span data-ttu-id="7d57c-115">Service de créer des comptes pour les nouveaux ordinateurs hôtes et les Instances d’hôte</span><span class="sxs-lookup"><span data-stu-id="7d57c-115">How to Create Service Accounts for New Hosts and Host Instances</span></span>](../core/how-to-create-service-accounts-for-new-hosts-and-host-instances.md)  
  
-   [<span data-ttu-id="7d57c-116">Comment modifier les comptes de Service et les mots de passe</span><span class="sxs-lookup"><span data-stu-id="7d57c-116">How to Change Service Accounts and Passwords</span></span>](../core/how-to-change-service-accounts-and-passwords.md)
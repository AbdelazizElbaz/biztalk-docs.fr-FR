---
title: "Gestion de la sécurité de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- security, user accounts
- security, passwords
- certificates, security
- security, certificates
- security, BizTalk Server
- passwords, security
- user accounts, security
ms.assetid: adc89b0a-9846-4c99-b0fc-a32fc56ed769
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f31ef3483661b20ff62cadb0ec601282a05af9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-server-security"></a><span data-ttu-id="d9a09-102">Gestion de la sécurité de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d9a09-102">Managing BizTalk Server Security</span></span>
<span data-ttu-id="d9a09-103">Pour bénéficier d'un environnement Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sécurisé, vous devez gérer des comptes, des certificats et des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="d9a09-103">Maintaining a secure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment requires that you manage accounts, certificates, and passwords.</span></span> <span data-ttu-id="d9a09-104">Pour garantir la sécurité des documents commerciaux traités par BizTalk Server, les administrateurs BizTalk Server gèrent les comptes et certificats suivants :</span><span class="sxs-lookup"><span data-stu-id="d9a09-104">To help ensure the security of the business documents handled by BizTalk Server, BizTalk Server administrators manage the following accounts and certificates:</span></span>  
  
-   <span data-ttu-id="d9a09-105">**Groupe Administrateurs BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d9a09-105">**BizTalk Server Administrators group**.</span></span> <span data-ttu-id="d9a09-106">Les utilisateurs qui exécutent des tâches d'administration via la console Administration de BizTalk ou le fournisseur Microsoft Windows Management Instrumentation (WMI) doivent bénéficier des autorisations appropriées dans Microsoft SQL Server et Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="d9a09-106">For users to perform administrative tasks either through the BizTalk Administration console or by using the Microsoft Windows Management Instrumentation (WMI) provider, they must be granted the proper privileges in Microsoft SQL Server and Microsoft Windows.</span></span> <span data-ttu-id="d9a09-107">Pour plus d’informations sur les privilèges pour les tâches administratives, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d9a09-107">For more information about the privileges for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
     <span data-ttu-id="d9a09-108">Pour plus d’informations sur l’ajout d’utilisateurs au groupe Administrateurs de BizTalk Server ou la suppression des utilisateurs du groupe Administrateurs de BizTalk Server, consultez [comment gérer le groupe d’administrateurs BizTalk Server](../core/how-to-manage-the-biztalk-server-administrators-group.md).</span><span class="sxs-lookup"><span data-stu-id="d9a09-108">For information about adding users to the BizTalk Server Administrators group or removing users from the BizTalk Server Administrators group, see [How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md).</span></span>  
  
     <span data-ttu-id="d9a09-109">Pour plus d’informations sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md).</span><span class="sxs-lookup"><span data-stu-id="d9a09-109">For more information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).</span></span>  
  
-   <span data-ttu-id="d9a09-110">**Groupe opérateurs BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d9a09-110">**BizTalk Server Operators group**.</span></span> <span data-ttu-id="d9a09-111">Le rôle Opérateurs BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.</span><span class="sxs-lookup"><span data-stu-id="d9a09-111">The BizTalk Server Operator is a low privileged role that only has access to monitoring and troubleshooting actions.</span></span>  
  
     <span data-ttu-id="d9a09-112">Les membres du groupe Opérateurs BizTalk Server peuvent effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9a09-112">Members of the BizTalk Server Operators group can do the following:</span></span>  
  
    -   <span data-ttu-id="d9a09-113">Afficher l'état et le flux de messages du service.</span><span class="sxs-lookup"><span data-stu-id="d9a09-113">View service state and message flow.</span></span>  
  
    -   <span data-ttu-id="d9a09-114">Démarrer ou arrêter des applications.</span><span class="sxs-lookup"><span data-stu-id="d9a09-114">Start or stop applications.</span></span>  
  
    -   <span data-ttu-id="d9a09-115">Démarrer ou arrêter des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d9a09-115">Start or stop orchestrations.</span></span>  
  
    -   <span data-ttu-id="d9a09-116">Arrêter ou démarrer des ports d'envoi et des groupes de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d9a09-116">Start or stop send ports or send port groups.</span></span>  
  
    -   <span data-ttu-id="d9a09-117">Activer ou désactiver des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="d9a09-117">Enable or disable receive locations.</span></span> <span data-ttu-id="d9a09-118">Les modifications ne sont pas prises en compte avant la fin de l'intervalle d'actualisation du cache de 60 secondes (intervalle par défaut).</span><span class="sxs-lookup"><span data-stu-id="d9a09-118">The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default.</span></span> <span data-ttu-id="d9a09-119">Cet intervalle est défini au niveau du groupe BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d9a09-119">The cache refresh interval is set at the BizTalk Server group level.</span></span>  
  
    -   <span data-ttu-id="d9a09-120">Terminer et reprendre les instances de service.</span><span class="sxs-lookup"><span data-stu-id="d9a09-120">Terminate and resume service instances.</span></span>  
  
     <span data-ttu-id="d9a09-121">Les membres du groupe Opérateurs BizTalk Server ne peuvent pas effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9a09-121">Members of the BizTalk Server Operators group cannot do the following:</span></span>  
  
    -   <span data-ttu-id="d9a09-122">Modifier la configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d9a09-122">Modify the configuration for BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="d9a09-123">Afficher les propriétés de contexte de message marquées comme informations d'identification personnelle ou les corps de message.</span><span class="sxs-lookup"><span data-stu-id="d9a09-123">View message context properties classified as Personally Identifiable Information (PII) or message bodies.</span></span>  
  
    -   <span data-ttu-id="d9a09-124">Modifier le routage des messages, par exemple supprimer ou ajouter des abonnements au système en cours d'exécution, ou publier des messages dans un composant d'exécution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d9a09-124">Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9a09-125">Un utilisateur membre du groupe Opérateurs BizTalk Server et administrateur local sur les ordinateurs exécutant BizTalk Server peut accéder aux données présentes sur ceux-ci et non disponibles aux membres du groupe Opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d9a09-125">If a user who is a member of the BizTalk Server Operators group is also a local administrator on the computers running BizTalk Server, this user can access data beyond the role of the Operators group on these computers.</span></span> <span data-ttu-id="d9a09-126">Pour plus d’informations, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d9a09-126">For more information, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9a09-127">Si vous souhaitez autoriser un utilisateur membre du groupe Opérateurs BizTalk Server à surveiller des serveurs BizTalk distants, cet utilisateur doit également être membre du groupe Administrateurs local sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d9a09-127">If you want to allow a user who is a member of the BizTalk Server Operators group to monitor remote BizTalk servers, this user must also be a member of the local Administrators group on the remote computers.</span></span>  
  
-   <span data-ttu-id="d9a09-128">**Les comptes de service et les hôtes**.</span><span class="sxs-lookup"><span data-stu-id="d9a09-128">**Hosts and service accounts**.</span></span> <span data-ttu-id="d9a09-129">Lors de la création d'un hôte et des instances d'hôte associées, vous devez fournir au groupe Windows les informations d'identification des comptes hôtes et de service pour chaque instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="d9a09-129">When creating a host and its associated host instances, you must provide the Windows group for the host and the service account credentials for each host instance.</span></span> <span data-ttu-id="d9a09-130">Vous devez vous assurer que les comptes de service d'instance d'hôte sont membres du groupe Windows pour l'hôte.</span><span class="sxs-lookup"><span data-stu-id="d9a09-130">You must ensure that the host instance service accounts are members of the Windows group for the host.</span></span>  
  
-   <span data-ttu-id="d9a09-131">**Certificats de signature**.</span><span class="sxs-lookup"><span data-stu-id="d9a09-131">**Signing certificates**.</span></span> <span data-ttu-id="d9a09-132">Les certificats de signature (certificats de clé privée) sont spécifiés pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d9a09-132">Signing certificates (private key certificates) are specified for the BizTalk group.</span></span> <span data-ttu-id="d9a09-133">Ils sont facultatifs et un administrateur BizTalk Server peut les modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="d9a09-133">These are optional and can be changed at any time by a BizTalk Server administrator.</span></span>  
  
 <span data-ttu-id="d9a09-134">Pour plus d’informations relatives aux comptes Windows qui utilise de BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="d9a09-134">For more complete information about Windows accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9a09-135">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d9a09-135">In This Section</span></span>  
  
-   [<span data-ttu-id="d9a09-136">Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows</span><span class="sxs-lookup"><span data-stu-id="d9a09-136">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)  
  
-   [<span data-ttu-id="d9a09-137">Meilleures pratiques pour la gestion des certificats</span><span class="sxs-lookup"><span data-stu-id="d9a09-137">Best Practices for Managing Certificates</span></span>](../core/best-practices-for-managing-certificates1.md)  
  
-   [<span data-ttu-id="d9a09-138">La gestion des comptes d’utilisateurs et groupes Windows</span><span class="sxs-lookup"><span data-stu-id="d9a09-138">Managing Windows Groups and User Accounts</span></span>](../core/managing-windows-groups-and-user-accounts.md)
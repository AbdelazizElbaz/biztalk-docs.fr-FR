---
title: "Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, Windows groups
- authenticating, best practices
- Windows groups, security
- best practices, user accounts
- best practices, security
- security, best practices
- user accounts, security
- authenticating, security
- Windows groups, best practices
- best practices, authenticating
- user accounts, best practices
- hosts, security
- hosts, best practices
- best practices, hosts
ms.assetid: 0c4a141e-97ce-434a-8e45-a56c634bbd6c
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f7560e3867bf290f20e0f2f49a740d7298131b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-managing-windows-groups-and-user-accounts"></a><span data-ttu-id="49bd8-102">Méthodes conseillées pour la gestion des groupes et comptes d'utilisateur Windows</span><span class="sxs-lookup"><span data-stu-id="49bd8-102">Best Practices for Managing Windows Groups and User Accounts</span></span>
<span data-ttu-id="49bd8-103">Cette section présente les meilleures pratiques relatives à la gestion de la sécurité dans les groupes et les comptes d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="49bd8-103">This section contains best practices and tips for managing security for Windows groups and user accounts.</span></span>  
  
-   <span data-ttu-id="49bd8-104">**Utiliser des comptes de service avec des privilèges minimaux requis pour les instances d’hôte**</span><span class="sxs-lookup"><span data-stu-id="49bd8-104">**Use service accounts with minimum privileges necessary for host instances**</span></span>  
  
     <span data-ttu-id="49bd8-105">Pour garantir la sécurité de votre environnement BizTalk Server, il est recommandé d'utiliser les comptes de service avec les privilèges minimaux requis pour l'exécution des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="49bd8-105">To help ensure the security of your BizTalk Server environment, we recommend that you use service accounts with the minimum privileges necessary to run host instances.</span></span> <span data-ttu-id="49bd8-106">Pour plus d’informations sur les privilèges minimaux qui requièrent des comptes de service, consultez [contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md).</span><span class="sxs-lookup"><span data-stu-id="49bd8-106">For more information about the minimum privileges that service accounts require, see [Access Control and Data Security](../core/access-control-and-data-security.md).</span></span>  
  
-   <span data-ttu-id="49bd8-107">**Utilisez différents groupes d’utilisateurs pour l’authentification de la confiance et les hôtes non approuvés**</span><span class="sxs-lookup"><span data-stu-id="49bd8-107">**Use different user groups for authentication trusted and non-trusted hosts**</span></span>  
  
     <span data-ttu-id="49bd8-108">Pour vérifier que les hôtes non approuvés par authentification bénéficient de moins de privilèges que les hôtes approuvés par authentification, vous devez utiliser des comptes de service différents pour chaque hôte.</span><span class="sxs-lookup"><span data-stu-id="49bd8-108">To ensure that non-authentication trusted hosts have fewer privileges than authentication trusted hosts, you must use different service accounts for each host.</span></span>  
  
-   <span data-ttu-id="49bd8-109">**Utiliser un groupe d’utilisateurs différents pour chaque hôte BizTalk**</span><span class="sxs-lookup"><span data-stu-id="49bd8-109">**Use a different user group for each BizTalk Host**</span></span>  
  
     <span data-ttu-id="49bd8-110">Pour maximiser la limite de sécurité entre les hôtes, il est recommandé d'utiliser différents groupes d'utilisateurs Windows pour chaque hôte BizTalk de votre groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="49bd8-110">To maximize the security boundary between hosts, we recommend that you use a different Windows user group for each BizTalk Host in your BizTalk group.</span></span>  
  
-   <span data-ttu-id="49bd8-111">**Supprimer l’utilisateur de l’installation à partir du groupe Administrateurs de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="49bd8-111">**Remove the installation user from the BizTalk Server Administrators group**</span></span>  
  
     <span data-ttu-id="49bd8-112">Lorsque vous installez BizTalk Server sur un seul serveur avec des groupes locaux, l'utilisateur effectuant une installation interactive de BizTalk Server est automatiquement ajouté au groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="49bd8-112">When you install BizTalk Server on a single computer with local groups, the user performing an interactive installation of BizTalk Server is automatically added to the BizTalk Server Administrators group.</span></span> <span data-ttu-id="49bd8-113">De cette manière, l'utilisateur peut configurer BizTalk Server avec le Gestionnaire de configuration.</span><span class="sxs-lookup"><span data-stu-id="49bd8-113">This allows that user to configure BizTalk Server with the Configuration Manager.</span></span>  
  
     <span data-ttu-id="49bd8-114">Si l'utilisateur qui installe le serveur BizTalk Server n'est pas l'administrateur de ce dernier, il est recommandé de le supprimer du groupe Administrateurs BizTalk Server une fois le serveur BizTalk Server configuré.</span><span class="sxs-lookup"><span data-stu-id="49bd8-114">If the user who installs BizTalk Server will not be administering BizTalk Server, we recommend that you remove this user from the BizTalk Server Administrators group after BizTalk Server is configured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bd8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49bd8-115">See Also</span></span>  
 [<span data-ttu-id="49bd8-116">Gestion de la sécurité de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="49bd8-116">Managing BizTalk Server Security</span></span>](../core/managing-biztalk-server-security.md)
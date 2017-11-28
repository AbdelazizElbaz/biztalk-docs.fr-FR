---
title: "À l’aide de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO]
- SSO, managing
ms.assetid: e7245632-9c71-4b1f-836d-a4ea1dd6e5ee
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 850425f140b526baf251568f09ab47db9115e8ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-sso"></a><span data-ttu-id="a363c-102">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-102">Using SSO</span></span>
<span data-ttu-id="a363c-103">Le composant logiciel enfichable MMC ou l'utilitaire de gestion de ligne de commande (ssomanage) permet de gérer le système SSO.</span><span class="sxs-lookup"><span data-stu-id="a363c-103">You can use either the MMC Snap-in or the command line management utility (ssomanage) to manage the SSO system.</span></span> <span data-ttu-id="a363c-104">Cela concerne les activités telles que la mise à jour de la base de données SSO, l'ajout, la suppression, la gestion d'applications et l'administration de mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a363c-104">This includes activities such as updating the SSO database, adding, deleting, and managing applications, and administering user mappings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a363c-105">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter les outils de ligne de commande SSO avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a363c-105">On a system that supports User Account Control (UAC), you may need to run the SSO command line tools with Administrative privileges.</span></span>  
  
 <span data-ttu-id="a363c-106">Seuls les administrateurs SSO peuvent réaliser ces tâches.</span><span class="sxs-lookup"><span data-stu-id="a363c-106">Only Single Sign-On Administrators can perform these tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a363c-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a363c-107">In This Section</span></span>  
  
-   [<span data-ttu-id="a363c-108">Comment configurer le serveur d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-108">How to Set the SSO Server</span></span>](../core/how-to-set-the-sso-server.md)  
  
-   [<span data-ttu-id="a363c-109">Comment activer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-109">How to Enable SSO</span></span>](../core/how-to-enable-sso.md)  
  
-   [<span data-ttu-id="a363c-110">Comment modifier le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="a363c-110">How to Change the Master Secret Server</span></span>](../core/how-to-change-the-master-secret-server.md)  
  
-   [<span data-ttu-id="a363c-111">Comment désactiver l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-111">How to Disable SSO</span></span>](../core/how-to-disable-sso.md)  
  
-   [<span data-ttu-id="a363c-112">Comment mettre à jour la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="a363c-112">How to Update the SSO Database</span></span>](../core/how-to-update-the-sso-database.md)  
  
-   [<span data-ttu-id="a363c-113">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="a363c-113">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="a363c-114">Comment configurer les Tickets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-114">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)  
  
-   [<span data-ttu-id="a363c-115">Comment auditer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-115">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="a363c-116">Comment activer SSL pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a363c-116">How to Enable SSL for SSO</span></span>](../core/how-to-enable-ssl-for-sso.md)  
  
-   [<span data-ttu-id="a363c-117">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="a363c-117">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)  
  
-   [<span data-ttu-id="a363c-118">Comment spécifier les administrateurs de l’authentification unique et les applications associées à des administrateurs de comptes</span><span class="sxs-lookup"><span data-stu-id="a363c-118">How to Specify SSO Administrators and Affiliate Administrators Accounts</span></span>](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)  
  
-   [<span data-ttu-id="a363c-119">Gestion des Applications associées</span><span class="sxs-lookup"><span data-stu-id="a363c-119">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)  
  
-   [<span data-ttu-id="a363c-120">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="a363c-120">Managing User Mappings</span></span>](../core/managing-user-mappings.md)  
  
-   [<span data-ttu-id="a363c-121">L’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="a363c-121">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)
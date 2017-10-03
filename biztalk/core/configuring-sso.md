---
title: Configuration de SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, command line utilities
- configuring, SSO
- SSO, interfaces
- SSOConfig [SSO]
- SSO, configuring
- SSOClient [SSO]
- SSO, tools
- SSOManage [SSO]
ms.assetid: 6f755735-9b48-4771-beec-ced844f3d532
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d729633717d709a83c10e9b50c55791029902010
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-sso"></a><span data-ttu-id="ce981-102">Configuration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="ce981-102">Configuring SSO</span></span>
<span data-ttu-id="ce981-103">Vous pouvez configurer l'authentification unique de l'entreprise à l'aide d'utilitaires de ligne de commande, d'outils utilisant l'interface utilisateur ou d'interfaces COM ou Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="ce981-103">You can configure Enterprise Single Sign-On by using command line utilities, UI tools, or COM or Microsoft .NET interfaces.</span></span>  
  
## <a name="sso-command-line-utilities"></a><span data-ttu-id="ce981-104">Utilitaires de ligne de commande SSO</span><span class="sxs-lookup"><span data-stu-id="ce981-104">SSO command line utilities</span></span>  
 <span data-ttu-id="ce981-105">Trois utilitaires de ligne de commande distincts permettent d'effectuer des tâches liées à l'authentification unique de l'entreprise :</span><span class="sxs-lookup"><span data-stu-id="ce981-105">You use three different command line utilities to perform Enterprise Single Sign-On tasks:</span></span>  
  
 <span data-ttu-id="ce981-106">**SSOConfig.**</span><span class="sxs-lookup"><span data-stu-id="ce981-106">**SSOConfig.**</span></span> <span data-ttu-id="ce981-107">permet à un administrateur de l'authentification unique (SSO) de configurer la base de données SSO et de gérer le secret principal.</span><span class="sxs-lookup"><span data-stu-id="ce981-107">Enables an SSO administrator to configure the SSO database and to manage the master secret.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce981-108">L'Assistant Configuration crée la base de données SSO et le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="ce981-108">The Configuration Wizard creates the SSO database and the master secret server.</span></span>  
  
 <span data-ttu-id="ce981-109">**SSOManage.**</span><span class="sxs-lookup"><span data-stu-id="ce981-109">**SSOManage.**</span></span> <span data-ttu-id="ce981-110">Active les administrateurs SSO, administrateurs d’applications associées SSO et administrateurs de l’application mettre à jour la base de données SSO à ajouter, supprimer et gérer des applications, administrer des mappages d’utilisateur et pour définir les informations d’identification de la filiale utilisateurs de l’application.</span><span class="sxs-lookup"><span data-stu-id="ce981-110">Enables SSO administrators, SSO affiliate administrators, and application administrators to update the SSO database to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users.</span></span> <span data-ttu-id="ce981-111">Certaines opérations peuvent être réalisées uniquement par les administrateurs SSO ou uniquement par les administrateurs SSO et les administrateurs d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="ce981-111">Some operations can be performed only by the SSO administrators, or, only by the SSO administrators and SSO affiliate administrators.</span></span> <span data-ttu-id="ce981-112">Toutes les opérations pouvant être réalisées par les administrateurs d'applications peuvent également l'être par les administrateurs SSO et les administrateurs d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="ce981-112">All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and the SSO Affiliate Administrators.</span></span>  
  
 <span data-ttu-id="ce981-113">**SSOClient.**</span><span class="sxs-lookup"><span data-stu-id="ce981-113">**SSOClient.**</span></span> <span data-ttu-id="ce981-114">permet aux utilisateurs de l'authentification unique de gérer leurs propres mappages et de définir leurs informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="ce981-114">Enables Single Sign-On users to manage their own user mappings and set their credentials.</span></span>  
  
 <span data-ttu-id="ce981-115">Pour plus d’informations sur les comptes de l’authentification unique, consultez [groupes utilisateur SSO](../core/sso-user-groups.md).</span><span class="sxs-lookup"><span data-stu-id="ce981-115">For more information about the SSO accounts, see [SSO User Groups](../core/sso-user-groups.md).</span></span>  
  
## <a name="sso-ui-tools"></a><span data-ttu-id="ce981-116">Outils utilisant l'interface utilisateur SSO</span><span class="sxs-lookup"><span data-stu-id="ce981-116">SSO UI tools</span></span>  
 <span data-ttu-id="ce981-117">**Enterprise SSO enfichable MMC.**</span><span class="sxs-lookup"><span data-stu-id="ce981-117">**Enterprise SSO MMC Snap-in.**</span></span> <span data-ttu-id="ce981-118">permet aux administrateurs SSO, aux administrateurs d'applications associées à SSO et aux administrateurs d'application de mettre à jour la base de données SSO afin d'ajouter, de supprimer et de gérer des applications, d'administrer des mappages d'utilisateurs et de définir des informations d'identification pour les utilisateurs d'applications associées.</span><span class="sxs-lookup"><span data-stu-id="ce981-118">Enables SSO Administrators, SSO Affiliate Administrators, and Application Administrators to update the SSO database, to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users.</span></span> <span data-ttu-id="ce981-119">Certaines opérations peuvent être effectuées uniquement par les administrateurs de l’authentification unique, ou uniquement par l’authentification unique, les administrateurs et l’authentification unique associée aux administrateurs.</span><span class="sxs-lookup"><span data-stu-id="ce981-119">Some operations can be performed only by the SSO administrators, or only by the SSO administrators and SSO affiliate administrators.</span></span> <span data-ttu-id="ce981-120">Toutes les opérations qui peuvent être effectuées par les administrateurs d’applications peuvent également être effectuées par les administrateurs SSO et administrateurs d’applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="ce981-120">All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and SSO Affiliate Administrators.</span></span>  
  
 <span data-ttu-id="ce981-121">**Utilitaire Client SSO :**</span><span class="sxs-lookup"><span data-stu-id="ce981-121">**SSO Client Utility.**</span></span> <span data-ttu-id="ce981-122">permet aux utilisateurs finaux de gérer leurs propres mappages et de définir leurs informations d'identification à l'aide de l'outil utilisant l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ce981-122">Enables end users to manage their own mappings and set their credentials using the UI tool.</span></span>  
  
## <a name="sso-com-and-net-interfaces"></a><span data-ttu-id="ce981-123">Interfaces COM et .NET SSO</span><span class="sxs-lookup"><span data-stu-id="ce981-123">SSO COM and .NET interfaces</span></span>  
 <span data-ttu-id="ce981-124">Dans l'optique de simplifier l'administration du système SSO, l'authentification unique de l'entreprise propose des interfaces de programmation COM et .NET qui vous permettent de créer des composants personnalisés ainsi que des scripts.</span><span class="sxs-lookup"><span data-stu-id="ce981-124">Enterprise Single Sign-On provides COM and .NET programmatic interfaces that enable you to create custom components, and to create scripts to facilitate the administration of the SSO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce981-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce981-125">See Also</span></span>  
 [<span data-ttu-id="ce981-126">Composants de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="ce981-126">SSO Components</span></span>](../core/sso-components.md)
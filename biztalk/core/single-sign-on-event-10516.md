---
title: "Single Sign-On : Événement 10516 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d20df92f-c995-4cbc-a8f9-21cea30b82c9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b74ca4a47bc62d28b25564bd5843729c56362
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10516"></a><span data-ttu-id="23d92-102">Single Sign-On : Événement 10516</span><span class="sxs-lookup"><span data-stu-id="23d92-102">Single Sign-On: Event 10516</span></span>
## <a name="details"></a><span data-ttu-id="23d92-103">Détails</span><span class="sxs-lookup"><span data-stu-id="23d92-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23d92-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="23d92-104">Product Name</span></span>|<span data-ttu-id="23d92-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="23d92-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="23d92-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="23d92-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="23d92-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="23d92-107">Event ID</span></span>|<span data-ttu-id="23d92-108">10516</span><span class="sxs-lookup"><span data-stu-id="23d92-108">10516</span></span>|  
|<span data-ttu-id="23d92-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="23d92-109">Event Source</span></span>|<span data-ttu-id="23d92-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="23d92-110">ENTSSO</span></span>|  
|<span data-ttu-id="23d92-111">Composant</span><span class="sxs-lookup"><span data-stu-id="23d92-111">Component</span></span>|<span data-ttu-id="23d92-112">N\A</span><span class="sxs-lookup"><span data-stu-id="23d92-112">N\A</span></span>|  
|<span data-ttu-id="23d92-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="23d92-113">Symbolic Name</span></span>|<span data-ttu-id="23d92-114">SSO_ERROR_BAD_SSO_APP_ADMIN</span><span class="sxs-lookup"><span data-stu-id="23d92-114">SSO_ERROR_BAD_SSO_APP_ADMIN</span></span>|  
|<span data-ttu-id="23d92-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="23d92-115">Message Text</span></span>|<span data-ttu-id="23d92-116">Le compte Administrateurs d'applications associées à SSO n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="23d92-116">The SSO Affiliate Administrators account is not valid.</span></span> <span data-ttu-id="23d92-117">S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="23d92-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="23d92-118">S'il s'agit d'un compte de domaine, contactez votre administrateur système.</span><span class="sxs-lookup"><span data-stu-id="23d92-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="23d92-119">Activez SSO lorsque le compte est valide.%r</span><span class="sxs-lookup"><span data-stu-id="23d92-119">Enable SSO when the account is valid.%r</span></span><br /><br /> <span data-ttu-id="23d92-120">Administrateurs d’applications associées SSO : %1 %r</span><span class="sxs-lookup"><span data-stu-id="23d92-120">SSO Affiliate Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="23d92-121">Comptes non valides : %2 %r</span><span class="sxs-lookup"><span data-stu-id="23d92-121">Invalid accounts: %2%r</span></span><br /><br /> <span data-ttu-id="23d92-122">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="23d92-122">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23d92-123">Explication</span><span class="sxs-lookup"><span data-stu-id="23d92-123">Explanation</span></span>  
 <span data-ttu-id="23d92-124">Cette erreur indique que le groupe ou le compte Administrateurs d'applications associées à SSO créé par l'authentification unique de l'entreprise ne correspond pas à un compte Windows valide.</span><span class="sxs-lookup"><span data-stu-id="23d92-124">This Error event indicates that the SSO Affiliate Administrator account or group created by Enterprise Sing Sign-on is not a valid Windows account.</span></span> <span data-ttu-id="23d92-125">Le compte Administrateurs d'applications associées à SSO peut correspondre à un compte individuel ou de groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="23d92-125">The SSO Affiliate Administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="23d92-126">Le compte Administrateurs d'applications associées à SSO peut également correspondre à un compte de groupe local ou de domaine.</span><span class="sxs-lookup"><span data-stu-id="23d92-126">The SSO Affiliate Administrator account can also be either a domain or local group account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23d92-127">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="23d92-127">User Action</span></span>  
 <span data-ttu-id="23d92-128">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="23d92-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="23d92-129">Assurez-vous que le compte Administrateurs d'applications associées à SSO existe.</span><span class="sxs-lookup"><span data-stu-id="23d92-129">Verify the SSO Affiliate Administrator account exists.</span></span>  
  
 <span data-ttu-id="23d92-130">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="23d92-130">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="23d92-131">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="23d92-131">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="23d92-132">Comment mettre à jour la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="23d92-132">How to Update the SSO Database</span></span>](../core/how-to-update-the-sso-database.md)
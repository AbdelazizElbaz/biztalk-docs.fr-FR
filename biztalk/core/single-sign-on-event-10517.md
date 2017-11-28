---
title: "Single Sign-On : Événement 10517 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b63e4b0-0ef6-45c2-b8b1-55ac20e79e26
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2716eb7d331ec5c15070555a028c00310188856c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10517"></a><span data-ttu-id="d8cfb-102">Single Sign-On : Événement 10517</span><span class="sxs-lookup"><span data-stu-id="d8cfb-102">Single Sign-On: Event 10517</span></span>
## <a name="details"></a><span data-ttu-id="d8cfb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d8cfb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8cfb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d8cfb-104">Product Name</span></span>|<span data-ttu-id="d8cfb-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d8cfb-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d8cfb-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d8cfb-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d8cfb-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d8cfb-107">Event ID</span></span>|<span data-ttu-id="d8cfb-108">10517</span><span class="sxs-lookup"><span data-stu-id="d8cfb-108">10517</span></span>|  
|<span data-ttu-id="d8cfb-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d8cfb-109">Event Source</span></span>|<span data-ttu-id="d8cfb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d8cfb-110">ENTSSO</span></span>|  
|<span data-ttu-id="d8cfb-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d8cfb-111">Component</span></span>|<span data-ttu-id="d8cfb-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d8cfb-112">N\A</span></span>|  
|<span data-ttu-id="d8cfb-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d8cfb-113">Symbolic Name</span></span>|<span data-ttu-id="d8cfb-114">SSO_ERROR_BAD_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="d8cfb-114">SSO_ERROR_BAD_SSO_ADMIN</span></span>|  
|<span data-ttu-id="d8cfb-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d8cfb-115">Message Text</span></span>|<span data-ttu-id="d8cfb-116">Le compte Administrateurs de l'authentification unique n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-116">The SSO Administrators account is not valid.</span></span> <span data-ttu-id="d8cfb-117">S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="d8cfb-118">S'il s'agit d'un compte de domaine, contactez votre administrateur système.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="d8cfb-119">Activez SSO lorsque le compte est valide.%r</span><span class="sxs-lookup"><span data-stu-id="d8cfb-119">Enable SSO when the account is valid.%r</span></span><br /><br /> <span data-ttu-id="d8cfb-120">Les administrateurs de l’authentification unique : %1 %r</span><span class="sxs-lookup"><span data-stu-id="d8cfb-120">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="d8cfb-121">Comptes non valides : %2 %r</span><span class="sxs-lookup"><span data-stu-id="d8cfb-121">Invalid accounts: %2%r</span></span><br /><br /> <span data-ttu-id="d8cfb-122">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="d8cfb-122">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d8cfb-123">Explication</span><span class="sxs-lookup"><span data-stu-id="d8cfb-123">Explanation</span></span>  
 <span data-ttu-id="d8cfb-124">Cet événement d'erreur indique que le compte Administrateurs de l'authentification unique spécifié pour l'authentification unique de l'entreprise n'est pas un compte Windows valide.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-124">This Error event indicates that the SSO Administrators account specified for Enterprise Single Sign-On is not a valid Windows account.</span></span> <span data-ttu-id="d8cfb-125">Le compte de service exécutant le service d'authentification unique de l'entreprise doit être membre de ce compte.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-125">The service account running the Enterprise Single Sign-On service must be a member of this account.</span></span> <span data-ttu-id="d8cfb-126">Le compte Administrateurs de l'authentification unique peut être un compte de groupe Windows ou un compte individuel.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-126">The SSO Administrators account can be either a Windows group account or an individual account.</span></span> <span data-ttu-id="d8cfb-127">Il peut également être un compte de groupe de domaine ou local.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-127">The SSO Administrators account can also be either a domain or local group account.</span></span> <span data-ttu-id="d8cfb-128">Lorsque vous utilisez un compte individuel, vous ne pouvez pas modifier ce compte en un autre compte individuel.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-128">When using an individual account, you cannot change this account to another individual account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8cfb-129">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d8cfb-129">User Action</span></span>  
 <span data-ttu-id="d8cfb-130">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d8cfb-130">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="d8cfb-131">Vérifiez que le compte Administrateurs de l'authentification unique existe.</span><span class="sxs-lookup"><span data-stu-id="d8cfb-131">Verify the SSO Administrators account exists.</span></span>  
  
 <span data-ttu-id="d8cfb-132">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="d8cfb-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d8cfb-133">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d8cfb-133">SSO User Groups</span></span>](../core/sso-user-groups.md)
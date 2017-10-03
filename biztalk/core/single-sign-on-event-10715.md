---
title: "Single Sign-On : Événement 10715 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24bf65f00d9ef915d585c91aa06900b96d4b44d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10715"></a><span data-ttu-id="c6c22-102">Single Sign-On : Événement 10715</span><span class="sxs-lookup"><span data-stu-id="c6c22-102">Single Sign-On: Event 10715</span></span>
## <a name="details"></a><span data-ttu-id="c6c22-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c6c22-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6c22-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c6c22-104">Product Name</span></span>|<span data-ttu-id="c6c22-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c6c22-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c6c22-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c6c22-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c6c22-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c6c22-107">Event ID</span></span>|<span data-ttu-id="c6c22-108">10715</span><span class="sxs-lookup"><span data-stu-id="c6c22-108">10715</span></span>|  
|<span data-ttu-id="c6c22-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c6c22-109">Event Source</span></span>|<span data-ttu-id="c6c22-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c6c22-110">ENTSSO</span></span>|  
|<span data-ttu-id="c6c22-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c6c22-111">Component</span></span>|<span data-ttu-id="c6c22-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c6c22-112">N\A</span></span>|  
|<span data-ttu-id="c6c22-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c6c22-113">Symbolic Name</span></span>|<span data-ttu-id="c6c22-114">SSO_WARN_NO_CREATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="c6c22-114">SSO_WARN_NO_CREATE_ADAPTER</span></span>|  
|<span data-ttu-id="c6c22-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c6c22-115">Message Text</span></span>|<span data-ttu-id="c6c22-116">L'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir créer des adaptateurs.%r</span><span class="sxs-lookup"><span data-stu-id="c6c22-116">The client user must be a member of the SSO Administrators account to create adapters.%r</span></span><br /><br /> <span data-ttu-id="c6c22-117">L’utilisateur client : %1 %r</span><span class="sxs-lookup"><span data-stu-id="c6c22-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="c6c22-118">Les administrateurs SSO : %2 %r</span><span class="sxs-lookup"><span data-stu-id="c6c22-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="c6c22-119">Carte : %3 %r</span><span class="sxs-lookup"><span data-stu-id="c6c22-119">Adapter: %3%r</span></span><br /><br /> <span data-ttu-id="c6c22-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="c6c22-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6c22-121">Explication</span><span class="sxs-lookup"><span data-stu-id="c6c22-121">Explanation</span></span>  
 <span data-ttu-id="c6c22-122">Cet avertissement indique que l'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir créer des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="c6c22-122">This Warning event indicates that the client user must be a member of the SSO Administrators account to create adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6c22-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c6c22-123">User Action</span></span>  
 <span data-ttu-id="c6c22-124">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6c22-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="c6c22-125">Connectez-vous à l'aide d'un compte appartenant au groupe Administrateurs SSO.</span><span class="sxs-lookup"><span data-stu-id="c6c22-125">Logon with an account that belongs to the SSO Administrators group.</span></span>  
  
 <span data-ttu-id="c6c22-126">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c6c22-126">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="c6c22-127">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="c6c22-127">SSO User Groups</span></span>](../core/sso-user-groups.md)
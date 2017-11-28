---
title: "Single Sign-On : Événement 10519 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e709957e-a690-4a44-a863-07b2a55dae7b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928892ff1d0ee461a26095ddc7a72fd3accecf10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10519"></a><span data-ttu-id="3bbda-102">Single Sign-On : Événement 10519</span><span class="sxs-lookup"><span data-stu-id="3bbda-102">Single Sign-On: Event 10519</span></span>
## <a name="details"></a><span data-ttu-id="3bbda-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3bbda-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bbda-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3bbda-104">Product Name</span></span>|<span data-ttu-id="3bbda-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3bbda-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3bbda-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3bbda-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3bbda-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3bbda-107">Event ID</span></span>|<span data-ttu-id="3bbda-108">10519</span><span class="sxs-lookup"><span data-stu-id="3bbda-108">10519</span></span>|  
|<span data-ttu-id="3bbda-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3bbda-109">Event Source</span></span>|<span data-ttu-id="3bbda-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3bbda-110">ENTSSO</span></span>|  
|<span data-ttu-id="3bbda-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3bbda-111">Component</span></span>|<span data-ttu-id="3bbda-112">N\A</span><span class="sxs-lookup"><span data-stu-id="3bbda-112">N\A</span></span>|  
|<span data-ttu-id="3bbda-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3bbda-113">Symbolic Name</span></span>|<span data-ttu-id="3bbda-114">SSO_WARN_BAD_APP_ADMIN_GROUP</span><span class="sxs-lookup"><span data-stu-id="3bbda-114">SSO_WARN_BAD_APP_ADMIN_GROUP</span></span>|  
|<span data-ttu-id="3bbda-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3bbda-115">Message Text</span></span>|<span data-ttu-id="3bbda-116">Le compte Administrateurs d'applications associé à cette application n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="3bbda-116">The Application Administrators account for this application is not valid.</span></span> <span data-ttu-id="3bbda-117">S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="3bbda-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="3bbda-118">S'il s'agit d'un compte de domaine, contactez votre administrateur système.</span><span class="sxs-lookup"><span data-stu-id="3bbda-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="3bbda-119">Activez l'application une fois le compte valide.</span><span class="sxs-lookup"><span data-stu-id="3bbda-119">Enable the application when the account is valid.</span></span> <span data-ttu-id="3bbda-120">Vous pouvez ignorer ce message si vous n'envisagez pas d'utiliser cette application sur cet ordinateur.%r</span><span class="sxs-lookup"><span data-stu-id="3bbda-120">You can ignore this message if you are not going to use this application on this computer.%r</span></span><br /><br /> <span data-ttu-id="3bbda-121">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="3bbda-121">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="3bbda-122">Administrateurs d’application : %2 %r</span><span class="sxs-lookup"><span data-stu-id="3bbda-122">Application Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="3bbda-123">Comptes non valides : %3 %r</span><span class="sxs-lookup"><span data-stu-id="3bbda-123">Invalid accounts: %3%r</span></span><br /><br /> <span data-ttu-id="3bbda-124">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="3bbda-124">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bbda-125">Explication</span><span class="sxs-lookup"><span data-stu-id="3bbda-125">Explanation</span></span>  
 <span data-ttu-id="3bbda-126">Cet avertissement indique que le compte du groupe Administrateurs d'applications ne correspond pas à un compte Windows valide.</span><span class="sxs-lookup"><span data-stu-id="3bbda-126">This Warning event indicates that an Application Administrators group account is not a valid Windows account.</span></span> <span data-ttu-id="3bbda-127">Il existe un groupe de compte Administrateurs d'applications pour chaque application associée.</span><span class="sxs-lookup"><span data-stu-id="3bbda-127">There is one Application Administraotrs account group for each affiliate application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bbda-128">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3bbda-128">User Action</span></span>  
 <span data-ttu-id="3bbda-129">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bbda-129">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="3bbda-130">Assurez-vous que le compte Administrateurs d'applications spécifié existe.</span><span class="sxs-lookup"><span data-stu-id="3bbda-130">Verify the specified Application Administrators account exists.</span></span>  
  
-   <span data-ttu-id="3bbda-131">À l'aide de l'utilitaire d'administration SSO, vérifiez que l'application associée spécifiée est configurée de façon à utiliser le compte Administrateurs d'applications correct.</span><span class="sxs-lookup"><span data-stu-id="3bbda-131">Use the SSO Administration Utility to verify the specified affiliate application is configured to use the correct application administrators account.</span></span>  
  
 <span data-ttu-id="3bbda-132">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="3bbda-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="3bbda-133">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3bbda-133">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="3bbda-134">Applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="3bbda-134">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  
  
-   [<span data-ttu-id="3bbda-135">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="3bbda-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
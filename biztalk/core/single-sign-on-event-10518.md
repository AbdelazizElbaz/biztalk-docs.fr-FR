---
title: "Single Sign-On : Événement 10518 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 274e29f9-1933-4e40-83c0-2e84c6708315
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27b82d7f0a6bbaf02400679add53851867d728c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10518"></a><span data-ttu-id="9d467-102">Single Sign-On : Événement 10518</span><span class="sxs-lookup"><span data-stu-id="9d467-102">Single Sign-On: Event 10518</span></span>
## <a name="details"></a><span data-ttu-id="9d467-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9d467-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d467-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9d467-104">Product Name</span></span>|<span data-ttu-id="9d467-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9d467-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9d467-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9d467-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9d467-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9d467-107">Event ID</span></span>|<span data-ttu-id="9d467-108">10518</span><span class="sxs-lookup"><span data-stu-id="9d467-108">10518</span></span>|  
|<span data-ttu-id="9d467-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9d467-109">Event Source</span></span>|<span data-ttu-id="9d467-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9d467-110">ENTSSO</span></span>|  
|<span data-ttu-id="9d467-111">Composant</span><span class="sxs-lookup"><span data-stu-id="9d467-111">Component</span></span>|<span data-ttu-id="9d467-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9d467-112">N\A</span></span>|  
|<span data-ttu-id="9d467-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9d467-113">Symbolic Name</span></span>|<span data-ttu-id="9d467-114">SSO_WARN_BAD_USER_GROUP</span><span class="sxs-lookup"><span data-stu-id="9d467-114">SSO_WARN_BAD_USER_GROUP</span></span>|  
|<span data-ttu-id="9d467-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9d467-115">Message Text</span></span>|<span data-ttu-id="9d467-116">Le compte Utilisateurs d'applications pour cette application n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="9d467-116">The Application Users account for this application is not valid.</span></span> <span data-ttu-id="9d467-117">S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9d467-117">If it is a local account check that this account exists on the server.</span></span> <span data-ttu-id="9d467-118">S'il s'agit d'un compte de domaine, contactez votre administrateur système.</span><span class="sxs-lookup"><span data-stu-id="9d467-118">If it is a domain account contact your domain administrator.</span></span> <span data-ttu-id="9d467-119">Activez l'application une fois le compte valide.</span><span class="sxs-lookup"><span data-stu-id="9d467-119">Enable the application when the account is valid.</span></span> <span data-ttu-id="9d467-120">Vous pouvez ignorer ce message si vous n'envisagez pas d'utiliser cette application sur cet ordinateur.%r</span><span class="sxs-lookup"><span data-stu-id="9d467-120">You can ignore this message if you are not going to use this application on this computer.%r</span></span><br /><br /> <span data-ttu-id="9d467-121">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="9d467-121">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="9d467-122">Utilisateurs de l’application : %2 %r</span><span class="sxs-lookup"><span data-stu-id="9d467-122">Application Users: %2%r</span></span><br /><br /> <span data-ttu-id="9d467-123">Comptes non valides : %3 %r</span><span class="sxs-lookup"><span data-stu-id="9d467-123">Invalid accounts: %3%r</span></span><br /><br /> <span data-ttu-id="9d467-124">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="9d467-124">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d467-125">Explication</span><span class="sxs-lookup"><span data-stu-id="9d467-125">Explanation</span></span>  
 <span data-ttu-id="9d467-126">Cet événement d'avertissement indique qu'un compte de groupe Utilisateurs d'applications n'est pas un compte Windows valide.</span><span class="sxs-lookup"><span data-stu-id="9d467-126">This Warning event indicates that an Application Users group account is not a valid Windows account.</span></span> <span data-ttu-id="9d467-127">Il existe un compte du groupe Utilisateurs d'applications pour chaque application associée.</span><span class="sxs-lookup"><span data-stu-id="9d467-127">There is one Application Users account group for each affiliate application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d467-128">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9d467-128">User Action</span></span>  
 <span data-ttu-id="9d467-129">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d467-129">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="9d467-130">Vérifiez que le compte Utilisateurs d'applications spécifié existe.</span><span class="sxs-lookup"><span data-stu-id="9d467-130">Verify the specified Application Users account exists.</span></span>  
  
-   <span data-ttu-id="9d467-131">Utilisez l'utilitaire d'administration de l'authentification unique pour vérifier que l'application associée spécifiée est configurée pour utiliser le compte Utilisateurs d'applications correct.</span><span class="sxs-lookup"><span data-stu-id="9d467-131">Use the SSO Administration Utility to verify the specified affiliate application is configured to use the correct application users account.</span></span>  
  
 <span data-ttu-id="9d467-132">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="9d467-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9d467-133">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="9d467-133">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="9d467-134">Applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="9d467-134">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  
  
-   [<span data-ttu-id="9d467-135">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="9d467-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
---
title: "Single Sign-On : Événement 10731 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 605e77f0-61f2-4a97-9ea0-bdc56344e8d9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10960489638aa565a11ecc32c70fc3a8fc6d477b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10731"></a><span data-ttu-id="7adf5-102">Single Sign-On : Événement 10731</span><span class="sxs-lookup"><span data-stu-id="7adf5-102">Single Sign-On: Event 10731</span></span>
## <a name="details"></a><span data-ttu-id="7adf5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7adf5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7adf5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7adf5-104">Product Name</span></span>|<span data-ttu-id="7adf5-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7adf5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7adf5-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7adf5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7adf5-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7adf5-107">Event ID</span></span>|<span data-ttu-id="7adf5-108">10731</span><span class="sxs-lookup"><span data-stu-id="7adf5-108">10731</span></span>|  
|<span data-ttu-id="7adf5-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7adf5-109">Event Source</span></span>|<span data-ttu-id="7adf5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7adf5-110">ENTSSO</span></span>|  
|<span data-ttu-id="7adf5-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7adf5-111">Component</span></span>|<span data-ttu-id="7adf5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="7adf5-112">N\A</span></span>|  
|<span data-ttu-id="7adf5-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7adf5-113">Symbolic Name</span></span>|<span data-ttu-id="7adf5-114">SSO_WARN_INVALID_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="7adf5-114">SSO_WARN_INVALID_USER_NOT_IN_GROUP</span></span>|  
|<span data-ttu-id="7adf5-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7adf5-115">Message Text</span></span>|<span data-ttu-id="7adf5-116">Impossible de créer un mappage car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.%r</span><span class="sxs-lookup"><span data-stu-id="7adf5-116">A mapping could not be created because the specified user is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="7adf5-117">Nom de domaine : %1 %r</span><span class="sxs-lookup"><span data-stu-id="7adf5-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="7adf5-118">Nom d’utilisateur : %2 %r</span><span class="sxs-lookup"><span data-stu-id="7adf5-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="7adf5-119">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="7adf5-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="7adf5-120">Utilisateurs de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="7adf5-120">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="7adf5-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="7adf5-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7adf5-122">Explication</span><span class="sxs-lookup"><span data-stu-id="7adf5-122">Explanation</span></span>  
 <span data-ttu-id="7adf5-123">Cet événement d'avertissement indique qu'un mappage n'a pas pu être créé car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="7adf5-123">This Warning event indicates that a mapping could not be created because the specified user is not a member of the Application Users account.</span></span>  
  
 <span data-ttu-id="7adf5-124">Il y a un compte du groupe Utilisateurs d'applications pour chaque application associée.</span><span class="sxs-lookup"><span data-stu-id="7adf5-124">An application user's group account exists for each affiliate application.</span></span> <span data-ttu-id="7adf5-125">Les membres de ce compte peuvent vérifier leurs informations d'identification dans l'application associée et gérer leurs mappages d'informations d'identification dans l'application associée.</span><span class="sxs-lookup"><span data-stu-id="7adf5-125">Members of this account can verify their credentials in the affiliate application and can manage their credential mappings in the affiliate application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7adf5-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7adf5-126">User Action</span></span>  
 <span data-ttu-id="7adf5-127">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7adf5-127">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="7adf5-128">Ajoutez l'utilisateur spécifié au groupe Utilisateurs d'applications de l'application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7adf5-128">Add the specified user to the application user's group for the specified affiliate application.</span></span>  
  
 <span data-ttu-id="7adf5-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7adf5-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="7adf5-130">Groupes d’utilisateurs de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="7adf5-130">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="7adf5-131">Applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="7adf5-131">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)
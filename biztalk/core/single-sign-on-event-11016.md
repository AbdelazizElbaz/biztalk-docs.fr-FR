---
title: "Single Sign-On : Événement 11016 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3963b706-168d-438d-a068-637f8a6b7b0c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f84bfef5dcef8e28bb3616ce30f1addc77f240c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11016"></a><span data-ttu-id="29158-102">Single Sign-On : Événement 11016</span><span class="sxs-lookup"><span data-stu-id="29158-102">Single Sign-On: Event 11016</span></span>
## <a name="details"></a><span data-ttu-id="29158-103">Détails</span><span class="sxs-lookup"><span data-stu-id="29158-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29158-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="29158-104">Product Name</span></span>|<span data-ttu-id="29158-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="29158-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="29158-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="29158-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="29158-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="29158-107">Event ID</span></span>|<span data-ttu-id="29158-108">11016</span><span class="sxs-lookup"><span data-stu-id="29158-108">11016</span></span>|  
|<span data-ttu-id="29158-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="29158-109">Event Source</span></span>|<span data-ttu-id="29158-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="29158-110">ENTSSO</span></span>|  
|<span data-ttu-id="29158-111">Composant</span><span class="sxs-lookup"><span data-stu-id="29158-111">Component</span></span>|<span data-ttu-id="29158-112">Néant</span><span class="sxs-lookup"><span data-stu-id="29158-112">N/A</span></span>|  
|<span data-ttu-id="29158-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="29158-113">Symbolic Name</span></span>|<span data-ttu-id="29158-114">RPC EXTENDED ERROR INFORMATION%r</span><span class="sxs-lookup"><span data-stu-id="29158-114">RPC EXTENDED ERROR INFORMATION%r</span></span>|  
|<span data-ttu-id="29158-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="29158-115">Message Text</span></span>|<span data-ttu-id="29158-116">%1%r</span><span class="sxs-lookup"><span data-stu-id="29158-116">%1%r</span></span><br /><br /> <span data-ttu-id="29158-117">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="29158-117">Error Code: %2</span></span><br /><br /> <span data-ttu-id="29158-118">Échec de la fonction AuthzInitializeContextFromSid avec ERROR_ACCESS_DENIED.</span><span class="sxs-lookup"><span data-stu-id="29158-118">The AuthzInitializeContextFromSid function failed with ERROR_ACCESS_DENIED.</span></span> <span data-ttu-id="29158-119">Cela signifie que le compte de service sous lequel le serveur SSO est exécuté ne dispose pas d'autorisations suffisantes pour vérifier l'appartenance à un groupe dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="29158-119">This means that the service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory.</span></span> <span data-ttu-id="29158-120">Pour plus d'informations sur la résolution de ce problème, consultez votre documentation.%r</span><span class="sxs-lookup"><span data-stu-id="29158-120">Please check your documentation for details on how to fix this problem.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29158-121">Explication</span><span class="sxs-lookup"><span data-stu-id="29158-121">Explanation</span></span>  
 <span data-ttu-id="29158-122">Le compte de service sous lequel le serveur SSO est exécuté ne dispose pas d'autorisations suffisantes pour vérifier l'appartenance à un groupe dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="29158-122">The service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29158-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="29158-123">User Action</span></span>  
 <span data-ttu-id="29158-124">Consultez [serveur SSO](../core/sso-server.md) dans la documentation de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="29158-124">See [SSO Server](../core/sso-server.md) in the SSO documentation.</span></span>
---
title: "Single Sign-On : Événement 11059 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac5b6ce7-8819-4b9d-85f7-f5dfaf940487
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dfab1d020211565df452b6cfaf0bca14e724f0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11059"></a><span data-ttu-id="5831f-102">Single Sign-On : Événement 11059</span><span class="sxs-lookup"><span data-stu-id="5831f-102">Single Sign-On: Event 11059</span></span>
## <a name="details"></a><span data-ttu-id="5831f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5831f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5831f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5831f-104">Product Name</span></span>|<span data-ttu-id="5831f-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="5831f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5831f-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5831f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5831f-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5831f-107">Event ID</span></span>|<span data-ttu-id="5831f-108">11059</span><span class="sxs-lookup"><span data-stu-id="5831f-108">11059</span></span>|  
|<span data-ttu-id="5831f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5831f-109">Event Source</span></span>|<span data-ttu-id="5831f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5831f-110">ENTSSO</span></span>|  
|<span data-ttu-id="5831f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5831f-111">Component</span></span>|<span data-ttu-id="5831f-112">Néant</span><span class="sxs-lookup"><span data-stu-id="5831f-112">N/A</span></span>|  
|<span data-ttu-id="5831f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5831f-113">Symbolic Name</span></span>|<span data-ttu-id="5831f-114">SSO_INFO_INVALID_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="5831f-114">SSO_INFO_INVALID_USER_NOT_IN_GROUP</span></span>|  
|<span data-ttu-id="5831f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5831f-115">Message Text</span></span>|<span data-ttu-id="5831f-116">Impossible de créer un mappage car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.%r</span><span class="sxs-lookup"><span data-stu-id="5831f-116">A mapping could not be created because the specified user is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="5831f-117">Compte Windows : %1\\%2 %r</span><span class="sxs-lookup"><span data-stu-id="5831f-117">Windows Account: %1\\%2%r</span></span><br /><br /> <span data-ttu-id="5831f-118">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="5831f-118">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="5831f-119">Utilisateurs de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="5831f-119">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="5831f-120">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="5831f-120">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5831f-121">Explication</span><span class="sxs-lookup"><span data-stu-id="5831f-121">Explanation</span></span>  
 <span data-ttu-id="5831f-122">Le mappage n’a pas pu être créé car l’utilisateur spécifié n’est pas un membre du compte utilisateurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="5831f-122">The mapping could not be created because the specified user is not a member of the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5831f-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5831f-123">User Action</span></span>  
 <span data-ttu-id="5831f-124">Contactez votre administrateur de l'authentification unique de l'entreprise pour devenir membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="5831f-124">Contact your ENTSSO Administrator about becoming a member of the Application Users account.</span></span>
---
title: "Single Sign-On : Événement 10747 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63ae1ab4-0f4e-45a7-83c1-31b8037e4dd7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e26960bcba1ff3c640c88cd3fb6f5e4bd7dfceb6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10747"></a><span data-ttu-id="030e0-102">Single Sign-On : Événement 10747</span><span class="sxs-lookup"><span data-stu-id="030e0-102">Single Sign-On: Event 10747</span></span>
## <a name="details"></a><span data-ttu-id="030e0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="030e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="030e0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="030e0-104">Product Name</span></span>|<span data-ttu-id="030e0-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="030e0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="030e0-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="030e0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="030e0-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="030e0-107">Event ID</span></span>|<span data-ttu-id="030e0-108">10747</span><span class="sxs-lookup"><span data-stu-id="030e0-108">10747</span></span>|  
|<span data-ttu-id="030e0-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="030e0-109">Event Source</span></span>|<span data-ttu-id="030e0-110">N\A</span><span class="sxs-lookup"><span data-stu-id="030e0-110">N\A</span></span>|  
|<span data-ttu-id="030e0-111">Composant</span><span class="sxs-lookup"><span data-stu-id="030e0-111">Component</span></span>|<span data-ttu-id="030e0-112">N\A</span><span class="sxs-lookup"><span data-stu-id="030e0-112">N\A</span></span>|  
|<span data-ttu-id="030e0-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="030e0-113">Symbolic Name</span></span>|<span data-ttu-id="030e0-114">SSO_ERROR_UNKNOWN_NOTIFICATION</span><span class="sxs-lookup"><span data-stu-id="030e0-114">SSO_ERROR_UNKNOWN_NOTIFICATION</span></span>|  
|<span data-ttu-id="030e0-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="030e0-115">Message Text</span></span>|<span data-ttu-id="030e0-116">Un type de notification inconnu a été reçu.%r</span><span class="sxs-lookup"><span data-stu-id="030e0-116">An unknown notification type was received.%r</span></span><br /><br /> <span data-ttu-id="030e0-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="030e0-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="030e0-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="030e0-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="030e0-119">Type de notification : %3</span><span class="sxs-lookup"><span data-stu-id="030e0-119">Notification Type: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="030e0-120">Explication</span><span class="sxs-lookup"><span data-stu-id="030e0-120">Explanation</span></span>  
 <span data-ttu-id="030e0-121">Cet événement d'erreur indique qu'une erreur interne avec un type de notification non valide a été détectée par le service d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="030e0-121">This Error event indicates that an internal error with an invalid notification type was detected by the SSO service.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="030e0-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="030e0-122">User Action</span></span>  
 <span data-ttu-id="030e0-123">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="030e0-123">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="030e0-124">Recherchez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="030e0-124">Check the system and application event logs for associated events.</span></span>  
  
 <span data-ttu-id="030e0-125">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="030e0-125">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="030e0-126">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="030e0-126">Using SSO</span></span>](../core/using-sso.md)
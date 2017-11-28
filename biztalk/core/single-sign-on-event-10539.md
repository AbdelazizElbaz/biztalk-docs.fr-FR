---
title: "Single Sign-On : Événement 10539 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a67f5719-da7c-4ae0-a6fe-ff7b653a184d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ca34f40359b518e1a52b3326dae9917ca4910e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10539"></a><span data-ttu-id="d7095-102">Single Sign-On : Événement 10539</span><span class="sxs-lookup"><span data-stu-id="d7095-102">Single Sign-On: Event 10539</span></span>
## <a name="details"></a><span data-ttu-id="d7095-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d7095-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7095-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d7095-104">Product Name</span></span>|<span data-ttu-id="d7095-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d7095-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d7095-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d7095-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d7095-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d7095-107">Event ID</span></span>|<span data-ttu-id="d7095-108">10539</span><span class="sxs-lookup"><span data-stu-id="d7095-108">10539</span></span>|  
|<span data-ttu-id="d7095-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d7095-109">Event Source</span></span>|<span data-ttu-id="d7095-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d7095-110">ENTSSO</span></span>|  
|<span data-ttu-id="d7095-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d7095-111">Component</span></span>|<span data-ttu-id="d7095-112">CO</span><span class="sxs-lookup"><span data-stu-id="d7095-112">CO</span></span>|  
|<span data-ttu-id="d7095-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d7095-113">Symbolic Name</span></span>|<span data-ttu-id="d7095-114">SSO_WARN_SSO_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="d7095-114">SSO_WARN_SSO_TICKETS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="d7095-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d7095-115">Message Text</span></span>|<span data-ttu-id="d7095-116">Les tickets ne sont pas activés pour le système SSO.</span><span class="sxs-lookup"><span data-stu-id="d7095-116">Tickets are not enabled for the SSO system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7095-117">Explication</span><span class="sxs-lookup"><span data-stu-id="d7095-117">Explanation</span></span>  
 <span data-ttu-id="d7095-118">Cet événement d'avertissement indique que l'utilisation des tickets SSO n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="d7095-118">This Warning event indicates that the use of SSO tickets is not enabled.</span></span> <span data-ttu-id="d7095-119">L'activation de l'utilisation des tickets SSO est une fonctionnalité facultative du système SSO.</span><span class="sxs-lookup"><span data-stu-id="d7095-119">Allowing the use of SSO tickets is an optional feature of the SSO system.</span></span> <span data-ttu-id="d7095-120">Cette fonctionnalité n'a pas été activée sur votre système SSO.</span><span class="sxs-lookup"><span data-stu-id="d7095-120">This feature has not been enabled on your SSO system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7095-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d7095-121">User Action</span></span>  
 <span data-ttu-id="d7095-122">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d7095-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="d7095-123">Contactez votre administrateur de l'authentification unique pour activer les tickets pour le système SSO.</span><span class="sxs-lookup"><span data-stu-id="d7095-123">Contact your SSO Administrator to enable tickets for the SSO system.</span></span> <span data-ttu-id="d7095-124">Pour ce faire, utilisez les outils d'administration de l'authentification unique (interface graphique ou ligne de commande).</span><span class="sxs-lookup"><span data-stu-id="d7095-124">This can be done using the SSO administration tools (GUI or command line).</span></span>  
  
 <span data-ttu-id="d7095-125">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="d7095-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d7095-126">Comment configurer les Tickets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d7095-126">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)  
  
-   [<span data-ttu-id="d7095-127">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d7095-127">Using SSO</span></span>](../core/using-sso.md)
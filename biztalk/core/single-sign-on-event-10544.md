---
title: "Single Sign-On : Événement 10544 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1a01cda4272e2851f929c35fd2b767c321a9dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10544"></a><span data-ttu-id="8fcc1-102">Single Sign-On : Événement 10544</span><span class="sxs-lookup"><span data-stu-id="8fcc1-102">Single Sign-On: Event 10544</span></span>
## <a name="details"></a><span data-ttu-id="8fcc1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8fcc1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fcc1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8fcc1-104">Product Name</span></span>|<span data-ttu-id="8fcc1-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8fcc1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8fcc1-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8fcc1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8fcc1-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8fcc1-107">Event ID</span></span>|<span data-ttu-id="8fcc1-108">10544</span><span class="sxs-lookup"><span data-stu-id="8fcc1-108">10544</span></span>|  
|<span data-ttu-id="8fcc1-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8fcc1-109">Event Source</span></span>|<span data-ttu-id="8fcc1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8fcc1-110">ENTSSO</span></span>|  
|<span data-ttu-id="8fcc1-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8fcc1-111">Component</span></span>|<span data-ttu-id="8fcc1-112">CO</span><span class="sxs-lookup"><span data-stu-id="8fcc1-112">CO</span></span>|  
|<span data-ttu-id="8fcc1-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8fcc1-113">Symbolic Name</span></span>|<span data-ttu-id="8fcc1-114">SSO_WARN_TICKET_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="8fcc1-114">SSO_WARN_TICKET_EXPIRED</span></span>|  
|<span data-ttu-id="8fcc1-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8fcc1-115">Message Text</span></span>|<span data-ttu-id="8fcc1-116">Le ticket a expiré.%r</span><span class="sxs-lookup"><span data-stu-id="8fcc1-116">The ticket has expired.%r</span></span><br /><br /> <span data-ttu-id="8fcc1-117">Nom de l’application : %1</span><span class="sxs-lookup"><span data-stu-id="8fcc1-117">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8fcc1-118">Explication</span><span class="sxs-lookup"><span data-stu-id="8fcc1-118">Explanation</span></span>  
 <span data-ttu-id="8fcc1-119">Cet événement de type avertissement indique que le délai d'expiration du ticket a été dépassé.</span><span class="sxs-lookup"><span data-stu-id="8fcc1-119">This Warning event indicates that an application ticket timeout has expired.</span></span> <span data-ttu-id="8fcc1-120">Le délai d'expiration du ticket peut être spécifié au niveau du système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="8fcc1-120">Ticket timeout can be specified at both the system level and the application level.</span></span> <span data-ttu-id="8fcc1-121">S'il est spécifié à ces deux niveaux, celui relatif à l'application est utilisé pour déterminer la durée d'expiration.</span><span class="sxs-lookup"><span data-stu-id="8fcc1-121">If both system level and the application level timeout are specified, the application level timeout is used to determine the expiry time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8fcc1-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8fcc1-122">User Action</span></span>  
 <span data-ttu-id="8fcc1-123">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8fcc1-123">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="8fcc1-124">Déterminer la raison pour laquelle le ticket a expiré avant d'être validé.</span><span class="sxs-lookup"><span data-stu-id="8fcc1-124">Determine why the ticket expired before being validated.</span></span>  
  
-   <span data-ttu-id="8fcc1-125">Vérifier que la valeur du délai d'expiration du ticket est suffisamment importante pour couvrir la période allant de l'émission à l'échange du ticket.</span><span class="sxs-lookup"><span data-stu-id="8fcc1-125">Ensure that the Ticket timeout value is long enough to last between the time when the ticket is issued to the time that it is redeemed.</span></span>  
  
 <span data-ttu-id="8fcc1-126">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8fcc1-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8fcc1-127">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="8fcc1-127">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="8fcc1-128">Comment configurer les Tickets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8fcc1-128">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)
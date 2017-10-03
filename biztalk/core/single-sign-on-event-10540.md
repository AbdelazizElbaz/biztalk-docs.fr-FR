---
title: "Single Sign-On : Événement 10540 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce91ff30-3d68-4c5f-a955-5c426e94d917
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec48afebfa36411594c28908a233409311e32df9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10540"></a><span data-ttu-id="1c8da-102">Single Sign-On : Événement 10540</span><span class="sxs-lookup"><span data-stu-id="1c8da-102">Single Sign-On: Event 10540</span></span>
## <a name="details"></a><span data-ttu-id="1c8da-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1c8da-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c8da-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1c8da-104">Product Name</span></span>|<span data-ttu-id="1c8da-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1c8da-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1c8da-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1c8da-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1c8da-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1c8da-107">Event ID</span></span>|<span data-ttu-id="1c8da-108">10540</span><span class="sxs-lookup"><span data-stu-id="1c8da-108">10540</span></span>|  
|<span data-ttu-id="1c8da-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1c8da-109">Event Source</span></span>|<span data-ttu-id="1c8da-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1c8da-110">ENTSSO</span></span>|  
|<span data-ttu-id="1c8da-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1c8da-111">Component</span></span>|<span data-ttu-id="1c8da-112">CO</span><span class="sxs-lookup"><span data-stu-id="1c8da-112">CO</span></span>|  
|<span data-ttu-id="1c8da-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1c8da-113">Symbolic Name</span></span>|<span data-ttu-id="1c8da-114">SSO_WARN_APP_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="1c8da-114">SSO_WARN_APP_TICKETS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="1c8da-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1c8da-115">Message Text</span></span>|<span data-ttu-id="1c8da-116">Les tickets ne sont pas activés pour cette application.%r</span><span class="sxs-lookup"><span data-stu-id="1c8da-116">Tickets are not enabled for this application.%r</span></span><br /><br /> <span data-ttu-id="1c8da-117">Nom de l’application : %1</span><span class="sxs-lookup"><span data-stu-id="1c8da-117">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1c8da-118">Explication</span><span class="sxs-lookup"><span data-stu-id="1c8da-118">Explanation</span></span>  
 <span data-ttu-id="1c8da-119">Cette information indique que la fonction de création de tickets n'a pas été activée pour cette application.</span><span class="sxs-lookup"><span data-stu-id="1c8da-119">This Warning event indicates that the tickets feature has not been enabled for this application.</span></span> <span data-ttu-id="1c8da-120">L'utilisation des tickets SSO est une fonctionnalité facultative pour chaque application SSO.</span><span class="sxs-lookup"><span data-stu-id="1c8da-120">The use of SSO tickets is an optional feature for each SSO application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1c8da-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1c8da-121">User Action</span></span>  
 <span data-ttu-id="1c8da-122">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1c8da-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="1c8da-123">Contactez votre administrateur d'applications pour activer les tickets pour cette application SSO.</span><span class="sxs-lookup"><span data-stu-id="1c8da-123">Contact your Application Administrator to enable tickets for this SSO application.</span></span> <span data-ttu-id="1c8da-124">Pour ce faire, utilisez les outils d'administration de l'authentification unique (interface graphique ou ligne de commande).</span><span class="sxs-lookup"><span data-stu-id="1c8da-124">This can be done using the SSO administration tools (GUI or command line).</span></span>  
  
 <span data-ttu-id="1c8da-125">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="1c8da-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="1c8da-126">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="1c8da-126">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="1c8da-127">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="1c8da-127">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [<span data-ttu-id="1c8da-128">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="1c8da-128">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
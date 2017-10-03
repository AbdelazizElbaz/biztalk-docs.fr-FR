---
title: "Single Sign-On : Événement 10545 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64cb10ceef5827f9c0b0aab5d9810db061af8a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10545"></a><span data-ttu-id="d0e52-102">Single Sign-On : Événement 10545</span><span class="sxs-lookup"><span data-stu-id="d0e52-102">Single Sign-On: Event 10545</span></span>
## <a name="details"></a><span data-ttu-id="d0e52-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d0e52-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0e52-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d0e52-104">Product Name</span></span>|<span data-ttu-id="d0e52-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d0e52-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d0e52-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d0e52-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d0e52-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d0e52-107">Event ID</span></span>|<span data-ttu-id="d0e52-108">10545</span><span class="sxs-lookup"><span data-stu-id="d0e52-108">10545</span></span>|  
|<span data-ttu-id="d0e52-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d0e52-109">Event Source</span></span>|<span data-ttu-id="d0e52-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d0e52-110">ENTSSO</span></span>|  
|<span data-ttu-id="d0e52-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d0e52-111">Component</span></span>|<span data-ttu-id="d0e52-112">CO</span><span class="sxs-lookup"><span data-stu-id="d0e52-112">CO</span></span>|  
|<span data-ttu-id="d0e52-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d0e52-113">Symbolic Name</span></span>|<span data-ttu-id="d0e52-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="d0e52-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="d0e52-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d0e52-115">Message Text</span></span>|<span data-ttu-id="d0e52-116">Les tickets ne sont pas activés pour le système SSO.</span><span class="sxs-lookup"><span data-stu-id="d0e52-116">Tickets are not enabled for the SSO system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d0e52-117">Explication</span><span class="sxs-lookup"><span data-stu-id="d0e52-117">Explanation</span></span>  
 <span data-ttu-id="d0e52-118">Cet événement d'avertissement indique que les tickets ne sont pas activés pour le système SSO.</span><span class="sxs-lookup"><span data-stu-id="d0e52-118">This Warning event indicates that tickets are not enabled for the SSO System.</span></span> <span data-ttu-id="d0e52-119">Si la création de tickets est désactivée au niveau du système, la création de tickets ne peut pas être utilisée au niveau de l’Application associée soit.</span><span class="sxs-lookup"><span data-stu-id="d0e52-119">If ticketing is disabled at the system level, ticketing cannot be used at the Affiliate Application level either.</span></span> <span data-ttu-id="d0e52-120">Il est possible d’activer les tickets au niveau du système et de désactiver au niveau de l’Application associée.</span><span class="sxs-lookup"><span data-stu-id="d0e52-120">It is possible to enable tickets at the system level and disable it at the Affiliate Application level.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0e52-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d0e52-121">User Action</span></span>  
 <span data-ttu-id="d0e52-122">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d0e52-122">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="d0e52-123">Activez les tickets au niveau du système SSO.</span><span class="sxs-lookup"><span data-stu-id="d0e52-123">Enable tickets at the SSO System level.</span></span>  
  
 <span data-ttu-id="d0e52-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="d0e52-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d0e52-125">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="d0e52-125">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="d0e52-126">Comment configurer les Tickets d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="d0e52-126">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)
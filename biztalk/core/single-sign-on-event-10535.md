---
title: "Single Sign-On : Événement 10535 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b570b0b-5c45-4be3-80c9-a2c50601b677
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f96032c8176a251090453e493487a97d9cf0fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10535"></a><span data-ttu-id="8c73d-102">Single Sign-On : Événement 10535</span><span class="sxs-lookup"><span data-stu-id="8c73d-102">Single Sign-On: Event 10535</span></span>
## <a name="details"></a><span data-ttu-id="8c73d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8c73d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c73d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8c73d-104">Product Name</span></span>|<span data-ttu-id="8c73d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8c73d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8c73d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8c73d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8c73d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8c73d-107">Event ID</span></span>|<span data-ttu-id="8c73d-108">10535</span><span class="sxs-lookup"><span data-stu-id="8c73d-108">10535</span></span>|  
|<span data-ttu-id="8c73d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8c73d-109">Event Source</span></span>|<span data-ttu-id="8c73d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8c73d-110">ENTSSO</span></span>|  
|<span data-ttu-id="8c73d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8c73d-111">Component</span></span>|<span data-ttu-id="8c73d-112">CO</span><span class="sxs-lookup"><span data-stu-id="8c73d-112">CO</span></span>|  
|<span data-ttu-id="8c73d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8c73d-113">Symbolic Name</span></span>|<span data-ttu-id="8c73d-114">SSO_INFO_API_AUDIT</span><span class="sxs-lookup"><span data-stu-id="8c73d-114">SSO_INFO_API_AUDIT</span></span>|  
|<span data-ttu-id="8c73d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8c73d-115">Message Text</span></span>|<span data-ttu-id="8c73d-116">AUDIT D'AUTHENTIFICATION UNIQUE%r</span><span class="sxs-lookup"><span data-stu-id="8c73d-116">SSO AUDIT%r</span></span><br /><br /> <span data-ttu-id="8c73d-117">Fonction : %1 %r</span><span class="sxs-lookup"><span data-stu-id="8c73d-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="8c73d-118">ID de suivi : %2 %r</span><span class="sxs-lookup"><span data-stu-id="8c73d-118">Tracking ID: %2%r</span></span><br /><br /> <span data-ttu-id="8c73d-119">Ordinateur client : %3 %r</span><span class="sxs-lookup"><span data-stu-id="8c73d-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="8c73d-120">L’utilisateur client : %4 %r</span><span class="sxs-lookup"><span data-stu-id="8c73d-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="8c73d-121">Nom de l’application : %5</span><span class="sxs-lookup"><span data-stu-id="8c73d-121">Application Name: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8c73d-122">Explication</span><span class="sxs-lookup"><span data-stu-id="8c73d-122">Explanation</span></span>  
 <span data-ttu-id="8c73d-123">Cet événement d'audit d'informations indique qu'un événement conforme au niveau d'audit défini par l'utilisateur est survenu.</span><span class="sxs-lookup"><span data-stu-id="8c73d-123">This Information Audit event indicates that an event that meets the user defined audit level has occurred.</span></span> <span data-ttu-id="8c73d-124">Ce message d'événement inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8c73d-124">This event message includes:</span></span>  
  
 <span data-ttu-id="8c73d-125">**Fonction :** en cours d’exécution (fonction)</span><span class="sxs-lookup"><span data-stu-id="8c73d-125">**Function:** Function being performed</span></span>  
  
 <span data-ttu-id="8c73d-126">**ID de suivi :** GUID Unique généré lors de l’API SSO est d’abord appelée.</span><span class="sxs-lookup"><span data-stu-id="8c73d-126">**Tracking ID:** Unique GUID generated when an SSO API is first called.</span></span>  
  
 <span data-ttu-id="8c73d-127">**Ordinateur client :** ordinateur Client d'où provient la fonction.</span><span class="sxs-lookup"><span data-stu-id="8c73d-127">**Client Computer:** Client computer where the function originated.</span></span>  
  
 <span data-ttu-id="8c73d-128">**L’utilisateur client :** le nom du compte d’utilisateur qui a appelé la fonction.</span><span class="sxs-lookup"><span data-stu-id="8c73d-128">**Client User:** The name of the user account that invoked the function.</span></span>  
  
 <span data-ttu-id="8c73d-129">**Nom de l’application :** nom de l’authentification unique applications associées à l’application associée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="8c73d-129">**Application Name:** Name of the SSO affiliate application associated with this function.</span></span>  
  
 <span data-ttu-id="8c73d-130">Ce type d'événement permet de diagnostiquer des problèmes lors du développement, du dépannage ou de l'exécution d'une application.</span><span class="sxs-lookup"><span data-stu-id="8c73d-130">This type of event is used for diagnosing problems during development, troubleshooting, or running of an application.</span></span> <span data-ttu-id="8c73d-131">Les informations fournies permettent de déterminer l'appel de l'API SSO effectué.</span><span class="sxs-lookup"><span data-stu-id="8c73d-131">Information provided can be used to determine the SSO API call being made.</span></span>  
  
 <span data-ttu-id="8c73d-132">Le niveau d'audit peut être défini sur 0/1/2/3. 0 signifie « Aucun », 1 signifie « Bas » et affiche des erreurs uniquement, 2 signifie « Moyen » et affiche des erreurs et des avertissements, tandis que 3 signifie « Élevé » et affiche tous les messages d'audit.</span><span class="sxs-lookup"><span data-stu-id="8c73d-132">The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c73d-133">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8c73d-133">User Action</span></span>  
  
-   <span data-ttu-id="8c73d-134">Consultez le journal des événements pour connaître les messages d'événements associés.</span><span class="sxs-lookup"><span data-stu-id="8c73d-134">Check the event log for associated event messages.</span></span>  
  
 <span data-ttu-id="8c73d-135">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8c73d-135">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8c73d-136">Comment auditer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c73d-136">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="8c73d-137">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="8c73d-137">Using SSO</span></span>](../core/using-sso.md)
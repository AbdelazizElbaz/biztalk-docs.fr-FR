---
title: "Single Sign-On : Événement 10536 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d493a45b-c4ed-40fc-8803-b3ca12f9795b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 273533009d68c36d15f08b7ed106a3e1f7a1b380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10536"></a><span data-ttu-id="751af-102">Single Sign-On : Événement 10536</span><span class="sxs-lookup"><span data-stu-id="751af-102">Single Sign-On: Event 10536</span></span>
## <a name="details"></a><span data-ttu-id="751af-103">Détails</span><span class="sxs-lookup"><span data-stu-id="751af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="751af-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="751af-104">Product Name</span></span>|<span data-ttu-id="751af-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="751af-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="751af-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="751af-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="751af-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="751af-107">Event ID</span></span>|<span data-ttu-id="751af-108">10536</span><span class="sxs-lookup"><span data-stu-id="751af-108">10536</span></span>|  
|<span data-ttu-id="751af-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="751af-109">Event Source</span></span>|<span data-ttu-id="751af-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="751af-110">ENTSSO</span></span>|  
|<span data-ttu-id="751af-111">Composant</span><span class="sxs-lookup"><span data-stu-id="751af-111">Component</span></span>|<span data-ttu-id="751af-112">CO</span><span class="sxs-lookup"><span data-stu-id="751af-112">CO</span></span>|  
|<span data-ttu-id="751af-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="751af-113">Symbolic Name</span></span>|<span data-ttu-id="751af-114">SSO_WARN_API_AUDIT</span><span class="sxs-lookup"><span data-stu-id="751af-114">SSO_WARN_API_AUDIT</span></span>|  
|<span data-ttu-id="751af-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="751af-115">Message Text</span></span>|<span data-ttu-id="751af-116">AUDIT D'AUTHENTIFICATION UNIQUE%r</span><span class="sxs-lookup"><span data-stu-id="751af-116">SSO AUDIT%r</span></span><br /><br /> <span data-ttu-id="751af-117">Fonction : %1 %r</span><span class="sxs-lookup"><span data-stu-id="751af-117">Function: %1%r</span></span><br /><br /> <span data-ttu-id="751af-118">ID de suivi : %2 %r</span><span class="sxs-lookup"><span data-stu-id="751af-118">Tracking ID: %2%r</span></span><br /><br /> <span data-ttu-id="751af-119">Ordinateur client : %3 %r</span><span class="sxs-lookup"><span data-stu-id="751af-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="751af-120">L’utilisateur client : %4 %r</span><span class="sxs-lookup"><span data-stu-id="751af-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="751af-121">Nom de l’application : %5 %r</span><span class="sxs-lookup"><span data-stu-id="751af-121">Application Name: %5%r</span></span><br /><br /> <span data-ttu-id="751af-122">Code d’erreur : %6</span><span class="sxs-lookup"><span data-stu-id="751af-122">Error Code: %6</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="751af-123">Explication</span><span class="sxs-lookup"><span data-stu-id="751af-123">Explanation</span></span>  
 <span data-ttu-id="751af-124">Cet événement d'avertissement d'audit indique qu'un événement correspondant au niveau d'audit défini par l'utilisateur s'est produit.</span><span class="sxs-lookup"><span data-stu-id="751af-124">This Warning Audit event indicates that an event that meets the user defined audit level has occurred.</span></span> <span data-ttu-id="751af-125">Ce message d'événement inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="751af-125">This event message includes:</span></span>  
  
 <span data-ttu-id="751af-126">**Fonction :** en cours d’exécution (fonction)</span><span class="sxs-lookup"><span data-stu-id="751af-126">**Function:** Function being performed</span></span>  
  
 <span data-ttu-id="751af-127">**ID de suivi :** GUID Unique généré lors de l’API SSO est d’abord appelée.</span><span class="sxs-lookup"><span data-stu-id="751af-127">**Tracking ID:** Unique GUID generated when an SSO API is first called.</span></span>  
  
 <span data-ttu-id="751af-128">**Ordinateur client :** ordinateur Client d'où provient la fonction.</span><span class="sxs-lookup"><span data-stu-id="751af-128">**Client Computer:** Client computer where the function originated.</span></span>  
  
 <span data-ttu-id="751af-129">**L’utilisateur client :** le nom du compte d’utilisateur qui a appelé la fonction.</span><span class="sxs-lookup"><span data-stu-id="751af-129">**Client User:** The name of the user account that invoked the function.</span></span>  
  
 <span data-ttu-id="751af-130">**Nom de l’application :** nom de l’authentification unique applications associées à l’application associée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="751af-130">**Application Name:** Name of the SSO affiliate application associated with this function.</span></span>  
  
 <span data-ttu-id="751af-131">**Code d’erreur :** identifiant d’erreur Unique.</span><span class="sxs-lookup"><span data-stu-id="751af-131">**Error Code:** Unique error identifier.</span></span>  
  
 <span data-ttu-id="751af-132">Ce type d'événement permet de diagnostiquer des problèmes lors du développement, du dépannage ou de l'exécution d'une application.</span><span class="sxs-lookup"><span data-stu-id="751af-132">This type of event is used for diagnosing problems during development, troubleshooting, or running of an application.</span></span> <span data-ttu-id="751af-133">Les informations fournies permettent de déterminer l'appel de l'API SSO effectué.</span><span class="sxs-lookup"><span data-stu-id="751af-133">Information provided can be used to determine the SSO API call being made.</span></span>  
  
 <span data-ttu-id="751af-134">Le niveau d'audit peut être défini sur 0/1/2/3. 0 signifie « Aucun », 1 signifie « Bas » et affiche des erreurs uniquement, 2 signifie « Moyen » et affiche des erreurs et des avertissements, tandis que 3 signifie « Élevé » et affiche tous les messages d'audit.</span><span class="sxs-lookup"><span data-stu-id="751af-134">The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="751af-135">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="751af-135">User Action</span></span>  
  
-   <span data-ttu-id="751af-136">Consultez le journal des événements pour connaître les messages d'événements associés.</span><span class="sxs-lookup"><span data-stu-id="751af-136">Check the event log for associated event messages.</span></span>  
  
 <span data-ttu-id="751af-137">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="751af-137">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="751af-138">Comment auditer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="751af-138">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="751af-139">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="751af-139">Using SSO</span></span>](../core/using-sso.md)
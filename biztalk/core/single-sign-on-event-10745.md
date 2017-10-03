---
title: "Single Sign-On : Événement 10745 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed630e40-d876-4e90-937e-4d2d54fe9f1a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fe734562b9d8b3564a08f3f5196d53996bf40ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10745"></a><span data-ttu-id="fac8b-102">Single Sign-On : Événement 10745</span><span class="sxs-lookup"><span data-stu-id="fac8b-102">Single Sign-On: Event 10745</span></span>
## <a name="details"></a><span data-ttu-id="fac8b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fac8b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fac8b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fac8b-104">Product Name</span></span>|<span data-ttu-id="fac8b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="fac8b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fac8b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fac8b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fac8b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fac8b-107">Event ID</span></span>|<span data-ttu-id="fac8b-108">10745</span><span class="sxs-lookup"><span data-stu-id="fac8b-108">10745</span></span>|  
|<span data-ttu-id="fac8b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fac8b-109">Event Source</span></span>|<span data-ttu-id="fac8b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fac8b-110">ENTSSO</span></span>|  
|<span data-ttu-id="fac8b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="fac8b-111">Component</span></span>|<span data-ttu-id="fac8b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fac8b-112">N\A</span></span>|  
|<span data-ttu-id="fac8b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fac8b-113">Symbolic Name</span></span>|<span data-ttu-id="fac8b-114">SSO_ERROR_ADAPTER_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="fac8b-114">SSO_ERROR_ADAPTER_OFFLINE</span></span>|  
|<span data-ttu-id="fac8b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fac8b-115">Message Text</span></span>|<span data-ttu-id="fac8b-116">L'adaptateur est hors ligne.%r</span><span class="sxs-lookup"><span data-stu-id="fac8b-116">The adapter is offline.%r</span></span><br /><br /> <span data-ttu-id="fac8b-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="fac8b-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="fac8b-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="fac8b-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="fac8b-119">Message d’erreur : %3 %r</span><span class="sxs-lookup"><span data-stu-id="fac8b-119">Error Message: %3%r</span></span><br /><br /> <span data-ttu-id="fac8b-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="fac8b-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fac8b-121">Explication</span><span class="sxs-lookup"><span data-stu-id="fac8b-121">Explanation</span></span>  
 <span data-ttu-id="fac8b-122">Cette erreur indique que l'adaptateur spécifié est hors ligne.</span><span class="sxs-lookup"><span data-stu-id="fac8b-122">This Error event indicates that the specified adapter is offline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fac8b-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fac8b-123">User Action</span></span>  
 <span data-ttu-id="fac8b-124">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="fac8b-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="fac8b-125">Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées.</span><span class="sxs-lookup"><span data-stu-id="fac8b-125">Check the system and application event logs for associated errors.</span></span>  
  
-   <span data-ttu-id="fac8b-126">Recherchez des erreurs dans l'adaptateur externe.</span><span class="sxs-lookup"><span data-stu-id="fac8b-126">Check the external adapter for errors.</span></span>  
  
 <span data-ttu-id="fac8b-127">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fac8b-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="fac8b-128">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="fac8b-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
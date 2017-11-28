---
title: "Single Sign-On : Événement 10586 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7d480e9-dc34-44ac-9272-0caf80237bd9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 124ed0a722d0da0f21722f3b337c8bb938068b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10586"></a><span data-ttu-id="125bc-102">Single Sign-On : Événement 10586</span><span class="sxs-lookup"><span data-stu-id="125bc-102">Single Sign-On: Event 10586</span></span>
## <a name="details"></a><span data-ttu-id="125bc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="125bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="125bc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="125bc-104">Product Name</span></span>|<span data-ttu-id="125bc-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="125bc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="125bc-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="125bc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="125bc-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="125bc-107">Event ID</span></span>|<span data-ttu-id="125bc-108">10586</span><span class="sxs-lookup"><span data-stu-id="125bc-108">10586</span></span>|  
|<span data-ttu-id="125bc-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="125bc-109">Event Source</span></span>|<span data-ttu-id="125bc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="125bc-110">ENTSSO</span></span>|  
|<span data-ttu-id="125bc-111">Composant</span><span class="sxs-lookup"><span data-stu-id="125bc-111">Component</span></span>|<span data-ttu-id="125bc-112">Néant</span><span class="sxs-lookup"><span data-stu-id="125bc-112">N/A</span></span>|  
|<span data-ttu-id="125bc-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="125bc-113">Symbolic Name</span></span>|<span data-ttu-id="125bc-114">SSO_WARN_CRED_CACHE_OFF</span><span class="sxs-lookup"><span data-stu-id="125bc-114">SSO_WARN_CRED_CACHE_OFF</span></span>|  
|<span data-ttu-id="125bc-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="125bc-115">Message Text</span></span>|<span data-ttu-id="125bc-116">Le cache des informations d'identification a été désactivé pour ce serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="125bc-116">The credential cache has been disabled for this SSO server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="125bc-117">Explication</span><span class="sxs-lookup"><span data-stu-id="125bc-117">Explanation</span></span>  
 <span data-ttu-id="125bc-118">Le cache des informations d'identification, qui est généralement activé, a été désactivé.</span><span class="sxs-lookup"><span data-stu-id="125bc-118">The credential cache, which is generally enabled, has been disabled.</span></span> <span data-ttu-id="125bc-119">Seul un administrateur système peut activer ou désactiver le cache des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="125bc-119">Only a system administrator can enable or disable the credential cache.</span></span> <span data-ttu-id="125bc-120">La désactivation du cache des informations d'identification va parfois aboutir à l'émission d'informations d'identification plus récentes par le système ENTSSO, bien que les performances puissent s'en trouver ralenties.</span><span class="sxs-lookup"><span data-stu-id="125bc-120">Disabling the credential cache will sometimes result in more current credentials from the ENTSSO system, although it could slow down peformance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="125bc-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="125bc-121">User Action</span></span>  
 <span data-ttu-id="125bc-122">Pour réactiver le cache d’informations d’identification, consultez le tableau des propriétés des applications dans [Applications associées SSO](../core/sso-affiliate-applications.md).</span><span class="sxs-lookup"><span data-stu-id="125bc-122">To re-enable the credential cache, see the Afflilate Application Properties table in [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>
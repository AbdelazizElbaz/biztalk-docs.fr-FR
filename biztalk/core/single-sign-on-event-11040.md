---
title: "Single Sign-On : Événement 11040 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6ccdc06-9677-4454-ae2c-8dde78d6f3f8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9eafbbe1c0cbcb0db96c94d072ed511e69b2d6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11040"></a><span data-ttu-id="09b90-102">Single Sign-On : Événement 11040</span><span class="sxs-lookup"><span data-stu-id="09b90-102">Single Sign-On: Event 11040</span></span>
## <a name="details"></a><span data-ttu-id="09b90-103">Détails</span><span class="sxs-lookup"><span data-stu-id="09b90-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09b90-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="09b90-104">Product Name</span></span>|<span data-ttu-id="09b90-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="09b90-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="09b90-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="09b90-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="09b90-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="09b90-107">Event ID</span></span>|<span data-ttu-id="09b90-108">11040</span><span class="sxs-lookup"><span data-stu-id="09b90-108">11040</span></span>|  
|<span data-ttu-id="09b90-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="09b90-109">Event Source</span></span>|<span data-ttu-id="09b90-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="09b90-110">ENTSSO</span></span>|  
|<span data-ttu-id="09b90-111">Composant</span><span class="sxs-lookup"><span data-stu-id="09b90-111">Component</span></span>|<span data-ttu-id="09b90-112">Néant</span><span class="sxs-lookup"><span data-stu-id="09b90-112">N/A</span></span>|  
|<span data-ttu-id="09b90-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="09b90-113">Symbolic Name</span></span>|<span data-ttu-id="09b90-114">SSO_WARN_NETWORK_SERVICE</span><span class="sxs-lookup"><span data-stu-id="09b90-114">SSO_WARN_NETWORK_SERVICE</span></span>|  
|<span data-ttu-id="09b90-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="09b90-115">Message Text</span></span>|<span data-ttu-id="09b90-116">Le service SSO fonctionne avec un compte de service réseau.</span><span class="sxs-lookup"><span data-stu-id="09b90-116">The SSO service is running under the Network Service account.</span></span> <span data-ttu-id="09b90-117">Vous devez tenir compte de plusieurs éléments importants relatifs à ce compte.</span><span class="sxs-lookup"><span data-stu-id="09b90-117">There are some special considerations for this account.</span></span> <span data-ttu-id="09b90-118">Pour plus d'informations, reportez-vous à votre documentation.%r</span><span class="sxs-lookup"><span data-stu-id="09b90-118">See your documentation for details.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="09b90-119">Explication</span><span class="sxs-lookup"><span data-stu-id="09b90-119">Explanation</span></span>  
 <span data-ttu-id="09b90-120">Le service SSO fonctionne avec un compte de service réseau.</span><span class="sxs-lookup"><span data-stu-id="09b90-120">The SSO service is running under the Network Service account.</span></span> <span data-ttu-id="09b90-121">Vous devez tenir compte de plusieurs éléments importants relatifs à ce compte.</span><span class="sxs-lookup"><span data-stu-id="09b90-121">There are some special considerations for this account.</span></span> <span data-ttu-id="09b90-122">Par exemple, il est nécessaire d'effectuer un redémarrage après l'ajout d'un compte de service réseau.</span><span class="sxs-lookup"><span data-stu-id="09b90-122">For example, a reboot is required after adding a Network Service account.</span></span> <span data-ttu-id="09b90-123">De même, un fonctionnement sous un compte de service réseau vous permet d'exécuter uniquement un nombre très limité de scénarios.</span><span class="sxs-lookup"><span data-stu-id="09b90-123">Also, running under a Network Service account restricts you to running in very limited scenarios.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="09b90-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="09b90-124">User Action</span></span>  
 <span data-ttu-id="09b90-125">Pour plus d’informations, consultez [recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md).</span><span class="sxs-lookup"><span data-stu-id="09b90-125">For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).</span></span>
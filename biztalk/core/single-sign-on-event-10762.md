---
title: "Single Sign-On : Événement 10762 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 487fbeb0f077950605432861a9118eacd93f2c89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10762"></a><span data-ttu-id="87d6d-102">Single Sign-On : Événement 10762</span><span class="sxs-lookup"><span data-stu-id="87d6d-102">Single Sign-On: Event 10762</span></span>
## <a name="details"></a><span data-ttu-id="87d6d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="87d6d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87d6d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="87d6d-104">Product Name</span></span>|<span data-ttu-id="87d6d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="87d6d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="87d6d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="87d6d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="87d6d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="87d6d-107">Event ID</span></span>|<span data-ttu-id="87d6d-108">10762</span><span class="sxs-lookup"><span data-stu-id="87d6d-108">10762</span></span>|  
|<span data-ttu-id="87d6d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="87d6d-109">Event Source</span></span>|<span data-ttu-id="87d6d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="87d6d-110">ENTSSO</span></span>|  
|<span data-ttu-id="87d6d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="87d6d-111">Component</span></span>|<span data-ttu-id="87d6d-112">Néant</span><span class="sxs-lookup"><span data-stu-id="87d6d-112">N/A</span></span>|  
|<span data-ttu-id="87d6d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="87d6d-113">Symbolic Name</span></span>|<span data-ttu-id="87d6d-114">ENTSSO_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="87d6d-114">ENTSSO_E_WRONG_THREAD</span></span>|  
|<span data-ttu-id="87d6d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="87d6d-115">Message Text</span></span>|<span data-ttu-id="87d6d-116">Le composant de client SSO a été appelé sur un thread incorrect.</span><span class="sxs-lookup"><span data-stu-id="87d6d-116">The SSO client component has been called on the wrong thread.</span></span> <span data-ttu-id="87d6d-117">Il est actuellement verrouillé par un thread car il utilise une transaction.</span><span class="sxs-lookup"><span data-stu-id="87d6d-117">It is currently locked to a thread because it has a transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87d6d-118">Explication</span><span class="sxs-lookup"><span data-stu-id="87d6d-118">Explanation</span></span>  
 <span data-ttu-id="87d6d-119">Les composants peuvent uniquement appeler sur plusieurs threads lorsqu'ils n'utilisent pas une transaction.</span><span class="sxs-lookup"><span data-stu-id="87d6d-119">Components can only be multi-threaded when they do not have a transaction.</span></span> <span data-ttu-id="87d6d-120">Comme il traite une transaction, ce composant est verrouillé par un thread.</span><span class="sxs-lookup"><span data-stu-id="87d6d-120">This component has a transaction so it is locked to a thread.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87d6d-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="87d6d-121">User Action</span></span>  
 <span data-ttu-id="87d6d-122">Configurez votre application pour qu'elle n'appelle pas les composants de client SSO sur plusieurs threads lorsque ceux-ci utilisent des transactions.</span><span class="sxs-lookup"><span data-stu-id="87d6d-122">Configure your application so that it will not call SSO client components on multiple threads when using transactions.</span></span>
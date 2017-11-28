---
title: "Single Sign-On : Événement 10585 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51c55ada-1ee3-4626-b044-9c537d11f0d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b4781628121edad8904130e546038698de03161
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10585"></a><span data-ttu-id="4249a-102">Single Sign-On : Événement 10585</span><span class="sxs-lookup"><span data-stu-id="4249a-102">Single Sign-On: Event 10585</span></span>
## <a name="details"></a><span data-ttu-id="4249a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4249a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4249a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4249a-104">Product Name</span></span>|<span data-ttu-id="4249a-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="4249a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="4249a-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4249a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="4249a-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4249a-107">Event ID</span></span>|<span data-ttu-id="4249a-108">10585</span><span class="sxs-lookup"><span data-stu-id="4249a-108">10585</span></span>|  
|<span data-ttu-id="4249a-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4249a-109">Event Source</span></span>|<span data-ttu-id="4249a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4249a-110">ENTSSO</span></span>|  
|<span data-ttu-id="4249a-111">Composant</span><span class="sxs-lookup"><span data-stu-id="4249a-111">Component</span></span>|<span data-ttu-id="4249a-112">Néant</span><span class="sxs-lookup"><span data-stu-id="4249a-112">N/A</span></span>|  
|<span data-ttu-id="4249a-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4249a-113">Symbolic Name</span></span>|<span data-ttu-id="4249a-114">SSO_WARN_EXPIRED_TICKET_REDEEMED</span><span class="sxs-lookup"><span data-stu-id="4249a-114">SSO_WARN_EXPIRED_TICKET_REDEEMED</span></span>|  
|<span data-ttu-id="4249a-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4249a-115">Message Text</span></span>|<span data-ttu-id="4249a-116">Un ticket est échangé après que son délai d'expiration soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="4249a-116">A ticket is being redeemed after the ticket time-out period has expired.</span></span> <span data-ttu-id="4249a-117">Cette opération est autorisée car le délai d'expiration du ticket est désactivé pour cette application.%r</span><span class="sxs-lookup"><span data-stu-id="4249a-117">This is allowed because the ticket time-out is disabled for this application.%r</span></span><br /><br /> <span data-ttu-id="4249a-118">Nom de l’application : %1</span><span class="sxs-lookup"><span data-stu-id="4249a-118">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4249a-119">Explication</span><span class="sxs-lookup"><span data-stu-id="4249a-119">Explanation</span></span>  
 <span data-ttu-id="4249a-120">Le délai d'expiration du ticket peut être activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="4249a-120">Ticket time-out can be enabled or disabled.</span></span> <span data-ttu-id="4249a-121">Dans ce cas, un ticket est échangé même si son délai d'expiration est écoulé, car l'option d'expiration est désactivée.</span><span class="sxs-lookup"><span data-stu-id="4249a-121">In this case a ticket is being redeemed even though its time-out period has expired, because the time-out is disabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4249a-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4249a-122">User Action</span></span>  
 <span data-ttu-id="4249a-123">Si l'option d'expiration était supposée désactivée, aucune action n'est requise de la part de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4249a-123">If the time-out was supposed to be disabled, no user action is required.</span></span> <span data-ttu-id="4249a-124">Toutefois, si vous ne saviez pas que cette option était désactivée pour cette application particulière, vérifiez l'application immédiatement afin de vous assurer de vouloir l'autoriser.</span><span class="sxs-lookup"><span data-stu-id="4249a-124">However, if you were not aware that this particular application had its time-out disabled, check the application immediately to be sure you want to allow it.</span></span>
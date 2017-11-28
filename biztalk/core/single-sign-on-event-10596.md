---
title: "Single Sign-On : Événement 10596 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051fdf627edc3f560a8d02026207dc2fe5bb3533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10596"></a><span data-ttu-id="51b29-102">Single Sign-On : Événement 10596</span><span class="sxs-lookup"><span data-stu-id="51b29-102">Single Sign-On: Event 10596</span></span>
## <a name="details"></a><span data-ttu-id="51b29-103">Détails</span><span class="sxs-lookup"><span data-stu-id="51b29-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51b29-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="51b29-104">Product Name</span></span>|<span data-ttu-id="51b29-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="51b29-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="51b29-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="51b29-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="51b29-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="51b29-107">Event ID</span></span>|<span data-ttu-id="51b29-108">10596</span><span class="sxs-lookup"><span data-stu-id="51b29-108">10596</span></span>|  
|<span data-ttu-id="51b29-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="51b29-109">Event Source</span></span>|<span data-ttu-id="51b29-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="51b29-110">ENTSSO</span></span>|  
|<span data-ttu-id="51b29-111">Composant</span><span class="sxs-lookup"><span data-stu-id="51b29-111">Component</span></span>|<span data-ttu-id="51b29-112">Néant</span><span class="sxs-lookup"><span data-stu-id="51b29-112">N/A</span></span>|  
|<span data-ttu-id="51b29-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="51b29-113">Symbolic Name</span></span>|<span data-ttu-id="51b29-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span><span class="sxs-lookup"><span data-stu-id="51b29-114">SSO_WARN_TICKET_USER_NOT_IN_GROUP</span></span>|  
|<span data-ttu-id="51b29-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="51b29-115">Message Text</span></span>|<span data-ttu-id="51b29-116">Impossible d'échanger le ticket car l'utilisateur pour lequel il a été émis n'est pas un membre du compte Utilisateurs d'applications.%r</span><span class="sxs-lookup"><span data-stu-id="51b29-116">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="51b29-117">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="51b29-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="51b29-118">Ticket émis pour : %2 %r</span><span class="sxs-lookup"><span data-stu-id="51b29-118">Ticket Issued For: %2%r</span></span><br /><br /> <span data-ttu-id="51b29-119">Utilisateurs de l’application : %3</span><span class="sxs-lookup"><span data-stu-id="51b29-119">Application Users: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="51b29-120">Explication</span><span class="sxs-lookup"><span data-stu-id="51b29-120">Explanation</span></span>  
 <span data-ttu-id="51b29-121">Impossible d'échanger le ticket car l'utilisateur pour lequel il a été émis n'est pas un membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="51b29-121">The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="51b29-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="51b29-122">User Action</span></span>  
 <span data-ttu-id="51b29-123">Réémettez le ticket pour un client membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="51b29-123">Reissue the ticket to a user who is a member of the Application Users account.</span></span>
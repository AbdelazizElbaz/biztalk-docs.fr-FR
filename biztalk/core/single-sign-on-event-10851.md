---
title: "Single Sign-On : Événement 10851 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 582b92bf-2833-47cd-b685-1245e870d81d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdd719c77dc77fb626f97460ed92bd74ab6da812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10851"></a><span data-ttu-id="a09d9-102">Single Sign-On : Événement 10851</span><span class="sxs-lookup"><span data-stu-id="a09d9-102">Single Sign-On: Event 10851</span></span>
## <a name="details"></a><span data-ttu-id="a09d9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a09d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a09d9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a09d9-104">Product Name</span></span>|<span data-ttu-id="a09d9-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a09d9-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a09d9-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a09d9-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a09d9-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a09d9-107">Event ID</span></span>|<span data-ttu-id="a09d9-108">10851</span><span class="sxs-lookup"><span data-stu-id="a09d9-108">10851</span></span>|  
|<span data-ttu-id="a09d9-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a09d9-109">Event Source</span></span>|<span data-ttu-id="a09d9-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a09d9-110">ENTSSO</span></span>|  
|<span data-ttu-id="a09d9-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a09d9-111">Component</span></span>|<span data-ttu-id="a09d9-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a09d9-112">N/A</span></span>|  
|<span data-ttu-id="a09d9-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a09d9-113">Symbolic Name</span></span>|<span data-ttu-id="a09d9-114">ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC</span><span class="sxs-lookup"><span data-stu-id="a09d9-114">ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC</span></span>|  
|<span data-ttu-id="a09d9-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a09d9-115">Message Text</span></span>|<span data-ttu-id="a09d9-116">L'application ne peut pas être affectée à un adaptateur de synchronisation de mot de passe car l'indicateur « direct password sync » est défini pour elle.</span><span class="sxs-lookup"><span data-stu-id="a09d9-116">The application cannot be assigned to a password sync adapter because it has the 'direct password sync' flag set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a09d9-117">Explication</span><span class="sxs-lookup"><span data-stu-id="a09d9-117">Explanation</span></span>  
 <span data-ttu-id="a09d9-118">Une application ne peut pas utiliser la synchronisation de mot de passe directe et un adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a09d9-118">An application cannot use both direct password sync and a password sync adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a09d9-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a09d9-119">User Action</span></span>  
 <span data-ttu-id="a09d9-120">Examinez votre application et décidez si la synchronisation de mot de passe directe doit être activée pour elle. Dans l'affirmative, conservez l'indicateur défini tel que et ne tentez pas d'affecter l'application à un adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a09d9-120">Review your application and decide whether or not it should have direct password sync. If it should, leave the flag set as it is and do not attempt to assign the application to a password sync adapter.</span></span> <span data-ttu-id="a09d9-121">Dans la négative, désactivez l'indicateur et affectez l'application à un adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a09d9-121">If it should not, then turn the flag off and assign the application to a password sync adapter as appropriate.</span></span>
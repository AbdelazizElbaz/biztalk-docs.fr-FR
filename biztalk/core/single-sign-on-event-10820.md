---
title: "Single Sign-On : Événement 10820 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2da93a2c-d00d-4ca0-a0cf-453cee4bf3c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a3ae1be84ca0b936fe38463e51e6385071f7a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10820"></a><span data-ttu-id="796e2-102">Single Sign-On : Événement 10820</span><span class="sxs-lookup"><span data-stu-id="796e2-102">Single Sign-On: Event 10820</span></span>
## <a name="details"></a><span data-ttu-id="796e2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="796e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="796e2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="796e2-104">Product Name</span></span>|<span data-ttu-id="796e2-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="796e2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="796e2-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="796e2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="796e2-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="796e2-107">Event ID</span></span>|<span data-ttu-id="796e2-108">10820</span><span class="sxs-lookup"><span data-stu-id="796e2-108">10820</span></span>|  
|<span data-ttu-id="796e2-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="796e2-109">Event Source</span></span>|<span data-ttu-id="796e2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="796e2-110">ENTSSO</span></span>|  
|<span data-ttu-id="796e2-111">Composant</span><span class="sxs-lookup"><span data-stu-id="796e2-111">Component</span></span>|<span data-ttu-id="796e2-112">Néant</span><span class="sxs-lookup"><span data-stu-id="796e2-112">N/A</span></span>|  
|<span data-ttu-id="796e2-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="796e2-113">Symbolic Name</span></span>|<span data-ttu-id="796e2-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="796e2-114">ENTSSO_E_REQUIRE_OLD_PASSWORD</span></span>|  
|<span data-ttu-id="796e2-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="796e2-115">Message Text</span></span>|<span data-ttu-id="796e2-116">Lors de la modification du mot de passe d'un compte externe, l'adaptateur doit fournir l'ancien mot de passe.</span><span class="sxs-lookup"><span data-stu-id="796e2-116">When changing the password for an external account the adapter must supply the old password.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="796e2-117">Explication</span><span class="sxs-lookup"><span data-stu-id="796e2-117">Explanation</span></span>  
 <span data-ttu-id="796e2-118">La configuration de cette application requiert l'adaptateur de synchronisation de mot de passe pour fournir l'ancien mot de passe.</span><span class="sxs-lookup"><span data-stu-id="796e2-118">This application is configured in such a way that the password sync adapter is required to supply the old password.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="796e2-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="796e2-119">User Action</span></span>  
 <span data-ttu-id="796e2-120">Vérifiez la configuration de votre adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="796e2-120">Check the configuration of your password sync adapter.</span></span>
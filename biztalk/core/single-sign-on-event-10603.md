---
title: "Single Sign-On : Événement 10603 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 738d2939f4178fdfaa115b8dfcc2273935c37b85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10603"></a><span data-ttu-id="a84a4-102">Single Sign-On : Événement 10603</span><span class="sxs-lookup"><span data-stu-id="a84a4-102">Single Sign-On: Event 10603</span></span>
## <a name="details"></a><span data-ttu-id="a84a4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a84a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a84a4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a84a4-104">Product Name</span></span>|<span data-ttu-id="a84a4-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a84a4-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a84a4-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a84a4-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a84a4-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a84a4-107">Event ID</span></span>|<span data-ttu-id="a84a4-108">10603</span><span class="sxs-lookup"><span data-stu-id="a84a4-108">10603</span></span>|  
|<span data-ttu-id="a84a4-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a84a4-109">Event Source</span></span>|<span data-ttu-id="a84a4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a84a4-110">ENTSSO</span></span>|  
|<span data-ttu-id="a84a4-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a84a4-111">Component</span></span>|<span data-ttu-id="a84a4-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a84a4-112">N/A</span></span>|  
|<span data-ttu-id="a84a4-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a84a4-113">Symbolic Name</span></span>|<span data-ttu-id="a84a4-114">SSO_WARN_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="a84a4-114">SSO_WARN_DB_ACCESS</span></span>|  
|<span data-ttu-id="a84a4-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a84a4-115">Message Text</span></span>|<span data-ttu-id="a84a4-116">Impossible d'accéder à la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="a84a4-116">Could not access the SSO database.</span></span> <span data-ttu-id="a84a4-117">Si cette situation persiste, le service d'authentification unique se déconnecte.%r</span><span class="sxs-lookup"><span data-stu-id="a84a4-117">If this condition persists, the SSO service will go offline.%r</span></span><br /><br /> <span data-ttu-id="a84a4-118">%1.%r</span><span class="sxs-lookup"><span data-stu-id="a84a4-118">%1.%r</span></span><br /><br /> <span data-ttu-id="a84a4-119">Code d’erreur SQL : %2</span><span class="sxs-lookup"><span data-stu-id="a84a4-119">SQL Error code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a84a4-120">Explication</span><span class="sxs-lookup"><span data-stu-id="a84a4-120">Explanation</span></span>  
 <span data-ttu-id="a84a4-121">La base de données SSO n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="a84a4-121">The SSO database is unavailable.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a84a4-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a84a4-122">User Action</span></span>  
 <span data-ttu-id="a84a4-123">Consultez le code d'erreur SQL contenu dans l'avertissement.</span><span class="sxs-lookup"><span data-stu-id="a84a4-123">Check the SQL error code contained in the warning.</span></span> <span data-ttu-id="a84a4-124">Il peut vous donner des informations utiles.</span><span class="sxs-lookup"><span data-stu-id="a84a4-124">This may offer some guidance.</span></span> <span data-ttu-id="a84a4-125">Sinon, contactez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a84a4-125">If not, contact Microsoft Product Support Services.</span></span>
---
title: "Single Sign-On : Événement 10529 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ed70e0-8458-4736-883f-a4536f094dc0
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f33c0e475f9b54b5fc0a5d5415736d9717ccdf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10529"></a><span data-ttu-id="db7b2-102">Single Sign-On : Événement 10529</span><span class="sxs-lookup"><span data-stu-id="db7b2-102">Single Sign-On: Event 10529</span></span>
## <a name="details"></a><span data-ttu-id="db7b2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="db7b2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db7b2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="db7b2-104">Product Name</span></span>|<span data-ttu-id="db7b2-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="db7b2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="db7b2-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="db7b2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="db7b2-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="db7b2-107">Event ID</span></span>|<span data-ttu-id="db7b2-108">10529</span><span class="sxs-lookup"><span data-stu-id="db7b2-108">10529</span></span>|  
|<span data-ttu-id="db7b2-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="db7b2-109">Event Source</span></span>|<span data-ttu-id="db7b2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="db7b2-110">ENTSSO</span></span>|  
|<span data-ttu-id="db7b2-111">Composant</span><span class="sxs-lookup"><span data-stu-id="db7b2-111">Component</span></span>|<span data-ttu-id="db7b2-112">N\A</span><span class="sxs-lookup"><span data-stu-id="db7b2-112">N\A</span></span>|  
|<span data-ttu-id="db7b2-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="db7b2-113">Symbolic Name</span></span>|<span data-ttu-id="db7b2-114">SSO_INFO_GOT_CURRENT_SECRET</span><span class="sxs-lookup"><span data-stu-id="db7b2-114">SSO_INFO_GOT_CURRENT_SECRET</span></span>|  
|<span data-ttu-id="db7b2-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="db7b2-115">Message Text</span></span>|<span data-ttu-id="db7b2-116">Secret actuel obtenu auprès du serveur de secret principal.%r</span><span class="sxs-lookup"><span data-stu-id="db7b2-116">Got the current secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="db7b2-117">Nom du serveur de secret principal : %1 %r</span><span class="sxs-lookup"><span data-stu-id="db7b2-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="db7b2-118">MSID : %2</span><span class="sxs-lookup"><span data-stu-id="db7b2-118">MSID: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="db7b2-119">Explication</span><span class="sxs-lookup"><span data-stu-id="db7b2-119">Explanation</span></span>  
 <span data-ttu-id="db7b2-120">Cet événement d'informations indique que l'authentification unique a obtenu le secret principal demandé auprès du serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="db7b2-120">This Information event indicates that SSO has the requested master secret from the master secret server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="db7b2-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="db7b2-121">User Action</span></span>  
  
-   <span data-ttu-id="db7b2-122">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="db7b2-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="db7b2-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="db7b2-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="db7b2-124">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="db7b2-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="db7b2-125">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="db7b2-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
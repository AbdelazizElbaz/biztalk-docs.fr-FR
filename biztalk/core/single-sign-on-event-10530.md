---
title: "Single Sign-On : Événement 10530 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb37305-26fe-46a7-958d-3ed7f6876a7b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cf8759d2fe3b2281b87ffe9841bdd4e6b44081a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10530"></a><span data-ttu-id="e2b2b-102">Single Sign-On : Événement 10530</span><span class="sxs-lookup"><span data-stu-id="e2b2b-102">Single Sign-On: Event 10530</span></span>
## <a name="details"></a><span data-ttu-id="e2b2b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e2b2b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2b2b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e2b2b-104">Product Name</span></span>|<span data-ttu-id="e2b2b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e2b2b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e2b2b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e2b2b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e2b2b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e2b2b-107">Event ID</span></span>|<span data-ttu-id="e2b2b-108">10530</span><span class="sxs-lookup"><span data-stu-id="e2b2b-108">10530</span></span>|  
|<span data-ttu-id="e2b2b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e2b2b-109">Event Source</span></span>|<span data-ttu-id="e2b2b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e2b2b-110">ENTSSO</span></span>|  
|<span data-ttu-id="e2b2b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e2b2b-111">Component</span></span>|<span data-ttu-id="e2b2b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e2b2b-112">N\A</span></span>|  
|<span data-ttu-id="e2b2b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e2b2b-113">Symbolic Name</span></span>|<span data-ttu-id="e2b2b-114">SSO_INFO_GOT_PREVIOUS_SECRET</span><span class="sxs-lookup"><span data-stu-id="e2b2b-114">SSO_INFO_GOT_PREVIOUS_SECRET</span></span>|  
|<span data-ttu-id="e2b2b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e2b2b-115">Message Text</span></span>|<span data-ttu-id="e2b2b-116">Secret précédent obtenu du serveur de secret principal.%r</span><span class="sxs-lookup"><span data-stu-id="e2b2b-116">Got the previous secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="e2b2b-117">Nom du serveur de secret principal : %1 %r</span><span class="sxs-lookup"><span data-stu-id="e2b2b-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="e2b2b-118">MSID : %2</span><span class="sxs-lookup"><span data-stu-id="e2b2b-118">MSID: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e2b2b-119">Explication</span><span class="sxs-lookup"><span data-stu-id="e2b2b-119">Explanation</span></span>  
 <span data-ttu-id="e2b2b-120">Cet événement d'informations indique que l'authentification unique a obtenu le secret principal précédent.</span><span class="sxs-lookup"><span data-stu-id="e2b2b-120">This Information event indicates that SSO has the previous master secret.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2b2b-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e2b2b-121">User Action</span></span>  
  
-   <span data-ttu-id="e2b2b-122">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e2b2b-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="e2b2b-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="e2b2b-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="e2b2b-124">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="e2b2b-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="e2b2b-125">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="e2b2b-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
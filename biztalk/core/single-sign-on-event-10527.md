---
title: "Single Sign-On : Événement 10527 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf1785361ad343b3da4c7dc07b6a73a362fa14d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10527"></a><span data-ttu-id="a220b-102">Single Sign-On : Événement 10527</span><span class="sxs-lookup"><span data-stu-id="a220b-102">Single Sign-On: Event 10527</span></span>
## <a name="details"></a><span data-ttu-id="a220b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a220b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a220b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a220b-104">Product Name</span></span>|<span data-ttu-id="a220b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a220b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a220b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a220b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a220b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a220b-107">Event ID</span></span>|<span data-ttu-id="a220b-108">10527</span><span class="sxs-lookup"><span data-stu-id="a220b-108">10527</span></span>|  
|<span data-ttu-id="a220b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a220b-109">Event Source</span></span>|<span data-ttu-id="a220b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a220b-110">ENTSSO</span></span>|  
|<span data-ttu-id="a220b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a220b-111">Component</span></span>|<span data-ttu-id="a220b-112">0</span><span class="sxs-lookup"><span data-stu-id="a220b-112">0</span></span>|  
|<span data-ttu-id="a220b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a220b-113">Symbolic Name</span></span>|<span data-ttu-id="a220b-114">SSO_ERROR_GET_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="a220b-114">SSO_ERROR_GET_SECRET_FAILED</span></span>|  
|<span data-ttu-id="a220b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a220b-115">Message Text</span></span>|<span data-ttu-id="a220b-116">Une demande d'obtention d'un secret principal a échoué.%r</span><span class="sxs-lookup"><span data-stu-id="a220b-116">A request to get a master secret failed.%r</span></span><br /><br /> <span data-ttu-id="a220b-117">Numéro du secret : %1 %r</span><span class="sxs-lookup"><span data-stu-id="a220b-117">Secret Number: %1%r</span></span><br /><br /> <span data-ttu-id="a220b-118">L’utilisateur client : %2 %r</span><span class="sxs-lookup"><span data-stu-id="a220b-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="a220b-119">Ordinateur client : %3 %r</span><span class="sxs-lookup"><span data-stu-id="a220b-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="a220b-120">ID de suivi : %4 %r</span><span class="sxs-lookup"><span data-stu-id="a220b-120">Tracking ID: %4%r</span></span><br /><br /> <span data-ttu-id="a220b-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="a220b-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a220b-122">Explication</span><span class="sxs-lookup"><span data-stu-id="a220b-122">Explanation</span></span>  
 <span data-ttu-id="a220b-123">Cet événement d'erreur indique qu'une demande d'obtention du secret principal a échoué.</span><span class="sxs-lookup"><span data-stu-id="a220b-123">This Error event indicates that a request to get the master secret has failed.</span></span> <span data-ttu-id="a220b-124">Dans ce cas, le journal des événements de l'application doit contenir des messages associés.</span><span class="sxs-lookup"><span data-stu-id="a220b-124">In these cases there should be related messages in the Application event log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a220b-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a220b-125">User Action</span></span>  
 <span data-ttu-id="a220b-126">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a220b-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="a220b-127">Recherchez les événements ou erreurs associés dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="a220b-127">Check the Application event log for associated events or errors.</span></span>  
  
 <span data-ttu-id="a220b-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="a220b-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="a220b-129">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="a220b-129">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="a220b-130">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="a220b-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
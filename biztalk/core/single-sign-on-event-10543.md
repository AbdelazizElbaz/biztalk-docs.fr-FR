---
title: "Single Sign-On : Événement 10543 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b1ffda-a6c1-408c-acb4-074183d697bc
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9bf30640bf61f9c88de3fedbb5727be7a715aa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10543"></a><span data-ttu-id="00ef1-102">Single Sign-On : Événement 10543</span><span class="sxs-lookup"><span data-stu-id="00ef1-102">Single Sign-On: Event 10543</span></span>
## <a name="details"></a><span data-ttu-id="00ef1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="00ef1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00ef1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="00ef1-104">Product Name</span></span>|<span data-ttu-id="00ef1-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="00ef1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="00ef1-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="00ef1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="00ef1-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="00ef1-107">Event ID</span></span>|<span data-ttu-id="00ef1-108">10543</span><span class="sxs-lookup"><span data-stu-id="00ef1-108">10543</span></span>|  
|<span data-ttu-id="00ef1-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="00ef1-109">Event Source</span></span>|<span data-ttu-id="00ef1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="00ef1-110">ENTSSO</span></span>|  
|<span data-ttu-id="00ef1-111">Composant</span><span class="sxs-lookup"><span data-stu-id="00ef1-111">Component</span></span>|<span data-ttu-id="00ef1-112">CO</span><span class="sxs-lookup"><span data-stu-id="00ef1-112">CO</span></span>|  
|<span data-ttu-id="00ef1-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="00ef1-113">Symbolic Name</span></span>|<span data-ttu-id="00ef1-114">SSO_WARN_ORIGINAL_TICKET_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="00ef1-114">SSO_WARN_ORIGINAL_TICKET_VALIDATED</span></span>|  
|<span data-ttu-id="00ef1-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="00ef1-115">Message Text</span></span>|<span data-ttu-id="00ef1-116">Le ticket qui a été émis requiert la validation.</span><span class="sxs-lookup"><span data-stu-id="00ef1-116">The ticket was issued with validation required.</span></span> <span data-ttu-id="00ef1-117">Il ne peut pas être échangé pour cette application sans être validé.%r</span><span class="sxs-lookup"><span data-stu-id="00ef1-117">It cannot be redeemed for this application without being validated.%r</span></span><br /><br /> <span data-ttu-id="00ef1-118">Nom de l’application : %1</span><span class="sxs-lookup"><span data-stu-id="00ef1-118">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="00ef1-119">Explication</span><span class="sxs-lookup"><span data-stu-id="00ef1-119">Explanation</span></span>  
 <span data-ttu-id="00ef1-120">Cet événement d'avertissement indique qu'un ticket d'application qui a été émis requiert la validation.</span><span class="sxs-lookup"><span data-stu-id="00ef1-120">This Warning event indicates that an application ticket was issued with validation required.</span></span> <span data-ttu-id="00ef1-121">Les tickets ne peuvent pas être échangés sans être validés.</span><span class="sxs-lookup"><span data-stu-id="00ef1-121">Tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="00ef1-122">La validation du ticket est effectuée pour les applications associées individuelles.</span><span class="sxs-lookup"><span data-stu-id="00ef1-122">Validation of the ticket is on a per affiliate application basis.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00ef1-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="00ef1-123">User Action</span></span>  
 <span data-ttu-id="00ef1-124">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="00ef1-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="00ef1-125">Si vous utilisez l'authentification unique de l'entreprise, vérifiez que votre message est transmis via des hôtes approuvés uniquement.</span><span class="sxs-lookup"><span data-stu-id="00ef1-125">If you are using Enterprise Single Sign-On, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="00ef1-126">Cela permet de réduire le risque de falsification des données du message.</span><span class="sxs-lookup"><span data-stu-id="00ef1-126">This will reduce the risk of tampering with the data in the message.</span></span>  
  
-   <span data-ttu-id="00ef1-127">Si votre scénario le permet, désactivez l'étape de validation pour cette application.</span><span class="sxs-lookup"><span data-stu-id="00ef1-127">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="00ef1-128">La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="00ef1-128">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  
  
 <span data-ttu-id="00ef1-129">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="00ef1-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="00ef1-130">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="00ef1-130">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="00ef1-131">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="00ef1-131">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [<span data-ttu-id="00ef1-132">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="00ef1-132">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
---
title: "Single Sign-On : Événement 10542 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8e12444-b47c-4919-85b6-85c8e33b8342
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ebcf97a9de014d0651c9f239c1ae6e846925f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10542"></a><span data-ttu-id="4f0c7-102">Single Sign-On : Événement 10542</span><span class="sxs-lookup"><span data-stu-id="4f0c7-102">Single Sign-On: Event 10542</span></span>
## <a name="details"></a><span data-ttu-id="4f0c7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4f0c7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f0c7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4f0c7-104">Product Name</span></span>|<span data-ttu-id="4f0c7-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="4f0c7-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="4f0c7-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4f0c7-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="4f0c7-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4f0c7-107">Event ID</span></span>|<span data-ttu-id="4f0c7-108">10542</span><span class="sxs-lookup"><span data-stu-id="4f0c7-108">10542</span></span>|  
|<span data-ttu-id="4f0c7-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4f0c7-109">Event Source</span></span>|<span data-ttu-id="4f0c7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4f0c7-110">ENTSSO</span></span>|  
|<span data-ttu-id="4f0c7-111">Composant</span><span class="sxs-lookup"><span data-stu-id="4f0c7-111">Component</span></span>|<span data-ttu-id="4f0c7-112">CO</span><span class="sxs-lookup"><span data-stu-id="4f0c7-112">CO</span></span>|  
|<span data-ttu-id="4f0c7-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4f0c7-113">Symbolic Name</span></span>|<span data-ttu-id="4f0c7-114">SSO_WARN_APP_TICKETS_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="4f0c7-114">SSO_WARN_APP_TICKETS_VALIDATED</span></span>|  
|<span data-ttu-id="4f0c7-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4f0c7-115">Message Text</span></span>|<span data-ttu-id="4f0c7-116">Les tickets ne peuvent pas être échangés pour cette application s'ils n'ont pas été validés.%r</span><span class="sxs-lookup"><span data-stu-id="4f0c7-116">Tickets cannot be redeemed for this application without being validated.%r</span></span><br /><br /> <span data-ttu-id="4f0c7-117">Nom de l’application : %1</span><span class="sxs-lookup"><span data-stu-id="4f0c7-117">Application Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f0c7-118">Explication</span><span class="sxs-lookup"><span data-stu-id="4f0c7-118">Explanation</span></span>  
 <span data-ttu-id="4f0c7-119">Cet événement d'avertissement indique que les tickets de l'application ne peuvent pas être échangés sans être validés.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-119">This Warning event indicates that application tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="4f0c7-120">Une fois les tickets de l'application échangés, ils peuvent être validés ou non.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-120">When application tickets are redeemed they can be validated or not validated.</span></span> <span data-ttu-id="4f0c7-121">L'étape de validation permet d'accroître la sécurité en comparant le nom de l'utilisateur ayant émis le ticket avec le nom de l'utilisateur indiqué dans le message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-121">Validation improves security by comparing the name of the user who issued the ticket with the name of the user in the BizTalk message.</span></span> <span data-ttu-id="4f0c7-122">Si les noms diffèrent, la validation échoue.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-122">If the names are not the same then validation fails.</span></span> <span data-ttu-id="4f0c7-123">Lorsqu'un message BizTalk transite par un hôte non approuvé, le nom de l'utilisateur indiqué dans le message BizTalk est remplacé par celui de l'hôte non approuvé.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-123">When a BizTalk message flows through an un-trusted host, the name of the user in the BizTalk message is changed to that of the un-trusted host.</span></span> <span data-ttu-id="4f0c7-124">L'étape de validation permet de s'assurer que le message BizTalk a uniquement transité par les hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-124">Validation ensures that the BizTalk message has only flowed through trusted hosts.</span></span> <span data-ttu-id="4f0c7-125">Ce message signifie précisément que la validation est requise au niveau du système d'applications (en raison d'une option du système SSO définie), mais aucune information de validation n'a été fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-125">This message means specifically that validation is required at the application system level (due to an SSO system option setting), but no validation information was provided by the caller.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f0c7-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4f0c7-126">User Action</span></span>  
 <span data-ttu-id="4f0c7-127">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f0c7-127">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="4f0c7-128">Si vous utilisez BizTalk Server, assurez-vous que votre message transite uniquement par les hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-128">If you are using BizTalk Server, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="4f0c7-129">Cela permet de réduire le risque de falsification des données du message.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-129">This will reduce the risk of tampering with the data in the message.</span></span>  
  
-   <span data-ttu-id="4f0c7-130">Si votre scénario le permet, désactivez l'étape de validation pour cette application.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-130">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="4f0c7-131">La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="4f0c7-131">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  
  
 <span data-ttu-id="4f0c7-132">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="4f0c7-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="4f0c7-133">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="4f0c7-133">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="4f0c7-134">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="4f0c7-134">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [<span data-ttu-id="4f0c7-135">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="4f0c7-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
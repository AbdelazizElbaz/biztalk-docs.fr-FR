---
title: "Single Sign-On : Événement 10541 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e206158-5652-453c-91ac-9a75ab02809a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201a43682898f312687f3d5d453f3b050bc75d48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10541"></a><span data-ttu-id="9ad22-102">Single Sign-On : Événement 10541</span><span class="sxs-lookup"><span data-stu-id="9ad22-102">Single Sign-On: Event 10541</span></span>
## <a name="details"></a><span data-ttu-id="9ad22-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9ad22-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ad22-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9ad22-104">Product Name</span></span>|<span data-ttu-id="9ad22-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9ad22-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9ad22-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9ad22-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9ad22-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9ad22-107">Event ID</span></span>|<span data-ttu-id="9ad22-108">10541</span><span class="sxs-lookup"><span data-stu-id="9ad22-108">10541</span></span>|  
|<span data-ttu-id="9ad22-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9ad22-109">Event Source</span></span>|<span data-ttu-id="9ad22-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9ad22-110">ENTSSO</span></span>|  
|<span data-ttu-id="9ad22-111">Composant</span><span class="sxs-lookup"><span data-stu-id="9ad22-111">Component</span></span>|<span data-ttu-id="9ad22-112">CO</span><span class="sxs-lookup"><span data-stu-id="9ad22-112">CO</span></span>|  
|<span data-ttu-id="9ad22-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9ad22-113">Symbolic Name</span></span>|<span data-ttu-id="9ad22-114">SSO_WARN_SSO_TICKETS_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="9ad22-114">SSO_WARN_SSO_TICKETS_VALIDATED</span></span>|  
|<span data-ttu-id="9ad22-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9ad22-115">Message Text</span></span>|<span data-ttu-id="9ad22-116">Les tickets ne peuvent pas être échangés sans être validés.</span><span class="sxs-lookup"><span data-stu-id="9ad22-116">Tickets cannot be redeemed without being validated.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ad22-117">Explication</span><span class="sxs-lookup"><span data-stu-id="9ad22-117">Explanation</span></span>  
 <span data-ttu-id="9ad22-118">Cet événement d'avertissement indique que les tickets SSO ne peuvent pas être échangés sans être validés.</span><span class="sxs-lookup"><span data-stu-id="9ad22-118">This Warning event indicates that SSO tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="9ad22-119">Dans le cadre de leur échange, les tickets SSO peuvent être validés ou non.</span><span class="sxs-lookup"><span data-stu-id="9ad22-119">When SSO tickets are redeemed they can be validated or not validated.</span></span> <span data-ttu-id="9ad22-120">L'étape de validation permet d'accroître la sécurité en comparant le nom de l'utilisateur ayant émis le ticket avec le nom de l'utilisateur indiqué dans le message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9ad22-120">Validation improves security by comparing the name of the user who issued the ticket with the name of the user in the BizTalk message.</span></span> <span data-ttu-id="9ad22-121">Si les noms diffèrent, la validation échoue.</span><span class="sxs-lookup"><span data-stu-id="9ad22-121">If the names are not the same then validation fails.</span></span> <span data-ttu-id="9ad22-122">Lorsqu'un message BizTalk transite par un hôte non approuvé, le nom de l'utilisateur indiqué dans le message BizTalk est remplacé par celui de l'hôte non approuvé.</span><span class="sxs-lookup"><span data-stu-id="9ad22-122">When a BizTalk message flows through an un-trusted host, the name of the user in the BizTalk message is changed to that of the un-trusted host.</span></span> <span data-ttu-id="9ad22-123">L'étape de validation permet de s'assurer que le message BizTalk a uniquement transité par les hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="9ad22-123">Validation ensures that the BizTalk message has only flowed through trusted hosts.</span></span> <span data-ttu-id="9ad22-124">En particulier, ce message indique que la validation est requise au niveau du système SSO (en raison d'une option du système SSO) mais qu'aucune information de validation n'a été fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="9ad22-124">This message means specifically that validation is required at the SSO system level (due to an SSO system option setting), but no validation information was provided by the caller.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ad22-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9ad22-125">User Action</span></span>  
 <span data-ttu-id="9ad22-126">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ad22-126">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="9ad22-127">Si vous utilisez BizTalk Server, assurez-vous que votre message transite uniquement par les hôtes approuvés.</span><span class="sxs-lookup"><span data-stu-id="9ad22-127">If you are using BizTalk Server, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="9ad22-128">Cela permet de réduire le risque de falsification des données du message.</span><span class="sxs-lookup"><span data-stu-id="9ad22-128">This will reduce the risk of tampering with the data in the message.</span></span>  
  
-   <span data-ttu-id="9ad22-129">Si votre scénario le permet, désactivez l'étape de validation pour cette application.</span><span class="sxs-lookup"><span data-stu-id="9ad22-129">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="9ad22-130">La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="9ad22-130">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  
  
 <span data-ttu-id="9ad22-131">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="9ad22-131">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9ad22-132">Tickets SSO</span><span class="sxs-lookup"><span data-stu-id="9ad22-132">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="9ad22-133">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="9ad22-133">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [<span data-ttu-id="9ad22-134">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="9ad22-134">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
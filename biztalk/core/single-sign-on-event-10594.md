---
title: "Single Sign-On : Événement 10594 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804b2616080ceee0b6a31f7623e19e05c11481f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10594"></a><span data-ttu-id="c8af4-102">Single Sign-On : Événement 10594</span><span class="sxs-lookup"><span data-stu-id="c8af4-102">Single Sign-On: Event 10594</span></span>
## <a name="details"></a><span data-ttu-id="c8af4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c8af4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8af4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c8af4-104">Product Name</span></span>|<span data-ttu-id="c8af4-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c8af4-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c8af4-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c8af4-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c8af4-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c8af4-107">Event ID</span></span>|<span data-ttu-id="c8af4-108">10594</span><span class="sxs-lookup"><span data-stu-id="c8af4-108">10594</span></span>|  
|<span data-ttu-id="c8af4-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c8af4-109">Event Source</span></span>|<span data-ttu-id="c8af4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c8af4-110">ENTSSO</span></span>|  
|<span data-ttu-id="c8af4-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c8af4-111">Component</span></span>|<span data-ttu-id="c8af4-112">Néant</span><span class="sxs-lookup"><span data-stu-id="c8af4-112">N/A</span></span>|  
|<span data-ttu-id="c8af4-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c8af4-113">Symbolic Name</span></span>|<span data-ttu-id="c8af4-114">SSO_WARN_TICKET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="c8af4-114">SSO_WARN_TICKET_VALIDATE_FAILED</span></span>|  
|<span data-ttu-id="c8af4-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c8af4-115">Message Text</span></span>|<span data-ttu-id="c8af4-116">Échec de la validation du ticket.</span><span class="sxs-lookup"><span data-stu-id="c8af4-116">Validation of the ticket failed.</span></span> <span data-ttu-id="c8af4-117">Le nom de l'expéditeur doit correspondre à celui de l'émetteur du ticket.%r</span><span class="sxs-lookup"><span data-stu-id="c8af4-117">The sender name must match that of the ticket issuer.%r</span></span><br /><br /> <span data-ttu-id="c8af4-118">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="c8af4-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="c8af4-119">Ticket émis par : %2 %r</span><span class="sxs-lookup"><span data-stu-id="c8af4-119">Ticket Issued By: %2%r</span></span><br /><br /> <span data-ttu-id="c8af4-120">Nom de l’expéditeur : %3</span><span class="sxs-lookup"><span data-stu-id="c8af4-120">Sender Name: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c8af4-121">Explication</span><span class="sxs-lookup"><span data-stu-id="c8af4-121">Explanation</span></span>  
 <span data-ttu-id="c8af4-122">Pour qu'un ticket soit validé, les champs Ticket émis par et Nom de l'expéditeur (dans le message d'avertissement) doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="c8af4-122">In order for a ticket to be validated, the Ticket Issued By and Sender Name fields (in the warning message) must match.</span></span> <span data-ttu-id="c8af4-123">En revanche, si le message est transmis via un hôte BizTalk non approuvé, le champ Nom de l'expéditeur prend la valeur de l'hôte BizTalk non approuvé et le ticket n'est pas validé.</span><span class="sxs-lookup"><span data-stu-id="c8af4-123">If, however, the message is sent through a BizTalk untrusted host, the Sender Name gets changed to the name of the BizTalk untrusted host, and the ticket will not validate.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c8af4-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c8af4-124">User Action</span></span>  
 <span data-ttu-id="c8af4-125">Si vous utilisez l'authentification unique de l'entreprise, vérifiez que votre message est transmis via des hôtes BizTalk approuvés uniquement.</span><span class="sxs-lookup"><span data-stu-id="c8af4-125">If you are using Enterprise Single Sign-On, ensure that your message is flowing only through BizTalk trusted hosts.</span></span> <span data-ttu-id="c8af4-126">Cela permet de réduire le risque de falsification des données du message.</span><span class="sxs-lookup"><span data-stu-id="c8af4-126">This will reduce the risk of tampering with the data in the message.</span></span>  
  
 <span data-ttu-id="c8af4-127">Si vous ne maîtrisez pas entièrement les implications de sécurité pour votre cas, vous pouvez désactiver la validation pour cette application.</span><span class="sxs-lookup"><span data-stu-id="c8af4-127">If you fully understand the security implications for your scenario, you can turn off validation for this application.</span></span> <span data-ttu-id="c8af4-128">Notez que la validation est une option d'administration qui peut être désactivée pour le système ou pour cette application particulière.</span><span class="sxs-lookup"><span data-stu-id="c8af4-128">Note that validation is an administration option which can be turned off for the system or just for this particular application.</span></span>
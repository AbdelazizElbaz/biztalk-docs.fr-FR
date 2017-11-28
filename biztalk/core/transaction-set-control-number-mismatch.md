---
title: "Non-concordance de numéro de contrôle du document informatisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c4b0c3f-f3be-4c2c-8719-8e40aa7122b9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd80bac6a5c58306a8d9ca64748ddbb8cb2bc81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-control-number-mismatch"></a><span data-ttu-id="c0831-102">Numéro de contrôle de document informatisé incompatible</span><span class="sxs-lookup"><span data-stu-id="c0831-102">Transaction Set Control Number Mismatch</span></span>
## <a name="details"></a><span data-ttu-id="c0831-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c0831-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0831-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c0831-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c0831-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c0831-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c0831-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c0831-106">Event ID</span></span>|-|  
|<span data-ttu-id="c0831-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c0831-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c0831-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c0831-108"> EDI</span></span>|  
|<span data-ttu-id="c0831-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c0831-109">Component</span></span>|<span data-ttu-id="c0831-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c0831-110">EDI Engine</span></span>|  
|<span data-ttu-id="c0831-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c0831-111">Symbolic Name</span></span>|<span data-ttu-id="c0831-112">X12TsControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="c0831-112">X12TsControlNumberMismatchDescription</span></span>|  
|<span data-ttu-id="c0831-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c0831-113">Message Text</span></span>|<span data-ttu-id="c0831-114">Numéro de contrôle de document informatisé incompatible</span><span class="sxs-lookup"><span data-stu-id="c0831-114">Transaction Set Control Number Mismatch</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c0831-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c0831-115">Explanation</span></span>  
 <span data-ttu-id="c0831-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI a refusé le document informatisé entrant, car le numéro de contrôle contenu dans le champ SE02 de ce dernier ne correspondait pas à celui du champ ST02.</span><span class="sxs-lookup"><span data-stu-id="c0831-116">This Error/Warning/Information event indicates that the EDI receive pipeline rejected the incoming transaction set because the control number contained in the SE02 field of the transaction set did not match the control number in the ST02 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c0831-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0831-117">User Action</span></span>  
 <span data-ttu-id="c0831-118">Pour résoudre cette erreur, demandez à l'expéditeur du document informatisé de modifier le numéro de contrôle dans le champ SE02 du document informatisé refusé afin qu'il soit identique à celui du champ ST02, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="c0831-118">To resolve this error, have the sender of the transaction set change the control number in the SE02 field of the rejected transaction set to be the same as the control number in the ST02 field, and then resend the interchange.</span></span>
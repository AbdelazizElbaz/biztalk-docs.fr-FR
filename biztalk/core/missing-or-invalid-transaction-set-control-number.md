---
title: "Numéro de contrôle du jeu de transactions manquante ou non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6064b974-e8cd-4486-abc2-010afe0d956e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e9448c9be2cd05c7f7d8c18c13730933c1b5824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-transaction-set-control-number"></a><span data-ttu-id="ff8f3-102">Numéro de contrôle de document informatisé manquant ou non valide</span><span class="sxs-lookup"><span data-stu-id="ff8f3-102">Missing or invalid transaction set control number</span></span>
## <a name="details"></a><span data-ttu-id="ff8f3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ff8f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff8f3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ff8f3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ff8f3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ff8f3-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ff8f3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ff8f3-106">Event ID</span></span>|-|  
|<span data-ttu-id="ff8f3-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ff8f3-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ff8f3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ff8f3-108"> EDI</span></span>|  
|<span data-ttu-id="ff8f3-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ff8f3-109">Component</span></span>|<span data-ttu-id="ff8f3-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="ff8f3-110">EDI Engine</span></span>|  
|<span data-ttu-id="ff8f3-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ff8f3-111">Symbolic Name</span></span>|<span data-ttu-id="ff8f3-112">X12TsMissingOrInvalidTsControlNumberDescription</span><span class="sxs-lookup"><span data-stu-id="ff8f3-112">X12TsMissingOrInvalidTsControlNumberDescription</span></span>|  
|<span data-ttu-id="ff8f3-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ff8f3-113">Message Text</span></span>|<span data-ttu-id="ff8f3-114">Numéro de contrôle de document informatisé manquant ou non valide</span><span class="sxs-lookup"><span data-stu-id="ff8f3-114">Missing or invalid transaction set control number</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ff8f3-115">Explication</span><span class="sxs-lookup"><span data-stu-id="ff8f3-115">Explanation</span></span>  
 <span data-ttu-id="ff8f3-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception ou d'envoi n'a pas réussi à traiter l'échange, car la valeur du numéro de contrôle du document informatisé (champ ST02) était manquante ou non valide.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the interchange because the value of the transaction set control number (in the ST02 field) was missing or had an invalid value.</span></span> <span data-ttu-id="ff8f3-117">Le numéro de contrôle du document informatisé doit être une valeur alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-117">The transaction set control number must be an alphanumeric value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ff8f3-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ff8f3-118">User Action</span></span>  
 <span data-ttu-id="ff8f3-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff8f3-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="ff8f3-120">Assurez-vous que chaque document informatisé dispose d'un numéro de contrôle de document informatisé.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-120">Make sure that each transaction set has a transaction set control number.</span></span>  
  
2.  <span data-ttu-id="ff8f3-121">Assurez-vous que chaque numéro de contrôle de document informatisé est une valeur alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="ff8f3-121">Make sure that each transaction set control number is an alphanumeric value.</span></span>
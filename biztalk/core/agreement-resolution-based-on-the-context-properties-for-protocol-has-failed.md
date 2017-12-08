---
title: "Résolution de l’accord basée sur les propriétés de contexte de protocole a échoué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58fccd84-579c-4b5e-872b-33730d4079e8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76d74ad7aa4a73f4a0befcef32bc8051195cb080
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-based-on-the-context-properties-for-protocol-has-failed"></a><span data-ttu-id="79c84-102">La résolution de l'accord basée sur les propriétés de contexte du protocole a échoué.</span><span class="sxs-lookup"><span data-stu-id="79c84-102">Agreement Resolution based on the context properties for Protocol has failed</span></span>
## <a name="details"></a><span data-ttu-id="79c84-103">Détails</span><span class="sxs-lookup"><span data-stu-id="79c84-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79c84-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="79c84-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="79c84-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="79c84-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="79c84-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="79c84-106">Event ID</span></span>|-|  
|<span data-ttu-id="79c84-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="79c84-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="79c84-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="79c84-108"> EDI</span></span>|  
|<span data-ttu-id="79c84-109">Composant</span><span class="sxs-lookup"><span data-stu-id="79c84-109">Component</span></span>|<span data-ttu-id="79c84-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="79c84-110">EDI Engine</span></span>|  
|<span data-ttu-id="79c84-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="79c84-111">Symbolic Name</span></span>|<span data-ttu-id="79c84-112">AgreementResolutionContextPropertiesLookupFailed</span><span class="sxs-lookup"><span data-stu-id="79c84-112">AgreementResolutionContextPropertiesLookupFailed</span></span>|  
|<span data-ttu-id="79c84-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="79c84-113">Message Text</span></span>|<span data-ttu-id="79c84-114">Résolution de l’accord basée sur les propriétés de contexte pour {0} protocole a échoué.</span><span class="sxs-lookup"><span data-stu-id="79c84-114">Agreement Resolution based on the context properties for {0} Protocol has failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="79c84-115">Explication</span><span class="sxs-lookup"><span data-stu-id="79c84-115">Explanation</span></span>  
 <span data-ttu-id="79c84-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre l'accord sur la base des propriétés de contexte fournies par le client.</span><span class="sxs-lookup"><span data-stu-id="79c84-116">This Error/Warning/Information event indicates BizTalk Server was not able to resolve to an Agreement based on the context properties that are provided by the customer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79c84-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="79c84-117">User Action</span></span>  
 <span data-ttu-id="79c84-118">Pour résoudre cette erreur, renseignez les propriétés de contexte dans le message BizTalk de manière à ce que la résolution de l'accord puisse se produire.</span><span class="sxs-lookup"><span data-stu-id="79c84-118">To resolve this error, please provide the context properties as part of the BizTalk message such that Agreement Resolution can happen.</span></span>
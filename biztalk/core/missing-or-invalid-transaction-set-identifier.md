---
title: Identificateur du jeu de transactions manquante ou non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 282c8128-7d23-44e2-bf44-e90e52cb5fb1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f23f44587abf67e608cff79150d9633f1707ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-transaction-set-identifier"></a><span data-ttu-id="bbe9a-102">Identificateur du jeu de transactions manquante ou non valide</span><span class="sxs-lookup"><span data-stu-id="bbe9a-102">Missing or invalid Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="bbe9a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bbe9a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbe9a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bbe9a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bbe9a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bbe9a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="bbe9a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bbe9a-106">Event ID</span></span>|-|  
|<span data-ttu-id="bbe9a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bbe9a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bbe9a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="bbe9a-108"> EDI</span></span>|  
|<span data-ttu-id="bbe9a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="bbe9a-109">Component</span></span>|<span data-ttu-id="bbe9a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="bbe9a-110">EDI Engine</span></span>|  
|<span data-ttu-id="bbe9a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bbe9a-111">Symbolic Name</span></span>|<span data-ttu-id="bbe9a-112">EfactTsMissingOrInvalidTsIdentiferDescription</span><span class="sxs-lookup"><span data-stu-id="bbe9a-112">EfactTsMissingOrInvalidTsIdentiferDescription</span></span>|  
|<span data-ttu-id="bbe9a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bbe9a-113">Message Text</span></span>|<span data-ttu-id="bbe9a-114">Identificateur du jeu de transactions manquante ou non valide</span><span class="sxs-lookup"><span data-stu-id="bbe9a-114">Missing or invalid Transaction set identifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bbe9a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="bbe9a-115">Explanation</span></span>  
 <span data-ttu-id="bbe9a-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception ou d'envoi n'a pas pu traiter l'échange EDIFACT, car la valeur de l'identificateur de document informatisé (dans le champ UNH2.1) était manquante ou non valide.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the EDIFACT interchange because the value of the transaction set identifier (in the UNH2.1 field) was missing or had an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bbe9a-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bbe9a-117">User Action</span></span>  
 <span data-ttu-id="bbe9a-118">Pour résoudre cette erreur, assurez-vous que l'échange dispose d'une valeur pour le champ UNH2.1.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-118">To resolve this error, make sure that the interchange has a value for the UNH2.1 field.</span></span> <span data-ttu-id="bbe9a-119">Vérifiez que la valeur de UNH2.1 est un indicateur de type document valide de un à six caractères.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-119">Verify that the value of UNH2.1 is a valid one-digit to six-digit document-type designator.</span></span>
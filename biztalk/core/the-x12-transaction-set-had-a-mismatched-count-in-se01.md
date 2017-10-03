---
title: "Le X12 informatisé comportait un nombre incompatible dans SE01 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90079f5-5939-40b6-9756-d7943240c125
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41539f0492f90d3f7276b0d80af28c568593ef4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-x12-transaction-set-had-a-mismatched-count-in-se01"></a><span data-ttu-id="0cc4c-102">Le document informatisé X12 présentait un nombre incompatible dans SE01</span><span class="sxs-lookup"><span data-stu-id="0cc4c-102">The X12 Transaction set had a mismatched count in SE01</span></span>
## <a name="details"></a><span data-ttu-id="0cc4c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0cc4c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0cc4c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0cc4c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0cc4c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0cc4c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0cc4c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0cc4c-106">Event ID</span></span>|-|  
|<span data-ttu-id="0cc4c-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0cc4c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0cc4c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0cc4c-108"> EDI</span></span>|  
|<span data-ttu-id="0cc4c-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0cc4c-109">Component</span></span>|<span data-ttu-id="0cc4c-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="0cc4c-110">EDI Engine</span></span>|  
|<span data-ttu-id="0cc4c-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0cc4c-111">Symbolic Name</span></span>|<span data-ttu-id="0cc4c-112">X12StSeCountMismatch</span><span class="sxs-lookup"><span data-stu-id="0cc4c-112">X12StSeCountMismatch</span></span>|  
|<span data-ttu-id="0cc4c-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0cc4c-113">Message Text</span></span>|<span data-ttu-id="0cc4c-114">Le document informatisé X12 présentait un nombre incompatible dans SE01.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-114">The X12 Transaction set had a mismatched count in SE01.</span></span> <span data-ttu-id="0cc4c-115">SE01 était {0}, alors qu’elle aurait dû être {{1}.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-115">SE01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="0cc4c-116">Il a été corrigé.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-116">It has been corrected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0cc4c-117">Explication</span><span class="sxs-lookup"><span data-stu-id="0cc4c-117">Explanation</span></span>  
 <span data-ttu-id="0cc4c-118">Cet avertissement indique que le nombre spécifié dans le code de fin du document informatisé (champ SE01) ne correspond pas au nombre de segments dans le document informatisé de l'échange.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-118">This Warning indicates that the number in the transaction set trailer (SE01 field) did not match the number of segments in the transaction set of the interchange.</span></span> <span data-ttu-id="0cc4c-119">Le pipeline d'envoi corrige le nombre dans le champ SE01 et publie l'avertissement.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-119">The send pipeline corrects the count in the SE01 field and posts the warning.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0cc4c-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0cc4c-120">User Action</span></span>  
 <span data-ttu-id="0cc4c-121">Aucune action n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0cc4c-121">No action is necessary.</span></span>
---
title: "Nombre de documents informatisés inclus ne correspond pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db958803-4667-4558-81a6-70c62d6fe8bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16a28544757c3e9ae75dd7230673c4526fc2c8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-transaction-sets-do-not-match"></a><span data-ttu-id="427d9-102">Le nombre de documents informatisés inclus ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="427d9-102">Number of included transaction sets do not match</span></span>
## <a name="details"></a><span data-ttu-id="427d9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="427d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="427d9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="427d9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="427d9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="427d9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="427d9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="427d9-106">Event ID</span></span>|-|  
|<span data-ttu-id="427d9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="427d9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="427d9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="427d9-108"> EDI</span></span>|  
|<span data-ttu-id="427d9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="427d9-109">Component</span></span>|<span data-ttu-id="427d9-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="427d9-110">EDI Engine</span></span>|  
|<span data-ttu-id="427d9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="427d9-111">Symbolic Name</span></span>|<span data-ttu-id="427d9-112">X12FaNumberOfTsMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="427d9-112">X12FaNumberOfTsMismatchDescription</span></span>|  
|<span data-ttu-id="427d9-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="427d9-113">Message Text</span></span>|<span data-ttu-id="427d9-114">Le nombre de documents informatisés inclus ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="427d9-114">Number of included transaction sets do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="427d9-115">Explication</span><span class="sxs-lookup"><span data-stu-id="427d9-115">Explanation</span></span>  
 <span data-ttu-id="427d9-116">Cet événement d'erreur/d'avertissement/d'informations indique que le nombre de documents informatisés dans le groupe de l'échange X12 n'est pas égal au nombre dans le code de fin du groupe (champ GE01).</span><span class="sxs-lookup"><span data-stu-id="427d9-116">This Error/Warning/Information event indicates that the number of transaction sets in the group of the X12 interchange does not equal the number in the group trailer (GE01 field).</span></span> <span data-ttu-id="427d9-117">Cette situation se produit lorsque l'échange est conservé et que celui-ci est interrompu en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="427d9-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span> <span data-ttu-id="427d9-118">(Le message d'erreur n'est pas publié dans deux cas : lorsque l'échange est conservé et que les documents informatisés sont interrompus en cas d'erreur et lorsque l'échange est fractionné).</span><span class="sxs-lookup"><span data-stu-id="427d9-118">(The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="427d9-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="427d9-119">User Action</span></span>  
 <span data-ttu-id="427d9-120">Pour résoudre cette erreur, assurez-vous que le nombre dans le champ GE01 du code de fin du groupe est identique au nombre de documents informatisés dans le groupe de l'échange, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="427d9-120">To resolve this error, make sure that the number in the GE01 field of the group trailer is the same as the number of transaction sets in the group of the interchange, and then resend the interchange.</span></span>
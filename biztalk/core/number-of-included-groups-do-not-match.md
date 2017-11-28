---
title: Nombre de groupes inclus ne correspond pas | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d61ac17-92cd-4a5e-81e6-e2c6fc4085bb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f02262012a5d02cebaf86fae5a4d19d9b5486d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-groups-do-not-match"></a><span data-ttu-id="b6244-102">Le nombre de groupes inclus ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="b6244-102">Number of included groups do not match</span></span>
## <a name="details"></a><span data-ttu-id="b6244-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b6244-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6244-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b6244-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b6244-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b6244-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b6244-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b6244-106">Event ID</span></span>|-|  
|<span data-ttu-id="b6244-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b6244-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b6244-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b6244-108"> EDI</span></span>|  
|<span data-ttu-id="b6244-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b6244-109">Component</span></span>|<span data-ttu-id="b6244-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="b6244-110">EDI Engine</span></span>|  
|<span data-ttu-id="b6244-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b6244-111">Symbolic Name</span></span>|<span data-ttu-id="b6244-112">X12Ta1InvalidNumberOfIncludedGroupsDescription</span><span class="sxs-lookup"><span data-stu-id="b6244-112">X12Ta1InvalidNumberOfIncludedGroupsDescription</span></span>|  
|<span data-ttu-id="b6244-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b6244-113">Message Text</span></span>|<span data-ttu-id="b6244-114">Nombre d’inclus groupes ne correspondent pas</span><span class="sxs-lookup"><span data-stu-id="b6244-114">Number Of included groups do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6244-115">Explication</span><span class="sxs-lookup"><span data-stu-id="b6244-115">Explanation</span></span>  
 <span data-ttu-id="b6244-116">Cet événement de type erreur/avertissement/information indique que le nombre de groupes dans l'échange n'est pas égal au nombre figurant dans le code de fin de l'échange (champ IEA01).</span><span class="sxs-lookup"><span data-stu-id="b6244-116">This Error/Warning/Information event indicates that the number of groups in the interchange does not equal the number in the interchange trailer (IEA01 field).</span></span> <span data-ttu-id="b6244-117">Cette situation se produit lorsque l'échange est conservé et que celui-ci est interrompu en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="b6244-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span> <span data-ttu-id="b6244-118">(Le message d'erreur n'est pas publié dans deux cas : lorsque l'échange est conservé et que les documents informatisés sont interrompus en cas d'erreur et lorsque l'échange est fractionné).</span><span class="sxs-lookup"><span data-stu-id="b6244-118">(The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6244-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b6244-119">User Action</span></span>  
 <span data-ttu-id="b6244-120">Pour résoudre cette erreur, assurez-vous que le nombre figurant dans le champ IEA01 du code fin de l'échange est identique au nombre de groupes dans l'échange, puis procédez à un nouvel envoi de l'échange.</span><span class="sxs-lookup"><span data-stu-id="b6244-120">To resolve this error, make sure that the number in the IEA01 field of the interchange trailer is the same as the number of groups in the interchange, and then resend the interchange.</span></span>
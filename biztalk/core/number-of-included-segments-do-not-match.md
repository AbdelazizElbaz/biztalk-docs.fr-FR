---
title: Nombre de segments inclus ne correspond pas | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c868de02-fda7-4d84-be50-2c08cde0450c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01878c11c8464968b31a7f34ff75b5b494309f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-segments-do-not-match"></a><span data-ttu-id="0697e-102">Le nombre de segments inclus ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="0697e-102">Number of included segments do not match</span></span>
## <a name="details"></a><span data-ttu-id="0697e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0697e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0697e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0697e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0697e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0697e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0697e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0697e-106">Event ID</span></span>|-|  
|<span data-ttu-id="0697e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0697e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0697e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0697e-108"> EDI</span></span>|  
|<span data-ttu-id="0697e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0697e-109">Component</span></span>|<span data-ttu-id="0697e-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="0697e-110">EDI Engine</span></span>|  
|<span data-ttu-id="0697e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0697e-111">Symbolic Name</span></span>|<span data-ttu-id="0697e-112">X12TsIncludedSegCountMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="0697e-112">X12TsIncludedSegCountMismatchDescription</span></span>|  
|<span data-ttu-id="0697e-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0697e-113">Message Text</span></span>|<span data-ttu-id="0697e-114">Le nombre de segments inclus ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="0697e-114">Number of included segments do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0697e-115">Explication</span><span class="sxs-lookup"><span data-stu-id="0697e-115">Explanation</span></span>  
 <span data-ttu-id="0697e-116">Cet événement d'erreur/d'avertissement/d'informations indique que le nombre de segments du document informatisé de l'échange X12 n'est pas égal au nombre dans le code de fin du document informatisé (champ SE01).</span><span class="sxs-lookup"><span data-stu-id="0697e-116">This Error/Warning/Information event indicates that the number of segments in the transaction set of the X12 interchange does not equal the number in the transaction set trailer (SE01 field).</span></span> <span data-ttu-id="0697e-117">Cette situation se produit lorsque l'échange est conservé et que celui-ci est interrompu en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0697e-117">This occurs when the interchange is preserved and the interchange is suspended on an error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0697e-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0697e-118">User Action</span></span>  
 <span data-ttu-id="0697e-119">Pour résoudre cette erreur, assurez-vous que le nombre dans le champ SE01 du code de fin de l'échange soit identique au nombre de segments du document informatisé, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="0697e-119">To resolve this error, make sure that the number in the SE01 field of the interchange trailer is the same as the number of segments in the transaction set, and then resend the interchange.</span></span>
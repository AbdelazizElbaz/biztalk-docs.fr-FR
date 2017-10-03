---
title: "Un élément de fin est introuvable à la profondeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1edb60a-122a-4fe9-8d73-96521fe7326b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a90265b4348e4d35b66099f426b6f6177851ccc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-end-element-could-not-be-found-at-depth"></a><span data-ttu-id="a742a-102">Un élément de fin à la profondeur n'a pas pu être trouvé</span><span class="sxs-lookup"><span data-stu-id="a742a-102">An End Element could not be found at depth</span></span>
## <a name="details"></a><span data-ttu-id="a742a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a742a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a742a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a742a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a742a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a742a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a742a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a742a-106">Event ID</span></span>|-|  
|<span data-ttu-id="a742a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a742a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a742a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a742a-108"> EDI</span></span>|  
|<span data-ttu-id="a742a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a742a-109">Component</span></span>|<span data-ttu-id="a742a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a742a-110">EDI Engine</span></span>|  
|<span data-ttu-id="a742a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a742a-111">Symbolic Name</span></span>|<span data-ttu-id="a742a-112">EndElementNotFoundAtDepth</span><span class="sxs-lookup"><span data-stu-id="a742a-112">EndElementNotFoundAtDepth</span></span>|  
|<span data-ttu-id="a742a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a742a-113">Message Text</span></span>|<span data-ttu-id="a742a-114">Un élément de fin à la profondeur {0} n'a pas pu être trouvé</span><span class="sxs-lookup"><span data-stu-id="a742a-114">An End Element at depth {0} could not be found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a742a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a742a-115">Explanation</span></span>  
 <span data-ttu-id="a742a-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu traiter l'échange sortant car la validation du message XML a échoué.</span><span class="sxs-lookup"><span data-stu-id="a742a-116">This Error/Warning/Information event indicates that BizTalk Server could not process the outgoing interchange because the XML message failed validation.</span></span> <span data-ttu-id="a742a-117">Le message XML ne contenait pas de balise de fin pour un en-tête ou élément de données.</span><span class="sxs-lookup"><span data-stu-id="a742a-117">The XML message did not contain an end tag for a header or data element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a742a-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a742a-118">User Action</span></span>  
 <span data-ttu-id="a742a-119">Pour résoudre cette erreur, ajoutez la balise ou le code de fin approprié au message XML, puis renvoyez-le.</span><span class="sxs-lookup"><span data-stu-id="a742a-119">To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend.</span></span>
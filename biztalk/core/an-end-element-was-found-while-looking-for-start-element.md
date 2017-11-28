---
title: "Un élément de fin a été trouvé lors de la recherche à l’élément de départ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dacaa096b15a6f2969ed56b5bac2138876a6095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a><span data-ttu-id="39700-102">Un élément de fin a été trouvé lors de la recherche de l'élément de départ</span><span class="sxs-lookup"><span data-stu-id="39700-102">An End Element was found while looking for Start Element</span></span>
## <a name="details"></a><span data-ttu-id="39700-103">Détails</span><span class="sxs-lookup"><span data-stu-id="39700-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39700-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="39700-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="39700-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="39700-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="39700-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="39700-106">Event ID</span></span>|-|  
|<span data-ttu-id="39700-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="39700-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="39700-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="39700-108"> EDI</span></span>|  
|<span data-ttu-id="39700-109">Composant</span><span class="sxs-lookup"><span data-stu-id="39700-109">Component</span></span>|<span data-ttu-id="39700-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="39700-110">EDI Engine</span></span>|  
|<span data-ttu-id="39700-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="39700-111">Symbolic Name</span></span>|<span data-ttu-id="39700-112">EndElementFoundWhenLookingForStartElement</span><span class="sxs-lookup"><span data-stu-id="39700-112">EndElementFoundWhenLookingForStartElement</span></span>|  
|<span data-ttu-id="39700-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="39700-113">Message Text</span></span>|<span data-ttu-id="39700-114">Un élément de fin avec le nom {0} a été trouvé, lors de la recherche de départ possédant avec nom {{1}, à {{2} de profondeur</span><span class="sxs-lookup"><span data-stu-id="39700-114">An EndElement with name {0} was found, while looking for StartElement with name {1}, at depth {2}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="39700-115">Explication</span><span class="sxs-lookup"><span data-stu-id="39700-115">Explanation</span></span>  
 <span data-ttu-id="39700-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu traiter un message XML entrant (après l'analyse) ou un message XML sortant (avant la sérialisation) car la validation du message XML a échoué.</span><span class="sxs-lookup"><span data-stu-id="39700-116">This Error/Warning/Information event indicates that BizTalk Server could not process an incoming XML message (after parsing) or an outgoing XML message (before serialization) because the XML message failed validation.</span></span> <span data-ttu-id="39700-117">Le message XML ne contenait pas de balise de fin pour un en-tête ou élément de données.</span><span class="sxs-lookup"><span data-stu-id="39700-117">The XML message did not contain an end tag for a header or data element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="39700-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="39700-118">User Action</span></span>  
 <span data-ttu-id="39700-119">Pour résoudre cette erreur, ajoutez la balise ou le code de fin approprié au message XML, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="39700-119">To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend the message.</span></span>
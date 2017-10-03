---
title: "Délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69475949b404474ff4dc9fe53d553c24e125939c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a><span data-ttu-id="7d5f7-102">Les délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont identiques</span><span class="sxs-lookup"><span data-stu-id="7d5f7-102">Delimiters are not unique, segment and component separators are the same</span></span>
## <a name="details"></a><span data-ttu-id="7d5f7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7d5f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d5f7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7d5f7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7d5f7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7d5f7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7d5f7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7d5f7-106">Event ID</span></span>|-|  
|<span data-ttu-id="7d5f7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7d5f7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7d5f7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7d5f7-108"> EDI</span></span>|  
|<span data-ttu-id="7d5f7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7d5f7-109">Component</span></span>|<span data-ttu-id="7d5f7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7d5f7-110">EDI Engine</span></span>|  
|<span data-ttu-id="7d5f7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7d5f7-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="7d5f7-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7d5f7-112">Message Text</span></span>|<span data-ttu-id="7d5f7-113">Les délimiteurs ne sont pas uniques, les séparateurs de segments et de composants sont identiques</span><span class="sxs-lookup"><span data-stu-id="7d5f7-113">Delimiters are not unique, segment and component separators are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7d5f7-114">Explication</span><span class="sxs-lookup"><span data-stu-id="7d5f7-114">Explanation</span></span>  
 <span data-ttu-id="7d5f7-115">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car le terminateur de segment ou le séparateur de composants avaient la même valeur.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the segment terminator or the component separator were the same value.</span></span> <span data-ttu-id="7d5f7-116">Dans un échange X12, le terminateur de segment correspond au caractère situé en dernière position du segment ISA, alors que le séparateur de composants est le caractère situé dans le champ ISA16.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-116">In an X12 interchange, the segment terminator is character in the last character position of the ISA segment and the component separator is the character in the ISA16 field.</span></span> <span data-ttu-id="7d5f7-117">Dans un échange EDIFACT, le terminateur de segment correspond au caractère du champ UNA6, alors que le séparateur de composants est le caractère situé dans le champ UNA1.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-117">In an EDIFACT interchange, the segment terminator is the character in the UNA6 field and the component separator is the character in the UNA1 field.</span></span> <span data-ttu-id="7d5f7-118">Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7d5f7-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7d5f7-119">User Action</span></span>  
 <span data-ttu-id="7d5f7-120">Pour résoudre cette erreur, modifiez la valeur du terminateur de segment ou du séparateur de composants dans l'échange, puis soumettez à nouveau ce dernier.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-120">To resolve this error, change the value of either the segment terminator or the component separator in the interchange, and then resubmit the interchange.</span></span>
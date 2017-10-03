---
title: "Délimiteurs ne sont pas uniques, le séparateur de champs et de segments sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1441434a-e969-4803-8e44-c7738d9b23ed
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 440ffb1213936fba4b08a8ee478f6c141eba38fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-field-and-segment-separator-are-the-same"></a><span data-ttu-id="15d99-102">Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de segments sont identiques</span><span class="sxs-lookup"><span data-stu-id="15d99-102">Delimiters are not unique, field and segment separator are the same</span></span>
## <a name="details"></a><span data-ttu-id="15d99-103">Détails</span><span class="sxs-lookup"><span data-stu-id="15d99-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15d99-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="15d99-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="15d99-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="15d99-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="15d99-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="15d99-106">Event ID</span></span>|-|  
|<span data-ttu-id="15d99-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="15d99-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="15d99-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="15d99-108"> EDI</span></span>|  
|<span data-ttu-id="15d99-109">Composant</span><span class="sxs-lookup"><span data-stu-id="15d99-109">Component</span></span>|<span data-ttu-id="15d99-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="15d99-110">EDI Engine</span></span>|  
|<span data-ttu-id="15d99-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="15d99-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="15d99-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="15d99-112">Message Text</span></span>|<span data-ttu-id="15d99-113">Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de segments sont identiques</span><span class="sxs-lookup"><span data-stu-id="15d99-113">Delimiters are not unique, field and segment separator are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="15d99-114">Explication</span><span class="sxs-lookup"><span data-stu-id="15d99-114">Explanation</span></span>  
 <span data-ttu-id="15d99-115">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car l'élément de données et les séparateurs de segments avaient la même valeur.</span><span class="sxs-lookup"><span data-stu-id="15d99-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and segment separators were the same value.</span></span> <span data-ttu-id="15d99-116">Dans un échange X12, le séparateur d'éléments de données est le caractère se trouvant à la quatrième position du segment ISA et le terminateur de segment est le caractère figurant en dernière position du segment ISA.</span><span class="sxs-lookup"><span data-stu-id="15d99-116">In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the segment terminator is the character in the last character position of the ISA segment.</span></span> <span data-ttu-id="15d99-117">Dans un échange EDIFACT, le séparateur d'éléments de données est le caractère figurant dans le champ UNA2 et le terminateur de segment est le caractère figurant dans le champ UNA6.</span><span class="sxs-lookup"><span data-stu-id="15d99-117">In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the segment terminator is the character in the UNA6 field.</span></span> <span data-ttu-id="15d99-118">Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="15d99-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="15d99-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="15d99-119">User Action</span></span>  
 <span data-ttu-id="15d99-120">Pour résoudre cette erreur, modifiez la valeur de l'élément de données ou du séparateur de segments dans l'échange, puis soumettez à nouveau ce dernier.</span><span class="sxs-lookup"><span data-stu-id="15d99-120">To resolve this error, change the value of either the data element or segment separator in the interchange, and then resubmit the interchange.</span></span>
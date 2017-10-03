---
title: "Délimiteurs ne sont pas uniques, de champ et le séparateur de composants sont les mêmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba15b30-b07d-4caa-8c43-6b4d8c4ca81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f803612a905f0be196afcfc0b43af23501ccdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-field-and-component-separator-are-the-same"></a><span data-ttu-id="a7f6c-102">Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de composants sont identiques</span><span class="sxs-lookup"><span data-stu-id="a7f6c-102">Delimiters are not unique, field and component separator are the same</span></span>
## <a name="details"></a><span data-ttu-id="a7f6c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a7f6c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7f6c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a7f6c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a7f6c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a7f6c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a7f6c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a7f6c-106">Event ID</span></span>|-|  
|<span data-ttu-id="a7f6c-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a7f6c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a7f6c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a7f6c-108"> EDI</span></span>|  
|<span data-ttu-id="a7f6c-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a7f6c-109">Component</span></span>|<span data-ttu-id="a7f6c-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a7f6c-110">EDI Engine</span></span>|  
|<span data-ttu-id="a7f6c-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a7f6c-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="a7f6c-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a7f6c-112">Message Text</span></span>|<span data-ttu-id="a7f6c-113">Les délimiteurs ne sont pas uniques. Les séparateurs de champs et de composants sont identiques</span><span class="sxs-lookup"><span data-stu-id="a7f6c-113">Delimiters are not unique, field and component separator are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a7f6c-114">Explication</span><span class="sxs-lookup"><span data-stu-id="a7f6c-114">Explanation</span></span>  
 <span data-ttu-id="a7f6c-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car l'élément de données et les séparateurs de composants ont la même valeur.</span><span class="sxs-lookup"><span data-stu-id="a7f6c-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and component separators were the same value.</span></span> <span data-ttu-id="a7f6c-116">Dans un échange X12, le séparateur d'éléments de données correspond au caractère situé en quatrième position du segment ISA et le séparateur de composants correspond au caractère dans le champ ISA16.</span><span class="sxs-lookup"><span data-stu-id="a7f6c-116">In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the component separator is the character in the ISA16 field.</span></span> <span data-ttu-id="a7f6c-117">Dans un échange EDIFACT, le séparateur d'éléments de données correspond au caractère dans le champ UNA2 et le séparateur de composants correspond au caractère dans le champ UNA1.</span><span class="sxs-lookup"><span data-stu-id="a7f6c-117">In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the component separator is the character in the UNA1 field.</span></span> <span data-ttu-id="a7f6c-118">Une situation où deux séparateurs possèdent la même valeur peut se produire dans un scénario de lot conservé (mais provoquera une condition d'erreur) ou lorsqu'un échange est reçu via une transmission PassThrough, puis récupéré en tant que fichier XML dans MessageBox par le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a7f6c-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a7f6c-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a7f6c-119">User Action</span></span>  
 <span data-ttu-id="a7f6c-120">Pour résoudre cette erreur, modifiez la valeur de l'élément de données ou celle des séparateurs de composants, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="a7f6c-120">To resolve this error, change the value of either the data element or component separators, and then resubmit the interchange.</span></span>
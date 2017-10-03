---
title: "Délimiteurs ne sont pas uniques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cc4f9c8eeb3a16fdd45222313bfb013dbf32ae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique"></a><span data-ttu-id="dda63-102">Les délimiteurs ne sont pas uniques.</span><span class="sxs-lookup"><span data-stu-id="dda63-102">Delimiters are not unique</span></span>
## <a name="details"></a><span data-ttu-id="dda63-103">Détails</span><span class="sxs-lookup"><span data-stu-id="dda63-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dda63-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="dda63-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dda63-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="dda63-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dda63-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="dda63-106">Event ID</span></span>|-|  
|<span data-ttu-id="dda63-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="dda63-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dda63-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="dda63-108"> EDI</span></span>|  
|<span data-ttu-id="dda63-109">Composant</span><span class="sxs-lookup"><span data-stu-id="dda63-109">Component</span></span>|<span data-ttu-id="dda63-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="dda63-110">EDI Engine</span></span>|  
|<span data-ttu-id="dda63-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="dda63-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="dda63-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="dda63-112">Message Text</span></span>|<span data-ttu-id="dda63-113">Les délimiteurs ne sont pas uniques.</span><span class="sxs-lookup"><span data-stu-id="dda63-113">Delimiters are not unique</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dda63-114">Explication</span><span class="sxs-lookup"><span data-stu-id="dda63-114">Explanation</span></span>  
 <span data-ttu-id="dda63-115">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI n'a pas pu traiter un échange sortant, car au moins deux des séparateurs identifiés dans l'échange, et utilisés pour séparer les facets de l'échange, étaient identiques.</span><span class="sxs-lookup"><span data-stu-id="dda63-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because two or more of the separators identified in the interchange, and used to separate facets of the interchange, were the same.</span></span> <span data-ttu-id="dda63-116">Les séparateurs sont identifiés dans le segment ISA d'un échange X12 et dans le segment UNA d'un échange EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="dda63-116">The separators are identified in the ISA segment of an X12 interchange and in the UNA segment of an EDIFACT interchange.</span></span> <span data-ttu-id="dda63-117">Deux séparateurs ou plus peuvent présenter la même valeur dans un scénario de lot conservé ou si un échange est reçu via une transmission de transfert et récupéré par le port d'envoi sous la forme d'un fichier XML dans MessageBox.</span><span class="sxs-lookup"><span data-stu-id="dda63-117">Two or more separators with the same value can occur in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span> <span data-ttu-id="dda63-118">Cette erreur provoque l'échec du traitement de l'échange.</span><span class="sxs-lookup"><span data-stu-id="dda63-118">This error condition will cause processing of the interchange to fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dda63-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="dda63-119">User Action</span></span>  
 <span data-ttu-id="dda63-120">Pour résoudre cette erreur, identifiez les séparateurs de l'échange qui présentent la même valeur, puis modifiez la valeur de l'un d'eux.</span><span class="sxs-lookup"><span data-stu-id="dda63-120">To resolve this error, identify which separators in the interchange have the same value, and change the value of one of the separators.</span></span>
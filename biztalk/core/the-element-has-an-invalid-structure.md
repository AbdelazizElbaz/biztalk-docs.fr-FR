---
title: "L’élément a une structure non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb94843c-cd21-48e3-ba30-aed0518b4d78
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b825fb0d2f5b4fe985a2024b1c97e21f4308b58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-element-has-an-invalid-structure"></a><span data-ttu-id="a17c0-102">L'élément possède une structure non valide</span><span class="sxs-lookup"><span data-stu-id="a17c0-102">The element has an invalid structure</span></span>
## <a name="details"></a><span data-ttu-id="a17c0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a17c0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a17c0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a17c0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a17c0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a17c0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a17c0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a17c0-106">Event ID</span></span>|-|  
|<span data-ttu-id="a17c0-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a17c0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a17c0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a17c0-108"> EDI</span></span>|  
|<span data-ttu-id="a17c0-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a17c0-109">Component</span></span>|<span data-ttu-id="a17c0-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a17c0-110">EDI Engine</span></span>|  
|<span data-ttu-id="a17c0-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a17c0-111">Symbolic Name</span></span>|<span data-ttu-id="a17c0-112">X12NseStructurallyInvalidElementDescription</span><span class="sxs-lookup"><span data-stu-id="a17c0-112">X12NseStructurallyInvalidElementDescription</span></span>|  
|<span data-ttu-id="a17c0-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a17c0-113">Message Text</span></span>|<span data-ttu-id="a17c0-114">L'élément '{0}' possède une structure non valide</span><span class="sxs-lookup"><span data-stu-id="a17c0-114">The element '{0}' has an invalid structure</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a17c0-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a17c0-115">Explanation</span></span>  
 <span data-ttu-id="a17c0-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car un élément de données n'a pas la structure spécifiée par le schéma applicable.</span><span class="sxs-lookup"><span data-stu-id="a17c0-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, or the send pipeline could not process the outgoing interchange, because a data element did not have the structure specified by the applicable schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a17c0-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a17c0-117">User Action</span></span>  
 <span data-ttu-id="a17c0-118">Pour résoudre cette erreur, corrigez la structure de l'élément de données dans l'échange sortant, ou demandez à l'expéditeur de corriger la structure de l'élément de données dans l'échange entrant afin qu'elle soit conforme au schéma de document.</span><span class="sxs-lookup"><span data-stu-id="a17c0-118">To resolve this error, fix the structure of the data element in the outgoing interchange, or have the sender of the interchange fix the structure of the data element in the incoming interchange, so that it conforms to the document schema.</span></span>
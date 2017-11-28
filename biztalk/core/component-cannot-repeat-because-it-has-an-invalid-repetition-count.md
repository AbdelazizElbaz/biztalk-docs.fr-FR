---
title: "Composant ne peut pas répété, car il possède un nombre de répétitions non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 040d7ea4-60a9-495f-91d7-b5b868957e2d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d535d72b5f265f07e6ae3fb468ed56efdc7975b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="component-cannot-repeat-because-it-has-an-invalid-repetition-count"></a><span data-ttu-id="289f8-102">Ce composant ne peut pas être répété car il possède un nombre de répétitions non valide.</span><span class="sxs-lookup"><span data-stu-id="289f8-102">Component cannot repeat because it has an invalid repetition count</span></span>
## <a name="details"></a><span data-ttu-id="289f8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="289f8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="289f8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="289f8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="289f8-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="289f8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="289f8-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="289f8-106">Event ID</span></span>|-|  
|<span data-ttu-id="289f8-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="289f8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="289f8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="289f8-108"> EDI</span></span>|  
|<span data-ttu-id="289f8-109">Composant</span><span class="sxs-lookup"><span data-stu-id="289f8-109">Component</span></span>|<span data-ttu-id="289f8-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="289f8-110">EDI Engine</span></span>|  
|<span data-ttu-id="289f8-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="289f8-111">Symbolic Name</span></span>|<span data-ttu-id="289f8-112">SchemaCode118EInvalidRepetition</span><span class="sxs-lookup"><span data-stu-id="289f8-112">SchemaCode118EInvalidRepetition</span></span>|  
|<span data-ttu-id="289f8-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="289f8-113">Message Text</span></span>|<span data-ttu-id="289f8-114">Ce composant ne peut pas être répété, il possède un nombre de répétitions non valide de {0}.</span><span class="sxs-lookup"><span data-stu-id="289f8-114">Component cannot repeat, it has an invalid repetition count of {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="289f8-115">Explication</span><span class="sxs-lookup"><span data-stu-id="289f8-115">Explanation</span></span>  
 <span data-ttu-id="289f8-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car un composant d'élément, un élément, un segment ou une boucle ont été répétés dans l'échange alors que le schéma n'autorise pas les répétitions.</span><span class="sxs-lookup"><span data-stu-id="289f8-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because an element component, element, segment, or loop was repeated in the interchange while the schema does not allow the repetition.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="289f8-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="289f8-117">User Action</span></span>  
 <span data-ttu-id="289f8-118">Pour résoudre cette erreur, assurez-vous que le composant d'élément, l'élément, le segment ou la boucle ne se répètent pas dans l'échange, comme cela est requis par le schéma, et procédez à un nouvel envoi du message.</span><span class="sxs-lookup"><span data-stu-id="289f8-118">To resolve this error, ensure that the element component, element, segment, or loop does not repeat in the interchange, as required by the schema, and have the message resent.</span></span>
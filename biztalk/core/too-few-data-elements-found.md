---
title: "Les éléments de données trop peu trouvés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6eca6c1-73ee-4b9a-be84-461051eda963
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8244f927cb7aff9cd0cb517dd132b986d53d67f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="too-few-data-elements-found"></a><span data-ttu-id="f9483-102">Éléments de données trouvés insuffisants</span><span class="sxs-lookup"><span data-stu-id="f9483-102">Too few data elements found</span></span>
## <a name="details"></a><span data-ttu-id="f9483-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f9483-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9483-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f9483-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f9483-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f9483-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f9483-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f9483-106">Event ID</span></span>|-|  
|<span data-ttu-id="f9483-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f9483-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f9483-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f9483-108"> EDI</span></span>|  
|<span data-ttu-id="f9483-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f9483-109">Component</span></span>|<span data-ttu-id="f9483-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f9483-110">EDI Engine</span></span>|  
|<span data-ttu-id="f9483-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f9483-111">Symbolic Name</span></span>|<span data-ttu-id="f9483-112">X12FeTooFewDataElementsFoundDescription</span><span class="sxs-lookup"><span data-stu-id="f9483-112">X12FeTooFewDataElementsFoundDescription</span></span>|  
|<span data-ttu-id="f9483-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f9483-113">Message Text</span></span>|<span data-ttu-id="f9483-114">Éléments de données trouvés insuffisants</span><span class="sxs-lookup"><span data-stu-id="f9483-114">Too few data elements found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f9483-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f9483-115">Explanation</span></span>  
 <span data-ttu-id="f9483-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car un segment de l'échange contient un nombre d'éléments de données inférieur au nombre requis par le schéma de document ou le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="f9483-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a segment in the interchange contained fewer data elements than required by the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f9483-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f9483-117">User Action</span></span>  
 <span data-ttu-id="f9483-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de s'assurer que les segments comprennent le nombre d'éléments de données requis, puis demandez-lui de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="f9483-118">To resolve this error, have the sender of the interchange ensure that segments include the required number of data elements, and then resend the interchange.</span></span>
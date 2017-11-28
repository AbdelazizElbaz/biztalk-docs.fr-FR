---
title: "Message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d’un format incorrect | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6310c96f897126a498772f2147a20c84f7e926a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a><span data-ttu-id="52504-102">Le message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d'un format incorrect</span><span class="sxs-lookup"><span data-stu-id="52504-102">Message did not contain UNA and pipeline property for delimiters was incorrect format</span></span>
## <a name="details"></a><span data-ttu-id="52504-103">Détails</span><span class="sxs-lookup"><span data-stu-id="52504-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52504-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="52504-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="52504-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="52504-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="52504-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="52504-106">Event ID</span></span>|-|  
|<span data-ttu-id="52504-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="52504-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="52504-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="52504-108"> EDI</span></span>|  
|<span data-ttu-id="52504-109">Composant</span><span class="sxs-lookup"><span data-stu-id="52504-109">Component</span></span>|<span data-ttu-id="52504-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="52504-110">EDI Engine</span></span>|  
|<span data-ttu-id="52504-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="52504-111">Symbolic Name</span></span>|<span data-ttu-id="52504-112">EfactDelimiterIncorrectFormat</span><span class="sxs-lookup"><span data-stu-id="52504-112">EfactDelimiterIncorrectFormat</span></span>|  
|<span data-ttu-id="52504-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="52504-113">Message Text</span></span>|<span data-ttu-id="52504-114">Le message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d'un format incorrect '{0}'</span><span class="sxs-lookup"><span data-stu-id="52504-114">Message did not contain UNA and pipeline property for delimiters was incorrect format '{0}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="52504-115">Explication</span><span class="sxs-lookup"><span data-stu-id="52504-115">Explanation</span></span>  
 <span data-ttu-id="52504-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange EDIFACT entrant car il n'a pas pu déterminer les séparateurs requis pour le traiter.</span><span class="sxs-lookup"><span data-stu-id="52504-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because it could not determine the separators required to process the interchange.</span></span> <span data-ttu-id="52504-117">Cette erreur peut se produire si l'échange ne possède pas de segment UNA et que la propriété de pipeline EfactDelimiters ne définit pas les séparateurs de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="52504-117">This can occur if the interchange does not have a UNA segment and the EfactDelimiters pipeline property does not adequately define the separators.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52504-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="52504-118">User Action</span></span>  
 <span data-ttu-id="52504-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="52504-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="52504-120">Assurez-vous que l'échange possède un segment UNA qui définit les séparateurs pour l'échange, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="52504-120">Make sure that the interchange has a UNA segment that defines the separators for the interchange, and then resend the interchange.</span></span>  
  
2.  <span data-ttu-id="52504-121">Pour définir la propriété EfactDelimiters du pipeline d'envoi, ouvrez la console Administration de BizTalk Server, cliquez avec le bouton droit sur l'emplacement de réception qui recevra l'échange, cliquez sur Propriétés, puis sur les points de suspension pour le pipeline, puis entrez une chaîne contenant les valeurs des séparateurs.</span><span class="sxs-lookup"><span data-stu-id="52504-121">Set the EfactDelimiters pipeline property for the send pipeline by opening the BizTalk Server Administration Console, right-clicking the receive location that will be receiving the interchange, clicking Properties, clicking the ellipsis for the pipeline, and then entering a string containing the values of the separators.</span></span>
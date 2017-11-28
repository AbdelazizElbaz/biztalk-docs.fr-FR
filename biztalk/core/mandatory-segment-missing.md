---
title: Segment obligatoire manquant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e459a22-8de5-426a-a46a-1d0ab72b532d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1250499f127aaa09e21269b894ed7bd51bd6a6ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mandatory-segment-missing"></a><span data-ttu-id="f2326-102">Segment obligatoire manquant</span><span class="sxs-lookup"><span data-stu-id="f2326-102">Mandatory Segment Missing</span></span>
## <a name="details"></a><span data-ttu-id="f2326-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f2326-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2326-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f2326-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f2326-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f2326-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f2326-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f2326-106">Event ID</span></span>|-|  
|<span data-ttu-id="f2326-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f2326-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f2326-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f2326-108"> EDI</span></span>|  
|<span data-ttu-id="f2326-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f2326-109">Component</span></span>|<span data-ttu-id="f2326-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f2326-110">EDI Engine</span></span>|  
|<span data-ttu-id="f2326-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f2326-111">Symbolic Name</span></span>|<span data-ttu-id="f2326-112">X12MandatorySegmentMissingDescription</span><span class="sxs-lookup"><span data-stu-id="f2326-112">X12MandatorySegmentMissingDescription</span></span>|  
|<span data-ttu-id="f2326-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f2326-113">Message Text</span></span>|<span data-ttu-id="f2326-114">Segment obligatoire manquant</span><span class="sxs-lookup"><span data-stu-id="f2326-114">Mandatory Segment Missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2326-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f2326-115">Explanation</span></span>  
 <span data-ttu-id="f2326-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant car celui-ci ne contient pas un segment requis par le schéma de message (pour lequel minOccurs est supérieur à 0).</span><span class="sxs-lookup"><span data-stu-id="f2326-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the interchange did not contain a segment that is required by the message schema (for which minOccurs is greater than 0).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2326-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f2326-117">User Action</span></span>  
 <span data-ttu-id="f2326-118">Pour résoudre cette erreur, assurez-vous que l'échange contient tous les segments requis par le schéma de message, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="f2326-118">To resolve this error, make sure that the interchange contains all segments required by the message schema, and then have the message resent.</span></span>
---
title: Segment inattendu | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7169190c-8893-4076-8634-137fd43992f2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47ff173b88c51ecf28a4979cef3a0c61475c62c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unexpected-segment"></a><span data-ttu-id="67748-102">Segment inattendu</span><span class="sxs-lookup"><span data-stu-id="67748-102">Unexpected segment</span></span>
## <a name="details"></a><span data-ttu-id="67748-103">Détails</span><span class="sxs-lookup"><span data-stu-id="67748-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67748-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="67748-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="67748-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="67748-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="67748-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="67748-106">Event ID</span></span>|-|  
|<span data-ttu-id="67748-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="67748-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="67748-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="67748-108"> EDI</span></span>|  
|<span data-ttu-id="67748-109">Composant</span><span class="sxs-lookup"><span data-stu-id="67748-109">Component</span></span>|<span data-ttu-id="67748-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="67748-110">EDI Engine</span></span>|  
|<span data-ttu-id="67748-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="67748-111">Symbolic Name</span></span>|<span data-ttu-id="67748-112">X12UnexpectedSegmentDescription</span><span class="sxs-lookup"><span data-stu-id="67748-112">X12UnexpectedSegmentDescription</span></span>|  
|<span data-ttu-id="67748-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="67748-113">Message Text</span></span>|<span data-ttu-id="67748-114">Segment inattendu</span><span class="sxs-lookup"><span data-stu-id="67748-114">Unexpected segment</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="67748-115">Explication</span><span class="sxs-lookup"><span data-stu-id="67748-115">Explanation</span></span>  
 <span data-ttu-id="67748-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car celui-ci contient un segment non défini par le schéma de document ou le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="67748-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contains a segment that is not defined by either the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67748-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="67748-117">User Action</span></span>  
 <span data-ttu-id="67748-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de supprimer le segment inattendu que celui-ci contient, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="67748-118">To resolve this error, have the sender of the interchange remove the unexpected segment from the interchange, and then resend the interchange.</span></span>
---
title: "Schéma de contrôle doivent être des segments d’en-tête dans le bon ordre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f38e8f-243a-467f-84bd-a232ef148b4b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3362bce20e1e7d31fa870a5376128d2d721c11f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="control-schema-should-have-header-segments-in-the-correct-order"></a><span data-ttu-id="7c886-102">Les segments d'en-tête du schéma de contrôle doivent être placés dans l'ordre adéquat</span><span class="sxs-lookup"><span data-stu-id="7c886-102">Control schema should have header segments in the correct order</span></span>
## <a name="details"></a><span data-ttu-id="7c886-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7c886-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c886-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7c886-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7c886-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7c886-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7c886-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7c886-106">Event ID</span></span>|-|  
|<span data-ttu-id="7c886-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7c886-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7c886-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7c886-108"> EDI</span></span>|  
|<span data-ttu-id="7c886-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7c886-109">Component</span></span>|<span data-ttu-id="7c886-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7c886-110">EDI Engine</span></span>|  
|<span data-ttu-id="7c886-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7c886-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="7c886-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7c886-112">Message Text</span></span>|<span data-ttu-id="7c886-113">Schéma de contrôle doit avoir des segments dans l’ordre suivant : ISA GS ST... SE GE IEA</span><span class="sxs-lookup"><span data-stu-id="7c886-113">Control schema should have segments in the following order: ISA GS ST .... SE GE IEA</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7c886-114">Explication</span><span class="sxs-lookup"><span data-stu-id="7c886-114">Explanation</span></span>  
 <span data-ttu-id="7c886-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter l'échange entrant car les en-têtes et les codes de fin de l'échange, des groupes et des documents informatisés ne sont pas placés dans l'ordre approprié dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="7c886-115">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming interchange because the headers and trailers for the interchange, groups, and transaction sets were not in the correct order in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7c886-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7c886-116">User Action</span></span>  
 <span data-ttu-id="7c886-117">Pour résoudre cette erreur, assurez-vous que les en-têtes ISA, GS et ST et les codes de fin SE, GE et IEA sont placés dans l'ordre approprié dans l'échange, puis renvoyez celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7c886-117">To resolve this error, ensure that the ISA, GS, and ST headers, and the SE, GE, and IEA trailers, are in the correct order in the interchange, and then resend the interchange.</span></span>
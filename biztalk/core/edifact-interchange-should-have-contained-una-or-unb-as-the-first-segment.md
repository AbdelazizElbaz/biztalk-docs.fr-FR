---
title: "Aurait dû contenir l’échange EDIFACT UNA ou UNB comme premier segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc43fd17-31d0-48df-93cd-524b40034764
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673df728dea00852e9713aed12f8ced902a4fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-should-have-contained-una-or-unb-as-the-first-segment"></a><span data-ttu-id="61eea-102">L'échange EDIFACT aurait dû contenir UNA ou UNB comme premier segment</span><span class="sxs-lookup"><span data-stu-id="61eea-102">Edifact interchange should have contained UNA or UNB as the first segment</span></span>
## <a name="details"></a><span data-ttu-id="61eea-103">Détails</span><span class="sxs-lookup"><span data-stu-id="61eea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61eea-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="61eea-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="61eea-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="61eea-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="61eea-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="61eea-106">Event ID</span></span>|-|  
|<span data-ttu-id="61eea-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="61eea-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61eea-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="61eea-108"> EDI</span></span>|  
|<span data-ttu-id="61eea-109">Composant</span><span class="sxs-lookup"><span data-stu-id="61eea-109">Component</span></span>|<span data-ttu-id="61eea-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="61eea-110">EDI Engine</span></span>|  
|<span data-ttu-id="61eea-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="61eea-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="61eea-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="61eea-112">Message Text</span></span>|<span data-ttu-id="61eea-113">L'échange EDIFACT aurait dû contenir UNA ou UNB comme premier segment.</span><span class="sxs-lookup"><span data-stu-id="61eea-113">Edifact interchange should have contained UNA or UNB as the first segment.</span></span> <span data-ttu-id="61eea-114">{0} a été trouvé à la place.</span><span class="sxs-lookup"><span data-stu-id="61eea-114">Instead {0} was found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61eea-115">Explication</span><span class="sxs-lookup"><span data-stu-id="61eea-115">Explanation</span></span>  
 <span data-ttu-id="61eea-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter l'échange EDIFACT entrant, car le premier segment n'est ni un segment UNA ni un segment UNB.</span><span class="sxs-lookup"><span data-stu-id="61eea-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA nor a UNB segment.</span></span> <span data-ttu-id="61eea-117">Le segment UNA est facultatif ; le segment UNB est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="61eea-117">The UNA segment is optional; the UNB segment is mandatory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61eea-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="61eea-118">User Action</span></span>  
 <span data-ttu-id="61eea-119">Pour résoudre cette erreur, assurez-vous que l'expéditeur de l'échange a inclus un segment UNA ou UNB comme premier segment de l'échange, puis demandez-lui de renvoyer ce dernier.</span><span class="sxs-lookup"><span data-stu-id="61eea-119">To resolve this error, ensure that the sender of the interchange includes the UNA or UNB segment as the first segment of the interchange, and then resends the interchange.</span></span>
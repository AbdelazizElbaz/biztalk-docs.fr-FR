---
title: Version de groupe fonctionnel non pris en charge | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 715e6585-a07a-4060-a15b-0c9603fbef19
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b92b7844c750d9a709ac2376bb8f126a32119f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="functional-group-version-not-supported"></a><span data-ttu-id="a01aa-102">Version de groupe fonctionnel non prise en charge</span><span class="sxs-lookup"><span data-stu-id="a01aa-102">Functional Group Version Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="a01aa-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a01aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a01aa-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a01aa-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a01aa-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a01aa-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a01aa-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a01aa-106">Event ID</span></span>|-|  
|<span data-ttu-id="a01aa-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a01aa-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a01aa-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a01aa-108"> EDI</span></span>|  
|<span data-ttu-id="a01aa-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a01aa-109">Component</span></span>|<span data-ttu-id="a01aa-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a01aa-110">EDI Engine</span></span>|  
|<span data-ttu-id="a01aa-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a01aa-111">Symbolic Name</span></span>|<span data-ttu-id="a01aa-112">X12FaGroupVersionNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="a01aa-112">X12FaGroupVersionNotSupportedDescription</span></span>|  
|<span data-ttu-id="a01aa-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a01aa-113">Message Text</span></span>|<span data-ttu-id="a01aa-114">Version de groupe fonctionnel non prise en charge</span><span class="sxs-lookup"><span data-stu-id="a01aa-114">Functional Group Version Not Supported</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a01aa-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a01aa-115">Explanation</span></span>  
 <span data-ttu-id="a01aa-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car BizTalk Server ne prend pas en charge le numéro de version dans le segment GS08 d'un groupe fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="a01aa-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because BizTalk Server does not support the version number in segment GS08 of a functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a01aa-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a01aa-117">User Action</span></span>  
 <span data-ttu-id="a01aa-118">Pour résoudre cette erreur, assurez-vous que les numéros de version de chacune instance du segment GS08 de tous les groupes fonctionnels de l'échange sont pris en charge par BizTalk Server, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="a01aa-118">To resolve this error, ensure that the version numbers in each instance of segment GS08 in all functional groups in the interchange are supported by BizTalk Server, and then have the interchange resent.</span></span> <span data-ttu-id="a01aa-119">Notez que les versions standard que BizTalk Server prend en charge sont répertoriées dans la rubrique « Prise en charge du schéma de document EDI » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a01aa-119">Note that the standard versions that BizTalk Server supports are listed in the "EDI Document Schema Support" topic of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product help.</span></span>
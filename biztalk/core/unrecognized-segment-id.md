---
title: "Non reconnue d’ID de segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a00fe451-0a84-4dca-980c-682243fc9804
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a49de4c7f800d740d9219f787a325279eac4c15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-segment-id"></a><span data-ttu-id="72cbd-102">ID de segment non reconnu</span><span class="sxs-lookup"><span data-stu-id="72cbd-102">Unrecognized segment ID</span></span>
## <a name="details"></a><span data-ttu-id="72cbd-103">Détails</span><span class="sxs-lookup"><span data-stu-id="72cbd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72cbd-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="72cbd-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="72cbd-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="72cbd-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="72cbd-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="72cbd-106">Event ID</span></span>|-|  
|<span data-ttu-id="72cbd-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="72cbd-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="72cbd-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="72cbd-108"> EDI</span></span>|  
|<span data-ttu-id="72cbd-109">Composant</span><span class="sxs-lookup"><span data-stu-id="72cbd-109">Component</span></span>|<span data-ttu-id="72cbd-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="72cbd-110">EDI Engine</span></span>|  
|<span data-ttu-id="72cbd-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="72cbd-111">Symbolic Name</span></span>|<span data-ttu-id="72cbd-112">EfactUnrecognizedSegmentIDDescription</span><span class="sxs-lookup"><span data-stu-id="72cbd-112">EfactUnrecognizedSegmentIDDescription</span></span><br /><br /> <span data-ttu-id="72cbd-113">X12UnrecognizedSegmentIDDescription</span><span class="sxs-lookup"><span data-stu-id="72cbd-113">X12UnrecognizedSegmentIDDescription</span></span>|  
|<span data-ttu-id="72cbd-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="72cbd-114">Message Text</span></span>|<span data-ttu-id="72cbd-115">ID de segment non reconnu</span><span class="sxs-lookup"><span data-stu-id="72cbd-115">Unrecognized segment ID</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72cbd-116">Explication</span><span class="sxs-lookup"><span data-stu-id="72cbd-116">Explanation</span></span>  
 <span data-ttu-id="72cbd-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car un segment d'un document informatisé de l'échange n'est pas défini par le schéma de document correspondant.</span><span class="sxs-lookup"><span data-stu-id="72cbd-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a segment in a transaction set in the interchange was not defined by the corresponding document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72cbd-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="72cbd-118">User Action</span></span>  
 <span data-ttu-id="72cbd-119">Pour résoudre cette erreur, demandez à l'expéditeur de supprimer le segment non reconnu, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="72cbd-119">To resolve this error, have the sender of the interchange remove the unrecognized segment and resend the interchange.</span></span>
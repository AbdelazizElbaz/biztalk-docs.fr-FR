---
title: "Non valide ou manquant ASN.1 CMS de fin des octets de structure compressée au cours du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b73ce58-d827-4ffc-b2d7-78836298efc8
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc3158e05c433b131661d54db28f51e122e16127
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-trailing-asn1-cms-compressed-structure-bytes-during-decompression-processing"></a><span data-ttu-id="068f2-102">Octets de structure compressée ASN.1 CMS de fin manquants ou non valides lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="068f2-102">Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="068f2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="068f2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="068f2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="068f2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="068f2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="068f2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="068f2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="068f2-106">Event ID</span></span>|-|  
|<span data-ttu-id="068f2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="068f2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="068f2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="068f2-108"> EDI</span></span>|  
|<span data-ttu-id="068f2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="068f2-109">Component</span></span>|<span data-ttu-id="068f2-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="068f2-110">AS2 Engine</span></span>|  
|<span data-ttu-id="068f2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="068f2-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="068f2-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="068f2-112">Message Text</span></span>|<span data-ttu-id="068f2-113">Octets de structure compressée ASN.1 CMS de fin manquants ou non valides lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="068f2-113">Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="068f2-114">Explication</span><span class="sxs-lookup"><span data-stu-id="068f2-114">Explanation</span></span>  
 <span data-ttu-id="068f2-115">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="068f2-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="068f2-116">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="068f2-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="068f2-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="068f2-117">User Action</span></span>  
 <span data-ttu-id="068f2-118">Passez en revue la structure des données compressées et recherchez toute falsification du message.</span><span class="sxs-lookup"><span data-stu-id="068f2-118">Review the structure of the compressed data and check for tampering with the message.</span></span>
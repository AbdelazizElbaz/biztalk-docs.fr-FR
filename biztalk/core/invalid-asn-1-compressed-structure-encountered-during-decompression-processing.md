---
title: "Structure durant la décompression compressée ASN.1 non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e5ebbd6-249a-4746-8ee6-cfb1f52ecc94
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825889d3379a4cbc1dc61bc688eb5ffc28745a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-asn1-compressed-structure-encountered-during-decompression-processing"></a><span data-ttu-id="6f024-102">Structure compressée ASN.1 non valide lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="6f024-102">Invalid ASN.1 compressed structure encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="6f024-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6f024-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f024-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6f024-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6f024-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6f024-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6f024-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6f024-106">Event ID</span></span>|-|  
|<span data-ttu-id="6f024-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6f024-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6f024-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6f024-108"> EDI</span></span>|  
|<span data-ttu-id="6f024-109">Composant</span><span class="sxs-lookup"><span data-stu-id="6f024-109">Component</span></span>|<span data-ttu-id="6f024-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="6f024-110">AS2 Engine</span></span>|  
|<span data-ttu-id="6f024-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6f024-111">Symbolic Name</span></span>|<span data-ttu-id="6f024-112">InvalidASN1CompressedStructureEncountered</span><span class="sxs-lookup"><span data-stu-id="6f024-112">InvalidASN1CompressedStructureEncountered</span></span>|  
|<span data-ttu-id="6f024-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6f024-113">Message Text</span></span>|<span data-ttu-id="6f024-114">En-tête compressé ASN.1 non valide ou manquant lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="6f024-114">Invalid or missing ASN.1 compressed header encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6f024-115">Explication</span><span class="sxs-lookup"><span data-stu-id="6f024-115">Explanation</span></span>  
 <span data-ttu-id="6f024-116">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="6f024-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="6f024-117">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="6f024-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6f024-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6f024-118">User Action</span></span>  
 <span data-ttu-id="6f024-119">Passez en revue la structure des données compressées et recherchez toute falsification du message.</span><span class="sxs-lookup"><span data-stu-id="6f024-119">Review the structure of the compressed data and check for tampering with the message.</span></span>
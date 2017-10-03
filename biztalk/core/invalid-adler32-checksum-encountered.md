---
title: "De contrôle Adler32 non valide rencontré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c069e6435c3840e9a535d492943dfc3956a513f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-adler32-checksum-encountered"></a><span data-ttu-id="f0600-102">Total de contrôle Adler32 non valide rencontré</span><span class="sxs-lookup"><span data-stu-id="f0600-102">Invalid Adler32 checksum encountered</span></span>
## <a name="details"></a><span data-ttu-id="f0600-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f0600-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0600-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f0600-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f0600-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f0600-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f0600-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f0600-106">Event ID</span></span>|-|  
|<span data-ttu-id="f0600-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f0600-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f0600-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f0600-108"> EDI</span></span>|  
|<span data-ttu-id="f0600-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f0600-109">Component</span></span>|<span data-ttu-id="f0600-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="f0600-110">AS2 Engine</span></span>|  
|<span data-ttu-id="f0600-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f0600-111">Symbolic Name</span></span>|<span data-ttu-id="f0600-112">InvalidAdler32ChecksumInCompressedMessageError</span><span class="sxs-lookup"><span data-stu-id="f0600-112">InvalidAdler32ChecksumInCompressedMessageError</span></span>|  
|<span data-ttu-id="f0600-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f0600-113">Message Text</span></span>|<span data-ttu-id="f0600-114">Total de contrôle Adler32 non valide rencontré</span><span class="sxs-lookup"><span data-stu-id="f0600-114">Invalid Adler32 checksum encountered</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f0600-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f0600-115">Explanation</span></span>  
 <span data-ttu-id="f0600-116">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="f0600-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="f0600-117">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="f0600-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0600-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0600-118">User Action</span></span>  
 <span data-ttu-id="f0600-119">L’utilisation de **de contrôle Adler32 non valide rencontré** indique une probabilité élevée de falsification.</span><span class="sxs-lookup"><span data-stu-id="f0600-119">The use of **Invalid Adler32 checksum encountered** indicates a high probability of tampering.</span></span> <span data-ttu-id="f0600-120">Recherchez toute falsification si vous voyez **de contrôle Adler32 non valide rencontré**.</span><span class="sxs-lookup"><span data-stu-id="f0600-120">Check for tampering if you see **Invalid Adler32 checksum encountered**.</span></span>
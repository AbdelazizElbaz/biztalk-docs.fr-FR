---
title: "Champ de compression ASN.1 ZLib non valide rencontré lors du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7caf047-badd-49e8-b955-554e5ec7511f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a347f63325e1c93497d178ffcc486ff8bd1c4f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-asn1-zlib-compression-field-encountered-during-decompression-processing"></a><span data-ttu-id="df321-102">Champ de compression ASN.1 ZLib non valide rencontré lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="df321-102">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="df321-103">Détails</span><span class="sxs-lookup"><span data-stu-id="df321-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="df321-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="df321-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="df321-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="df321-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="df321-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="df321-106">Event ID</span></span>|-|  
|<span data-ttu-id="df321-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="df321-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="df321-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="df321-108"> EDI</span></span>|  
|<span data-ttu-id="df321-109">Composant</span><span class="sxs-lookup"><span data-stu-id="df321-109">Component</span></span>|<span data-ttu-id="df321-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="df321-110">AS2 Engine</span></span>|  
|<span data-ttu-id="df321-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="df321-111">Symbolic Name</span></span>|<span data-ttu-id="df321-112">InvalidOptionalZLibFieldEncountered</span><span class="sxs-lookup"><span data-stu-id="df321-112">InvalidOptionalZLibFieldEncountered</span></span>|  
|<span data-ttu-id="df321-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="df321-113">Message Text</span></span>|<span data-ttu-id="df321-114">Champ de compression ASN.1 ZLib non valide rencontré lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="df321-114">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="df321-115">Explication</span><span class="sxs-lookup"><span data-stu-id="df321-115">Explanation</span></span>  
 <span data-ttu-id="df321-116">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="df321-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="df321-117">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="df321-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="df321-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="df321-118">User Action</span></span>  
 <span data-ttu-id="df321-119">Passez en revue la structure des données compressées et recherchez des preuves de falsification.</span><span class="sxs-lookup"><span data-stu-id="df321-119">Review the structure of the compressed data and check for evidence of tampering.</span></span>
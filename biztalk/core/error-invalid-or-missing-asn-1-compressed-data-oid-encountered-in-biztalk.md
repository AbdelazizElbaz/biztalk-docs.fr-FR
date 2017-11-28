---
title: "Non valide ou manquante compressé données OID ASN.1 rencontré lors du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0171daa8-289a-43f1-8cbf-d779ef9dc2ea
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05af1fc0c9f6516f180cf629cd0a21d838f0b4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-asn1-compressed-data-oid-encountered-during-decompression-processing"></a><span data-ttu-id="eef94-102">OID de données compressées ASN.1 non valide ou manquant lors de la décompression.</span><span class="sxs-lookup"><span data-stu-id="eef94-102">Invalid or missing ASN.1 Compressed Data OID encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="eef94-103">Détails</span><span class="sxs-lookup"><span data-stu-id="eef94-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eef94-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="eef94-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eef94-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="eef94-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eef94-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="eef94-106">Event ID</span></span>|-|  
|<span data-ttu-id="eef94-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="eef94-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eef94-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="eef94-108"> EDI</span></span>|  
|<span data-ttu-id="eef94-109">Composant</span><span class="sxs-lookup"><span data-stu-id="eef94-109">Component</span></span>|<span data-ttu-id="eef94-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="eef94-110">AS2 Engine</span></span>|  
|<span data-ttu-id="eef94-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="eef94-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="eef94-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="eef94-112">Message Text</span></span>|<span data-ttu-id="eef94-113">OID de données compressées ASN.1 non valide ou manquant lors de la décompression.</span><span class="sxs-lookup"><span data-stu-id="eef94-113">Invalid or missing ASN.1 Compressed Data OID encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eef94-114">Explication</span><span class="sxs-lookup"><span data-stu-id="eef94-114">Explanation</span></span>  
 <span data-ttu-id="eef94-115">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="eef94-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="eef94-116">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="eef94-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eef94-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eef94-117">User Action</span></span>  
 <span data-ttu-id="eef94-118">Passez en revue la structure des données compressées et recherchez toute falsification du message.</span><span class="sxs-lookup"><span data-stu-id="eef94-118">Review the structure of the compressed data and check for tampering with the message.</span></span>
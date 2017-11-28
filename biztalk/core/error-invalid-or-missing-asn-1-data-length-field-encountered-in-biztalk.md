---
title: "Champ de longueur des données ASN.1 non valide ou manquant rencontré lors du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd08648d-77b9-42a3-a50e-fd87eb36758a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2eda6a99e101484919f83d1b14f2f9bbd38c217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-asn1-data-length-field-encountered-during-decompression-processing"></a><span data-ttu-id="fe5ef-102">Champ Longueur des données ASN.1 rencontré lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="fe5ef-102">Invalid or missing ASN.1 Data Length field encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="fe5ef-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fe5ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe5ef-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fe5ef-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fe5ef-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fe5ef-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fe5ef-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fe5ef-106">Event ID</span></span>|-|  
|<span data-ttu-id="fe5ef-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fe5ef-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fe5ef-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="fe5ef-108"> EDI</span></span>|  
|<span data-ttu-id="fe5ef-109">Composant</span><span class="sxs-lookup"><span data-stu-id="fe5ef-109">Component</span></span>|<span data-ttu-id="fe5ef-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="fe5ef-110">AS2 Engine</span></span>|  
|<span data-ttu-id="fe5ef-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fe5ef-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="fe5ef-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fe5ef-112">Message Text</span></span>|<span data-ttu-id="fe5ef-113">Champ Longueur des données ASN.1 rencontré lors de la décompression</span><span class="sxs-lookup"><span data-stu-id="fe5ef-113">Invalid or missing ASN.1 Data Length field encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe5ef-114">Explication</span><span class="sxs-lookup"><span data-stu-id="fe5ef-114">Explanation</span></span>  
 <span data-ttu-id="fe5ef-115">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="fe5ef-116">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe5ef-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fe5ef-117">User Action</span></span>  
 <span data-ttu-id="fe5ef-118">Passez en revue la structure des données compressées et recherchez toute falsification du message.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-118">Review the structure of the compressed data and check for tampering with the message.</span></span>